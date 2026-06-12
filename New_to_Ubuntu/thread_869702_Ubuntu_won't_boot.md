---
title: "Ubuntu won't boot"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Petrovic on 2008-07-25
I'm very green when it comes to working with Linux. I've had long term experience, and now suffer from long term anger with regards to Macro$haft Bindows. So, I thought I would try somethin new. However, I'm having some troubles with getting Ubuntu to boot. 
I've given Ubuntu an old Quantum Fireball 6.4gb IDE drive to itself to fun with, and set the jumper to 'Master'. Have unplugged all other SATA and the other IDE drive to minimise problems with selecting a primary drive like Bindows sometimes does. Last time I didn't remove drives, Bindows tried to install on what it called f: 
I go through the installation process completing the 7 steps and letting it go it's own. It then drops me onto the Ubuntu 'desktop' with the "install" and "examples" icons and what seems to be a fully working system.  
However, when I reboot the computer, I end up with "Disk boot error. Insert system disk and press enter". I can press enter till the cows come home, but it will keep restating the message till I either hit it with somethin out of frustration and power down, or I stick the CD in the drive and boot Ubuntu from CD. I am currently working in CD loaded Ubuntu.
Any assistance will be muchly appreciated as even with the limited use I've had, I'm already preffering it over Macro$haft Bindows
I'm running an AMD 3.2Ghz 64bit on MSI K8N Platinum SLI with 512mb Corsair 500mhz DDR and 2 Nvidia 6600gt's 128mb with SLI bridge (tho not functioning at present)
Cheers.

---

### Post by pedro_orange on 2008-07-25
> **Petrovic said:**
> 
I go through the installation process completing the 7 steps and letting it go it's own. It then drops me onto the Ubuntu 'desktop' with the "install" and "examples" icons and what seems to be a fully working system.  


Do you mean you boot from your LiveCD? And get your desktop.
THEN, you double click the install icon and do the 7 steps?

---

### Post by plucky on 2008-07-25
Have you changed the boot order in the BIOS to boot the hard disk?

Does the BIOS see it as HD0?

If that doesn't work,boot the live CD and post output of ```
sudo fdisk -l
``` That is lowercase L not a 1.

Good Luck

---

### Post by Petrovic on 2008-07-25
pedro: I've tried two ways. I've loaded the cd and worked through the installation menu offered there, and after reboot failure and reformatting, I've also tried clicking on the icon within Ububtu and installing there with the same result.

Plucky: Yeah, BIOS recieves the HD on CH.0. Really sorry to ask, but how do I enter command lines?

---

### Post by pedro_orange on 2008-07-25
> **Petrovic said:**
>  Really sorry to ask, but how do I enter command lines?

Boot into Ubuntu with the live cd, and go Applications > Accessories > Terminal

---

### Post by Petrovic on 2008-07-25
When I used the command above, this is what was displayed:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52c99abd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         743     5968116   83  Linux
/dev/sda2             744         784      329332+   5  Extended
/dev/sda5             744         784      329301   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

Where do I go from here?

---

### Post by some1here on 2008-07-25
Try this:

```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

Command (m for help): a
Partition number (1-5): 1

Command (m for help): w
```

reboot

---

### Post by Petrovic on 2008-07-25
> **some1here said:**
> Try this:

```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

Command (m for help): a
Partition number (1-5): 1

