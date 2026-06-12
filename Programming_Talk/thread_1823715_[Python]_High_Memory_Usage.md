---
title: "[Python] High Memory Usage"
date: 2011-08-12
forum: Programming Talk
---

### Post by cgroza on 2011-08-12
Hello,

I am working on the project listed in my signature and I have a problem.

From a cold start, it already takes 25.7 MB of memory. I have seen bigger and better text editors written in the same language that take only 8 MB (drPython for example).
I checked it using the System Monitor that Ubuntu includes.
I really don't understand where it is coming from.

I am looking on reducing the memory footprint and need a method to identify what is taking that much memory. 
Something like a profiler or similar.
Thank you.

---

### Post by cgroza on 2011-08-13
bump

---

### Post by NovaAesa on 2011-08-14
Have you done a google search yet? I did one just then for "memory profiler python" and it came up with a few projects that look promising - guppy and pysizer.

---

### Post by AureiAnimus on 2011-08-14
Also, a search for [python garbage collection] might give you more understanding about your problem.

I recently had a problem with python memory usage, which came down more or less to this (semi-pseudo-code):

```
for file in directory:
    text = open(file).read()
    do something with text
```

Now, if you're not familiar with lower level languages and the python garbage collector (like I was), you might think: well, the text variable is overwritten each time, so this can't possibly take that much more space than my largest file. Except: it's not really overwritten. So if this if loops continues, it will take the memory of the sum of all the files in the directory.

This can be avoided by placing the inner part of the for loop in a function and only passing that function the values it needs.
```

def read_and_do_something(file):
    text = open(file).read()
    do something with text
for file in directory:
    read_and_do_something(file)
```

this way the text variable (and all others, except file) are deleted when the function ends because they "run out of scope" which means that there's no way they could be accessed.

Hope this helps.

---

### Post by cgroza on 2011-08-14
Thanks for your tips. I will look in my code for cases like the one you showed me, although the app has barely started and did not have too much time to take that amount of memory.

---

### Post by Queue29 on 2011-08-14
If you're worried about memory efficiency you shouldn't be working with Python in the first place. The memory usage overhead of Python is obscene at best; it is not nor ever was a design goal of Python to be efficient.

---

### Post by cgroza on 2011-08-14
> **Queue29 said:**
> If you're worried about memory efficiency you shouldn't be working with Python in the first place. The memory usage overhead of Python is obscene at best; it is not nor ever was a design goal of Python to be efficient.
Ok, that is new to me.
I think a very big part of the memory belongs to the advanced GUI widgets I use.
Anyway, the memory usage seems stable,it does not leak or anything.

---

### Post by Smart Viking on 2011-08-14
> **Queue29 said:**
> If you're worried about memory efficiency you shouldn't be working with Python in the first place. The memory usage overhead of Python is obscene at best; it is not nor ever was a design goal of Python to be efficient.
Python is not simply this slow, prototyping language, it's a real language that can be used to make real applications. It's not like it doesn't consider efficiency, but it consider other things as well that makes it slower. So I disagree in that he/she shouldn't use Python in the first place.

---

### Post by lavinog on 2011-08-15
Have you tried converting your program to python3.x?

Garbage collection appears to behave differently between 2.x and 3.x
for instance, the following command will use a decent amount of memory in both versions (uses about 1g on my machine):
```
a=list(range(0,30000000))
```
The following command will free up that memory in 3.2 but 2.7 will not free up much if any memory:
```
del(a)
```

Also, I noticed that there are a considerable amount of plugins installed by default.  Have you tried disabling them by default?
Also the builtin bash shell and python interpreter will use up some memory as well.

25.7Mb is still pretty low for memory usage.  Keep in mind that python likes to keep unused objects in memory if it feels that it will need them in the future.  Allocating and freeing memory uses cpu cycles, so if it thinks that it will be allocating more memory in the future, it just wont free it up.

---

### Post by slavik on 2011-08-15
man pmap :)

---

### Post by ssam on 2011-08-15
> **AureiAnimus said:**
> Also, a search for [python garbage collection] might give you more understanding about your problem.

I recently had a problem with python memory usage, which came down more or less to this (semi-pseudo-code):

```
for file in directory:
    text = open(file).read()
    do something with text
```

Now, if you're not familiar with lower level languages and the python garbage collector (like I was), you might think: well, the text variable is overwritten each time, so this can't possibly take that much more space than my largest file. Except: it's not really overwritten. So if this if loops continues, it will take the memory of the sum of all the files in the directory.

This can be avoided by placing the inner part of the for loop in a function and only passing that function the values it needs.
```

def read_and_do_something(file):
    text = open(file).read()
    do something with text
for file in directory:
    read_and_do_something(file)
```

this way the text variable (and all others, except file) are deleted when the function ends because they "run out of scope" which means that there's no way they could be accessed.

Hope this helps.

did that actually help?

when you do
```
text = open(file).read()
```
that will create a string and attach the name 'text' to it. when you reassign 'text' to point at a new string then the old string still exists, but has not references pointing to it. the next time the garbage collector runs the memory can be freed.

by moving it into a function now you have 'text' going out of scope and hence no more references pointing to the old string. it still needs to wait for the garbage collector to find it.

i wonder if its more of an allocator issue. if you do
```

text = open("1.txt").read()
text = open("2.txt").read()

```
then the memory to hold 2.txt is allocated before 'text' is reassigned. so at some point both strings must be held in memory.

so may this would work, and save you the trouble of having to restructure the code 
```

for file in directory:
    text = open(file).read()
    do something with text
    del a

```
note that del does not free the memory, just removes the reference. but if you are lucky it might have been freed by the time you get back around to the start of the loop.

also if you could rewrite the code as
```

for file in directory:
    for line in open(file):
         do something with line

```
then you only need to hold 1 line of text at a time.

---

### Post by cgroza on 2011-08-15
ssam, I have few to no case similar to what you described to me. I do all the file manipulation through my text control, and I rarely read a file by myself.

lavinog, I tried disabling all the plugins, but that made only a 1-2 MB difference.
Maybe I should read more about python memory management.

---

