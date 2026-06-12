---
title: "error: no such device: c4d250ab-b08f-4a9a-84b9-344d9ea61e03. grub rescue"
date: 2013-12-19
forum: New to Ubuntu
---

### Post by saddam.md on 2013-12-19
Hi All,

I am new to Ubuntu .
I tried to install Ubuntu with my existing windows xp system and I successfully intalled it. 
I installed using the USB stick. while installing it tooks the partition from my external hard disk.
now I am facing two issues.

1) If i turn on my system without USB attached to it , system showing this error. "error: no such device: c4d250ab-b08f-4a9a-84b9-344d9ea61e03.
grub rescue>

But if i turn on my system attached with USB stick , The ubuntu starts without any problem.
but I want to run ubuntu without USB attached to my system.

Please Help

2) I am unable to switch back to my Windows xp which is still available in system.
I have seen in some computers , the system shows an option to select the operating system if there are more than one operating system installed but I am not getting that option.
To confirm about the OS installed on my system i tried to install the ubuntu again from the same usb stick , at that time, it shows that my system currently has installed two OS
Microsoft windows xp and Ubuntu 13.0.

Please tell me how to switch between Ubuntu and Xp.

Please Help.[-o

---

### Post by Tristan_Williams on 2013-12-19
First of all, Welcome to Ubuntu! 

To put it simply, the ubuntu installer has accidentally installed the bootloader onto your USB drive, instead of the HDD.
This is an easy fix, but also sucks if you have gotten very far into configuring your system.

To help you further, i need to know which version of ubuntu you installed, and which method.

Version could be 12.04, 12.10, 13.04, 13.10, etc...
Method is either LiveUSB (this is the most common), netinstall, or minimal install (mostly for advanced users)

---

### Post by saddam.md on 2013-12-19
all thanks for you reply .

I have installed version 13.10. and method is live usb.

Thanks,

---

### Post by Tristan_Williams on 2013-12-19
This is hard to explain to someone who has just begun using linux but here it goes...

When your computer boots, it reads what's called the "bootloader", and in your case (and my case too) the bootloader is Grub (Grand Unified Bootloader)

Most likely a result of a faulty Live Image, grub accidentally installed itself on your USB, instead of your hard drive.

To fix this, you will have to do the following:

1) Go to [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) , and download the appropriate version for your operating system.

2) Once downloaded and runnung, Under "Distribution", select Ubuntu (or whatever version of linux you prefer)

3) Under "Version" select the newest version, and make sure you choose the Live version (because netinstall is a little more difficult)

4) At the bottom, select USB, and select the USB drive you wish to use as your LiveUSB.

5) Click OK button, and wait for it to finish.

6) Restart your computer, and boot into your new LiveUSB

7) Once booted COMPLETELY (make sure you can access the internet) remove your USB drive. You do this because the Live installer installs Grub to /dev/sda1 (Hard drive #1). If the USB is left in the computer, it sees itself as /dev/sda1

8) Proceed with the normal method of installing.



Edit:  

Make sure you select "install alongside windows"

---

### Post by saddam.md on 2013-12-20
Dear Tristan ,

Thanks for the reply and advise
could you also tell me how can i switch to my preinstalled windows xp.

---

