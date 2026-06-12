---
title: "python problem."
date: 2019-12-24
forum: Programming Talk
---

### Post by wolftrax on 2019-12-24
hi there. 
I downloaded the MIT open course introduction to computer science course where they use python to teach programming concepts.  I watched the online lecture part one and two.   so I wanted to read the non programmers guide to python as they link to this , and gives you some assignments. 

the lecture tells me that input works as strings and the tutorial has the small program where you have to enter your name to pass. 
```
print("halt!") 
user_input=("who goes there ")
print("you may pass ",user_input) 

```
when I run this program it allows me to pass if I enter a number but if I enter a name or characters it will give me this error messsage 

```
Traceback (most recent call last):
  File "./halt.py", line 3, in <module>
    user_input=input("indtast navn")
  File "<string>", line 1, in <module>
NameError: name 'joe' is not defined

```

how come this happens ?

edit: I am using python version (3.6.7-1~18.04).

---

### Post by The Cog on 2019-12-24
Are you trying to use python2 or python3?

This works in python2:
```
print("halt!") 
user_input=raw_input("who goes there ")
print "you may pass ",user_input
```
This works in python3:
```
print("halt!")
user_input=input("who goes there ")
print("you may pass ",user_input)
```

---

### Post by wolftrax on 2019-12-24
> print("halt!")
user_input=input("who goes there ")
print("you may pass",user_input)

this is the exact program.   its what this [https://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_3/Who_Goes_There%3F](https://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_3/Who_Goes_There%3F)  tutorial says should but it as said only works for nummbers and not text strings.  
if I copy the program from the book and run it then it wil also just give me same error message. 

I also tried copy your code snippet. 
output is similar. 
> 

halt!
who goes there joe
Traceback (most recent call last):
  File "help.py", line 2, in <module>
    user_input=input("who goes there ")
  File "<string>", line 1, in <module>
NameError: name 'joe' is not defined
> 
halt!
who goes there 23 
('you may pass ', 23)




so it works fine with numbers but not with text strings.

---

### Post by wolftrax on 2019-12-24
its python version I am using python version (3.6.7-1~18.04).  which should be the version installed per default.  I did install idle as well but other than that I did not download or try to change anything its just not working as its supposed to do.

edit: I just tried the same program on windows vista with python version 3.8 and idle and it worked just as its supposed to do.

---

### Post by wolftrax on 2019-12-24
problem solved.  its because there are two python versions installed.   so when I write a python script it executes version 2.7 and that will off course not work.  I just found out that to invoke the python 3 version from commandline you have to type python 3 or else it will use version 2.7 instead.

---

### Post by mörgæs on 2019-12-25
Good, please mark the thread solved (top right corner, thread tools).

---

