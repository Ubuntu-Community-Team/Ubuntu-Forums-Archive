---
title: "[SOLVED] Boot Problems... (Please Help Or I May Break Down)"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by laurielegit on 2008-07-11
I have had Ubuntu working for a while when I decided I should try an other linux distro. I first chose open suse, hated it and then tried fedora and didn't hate it quite as much. some were along the way I managed to muck up the booter and I now am only able to run of a live fedora CD.
Here's my hard drive set-up:
Primary: 150gb - ATA Hitachi - Formerly windows only, now a corupted version of fedora
Secondary: 280gb - Ubuntu only, not recognised by booter.
Here's a time line of my misfortune:

1.Ubuntu working fine

2.Move all windows files from Primary to Secondary drive (so i can replicate windows environment)

3.Guild wars refusing to work with Ubuntu so I install Open suse (kde)

4.Dislike open suse so install Fedora. (I was resizing the windows partition down so I could make room for fedora)

5.Halfway through install I get a power cut and have to restart.

6.Fedora installer no longer recognises that windows or Ubuntu exist.(Windows partition was being resized when the power cut struck, but why can't it see Ubuntu?)

7.Reinstall Fedora but muck it up somewhere along the way.

8.Write this post and then go and panic.

So currently my thinking is that I need to some how edit the boot loader and direct it towards the Ubuntu file system.

P.S. I still have all the files for Ubuntu and they appear to be genuine. I cannot access my video folder however which is extremely annoying as it contains most of my work.

P.P.S. If you need more information I will be happy to provide it, either IM me or post on the thread.

---

### Post by rockin_goliath on 2008-07-11
First of all, if you can access your personal data, back it up. Thumb drives and hard drives will still mount on live cds.

Second, try following the instructions here to restore grub. I have no experience with Fedora, so these instructions are for Ubuntu.

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Alldan on 2008-07-11
Download Super Grub Disk from here: 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
It is a livecd so burn it, boot from it and then select to boot from ubuntu partition (safe) or you can try to reinstall original ubuntu grub from ubuntu partition.

---

### Post by laurielegit on 2008-07-11
> **Alldan said:**
> Download Super Grub Disk from here: 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
It is a livecd so burn it, boot from it and then select to boot from ubuntu partition (safe) or you can try to reinstall original ubuntu grub from ubuntu partition.

I think I'll take this route... my only problem with it is that while using the live CD I can't write another (only 1 CD drive). I'll see whether my dads laptop burns... he claims not but I still have hope.i

---

