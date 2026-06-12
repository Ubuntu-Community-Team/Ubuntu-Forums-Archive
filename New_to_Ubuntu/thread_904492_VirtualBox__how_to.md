---
title: "VirtualBox  how to"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Badoxide on 2008-08-29
Hello.To all

First may you all have a safe weekend. Well here gos I have downloaded the virtualbox_1.6.4-33808_Ubuntu_hardy_i386.deb  which I am going to install, but wanted to ask before I go and do, so.

I have a spare partition with 20Gb free space on it I would like to install the Virtual box on to, but I have no idea how to go about doing this. Could someone walk me, through the steps to get this done.

I am trying not to install this in my home dir.

Thank you

Badoxide

---

### Post by tuxxy on 2008-08-29
Heres a guide to installing and setting up a virtual drive

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by bumanie on 2008-08-29
[Here's a guide ]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html")that includes enabling usb support. You need the "free for home use" proprietary version.

---

### Post by Badoxide on 2008-08-29
Hi.tuxxy

Thanks for the fast help here. But I am not sure I follow what is being said on that site, or I have missed something. When installing will I have a chance to say where I'd like to install the VBox. Sorry if its on the site I just did not see it.

Also do I need to have an ISO at hand to install the VBox? or this can all be done after the install of the VBox. What I am trying to do is install it to me, spare partition then run say a live CD off the VBox. 

Thank you

Badoxide

---

### Post by tuxxy on 2008-08-29
You could create your own virtual partition of 20GB once virtualbox is installed, or are you trying to access an existing windows install on that 20GB partition through virtualbox?

---

### Post by Badoxide on 2008-08-29
Hey.tuxxy

I am running all out ubuntu no more windows, for me ;) But yes I am looking to install it to the free 20Gb if it can be done.

@ bumanie

Sorry my friend I didn't see you there. I will have a look at the link thanks for stopping by to help.

Thank you

Badoxide

---

### Post by tuxxy on 2008-08-29
Well I would use a virtual partition, it should be much easier and quicker to do, it shows you how to do this in the guide I linked.  

Heres a guide if you want to try it though 

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

---

### Post by Badoxide on 2008-08-29
Hey.tuxxy

Again thanks for all the help I think I'll go with the first links you posted, for me I'll post back how all gos for anyone else looking to try this. Have a great weekend.

Thank you

Badoxide

---

### Post by Davedom6766 on 2008-08-29
wow thanks I was looking around for the same type of thing this helped a lot

---

### Post by lovinglinux on 2008-08-29
You don't have to install the virtualbox onto other partition. The Virtualbox software itself will not occupy too much space. After installing the Virtualbox software you will start to create virtual machines. A virtual machine requires a virtual disk, which is essentially a file under your host system, with *.vdi extension. During the process of creating the virtual machine, you can choose the file name and directory where the virtual disk will be saved. At this point you can create the virtual disk for your virtual machine inside your 20Gb spare partition. If you create a virtual disk with less than 20Gb it will not occupy the entire spare partition, so you still can use it to save regular files (not created by the virtual machine).

Step-by-step:

1 - Double click the virtualbox_1.6.4-33808_Ubuntu_hardy_i386.deb and follow the instructions

2 - Once the Virtualbox software is installed open it and click File > Machine > New

3 - In the Wizard screen type a name for the Machine like "WindowsXP" or "Virtualbox 1" or something else, select the guest OS in the drop down list and click next.

4 - Select how much memory you will allocate for the virtual machine (must be considerably less than how much RAM you really have) and select next.

5 - Now is time to create the virtual disk. Since you don't have one, select "New". A new wizard will popup. Select "Dynamically expanding image", so you don't have to use the entire 20Gb partition at the beginning. When you install the OS and other software the disk size will be dynamically increased. Click next.

6 - Now you will choose the directory and file name for your virtual disk. Since you want to put the virtual machine on that 20Gb partition, simply put a name you identify as the disk of your virtual machine in the "Image File Name" input box. Click the folder icon on the right to select the place were it will be saved (your 20Gb partition). Then select the "Image Size", which is the initial size of your dynamically expanding disk. Remember that you don't have to put 20Gb here, because you probably won't need that much and if you do, the disk will be automatically resized if enough space is provided in the partition you are saving it.

7 - Click next until this wizard closes and you see the previous one. You should see the newly created virtual disk int he input box "Boot Hard Disk (Primary Master)". Click Next and Finish. Your virtual machine would be listed in the virtualbox software.

8 - Select the machine you have created than click Machine >  Settings > Advanced Tab. Click the Folder in the right side of the "Snapshot Folder" input field to select were you are going to save the machine snapshots. This could be the same 20Gb partition, but make sure you create a subfolder for each machine, with a Snapshots subfolder inside.  For example in  my system, the virtual machines are saved into a separate disk under /media/  mount point (see path below)

