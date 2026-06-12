---
title: "Shell Shocked from shell scripts"
date: 2009-08-03
forum: Programming Talk
---

### Post by lile001 on 2009-08-03
I am pretty new at shell scripts, having written two, one of which actually worked.  Now I'm trying to figure out why this doesn't work suddenly. 

I have a simple shell script called junk.sh, containing the classic line:

echo "Fear not our robot overlords"

I have run 

chmod 775 junk.sh
and
chmod +x junk.sh. 

When I type "junk" or "junk.sh" at a terminal, in the same directory, I get:

bash: junk: command not found

Now, I am sure that I did this successfully once before, making a little script that actually did something.  What does it take to make this script executable?

---

### Post by pizmooz on 2009-08-03
try adding as the very first line of your script:
```
#!/bin/bash
```

it is the 'she-bang', it determines what interpretor runs the scripts

---

### Post by benj1 on 2009-08-03
also you need to use ./junk.sh

unless youve exported the path in your .bashrc
ie
export PATH=$PATH:/home/user/bin

---

### Post by lile001 on 2009-08-03
> **pizmooz said:**
> try adding as the very first line of your script:
```
#!/bin/bash
```it is the 'she-bang', it determines what interpretor runs the scripts

Hmm.  Robot overlords are still winning.  Here's the script:

#!/bin/bash
echo "Fear not our robot overlords."

and the result is

bash: ./junk.sh: /bin/bash^M: bad interpreter: No such file or directory

---

### Post by kayvortex on 2009-08-03
Well,

> bash: ./junk.sh: /bin/bash^M: bad interpreter: No such file or directory

means that your shell can't find the interpretor that you requested -- i.e., /bin/bash can't be found on your system.

What does,
```
echo $SHELL
```
print out?

Edit: **forget that**, I've spotted that "^M" in the output you posted. What editor are you using to write that script? "^M" is usually the result of editing MS-DOS text files since Microsoft uses a different convention for indicating the end of a line in a text document.

---

### Post by jpkotta on 2009-08-03
Yes, CRLF line endings will muck up a shebang line.  You need Unix (LF) endings.  Look at the tofrodos package, and you probably want to configure your editor to save with Unix line endings.

---

### Post by lile001 on 2009-08-03
> **kayvortex said:**
> Well,



means that your shell can't find the interpretor that you requested -- i.e., /bin/bash can't be found on your system.

What does,
```
echo $SHELL
```print out?

Edit: **forget that**, I've spotted that "^M" in the output you posted. What editor are you using to write that script? "^M" is usually the result of editing MS-DOS text files since Microsoft uses a different convention for indicating the end of a line in a text document.


Ah that's it.  I was playing around with Wine yesterday and now Notepad is infesting my system.  I didn't pay attention to what editor pops up.  gedit fixed it.

---

