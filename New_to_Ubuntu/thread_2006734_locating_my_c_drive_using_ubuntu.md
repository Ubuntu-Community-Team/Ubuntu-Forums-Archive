---
title: "locating my c drive using ubuntu"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by bowa on 2012-06-19
Can you please help.  My pc has lost something in its start up, so i  have managed to get ubuntu onto a cd and get pc to run tht way. I am  unable to locate mu old c drive to get my picture off. i have read that i  need to type sudo blah blah, but i dont know how to access Accessories  etc in this op system. I have not installed un, just running from a cd.  please help, im v frustrated

---

### Post by MG&amp;TL on 2012-06-19
If you open the file manager (top icon in the launcher, if I recall), does it not have a "file system" listed on the left side?

---

### Post by matt_symes on 2012-06-19
Hi

Welcoome to the forums bowa :)

> **bowa said:**
> Can you please help.  My pc has lost something in its start up, so i  have managed to get ubuntu onto a cd and get pc to run tht way. I am  unable to locate mu old c drive to get my picture off. i have read that i  need to type sudo blah blah, but i dont know how to access Accessories  etc in this op system. I have not installed un, just running from a cd.  please help, im v frustrated

Linux does not name it's partitions the same way windows does.

It does not use C:, D:, E: etc.

It uses sda1, sda2, sda3... (for the first drive) and sdb1, sdb2, sdb3.. for the second drive.

