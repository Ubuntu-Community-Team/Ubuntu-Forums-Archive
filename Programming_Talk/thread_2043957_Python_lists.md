---
title: "Python lists"
date: 2012-08-17
forum: Programming Talk
---

### Post by angus1964 on 2012-08-17
I have the following function.
```
def createFullList(n, startWeek):
    
    oldWeek = startWeek
    for x in range(n-2):
        tempOne = oldWeek[0]
        oldWeek.insert(-1, tempOne)
        del oldWeek[0]
        print (oldWeek)
        week[x] = (oldWeek)
       
```
The n comes from the user entering the number of teams, startWeek comes from another function which creates the first list.

When run get the following error. week[x] = (oldWeek)
IndexError: list assignment index out of range
       
What i need at the end of the function is a list for each week from 1 up number of teams - 1. Therefore i need week[1] = [1,2,3,4,5,6,7,8], week[2] =[2,3,4,5,6,7,1,8] and so on up to week[7] = [7,1,2,3,4,5,6,8]. thats an example if the user inputs 8. i know how to do the rotation its creating the list of lists so to speak that im stuck on.

---

### Post by Bachstelze on 2012-08-17
You can do

```
week.append(oldweek)
```

---

### Post by angus1964 on 2012-08-17
Thanks for the quick reply. Im fairly new to python so hopefully this wont sound too stupid.
wouldn't ```
week.append(oldweek)
```
Create one long list with all the weeks together.
What i really need is separate lists i.e week[1], week[2] etc as i then take them and change the order of the weeks around.

---

### Post by Bachstelze on 2012-08-17
[font=monospace]l.append(x)[/font] inserts the object x at the tail of the list l. This is exactly what you are trying to do with your last line, except that your code doesn't work. ;)

---

### Post by angus1964 on 2012-08-17
My last line was meant to create n-1 number of lists. I understand that append would give me one long list but that is not really any use for the rest of my code.

---

### Post by Bachstelze on 2012-08-17
> **angus1964 said:**
> I understand that append would give me one long list

You are wrong.

---

### Post by angus1964 on 2012-08-17
My apologies im confusing append with extend. But using append i will still only have 1 list i really want to create 7 ( or n-1) lists is there any way to do this?

---

### Post by angus1964 on 2012-08-17
Aplogies again i put.
```
week.append(oldweek)
``` 
In as my last line and it worked fine, when it has run at hte command prompt i typed ```
print(week[2])
```
but the output was the same as the last line of the loop which i assumed would be week[7]. Have i missed something?

---

### Post by Bachstelze on 2012-08-17
This is because in Python, lists are just stored by reference. Look at this:

```
a = [1, 2, 3]
b = a
a[1] = 0
print a
print b
```

You see that a and b are both [1, 0, 3]. When we do a = b, we say that a and b are the same list, so when we modify a, we also modify b.

The same happens in your code: you are always storing oldWeek, so it's always the same list. You need to store a *copy* of the current oldWeek each time :

```
week.append(oldWeek[:])
```

---

### Post by angus1964 on 2012-08-17
Many thanks for your help, i've got it working to a fashion.
My code is now.
```
def createFullList(n, startWeek):
    
    for x in range(n-2):
        tempOne = startWeek[0]
        startWeek.insert(-1, tempOne)
        del startWeek[0]
        
        week.append(startWeek[:])
    print (week)  
    return week
```
 
This works but the problem i now have is that my list doesnt include the original week, i have tried week = startWeek in various places but it always seems to muck up the lists. Any ideas how i would get this to be included.

---

### Post by Bachstelze on 2012-08-18
Just append it before the loop (or after, depending on where you want it to be in the list)

```
def createFullList(n, startWeek):
    week.append(startWeek[:])
    for x in range(n-2):
        tempOne = startWeek[0]
        startWeek.insert(-1, tempOne)
        del startWeek[0]
        
        week.append(startWeek[:])
    print (week)  
    return week
```

---

