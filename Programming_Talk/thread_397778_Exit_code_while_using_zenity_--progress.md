---
title: "Exit code while using zenity --progress"
date: 2007-03-31
forum: Programming Talk
---

### Post by musther on 2007-03-31
I have a bash script which does something like this:

```

command
if [ $? != "0" ]; then
bla bla bla

```

The problem is, I would like it to do this

```

command | zenity --progress --auto-close etc etc etc
if [ $? != "0" ]; then
bla bla bla

```

The problem with that is of course that $? will be returning the exit status of zenity, not my command, and zenity will exit with 0 even if my command fails with an exit != 0.

How do I go about this?

Thanks

---

### Post by Mr. C. on 2007-03-31
From man bash:

>        PIPESTATUS
              An  array  variable (see Arrays below) containing a list of exit
              status values from the processes in  the  most-recently-executed
              foreground pipeline (which may contain only a single command).
MrC

---

### Post by musther on 2007-04-01
Thank you very much, I'm still learning bash scripting (although I think I'm learning quite quickly), and although at first I thought your answer didn't contain enough information, it was the perfect amount to make me learn for myself, rather than just giving me the answer.

Thanks again.

---

### Post by Mr. C. on 2007-04-01
You're welcome.

MrC

---

### Post by kwaanens on 2007-04-02
> **musther said:**
> Thank you very much, I'm still learning bash scripting (although I think I'm learning quite quickly), and although at first I thought your answer didn't contain enough information, it was the perfect amount to make me learn for myself, rather than just giving me the answer.

I have been struggling with the exact same problem. Care to post your lines, that makes your case work. (I'm *not* learning quickly...)

- K

---

### Post by Mr. C. on 2007-04-02
You will easily find the solutions here in the forums: search PIPESTATUS.

If you are having trouble with shell scripting, perhaps this online shell scripting course will help:

[http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)

MrC

---

### Post by musther on 2007-04-02
Simply use the array variable PIPESTATUS like this:

```
if [ "${PIPESTATUS[*]}" != "0" ]; then
```

Where the * is the position in the pipe you want to read the exit status for, 0 being the first command in the pipe, 1 being the second, 2 being the third etc...

But yes, I sugges an online bash guide too, and the forums of course.  :-)

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by kwaanens on 2007-04-02
> **musther said:**
> Simply use the array variable PIPESTATUS like this:

```
if [ "${PIPESTATUS[*]}" != "0" ]; then
```

Where the * is the position in the pipe you want to read the exit status for, 0 being the first command in the pipe, 1 being the second, 2 being the third etc...

All I get with that is:
20: Syntax error: Bad substitution

---

### Post by musther on 2007-04-02
Here is a simple script which works, use it as your example.  If you have a problem running this script, then there must be something wrong somewhere else, if it works and your script doesn't, there must be a problem somewhere in your script.

```
#!/bin/bash
#
#Are you online?
#
ping google.com -c 5 | zenity --progress --text="Testing" --pulsate --auto-close
if [ "${PIPESTATUS[0]}" != "0" ]; then
zenity --error --text="Sorry, You do not currently have a fully working internet connection." --title="Error"
fi
exit
```

---

### Post by kwaanens on 2007-04-03
Allright!

I found out what made the difference. And I didn't even know that made one. The difference is in:
#!/bin/sh
or
#!/bin/bash
It does not work in the former, but does so in the latter.
Thanks!

- Ketil

---

### Post by musther on 2007-04-03
That determines which shell is to be used to execute the file, bash is (if I'm not mistaken) the most common these days, and it's the default shell you use when you open up a terminal window.  But there are many other shells, sh is a different shell, with different commands.

---

### Post by kwaanens on 2007-04-03
Yeah, I was aware, but didn't know that it made that much difference. That's a gotcha I need to remember.

---

