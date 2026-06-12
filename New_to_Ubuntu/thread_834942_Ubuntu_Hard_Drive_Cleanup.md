---
title: "Ubuntu Hard Drive Cleanup"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by bronco 2010 on 2008-06-20
I have a question regarding cleaning up my Ubuntu hard drive.

To make a long story short, I am managing my own business when I realize that there is no space on my dual boot Vista-Ubuntu machine.  After cleaning things up, there is 1 GB free.

I want to clean up more before I go to other alternatives (re-doing the partition is one), and I'm wondering if I can see on my system what is taking up the most space.  df in the terminal shows me what is taken up, but is there something in windows that can tell me what is taking up the most space?

Thanks in advance to responses.

---

### Post by bronco 2010 on 2008-06-20
I didn't know deleting the stuff from trash would be a big help.

The other question still counts through:  How do you see what files are taking up a lot of space?

---

### Post by Dynaflow on 2008-06-20
In Linux, Graphical Disk Map (gdmap in Synaptic) is a neat utility for visually showing what's taking up the most space.  Something similar for Windows would be SpaceMonger or SequoiaView.

---

### Post by bronco 2010 on 2008-06-20
Thank you.  I'll take a look at those.

---

### Post by philliptweedie on 2008-06-20
Try baobab in ubuntu, its installed by default in hardy at least. Its called something else though in the menus. It's in applications>accessories. It gives you a good idea of where all your ubuntu space is going.

Also, if you've done a lot of updates try sudo aptitude autoclean. It cleared out a ton of stuff for me that had been kept over after various updates.

---

### Post by Dynaflow on 2008-06-20
> **philliptweedie said:**
> ...

Also, if you've done a lot of updates try sudo aptitude autoclean. It cleared out a ton of stuff for me that had been kept over after various updates.

If you're running critically low on space (a *gig* is critically low?  that makes me feel old), I would recommend opening Synaptic, going to Settings -> Preferences -> Files [tab] and telling the system to "Delete downloaded packages after installation."

---

### Post by philliptweedie on 2008-06-20
> **Dynaflow said:**
>  (a *gig* is critically low?  that makes me feel old) 

lol. Also, thank you for the Synaptic tip, a much better way than typing in that command every few days!

---

### Post by shay1 on 2008-06-22
On windows machines I have used ExplorerXP, which is free, to investigate file sizes as it does what windows explorer doesn't. namely identify directory sizes.  

It will find all those files, especially the rubbish that Windows accumulates but even more so the restore points and backups. If you are using it for business you will be backing up daily presumably? (if not why not?:)) These will be generating very large files and keeping them on your hard drive. My guess is that it will be windows that is the main culprit in filling your drive - perhaps you would let us know what you find, please.

I downloaded it from the Computeractive magazine website in the UK but the program's website is [www.explorerXP.com](www.explorerXP.com)

Shay

---

### Post by nowshining on 2008-06-22
u actually have more than 1GB left - ubuntu/linux reserves X amount of disk space so ur able to login to linux/ubuntu incase of low hard drive space.

---

### Post by bred on 2008-06-22
[COLOR="DarkSlateBlue"]> **Dynaflow said:**
>  (a *gig* is critically low?  that makes me feel old) :)

thx for synaptic tip dude :)[/COLOR]

---

### Post by bred on 2008-06-22
[COLOR="Navy"]a good

HOWTO: Cleaning up all those unnecessary junk files...

[http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")[/COLOR]

---

### Post by sailor2001 on 2008-06-22
in hardy,  applications/accessories/disk usage analyzer to see where everything is

---

