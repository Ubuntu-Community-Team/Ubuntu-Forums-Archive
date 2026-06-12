---
title: "Mouse and Keyboard issue Ubuntu 16.04 LTS"
date: 2016-05-08
forum: New to Ubuntu
---

### Post by Blake_Lee on 2016-05-08
Hello,

I am having issues on boot with my mouse and keyboard. They do not work on boot, occasionally they will. They work in my BIOS and in Windows, just not in Ubuntu. I can get them to work by Unplugging and replugging them several times. It also seems to make no difference if they are in USB 2.0 or 3.0. I have tried several things I've found from google with nothing working. Also When the keyboard is working and the mouse is not lsusb still shows my mouse.

Set up
sda 256GB SSD with Windows Only, sdb 1TB with Ubuntu and partition just for storage. (Grub is on this drive)
Mouse: Razer Naga Epic
Keyboard: Model M with USB cable (No PS/2 or adapter)
Processor i7 4790K
Motherboard: Asus Z97-A, Legacy USB is enabled, fastboot is disabled
GPU: Evga 970

Things I've tried
complete power down from the wall and removing all USBs and waiting
Different USB ports
Various bios settings
adding "iommu=soft" in grub
adding autosuspend=1 in grub
taking out my SSD and reinstalling Ubuntu 16.04.
installing Ubuntu 14.04, UbuntuMate 16.04 neither of these have worked.

---

### Post by Geoffrey_Arndt on 2016-05-08
See below - but know that all Logitech mouse and keyboards are Linux friendly by design, but not much manufacturer support for linux from Razer.    

A competent user did a workaround described here:  [URL="http://norgelinux.blogspot.com/2012/02/razer-anasi-on-arch-linux.html?m=1"]http://norgelinux.blogspot.com/2012/02/razer-anasi-on-arch-linux.html?m=1


[/URL]

---

### Post by Blake_Lee on 2016-05-08
This is to get the extra buttons on the mouse to work, which is not a concern right now. Even if this solved my mouse problem I would still have the keyboard issue.

I just tried arch linux and debian. Mouse does not come on at all. I know it's not the mouse because using the mouse on my laptop with linux they work fine. I feel like it has to be some setting in my bios but I feel like I have honestly tried everything. It also doesn't make sense to me that they will work by simply replugging them in. Any thoughts?

---

### Post by neu5eeCh on 2016-05-09
Just a Hail Mary, but do you have a USB hub? Have you tried plugging your mouse and keyboard into that? This idea is based on your assertion that the mouse works on the Linux Laptop. Have you tried the keyboard on the laptop?

---

### Post by Blake_Lee on 2016-05-09
I do not have a hub. I might can order one to see if that fixes the issue. But The keyboard and mouse both worked on the laptop running ubuntu 14.04

---

### Post by neu5eeCh on 2016-05-09
> **Blake_Lee said:**
> I do not have a hub. I might can order one to see if that fixes the issue. But The keyboard and mouse both worked on the laptop running ubuntu 14.04

Okay, but that advice is a *Hail Mary*. I wouldn't suggest you buy one unless you think you'll use it if and when my suggestion doesn't work.

---

### Post by Blake_Lee on 2016-05-09
I'm willing to try anything shy of replacing my Motherboard. I ordered a USB PCI-E card to see if that will work. Plus I can always use it if not.

---

### Post by Geoffrey_Arndt on 2016-05-10
Willing to try anything but not willing to try an inexpensive Logitech mouse, keyboard, or combo, . . . either wired or wireless???.    I like putting my money into companies that do a competent job writing linux drivers.

---

### Post by Blake_Lee on 2016-05-10
That's not a problem. If you read earlier both the keyboard and mouse work with Ubuntu on my laptop.

---

### Post by Blake_Lee on 2016-05-13
Just in case anyone is wondering or having a similar issue the $30 PCI-E USB 3.0 card resolved my issue. Everything works perfectly, No need for a logitec mouse and keyboard.

---

### Post by burtms@gmail.com on 2016-12-31
I can switch between several desktops, and some rarely or never show the problem, others do:

GNOME, GNOME Flashback (Compiz), GNOME Flashback (Metacity), and Ubuntu have the problem.

LXDE, Openbox, Xfce Session rarely or never exhibit the problem.

I have 3 mice and only one has the issue:
Ativa Model 406130 has the problem.
IBM M-UY101 has no problem.
Microsoft Basic Optical Mouse has no problem.

[http://askubuntu.com/questions/489907/ubuntu-14-04-frequent-mouse-freeze](http://askubuntu.com/questions/489907/ubuntu-14-04-frequent-mouse-freeze) shows ways to clear the problem. Once cleared, I have not seen it come back during a login session. (I'm not sure about what happens after logging off.)

---

### Post by burtms@gmail.com on 2016-12-31
FYI, the problem still exists in 16.10.

---

### Post by victorl on 2017-01-22
I want to add my solution to this problem. (System: ubuntu 16.04LT, on a 6-core Intel Sandybridge Extreme desk top system, which I built on my own many years ago)

Problem description: 
1. Many times when the machine was waked up from suspend mode, the keyboard would not work - e.g., cannot key in password. I could move the mouse pointer. Clicking had no effect as well. This happened randomly, but it started to become more frequent.
2. It also happened that in the middle of my work, such as openning up a file, the machine would suddenly not respond. Rebooting was my only method.
3. ctrl+alt + F1 was my only way to get a terminal. use ctrl+alt + f7 to come back. This did not help me much, since I was clueless what to do with it. This could be the right place you want to apply the solution below. 
4. After reading some post, I reinstalled the graphic display monitor to gdm, this ended up messing up things more. The ubuntu system will hang to the purple login screen, complaining "the graphic card and input device settings could not be detected correctly." I almost ended up reinstalling ubuntu, but I discarded that idea because reinstalling means wiping out everything. I would have to figure out a way to get my documents/data out.

Solution:
1. Rebooting the machine from the Grub advanced menu by press ESC or F2 when the system is entering the dual-boot menu. One of the grub menu option will allow you to open a terminal window.
2. mount -o remount, rw/                      //this command will mount the file system, otherwise, the following step will complain "failed to write temp state file..." or other error.
3. sudo dpkg-reconfigure lightdm           //lightdm was the default installation. I installed "gdm" in this same way to solve the problem, but it was fatal. What I am doing here is basically reinstalling lightdm. From all the reading I had, lightdm should actually work better than gdm in ubuntu, but somehow the system updates messed up the initial lightdm installation. 

I have had lightdm reinstalled for more than two weeks now. So far the keyboard/mouse have not had any issue. I thought I should write this done to help other people.

Update: After writing the above post this morning, I started to have a frozen screen when using chrome. It is the 3rd times today - I just disabled the hardware acceleration in chrome settings. Hopefully this will solve the problem. Note: I have 8GB RAM.

---

### Post by dakotapa on 2017-04-21
I tried installing the ckb beta drivers. I have a corsair rgb strafe k70 and the sabre mouse.

what worked for me was using a little usb hub i had lying around.

unplugged keyboard and mouse from the motherboard. Plugged in hub and keyboard and mouse and 10 seconds later both worked.

---

