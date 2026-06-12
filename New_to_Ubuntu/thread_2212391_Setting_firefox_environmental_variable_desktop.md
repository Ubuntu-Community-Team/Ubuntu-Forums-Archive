---
title: "Setting firefox environmental variable desktop"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-03-21
Hi, 

webgl hardware acceleration no longer works for FF28. Following  [https://bbs.archlinux.org/viewtopic.php?pid=1394765](https://bbs.archlinux.org/viewtopic.php?pid=1394765) I put "export MOZ_USE_OMTC=1" in .bashrc. But this only works if I start Firefox with the command line.

I am wondering if there is a way to set this environmental variable so that Firefox would use it even if launched from the gui.  I know I can set env in the .desktop file but the downside is that it will get erased on update and FF updates quite often. Is there a more permanent way of doing it?

Edited: putting 'export MOZ_USE_OMTC=1' or  'MOZ_USE_OMTC=1' in ~/.mozilla/firefox/profiles.ini does not work.

---

### Post by monkeybrain20122 on 2014-03-21
OK, here is a way but kind of clumsy, hope someone may come up with a better method.

Copy /usr/share/applications/firefox to ~/.local/share/applications. Change the command of the local copy to 
```
env MOZ_USE_OMTC=1 firefox %U
```
and pin that to the Unity launcher instead of the original one. So it won't get updated.

Catch is now there is another Firefox in the dash and it is the original one.

Edited: need to change the name too as otherwise the original launcher would be used, apparently system got confused. So I renamed it to 'Firefox" (without "Web Browser")

---

### Post by deadflowr on 2014-03-21
Try the launcher way you were thinking of doing, but save it to ~/.local/share/applications.
.desktop files in here don't get overwritten when updates come through.
Problem is it would be per-user, so multi-user setup would need it to be moved into multi-users home folders.
Just a thought.

***Edit:*** Did you read my mind?

---

### Post by vasa1 on 2014-03-21
If you have your .desktop file in ~/.local/share/applications it will survive the update.

Aargh! Ninja'ed :(

---

### Post by deadflowr on 2014-03-21
> **vasa1 said:**
> If you have your .desktop file in ~/.local/share/applications it will survive the update.

Aargh! Ninja'ed :(

By the OP.:lolflag:

But you should be able to unpin the original one.
for something like this where I'm not sure which one I am using I rename the launcher
to something like My Firefox in the Name = line in the launcher.
That a way I know it's the right one.

---

### Post by monkeybrain20122 on 2014-03-21
> **deadflowr said:**
> By the OP.:lolflag:

But you should be able to unpin the original one.
for something like this where I'm not sure which one I am using I rename the launcher
to something like My Firefox in the Name = line in the launcher.
That a way I know it's the right one.

The original one is unpinned but it is in the dash. The new one is not since it is pinned to the dock. :) They have to have different names, so the new one is "Mozilla Firefox Web Browser" instead of just "Firefox Web Browser" :)

---

### Post by coldcritter64 on 2014-03-21
> **monkeybrain20122 said:**
> Hi, 

...Following  [https://bbs.archlinux.org/viewtopic.php?pid=1394765](https://bbs.archlinux.org/viewtopic.php?pid=1394765) I put "export MOZ_USE_OMTC=1" in .bashrc. But this only works if I start Firefox with the command line....

Instead of ~/.bashrc try adding the export command line to the end of the ~/.profile file, do a log out and then back in and see if the variable sticks, use "echo $MOZ_USE_OMTC" and the terminal should return "1" with the variable set this way correctly. Then test if your browser uses it when started up. Saves messing with desktop config files.

---

### Post by monkeybrain20122 on 2014-03-21
> **coldcritter64 said:**
> Instead of ~/.bashrc try adding the export command line to the end of the ~/.profile file, do a log out and then back in and see if the variable sticks, use "echo $MOZ_USE_OMTC" and the terminal should return "1" with the variable set this way correctly. Then test if your browser uses it when started up. Saves messing with desktop config files.

Hi, it works! That is the kind of solution I was looking for. Thanks.

I am marking this thread as 'solved'.

---

