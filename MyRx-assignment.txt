# 1. Given a sorted array of positive and negative numbers. You have to Square it and sort it.

def sorted_squared_numbers(arr):
    squared_numbers = []
    for num in arr:
        squared_numbers.append(num * num)
 
    for i in range(len(squared_numbers)-1):
        for j in range(len(squared_numbers)-i-1):
            if squared_numbers[j]>squared_numbers[j+1]:
                squared_numbers[j],squared_numbers[j+1]=squared_numbers[j+1],squared_numbers[j]
    return squared_numbers


user_input = list(map(int,input().split())) # input should be numbers separated by space
result = sorted_squared_numbers(user_input)
print(output_list)


# 2. Design an immutable class 

from dataclasses import dataclass
from datetime import date

@dataclass(frozen=True)
class Address:
    city: str
    state: str

@dataclass(frozen=True)
class Employee:
    name: str
    id: str
    date_of_joining: date
    addresses: list[Address]

address1 = Address("hyderabad","telangana")
address2 = Address("whitefield","bangalore")

emp1 = Employee(
    name="steve rogers",
    id="2025",
    date_of_joining=date(2025, 2, 15),
    addresses=(address1, address2)
)
print(emp1)



# 3. Given an array of Red Green Blue balls.You have to sort it.

def get_sorted_balls(arr):
    B_count=0
    G_count=0
    R_count=0 

    for color in arr:
        if color=="B":
            B_count+=1 
        elif color=="G":
            G_count+=1 
        else:
            R_count+=1

    index=0

    for _ in range(B_count):
        arr[index]="B" 
        index+=1 

    for _ in range(G_count):
        arr[index]="G" 
        index+=1 
    
    for _ in range(R_count):
        arr[index]="R" 
        index+=1 
    
    return arr 

user_input=input().split() # input should be alphabets separated by space
result=get_sorted_balls(user_input)
print(user_input)

# 4. We are given two arrays that represent the arrival and departure times of trains, the
# task is to find the minimum number of platforms required so that no train waits.


def min_no_platforms(arrivals, departures):
 
    arrivals.sort()
    departures.sort()
    n = len(arrivals)
    platform_count = 0
    max_platforms = 0
    i = 0
    j = 0

    while i < n and j < n:
        if arrivals[i] <= departures[j]:
            platform_count += 1
            max_platforms = max(max_platforms, platform_count)
            i += 1
        else:
            platform_count -= 1
            j += 1

    return max_platforms

def convert_to_minutes(t):
    hours, minutes = map(int, t.split(':'))
    return hours * 60 + minutes

arrivals = ["9:00", "9:40", "9:50", "11:00", "15:00", "18:00"]
departures = ["9:10", "12:00", "11:20", "11:30", "19:00", "20:00"]

arrivals = [convert_to_minutes(t) for t in arrivals]
departures = [convert_to_minutes(t) for t in departures]

result = min_no_platforms(arrivals, departures)
print(f"Minimum number of platforms: {result}")


# 5. Sort hashmap by value.

dict_1 = {101: "John Doe", 102: "Jane Smith", 103: "Peter Johnson"}

sorted_dict = sorted(dict_1.items(), key=lambda item: item[1])

result_dict=dict(sorted_dict)

print(result_dict)

