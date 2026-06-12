---
title: "Checking Burned ISO Disk"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Covalent Bond on 2008-04-29
I have downloaded Hardy Heron and burned it to a disk, but when I put the disk in and start the computer, I do not get the option to check the disk for errors.  I can see the option, but the screen immediately goes to the language selection screen.  Further, I can not use my mouse to  move through the language screen.  Fortunately, it selects English, but I would not be able to make any other selection if I wanted.  Is there another way to check the disk for errors.  I am not terribly familiar with the terminal, but if the command is not too convoluted, I think I could manage.
TX
CB

---

### Post by skymera on 2008-04-29
You can run an MD5 checksum from within windows.
The MD5 should be provided somewhere on the Ubuntu website.

---

### Post by Covalent Bond on 2008-04-29
I remain uncertain how to check the disk.  I want to try and do this through Ubuntu.  I typed "md5 checksum" in the terminal window and it mentioned sleuthkit which I installed via synaptic, but have no idea how to access sleuthkit or how to ultimately check the copied disk for errors.  Sorry for being so dense.
CB

---

### Post by eapache on 2008-04-29
You can navigate the languages with the arrow keys, and select your language with "Enter". You can then navigate the menu the same way and select the "Check CD for errors" option that way.

---

### Post by OffAxis on 2008-04-29
you would use 
```
md5sum -c <filename>
```

to get the checksum off the .iso file that you downloaded and then compare it to the known good value off the download page.
(I know-doesn't check the disc, but you should be able to check that on boot).

I'm confused; Yes, the disc pops up with the language selection first, but what happens when you press 'Enter'?
Does it not give you access to the typical LiveCD boot menu? (the one you mention that you can see, but can't access)

---

### Post by Covalent Bond on 2008-04-29
OffAxis:

When the computer starts with the CD in the drive, I very quickly see a screen with several options, MD5 checksum being one, but it then goes to the language screen and gives me a number of seconds before the selection is loaded.  Hitting enter does nothing and I can not select any other language other than the one selected (English).  After the time runs out, the disk loads to the liveCD program which then give me a chance to explore Ubuntu or install.  However, my fear is that the disk has some damage and will not install as needed.  For what it is worth, I plan to do a clean install rather than update from Gutsy.  I also plan on a dual boot system with a clean Windows SP install first then Hardy Heron.  

What file name do I use in the terminal?  I know, dense.

Thanks for your assistance.
CB

---

