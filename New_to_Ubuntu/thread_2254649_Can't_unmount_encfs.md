---
title: "Can't unmount encfs"
date: 2014-11-28
forum: New to Ubuntu
---

### Post by pgslmatias on 2014-11-28
So I run Xubuntu on my computer and decided I should give encfs a try. So, I followed a tutorial and was able to create a mounting point and the folder to store the data. Everything was working fine, untill my Xubuntu experienced an internal error while I was copying some images to the folder. The screen just froze and the computer wouldn't answer any command, i.e., wouldn't shutdown manually, open terminal or anything. So, I waited untill the computer ran out of battery, charged it and started it. The mages are already in the folder, but I'm unable to unmount it. The name of the folder is mntpoint. When I ran the command I get the following error:  fusermount -u ~/mntpoint
fusermount: entry for /home/pedro/mntpoint not found in /etc/mtab
Why is this happening? I tried rebooting the computer but I still get the same mistake. Sorry if this seems like a stupid question I'm still a beginner at these things. Thanks;)

---

### Post by JeQhdMD on 2014-11-29
I don't know about the cause of the errors, but if you like encfs, it's much easier to manage if you install the front end control program "gnome encfs manager" . . . it may have it's own "ppa" (in other words, it's own repo vs the ubuntu software center).   But it really simplifies running encfs.  So, you might think about unistalling encfs first, then reinstalling and finally getting the deb file (just google gnome encfs manager).

---

### Post by pgslmatias on 2014-11-29
Well, Xubuntu doesn't use Gnome, maybe I'll install it via command line but I really like Xubuntu because it's faster, even though the resources aren't as good

---

### Post by mcduck on 2014-11-30
You don't need to run Gnome to use GEncfs Manager. It works just fine with XFCE (which shares fair amount of components with Gnome anyway)

---

