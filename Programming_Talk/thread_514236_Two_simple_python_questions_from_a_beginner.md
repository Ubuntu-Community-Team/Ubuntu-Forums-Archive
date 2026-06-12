---
title: "Two simple python questions from a beginner"
date: 2007-07-31
forum: Programming Talk
---

### Post by tc101 on 2007-07-31
I have two questions about the code below and the results that follow

1.  Why are all three lines I have written showing up on one line.  I thought I would be writing out 3 lines to the file.
2.  Notice what I am doing with time.  Readline is reading is reading from the previous run, not the current run.  It is as if I have not really closed the file.


```
import time
t = time.strftime('%X ')
print "time =", t
f=open('01workfile', 'w')
s = "time is " +  t
f.write(s)
f.write("this is a test line 2 - ")
f.write("this is a test line 3 - ")
f.close
f2=open('01workfile')
s = f2.readline()
print s

```


>>> 
time = 13:14:46 
time is 13:14:25 this is a test line 2 - this is a test line 3 - 
>>> 
time = 13:14:56 
time is 13:14:46 this is a test line 2 - this is a test line 3 -

---

### Post by LaRoza on 2007-07-31
Add a newline character, '\n'.

---

### Post by pmasiar on 2007-07-31
print adds newline to putput (unless ended by comma), but write() does not, you need to add it yourself.

---

### Post by tc101 on 2007-07-31
Thanks.  The /n answers my first question.  

Now this is the only thing I am confused about, and I have changed the code to make it clearer

```
import time
t = time.strftime('%X ')
print "time program run =", t
f=open('01workfile', 'w')
s = "time line written is " +  t + "\n"
f.write(s)
f.write("this is a test line 2 - \n")
f.write("this is a test line 3 - \n")
f.close
f2=open('01workfile')
for line in f2:
    print line

```

gives results

time program run = 13:36:55 
time line written is 13:35:03 

this is a test line 2 - 

this is a test line 3 -

===================

i```
mport time
t = time.strftime('%X ')
print "time program run =", t
f=open('01workfile', 'w')
s = "time line written is " +  t + "\n"
f.write(s)
f.write("this is a test line 2 - \n")
f.write("this is a test line 3 - \n")
f.close
f=open('01workfile')
for line in f:
    print line

```

gives results

time program run = 13:37:52 
time line written is 13:37:52 

this is a test line 2 - 

this is a test line 3 - 

================

Notice that in the first example it is reading a previous creation of the file.  You can see this because the times are not the same.

Notice in the second example it is reading the current creation of the file.  The only difference between the two examples is that in the first one I used a different file name to open the file.  In the second example I use the same file name to open the file.

It looks like the file is not actually closed in the first example.  Why?

---

### Post by smartbei on 2007-07-31
The correct command is:
```

f.close() #note the parentheses

```
close is a method of the file handler.

---

### Post by tc101 on 2007-07-31
Thanks.  That solves the problem.  I don't understand why it didn't give me an error when I had the wrong syntax.

---

### Post by pmasiar on 2007-07-31
f.close() executes the code.

f.close will return address of the callable (which you discarded without using). Functions and methods are first-class objects and can be passed - ie you can pass a function name as parameter, to be executed. Look:

```

def add2(x, y):
	return x + y

def do(f, *args):
	return f(*args) # execute passed function with given arguments)

do(add2, 2, 3) # reference to our function add2 
5



```

Cool, eh?

---

### Post by tc101 on 2007-07-31
Very cool.

---

