---
title: "Trouble Installing Guest Additions VirtualBox"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by RyujiOtogi on 2012-02-21
I'm trying to install guest additions into my Ubuntu Server 11.10 x64 bit (guest OS)within VirtualBox (latest addition as of writing) on my Mac OS X Lion (host OS).I don't know where to mount the guestadditions.iso . Google didn't help with the specifics. I tried VirtualBox-->[Virtual Machine Name]-->Settings-->Storage-->IDE Controller and chose VBoxGuestAdditions.iso as a disc mount.  Later I would also try to add this to the SATA Controller instead, not really knowing what to do. Following the instructions of a How-To I found, I messed with both of these options while typing the necessary command prompts.


After entering the "cd /media" prompt to change my directory to media, I tried to enter "sudo mdkir" but was met with a "cannot create directory 'cdrom': File exists" error. The "sudo mount /dev/cdrom /media/cdrom mount" command only returned a "no medium found on /dev/sr1" message. On several How-To's I found, it instructed me earlier to locate the menu button within the VM and click on "Install Guest Addons". I cannot find this menu button or any kind of option that allows me to do that, whether I'm in the Ubuntu VM or at the VM Load Screen on VirtualBox. 

As you can probably tell I'm a total noob at this. I just need to be pointed in the right direction with what I have--it seems Google wants to tell me how to do this with anything but that.  I really appreciate your time and efforts.

---

### Post by wildmanne39 on 2012-02-21
Hi, I have never installed it on a server but virtualbox has very good documentation on there site.
[https://www.virtualbox.org/](https://www.virtualbox.org/)
Thanks

---

### Post by RyujiOtogi on 2012-02-21
I was following the directions provided for in the VirtualBox manual. I typed "sudo apt-get install dkms" as instructed. Afterwards, it says to "**Insert the             VBoxGuestAdditions.iso CD file             into your Linux guest's virtual CD-ROM drive**". The How-To does not explain exactly how to do this. This is presumably 'common sense' stuff that a more intuitive person or experienced VirtualBox user would not need to ask about, but I'm neither one of those. :-? As I said before, I went to Settings-->Storage-->SATA Controller and chose to mount VBoxGuestAdditions.iso as the CD. But I'm not even sure if that's what I'm supposed to do.

 Even more frustratingly, the tutorial keeps instructing me to go to the 'Devices Menu' in the 'Virtual Machine Menu Bar' to click on 'Install Guest Additions'. When I open a virtual machine, I don't see a 'Menu Bar' or 'Devices Menu'--let alone the 'Install Guest Additions' button I've been looking for. Whenever I open a virtual machine, all I see are small unlabeled icons at the bottom-right of the window. I've clicked on all of them in search of this "Install Guest Additions' button. When clicking on the CD-icon within the virtual machine, I can check and un-check the 'VBoxGuestAdditions.iso', but this seemingly does nothing. 

Whenever I type the "sh ./VBoxLinuxAdditions.run" command, I simply get an "sh: Can't open ./VBoxLinuxAdditions.run" error. Based on the tutorials I've read, you would think I'm running an entirely different program! I'm utterly confused and don't even know where to begin. I've tried making use of all the self-help I can get.

---

### Post by RyujiOtogi on 2012-02-21
I just gave up on the Server and tried this with my Ubuntu 11.10 x32 bit desktop build with the graphical interface, and it worked fine. I'm not sure why the server was being so impossible. I'll mark this thread as solved but if anyone would care to offer a solution to my problem with the Server-edition I wouldn't mind hearing it!

---

### Post by wildmanne39 on 2012-02-21
Hi, I am glad you have it working in graphical mode at least, I thought the directions would be good enough to work for servers but have never tried to setup a server, It is for sure easier with a graphical interface.
Thanks

---

### Post by misterbiskits on 2012-02-21
> go to the 'Devices Menu' in the 'Virtual Machine Menu Bar' to click on  'Install Guest Additions'. When I open a virtual machine, I don't see a  'Menu Bar' or 'Devices Menu'In the Guest window, try pressing HOST+HOME (Host = Right-CTRL by default) and see if a menu pops up.  One of the options in the menu should be Devices>install Guest Additions.

Alternately, try pressing HOST+F to cycle through screen modes.  In windowed mode the Virtualbox menu should appear where you would normally expect a menu to be in any window.  In fullscreen mode, the menu is located bottom centre, you might have to mouse down to bottom centre to reveal it.

Once you are able to find Devices>install Guest Additions, you will need to install a few things in the guest machine.  First, find out your kernel version

```
$ uname -r
```remember the result, you will need to add it to the next line of code:

```
sudo apt-get install dkms build-essential linux-headers-_*resultofuname-r*_

sudo reboot # i am not sure if this is necessary but it was in the tutorial
sudo mkdir /media/cdrom
sudo mount /dev/cdrom /media/cdrom
cd /media/cdrom
sudo ./VBoxLinuxAdditions.run

```** This is how I installed the Guest Additions in **Ubuntu Server 10.04**, but i suspect the procedure is the same for 11.10.

Let me know if it works out.

---

### Post by jacobl on 2012-03-31
> **RyujiOtogi said:**
> The "sudo mount /dev/cdrom /media/cdrom mount" command only returned a "no medium found on /dev/sr1" message.

> **RyujiOtogi said:**
> I'll mark this thread as solved but if anyone would care to offer a solution to my problem with the Server-edition I wouldn't mind hearing it!

I had the same issue.  Try this:

"sudo mount /dev/sr0 /media/cdrom"

---

