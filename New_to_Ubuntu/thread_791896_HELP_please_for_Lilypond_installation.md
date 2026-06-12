---
title: "HELP please for Lilypond installation"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Giffo on 2008-05-12
Hi, still a newbie with Ubuntu here - I have a problem with Lilypond.  I have tried several times to install and run it - usually having to de-install etc.. and try (yet) again.  I have used Lilypond on another laptop some time ago and it was great but, it seems there is a lot of traffic regarding the difficulties installing/running et al..   

I have just now downloaded and installed (I think... it says it is there!)  from the Ubuntu site but cannot run this even from terminal.It all seems to be there. Is there a simple 'newbie' document somewhere that will enable m to get this up and running please anyone??

Thanks!  Giffo

---

### Post by mirceade on 2008-05-12
Just tested the install on a 8.04 and it seems to work.

Software is usually installed in Linux/Ubuntu not by downloading it from the official site (as you usually do in Windows based OSes) but through a software repository. This way software is automatically updated throughout the system whenever it is changed by the authors. Use Aplications/Add Remove and select lilypond. 

Try "sudo apt-get install lilypond" in a console if Add/Remove doesn't work for you. 

**Make sure before doing that, that the Universe repository is enabled in System/Administration/Software sources.**

But if you already knew that... there isn't much else I can do for ya.

---

### Post by Giffo on 2008-05-13
Thanks so much for your help mirceade... I have now got Lilypond (aledgedly) installed with the icon where it should be but, problem I had before is still there with the message when clicking on the icon

Could not launch menu item
Failed to execute child process
"Lilypond" (No such file or directory)

The problem I have had is when I have downloaded this before I did not get the icon but the folder was visible with the files.  Now, it is in the menu but... still can't run it.  Great programme (I ued it on a colleagues machine) but frustrating beyond belief here....

Yourhelp is much appreciated!  Thanks!!!

---

### Post by ocarinahuff on 2008-08-12
I need help installing Lilypond.  I get dependency errors when it tries to install texlive and related packages.  I tried 'sudo dpkg --configure -a' and 'sudo apt-get install -f', even reinstalled it after using apt-get autoremove, autoclean and clean.  The dependency problem is driving me nuts!  Please help!!!

---

