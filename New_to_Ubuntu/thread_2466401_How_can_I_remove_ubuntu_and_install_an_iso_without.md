---
title: "How can I remove ubuntu and install an iso without usb or cd?"
date: 2021-08-26
forum: New to Ubuntu
---

### Post by doxne on 2021-08-26
In summary:
I want to partition the hard disk and put an iso on it, then load the iso and erase ubuntu. I need help to know how to do it.

No need to read:
I want to format ubuntu and install an iso of windows 10 lite, it is quite difficult to use linux for games, many do not load me so I decided to go back to a version of windows 10 but lite, I have tried to do it with usb and cd, but for some reason I a line appears when I load them and the boot does not work. Look for solutions and nothing, so what I want is to make a disk partition, put an iso on it and start it to format the partition with ubuntu. I was going to do it with EasyBcD, but it doesn't work and I can't find alternatives that I can understand.
[IMG]https://i.ibb.co/g4mJkYP/d.png[/IMG]

---

### Post by C.S.Cameron on 2021-08-26
See if this is what you need: [https://askubuntu.com/questions/1337487/using-ubuntu-to-reinstall-windows-10-using-grub2-and-no-usb](https://askubuntu.com/questions/1337487/using-ubuntu-to-reinstall-windows-10-using-grub2-and-no-usb)

---

### Post by doxne on 2021-08-27
> **C.S.Cameron said:**
> See if this is what you need: [https://askubuntu.com/questions/1337487/using-ubuntu-to-reinstall-windows-10-using-grub2-and-no-usb](https://askubuntu.com/questions/1337487/using-ubuntu-to-reinstall-windows-10-using-grub2-and-no-usb)

I can't make a partition, I'm new to linux, I don't understand how I can do it, I can't unmount the partition because it has the OS.
[IMG]https://i.ibb.co/vhwbK6D/Captura-de-pantalla-de-2021-08-27-02-01-49.png[/IMG]

---

### Post by yancek on 2021-08-27
First off, if you want to create a bootable windows from a usb/DVD, I would suggest you go to a windows forum of which there are many.

If you can't your windows iso bootable on a flash drive, why do you think it will work on a hard drive?  What methods/steps did you use to create a bootable windows?  It's certainly possible if you leave Ubuntu on the drive to boot the windows extracted iso just as it is without the Ubuntu bootloader, using similar methods to creating the bootable usb..

> what I want is to make a disk partition, put an iso on it and start it to format the partition with ubuntu. 

You have Ubuntu on a very large partition so you could shrink that and create and ntfs partition to put your extracted windows iso on.  You can NOT do this from a running system, be it Ubuntu, another Linux or windows.  Use the USB/DVD on which you had the Ubuntu install iso as it has GParted on it.  You click the Partition tab at the top and then click the Resize tab in the drop down menu and shrink it to about 200GB and use create a 10GB partition on which to put the windows installer, then create another ntfs partition on which to install windows. 

Did you have windows 10 previously installed?

---

### Post by grahammechanical on 2021-08-27
It is a few years since I downloaded from Microsoft an evaluation ISO of Windows 8 and tried to install it. I had already created unallocated space at the front of the hard drive by using a Ubuntu live session and GParted to shrink my Ubuntu partition. I failed because I ran the Windows 8 live session and selected Install and Windows 8 did not install.

I succeeded when I ran the Windows 8 live session again and then choose to run the partition manager and use that to turn the unallocated space into a Windows partition with a Windows format that the installer could detect and offer to install Windows 8 into.

You may have to do something similar if you wish to dual boot with Ubuntu as I wanted to do. But, that is not what you want. So, I agree with earlier advice that you seek instruction from a Windows web site. Just to show how helpful we are at Ubuntu forums, please read these instructions.

> Select the partition with the current installation (usually "Drive 0"), and click the **Delete** button.

[LIST=1]
[*] **Quick tip:** If "Drive 0" has multiple partitions, you  have to select and delete each partition to allow the setup to use the  entire hard drive for the new clean installation. The Windows 10 setup  will create the required partitions automatically during the process.  Also, it's not necessary to delete the partitions on secondary drives.
[/LIST]
 [https://www.windowscentral.com/how-do-clean-installation-windows-10](https://www.windowscentral.com/how-do-clean-installation-windows-10)

Regards

---

### Post by ActionParsnip on 2021-08-27
I'd just borrow a USB stick with the Windows installer on. Saves you a tonne of hassle

---

### Post by C.S.Cameron on 2021-08-28
**Modify root Partition without USB**

Since you do not already have any spare space to create extra partitions, You can boot an Ubuntu ISO **toram** using Ubuntu's GRUB and modify the root partition.

1) Put the Ubuntu ISO file on your desktop.

2) Add menuentry for ISO to GRUB, (Add the following menu entry to **/etc/grub.d/40_custom** and then run **sudo update-grub** in terminal):

```

menuentry "ubuntu-20.04.2-desktop-amd64.iso desktop toram" {
       set isofile="/home/cscameron/Desktop/ubuntu-20.04.2-desktop-amd64.iso"
       loopback loop (hd0,3)$isofile
       linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile fsck.mode=skip toram
       initrd (loop)/casper/initrd
}
```
       (Use your own username, not mine).

3) Reboot and select **"ubuntu-20.04.2-desktop-amd64.iso desktop toram"** from the GRUB menu.

4) Once booted open terminal and run:

```
sudo umount -lrf /isodevice
```

5) You should now be able to shrink the root partition and add more partitions using GParted.

**If you have a spare USB drive 8GB or larger,** the method on the following page using **mkusb** might be easier:

