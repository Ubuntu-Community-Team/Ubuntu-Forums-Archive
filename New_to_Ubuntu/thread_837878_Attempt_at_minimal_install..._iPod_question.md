---
title: "Attempt at minimal install... iPod question"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by tdrusk on 2008-06-22
I am trying to do a minimal install with fluxbox. My iPod is not being recognized in gtkpod or banshee. What do I need to do from a minimal install to mount and use my iPod?

---

### Post by rockerphil on 2008-06-23
with your iPod connected type this in terminal

sudo fdisk -l

if you've only gone one hard drive your iPod should show up as a secondary hard drive. on my machine it would show up as /dev/sdb1. so you want to make a mount point for your iPod in your home folder (or wherever you want it to mount) say ~/iPod. so in terminal type this

mkdir ~/iPod

that will create the mount point for your iPod to mount to. then to mount the  iPod type this in terminal

sudo mount /dev/sdb1 ~/iPod

of course you'll have to adjust the names to the drive name of your iPod (/dev/sdb1 in the examples) and the mount point to the name of the folder you want it to mount to. if you would like you can post the output of the command:

sudo fdisk -l

and i could give more specific instructions

---

### Post by tdrusk on 2008-06-23
Thanks for your help so far. It is showing up in my home folder, but gtkpod still isn't recognizing it. 

I want it to work just like default Ubuntu works with my iPod, only using gtkpod. What do I have to do?

---

### Post by rockerphil on 2008-06-23
i had a similar problem with an old mp3 player that didn't want to play nice with Ubuntu and only wanted to show up as a read only file system, so my first action was to change the file permissions by typing this in terminla

sudo chmod +w <filename> (<filename> being the name of the file you're changing the permissions of without the <>)

and if that doesn't work i would add a line to the /etc/fstab file so that when you boot up your system auto-mounts the drive, i've never done it with an iPod, so i don't know what the line would look like. i personally have never used an iPod in Ubuntu, and i'm personally a minimalist enthusiast, so i'm not all that GUI oriented, so i wouldn't know exactly what to do to make it play nice with gtkpod or Banshee, i personally always just did the drag & drop bit using the file manager. sorry i couldn't help any more than that


Phil

---

