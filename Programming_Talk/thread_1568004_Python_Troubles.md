---
title: "Python Troubles"
date: 2010-09-04
forum: Programming Talk
---

### Post by Fableflame on 2010-09-04
Okay, so I'm learning Python as my first language, and I've come across a problem in this tutorial, a typo in one of the example codes. Since I don't know Python yet, I have no idea what the typo is or how to fix it. I know it's a typo in the example, because after trying to find errors that I made typing it out, I actually copy-pasted it, and still got the error.

If you go to [http://learnpythonthehardway.org/index](http://learnpythonthehardway.org/index) and open up the .pdf file, and go down to page 39, the typo is in exercise 15.

This is the code it give me to run in the example:

```
1
from sys import argv
2
3
script, filename = argv
4
5
txt = open(filename)
6
7
8
print "Here's your file %r:" % filename
print txt.read()
9
10
11
print "I'll also ask you to type it again:"
file_again = raw_input("> ")
12
13
txt_again = open(file_again)
14
15
print txt_again.read()

```

Now, when I run this code, this is the terminal readout:

```
Traceback (most recent call last):
  File "ex15.py", line 3, in <module>
    script, filename = argv
ValueError: need more than 1 value to unpack
```

Can anyone explain to me what's going on here, and tell me how to fix this so I can continue learning Python? I've really liked this tutorial up until this point, and I'd like to continue using it.

---

### Post by MadCow108 on 2010-09-04
argv is the list of the command line options
it has always at least one entry, the script name, and as many more entries as command line optons where given

```

script, filename = argv

```
here the entries of list argv is assigned to two named variables
It expects that argv has two entries, which is the case when you have given one command line option, e.g.:

python file.py filename

this would be equivalent (but not so nice) code:
```

script = argv[0]
filename = argv[1]

```

---

### Post by Fableflame on 2010-09-04
Alright MadCow108, I changed the code to:

```
from sys import argv

script = argv[0]
filename = argv[1]

txt = open(filename)

print "Here's your file %r:" % filename
print txt.read()

print "I'll also ask you to type it again:"
file_again = raw_input("> ")

txt_again = open(file_again)

print txt_again.read()
```

But that gave me this error;

```
Traceback (most recent call last):
  File "ex15.py", line 4, in <module>
    filename = argv[1]
IndexError: list index out of range

```

---

### Post by MadCow108 on 2010-09-04
same problem, you are not passing any options to the script

add this to catch your error:
```

if len(argv) != 2:
  print "usage script.py filename"
  exit()

```

---

