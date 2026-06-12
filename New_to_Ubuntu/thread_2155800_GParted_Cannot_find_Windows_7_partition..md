---
title: "GParted Cannot find Windows 7 partition."
date: 2013-06-19
forum: New to Ubuntu
---

### Post by raenCamp on 2013-06-19
I made a ubuntu disk using version 13.04 from which I booted my laptop (Hp G60 windows 7 Home premium pre-installed).  I am currently using ubuntu because my computer cannot boot from windows 7 and I want to access my files that are on win 7 partition.  I tried GParted but it is not detecting my hard drive.  Can anyone tell me what the problem is and if there is a way to fix it? 
Also how can I check the health of my hard drive, if this is the reason why it is not being detected.

p.s. I have windows 7 **_pre-installed_**, I am stressing this fact because most of the searches online are about installing windows then installing ubuntu manually and this was not the case for me. I already have win 7 on my computer and I am **_trying_** ubuntu from the disk I don't want to install it yet. My main objective right now is to retrieve my files from win 7 partition.  

Any help will be greatly appreciated, thanks in advance.

---

### Post by ahallubuntu on 2013-06-19
~

---

### Post by Mark Phelps on 2013-06-19
You said the PC does not boot from Win7.  When you try to boot, what happens? What do you see?

---

### Post by raenCamp on 2013-06-19
A black screen with " no bootable device - insert disk and press any key" that's what happens but now that I have the Ubuntu disc I can boot to that. It's just that I want my files just in case the drive really is dead.

---

### Post by ahallubuntu on 2013-06-19
~

---

### Post by oldfred on 2013-06-19
My older version of gparted would not show my sda with Windows XP even though it booted XP. After running chkdsk gparted then showed it and XP even booted faster - 4 minutes instead of 5. I do not now run XP.
Newer versions of gparted seem to show those type of drive issue but will have red or yellow icons with warnings to right click on for more info.

If BIOS does not show drive then nothing will mount it or let you recover. 
If BIOS shows it then some recovery tools may mount it.

---

