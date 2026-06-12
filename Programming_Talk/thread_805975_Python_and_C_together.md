---
title: "Python and C together"
date: 2008-05-24
forum: Programming Talk
---

### Post by calsaverini on 2008-05-24
Hi, 

I'm new to python and not a very skilled programmer in C as well. But I need to create from scratch a program to analyze some data I have for my doctoring thesis so I need to do this. 

I have already made a program in C that receive the data in command line like this:

```
./my_cute_program x1 x2 x3 ... xN
```

where x1, x2, etc... are the needed data.

The program used to be run from a bash script that got the data from a mysql database and made the above call to the program.

But then, the script where soooo slow for tests I needed to run (it took like half an hour to generate some 10³ gaussian random numbers and send them to the C program) that I decided to use a very simple Python program to do this.

The Python program simply generate a string with the data:

S = " x1 x2 ... xN"

and called the C program via the os.system command:

```
os.system('./my_cute_program'+S)
```

Until now I was only looking to the text output of the C program so I had no problem with any C/Python integration (I just didn't needed it). But now I need to run some automated tests for many many runs of the C program, make histograms and such. So I need the python program to read variables from the C program.

My questions are:
1) Is there a way that my Python program can read variables from the C program when the later finish its run?

2) Is there a more intelligent way to call the C program from python? The method I use above is just make a call to the OS. It seems to me a dumb way to do it. Is there a way I can call maybe the main() function of my C program from inside python or something like that? 
- 

Thanks for helping.

---

### Post by unutbu on 2008-05-24
```
#!/usr/bin/env python
from os import popen
cmd='./my_cute_program'+S
result=popen(cmd,'r')
for line in result:
    ...
result.close()
```

I think popen is the command you want.

There might be a better way; I'm just learning Python myself.

---

### Post by calsaverini on 2008-05-24
Hummm... this seems to be good. Then I'll probably have to learn about how to use pipes. [:P]

I'm a complete begginer.

---

### Post by pmasiar on 2008-05-24
Simpler way than pipes would be to redirect output of C program to a file, either append all together, or each one in separate file, and then read/parse/analyze results in Python.

But I am curious why bash was too slow - IMHO culprit would be database and not bash.

---

### Post by calsaverini on 2008-05-25
> **pmasiar said:**
> But I am curious why bash was too slow - IMHO culprit would be database and not bash.

I think the problem was with the random number generator I was using in the bash script. When I was running the test, I didn't used the real data from the mysql database. I just feed in some random data exactly to save time. I don't know why it was so slow.

Using files would probably be easy and imediate. But yesterday I decided to use this problem as an excuse to actually learn to extend python with C. I found some interesting things over the net, but it's very difficult to find a tutorial with SIMPLE examples. The usual examples are "let's do so and so with this rather complicated library that you'll have to learn how to use before you can understand what I did here". 

But there are some helpful examples:

[LIST]
[*][http://www.swig.org/](http://www.swig.org/) - this is a very useful tool to build C extensions to python without having to bother about the headers and functions to convert data types.,

[*][http://en.wikibooks.org/wiki/Python_Programming/Extending_with_C](http://en.wikibooks.org/wiki/Python_Programming/Extending_with_C) - This page in the Python Wikibook, on the Wikimedia site, was the only really simple example I've found of how to build a C extension. A real "hello world" example is always useful.
[/LIST]

Thanks for the help. When I really learn how to do it I'll make a longer post just describing it.

---

