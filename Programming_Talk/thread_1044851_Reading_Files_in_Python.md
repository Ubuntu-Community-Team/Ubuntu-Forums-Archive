---
title: "Reading Files in Python"
date: 2009-01-19
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-01-19
I have a some doubts as far as reading files is concerned.

Assume the following

q1)
for i in infile.readlines():
<tab>l=string.split(i," ")
<tab>if l[0]=="i"
etc.

When i wrote the code i realised that l[0]="i" stataement never gets satisfied. The program never entered the if statement.

q2)
Suppose i want to assign values a,b to text which lines on the first and second line of the file simultaneuously. how do i do it.

---

### Post by slavik on 2009-01-19
1. you're splitting on 'i' ... those chars will get taken out. and you are correct, the if will not be satisfied, what are you trying to achieve here?

2. I am not a Python expert but something like this should work.
array = file.lines()
a,b = array[0], array[1]

---

### Post by muntasir_120 on 2009-01-20
It is not clear what exactly you are expecting this bit of code to do, especially not without knowing the content of the file opened as infile.

You are actually splitting on ' ' (space) and not 'i'.

What is really happening here is that you are splitting each line into tokens separated by space. Then you are checking to see if the first token of a line (l[0], l is the list of tokens) is 'i'. This condition will only be satisfied if l[0] is just a single 'i' (i.e. it will not match if l starts with an 'i' and has more that 1 characters). There are probably no lines in your input file that start with a sungle 'i' by itself.

---

### Post by s|fr on 2009-01-20
your python code will throw. You do not access string methods like that.

1) if you want to split "i" on spaces you have to do i.split(" ")
```

for i in infile.readlines():
 tokens = i.split(" ")     <<<< ------- THIS
 if (tokens[0] == "whatever"):
  print "booyakasha"

```

2) Assuming your file can have more than 2 lines:
```

 line1, line2 = infile.readlines()[0:2]

```

[0:2] way of reading collections is called slicing.

hope that helps.

---

### Post by 7raTEYdCql on 2009-01-20
This is in reply to s|fr.

I dont get the second point.
If my file contains many lines. And if i want to loop through all the lines.
Taking the data from two lines at a time and stroring them in two different variables.

How will my for statement look like.

I cant give
for i,j in infile.readlines()[0:2]:
Error is said as too many arguments provided.

---

### Post by 7raTEYdCql on 2009-01-20
And this is for my first question.

if l[0]="i" never worked but this did.

if "i" in l

The two aren't the same. But assuming every line contained only one letter as a charachter and that letter was the first of every line. Why wasn't the first working and why was the second.


Note dont try to make any sense as to why i am asking these questions. I am taking part in my college codejam(competition is over). And for practice sake i am doing all the sums. It is for that.

---

### Post by s|fr on 2009-01-20
> **i.mehrzad said:**
> This is in reply to s|fr.

I dont get the second point.
If my file contains many lines. And if i want to loop through all the lines.
Taking the data from two lines at a time and stroring them in two different variables.

How will my for statement look like.

I cant give
for i,j in infile.readlines()[0:2]:
Error is said as too many arguments provided.

Ok so the first time I maybe misunderstood or perhaps the explanation was poor but anyway. I thought you just wanted to read the first 2 lines. :).

What I understood from your new post is that you want to step through your lines 2 at a time in the loop. In order to do this:

```

lines = file.readlines()
for i in range(len(lines)):
 if (i%2 != 0): continue
 subset_lines = []
 subset_lines = a[i:i+2]
 # do what you want with subset_lines 

```

I am sure you can optimise the above code maybe you'll do it yourself. subset_lines will contain the 2 lines upon each iteration for every iteration unless you have an odd number of lines in which case the last iteration will have only one line in subset_lines.

hope that helps

---

### Post by Sprut1 on 2009-01-20
> **i.mehrzad said:**
> And this is for my first question.

if l[0]="i" never worked but this did.

if "i" in l

The two aren't the same. But assuming every line contained only one letter as a charachter and that letter was the first of every line. Why wasn't the first working and why was the second.

Note dont try to make any sense as to why i am asking these questions. I am taking part in my college codejam(competition is over). And for practice sake i am doing all the sums. It is for that.

```
if l[0]="i":
```
You can't ask and set at the same time, this is correct:
```
if l[0]=="i":
```

This will check for any occurrence of char "i" in l.
```
if "i" in l
```

---

### Post by s|fr on 2009-01-20
a) "i" in l is not the same as b) "i" == l

let me explain.
a) is saying that the interpreter should check if the substring "i" exists in the string l. so:

```

# GOOD
line = "no i in team"
if ("i" in line):
 print "This will work because i is in the variabe line"

#BAD
line = "found me though"
if ("i" in line):
 print "This will not work because the substirn i is not in variable line"

```

b) on the other hand is saying is l exactly the same string as "i". so:

```

#GOOD
line = "i"
if ("i" == line):
 print "This will work because i is the same full string as stored in the variable line"
#BAD
line = "imememememe"
if ("i" == line):
 print "This wil not work because i is not same full string as stored in the variable line"

```

hope that helps.

---

### Post by 7raTEYdCql on 2009-01-20
What is a in a[i:i+2].

---

### Post by eightmillion on 2009-01-20
> **i.mehrzad said:**
> What is a in a[i:i+2].

I think that should be lines[i:i+2]. Here's a simpler way to do what he was trying to do:

```

lines = file.readlines()
subset_lines = []
for i in range(0,len(lines),2):
   subset_lines.append(lines[i:i+2])
```

I'm also surprised that no one has mentioned startswith.

```
In [52]: x = string.letters

In [53]: x
Out[53]: 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'

In [54]: x.startswith('a')
Out[54]: True

In [55]: x.startswith('abcd')
Out[55]: True

In [56]: x.startswith('fghi')
Out[56]: False

```

---

### Post by s|fr on 2009-01-21
eightmillion is right. "a" should be "lines". Thanks eight.

Also the reason startswith was not mentioned is because there is no condition as such where "i" is going to be in the string.

hope that helps.

---

### Post by eightmillion on 2009-01-21
The reason I mention startswith is because there never was any splitting on "i". I think that was just an interpretation error.
> for i in infile.readlines():
   l=string.split(i," ")
   if l[0]=="i"
splits the variable i on spaces and then checks whether the first element of l is the character "i". It's the equivalent of i.split(" "). If that is the intended behavior, "i" could be in the string. This whole thing would be easier to sort out if it was clear what the goal was.

---