/media/disk/Machines/Virtualbox 3/Snapshots

were "/disk" is my second HD, "/Machines" is were I put everything related to virtual machines, "/Virtualbox 3" is the virtual machine I'm creating for this tutorial and "/Snapshots" is the folder were the snapshots of this particular machine will be saved. 

You can configure other options as you like (read the manual). To start the machine, simply select the machine you want to start and click the green arrow in the main menu.

That's it. Please read the manual to understand how it works and how to configure the other options properly. You will need to mount a virtual CD/DVD or iso file to boot the virtual machine with the LiveCD or similar, otherwise it will start but no OS will be found and you will receive an error message.

---

### Post by Badoxide on 2008-08-29
Hello.lovinglinux

Wow thanks this is what I was thinking about doing. I like the way you setup your VBox. Now if I may could you have a look at this here.


Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2675    21486906   83  Linux
/dev/sda2            2676        5350    21486937+  83  Linux
/dev/sda3            5351        5654     2441880   82  Linux swap / Solaris
/dev/sda4            5655       30401   198780277+  83  Linux

I was thinking of installing in say /dev/sda2  I am not all to sure this is what I should be doing. I just can't seem to make out where this thing goes. If it is #2 how would I go about sending the install there.


Thank you

Badoxide

---

### Post by lovinglinux on 2008-08-29
> **Badoxide said:**
> Hello.lovinglinux

Wow thanks this is what I was thinking about doing. I like the way you setup your VBox. Now if I may could you have a look at this here.


Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2675    21486906   83  Linux
/dev/sda2            2676        5350    21486937+  83  Linux
/dev/sda3            5351        5654     2441880   82  Linux swap / Solaris
/dev/sda4            5655       30401   198780277+  83  Linux

I was thinking of installing in say /dev/sda2  I am not all to sure this is what I should be doing. I just can't seem to make out where this thing goes. If it is #2 how would I go about sending the install there.


Thank you

Badoxide

We need to speak the same language. When you say "installing" you are talking about creating a virtual machine, not installing Virtualbox software right? Because the Virtualbox software (the one distributed by Sun, that allow us to create virtual machines like VMWare) should be installed as a regular package using the deb file you downloaded. The package manager will handle the installation and it's paths. 

