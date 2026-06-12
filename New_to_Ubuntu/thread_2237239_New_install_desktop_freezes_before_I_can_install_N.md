---
title: "New install desktop freezes before I can install NVidia nForce driver . ."
date: 2014-07-31
forum: New to Ubuntu
---

### Post by JeQhdMD on 2014-07-31
Hello,

I'm trying to install the latest Ubuntu 14.04.1 on a friends laptop:

>   HP Pavilion tx1000us
>  2 GiB Ram
>  Dual amd64 x2 TL-58 running at 1600.00 mhz
>  Nvidia (nForce 2/3/5xx) video (am sure it's NVidia, but not sure if nForce)
>  Broadcom B43 wireless
> SATA ST9/60821AS storage
>  HDA Intel Audio


Anyway, the install processes without error except at the end where there is a popup warning about video drivers and the message disappears before I can clearly read it all.  The startup process appears to complete normally, but about 5 seconds after the login, the whole graphical desktop just freezes.   Mouse cannot be controlled, cannot select any apps to run or to access the setup area for getting proprietary drivers downloaded and installed.

Boot parameter "nomodeset" did not appear to change anything (at my last try which was a couple months ago).   There is a slight chance I didn't input it correctly.   Note, Ubuntu is the only OS on this laptop.

Is there a way to install Ubuntu in text mode, and then download/install the NVidia drivers before activating the Unity desktop?

---

### Post by kira-yamato-2008 on 2014-07-31
It could partly be because of your lack of ram, or possibly because of the older video card. Your card should be am Nvidia GeForce Go 6150. To make sure open a terminal window(Ctrl+Alt+T) and type in lspci. 

At any rate the laptop you have is a significantly dated model and with only two gigs of ram you might have issues. I suggest two things:
-Boot from CD/DVD/USB and run a memtest from a distro disc. You might have an issue with memory that's no longer in prime condition.
-Instead of using the standard Ubuntu self run a lighter distro like Xubuntu, or Lubuntu.

One of the reasons for the second suggestion is your PC no longer has an efficient amount of ram for the OS especially with the Unity Desktop. For two reasons, 2 GB isn't much in this day and age, and you should have intigrated graphics which shares the system memory. In which case up to a quarter of your system memory is set for use as video ram for the integrated Graphics.

---

### Post by JeQhdMD on 2014-07-31
Well, good news.  Ubuntu Trusty Tahr is fully installed on this old laptop.  I had to input the "nomodeset" boot parameter again into Grub.   My initial error was not putting nomodeset at the _very end_ of the line.  Once I did that, it was one step at a time to:

>  install synaptic
>  select fastest server for downloads
>  install ubuntu restricted-extras via synaptic
>  install nvidia driver for graphics chip  via system settings>software updates>restricted drivers
>  install the broadcome driver via same tab/screen as above

Until I installed the restricted extras, the restricted drivers (nvidia and broadcom) didn't show up

Next step (tomorrow) is to create a new partition and setup a dual boot with Xubuntu 14 as Unity drags a bit on this machine (although it is fully useable)

Thanks for the info . . . I do appreciate it.

---

