---
title: "Can't install Ubuntu Server packages from USB drive"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by defu on 2012-08-08
I've set up a Ubuntu Server 12.04, but it isn't connected to the internet. I'm trying to connect it through my wireless network. However I'm unable to do this because I cannot install the wireless tools through a USB. I've tried mounting it and creating a directory. Proceeded to run command

sudo dpkg -i wireless-tools_30-pre9-3ubuntu4_i386.deb

...And I recieve an error. "cannot access archive: No such file or directory".

Doesn't make much sense seeing as it certainly does exist on the USB flash drive. Perhaps I'm not mounting it correctly... But I can't really tell because when I run a mount command it doesn't provide feedback.

Any feedback or help would be really appreciated. As someone whose new to this, I could use as much help as possible.

---

### Post by audiomick on 2012-08-08
I would firstly try and copy the file onto the drive of the computer itself, and then ascertain that it is really there. Remove the USB drive and make sure you can find the file you are trying to install.

Then make sure you are really in the directory before you issue the dpkg command, or, similarly, that path given in the command is absolutely correct.

---

### Post by defu on 2012-08-08
Excuse my lack of knowledge, but how would I do that? I can't think of how I would copy the file to the hard drive without using the Ubuntu server OS, or any OS.

---

### Post by audiomick on 2012-08-09
> **defu said:**
>  I can't think of how I would copy the file to the hard drive without using the Ubuntu server OS, or any OS.

> **defu said:**
> I cannot install the wireless tools through a USB. I've tried mounting it and creating a directory.

You're not entirely clear here, but I assume you mean you have the driver you want to install on either a USB stick or a USB external drive. You have tried to mount the USB storage device, and were unable to install the driver from it because dpkg said it couldn't find the device. 

So...
Firstly, of course you are doing the copy operation that I suggested from the server OS.

Have you got a GUI on there or is it all command line? If you have a GUI, you could use the file manager to see if you can navigate to the USB storage device. If you are working from the command line, the the cd command. This will show you that the device is mounted or not. I am sure there is also some command to find out if a device is mounted, but I don't know it.

Having established whether or not the thing is mounted, you then either know that you have to address that problem directly (why didn't it mount) or you can use the cp command (or the GUI if you have one) to copy the file across to the computer's own drive.

No doubt dpkg should work when addressed to a properly mounted external drive, but on the one hand I have had the occasional problem with things not quite working right when an external device is involved, and on the other hand I like to break things down to simple steps in order to be able to see where the problem is happening.

So, having copied the file across to the computer's own drive and verified it is there with the ls command, you know that there is no reason for dpkg not to work, assuing the path in that command is given correctly and there is nothing else wrong with the system that is getting in the way.

Another option you could consider would be to boot the server computer from a live CD and use that environment to copy the file across to the hard drive of the computer. I would then boot back into the server's own system and try and install from there. I believe it is also possible to use chroot from the live CD environment to get into the installed system and do things in there, e.g. install the driver, but I have no idea how to do that. 

I hope that makes what I am suggesting a bit clearer.

---

### Post by lkraemer on 2012-08-10
defu,
All the *.deb files will reside on your server at: /var/cache/apt/archive

But, you are trying to install from a USB Flash Drive that is mounted
at some location on your server.  You have to find that path where the
USB Flash Drive is mounted.  Use one of these commands:
```

dmesg | tail
mount
sudo blkid
fdisk -l

```
Assume your USB is mounted at /dev/sdc1 on /media/D003-91F5
You can copy the *.deb's to /var/cache/apt/archive and then install the 
software or install from the USB.
Change your dir to either Source Path or Destination Path.
```

cd /var/cache/apt/archive
cp /path/to/files/on/mounted/USB/*.deb .

```
DON'T Overlook the "PERIOD" at the end of the above line which means "Current Location".
Or use a direct install from USB.
```

sudo dpkg -i /media/D003-91F5/wireless-tools_30-pre9-3ubuntu4_i386.deb

```

Be sure to un-mount your USB Flash drive with the command:
```

umount /media/D003-91F5

```


Larry

---

