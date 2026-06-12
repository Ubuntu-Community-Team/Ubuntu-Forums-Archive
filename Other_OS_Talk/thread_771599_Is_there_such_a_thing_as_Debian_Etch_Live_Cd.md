---
title: "Is there such a thing as Debian Etch Live Cd?"
date: 2008-04-27
forum: Other OS Talk
---

### Post by hockeyfighter09 on 2008-04-27
I was wondering this and I cant find solid evidence if there is.  If anyone could fill me in and provide a link it would be much appreciated.:)

---

### Post by pieisgood4589 on 2008-04-27
> **hockeyfighter09 said:**
> I was wondering this and I cant find solid evidence if there is.  If anyone could fill me in and provide a link it would be much appreciated.:)

[http://live.debian.net/](http://live.debian.net/)

It's not an official Debian project, so it's not officially supported either but... Give it a go :popcorn:

---

### Post by hockeyfighter09 on 2008-04-27
Would this be exactly like having an official Debian Etch System installed?  Thanks for the link I think I am going to have a go at it, but I am just wondering since you said its not officially supported.:)

---

### Post by pieisgood4589 on 2008-04-27
> **hockeyfighter09 said:**
> Would this be exactly like having an official Debian Etch System installed?  Thanks for the link I think I am going to have a go at it, but I am just wondering since you said its not officially supported.:)

I'm really not sure, sorry for the not-so-great help, but... It seems to be a stable liveCD, although it doesn't seem to be able to install- the Debian guys say to just use KNOPPIX... :( I really can't find out much... Sorry again

---

### Post by init1 on 2008-04-27
> **hockeyfighter09 said:**
> Would this be exactly like having an official Debian Etch System installed?  Thanks for the link I think I am going to have a go at it, but I am just wondering since you said its not officially supported.:)
Yes, I believe it would. All the packages come from the official repos. You may also want to try Live Helper.
```

apt-get install live-helper

``` 
I have not been able to get it working in anything but Etch but, it is extremely useful. It allows you to select the packages you want in the live CD. It takes some configuration though. 

Follow these directions (some of the info on the page prior to this quote is old and no longer works):
> 
Configuring the settings for your Debian based Live CD:

1. Login as root and open a terminal (must be done as root user)
2. From the terminal, type lh_config

Now we can edit the configuration files that have been created in (root's Home) debian-live/config/ directory

    * Open debian-live/config/chroot, Set the interactive parameter LIVE_INTERACTIVE="enabled" (this allows you to chroot to the filesystem and make changes before it is compressed)
    * You should also set the live package to install. For example: LIVE_PACKAGES_LISTS="gnome" (will install the gnome desktop)
    * Save changes and close the chroot file

Note: To create a USB Image instead of an ISO, open debian-live/config/binary and change the image type parameter from iso to usb-hdd LIVE_BINARY_IMAGES="usb-hdd"

Building the Debian based Live Linux ISO or IMG:

Now that we have made a couple of basic configuration changes we can proceed with the build process.

1. Back at the terminal type cd debian-live (moves us to debian-live, where our live distro is going to be built)
2. Type lh_build (starts the build process based on our live configuration settings)

During the build process, live-helper will create a directory named chroot containing the Linux filesystem that will later be compressed. Once live-helper has finished installing the core components, it will start an interactive shell (change root directory to chroot) pausing the build and allow you to install additional packages and make changes or adjustments before it compresses the filesystem and builds the final Live Linux ISO.

3. At the terminal, when the script responds with the following:
Pausing build: starting interactive shell…

    * make your changes, if any and then type exit to allow live-helper to continue.

Burn the ISO and test your new creation:

Once live-helper has finished, you'll find your completed ISO in the debian-live directory.

1. Burn the ISO to a CD or DVD

2. Test your new creation by rebooting from the CD/DVD.

Or to Copy the IMG to the USB device:

1. From the terminal type fdisk -l and locate your USB device. Example: dev/sdX (where X represents your USB device)

2. Type dd if=binary.img of=/dev/sdX

3. Reboot your PC, booting from the USB device

Note: With your CD/DVD or USB build, you can save your changes back to a USB device via the persistent feature. Simply create a partition on the device labeled casper-rw and type live persistent at boot to enable saving and restoring of settings/changes.

Example: mkfs.ext2 -L casper-rw /dev/sdx2

As is also shown in the Ubuntu tutorial!


[http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/](http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/)

---

### Post by darrelljon on 2008-04-28
I read that the latest Debian Live CD is also installable (possibly through a graphical installer).

---

