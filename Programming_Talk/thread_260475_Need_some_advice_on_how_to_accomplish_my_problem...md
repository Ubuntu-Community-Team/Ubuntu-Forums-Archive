---
title: "Need some advice on how to accomplish my problem...."
date: 2006-09-18
forum: Programming Talk
---

### Post by MrMojoRising on 2006-09-18
Okay, so i have a problem that i'm blanking on how to solve. I'm hoping you brilliant Ubuntu'ers can help me.

I have a subtitle file which is basically a list of numbers on 1 line each followed by some text --- ie:

```
{3221}{3254}Goodnight, lady.
{3341}{3454}I know him. He lives|in the City.He will recognise us.
{3460}{3540}It is his boss'es|money.He doesn't care!
{3652}{3729}Aren't you|From the City of God?

```
How would I increase each number by X? ie: X=89771

Mind you this file is about 1000 lines long so manually going to each number and adding 89771 would be somewhat inefficient.

**Is there a simple perl/C/java script to parse the file and add a certain number to each number in each line?**

Even a bash command would work....

Thanks in advance for any and all help you guys/gals provide.

---

### Post by ghostdog74 on 2006-09-19
> **MrMojoRising said:**
> Okay, so i have a problem that i'm blanking on how to solve. I'm hoping you brilliant Ubuntu'ers can help me.

I have a subtitle file which is basically a list of numbers on 1 line each followed by some text --- ie:

```
{3221}{3254}Goodnight, lady.
{3341}{3454}I know him. He lives|in the City.He will recognise us.
{3460}{3540}It is his boss'es|money.He doesn't care!
{3652}{3729}Aren't you|From the City of God?

```
How would I increase each number by X? ie: X=89771

Mind you this file is about 1000 lines long so manually going to each number and adding 89771 would be somewhat inefficient.

**Is there a simple perl/C/java script to parse the file and add a certain number to each number in each line?**

Even a bash command would work....

Thanks in advance for any and all help you guys/gals provide.

here's one in Python:
```

import re #regex module
x = 89771
for lines in open("1000lines.txt"): 	
 	found = re.search(r"{(\d+)}{(\d+)}(.*)",lines).groups()
 	print "{" , int(found[0]) +  x , "}{" , int(found[1]) + x , "}" , found[2]

```

output:
```

{ 92992 }{ 93025 } Goodnight, lady.
{ 93112 }{ 93225 } I know him. He lives|in the City.He will recognise us.
{ 93231 }{ 93311 } It is his boss'es|money.He doesn't care!
{ 93423 }{ 93500 } Aren't you|From the City of God?

```

---

### Post by po0f on 2006-09-19
Not to steal your thunder, but here it is, scriptified:
```
#!/usr/bin/python

import sys, re

X = 89771

def main():
  try:
    # Open the file and get it's contents
    fd = open(sys.argv[1])
    lines = fd.readlines()
    fd.close()
  except IndexError:
    # If no file was specified on the command line, exit.
    sys.exit("No file specified.")
  except IOError:
    # If we can't read the file, or it doesn't exist, exit.
    sys.exit("Error opening/reading file.")

  for line in lines:
    # ghostdog74's re pattern
    found = re.search(r"{(\d+)}{(\d+)}(.*)", line).groups()
    print "{", int(found[0]) + X, "}{", int(found[1]) + X, "}", found[2]

if __name__ == "__main__":
  main()
```

I was trying to come up with a solution for this earlier but I suck at RE.  To use it, just type in a terminal:
```
$ python myscript.py somefile.txt > somefile2.txt
```

Also added some comments, so maybe someone will learn a little bit of Python as well.  If you have questions, ask.

---

### Post by MrMojoRising on 2006-09-19
wow guys! thanks a bunch, that's perfect.

Damn i really should've kept up on my programming skills.
I think i'll try to pick it back up again

---

### Post by MrMojoRising on 2006-09-19
Uh oh......actually not so perfect.

The output file can't have spaces around each number.

it's gotta be:

{1234}{5678}

Not:

{ 1234 }{ 5678 }

I tried as much as possible to fix the script you guys provided but i couldn't fix that problem......
**Do you guys know what's wrong?**

---

### Post by po0f on 2006-09-19
Here you go:
```
#!/usr/bin/python

import sys, re

X = 89771

def main():
  try:
    # Open the file and get it's contents
    fd = open(sys.argv[1])
    lines = fd.readlines()
    fd.close()
  except IndexError:
    # If no file was specified on the command line, exit.
    sys.exit("No file specified.")
  except IOError:
    # If we can't read the file, or it doesn't exist, exit.
    sys.exit("Error opening/reading file.")

  for line in lines:
    # ghostdog74's re pattern
    found = re.search(r"{(\d+)}{(\d+)}(.*)", line).groups()
    print "{%d}{%d}%s" % (int(found[0]) + X, int(found[1]) + X, found[2])

if __name__ == "__main__":
  main()
```

I tested it, so it should work.  Sorry, I didn't think the spaces were going to be a problem.

---

### Post by MrMojoRising on 2006-09-19
Spot on, Thanks a million.

---

