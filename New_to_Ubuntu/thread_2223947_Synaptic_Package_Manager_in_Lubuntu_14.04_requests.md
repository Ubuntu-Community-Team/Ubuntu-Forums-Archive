---
title: "Synaptic Package Manager in Lubuntu 14.04 requests disc be inserted"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by steve119 on 2014-05-13
I am trying to get a Netgear wireless USB antenna (Broadcom BCM43231 N-300) to work. In order to do that, some packages need to be installed, beginning with ndiswrapper 1.59 and ndisgtk. Firing up the Synaptic Package Manager and searching for the package (ndisgtk) does locate it but it also states that 15 other packages need to be installed. When attempting to do so it requests that the installation disc including (Trusty Tar) be inserted, but I can't get the drive to open to insert the disc I used to install Lub14, and even when it WAS in and I directed the manager to look there it claimed it couldn't find them on it. The disc was made at the local public library by the library staff for me so I don't know what is on it myself nor where to look for them. IF the SPM looks on the internet as well as local media, why isn't it looking on the net for the files? Assume for my sake that I don't know where the /home directory is much less where to find ndisgtk. (Read absolute NOOB, even in simple linux CLI codes. I know about a half dozen or so, mostly useless in this case.) Any non-judgemental information relevant to solving the ndis issues would be welcome, especially a step by step. If you need certain system responses in order to determine results, I could do that too, I just need to know what is relevant. Thanks in advance, I appreciate it. (Really)

---

### Post by oldrocker99 on 2014-05-13
Fire up Synaptic, and go to Settings/Repositories. A window called **Software & Updates** will open. Select **Other Software**. Make sure that the cdrom line is **un**checked. Close, and click on **Reload** to correct your repositories, and you **should** be OK.

---

### Post by steve119 on 2014-05-19
I did everything as you said, and it looks like it did what it was supposed to, and now that I have I know what to do if I need to reinstall something from the cd. Now I have to backtrack to see what I need to do to get the wireless to work. I've tried and retried bits and pieces but I don't see any function in the wireless antenna yet. Linux knows it's there as it is listed under** lsusb**, and **ndiswrapper** is "untarred" in one (or more) places, and I think **ndisgtk** is somewhere as well, but how to get it all "in the same room" working together is another story, probably another post as well. Thanks for your info, I appreciate it, as it did clear up a problem, and taught me something I can actually use.

---

### Post by Vladlenin5000 on 2014-05-19
[http://ubuntuforums.org/showthread.php?t=2221251&highlight=BCM43231](http://ubuntuforums.org/showthread.php?t=2221251&highlight=BCM43231)

---

