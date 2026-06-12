---
title: "[SOLVED] How to install Ubuntu 8.04 on USB hard disk"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by dkc.com on 2008-06-07
[FONT="Comic Sans MS"][COLOR="Purple"]Hi,
I am basically a window user who heard a lot about linux. As a result I tried a live cd of Ubuntu 7. I enjoyed it very much. Afterwards I installed it on a small partition of my hard disk. But it was a too small partition for a great OS. So I bought a 320 gb external hard disk.
I followed the following link to install it on one of the 75 gb partitions of my USB hard disk:

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

I exactly followed the link but I may have made a mistake in the last step.

When I try to boot from USB hard disk it returns with GRUB error 22.

Can any body help? [/COLOR][/FONT]

---

### Post by ethanklein on 2008-06-07
I'm a newb too but I would check to see if you formated the Drive correctly. After that I would check the drives config with your Ubuntu. You might have to manually mount the hard drive. I have no clue how to do that. Just some ideas.

---

### Post by meierfra. on 2008-06-07
Did you disconnect the internal drive during the installation?

Does the Grub menu appear at boot up?  (Press "Esc" after the Bios screen)

Boot from the LiveCD, open a terminal "Application->Accessories->Terminal)

and post the output of

```
sudo fdisk -l
```
(l is  a lower case L)

Go to Places->Computer. One of the icons is for Ubuntu.  Double click it, navigate to /boot and then /boot/grub. Post the content of the file "menu.lst" in that folder.

---

### Post by mr_boo1711 on 2008-06-07
I'm still learning too, so forgive the vagueness! (Is that a word?! lol)

It sounds like your system cant find the grub.  It happened to me recently after I did a re-install of linux after tinkering with it for two years. Long story short it was because everytime I plugged in my external USB drive (It didnt have the OS on it incidently, it was just for media and stuff) and started the machine, the computer got 'confused' over which harddrive the grub was located on and subsequently returned error 22.

Your problem might be that the external USB drive might not be detected corretly at boot, or even not detected at all.  It might be worth starting on the bios and looking at the storage drives to make sure they're actually there.

As I said - I aint an expert by any means, but I reckon its worth a look... :) Good luck.

---

### Post by dkc.com on 2008-06-07
> **meierfra. said:**
> Did you disconnect the internal drive during the installation?

Does the Grub menu appear at boot up?  (Press "Esc" after the Bios screen)

Boot from the LiveCD, open a terminal "Application->Accessories->Terminal)

and post the output of

```
sudo fdisk -l
```
(l is  a lower case L)

Go to Places->Computer. One of the icons is for Ubuntu.  Double click it, navigate to /boot and then /boot/grub. Post the content of the file "menu.lst" in that folder.

Hi friend,
Thanks for such a quick reply.
I didn't disconnect my internal hard drives because I don't know how to do it in a laptop? I can physically remove it from a desktop but never touched Laptop in that way. Is it possible to disconnect it through BIOS?

I didn't press ESC after BIOS screen but the GRUB manu appeared and when I selected the option to boot Linux it returned with error 22.

One thing I didn't understand from you reply is about menu.lst. Where can I find that file? Can you explain it in a bit detail as I am an absolute newbee.

Thank you very much.

---

### Post by meierfra. on 2008-06-07
try this


Select Ubuntu at the grub menu.Do not press "enter", but press "e" instead. At the new screen press "e" again.

You will get a line which looks like this

root (hd1,0)


But the numbers could be different. Change it to

root (hd0,0)   
(Change the first number to zero, but do not change the second number)

Press "enter" and then "b" to boot.

This should boot you into Ubuntu. Once you booted into ubuntu, you need to make these changes permanent:

Open a terminal (Click on Applications in the menu in the top left corner. Then on Accessories and finally on terminal)

Type

```
gksudo gedit /boot/grub/menu.lst
```
and press enter. (the "l" is a lowercase "L", not a one) It will asked you for your password. 

In the file which opens,
change 

#groot (hd1,0)

to 

#groot (hd0,0)
(so again change the first number to zero, but do no change to second number)

Save the file.

In the terminal type


```
sudo update-grub
```
It might asked you for your password again. This time while you type your password it will feel like nothing is happening. That's normal, just press "enter" when you are done typing the password.

Reboot and you should be able to get into Ubuntu without any problems.

---

### Post by dkc.com on 2008-06-07
> **meierfra. said:**
> try this


Select Ubuntu at the grub menu.Do not press "enter", but press "e" instead. At the new screen press "e" again.

You will get a line which looks like this

root (hd1,0)


But the numbers could be different. Change it to

root (hd0,0)   
(Change the first number to zero, but do not change the second number)

Press "enter" and then "b" to boot.

This should boot you into Ubuntu. Once you booted into ubuntu, you need to make these changes permanent:

Open a terminal (Click on Applications in the menu in the top left corner. Then on Accessories and finally on terminal)

Type

```
gksudo gedit /boot/grub/menu.lst
```
and press enter. (the "l" is a lowercase "L", not a one) It will asked you for your password. 

In the file which opens,
change 

#groot (hd1,0)

to 

#groot (hd0,0)
(so again change the first number to zero, but do no change to second number)

Save the file.

In the terminal type


```
sudo update-grub
```
It might asked you for your password again. This time while you type your password it will feel like nothing is happening. That's normal, just press "enter" when you are done typing the password.

Reboot and you should be able to get into Ubuntu without any problems.

Hi friend,

Your suggestion worked fine for me and I could boot in to my Linux system. But afterwards using sudo command and making the change permanent confused me.

Let me tell you, what I did.


Opened the Terminal
Typed gksudo gedit/boot/grub/menu.lst
pressed l


but it did nothing. I neither asked for a password nor opened any file. I am new at all these commands so quite possible that I may have made mistake. Can you once again give me step by step instructions from the sudo command? Also one more thing, how to save the changes? Is there any special sudo for that?

Sorry to trouble you again. Thanks.

---

### Post by Stefanie on 2008-06-07
> Typed gksudo gedit/boot/grub/menu.lst

i think you forgot the space between gedit and /boot . Copy-paste this line:
```
gksudo gedit /boot/grub/menu.lst
``` (you can't use ctrl-V to paste in the terminal. use ctrl-shift-v instead!)

---

### Post by dkc.com on 2008-06-07
> **Stefanie said:**
> i think you forgot the space between gedit and /boot . Copy-paste this line:
```
gksudo gedit /boot/grub/menu.lst
``` (you can't use ctrl-V to paste in the terminal. use ctrl-shift-v instead!)

Thanks Buddy,
My all problems are solved and I am happily using Ubuntu now.
This is the benefit of Linux communities.
Hates off.

---

