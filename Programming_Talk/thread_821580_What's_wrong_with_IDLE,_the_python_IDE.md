---
title: "What's wrong with IDLE, the python IDE?"
date: 2008-06-07
forum: Programming Talk
---

### Post by worc on 2008-06-07
I'm running IDLE on Ubuntu 8.04, I install it with
```
sudo apt-get install idle
```
Python version is 2.5.2
IDLE version is 1.2.2

All works fine except function invoking.
Say, the basic help() function, if I type in help(dir) and hit RETURN, nothing happens, and the keyboard seems to be locked inside IDLE. I mean no matter what I type afterwards, it looks like I typed nothing. The keyboard still functions well outside IDLE. 
To see the feedback of help(dir), I have to choose File->Print Window, then I see the pointer moves to the next line, and now if I hit RETURN again, it prints out the help info for "dir", and then my keyboard seems alive again!

Python interactive session works ok as expected. It seems that only IDLE doesn't like the tailing "()" of functions. I've tried several different functions, same issue happens every time I hit RETURN after typing in the function (like "somefunction(whatever)"). But, without hitting RETURN, how can I execute the function?


Really strange, isn't it? Or am I missing something?

---

### Post by worc on 2008-06-08
BUMP~~~

Did I explain this clear? Or no one has the same problem?

---

### Post by Smygis on 2008-06-08
I had so many problems with IDLE i quit using it a log time ago.
IDLE sucks. Thats why. Trys to be both a editor and some sort of interperter at the same time and fails at both. Sure it works if im only going to open a file and change some small thing. But i dont even want to use it for that
Use a real editor instead (SPE, geany, gedit).

And dont bump your threads.

---

### Post by loell on 2008-06-08
bumping your unanswered thread once in a while is just fine :)

you can also try [eclipse-pydev]("apt:eclipse-pydev") .

---

### Post by worc on 2008-06-09
Thanks for all the kind suggestions!

As IDLE is recommended by a lot of python learning books, I'd really like to try it out. 

Can anyone confirm the issue to me? I'm not even sure about if this is only happening to me!

---

### Post by rlameiro on 2008-06-09
I don't have that problem in here. same specs....
in the windows machine, also no probs.... but Im not an expert, just a begginer

---

### Post by gnuman on 2008-06-11
> **worc said:**
> Thanks for all the kind suggestions!

As IDLE is recommended by a lot of python learning books, I'd really like to try it out. 

Can anyone confirm the issue to me? I'm not even sure about if this is only happening to me!

Doesn't happen to me, and I have Python running on several Ubuntu computers and a neglected Windows box....

I've always installed IDLE via the package manager and make sure I choose the version that matches the version of Python I have installed.  For instance, 2.5 rather than the older IDLE for 2.4.

Edit: I see you have IDLE 1.2.2, so that should be fine.

Interesting post, btw.

---

### Post by amentajo on 2008-10-05
This is happening to me too.

It appears that this strange occurrence happens when the IDLE editor either highlights something (such as when parentheses close), and when it closes a tooltip (such as when a command is typed and parentheses are opened).  This phenomenon usually does indeed revive when a menu bar is clicked, but not always.  Sometimes I have to restart IDLE itself.  I have been having this problem in Ubuntu only (on GNOME), not Windows, in both 2.5 (IDLE 1.2.2) and 2.6 (IDLE 2.6).  My GNOME desktop effects are set to "None" (this sometimes seems to cause problems).

I installed 2.5 with Synaptic, and I compiled 2.6 from source.

---

### Post by sheto on 2008-10-25
This does not happen to me. I have the same version of IDLE installed. Maybe installing the Python-tk package will help.

---

### Post by magret55 on 2008-10-26
> **worc said:**
> Thanks for all the kind suggestions!

As IDLE is recommended by a lot of python learning books, I'd really like to try it out. 

Can anyone confirm the issue to me? I'm not even sure about if this is only happening to me!


I had the same problem with idle, except I had to restart idle to get the keyboard to start working in it again (it was fine everywhere else).

Do you run scim? 

I installed scim: this problem started happening.
I uninstalled scim: problem went away.

Coincidence? Doubt it.

---

### Post by Paul Miller on 2008-10-28
Try 
```

mv ~/.idlerc ~/.idlerc.old

```
What this does is move your idle settings to someplace idle won't look for them.  Then, next time you start idle, it should create the .idlerc directory anew with fresh settings.  If this fixes things to your satisfaction, you can then delete the ~/.idlerc.old directory.  If not, you still have the stuff in the directory available, should you want it.

---

### Post by qns8dn3 on 2008-11-17
I have the same problem with IDLE.
The problem disappear when I open IDLE without SCIM support.

To open IDLE without SCIM, open a terminal and enter following command:
```
GTK_IM_MODULE="" XMODIFIERS="" idle
```

---

