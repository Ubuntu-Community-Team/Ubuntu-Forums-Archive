---
title: "since I used Wubi, is it possible to use those files to install Ubuntu on another cpu"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-06-14
and would it be possible to delete Windows XP off of it? its not my main computer, and I absolutely abhor windows XP. Even if I cant delete XP while using the wubi files, is it possible to copy the files from this pc, onto my other one so I can have ubuntu on it?

---

### Post by avtolle on 2008-06-14
If you downloaded the iso file, and then had Wubi install from it, you will need to burn the iso file to CD to install on your other computer (a fresh install). AFAIK, there is not a way to merely copy the installed files over as you suggest you want to do.

If you delete XP, since your ubuntu is installed as a folder under it, you will lose your Ubuntu as well.

---

### Post by balaknair on 2008-06-14
Copying the files off one PC onto the other won't install Ubutu, you need to install Ubuntu from the CD. A fresh full install of Ubuntu would be better(not a Wubi installation) since Wubi uses the Windows filesystem, and Ubuntu works much better with Linux filesystems like ext3 or ReiserFS, plus it also installs the Master Boot Record needed to boot the PC on the Hard drive.
You could try booting off the Live CD on the target PC and see if it detects all your hardware before you install(and wipe your PC clean losing your existing Windows partition). You can always copy over your Gnome configuration files(if that's what you're worried about), you can use apt-on-cd to back up all the downloaded installation files(additional programs and updates on your wubi install) so you won't have to download them again.
[http://www.ubuntugeek.com/create-backup-of-all-installed-packages-using-aptoncd-in-ubuntu.html](http://www.ubuntugeek.com/create-backup-of-all-installed-packages-using-aptoncd-in-ubuntu.html)

Another link which might be useful for what I think you're trying to do
[http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)


What I would suggest is:
1)Back up important files on your second PC
2)Boot off the Live CD
3)Try out Ubuntu off the Live CD, browse the net, play a media file like a movie or audio(not mp3) file, plug in a USB device like a thumb drive, so that you know it's OK with your hardware on this PC. I'd suggest taking your time and try this for 2-3 days so that you get to try out most of the routine things you need to do on this PC.
4)If you can do all of this, you can go ahead and install Ubuntu, and the installer will guide you through the steps. If you want to erase Windows completely, choose manual partitioning, you can format the Windows partition during install(remember that you will lose all files on that partition if you do this). If you want you can also erase the hard drive completely and partition it as an exclusively Ubuntu PC.

Before you try this, I suggest you read these pages
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

This is possibly the best guide for anyone new to Ubuntu I know of(thanks to aysiu : D)
and I highly recommend you read it before installing Ubuntu.

All the best and hope you enjoy your Ubuntu experience.

---

