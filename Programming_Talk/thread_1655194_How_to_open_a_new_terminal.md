---
title: "How to open a new terminal"
date: 2010-12-29
forum: Programming Talk
---

### Post by rmariappan on 2010-12-29
Hi everyone,
   I am trying to develop a  new command line chat application in c. 
For that i need to open a new terminal to continue chatting in that window and keeping that main menu in the previous window. But i dono how to open a new window in C. Is there any way to do so...
Thanks in advance..:lolflag:

---

### Post by r-senior on 2010-12-29
> **rmariappan said:**
> I am trying to develop a new [COLOR="Red"]command line[/COLOR] chat application in c.
So GTK+ isn't what was being asked for.

What about fork/exec?

[http://en.wikipedia.org/wiki/Fork-exec](http://en.wikipedia.org/wiki/Fork-exec)

Running a new xterm or gnome-terminal becomes os-specific of course.

---

### Post by hakermania on 2010-12-29
"But i dono how to open a new window in C"

---

### Post by ziekfiguur on 2010-12-30
Like r-senior said, you could use fork/exec. 
An easier way would be to use something like ```
system("xterm -e yourchatprogram");
```
However, this will block the execution of the calling program as long as the new terminal is running, so it might not be what you want.

Or maybe you could try to build some kind of wrapper around the screen command.

If you don't want to start a separate program, I think you will have to use a GUI toolkit like GTK+ or QT.

@hakermania Please read section II point 16 of the forum code of conduct. :(

---

### Post by hakermania on 2010-12-30
> **ziekfiguur said:**
> Like r-senior said, you could use fork/exec. 
An easier way would be to use something like ```
system("xterm -e yourchatprogram");
```However, this will block the execution of the calling program as long as the new terminal is running, so it might not be what you want.

Or maybe you could try to build some kind of wrapper around the screen command.

If you don't want to start a separate program, I think you will have to use a GUI toolkit like GTK+ or QT.

You can use ```
system("xterm -e yourchatprogram**&**");
```This will just launch the xterm.
> **ziekfiguur said:**
> @hakermania Please read section II point 16 of the forum code of conduct. :sad:
I was more polite than just telling to google about GTK+. I give him a solution that doesn't include writing. :/ If this was rude, sorry!

---

### Post by rmariappan on 2010-12-31
Wow well Thanks to all of you,
I am sorry for not asking question much clear.
I need to open a new terminal only not  a GUI window.
@r-senior: Ya i tried fork and exec but it creates a new process in the same terminal i want to made it in  new termianl

@[ziekfiguur]("http://ubuntuforums.org/member.php?u=960698"): Thanks for the great command. I found a way to go around that short coming. i forked a new process and from that i call system("xterm..."). So that the new process does nt need to wait for it. 
Once again Thank you all.

I have one more doubt. Is "xterm"  will be available in all versions of linux ie even in tiny core linux, so that i can made the code work in all linux distributions,.

---

### Post by ziekfiguur on 2010-12-31
Actually the system function also calls fork and exec. If you call exec with "xterm" "-e" and "yourchatprogram" as commands it will open a new terminal. 
System actually calls fork and exec *twice* because the command is executed through /bin/sh.
So calling fork and exec and then system is very redundant, instead you could better use just system with hakermania's command "xterm -e yourchatprogram &".
Or, even better, just fork then ```
char * cmd[] = {"/usr/bin/xterm", "-e", "yourchatprogram", NULL};
execv(cmd[0], cmd);
```

As far as i know xterm will be available on every version of linux, other terminals like gnome-terminal or konsole may not be available.

---

### Post by rmariappan on 2010-12-31
Thanks to all of you
My doubts are over, Will meet you with more doubts soon..
Thanks..
Wish you all have a happy and prosperous new year...

---

### Post by trent.josephsen on 2010-12-31
"All" versions of Linux don't even have Xorg, and of those that do (or make it available), many don't install xterm with it.  Arch and Gentoo both work fine without xterm installed.

One way to solve this is to make a launcher that searches at startup for some kind of terminal application -- you could even provide it as an option on the command line -- and launches the interactive menu (plus children) in that application.  That way you can launch it as you would a real GUI program.

---

### Post by ziekfiguur on 2011-01-01
Maybe check if the TERM environment variable has been set.  In ubuntu it's set to xterm by default.  But I don't think every OS does that either.

---

### Post by rmariappan on 2011-01-02
> **trent.josephsen said:**
> 

One way to solve this is to make a launcher that searches at startup for some kind of terminal application
Would you please explain that clearly,,, launcher means i cant understand whether you telling about program launching or system startup..

> **trent.josephsen said:**
> 
you could even provide it as an  option on the command line -- and launches the interactive menu (plus  children) in that application.  That way you can launch it as you would a  real GUI program.
What to provide as an command line.. 
Please don anger if the questions are stupid.. I am a beginner in programming....

---

### Post by llawwehttam on 2011-01-02
CLI chat for linux? You might want to have a look at finch. Its a CLI version of pidgin.

---

### Post by ziekfiguur on 2011-01-02
> **rmariappan said:**
> Would you please explain that clearly,,, launcher means i cant understand whether you telling about program launching or system startup..
A simple shell script that searches for available terminals and starts one. From your program you could then start the launcher instead of for instance xterm.

> **rmariappan said:**
> 
What to provide as an command line.. 
Please don anger if the questions are stupid.. I am a beginner in programming....
The name of a terminal program. That way the user could specify what kind of terminal your program should use.

---

### Post by trent.josephsen on 2011-01-02
Quite so.

What I'm getting at is to determine the program you want to start (gnome-terminal, konsole, xterm, whatever) at run time rather than compile time.  Something like (pseudocode)
```
if gnome-terminal is available
    run gnome-terminal -e yourprogram
else if konsole is available
    run konsole -e yourprogram
else if xterm is available
    run xterm -e yourprogram
else
    print "Sorry, I can't find a terminal application."
```

You could do this as a separate launcher, probably a shell script as ziekfiguur mentioned, or you could hard-code it into your program.

---

### Post by rmariappan on 2011-01-03
@ziegfiguur and  @ trent.josephsen : Oh Thanks.. Got it.

---

