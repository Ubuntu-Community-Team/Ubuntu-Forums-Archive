---
title: "HOWTO: PlayStation 3 - Installing Ubuntu on the PS3"
date: 2006-12-10
forum: Outdated Tutorials &amp; Tips
---

### Post by candell on 2006-12-10
[FONT="Tahoma"]
[SIZE="3"]The original and current version of this howto will be here:

  * HOWTO:  [http://www.louiscandell.com/ps3/](http://www.louiscandell.com/ps3/)
  * Images: [http://www.louiscandell.com/ps3/images/](http://www.louiscandell.com/ps3/images/)[/SIZE]

[SIZE="6"]Installing Debian Linux / Ubuntu Linux on the PlayStation 3 - (PS3)[/SIZE]


[SIZE="4"]Introduction[/SIZE]


Ah, the PlayStation 3... people getting shot... people standing in line for days just to get their hands on one.  I noticed a lot of you are trying to install Ubuntu on this badboy, so I am going to show you how to cross-install Ubuntu Linux / Debian Linux on your PlayStation 3 from an existing Linux system.  Please don't moan and complain about having to install Fedora Core 5 onto your PS3 before installing Ubuntu.  I had already installed Fedora Core 5 onto my PlayStation 3 before getting the urge to install Ubuntu, and I'm sure a majority of you have already installed Fedora on your PS3 so it's not a big deal.  You can probably skip section 01 if you are an advanced user thats comfortable with the kboot prompt, as it's a minimal Linux environment with enough tools for you to skip to step 02, but I'm showing you how I got Ubuntu on the PS3 so here we go.


Here are some pictures of my PS3 running Xubuntu:  [SIZE="3"][http://louiscandell.com/ps3/images/](http://louiscandell.com/ps3/images/)[/SIZE]
[SIZE="4"]


01 - Installing kboot on the PlayStation 3[/SIZE]


These are the items I used:

    * USB Storage Drive (Thumb Drive, Compact Flash, Pro Duo, etc.)
    * USB External Drive
    * DVD Burner
    * debootstrap_0.3.3.0ubuntu7_all.deb - [http://archive.ubuntulinux.org/ubuntu/pool/main/d/debootstrap/](http://archive.ubuntulinux.org/ubuntu/pool/main/d/debootstrap/)
    * Fedore Core 5 DVD - [http://fedora.redhat.com/Download/mirrors.html](http://fedora.redhat.com/Download/mirrors.html)
    * [http://www.louiscandell.com/ps3/files/CELL-Linux-CL_20061110-ADDON.iso](http://www.louiscandell.com/ps3/files/CELL-Linux-CL_20061110-ADDON.iso)
    * [http://www.louiscandell.com/ps3/files/CELL-Linux-CL_20061110-SRCCD.iso](http://www.louiscandell.com/ps3/files/CELL-Linux-CL_20061110-SRCCD.iso)
    * Few Blank CDR's and DVD's
    * Beer

I went ahead and followed sections 01 - 03 from these instructions:

    * [http://www.louiscandell.com/ps3/doc/HowToEnableYourDistro.html](http://www.louiscandell.com/ps3/doc/HowToEnableYourDistro.html)


I'm going to give it to you real quick breakdown here:

    * Plug your USB storage drive into your main boxen and create the directory structure USB:\PS3\OTHEROS
    * Download otheros.bld and otheros.self onto USB:\PS3\OTHEROS
    * Remove the USB storage drive and plug it into your PS3 and boot that sucker up!
    * On the XMB go into Settings Menu > System Settings > Format Drive
    * I have a 20GB PS3 so I chose the option of making two 10GB partitions.  Please edit this section as needed if you have the 60GB PS3.
    * Once you are done formatting the PS3's internal drive, go into Settings Menu > System Settings > Install Other OS
    * Click "OK" and it will install the kboot image onto your PS3.
    * Once you are done, go back into Settings Menu > System Settings > Default System > Choose "Other OS"
    * Restart your PS3 and you should be on the kboot prompt

Now once you are on the kboot prompt you are within a minimal Linux environment.


[SIZE="4"]
02 - Installing a Base Linux Distribution to ease our cross-install of Ubuntu on the PS3[/SIZE]


Note:  You can probably skip this step if you are an advanced user as you can do a lot with the kboot/busybox environment.  I'm providing this section as I had already installed Fedora Core 5 on my PlayStation 3 before getting the urge to install Ubuntu.  This will be real quick I promise! :)

Here is more information on kboot if you are interested:

    * [http://kboot.sourceforge.net/](http://kboot.sourceforge.net/)


Once you have both the Fedora Core 5 DVD and the ADDON CD burned follow these steps:

    * Insert your freshly burned Fedora Core 5 DVD into the PlayStation 3.
    * Once on the kboot prompt type:  install-fc sda
    * It will ask you to insert the Fedora Core DVD. Type 'y' then press Enter.
    * Remember, choose option '1' - Fedora Core Minimum Install
    * Type 'y' when it says Caution!! All data in /dev/sda will be removed.  Remember, you can always resize /dev/sda with parted once you are done.  
    * Go grab another beer as you have a few minutes before the install is done.
    * Once done, the Fedora Core CD will pop out.
    * Insert the ADDON cd you burned earlier and type 'y' when it requests the ADDON CD.
    * Once the install is done you can type in your root password and then type reboot.
    * Reboot into your Fedora Core system.
    * Log in as root with the password you created.
    * Since this is a minimal install - go ahead and insert your Fedora Core 5 DVD into your PlayStation 3 and mount /mnt/cdrom 
    * Then go ahead and issue the command yum install dhclient
    * Type: 'dhclient' as root and it should give you an IP address if you are a DHCP person, otherwise, google on how to configure ifconfig for a static IP address.
    * Type: 'yum install cfdisk' as root to install cfdisk - only if you feel more comfortable with cfdisk and find fdisk too cryptic.

Once you are at this step you are ready to install Ubuntu.  Like I said, you can probably skip section 02 if you are an advanced user, but I'm sure a majority of you have Linux already installed on /dev/sda so its not a problem.


[SIZE="4"]03 - Cross-Installing Ubuntu / Debian on the PlayStation 3[/SIZE]


I followed the instructions on Installing Ubuntu from a Unix/Linux System but I will show you what steps I followed.  This assumes that you have either repartitioned /dev/sda2 with GNU Parted or have an external USB storage device with at least 500MB for a minimal debian install or  2GB of available space for an Ubuntu desktop as it depends on how you want to use your PlayStation 3.  At this point you should be within your Fedora install on /dev/sda with a working Internet connection, as we are going to install a minimal debian install and then upgrade it to Ubuntu/Xubuntu/Kubuntu... whatever you want.  These are the steps I took.  I'm going to assume your USB storage device is /dev/sdc, so go ahead and change it to whatever comes up on dmesg.  Here we go:

    * As root within Fedora Core - type dmesg and find what your USB Storage device.  Let's assume it is /dev/sdc
    * Type: 'fdisk /dev/sdc' or 'cfdisk /dev/sdc' as root depending on what partitioning tool you feel comfortable with.  Partitioning a drive with fdisk or cfdisk is trivial and well documented on google.com - I used fdisk to partition my 80GB drive as follows:  1.) swap:/dev/sdc1 @ 512MB -- 2.) /boot:/dev/sdc2 @ 100MB (for extra kernels and initrd's and wot not) -- 3.) /home:/dev/sdc3 @ 30GB --- 4.) /ubuntu:/dev/sdc5 @ 10GB --- 5.) Left the rest as free space for other Linux Distributions and what not.


Once done partitioning your USB storage device - you will need to create a filesystem on your partitions

    * $ mkfs.ext2 /dev/sdc2
    * $ mkfs.ext3 /dev/sdc3
    * $ mkfs.ext3 /dev/sdc5
    * $ mkswap /dev/sdc1
    * $ sync; sync; sync
    * $ swapon /dev/sdc1 

You now have enough to start your Ubuntu installation.

    * $ mkdir /mnt/ubuntu
    * $ mount /dev/sdc5 /mnt/ubuntu
    * $ mkdir /mnt/ubuntu/boot
    * $ mount /dev/sdc2 /mnt/ubuntu/boot

Once you are done mounting your partitions you will go ahead and download debootstrap binary from a remote or local Ubuntu mirror, and follow these following steps:

    * $ cd /tmp
    * $ wget [http://louiscandell.com/ps3/debootstrap/debootstrap_0.3.3.0ubuntu7_all.deb](http://louiscandell.com/ps3/debootstrap/debootstrap_0.3.3.0ubuntu7_all.deb)
    * $ ar -xf debootstrap_0.3.30ubuntu7_all.deb
    * $ cd /
    * $ zcat < /tmp/data.tar.gz | tar xv

Or you can just be lazy and do the following:

    * $ cd /tmp
    * $ wget [http://louiscandell.com/ps3/debootstrap/data.tar.gz](http://louiscandell.com/ps3/debootstrap/data.tar.gz)
    * $ cd /
    * $ zcat < /tmp/data.tar.gz


And you are done... either way will work.  I'm just lazy I guess.  I downloaded a xubuntu 6.10 Edgy iso just to have in case I needed it, so you can do so if you like but its not required since it will technically be a net install.

Once you are done with the above then just issue the command:

    * $ /usr/sbin/debootstrap --arch powerpc edgy /mnt/ubuntu [http://archive.ubuntulinux.org/ubuntu](http://archive.ubuntulinux.org/ubuntu)


And sit back and watch the screen fly as a base Ubuntu system creates itself from your hard work.  I would suggest another "beverage" at this point in time and oh maybe some junk food.



[SIZE="4"]04 - Configuring Minimal Install of Ubuntu Base System[/SIZE]


I want to get us into our Ubuntu Desktop as quickly as possible and with minimal work, so lets copy the kernel from Fedora Core 5 and use it to quickly get into a GUI we all know and love:

    * $ cp /boot/* /mnt/ubuntu/boot
    * $ cd /mnt/ubuntu/boot
    * $ cp vmlinux-2.6.16 ../vmlinux
    * $ cp initrd.img ../
    * $ cd /mnt/ubuntu/lib
    * $ cp /lib/2.6.16 .


The above will have a 2.6.16 kernel, initrd and modules at your disposal in case you mess something up in the near future and will get us into our Ubuntu Desktop as quickly as possible.

Once done with debootstrap you will go ahead and configure your Base System.

I'm partial to GNU Emacs, but you might be a vi, vim or nano type of character so just to make this as easy as possible do the following:

    * $ chroot /mnt/ubuntu /bin/bash
    * $ source /etc/profile
    * $ apt-get install nano


The above command has you in your new Ubuntu system in its infant state.

At this point you will configure your /etc/fstab file.

Here is a basic one for me:

# /etc/fstab: static file system information.
#
# file system    mount point   type    options                  dump pass
/dev/sdc5         /             ext2    defaults                0    0
/dev/sdc3	  /home		ext3	defaults	        0    0
/dev/sdc2         /boot         ext2    defaults	        0    2
/dev/sdc1        none          swap    sw                       0    0
proc             /proc         proc    defaults                 0    0
sys              /sys          sysfs   defaults                 0    0
/dev/fd0         /mnt/floppy   auto    noauto,rw,sync,user,exec 0    0
/dev/cdrom       /mnt/cdrom    iso9660 noauto,ro,user,exec      0    0

###### /etc/fstab done

Once done configuring your /etc/fstab file you can manually mount each filesystem once you are chrooted into your Ubuntu System, or you can automatically mount them.  

    * $ mount -a


The above game me some errors, so I made sure that both /proc and /sys were mounted.  Check to see if they are mounted by seeing if there is anything in them:

    * $ ls /proc /sys


If /proc and /sys are not mounted then you will manually mount them like this:

    * $ cd /
    * $ mount -t proc proc proc
    * $ mount -t sysfs sysfs sys

Once done, you will configure your keyboard, networking, timezone, locales, install a kernel and all that good stuff so you can boot up into your Ubuntu desktop and kick some butt!  I'm sure you're probably tired of being in the CLI and we do need a kernel, but remember we copied over the 2.6.16 kernel from our Fedora Core system, so lets get into our Ubuntu System and then start customizing and tailoring our system to our specific needs:

    * $ apt-get install dhclient
    * $ apt-get install openssh-server openssh-client
    * $ apt-get install whatever else you need to make your experience as nice as possible.


You can download a kernel if you like, but I'm sure you would rather be inside your Ubuntu Desktop as quickly as possible, so just use what I've given you and go from there.


[SIZE="4"]
05 - Installing The Xubuntu / Ubuntu / Kubuntu desktop[/SIZE]


Congrats as you've made it this far!  At this stage you have a choice of installing whatever desktop you like.  You can either install the Ubuntu, Xubuntu or the Kubuntu desktop at this stage of the install.  You will want to issue one of the following commands depending on what desktop you want.  I went ahead and installed Xubuntu, as I'm more of a CLI type of person.

    * $ aptitude -y install '~txubuntu-desktop'
    * $ aptitude -y install '~tubuntu-desktop'
    * $ aptitude -y install '~tkubuntu-desktop'

Once the above is done you are finished.  You should be inside your Ubuntu Desktop, but what is this... it looks like a big block party and everything is so large and in charge!  Not to fear... you just need to do a few more things to make everything fit inside your Ubuntu Desktop.

[SIZE="4"]06 - Configuring /etc/X11/xorg.conf and ps3videobuffer to make everything look great.
[/SIZE]


[/FONT]

---

### Post by Ciego on 2006-12-10
Is it possible to install Ubuntu from the kboot promp without installing Fedora?

---

### Post by ebryn on 2006-12-11
To run Ubuntu off the PS3 hard drive just debootstrap back onto the hard drive after following the howto.

Rather than reformat I left /etc/kboot.conf, /boot, and /lib/modules on the drive and deleted everything else. I'm still using the FC5 kernel.

I just finished bootstrapping feisty and now I'm installing the desktop packages.

---

### Post by Ciego on 2006-12-11
> **candell said:**
> [FONT="Tahoma"]

[SIZE="4"]04 - Configuring Minimal Install of Ubuntu Base System[/SIZE]

I want to get us into our Ubuntu Desktop as quickly as possible and with minimal work, so lets copy the kernel from Fedora Core 5 and use it to quickly get into a GUI we all know and love:

    * $ cp /boot/* /mnt/ubuntu/boot
    * $ cd /mnt/ubuntu/boot
    * $ cp vmlinux-2.6.16 ../vmlinux
    * $ cp initrd.img ../
    * $ cd /mnt/ubuntu/lib
    * $ cp /lib/2.6.16 .


The above will have a 2.6.16 kernel, initrd and modules at your disposal in case you mess something up in the near future and will get us into our Ubuntu Desktop as quickly as possible.

[/FONT]

Can you please tell me what files were copied here other than the kernel and initrd.img.  Are they the files from the /target folder in the addon iso?  I am attempting to install Ubuntu without installing Fedora first.  I know that I will have to convert these files to .deb from .rpm but I am not sure exactly where they need to go.  I see the /etc/kboot.conf and the /boot files on the addon disc but there is not a /lib/modules there.  I am assuming that they are the files in /target but I am not sure.

---

### Post by Ciego on 2006-12-15
For those interested, I created a thread for sharing PS3 aliases for the Playstation network.

[http://ubuntuforums.org/showthread.php?t=319528](http://ubuntuforums.org/showthread.php?t=319528)

---

### Post by cyber pete on 2006-12-25
I'm going to attempt this when I pick up a USB keyboard tomorrow. Queston for you..where you able to get the XGL DESKTOP to work on unbuntu on the PS3? 

This is my eventual goal is get VLC MEDIA PLAYER and the XGL DESKTOP running on ubuntu on my PS3.

---

### Post by [Nirvana] on 2006-12-25
If I install Ubuntu onto the PS3, I can still use the console right? What is the command?

---

### Post by gorilla_king on 2006-12-26
haha, i wish i had a ps3 now. they're so fast...

---

### Post by CheddarBot on 2006-12-28
Is there a way to instal ubuntu on a jump drive, than boot from that on the console? I kind of want to keep as much space as possible on the ps3, for when it is possible to back up games on the hdd.

---

### Post by Morbett on 2006-12-30
Does anyone have any feedback on how Ubuntu works on a PS3?  Are there any major limitations?  (i.e. the low memory thing)

This looks too good to be true.

Thanks for your input!

---

### Post by allaryin on 2007-01-03
> **CheddarBot said:**
> Is there a way to install ubuntu on a jump drive, than boot from that on the console? I kind of want to keep as much space as possible on the ps3, for when it is possible to back up games on the hdd.

The partition utility in the ps3 console only seems to have options for the following:
 - all ps3
 - 10gb ps3, remainder unix
 - 10gb unix, remainder ps3

So... 50gb should probably suffice you even if you can't use usb ;)

I'll play with USB hd on it later tonight...

---

### Post by TmP on 2007-01-04
Can you please do some performance tests? I was wondering how the CELL would be useful for video encoding? I bet it is not yet supported well but it would be amaizing to harness all that power to something usefull. 

I heard that Sony wasn't willing to give Yellowdog access to the accelerated graphics capability of the PS3. So I guess XGL is out of the question at the moment. Maby in the future?

What i would love to seen in the future is a ISO of Ubuntu to install on Linux, that would start up with a beautiful Beryl animation...

---

### Post by TmP on 2007-01-04
Ehem....

Your second screenshot?
Last line?

"* Restarting OpenBSD Secure Shell server..." ?

I didn't know XUbuntu wasn't a Debian...

And my... your gear is impressive!

---

### Post by the Goat on 2007-01-06
I'm trying to follow these directions and a have a questions.

How do I run GNU Parted on the PS3?  I need to resize the sda1 partition to make room for 
ubuntu.

Also, I couldn't install cfdisk.  I greped the packages yum listed and couldn't cfdisk anywhere.  I'm not too concerned.  i've used fdisk before.

---

### Post by inee on 2007-01-08
hi,

its been maybe ten years since i've gone on a red hat terminal, so treat me as a noob.

im trying to install ubuntu onto the ps3. i got fedora and yellow dog running; but my ultimate goal is to get ubuntu and darwin on the machine. im running into several roadblocks and hope the more experienced members here can lead the way.

a guide for ubuntu on ps3 was written here:

[http://louiscandell.com/ps3/](http://louiscandell.com/ps3/)

but it goes through several steps and requirements that i think we can skip. it requires that you install ubuntu on a usb hdd where you can partition it, PLUS, it also requires fedora as a base install, then cross-installing onto debian and then upgrading to ubuntu.

i want a simpler way where i can install ubuntu from kboot prompt with a dvd-rom installer ready.

keep in mind there are a few things that make the ps3 installation different:

1. the ps3 boots into kboot only. cannot boot from hdd and cannot boot from cdrom or usbdrive.

2. only 1 partition available: /dev/sda (i imagine parted can fix this)

3. ppc architecture



okay, some issues i want cleared. 

1. can i modify kboot to load the cdrom such that i can install from the cdrom? if this is possible then i can just plug in the installer cd (whether ubuntu, osx, or darwin) and let it run its course.

2. can i do without partitioning the hdd? id imagine just making a /ubuntu folder and installing everything there. the guide above requires partitioning of the hdd which the ps3 does not allow by default (although yellow dog's druid was able to do it). 

3. can kboot boot ubuntu instead of yaboot? in that case, can kboot boot darwin/osx too (darwin/osx requires bootx)?

4. i get this error:

w: failure trying to run: chroot /mnt/ubuntu mount -t proc proc /proc

after typing this:

/usr/sbin/debootstrap --arch powerpc edgy /mnt/ubuntu [http://archive.ubuntulinux.org/ubuntu](http://archive.ubuntulinux.org/ubuntu)

specifically after "i: validating libatu1" step. what does that mean and how do i fix it? 


this error happens after i chose "minimal fedora install". i dont get it when i choose the full install (2.5hrs wait); but the guide above states to use the minimal install.



all the help is greatly appreciated. hope i can get ubuntu running NATIVELY on the ps3 without an external usb hdd.

---

### Post by Ciego on 2007-01-08
> **inee said:**
> 

1. can i modify kboot to load the cdrom such that i can install from the cdrom? if this is possible then i can just plug in the installer cd (whether ubuntu, osx, or darwin) and let it run its course.



You can modify the kboot.conf file to your liking.  This file tells kboot what to execute after it boots up.  I believe it is located at /etc/kboot.conf 

> **inee said:**
> 

2. can i do without partitioning the hdd? id imagine just making a /ubuntu folder and installing everything there. the guide above requires partitioning of the hdd which the ps3 does not allow by default (although yellow dog's druid was able to do it). 



You can partition the hard drive for linux from the PS3 XMB (either 10GB for linux or 10GB for PS3 ... you have to choose) but once you are at the kboot prompt, you can format the linux partition however you would like using fdisk.  If you have the 60GB PS3 and you choose 10 GB for the PS3 partition, that will leave you with 50GB for the linux partition that you can manage with fdisk from the kboot prompt.

> **inee said:**
> 

3. can kboot boot ubuntu instead of yaboot? in that case, can kboot boot darwin/osx too (darwin/osx requires bootx)?



Again, as far as I know, you can modify kboot to our liking to boot up whatever you want.

---

### Post by seuaniu on 2007-01-08
> **TmP said:**
> Ehem....

Your second screenshot?
Last line?

"* Restarting OpenBSD Secure Shell server..." ?

I didn't know XUbuntu wasn't a Debian...

And my... your gear is impressive!

The fine folks over at openbsd started the openssh project many many moons ago.  Every linux distro that uses openssh is using a port from bsd.  The "starting openbsd ssh server" line is just part of the script that lets you know whats going on.  If you wanted, you could do a ```
 sudo vi /etc/init.d/ssh 
```

and edit that to say whatever you want, ie "Starting Microsoft ssh server", if you get a kick out of reading boot messages ;)

---

### Post by theBishop on 2007-01-10
Just a heads up, I didn't feel like downloading/installing Fedora to do all this.

So I downloaded the Gentoo LiveCD (brilliant piece of work BTW) from here:
[http://gentoo.mirrors.pair.com/experimental/ppc64/livecd/livecd-ppc64-beta.iso](http://gentoo.mirrors.pair.com/experimental/ppc64/livecd/livecd-ppc64-beta.iso)

(any mirror will have it in experiemental/ppc64/livecd) 

Press tab at the kboot prompt to choose the resolution compatible with your TV and press enter.

The live CD will load up to a Gnome desktop.  I opened up a terminal and typed "sudo -s" to get root access.  Then, i wandered over to /etc/init.d and typed "./xdm stop" to kill X dead.

then I wget'd the bootstrap file from the OPs server to the /tmp folder.

NOW HERE's THE TRICKY PART (its not too bad):

because the liveCD is a read-only file system, you can't unpack data.tar.gz to /.  You have to unpack it to /tmp.  I did this with "tar zxvf data.tar.gz".  This created the usr folder whose contents would usually be in /usr/.  

so then i tried to ./ debootstrap from the /tmp/usr/sbin folder.  But it didn't like that because it was looking for a "functions" file in "/usr/lib/debootstrap", big mistake pal!

No big deal, just fire up VIM (or whatever), and change line11 from:
DEBOOTSTRAP_DIR=/usr/lib/debootstrap

to

DEBOOTSTRAP_DIR=/tmp/usr/lib/debootstrap

then run the debootstrap command from /tmp/usr/sbin instead of /usr/sbin, it'll run for a while, and follow the rest of candell's guide.

---

### Post by Ciego on 2007-01-10
> **theBishop said:**
> 

then run the debootstrap command from /tmp/usr/sbin instead of /usr/sbin, it'll run for a while, and follow the rest of candell's guide.

What is the command that you run at this point.  I am getting an error "bash: debootstrap: command not found"

**RESOLVED:**

I guess the command is
```
$ /tmp/usr/sbin/debootstrap --arch powerpc edgy /mnt/ubuntu http://archive.ubuntulinux.org/ubuntu
```

I just typed that and off it went

BTW:  Great find theBishop.  I have been looking for a way to install Ubuntu without installing anything else first ... and yes, that live CD is a masterpiece.

---

### Post by Andaconda on 2007-01-14
When I am at the kboot promt and I type in "install-fc sda" I get the error "eval: 1: install-fc: not found" I have done everything else on the instructions. I am a complete Linux noob and I know nothing about linux. If someone could help me that would be great.

---

### Post by Ciego on 2007-01-14
> **Andaconda said:**
> When I am at the kboot promt and I type in "install-fc sda" I get the error "eval: 1: install-fc: not found" I have done everything else on the instructions. I am a complete Linux noob and I know nothing about linux. If someone could help me that would be great.

Do you have the Fedora core DVD in the drive?

---

### Post by Andaconda on 2007-01-14
> **Ciego said:**
> Do you have the Fedora core DVD in the drive?

Yes I had the DVD in the drive. I think I followed the directions correctly. I did it over again acouple of times and it still didn't work.
I guess i'll give you a better explanation of the error.
After I formatted the HD and Installed kboot I rebooted the ps3 and inserted the fedora 5 dvd. 
the kboot prompt then says 
"UDF-fs: no VRS found
UDF-fs: no VRS found
kboot:"

at the prompt if I set it sit it then displays 
"UDF-fs: no VRS found
/init: eval: 1: /dev/sr0:/ppc/ppc64/vmlinux-ps3: not found" and it keeps on displaying this over and over again.

when I am at the prompt if I type in "install-fc sda" it then displays 
"/init: eval: 1: install-fc: not found"

I have made sure its the right DVD, I burned it at maximum speed, I'll try burning it at a slow speed, I dont know if that will make a difference either.
Do I need an external HDD plugged in, I dont have one at the moment, my flash drive is plugged in, I have tried it with the flash drive not in. It didn't work either way. I dont know if that matters though. Any help you can give me will be appreciated

---

### Post by Ciego on 2007-01-15
You do not need an external hard drive for this to work.  It sounds like it is a problem with the DVD that you burned.  In general, I think it is considered standard practice to burn at very slow speeds when you are burning an OS install disk.  I would recommend a 4x or 8x burn, but my burner will only do 16x at its slowest and I think at that speed I have had one bad burn out of 10 or so.

The "UDF-fs: no VRS found" part is normal I guess ... mine says that too.

---

### Post by Andaconda on 2007-01-17
I reformatted the ps3 HD so that it gave all of the 60gb to the ps3 system. Then I reformatted it so that it gave 10gb to the Other OS. It works fine now. I think kboot was configured for Yellow Dog Linux because I had that on before. Thanks for the tutorial. Its great.

---

### Post by juanzone on 2007-01-20
> **Ciego said:**
> What is the command that you run at this point.  I am getting an error "bash: debootstrap: command not found"

**RESOLVED:**

I guess the command is
```
$ /tmp/usr/sbin/debootstrap --arch powerpc edgy /mnt/ubuntu http://archive.ubuntulinux.org/ubuntu
```

I just typed that and off it went

BTW:  Great find theBishop.  I have been looking for a way to install Ubuntu without installing anything else first ... and yes, that live CD is a masterpiece.


I have been able to debootstrap using the methods described above, but now I'm stuck. I'm trying to install Ubuntu onto the native PS3 hard disk with the Gentoo LiveCD, but I don't exactly know what to do after debootstrapping. I'm trying to follow Candell's guide from instruction number 4, but I can't cp the kernel nor can I chroot. I apologize if I'm missing something totally obvious, but I'm quite new to linux (started just a few days ago with YDL). Hopefully, someone can guide me to the right direction. Thanks!):P

---

### Post by Ciego on 2007-01-20
> **juanzone said:**
> I have been able to debootstrap using the methods described above, but now I'm stuck. I'm trying to install Ubuntu onto the native PS3 hard disk with the Gentoo LiveCD, but I don't exactly know what to do after debootstrapping. I'm trying to follow Candell's guide from instruction number 4, but I can't cp the kernel nor can I chroot. I apologize if I'm missing something totally obvious, but I'm quite new to linux (started just a few days ago with YDL). Hopefully, someone can guide me to the right direction. Thanks!):P

I have been working on the same thing for a few days now.  I think that the reason you cannot copy the kernel is because it has a different name on the Gentoo CD.  Try this.

```
$ cp /boot/kernel-genkernel-ppc-2.6.16-ps3 /mnt/ubuntu/boot/vmliux
```

This will copy the kernel from the CD to a file named vmlinux in the /mnt/ubuntu/boot directory.

I think that I am going to try it using the kernel from the ADDON CD because I am having some problems with this one. 

I am writing a HOW-TO for this right now but I am still working out a few kinks.  I could email it to you if you would like to see what I have so far .... just PM me.

---

### Post by Ciego on 2007-01-21
I have posted another HOWTO for installing Ubuntu on the PS3 with a live CD.  

[http://ubuntuforums.org/showthread.php?p=2042834#post2042834](http://ubuntuforums.org/showthread.php?p=2042834#post2042834)

---

### Post by steve101101 on 2007-02-23
I have been running ubuntu on the ps3 for a little while and it runs at the same pace as YDL or slightly better. kubuntu will be the next best on system resources with xubuntu being the most efficient.

---

### Post by Cbotron on 2007-03-05
Do you have videos of ubuntu on the ps3?

---

### Post by ceros on 2007-03-30
Compatibility for Ubuntu fiesty on Playstation 3 has been implemented as described at [https://blueprints.launchpad.net/ubuntu/+spec/ps3-compatibility](https://blueprints.launchpad.net/ubuntu/+spec/ps3-compatibility).

CD images are provided which allow you to run ubuntu without changing anything on your PS3 and at your option, to install it onto the system. It should be noted though that these images are not intended for normal use yet, so beware.

As for me, I'm downloading an image now and trying it tonight. I'll post what happens later.

---

### Post by unox on 2007-04-01
Hey, I'm following the guide now, and just found something you should add.
You do not say what core of fedora to download = PPC (although it's easy to open the step 1-3 link and see ;) )

---

### Post by ceros on 2007-04-01
I tried the desktop CDs for Ubuntu. Since I only have an SDTV, it's kind of hard to see some of the forms when you try to install Ubuntu to the hard drive. Also, there's no sound. Also, there's something wrong with the network connection. I posted a guide along with a section of known bugs at [https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3).

---

### Post by byron_moran on 2007-06-10
hi i have a quick question, it does matter if i  install the 32bit or the 64bit ubuntu version on my PS3?..will i get more from it if i use the 64bit version?.

thanks.

---

### Post by HobbitCy on 2007-06-13
hi guys iv just skipped most of the howtos well i read a bit and i got ubuntu on my ps3
what i did was get the PPC version my understating is this is the only version that will work
im almost sure its a 32bit version 
and its also a custom live cd coz the ordinary version wouldnt install properly
just poped the disk in pressed install and went through the 7 steps restarted and i was in ubuntu

---

### Post by hebetude on 2007-10-13
More straightforward method here:
[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

The LiveCD works, I have to go buy a component cable so I can use the installer though :X

---

### Post by faical117 on 2007-11-13
oh waw how nice & fast ubuntu !! :guitar:

---

### Post by discoade on 2007-12-08
im a little confused! 

can anyone confirm that the iso i need to install gutsey an my ps3 is the playstation 3 desktop cd located [here]("http://cdimage.ubuntu.com/custom/20071115-gutsy-ps3/")

is that the complete package i need to get ubuntu up and running?

---

### Post by hebetude on 2007-12-08
refer to this for list of files: [https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

---

### Post by cchester on 2007-12-11
Hi Guys,

I have run into an issue I type at the kboot boot-game-os and I get an error. Can someone tell me how to get back into just the regular part of my ps3. I can't install unbuntu 7.04 because it keeps freezing at 15% when trying to install. Also ubuntu 7.10 just came up with errors when I tried to boot the cd.

Thanks

---

### Post by discoade on 2007-12-11
press and hold the pwr button (while powered down) for approx 5 seconds untill the ps3 beeps twice then power up. it should boot to your ps3 os.

it sounds like you have a corrupt installation cd.  re burn it at a very low speed. ie 4x

---

### Post by hebetude on 2007-12-11
I'm pretty sure that formats the hdd.  Thats the fubar method for when you try to brick your ps3 with bad install CDs.  Re-burn your installation CD at 1x (or your slowest setting) and try again.  Don't use a 10year old rewritable as installation media either.

Google psubuntu if you run into any other problems.  

You should note that the PS3 is a lousy computer, and IMHO not worth the time putting linux on it.  I put ubuntu on it and about a hour later reformatted and stuck to the gameOS.  Unless you plan on writing all optimized code for the Cell chip, performance is going to be very poor.

Cell programming:
[http://www.ibm.com/developerworks/library/pa-tipspu2/](http://www.ibm.com/developerworks/library/pa-tipspu2/)
[http://www.ibm.com/developerworks/power/library/pa-celltips1/](http://www.ibm.com/developerworks/power/library/pa-celltips1/)

---

### Post by tbuss on 2007-12-31
**Problem**

When I'm testing video modes, ps3videomode -v 3 works great. When I start gdm to see if it works in Gnome, It displays at the same default resolution (very large). Creating a ps3videomode file in /etc/event.d with the videomode I tested did not work either.

Why does the resolution display properly when I'm testing, but fails to display in Gnome? Any help would be great.

**This is what I tried**

> sudo /etc/init.d/gdm stop
(Alt-F1 to switch to the first console in tekst mode)
ps3videomode -h (for the lists available)
ps3videomode -v {x} (change x to the resolution you want to try)

* if you found what you where looking for, try filling up the screen with x's to see if the screen doesn't have any anomalies

Start the gdm to see if it works in Gnome:

/etc/init.d/gdm start

If it does, goto a terminal console and make it final through editing (or creating) a "ps3videomode" file in the /etc/event.d folder:

sudo nano /etc/event.id/ps3videomode

Insert the following commands in this file:

start on run level 2
exec /usr/bin/ps3videomode -v {x} (the videomode you tested)

Exit with Alt-X, save: yes, confirm filename 

---

### Post by gwsmokey on 2008-06-26
Well, I installed the Gusty 7.10 os, and I am having extreme problems getting back into the XMB.

Looks like i created an user during instalation that i would like to use. Well, no matter what I get a very low resolution when i load the gui. It gets worse from here.

No matter what when i am in the gui - i cant change my video mode using ps3videomode -h 37 or 5 - aka 37 is 1080p for me.

I edited the kboot.conf file. I also made a backup. I cant seem to save in it. Like I dont have root privledges. Is anyone familiar with this? I try to login as root using the same exact password for my actual user name. And cant login.

I type root, then the password. Fails.

So then i go with gwsmokey and the password and i am in. But guess what, once i open temrminal and try to change my video mode - i get a scrambled buffer screen that is unusable. I have to hard boot too... Oh what is up with Ubuntu not shutting down properly? I have to hit the switch...

I just installed a 320gb HDD earlier. I cant change video mode in the gui, i cant get back to the game os from the gui :( 

I am so SOL. Please can anyone help me? I had YDL working fine :P once this HDD was upgraded i am a noob all over again.

Thanks!

---

### Post by Tass on 2008-09-24
> **cchester said:**
> Hi Guys,

I have run into an issue I type at the kboot boot-game-os and I get an error. Can someone tell me how to get back into just the regular part of my ps3. I can't install unbuntu 7.04 because it keeps freezing at 15% when trying to install. Also ubuntu 7.10 just came up with errors when I tried to boot the cd.

Thanks

OK - I've had the EXACT same issue (10 months later :p). Not sure if anyone's resolved this?  I'm using 7.10. I can boot into the Live CD with my disc, so I think that's OK?  I'll try burning it again though.

Any updates?

Oh - BTW, I've also lost my mouse?  It used to come up as soon as I started the install - now nothing.  When running 'livel from the kboot, I get the following errors.  Any ideas?
USB 3-2.1 : device descriptor read/64, error -32
USB 3-2.1 : device descriptor read/64, error -32
USB 3-2.1 : device descriptor read/64, error -32
USB 3-2.1 : device descriptor read/64, error -32
USB 3-2.1 : device not accepting address 5, error -32
USB 3-2.1 : device not accepting address 6, error -32


I've swapped the keyboard round on both USB ports, and it works fine - the mouse is a no-go :(

---

### Post by Tass on 2008-09-25
OK - made some progress.  Got the install working by dropping my resolution from 1080p to 720p - worked like a charm.

I'm still not able to use my mouse, so find myself unable to do anything - very frustrating!

As mentioned, everything was working fine, automatically picking up both my wired & bluetooth (docking station/hub connected via USB) whenever I plugged them in.

Now nothing will get them going.  Quite often I find that rebooting, sitting on the kboot screen, by keyboard doesn't work.  It seems to be quite intermittent, although the mouse NEVER works.  Anything I could do?

Once I get to the ubuntu login (auto-starts from kboot after 1 min or something), the keyboard always works.  This gets me into ubunut, but I can't access my menus! (anyone know shortcuts??).  I can get to the Terminal (Ctrl + Alt + F1), but wouldn't know where to begin with that?

I can't help think that this is an issue with the PS3 firmware somewhere - tempted to use the Restore PS3 OS option, although not sure what that will do.  Maybe worth a firmware upgrade?

---

### Post by Tass on 2008-09-27
OK - did an upgrade - still no luck.

Just checked, and realised that my PS3 controller doesn't charge in either of my PS3 USB ports.  I've checked that the controller charges fine on my laptop.

I've checked that my keyboard still works when booted into Ubuntu on either port.  I've checked and seen that my mouse still doesn't work on either USB port in Ubuntu or PS3 browser.

Going to try the Restore PS3 system soon - any other ideas before I do that?

Thanks,

Tass

---

### Post by mendieta on 2008-10-26
Anyone knows if (*)buntu 8.10 will have out of the box support for the PS3? I am looking both for a game console for the kids, and a set-top pc to install Mythbuntu, and it strikes me that the PS3 could do both things at a reasonable price

Thanks!

---

### Post by KrustyRusty on 2009-01-17
I'm trying to setup the display on my ps3 by using this command 'ps3videomode -v (X)' where (x) is the video mode, but when i press enter, the next line says 'error open:-1' any ideas what this means?



(sorry, this is my first time using linux)

---

### Post by baldheadmatt on 2009-01-17
WANT A MUCH EASIER WAY???

Check out this article buy Popular Mechanics

[http://www.popularmechanics.com/technology/how_to/4263321.html](http://www.popularmechanics.com/technology/how_to/4263321.html)

Enjoy

---

