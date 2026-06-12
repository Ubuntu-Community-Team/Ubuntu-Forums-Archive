---
title: "Brasero"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by Old-un on 2011-09-10
I've been trying to burn some mp3 music files to a cd using Brasero but have somehow lost my way.

1) I open up Brasero and click on New Project
2) I then drag and drop all the music files i want to record to a cd in the New Audio Project Window and click Burn.
3) Now a new window opens called Location for image file?

I'm lost. Could someone help me please.

---

### Post by ajgreeny on 2011-09-10
Have you already put a CD-R in the disk tray?  If not brasero asks you to make an iso file which you can later burn to disk.

Just stick a disk in and all should be OK.

---

### Post by haqking on 2011-09-10
> **Old-un said:**
> I've been trying to burn some mp3 music files to a cd using Brasero but have somehow lost my way.

1) I open up Brasero and click on New Project
2) I then drag and drop all the music files i want to record to a cd in the New Audio Project Window and click Burn.
3) Now a new window opens called Location for image file?

I'm lost. Could someone help me please.


You are asking to burn as an image instead of to a CD medium.

you also might need to :

sudo apt-get install ubuntu-restricted-extras

to support the .mp3 on a audio cd

---

### Post by Old-un on 2011-09-10
I tried to use k3b to burn the mp3's but all i got back was wrong format?  Could you tell me how i might check to see if ubuntu-restricted-extras are already installed or not.

---

### Post by haqking on 2011-09-10
> **Old-un said:**
> I tried to use k3b to burn the mp3's but all i got back was wrong format?  Could you tell me how i might check to see if ubuntu-restricted-extras are already installed or not.


just type the command for it.

if its installed then no worries.

as for .mp3 in k3b you need to do:

[I]sudo apt-get install libk3b6-extracodecs

[/I]try to use k3b instead of brasero if you can, IMO brasero is flaky.

---

