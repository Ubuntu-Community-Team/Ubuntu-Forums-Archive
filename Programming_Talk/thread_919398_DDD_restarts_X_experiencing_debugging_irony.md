---
title: "DDD restarts X :experiencing debugging irony"
date: 2008-09-13
forum: Programming Talk
---

### Post by RU-In? on 2008-09-13
Has anybody had problems with DDD? I installed DDD from synaptic and when started, it crashes the X desktop, goes to login screen. Im not sure it is actually crashing X, but it behaves the same as a ctl-alt-bkspc. When logged back in, I can see that DDD is still running (using the system monitor) and so I kill it.

I run 'ddd --check-configuration' and it tells me that it cannot find 'XKeysymDB'. I do a 'locate XKeysymDB' and I find that it is located in the '/usr/share/X11/XKeysymDB', so I add 'XKEYSYMDB="/usr/share/X11/XkeysymDB" to the /etc/environment file. I run 'ddd --check-configuration' again, and its happy (so it reports). DDD (or one of its children or something) still crashes the display, and now the keyboard won't work in X session, so go to another term. (keyboard works on tty1, etc.) and remove the environment var.,...the keyboard is back in the X (tty7). Gave up on that route...

I tried installing from source, but the dependencies where getting to be ridiculous (for me at least, one after another) but I installed them anyway, mostly the Motif & lessif stuff, all to do with X libs, I did finally get configure script happy but make didn't like it at all, aborted...

Found a .deb package over at debian, the dependency in that package is old (libstdc++4xx), and wants to revert to older versions of gcc if I go to install the lib, so I did not. Aborted...

The irony here is that I wanted to install that package to learn more about debugging. I've been trying to (finally) run down a few packages that are broke, like xsane, pulseaudio (pa screws up often..I removed it), and a couple others. I am not good at debugging (yet), so I wanted to learn to use some tools like GDB (maybe I should use that on DDD), and Strace too, and all about the /proc files. I was following a book 'self service linux' (only up to the intro where it is suggested that I install ddd. Im think of not using it, but It looked pretty nifty.

Lets see...I am using Hardy on a P4 w/ HT. Have an NVidia GForce 6200 w/ proprietary drivers. My syslog does not say anything about the xserver (surprisingly enough), thats why Im not really sure it is an actual crash of X (maybe something to do w/ Xkeys sending a sig?). Also the ddd log does not report anything wrong either. When I run DDD I do see the splash and then the window for about 1 second, and then it is as if I reset w/ a ctl-alt-bkspc, except when logged back in, ddd is still has a process, but nothing else in the session is up.

---

### Post by dwhitney67 on 2008-09-13
It's odd that DDD (ddd) would do that (crash X).  What were you debugging... a simple app or one that controls/interfaces with X?

You need to be wary of debugging applications that require event notifications to properly operate.  The debugger will suspend the process as it steps through each instruction.  Probably not the most desirable situation if you are debugging an X application.

---

### Post by RU-In? on 2008-09-14
1st, thanks for a fast reply...

> What were you debugging... a simple app or one that controls/interfaces with X?
I actually was not debugging anything, yet. I had just installed DDD, and went to run it and see what it looks like, and verify the install (habit). Thats when all of this began . This happened today. Thats why I actually decided to post the issue (My first time BTW, I usually can search out a solution in the 2 1/2 yrs. of Linux) because I considered it more of an install/dependency issue (or a problem of one of the dependencies..like maybe the debugger it calls) thats an idea...but I can run GDB in a term just fine, although I haven't had it do anything yet. Thats is also why I say 'irony'...I was installing tools, trying to anyway, to hunt down an issue, and in turn created a whole new one :) Luckily, I like problems..or at least I like problem solving (nobody likes 'problem' per se)

What I would like to work on first is Xsane (actually the backend I'm pretty sure), or whatever child is causing problems. Xsane (since feisty) has caused a seg. fault right after choosing a scanner...but that is prob. for another post I'm sure. I thought that would be a good start for me though.

The plot will thicken, so to say, if I find that others are running a simular system and not having any problems like this with DDD.

Probably, in all practicality, I should just move on and use the cdb (curses version), or just work w/ Strace and GDB...but this is bugging me. I also have a fairly clean system, I reinstalled the from the CD just around 3 weeks ago, and (this time) I am keeping better track of what I install. There is nothing that is not from the repos yet, except a few binaries in my home folder, that run in place.

Thanks

---

### Post by dwhitney67 on 2008-09-14
I wish I could help, but I don't have a clue.  Perhaps you could consider uninstalling DDD and then installing it again.  But I'm not sure if this will buy you anything.

For what it is worth, I have zero-trouble running DDD version 3.3.11 (i486-pc-linux-gnu).

---

### Post by RU-In? on 2008-09-14
I really appreciate your effort, Thanks. 

I did reinstall from the repos (about 4 times in all). I even reinstalled just so I could reproduce some of the responses in order to give an accurate description in this thread. Plus as I mentioned too, I attempted to install two other ways, source & .deb package, both without success.

I think I will try to reinstall DDD, create a new account and login, and then execute DDD to see what happens (maybe not in that order). That could be an easy indication, if it works in a fresh account...then at least I know its my settings, or if it does not work, then I know that its most likely system wide (I would guess).

Whatever I find out, I will post back here. That way anybody in the future that has a similar issue can use any of my findings, or the advice of anyone else that may participate in this thread.

Thanks

---