Command (m for help): w
```

reboot


Tried these steps and the halting error is now "Problem loading operating system" So, it has made a difference of sorts, however, it still won't load ](*,)

*Note: Sorry for the delay. Was havin a spat with the ISP. Stupid artards!

---

### Post by plucky on 2008-07-25
> Tried these steps and the halting error is now "Problem loading operating system" So, it has made a difference of sorts, however, it still won't load

I think all that command does is toggle the boot flag on the partition.

Boot the Live CD

Open a terminal **Applications > Accessories > Terminal** then input ```
gksudo nautilus
``` find your sda1 partition and double click on it.This should mount the partition and it should appear on your desktop.Click on the icon and it should open the file browser.Navigate to **Boot > Grub** and click on **menu.lst** Post the output of that file to the forum so that we can see if it is correct.

I think you need to write grub to the MBR of the drive.

To setup grub to the MBR use these commands in a terminal window
```
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quit
```

Provided there are no errors,you should have written grub boot to the MBR and so now you should be able to boot provided the menu.lst file is ok.


Good Luck

---

### Post by Petrovic on 2008-07-25
Alrighty. I found the "boot" folder within the file browser which opened after using the command given before, however there was no sign of the afore mentioned **menu.lst**. There were five files named "abi-2.6.24-19-generic" "config-2.6.24-19-generic" "memtest86+.bin" "System.map-2.6.24-19-generic" and "vmlinuz-2.6.24-19-generic" located within /boot
Just to make sure that I'm looking in the right place, this sda1 partition you're speeking of is aka "File System" as listed in the nav box on the left of the window yeah?

---

### Post by pedro_orange on 2008-07-25
You should find it in /boot/grub/menu.lst

(grub being a folder within boot)

Among other things in that file you want to find the bits that look like:

```
title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=3fe9dc7d-ee53-4b38-bc76-9ca9147cd42b ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet
```

And post them here.

---

### Post by philinux on 2008-07-25
You need to look in the Grub folder within Boot.

---

### Post by Petrovic on 2008-07-25
UUmm...yeah....about that Grub folder....it's not there. There's only the 5 files that I named in my previous post.

---

### Post by philinux on 2008-07-25
Thats the problem then no Grub which is the bootloader.

Use the livecd to install it follow this guide.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Petrovic on 2008-07-25
Thanks for the help guys. Am trying philinux's link now. Will let you know if I have any more drama's.

---

### Post by Petrovic on 2008-07-26
> **plucky said:**
> 

I think you need to write grub to the MBR of the drive.

To setup grub to the MBR use these commands in a terminal window
```
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quit
```

Provided there are no errors,you should have written grub boot to the MBR and so now you should be able to boot provided the menu.lst file is ok.


Good Luck

Ok, I'm up to this set of steps after following the instructions philinux gave via the link, however, grub is located in / instead of /boot. I've tried to copy-paste it into /boot but it won't have a bar of it. It will load into grub when I reboot as this is what happened last time. Stage1 is located within this folder also. When I >find /grub/stage1 it locates on hd0,0 but >find /boot/grub/stage1 will find nothing. If I run >setup (hd0) and grub isn't in /boot will it still work, or will this just install stuff where it can't be read on boot? Also, there is no menu.lst within /grub. Will this be created when i >setup (hd0) or is this something needed for this process to happen?

---

### Post by plucky on 2008-07-26
> however, grub is located in / instead of /boot. I've tried to copy-paste it into /boot but it won't have a bar of it

To do that you will need to be in super user mode.```
gksudo nautilus
``` will get you into super user mode.

**Have you actually mounted your root partition?** 

Make sure you are looking at your hard drive and not the CD,as the files are all the same.You will need to mount the drive to make changes to it.

> If I run >setup (hd0) and grub isn't in /boot will it still work, or will this just install stuff where it can't be read on boot?

The setup (hd0) command is writing the stage 1 file to the MBR of HD0,and the root (hd0,0) command is telling grub which partition to look for the boot files.I am not sure, but I assume it will look for the files in the /boot partition as that is where they should be located.

> Also, there is no menu.lst within /grub. Will this be created when i >setup (hd0) or is this something needed for this process to happen? 

No,menu.lst is generated during the install of the operating system and it looks for all the different operating systems on your disks and puts lines for booting different operating systems into menu.lst.

There is a command that will generate a new menu.lst,but I am not sure how it works from a Live CD.```
sudo update-grub
```

See this [link](http://users.bigpond.net.au/hermanzone/p15.htm) for information on grub.

Might it not be quicker to re-install the operating system and make sure it writes grub to the MBR and generates a menu.lst?

---

### Post by Petrovic on 2008-07-28
Plucky, Pedro and Philinix, thanks heaps for ya help. Unfortunately, it seems as tho there's somethin wrong in the system somewhere, as every time I try to reinstall it either hangs, or bypasses the cd loader install and the desktop installer either won't run or hangs between 15%-90%. When I eventually get the cash to buy myself a new system, I shall try once again to get a linux based os happenin. 
Any drama's, I'll head here to this post before hasseling you knowledgable peops.
Peace out.

---

### Post by Tod Merley on 2008-07-28
> **Petrovic said:**
> Plucky, Pedro and Philinix, thanks heaps for ya help. Unfortunately, it seems as tho there's somethin wrong in the system somewhere, as every time I try to reinstall it either hangs, or bypasses the cd loader install and the desktop installer either won't run or hangs between 15%-90%. When I eventually get the cash to buy myself a new system, I shall try once again to get a linux based os happenin. 
Any drama's, I'll head here to this post before hasseling you knowledgable peops.
Peace out.

Hi Petrovic!

There is a folder /var/log  which may contain a file "installer" or similar with a record of the install and why it failed.  I have never actually experimented with this so I do not know if it resides within the RAMdisk of the Live system or on the Hard Drive (I would guss the RAMdisk - pulling a terminal in the live mode after a failed install).  You may do well to look at it and several other of the files there for clues, specifically "messages", "dmesg", and perhaps "system".

You may do well to wait for the updated HW, you will be happier with it anyway.  However, you also have here a good learning enviornment.

To navigate to the folder in the terminal type:

cd /var/log

To list the files there type:

ls

For a more detailed listing type"

ls -l -a

To view a man (ual) file about any of these commands type:

To view a file there type:

man command  (e.g. man ls)

less filetoview  (e.g. less messages)

Have a lot of fun!

Tod

---

