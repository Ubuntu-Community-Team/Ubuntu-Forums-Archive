---
title: "Python - For loop question"
date: 2010-04-20
forum: Programming Talk
---

### Post by WillFerrellLuva on 2010-04-20
My goal is to find all of the "permutations" of a number.  In this sense I mean that the permutations of 123 would be:  123, 132, 213, 231, etc...

I tried to accomplish this with the following python code:
```

def find_perms(z):
    """Takes an integer and returns an array of integers"""
    s_z = str(z)
    list_z= []
    for letter in s_z:
        list_z.append(letter)
    #print list_z
    perms = []
    for a in range(2):
        for b in range(1):
            temp = list_z
            print temp
            a_z = temp[a]
            del temp[a]
            b_z = temp[b]
            del temp[b]
            c_z = temp[0]
            perms.append(int(a_z + b_z + c_z))
            
    return perms    

def main():
    print find_perms(123)
       
if __name__ == "__main__":
    main()

```

However when I run this it becomes clear that the line
```

temp = list_z

```
is not functioning like I intended it to, and is not resetting the temp list every iteration of the for loop.

Is it possible to make the "temp = list_z" statement reset the value of temp every iteration through the for loop, or is there another way to find the "permutations" of the number?

Sorry if this is a newbie question, I'm still pretty new to python, and as always any help would be greatly appreciated.

---

### Post by wmcbrine on 2010-04-20
temp = list_z[:]

That will make a copy. What's happening now is that you're just creating a second label for the same list.

---

### Post by WillFerrellLuva on 2010-04-20
ah I see.  tyvm for the info

---

### Post by Can+~ on 2010-04-20
Also:

[PHP]from itertools import permutations

for i in permutations([1, 2, 3]):
    print i[/PHP]

```
(1, 2, 3)
(1, 3, 2)
(2, 1, 3)
(2, 3, 1)
(3, 1, 2)
(3, 2, 1)
```

If you're doing this for learning purposes, you can use this to check your results.

---

