---
title: "[SOLVED] Desktop Icon Problem - PLEASE HELP!"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Sunshine1987 on 2008-11-20
If anyone can figure out this problem (or what I'm saying!) I would *really* appreciate it beyond belief!

While using Ubuntu 8.10, I logged in to find that all the folders inside my Home Folder (Documents, Examples, Music, Pictures, and Video) on my Desktop, for some strange reason.  I'm able to access the contained files now from both my new Desktop icons and on the top panel Places tab.  However, when I delete the newly added folders off of my Desktop, I'm no longer able to access the files from my Places tab.  If I add a new folder to my Home folder, it will immediately appear on my Desktop as well, and vice versa.  Could anyone explain how to remove these folders from my Desktop without losing my files and fix this problem?

The *only* recent change I made to my computer was downloading a ZoneAlarm firewall on my Windows XP partition - that's it.  I don't know if that could have any affect on my Ibex partition, but I turned ZoneAlarm off as a precaution.

---

### Post by CatKiller on 2008-11-20
Press Alt-F2 and run *gconf-editor*. Look for the /apps/nautilus/preferences/desktop_is_home_dir key and untick it.

---

### Post by ibuclaw on 2008-11-20
No, what happens in Windows does not affect Ubuntu and vice versa.

I had someone with the exact same problem as this quite a while ago, and to memory we resolved the issue. (let me just find it).

[EDIT]
OK, found it: here is the thread. [http://ubuntuforums.org/showthread.php?t=831508](http://ubuntuforums.org/showthread.php?t=831508)

But to save you having to read through it, can you just clarify something?

What is the name of the "Desktop" folder in your home directory?

And when I say name, I mean the **Exact Casing of the Letters**

Regards
Iain

---

### Post by Sunshine1987 on 2008-11-21
Thanks so much for the advice!  I really appreciate your helpful tips.  Unfortunately, neither of them seemed to work in this case, but your effort is still greatly appreciated!  I searched online for the problem and stumbled upon a thread marked "solved" that fixed the problem.  The link is as follows:

[http://ubuntuforums.org/showthread.php?p=5560476](http://ubuntuforums.org/showthread.php?p=5560476)

Thanks again!

---

### Post by ibuclaw on 2008-11-21
Thanks for the input. You are welcome and I'm glad you've resolved this.

I'll put that link in my notebook of problems/solutions :D


Regards
Iain

---

