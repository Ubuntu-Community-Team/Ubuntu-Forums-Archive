---
title: "[SOLVED] Error with X server and bashrc"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-21
Hi, all:

I've had this problem before, and I still haven't figured out how I solved it the first time, or why it's not working this time.  

root@tarahmarie-desktop:/home/tarahmarie# kdesu krusader
No protocol specified
kdesu: cannot connect to X server :0
root@tarahmarie-desktop:/home/tarahmarie# DISPLAY=:0.0 xhost +
No protocol specified
xhost:  unable to open display ":0.0"


I set the path for x in /root/.bashrc as:

#Tarah added this in on 9/21/08
export PATH=$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/bin/X11:/usr/X11R6/bin

WTF??

---

### Post by nowshining on 2008-09-22
try removing the .Xauthority files in ur home folder and logout and backin, what version of kubuntu are u running, what is ur KDE version?

if ur running gutsy and using the default 3.5.8 try updating to 3.5.9 from the kde site and it should fix many issues, as it did mine when i had similiar troubles..

---

### Post by tarahmarie on 2008-09-22
I removed the Xauthority file; apparently a new one was generated when I logged back in.  I'm running KDE 4.1.1, Hardy 8.04.  Take a look at this:

~ : Yes, Supreme Empress? $ kdesu krusader
passprompt


kbuildsycoca running...

DCOP Cleaning up dead connections.

~ : Yes, Supreme Empress? $ krusader
~ : Yes, Supreme Empress? $ su
Password: 
/home/tarahmarie: Darth Prompt (8<| # cd ..
/home: Darth Prompt (8<| # cd ..
/: Darth Prompt (8<| # krusader
No protocol specified
krusader: cannot connect to X server :0
/: Darth Prompt (8<| # 


It seems to only have a problem when I'm in root.  What would I have done differently?

---

### Post by tarahmarie on 2008-09-22
bump

---

### Post by nowshining on 2008-09-22
is this program from the repos?a did you install/compile it manually?? have u done any updates lately??

---

### Post by Mornedhel on 2008-09-22
> **tarahmarie said:**
> root@tarahmarie-desktop:/home/tarahmarie# kdesu krusader

Could you try kdesu krusader from a non-root shell ? (Why do you need kdesu when you're root already anyway ?)

---

### Post by tarahmarie on 2008-09-22
the problem is that the X server isnt' working properly when I'm root.  I should be able to start krusader as root, and I can't, like you all see in the output above.  How do I fix that?

---

### Post by Mornedhel on 2008-09-22
I recently switched back from a Kubuntu installation to Ubuntu, but I remember having the same problem. Starting Krusader with kdesu should give you administration rights though, no need to log in as the actual root user.

I too was a bit confused at first since I was used to starting GUI applications (not graphical sessions, mind you !) as root before Hardy. In Kubuntu 8.04 it seems like it's been made impossible. (Still possible in Ubuntu.)

---

### Post by tarahmarie on 2008-09-22
Ah, so the problem isn't that I don't know how to get X windows to open in root, the problem is that one CANNOT start X windows as root?

---

### Post by Mornedhel on 2008-09-22
That's what it looks like for Kubuntu. Still works on Ubuntu :

```
mornedhel@vega-laptop:~$ su
Password: 
root@vega-laptop:/home/mornedhel# synaptic
```Works like a charm. At first I tried the same thing you did on Kubuntu, since I was used to it working on Gnome. Su'ing as root then trying to start adept-manager returned the same error message. kdesu adept-manager worked, though.

Also, remember that root is not supposed to use GUIs at all. If you need administration rights, use sudo for console applications and gksu (kdesu in your case) for GUI applications.

---

### Post by tarahmarie on 2008-09-22
Ah.  Thanks for explaining it to me.  I was having trouble with some file permissions that were tough to reset unless I could be root and open a file manager.

---

