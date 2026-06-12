---
title: "[SOLVED] Another Noob with an Error 15 Problem"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by RadioSilence on 2008-05-16
I've not been able to get Ubuntu to successfully install.  I'm a complete linux Noob and nothing I've seen addressing this problem makes any sense to me at all so I apologize in advance because I have found a few articles and a bug on this type of problem that seem similar.

I've gone through the install process several times from within Windows (off of install disk I created from downloaded image) on all of my hard disks and the outcome is the same in all circumstances.  I install Ubuntu through Windows which then reboots into Ubuntu and attempts to complete installation.  This part of the process seems to go completely smoothly until the install reaches 100% in which it reboots (seems more like a crash actually).  

When trying to go back into Ubuntu on boot, I get this error:
 
[B]"Filesystem type is ntfs, partition type 0X7
 
Kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=EAB0E904BOE8D859 loop=/ubuntu/disks/root.disk ro quiet splash
 
Error 15: File not found
 
Press any key…"[/B]
 
I then have the option to boot up under memtest or a safer mode or WinXP which is my native environment.  However, if I try to boot up XP without a restart I get this message as well:
 
"Error occurred while save default
NTCDR is missing"
 
I assume these are not related.

I did see in another thread that ago recommended this for a fix:

If so edit c:\ubuntu\disks\boot\grub\menu.lst
there should be something like 
root (hd1,1)/ubuntu/disks
change the X in: 
(hdX,Y)
If X is 0 try 1 and if it is 1 try 0

I attempted this but to without any change in the outcome at all.

I do have multiple discs.  I’m currently trying to run Ubuntu off my C drive where Windows also resides but, again, I’ve tried them all.  The outcome is always the same although I’ve noticed the error message changes slightly in the string above that says UUID=EAB0E904BOE8D859, sometimes the sequence of numbers/letters changes.

I’m running a Q Core Intel chip, 4 G’s of Ram on an ASUS P5K motherboard.  I’m not running anything SATA.  My 2 primary HD’s are running IDE off the board and my optical drives and other HD are running IDE off of an ATA PCI IDE converter card.
  
 I would greatly appreciate if anyone could point me in the right direction.

Thanks in advance.

---

### Post by Mark_in_Hollywood on 2008-05-16
First, please say whether you have your data backed up onto something that isn't connected to the computer.

Error 15 are GRUB messages.

If you are willing to do this my way, I think it is the easiest way to get it all up and running. If you have to use both MS and Ubuntu, wait for another poster to get back to you, I'm not your guy.

Using the Ubuntu CD, boot into it. When it asks if you want to run Ubuntu without installing select that option.

When the OS is loaded and you have a desktop, open System/Administration/Partition Editor. when GParted loads, check the top right and see the disk that gives the error message. If more than one storage device is connected, all will show in a drop down list.

Highlight the disk with the problem and reformat it, selecting ext3, Primary, etc. Reboot- reinstall Ubuntu. That's what I had to do.

---

### Post by RadioSilence on 2008-05-16
Thanks for the response.  All data is secured in another location.

I think I will need to have both MS and Ubuntu handy while I'm learning how to use the OS and linux and general.

Your post brings up another problem for me, since my optical drives are going through a PCI IDE card, I can't boot from a CD.  I've ordered a SATA optical drive to remedy this but for now I'm stuck trying to install in WinXP.

Stupid question: Why does this not work if running both MS and Ubuntu?  Could I do what you've outlined on an HD seperate from the MS files and retain dual boot ability?

Thanks again.

---

### Post by ace007 on 2008-05-16
When it boots hit c, that will bring you to a Grub prompt.
```

grub>

```
Do
```

find /grub/stage1

```
If you did not do a /boot partition do
```

find /boot/grub/stage1

```
Or whatever info you received where your linux partition is.
> **Ralphie said:**
> I have found an easier way to do this.


[SIZE="1"](from[ budman]("http://www.linuxforums.org/forum/gentoo-linux-help/31581-error-15-file-not-found-startup.html"))[/SIZE]

One of these commands will give you an answer like
```
root (hd0.0)
```

Now press Esc.
Select the first boot option and press "e"

Press "e" again on the root option
Change the hd(X,X) to whatever you got above. for me it was hd (0,0).
Press Enter.
Now press "b"

Ubuntu should load up.

Now that you are in, you need to change this for good.
Open a terminal and enter
```
sudo gedit /boot/grub/menu.lst
```
or, depending on your setup
```
sudo gedit /grub/menu.lst
```

Scroll down towards the bottom of the file, and you will find the same "root (hdX,X)" change it appropriately, and you can save!

Also while editing, you can go ahead and change all of the root options for the different ubuntu modes, because they are all most likely wrong.


PS: Windows wont load with "No NTLDR" because GRUB is now the bootloader

---

### Post by RadioSilence on 2008-05-16
That actually sounds pretty straight forward.  I'll give that a shot.  Thank you.

---

### Post by RadioSilence on 2008-05-16
This solution solved the problem completely.  Very exciting. 

Thanks very much.

---

### Post by Mark_in_Hollywood on 2008-05-16
Please find the top of this thread you began and under Thread Tools, please mark the thread as SOLVED.

---

