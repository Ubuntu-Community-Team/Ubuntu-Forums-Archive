---
title: "Using a Live CD to save a computer"
date: 2007-06-12
forum: Other OS Talk
---

### Post by Fireblend on 2007-06-12
Hey, a friend of mine's XP computer seems to be in that classic eternal "loading windows->computer resets" loop and I was wondering what I could do with the live CD. I know I could probably install ntfs-3g and recover files from the hard drive assuming it's not that what's damaged in the first place, but is there anything else I can do? Also, Ubuntu doesn't come already with ntfs-3g, and it worries me that I won't be able to connect to internet, so what's another distro that has a LiveCD with ntfs-3g included? I already have Knoppix's and PCLinux's .isos around somewhere, do any of those come with it?

---

### Post by LaRoza on 2007-06-12
You do not need any write support for ntfs, you could easily recover files without it if you are saving the information to a drive in another format. You could use GParted and create a partition on the same drive as Windows to move the files you wish to recover. You can use any live cd, but I recommend Knoppix or Slax if you can get them.

Linux, Knoppix, Ubuntu and others can READ NTFS, not write to it without a driver, so you can copy the files with no problem.

You probably don't want to use Linux to write to ntfs drives, as it can cause problems I hear.

If your hard drive starts, as it seems to be doing, the files can be recovered.

-edit Slax 6 has NTFS write support, I just found out  [http://www.slax.org/](http://www.slax.org/)

---

### Post by Fireblend on 2007-06-12
Thanks. I guess what I'm looking for is either a LiveCD that mounts them automatically so I don't have to bother with terminal work or a guide on what commands to follow with Ubuntu's LiveCD so I can mount them and start the backup :p I know there's a tool with pretty interface for this(ntfs-config) but as I said I don't have internet available on the machine :(

---

### Post by LaRoza on 2007-06-12
Slax will mount the drives automatically I believe.

---

### Post by mips on 2007-06-12
There are distros dedicate to rescue recovery functions, many posts about them here in the forums.

---

### Post by lintoon on 2007-06-29
Knoppix should mount your drives on the desktop.  This will allow you to copy the data to a usb stick, cdr or to another networked pc.

---

### Post by The_Real_Crunk on 2007-12-27
Im having a somewhat similar problem. My XP PC is constantly restarting from the safemode screen with every choice it offers. I got ahold of an Ubuntu Live CD, and I can get to its desktop.

I can see my HD listed on the side, but when I try to access it it says it cant  mount internal drives because of system policy and shows a little login window. It says the user is Ubuntu, and theres a spot for a password. I was never asked to make an account and password so I dont know what to type in there. Even if I did know the password, would I then have access to my files?

I have a 500gig external HD and I was planning on transfering all my files onto there through the Ubuntu Live CD. Would that work as easy as Im hoping it will? Just find all my files, copy/paste them over to my external HD, then reformat my internal HD, and copy/paste all my files back over?

Ive never used linux or Ubuntu before, so please be kind. :confused:

---

### Post by K.Mandla on 2007-12-27
There's a recovery version of Ubuntu around here somewhere ... Rescubuntu? Is that right?

Edit: Aha! I found it on bapoumba's blog.

[http://bapoumba.wordpress.com/2007/10/20/rescue-remix-a-data-recovery-toolkit-was-rescubuntu/](http://bapoumba.wordpress.com/2007/10/20/rescue-remix-a-data-recovery-toolkit-was-rescubuntu/)

There's also this page in the wiki.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by iNeed on 2008-06-15
> **The_Real_Crunk said:**
> Im having a somewhat similar problem. My XP PC is constantly restarting from the safemode screen with every choice it offers. I got ahold of an Ubuntu Live CD, and I can get to its desktop.

I can see my HD listed on the side, but when I try to access it it says it cant  mount internal drives because of system policy and shows a little login window. It says the user is Ubuntu, and theres a spot for a password. I was never asked to make an account and password so I dont know what to type in there. Even if I did know the password, would I then have access to my files?

I have a 500gig external HD and I was planning on transfering all my files onto there through the Ubuntu Live CD. Would that work as easy as Im hoping it will? Just find all my files, copy/paste them over to my external HD, then reformat my internal HD, and copy/paste all my files back over?

Ive never used linux or Ubuntu before, so please be kind. :confused:

How did you get to your Desktop?, Mine still says I/O error, Error reading Boot Cd.

---

### Post by LaRoza on 2008-06-15
> **iNeed said:**
> How did you get to your Desktop?, Mine still says I/O error, Error reading Boot Cd.

Please create a new thread for your technical problems.

This thread is really old and the responses are out of date, especially mine about not being able to write to NTFS.

---

