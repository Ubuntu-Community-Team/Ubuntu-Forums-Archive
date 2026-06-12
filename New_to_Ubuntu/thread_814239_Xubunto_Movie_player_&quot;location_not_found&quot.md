---
title: "Xubunto Movie player &quot;location not found&quot;"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by bryont on 2008-05-31
Hello,
I am new to linux.  Loaded Xubunto on a machine and it is working farily well.

However I can not seem to get Totem movie player to find any music CD's.

There are two drives, CD and DVD.  Both can can be found by the file system.

But Movie player says "location not found" when trying to play a music cd.

Whats the best resources to read and where to look to find a solution.
Thanks
BT

---

### Post by quelx on 2008-05-31
Not a fix per se, but you should be able to listen to you CDs

[http://ubuntuforums.org/showthread.php?t=662735](http://ubuntuforums.org/showthread.php?t=662735)

---

### Post by bryont on 2008-06-01
I don't know enough yet to understand the fix.  When I tried to give the command in the terminal window I received error

:~$ mplayer -cache 10000 cdda://
The program 'mplayer' can be found in the following packages:
 * mplayer-nogui
 * mplayer
Try: sudo apt-get install <selected package>
bash: mplayer: command not found

---

### Post by sayakb on 2008-06-01
You can use Rhythmbox (Applications->Sound and Video->Rhythmbox music player) to play music CDs. Make sure you have the ubuntu-restricted-extras package installed.

---