You should understand that a virtual machine needs a virtual drive, but this is not necessarily (i'm not sure if it is even possible)  another standalone disk or entire partition like when you setup another OS on dual-boot. I plain terms, a virtual machine drive is a self-contained file ("like a zip" file) inside any folder of your host computer. You can put it anywhere you want. You can even move it if you make it dynamically expanding and it grows too much. You can even duplicate the file to create new machines without installing the OS and you favorite applications again. 

Take a look in the folder structure below. I have omitted the "Virtual Machines" top level folder in my previous post to avoid confusion, because it doesn't have to be named "Virtual", "Machine" or "Virtual Machine". It could have any name you want, it is just a folder were I put all virtual machines.

[[IMG]http://img527.imageshack.us/img527/7619/screenshotqs5.th.png[/IMG]](http://img527.imageshack.us/my.php?image=screenshotqs5.png)

So the complete structure is like this:

> Virtual Machines (just a folder to organize myself)
  >> Machines (where I put logs, snapshots and machine configuration files)

       >>> Virtualbox 1 (all things related to machine 1)
              >>>> Logs (automatically created for logs)
              >>>> Snapshots (folder path configured by me to save snapshots)

       >>> Virtualbox 2 (all things related to machine 2)
              >>>> Logs (automatically created for logs)
              >>>> Snapshots (folder path configured by me to save snapshots)

  >> VDI (were I put all virtual drives)

The VDI folder is were I save all virtual drive files. In other words, the self-contained files that contain the installed OS and software of the virtual machines. These are the biggest files of the initial virtualbox setup. Nevertheless, the snapshots folders will probably become bigger than this one if you save a lot of snapshots.

So, everything is under the "Virtual Machines" folder, which is a regular folder like all nested folders below it. This folder tree is on another disc just because I wiped Windows from it and this space was available, but I could have saved it under my home directory.

EDIT: if you look inside the VDI folder you will notice 4 files. I have named them after the corresponding machines to facilitate identification in the File Manager and included letters C and D that represent the virtual drive inside the virtual machine. This is not necessary, I just do it if I need to backup, delete or move my virtual drives. For example, I know that "Virtualbox 1C.vdi" is the "C:/" drive of my Windows virtual box and "Virtuabox 1D.vdi" is the "D:/" drive of the same machine. The file "Virtualbox 2C.vdi" is the root mount point of my Linux virtualbox and the file "Virtualbox 2D.vdi" is the /home mount point of my Linux virtualbox.

So, you don't have to worry about partitioning or mounting any drive, just create your virtual machines and save the VDI files (virtual drives) somewhere with enough available space.

---

### Post by Badoxide on 2008-08-29
Hi.lovinglinux

OK I am trying to follow you on this. So there is no need to install VBox ??? I can just extract it to a folder that I want, and just move it when I feel like.

What I would like to do if it can be done is to make a folder in say /dev/sda2 then extract it, and run from there. Do I have you all wrong here am I driving you nut's Yet.

B-O

---

### Post by AndyCooll on 2008-08-29
First you need to install VirtualBox. However that is just the software application for creating and running virtual drives. 

Once you've installed VirtualBox you start it up and from there you can create virtual drives or open up already created ones. The virtual drives can be stored anywhere (as mentioned before, they're like zip files) and they run in a Window, just the way Firefox or Open Office runs in a window.

Think of virtualisation as two parts, the virtual-drive itself and the app to run. Virtualbox is the app that runs it. Just as when you play music you need two parts, the audio file itself and the player.

:cool:

---

### Post by wolfie2x on 2008-08-29
> **Badoxide said:**
> Hi.lovinglinux

OK I am trying to follow you on this. So there is no need to install VBox ??? I can just extract it to a folder that I want, and just move it when I feel like.

What I would like to do if it can be done is to make a folder in say /dev/sda2 then extract it, and run from there. Do I have you all wrong here am I driving you nut's Yet.

B-O

Badoxide I think you have got the concept of virtual machines mixed up a bit. First clean up ur mind; unlearn what u already know; and think fresh.. it's really simple.

VirtualBox is a *small* *program* like firefox. It's not a *virtual machine*; u install it just like a normal program on your ubuntu partition. you don't need separate partitions; nothing complicated there.

Now you need to *create* a *virtual machine* (lets say WindowsXP). This creates a *big* file; about 4GB. this is big, but it's still just a normal *file*; you don't need a dedicated partition for it! put it anywhere you want; you can even move it later since it's just a file.

how you *create* the virtual machine is, first u run VirtualBox, then insert your Windows CD, and create the virtual machine. done.

how you *run* the virtual machine is you run VirtualBox, select the created WinXP, and press start. done. 

hope this gives u a better picture..

---

### Post by Leonivek on 2008-08-29
**I think he's confusing dual-booting and virtual machines.  **

What he needs is instructions with **screenshots**:  
[http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html](http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html).

**EDIT:**  Although those instructions are for Hardy, they can be followed fairly the same for Gutsy.  Just **watch the filenames** (the .deb file you downloaded) used when copying and pasting terminal commands; make sure you change them to match the actual filename of the file YOU have.

---

### Post by lovinglinux on 2008-08-29
> **Badoxide said:**
> Hi.lovinglinux

OK I am trying to follow you on this. So there is no need to install VBox ??? I can just extract it to a folder that I want, and just move it when I feel like.
B-O

No. You need to install VBox like any other software you download. Like AndyCooll mentioned, the VBox is the "player". You need this player installed on your machine. Just click twice over the file you have already downloaded and you will be prompted for installation. It will not be extracted, it will be installed. Don't worry about the machines yet and don't worry about where you are gonna put all the stuff. The installation is practically automatic and will not harm you system.

> **Badoxide said:**
> Hi.lovinglinux
What I would like to do if it can be done is to make a folder in say /dev/sda2 then extract it, and run from there. Do I have you all wrong here am I driving you nut's Yet.
B-O

The file you have downloaded has a "deb" extension. This is not like "zip", "rar" or other file that can be extracted. Think about it more like an "exe" file on Windows. You click over it and the computer will help you to install. It doesn't matter where this file is when you click it. Just click twice over it and follow the instructions.

---

### Post by Badoxide on 2008-08-31
Hey.To all

Well everyone I'd like to say a great big thank you to all of you. With your help I was able to get VBox installed, and running ;) wow its cool to have one OS running within another gee I hope I just said that right.

I hope all of you have had a good weekend ;) again a ton of thanks to all of you.

B-O

---

### Post by lovinglinux on 2008-08-31
> **Badoxide said:**
> Hey.To all

Well everyone I'd like to say a great big thank you to all of you. With your help I was able to get VBox installed, and running ;) 

You are welcome. I'm glad you make it.

> **Badoxide said:**
> wow its cool to have one OS running within another gee I hope I just said that right.

Yeah, it's cool, but awesome is spinning the compiz cube with Windows inside a VBox exhibiting a nice BSOD. \\:D/

Good weekend for you too.

---