[https://askubuntu.com/a/1359829/43926](https://askubuntu.com/a/1359829/43926)



.

---

### Post by doxne on 2021-08-29
> **C.S.Cameron said:**
> **Modify root Partition without USB**

Since you do not already have any spare space to create extra partitions, You can boot an Ubuntu ISO **toram** using Ubuntu's GRUB and modify the root partition.

1) Put the Ubuntu ISO file on your desktop.

2) Add menuentry for ISO to GRUB, (Add the following menu entry to **/etc/grub.d/40_custom** and then run **sudo update-grub** in terminal):

```

menuentry "ubuntu-20.04.2-desktop-amd64.iso desktop toram" {
       set isofile="/home/cscameron/Desktop/ubuntu-20.04.2-desktop-amd64.iso"
       loopback loop (hd0,3)$isofile
       linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile fsck.mode=skip toram
       initrd (loop)/casper/initrd
}
```
       (Use your own username, not mine).

3) Reboot and select **"ubuntu-20.04.2-desktop-amd64.iso desktop toram"** from the GRUB menu.

4) Once booted open terminal and run:

```
sudo umount -lrf /isodevice
```

5) You should now be able to shrink the root partition and add more partitions using GParted.

**If you have a spare USB drive 8GB or larger,** the method on the following page using **mkusb** might be easier:

[https://askubuntu.com/a/1359829/43926](https://askubuntu.com/a/1359829/43926)



.

Well, I would like to do it through a usb, I have a usb, that usb has the iso already configured of windows. But there is a problem, nothing happens at first, a hyphen appears blinking on the screen, the same thing happened to me when I tried to install ubuntu and delete windows, but in windows its easy create partitions and install isos.

So now I would like to know how to install windows via usb and uninstall ubuntu.

---

### Post by doxne on 2021-08-29
> **doxne said:**
> Well, I would like to do it through a usb, I have a usb, that usb has the iso already configured of windows. But there is a problem, nothing happens at first, a hyphen appears blinking on the screen, the same thing happened to me when I tried to install ubuntu and delete windows, but in windows its easy create partitions and install isos.

So now I would like to know how to install windows via usb and uninstall ubuntu.

I tried to do it with the link you left me but it didn't work for me, I get this:
[IMG]https://i.ibb.co/X416rHj/Captura-de-pantalla-de-2021-08-29-18-29-55.png[/IMG]
I'm sure it's because of the iso, but I want to use this iso because it's lite. (It is the official windows, I am not that stupid to download a bad iso)
What do I do then? I want to install the iso through a USB now, but new problems appear and also let's not forget that I have problems starting the USB, my bios does not start it I do not know why (I only have legacy boot).

---

### Post by C.S.Cameron on 2021-08-29
You need a USB device at least 8GB in size. (The one I use for installing Windows is 16 GB). 

Win10_20H2_English_x64.iso is over 6GB.

It looks to me like your USB is too small.


I am not familiar with Windows Lite, It is not an official Microsoft project:

From Microsoft:
"The Windows Lite you read about is a hacked version of Windows 10, it has had its source files altered by persons unknown to remove all the UWP apps and other functionality"

---

### Post by bobunderwood99 on 2021-08-29
You need to create a bootable USB drive that has the Windows 10 ISO with a tool like Etcher [https://www.balena.io/etcher/](https://www.balena.io/etcher/) or UNetbootin [https://unetbootin.github.io/](https://unetbootin.github.io/) (so you may need to copy your Win 10 ISO to
your computer first).

Then be sure your computer BIOS is set to boot from USB first. Boot from the bootable USB drive you created - the Windows installer will start.

---

### Post by doxne on 2021-08-29
> **C.S.Cameron said:**
> You need a USB device at least 8GB in size. (The one I use for installing Windows is 16 GB). 

Win10_20H2_English_x64.iso is over 6GB.

It looks to me like your USB is too small.


I am not familiar with Windows Lite, It is not an official Microsoft project:

From Microsoft:
"The Windows Lite you read about is a hacked version of Windows 10, it has had its source files altered by persons unknown to remove all the UWP apps and other functionality"

I have a 24gb usb, it is not called the lite version, it is a version for companies that has fewer programs, things like the weather, xbox, things like that, if you want I can give you the microsoft link. Now, how can I do to install windows from a usb in ubuntu?

Edit:
In my opinion the best windows and it is the one that I really want to install, it is the version of Windows 10 LTSC (Long Term Servicing Channel)
[https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)

---

### Post by C.S.Cameron on 2021-08-30
August 24th I used the method shown at this link: [https://askubuntu.com/a/1359829/43926](https://askubuntu.com/a/1359829/43926)
I had no problems and the USB booted right up.
I was using Legacy boot also.
I do not know why you are getting "No suitable target device found".
I will PM sudodus, (mkusb's creator) and ask him to have a look.

---

### Post by sudodus on 2021-08-30
Looking at the screenshot in post #9, think than you ran mkusb-dus from the internal drive /dev/sda. It started dus, and dus could not see any other drive.

Either there was no other drive plugged in at that time, or there is a problem with the USB drive or with the USB system in the computer.

(The error at  line 74 is makes no difference here, because control is given to dus, and it is dus that cannot find any other drive.)

Some time ago I wrote some instructions how to analyze a similar problem, and I think they can be applied in this case. Please look at [this link to AskUbuntu](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035). Good luck :-)

---

### Post by doxne on 2021-08-30
Many thanks to both of you, I will try the methods both gave me.

---

### Post by doxne on 2021-08-31
I need help, I can't load the usb because it's gpt, I get a blinking line when I start it from bios or legacy.

---

### Post by sudodus on 2021-08-31
Please describe with as many details as possible what you did and how it failed (which tutorial, commands, error messages etc)

---

