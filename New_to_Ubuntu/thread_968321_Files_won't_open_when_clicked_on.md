---
title: "Files won't open when clicked on"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by lolwhites on 2008-11-02
Whenever I click on a file, it appears active for a minute (the "clock" signal), then nothing. To open any file, I have to open the program first, then navigate to the right directory, or use the command line.

This only happens on my account, not anyone else's on the same machine.

---

### Post by Crafty Kisses on 2008-11-02
Have you tried rebooting, and if you have did you get the same result?

---

### Post by lolwhites on 2008-11-02
Yes and yes.

---

### Post by oldsoundguy on 2008-11-02
> **Codename said:**
> Have you tried rebooting, and if you have did you get the same result?

+1

I have one box that either it is a flaky memory stick, or I am having very minor HD issues .. I find that I do have to re-boot it sometimes.  The other 3 Linux boxes, not so.  So it MAY be a hardware issue.  Especially when you get the "this has been rebooted x amount of times and needs to be checked" and then you get a HUGE list of things being fixed and asked if you want to fix them!! (but thank God it is Linux and it will fix itself .. with Windows, it would have to go to the shop!)

---

### Post by oldsoundguy on 2008-11-02
re-reading ... your permissions need to be re-set for your usage.

---

### Post by Crafty Kisses on 2008-11-02
What are the results of this command?
```
uname -r
```
I'm also thinking it could be a permission issue, but I'd like to see that command before going forward. I'm guessing you have the default Intrepid kernel (2.6.27-7-generic), but let's just see. I'd also like you to look in this directory:
```
~/.local/share/applications
```
To see what files do not work when you double click on them.

---

### Post by lolwhites on 2008-11-02
uname -r gives *2.6.27-7-generic*

None of the files in the directory you give will work when I click on them. That includes wine, vlc (appears five times, but only three with an icon), Theme Installer, System Settings, Seamonkey Composer, scalc (which, like other OOo applications, onlu open when the system's freshly booted), Python, Parley, Orca, mimeinfo.cache, mimeapps.lst, Menu Editor (which won't open when I right click on the menus), ksoduku, Khangman, gpicview, Firefox, defaults, Bug Report Tool, audacity and the wine folder.

---

