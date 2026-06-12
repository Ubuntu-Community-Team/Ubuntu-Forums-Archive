---
title: "compiz: can you help me debug this error?"
date: 2009-08-27
forum: Programming Talk
---

### Post by PGScooter on 2009-08-27
Hi, I have found what I believe to be a small bug in compiz. I would love to learn how to debug this error for my learning purposes and because I think it could be underlying a bigger bug. I tried to install the -dbgsym package for what I think is the problem-causing package, but the compiz PPA does not have it, which leads me to believe that it is not used in debugging compiz (see output at end of post).

The bug: when playing the game maelstrom in fullscreen when compiz (even when no gnome-do and no plugins enabled), after about 20 minutes, the game is taken out of full screen and the window becomes unresponsive for 10-20 seconds. I do not experience this problem when compiz is not running.

Thank you!

```

jerome@system76-pc:~$ sudo apt-get install compiz-core-dbgsym 
[sudo] password for jerome: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-core-dbgsym: Depends: compiz-core (= 1:0.8.2-0ubuntu8) but 1:0.8.2-0ubuntu8.1 is to be installed
E: Broken packages
jerome@system76-pc:~$ 

```

note that I posted in the Desktop Environments section (and received no reply):
[http://ubuntuforums.org/showthread.php?t=1249998](http://ubuntuforums.org/showthread.php?t=1249998)

---

