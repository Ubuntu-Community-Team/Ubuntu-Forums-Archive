---
title: "download question"
date: 2017-09-13
forum: New to Ubuntu
---

### Post by owby on 2017-09-13
I am trying to change systems from win 10 to Ubuntu and after downloading twice I get the same message--Language\\P2GRC.dll is missing.  What am I doing wrong?  As a senior citizen I don't understand 99% of what I read on this forum so please keep it simple.  Thanks for any help. JSM

---

### Post by lisati on 2017-09-13
A little research on my part suggests that the error message might be related to Power2Go, software that is sometimes used on Windows systems to burn (record) stuff on disk.

When does the error you are seeing appear?

---

### Post by owby on 2017-09-14
The message "missing" appears when I try to do anything with the download.  It appears that the files are not complete.  When I double click to open the main file I get the message.

---

### Post by Bucky Ball on 2017-09-14
Welcome. You don't double-click to open any main file. You download the Ubuntu ISO[ from here]("https://www.ubuntu.com/download/desktop") (the long-term support 16.04.3 is a good place to start), create bootable install media from the ISO (instructions for creating USB or DVD further down the linked page).

You then boot from the install media you just created and install Ubuntu to an area of free space you have created. If you are looking to dual-boot, Ubuntu goes on its OWN partition, not inside Windows or anything to do with Windows. The two operating systems will run totally independently and you will need to either boot into Windows or Ubuntu when you start the machine (although you can set things up to share data files between the two once at a desktop).

Hope that gives you some clues. ;)

PS: When you boot from the install media you will get a list of options; 'Install Ubuntu' 'Try Ubuntu' and a few others. If you want to have a look around before install without changing anything on your hard drive, choose 'Try Ubuntu'. That will take you to a desktop and you can have a look around. If you want to install from there, there is an install icon on the desktop. Just double-click it.

Importantly, and I repeat; you will need free space or a Linux partition prepared to install Ubuntu to.

---

### Post by HermanAB on 2017-09-14
More importantly - make a backup of all your data before you start to mess around with installing Ubuntu, since you could inadvertently wipe your whole disk drive.

---

### Post by SeijiSensei on 2017-09-14
I've used Rufus to create a USB stick from Windows as described here:

[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows)

---

### Post by Bucky Ball on 2017-09-14
> **HermanAB said:**
> More importantly - make a backup of all your data before you start to mess around with installing Ubuntu, since you could inadvertently wipe your whole disk drive.

+1. ;)

---

### Post by owby on 2017-09-14
Thank you all for your suggestions but I think something is blocking the download.  After trying it 5 times I always get the message that a "language" file is missing.  This happens at the very start when the download ends.  I've put it on a dvd but is still tells me that file is missing--"please download again".  I think I"ll send for a usb stick with the program on it.  Again, thanks for the input.  JSM

---

### Post by oldos2er on 2017-09-14
Ubuntu isn't a program,  it's an operating system, an important distinction. It also does not run Windows applications;  however it does come with some basic applications like a Web browser,  email client,  office suite,  etc.

As was mentioned please don't install it without having known good backups.

---

### Post by wheatpenny2 on 2017-09-14
> **HermanAB said:**
> More importantly - make a backup of all your data before you start to mess around with installing Ubuntu, since you could inadvertently wipe your whole disk drive.


My first time experimenting with Ubuntu about 6 or 7 years ago, I did just that: Completely deleted Windows Vista from my laptop unintentionally (trying to set up a dual-boot).

---

### Post by lisati on 2017-09-14
Don't try to open the downloaded file as if it was a regular program or file for Windows. You need to place a copy on a DVD or USB drive in a such a way that your computer can "boot" (start) using the DVD or USB instead of from the C: drive that Windows would normally use.

---

### Post by genericvii143 on 2017-09-16
Yes, i was about to suggest Rufus it's a great software.

---