You should be able to see your Windows "drive" (it's actually usually called a partition) by using Nautilus. 

This is Ubuntu's equivalent of Windows Explorer. If the partition has a label then it should appear in Nautilus.

You can run Nautilus by pressing ALT + F2 together and typing ```
nautilus
``` in the Run as dialog.

You need to mount the windows partition. 

You can do this by looking in the left hand side of nautilus under devices. You should see the windows partition there. It will not be called c: but will have the same name as the partition label.

Click on the correct partition, it will mount it and you should see the files on the right hand part of Nautilus.

Take a look at the image.

If you cannot see the windows partition, post back and we will look deeper.

EDIT: Hi MG&TL

Kind regards

---

### Post by X D face me on 2012-06-20
you can easily acces your files using your file explorer (nautilus) to acces your windows files. for that: inside your file explorer, go to the file system, then go into the "host" folder. your windows files and programs should be right there.

---

### Post by pissedoffdude on 2012-06-20
As other have suggested, open the file browser, look for your windows drive in the panel on the left, click it, and check if it mounts.

If it's not showing up, or if it's not mounting, then run this command:```
sudo fdisk -l
```

This will give you a list of your hard drives and partitions.  From there, you should be able to identify the windows drive.  If you have multiple ntfs partitions, your c drive will probably be the largest one.  It should be labeled something like /dev/sda1

Then, run these commands:```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```

Afterwards, reopen the filemanager and your c drive should appear and you should be able to mount it.

---

### Post by bowa on 2012-06-21
yes it does.

---

### Post by bowa on 2012-06-21
What is the Z shaped symbol after sudo fdisk -Z ?

---

### Post by bowa on 2012-06-21
Does as you suggest a found Nautilus, but there is no windows listed on left hand side.

---

### Post by bowa on 2012-06-21
Cannot find "host" folder in file system.

---

### Post by coffeecat on 2012-06-21
> **bowa said:**
> Cannot find "host" folder in file system.

@bowa, are you running Ubuntu from a live CD session, that is booting up from a CD and running the Ubuntu desktop? That is what your first post seems to suggest. If you are, don't bother looking for the host folder - you won't find it. The host folder is a feature of a wubi installation where Ubuntu is installed inside your Windows partition. 

If you are running from the live CD, this is all you need do. Open a Nautilus file browser - that is "home folder" near the top of the launcher if you are running Ubuntu with the Unity desktop, or if you are running an older version of Ubuntu, choose the home folder from the Places menu.

Once the Nautilus window is open, look at all the choices on the left. Do **not** open "File System" where it says only "File System" and nothing else. Your Windows partition should be listed near the top of the list. It won't be labelled "C:". If the Windows partition has a partition label, which appears as the C: drive label in Windows, you will see that. But if there is no partition label, you will see "XX GB File system", where XX is the size of the C: partition. Simply click where the partition is listed in the left pane and it will be automounted for you. The display in the main pane will change to your Windows C: filesystem. Open on the "Users" folder (if I remember correctly) and then find your Windows account folders somewhere in that folder tree.

---

### Post by philinux on 2012-06-21
> **bowa said:**
> What is the Z shaped symbol after sudo fdisk -Z ?

Thats a lower case L

---

### Post by bowa on 2012-06-23
> **philinux said:**
> Thats a lower case L
\thanks x

---

### Post by bowa on 2012-06-23
Im running from a CD, I have done as you suggest and go into nautilus  via alt and F2 bear with me this  operating system  is so alien to me. I  am not able to see anything listed on the left re windows or xx GB file  system.  is there a way i can take a screen shot?

---

### Post by coffeecat on 2012-06-23
> **bowa said:**
> is there a way i can take a screen shot?

Alt + PrintScreen for a screenshot of the open window or just PrtScrn for the whole desktop.

What version of Ubuntu are you using on the CD? I can't see that you've told us this. If you are not sure, what is the name of the ISO that you used to burn the CD? Or in the live CD session open a terminal (ctrl-alt-t) and see what the output of this command says:

```
cat /etc/lsb-release
```

---

### Post by bowa on 2012-06-23
> **coffeecat said:**
> Alt + PrintScreen for a screenshot of the open window or just PrtScrn for the whole desktop.

What version of Ubuntu are you using on the CD? I can't see that you've told us this. If you are not sure, what is the name of the ISO that you used to burn the CD? Or in the live CD session open a terminal (ctrl-alt-t) and see what the output of this command says:

```
cat /etc/lsb-release
``` sorry to appear really stupid, you guy's really know your stuff, the only answer i can give you re this is i downloaded it this week from the ubuntu website using roxio onto a dvd, loaded it into my dodgy pc, ran direct from cd without installing.  It asked me if i wanted to try or install, maybe it would be better if i installed it?  what do you think. I can get to the desk top, i then use nautilus to get to a page that shows: devices SYSTEM RESERVE, ACER. computer HOME DESKTOP DOCUMENTS DOWNLOADS MUSIC PICTURES VIDEO FILE SYSTEM TRASH. I am really lost. :(

---

### Post by bowa on 2012-06-23
> **bowa said:**
> sorry to appear really stupid, you guy's really know your stuff, the only answer i can give you re this is i downloaded it this week from the ubuntu website using roxio onto a dvd, loaded it into my dodgy pc, ran direct from cd without installing.  It asked me if i wanted to try or install, maybe it would be better if i installed it?  what do you think. I can get to the desk top, i then use nautilus to get to a page that shows: devices SYSTEM RESERVE, ACER. computer HOME DESKTOP DOCUMENTS DOWNLOADS MUSIC PICTURES VIDEO FILE SYSTEM TRASH. I am really lost. :(
Yes i did it ubuntu 12.04 LTS

---

### Post by bowa on 2012-06-23
> **coffeecat said:**
> Alt + PrintScreen for a screenshot of the open window or just PrtScrn for the whole desktop.

What version of Ubuntu are you using on the CD? I can't see that you've told us this. If you are not sure, what is the name of the ISO that you used to burn the CD? Or in the live CD session open a terminal (ctrl-alt-t) and see what the output of this command says:

```
cat /etc/lsb-release
```
Yes i did it ubuntu 12.04 LTS

---

### Post by coffeecat on 2012-06-23
> **bowa said:**
> i then use nautilus to get to a page that shows: devices SYSTEM RESERVE, ACER. computer HOME DESKTOP DOCUMENTS DOWNLOADS MUSIC PICTURES VIDEO FILE SYSTEM TRASH. I am really lost. :(

ACER is your Windows C: partition. Simply click on where it says ACER. Don't click on System Reserve.

---

### Post by bowa on 2012-06-24
> **coffeecat said:**
> ACER is your Windows C: partition. Simply click on where it says ACER. Don't click on System Reserve.I have tried clicking on the ACER and it says " unable to mount acer, Error mounting:mount exited with exit code 13:ntfs_attr_pread_i:ntfs_pread
failed :input/output error
failed to read ntfs$bitmap:input/output error NTFS is either inconsistent, or there is a hardware fault, or its a softRAID/ fakeRAID hardware.

---

### Post by coffeecat on 2012-06-24
At least we're sort-of getting somewhere. The Acer partition is your Windows C: partition, but there is (probably) a filesystem corruption, hence the message you are getting. Ubuntu will not mount a damaged filesystem - this is a failsafe protection.

You need to do a chkdsk from Windows, but if Windows fails to boot this is going to be a challenge. First thing to try. Choose Windows from the grub menu and then press F8 as soon as you can. You have to be very quick. What I do is to tap F8 repeatedly as soon as I have pressed return in the grub menu. Try booting in safe mode, or is there a choice to repair Windows from the F8 menu? I can't remember.

Alternatively. Do you have or can you borrow a Microsoft Windows installation DVD appropriate for the version of your Windows operating system? I.e 64- or 32-bit for 64-bit/32-bit, and Vista for Vista, Windows 7 for Windows 7. An Acer Windows restore DVD will not do. The reason I ask is that you can run chkdsk from the installation DVD, and do other boot repairs on Windows.

Also - are you running Windows 7? It looks as though you may be. If you are, do you have access to another Windows 7 installation - friend or family, whoever? If you can use another Windows 7 system, you can create a repair CD from it which you can then use to repair your system. If you can do this, say so, and I can tell you how to make the CD.

---

### Post by bowa on 2012-06-27
> **coffeecat said:**
> At least we're sort-of getting somewhere. The Acer partition is your Windows C: partition, but there is (probably) a filesystem corruption, hence the message you are getting. Ubuntu will not mount a damaged filesystem - this is a failsafe protection.

You need to do a chkdsk from Windows, but if Windows fails to boot this is going to be a challenge. First thing to try. Choose Windows from the grub menu and then press F8 as soon as you can. You have to be very quick. What I do is to tap F8 repeatedly as soon as I have pressed return in the grub menu. Try booting in safe mode, or is there a choice to repair Windows from the F8 menu? I can't remember.

Alternatively. Do you have or can you borrow a Microsoft Windows installation DVD appropriate for the version of your Windows operating system? I.e 64- or 32-bit for 64-bit/32-bit, and Vista for Vista, Windows 7 for Windows 7. An Acer Windows restore DVD will not do. The reason I ask is that you can run chkdsk from the installation DVD, and do other boot repairs on Windows.

Also - are you running Windows 7? It looks as though you may be. If you are, do you have access to another Windows 7 installation - friend or family, whoever? If you can use another Windows 7 system, you can create a repair CD from it which you can then use to repair your system. If you can do this, say so, and I can tell you how to make the CD.
Yes im running window 7,I made a disk from my daughters  dell, tried to run it in my acer, it says something along the lines windows is installing files ............................... then it opens to the blue screen with the pretty pattern on and just sits there. I think im screwed. Can i take the hard drive out and put it in a desk top? If something is missing from the start up, the operating system on the old vista hard drive will fire up and i should then be able to access the acer hard drive?? clutching at straws.  just would love to be able to get all that stuff off i should have backed up. Hind sight and all that!!

---

### Post by bowa on 2012-06-27
> **coffeecat said:**
> At least we're sort-of getting somewhere. The Acer partition is your Windows C: partition, but there is (probably) a filesystem corruption, hence the message you are getting. Ubuntu will not mount a damaged filesystem - this is a failsafe protection.

You need to do a chkdsk from Windows, but if Windows fails to boot this is going to be a challenge. First thing to try. Choose Windows from the grub menu and then press F8 as soon as you can. You have to be very quick. What I do is to tap F8 repeatedly as soon as I have pressed return in the grub menu. Try booting in safe mode, or is there a choice to repair Windows from the F8 menu? I can't remember.

Alternatively. Do you have or can you borrow a Microsoft Windows installation DVD appropriate for the version of your Windows operating system? I.e 64- or 32-bit for 64-bit/32-bit, and Vista for Vista, Windows 7 for Windows 7. An Acer Windows restore DVD will not do. The reason I ask is that you can run chkdsk from the installation DVD, and do other boot repairs on Windows.

Also - are you running Windows 7? It looks as though you may be. If you are, do you have access to another Windows 7 installation - friend or family, whoever? If you can use another Windows 7 system, you can create a repair CD from it which you can then use to repair your system. If you can do this, say so, and I can tell you how to make the CD. Tried the F8 safe mode, repair  etc, windows is loading files and then nothing.

---

### Post by coffeecat on 2012-06-27
> **bowa said:**
> Yes im running window 7,I made a disk from my daughters  dell, tried to run it in my acer, it says something along the lines windows is installing files ............................... then it opens to the blue screen with the pretty pattern on and just sits there. I think im screwed. Can i take the hard drive out and put it in a desk top? If something is missing from the start up, the operating system on the old vista hard drive will fire up and i should then be able to access the acer hard drive?? clutching at straws.  just would love to be able to get all that stuff off i should have backed up. Hind sight and all that!!

If you have made the repair CD, it shouldn't say anything about installing files. I hope you haven't started the installer from the Dell installation DVD, because if you have you could very well have overwritten some or all of your Windows C: partition. When you boot up the Windows 7 repair CD you will see the screen as here with various repair options:

[http://windows.microsoft.com/en-us/windows7/What-are-the-system-recovery-options-in-Windows-7](http://windows.microsoft.com/en-us/windows7/What-are-the-system-recovery-options-in-Windows-7)

---

### Post by bowa on 2012-06-27
> **coffeecat said:**
> If you have made the repair CD, it shouldn't say anything about installing files. I hope you haven't started the installer from the Dell installation DVD, because if you have you could very well have overwritten some or all of your Windows C: partition. When you boot up the Windows 7 repair CD you will see the screen as here with various repair options:

[http://windows.microsoft.com/en-us/windows7/What-are-the-system-recovery-options-in-Windows-7](http://windows.microsoft.com/en-us/windows7/What-are-the-system-recovery-options-in-Windows-7)
i clicked on the start repair and white writing came along the bottom of the screen saying windows is LOADING  files ................ and then it went to the blue fancy screen and stuck there. Sorry, just run it again, its defo loading not installng

---

