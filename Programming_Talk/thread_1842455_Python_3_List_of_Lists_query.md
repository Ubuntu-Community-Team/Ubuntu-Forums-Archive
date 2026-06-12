---
title: "Python 3 List of Lists query"
date: 2011-09-11
forum: Programming Talk
---

### Post by Ravenshade on 2011-09-11
Hi, I've defined a list

list_name = [ [a, b], [x, y]] 

Now...I know how to access a list normally or at least read information from it using list_name[1] or such like. Now... that isn't helpful on telling me how to access a or y. If you would be so kind as to help me out. 

Thanks for your assistance.

---

### Post by Queue29 on 2011-09-11
list_name[1] returns [x, y], so

list_name[1][0] will thus return x

---

### Post by simeon87 on 2011-09-11
It works the same way. When you do list_name[0], you get back the first element, which is the list [a, b]. This is also a list, so you can do [0] to get the first element. So the following can be used to get the element a:

> list_name[0][0]

---

### Post by Ravenshade on 2011-09-11
It worked o.o thanks. 

Though another question >.< 

list_name.append(x) only applies one object or so I though. 

I'd like to add [c, d] to the array. Thus I tried to create a temporary array and then append that...

temp = [] 

list_name.append(temp) >.> Any avenues I could pursue?

---

### Post by ofnuts on 2011-09-11
> **Ravenshade said:**
> It worked o.o thanks. 

Though another question >.< 

list_name.append(x) only applies one object or so I though. 

I'd like to add [c, d] to the array. Thus I tried to create a temporary array and then append that...

temp = [] 

list_name.append(temp) >.> Any avenues I could pursue?
If you have 

list=[[1, 2], [3, 4]] 

then 

list.append([5,6]) 

adds its single parameter as one single element ([5,6]) to the list, and yields

list=[[1, 2], [3, 4], [5, 6]]

while 

list.extend([5,6]) 

takes the elements of the list parameter (5, and 6), and add each to the list:

list=[[1, 2], [3, 4], 5, 6]

---

### Post by Ravenshade on 2011-09-11
...

Wasn't adding the brackets. XD oh well. Thanks everyone.

---

