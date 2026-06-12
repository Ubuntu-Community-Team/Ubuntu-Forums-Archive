---
title: "Enhanced Gfxboot: Mepis Version"
date: 2008-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by wkdude18 on 2008-07-30
Not For the Linux Wary!!!

Prerequisites: Have a Second Computer or a system rescue CD at hand like INSERT or System Rescue CD or even GParted. In case something goes wrong you'll be able to download and burn a cd iso so you can save your system or already have a CD on hand to do so.

Optimal Conditions: Decent Linux/CLI knowledge, knowledge of what partition/drive your Ubuntu install is on, maybe some experience with a grub prompt (doesn't need to be much).

    Have you ever heard of SuSE's gfxboot? Have you ever used it? Have you ever used the standard splashimage feature that comes with Ubuntu? Don't have any idea what I'm talking about? Well, I'm about to tell you a way to make your boot menu look fabulous.
   Mepis's gfxboot is different form SuSE's because it has a different layout and it supports larger image sizes according to CatDude, [http://www.murga-linux.com/puppy/viewtopic.php?p=194724#194724](http://www.murga-linux.com/puppy/viewtopic.php?p=194724#194724). Mepis also allows for a special feature; you can set the likelihood that a dancing penguin animation appears instead of your normal splash. In this tutorial, I will go through the process of installing and editing Mepis's GRUB patch.

STAGE 1 Installing Mepis Gfxboot

   Unfortunately, I have no .deb file for you all today, but I find the process I use is also quite easy. First, make a backup copy of your grub files. This is done by making a directory (I prefer /home/username/Grub_Backup) in any location as long as you remember it, and then ```
cd /boot/grub
ls
sudo cp * /path/to/your/directory/
```
If all goes well, the contents of your grub backup directory should be the same of those as your /boot/grub. Make sure you try to copy with root privileges.
    Second, extract the tarball to a directory and copy the contents of the Grub-Files directory into your /boot/grub. If you want to use a GUI to do this enter:```
sudo nautilus
```. Make sure however, when you copy the files, select the option Replace All when an error window comes up (which it should if you have Grub installed), to save yourself time and to ensure a correct outcome. If not, do it by command line. ```
pwd
(correct response) ???/Grub-Files/
sudo cp * /boot/grub/
``` Now you should have the copies of the Mepis Gfxboot installed for your grub files.
     If you are unfamiliar with where your Ubuntu is installed enter ```
sudo fdisk -l
``` and look for the name of your hard drive/partition where Ubuntu is installed. If this does not help you at all, reply with an inquiry and I'll try to help you out. Nonetheless, if you now know where your Ubuntu installation is, say sda1, we can finish installing. Now enter ```
sudo grub
``` You should see a message like Checking for BIOS drives this may take a while. Wait patiently until you see the grub prompt (grub >). First enter ```
root (hd[# of order of hard disk where Ubuntu is installed-1],[partition number on hard disk -1])
``` For example, lets say /dev/sda is the third hard disk on your computer, so in this case I would enter ```
root (hd[3-1],[1-1])
root (hd2,0)
```. Remember, the first was an explanation of the math, the second was the example. Now, if you have grub installed on a root partition do ```
setup (hd2,0)
``` using the same example as above. If you want grub installed in the MBR or have no idea what I'm talking about (but please try to learn if your computer is a dual/multi-boot) enter ```
setup (hd0)
```. If this all becoming too confusing for you, I recommend reading, (not necessarily acting upon) Saikee's great post at Justlinux, [http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959). So again in my example I would do ```
sudo grub
``` wait for the grub prompt to load and then at grub> ```
root (hd2,0)
```and if I wanted to install on the MBR ```
root (hd0)
```. In this example Gfxboot should be the first thing to show up after the BIOS on your computer. 
    Now if you have SuSE Gfxboot installed, understand that Mepis and SuSE gfxboots are NOT COMPATIBLE!!! Therefore, if you want to immediately see the fruits of your labor, use one of the gfxboot files I included in the tarball (message.something). I will tell you how. First, lets make sure that you have the same GRUB configuration restored from previously. First, go to your Grub_Backup folder or whatever you named it and ```
sudo cp menu.lst /boot/grub/
``` menu.lst is the configuration file for grub, except for in some distros where it grub.conf is symlinked to it if I have my facts down straight (Ubu uses menu.lst). Now copy one of the message files of your choice to /boot/grub ```
sudo cp message.(something) /boot/grub/
``` Now ```
cd /boot/grub
sudo nano menu.lst
``` Add the following line near right before the OS entries```
gfxmenu /boot/grub/message.(something)
```This tells GRUB what cpio archive to use to setup the graphical menu.
    First, reboot your computer and see if all of this is working for you, if not ask me to help you out. Please forgive unclear instructions, this is my first tutorial. If all goes well on to 

STAGE 2 Editing Mepis Gfxboot

   I have included several gfxboot files into

---

