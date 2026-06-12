---
title: "Reading Program Output"
date: 2007-06-11
forum: Programming Talk
---

### Post by Pru on 2007-06-11
Hi, I'm relatively new to programming in Linux, I've made a few small python apps but nothing too complex.

I now want to make a program that would read the output of a program (what would usually show up in a terminal if i were to run it from there) and output it onto my g15 screen.

I know how to output to the g15 screen, but I don't know how to read the program's output and I don't know where to start.


The main program I'm hoping to use this with is Quake 3.

---

### Post by CptPicard on 2007-06-11
Well, doing it the Linux way, you'll just pipe the program's output into your python script and read it in the script from the standard input. Thus:

```

mybox$ someprogram | python yourscript.py

```

And in yourscript.py

```

import sys

for line in sys.stdin:
  print line  # or whatever you do with it

```

---

### Post by RawMustard on 2007-06-13
I'm interested in this also, can this be done live?  I mean can I run a script in a terminal and then see what another script or program is sending to it in real time?  Am I making sense?

---

### Post by Pru on 2007-06-17
> **CptPicard said:**
> Well, doing it the Linux way, you'll just pipe the program's output into your python script and read it in the script from the standard input. Thus:

```

mybox$ someprogram | python yourscript.py

```

And in yourscript.py

```

import sys

for line in sys.stdin:
  print line  # or whatever you do with it

```

I've tried this in so many different ways and I can't get it to work, is there any links that would be of use or what I should google for?

---

### Post by CptPicard on 2007-06-17
To the question of whether this is real time... yes this works real time. You may want to make  sure you're flushing stdout in your outputting program regularly though, otherwise you'll get the output in chunks of buffer size.

And as to why this doesn't work.. hmm... I really would appreciate more information of why and what exactly is not working. Piping standard output into another process' standard input is such a basic piece of shell functionality that I have a hard time understanding how it can go wrong ;)

My example should pretty much work as it is, you can try it by for example cat'ing a text file into the script I gave -- it should just pass it through into the terminal normally. If you want to google for something, you might try "bash pipes" for the associated concepts... and "reading standard input in python". I think the latter search was what I used to check the exact syntax for stdin for my last post.

---

### Post by Smygis on 2007-06-17
```

import commands

print '"uname -a" from inside python'
uname = commands.getoutput("uname -a")
print uname

```

gives the output:
"uname -a" from inside python
Linux Bob 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686 GNU/Linux


EDIT: Oh, You want it to read the output while the app is running. eg displaying the output from quake3 on the g15.  *someapp > deviceforoutput*
Or perhaps making q3 to write output to a file and then have the python app to read it.

---

