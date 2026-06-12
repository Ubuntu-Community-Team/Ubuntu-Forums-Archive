---
title: "Newbie : Eclipse + Java"
date: 2005-05-26
forum: Programming Talk
---

### Post by butterball23 on 2005-05-26
This is what I want to do:

I'm trying to use Eclipse IDE with CDT (C/C++) plug-in with Ubuntu and Windows 2000/XP. (develop on both platforms with the same IDE).

I'm using Eclipse 3.1 M7 (Milestone 7) with the compatible CDT plug-in.
(Its faster than the 3.0.x series)

Obviously, I need Java Runtime Environment to make Eclipse work. I had issues with ver 1.5 series, so I went with 1.4.2 series, and its fine. (In Windows).

The problem now is that, in Ubuntu, after reading the Wiki (setting up respository, installing Java, and Eclipse), and going through all the stuff...Eclipse throws up an error. :( (So close to the finish line! D'OH!)

The error message is :

[b]_Error_
*The Eclipse executable launcher was unable to locate its companion startup startup.jar file (in the same directory as the executable).*[/b]

(But the startup.jar file is there!)

What's causing this issue?
Should I start again?

Thinking that it could be Eclipse 3.1, I tried using Eclipse 3.0.2 and the same message appears. :(

Any suggestions? 
( Don't worry, I'm not afraid of the command line. :) )

---

### Post by jerome bettis on 2005-05-26
try running it as root once just to see if it will go.  it sounds like it might be a permissions issue.

---

### Post by jerome bettis on 2005-05-26
[QUOTE=butterball23]( Don't worry, I'm not afraid of the command line. :) )[/QUOTE]

then just use vim and Makefile instead.  it's nice once you get good at it.

---

### Post by butterball23 on 2005-05-26
[QUOTE=jerome bettis]try running it as root once just to see if it will go.  it sounds like it might be a permissions issue.[/QUOTE]

How do I go about doing this in Ubuntu?

---

### Post by butterball23 on 2005-05-26
Well, I logged in as root user, tried to run Eclipse...Same problem.

So it looks like something else. Hmmm.

OK...Let's simplify the situation.

This is what I did.

(1) Install JRE 1.4.2 based on instructions here.
=> [http://java.sun.com/j2se/1.4.2/jre/install-linux.html](http://java.sun.com/j2se/1.4.2/jre/install-linux.html)

(2) I then use this..(Terminal window).
[b]export JAVA_HOME=/usr/local/j2re1.4.2_08; 
export PATH=$JAVA_HOME/bin:$PATH[/b]

(3) I uncompressed Eclipse 3.1 M7 into a folder called "eclipse" in **/opt**

(4) I double-clicked on "eclipse".

(5) The splash screen appear! :D

(6) But then an error popped up telling me I should view some log file! :(

Log is telling me that the location I put Eclipse directory doesn't support "file locking" feature. ??? :(

---

### Post by butterball23 on 2005-05-26
What a pain in the ASS!

The file locking issue turns out to be an age old problem that some people may encounter when using Eclipse.

To disable the file locking thing, run Eclipse as follows :
**eclipse -vmargs -Dosgi.locking=none**

I tested this in a Terminal window in root mode...SUCCESS!

I GOT THE SON OF A B*TCH TO WORK! :D :D :D :D

---

### Post by nomad311 on 2005-07-23
ha NEVERMIND ...i dled the x86_64 ...hey its 6:30am here ...getting the right one 

should work!

-nomad311

---

