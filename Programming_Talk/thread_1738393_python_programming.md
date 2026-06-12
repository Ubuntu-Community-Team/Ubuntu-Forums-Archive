---
title: "python programming"
date: 2011-04-24
forum: Programming Talk
---

### Post by scorpious on 2011-04-24
I posted this question in absolute beginner talk but should probably have posted it here.

anyway here's my programme


```
def start():
    size = (raw_input("Board size: "))
    number = ['2','3','4','5','6','7','8','9']
    while size not in number:
        print 'must be between 2 and 9'
        size = (raw_input("Board size: "))
    size = int(size)
    return size


def set_up(n):
    row = []
    grid = []
    count = 0
    while count != n:
        row.append('.')
        count += 1
    count = 0
    while count != n:
        grid.append(row)
        count += 1
    return grid
    
def assign_numbers(grid):
    print grid
    list = grid
    count = 0
    number = len(list) - 2
    start = 3
    while count <= number:
        list [count][0] = start
        print list
        count += 1
        start = start - 1
    return list

def assign_letters(grid):
    print grid
    new_list = grid[-1]
    number = len(new_list)
    letters = ['.','a','b','c','d','e','f','g','h']
    letters = letters[0:number]
    grid[-1] = letters
    print grid
    
    
    
    
grid_size = start()
grid1 = set_up(grid_size)
grid2 = assign_numbers(grid1)
grid3 = assign_letters(grid2)
print grid3
```when I input '4' I expected it to print
```
[['3', '.', '.', '.'], ['2', '.', '.', '.'], ['1', '.', '.', '.'], ['.', 'a', 'b', 'c']]
```but the assign_numbers function is giving me grief and i get
```
[['1', '.', '.', '.'], ['1', '.', '.', '.'], ['1', '.', '.', '.'], ['.', 'a', 'b', 'c']]
```can anyone tell me why it returns a whole bunch on 1s?

cheers
Tom

---

### Post by Tony Flury on 2011-04-24
it is due to the way that python applies objects and creates lists.

When you append row to grid - in your set_up function - you get n references to the same row object - so when you change grid[0] - you change the row object.

you need something like : 

```

grid.append(list(row))

```

To ensure you get a copy of your empty row - and not a copy of the reference.

[http://docs.python.org/library/functions.html?highlight=function%20list#list](http://docs.python.org/library/functions.html?highlight=function%20list#list)

---

### Post by lavinog on 2011-04-25
Try this:
```
def set_up(n):
    row = []
    grid = []
    count = 0
    while count != n:
        row.append('.')
        count += 1
    count = 0
    while count != n:
        grid.append(row[:])
        count += 1
    return grid

```

row[:] will make a copy of row instead of linking the same list object.

---

### Post by scorpious on 2011-04-25
It works! You two are geniuses! 

Thank you so much!!!




Lots of frustration right there haha :)

---

### Post by lavinog on 2011-04-25
I made some changes to the code to demonstrate some other ways you can accomplish those tasks:

```

def start():
    size = (raw_input("Board size: "))
    number = ['2','3','4','5','6','7','8','9']
    while size not in number:
        print 'must be between 2 and 9'
        size = (raw_input("Board size: "))
    size = int(size)
    return size


def set_up(n):
    grid = list()
    row = ['.'] * n # Creates ['.', '.', '.', '.',...etc]
    for r in range(n):
        grid.append(row[:]) 
    return grid
    
def assign_numbers(grid):
    list_ = grid   # Avoid keywords (like list) for variables
    
    start = 3
    
    for row in list_[:-1]: #list_[:-1] stops before last row
        row[0]=start
        start-=1  # same as start = start - 1
    return list_

def assign_letters(grid):
    number = len(grid)
    letters = ['.','a','b','c','d','e','f','g','h']
    grid[-1] = letters[0:number]
    return grid
    
    
    
    
grid_size = start()
grid1 = set_up(grid_size)
grid2 = assign_numbers(grid1)
grid3 = assign_letters(grid2)
print grid3


```

---

### Post by Tony Flury on 2011-04-26
> **lavinog said:**
> Try this:


row[:] will make a copy of row instead of linking the same list object.

Odd - i am sure i tried that - and it did not work - and now it does.

---

