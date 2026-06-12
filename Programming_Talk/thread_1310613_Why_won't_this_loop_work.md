---
title: "Why won't this loop work?"
date: 2009-11-01
forum: Programming Talk
---

### Post by DanielJackins on 2009-11-01
I'm trying to sort through a list of grades, and from it create a list that stores however many grades fall under each grade segment (ie < 1.0, < 2.0, etc). I made this loop, which is probably very poorly coded (my brother always says nested loops are bad?) but even so I cannot see why it doesn't work. Here it is.

```
file = open('grades1.txt', 'r')

line = ''
students = []
grades = []
grade_dist = []
check = 0
theta = 0
theta1 = 0

# Creates a list of students from the input file, stopping when it reaches EOF

while line != 'EOF':
    line = file.readline()   
    students.append(line.split("\t"))

# Removes A1 and EOF from list (not needed)

students = students[1:-1]

for student in students:
    grades.append(student[5])

print grades

[B]while check <= 10:
    count = 0
    for grade in grades:
        if float(grade) < (check + 1):
            count += 1
            grades.remove(grade)
    grade_dist.append(count)
    check += 1[/B]



#for thing in grade_dist:
#    theta = 2*360*(thing/200.0)
#    print 'arc 400 300 200 200', theta1, theta, 'pie'
#    theta1 = theta
#    print theta

```
 
The bolded while loop is what I'm interested in. So for every grade in the list of grades, it checks if it's under 1, and if it is, increases the count and removes it from the list, doing the same for every element and obtaining a final count of grades under 1. It works correctly for the first loop, and for the most part the rest of the loops, but for some reason on the second loop and on it misses some values it should be catching, like a 1.5 (which is less than 2) some ways down the list. It catches all the other 1.5's, but not that one.

Any suggestions/input?

Thanks

---

### Post by eightmillion on 2009-11-02
> **DanielJackins said:**
> 
The bolded while loop is what I'm interested in. So for every grade in the list of grades, it checks if it's under 1, and if it is, increases the count and removes it from the list, doing the same for every element and obtaining a final count of grades under 1. It works correctly for the first loop, and for the most part the rest of the loops, but for some reason on the second loop and on it misses some values it should be catching, like a 1.5 (which is less than 2) some ways down the list. It catches all the other 1.5's, but not that one.

Any suggestions/input?

Thanks

The reason it doesn't work is because you're popping values out of grades while you're looping over grades. If you're going to remove the values, you have to do it after your loop is finished. See this example:
[PHP]>>> x = range(10)
>>> for i in x:
...     x.pop()
...
9
8
7
6
5
>>> print x
[0, 1, 2, 3, 4][/PHP]
Notice how it doesn't loop 10 times, like what would be expected, because I'm removing values from the list with each iteration. I'm not sure on the inner workings, but I suspect that python reevaluates the loop conditions with every iteration. When it gets to the 6th iteration, there's only 5 things in the list and it's already completed 5 iterations, so the loop is finished.

---

