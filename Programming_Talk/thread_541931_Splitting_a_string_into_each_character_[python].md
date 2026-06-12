---
title: "Splitting a string into each character [python]"
date: 2007-09-03
forum: Programming Talk
---

### Post by Ashfire908 on 2007-09-03
Ok, I'm new to python and in programming in general as well. I'm writing a python script to download video files (avi, wmv, mov, etc) from a website. The videos each have a different identification number, which don't match up with the episode number of the video series. 

I'm don't need help with making python put the two numbers together, but i don't have links to download. I can generate the file link from the video's ID. Only problem is that I need to read the individual numbers in the ID, which is a string of numbers (i'll figure how to make the numbers stored as intergers later.) i would need to take a id number, like 342, and split it down so i could get a list to use, containing '3', '4', '2'  (or more preferably '300', '40', '2')

How would i go about reading a specified position in the string and then append/expand it to a list?

---

### Post by christhemonkey on 2007-09-03
To just split the string numbers into a list is easy:
```
numbers = "342"
lst = list(numbers)
print lst

```

To get it to to do it into hundreds and things is a little harder (but in no way impossible!)

---

### Post by Smygis on 2007-09-03
```

>>> nums = "342"
>>> lst = []
>>> for i in zip(reversed(nums), range(len(nums))):
...     lst = [i[0]+"0"*i[1]] + lst
... 
>>> lst
['300', '40', '2']


```

---

### Post by Ashfire908 on 2007-09-03
> **christhemonkey said:**
> To just split the string numbers into a list is easy:
```
numbers = "342"
lst = list(numbers)
print lst

```To get it to to do it into hundreds and things is a little harder (but in no way impossible!)
Thanks! That worked, and now i can get python to read the files! :)

---

### Post by nanotube on 2007-09-03
a string is already a list... the only difference between a string and a list(string) is that a list is mutable, while a string is not. so e.g., if you want to get the last three digits, you would slice off a [-3:]. and you can basically do whatever you can with a list. examples:
```
>>> a
'1234567890'
>>> a[-3:-1]
'89'
>>> a[-3:]
'890'
>>> a[-2]
'9'
>>> a[5]
'6'

```
hope this helps.

---

### Post by AZzKikR on 2007-09-04
edit: nvm, didn't read the OP's question.

---

