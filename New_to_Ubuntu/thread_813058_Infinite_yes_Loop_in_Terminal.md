---
title: "Infinite yes Loop in Terminal?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by DaltonAdair on 2008-05-30
I was screwing around in the Terminal today and decided to enter the command "yes", all by it's lonesome, among other random things.

(Dangerous I know, but this is a test machine I abuse radically on a near daily basis.)

At any rate, when that command is entered, the Terminal returns this:

y
y
y
y
y
y
y
y
y

Until I break operation. Any ideas what that is all about? I tried "no" as well, and nothing interesting happens.

---

### Post by Duck2006 on 2008-05-30
What was the command you answer yes to?

---

### Post by llamakc on 2008-05-30
Read about it here:

```
man yes
```

---

### Post by DaltonAdair on 2008-05-30
Okay, so "yes" by itself, as a command
( user@user-desktop:-$ yes )
is intended to put out a string of "y" endlessly. Thought maybe it was a quirk.

But what for?

---

### Post by Duck2006 on 2008-05-30
You should find the answer here.

> SEE ALSO
       The full documentation for yes is maintained as a Texinfo manual.  If the info and yes programs are properly installed at your site, the command

              info coreutils ’yes invocation’

       should give you access to the complete manual.

---

### Post by sisco311 on 2008-05-30
For example you can pipe or redirect yes into a command expecting user input.
*```
yes | rm -r dirname
```* has same effect as ```
*rm -fr dirname
```*

---

### Post by DaltonAdair on 2008-05-30
So, I can run a while loop with yes and then have a program ask for input from it? Automated yes? Interesting. I wonder why there isn't a loop for no as well. 

Anywhos, thanks for the info guys. :)

---

### Post by sisco311 on 2008-05-30
```
yes no
```or
```
yes To read the man page of yes type '"man yes"', without the quotes , in the terminal.
```:)

---

