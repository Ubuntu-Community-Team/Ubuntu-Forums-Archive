---
title: "Manually mounting a Digital Camera"
date: 2004-12-29
forum: Outdated Tutorials &amp; Tips
---

### Post by gregorian21 on 2004-12-29
Just bought a digital camera (Sony DSC-V3), took some pictures and tried to offload the images to my computer via the USB port.
 On Windows you normally get an indication telling you that the camera has been detected and mounted and the images can be transferred. Being a Linux and Ubuntu newbie I wasn't sure what to expect when I connected the camera to the USB port.
 So connected the camera and switched on the USB transfer mode, but nothing happened. Tried to access the photos using gThumb as was suggested in a few posts, but my camera wasn't detected. I suspect the camera uses PTP over USB, so I manually set the value to Sony DSC-V1, but the camera was still not being detected.
    So I tried to mount the drive manually as explained in the excellent** [color=black][Ubuntu Starter Guide]("http://ubuntuguide.org/index.html#mountunmountfat")[/color]**, as follows:
  
 

[list=1]
[*]Created a new mount point**:      [color=black]$ su[/color][font=Courier New][color=black]do mkdir /mnt/camera[/color][/font]**
[*]Mounted the camera: [color=black]**     $ sudo mount /dev/sda1 /mnt/camera -t vfat -o umask=000**[/color]
[/list]and I had instant access to my photos in the /mnt/camera directory.
    
    I am not certain, but I think it's important to unmount the device before disconnecting it from the computer by issuing the **[color=black]$ sudo umount /mnt/camera[/color]** command.
    
 The above may seem simple to Linux gurus, but I spent the best part of an hour trying to figure that out. I'm hoping my post will help others in the same situation.:)[color=black]
    [/color]

---

### Post by alpha on 2004-12-29
[QUOTE=gregorian21]Just bought a digital camera (Sony DSC-V3), took some pictures and tried to offload the images to my computer via the USB port.
 On Windows you normally get an indication telling you that the camera has been detected and mounted and the images can be transferred. Being a Linux and Ubuntu newbie I wasn't sure what to expect when I connected the camera to the USB port.
 So connected the camera and switched on the USB transfer mode, but nothing happened. Tried to access the photos using gThumb as was suggested in a few posts, but my camera wasn't detected. I suspect the camera uses PTP over USB, so I manually set the value to Sony DSC-V1, but the camera was still not being detected.
    So I tried to mount the drive manually as explained in the excellent** [color=black][Ubuntu Starter Guide]("http://ubuntuguide.org/index.html#mountunmountfat")[/color]**, as follows:
  
 

[list=1]
[*]Created a new mount point**:      [color=black]$ su[/color][font=Courier New][color=black]do mkdir /mnt/camera[/color][/font]**
[*]Mounted the camera: [color=black]**     $ sudo mount /dev/sda1 /mnt/camera -t vfat -o umask=000**[/color]
[/list]and I had instant access to my photos in the /mnt/camera directory.
    
    I am not certain, but I think it's important to unmount the device before disconnecting it from the computer by issuing the **[color=black]$ sudo umount /mnt/camera[/color]** command.
    
 The above may seem simple to Linux gurus, but I spent the best part of an hour trying to figure that out. I'm hoping my post will help others in the same situation.:)[color=black]
    [/color][/QUOTE]
 Thanks for that. :D
It'll come in handy when I receive my install disk sometime next year.

---

### Post by kleeman on 2004-12-29
You many also want to check out gtkam and digikam (gtk and kde apps) which use the libphoto2 libraries to read digital camera info. Worked well with my canon powershot a75 (after upgrading libphoto2)

---

### Post by adroit on 2005-01-01
this configuration works to webcams????

how I can make work my webcam???

---

### Post by gregorian21 on 2005-01-01
[QUOTE=adroit]this configuration works to webcams????
   
 how I can make work my webcam???[/QUOTE] The above procedure should work for digital cameras or external HDDs connected via USB. As for webcams, I haven't tried one with Ubuntu (or any flavour of Linux for that matter), so I wouldn't have a clue... sorry.
   
   A quick search on [gnomefiles.org]("http://gnomefiles.org/") brought up apps like [camorama]("http://camorama.fixedgear.org").
   Give it a try if you haven't already.

---

### Post by mirtux on 2005-03-06
[QUOTE=kleeman]You many also want to check out gtkam and digikam (gtk and kde apps) which use the libphoto2 libraries to read digital camera info. Worked well with my canon powershot a75 (after upgrading libphoto2)[/QUOTE]
Hi,
   one question regarding digikam: i have problems accessing photos from a Powershot A400 camera when running digikam as a non root user. Everything goes smoothly when running as root. I've tried to change the write permissions of /usr/bin/digikam but nothing has changed.
Any ideas,
thanks,
MC

---

### Post by stateq2 on 2005-03-06
to add...you may also want to edit your fstab to make things a bit easier
```

/dev/sda1       /media/usb      auto    rw,user,noauto  0   0

```

that way, users can mount by:
```

mount /dev/sda1

```
and have read/write access to it.

---

### Post by Quest-Master on 2005-03-06
Actually, it is not needed to mount the digital camera when plugged in, as it will be automatically mounted.

However, if you do not unmount it, you will experience corruption on whatever kind of removable media it is. A reformat will be needed, and all data will be lost. Trust me, I learned the hard way, believing that Project Utopia automatically did the unmounting as well. :(

---

### Post by mirtux on 2005-03-07
Hi,
 i don't need to mount the camera as this is automatically done by digikam... as a root user..... I cannot access it as a normal user.

MC

---

### Post by Beire on 2005-03-07
[QUOTE=mirtux]Hi,
 i don't need to mount the camera as this is automatically done by digikam... as a root user..... I cannot access it as a normal user.

MC[/QUOTE]
 $ sudo mount /dev/sda1 /mnt/camera -t vfat -o umask=000
mount: special device /dev/sda1 does not exist

:/

---

### Post by thekore on 2005-03-07
[QUOTE=Beire]$ sudo mount /dev/sda1 /mnt/camera -t vfat -o umask=000
mount: special device /dev/sda1 does not exist

:/[/QUOTE]
 im afraid i get the same error...

---

### Post by gregorian21 on 2005-04-09
I got the same message on Warty.
By the way, I upgraded to Hoary and the problem disappeared. In fact Hoary now recognises my camera and even offers to import the images... couldn't ask for more :)

---

### Post by kuleali on 2005-04-12
thank's for this fine HOWTO.

---

### Post by KrazyPenguin on 2005-05-04
I'm using a FinePix A120, good dig camera for the price.

It works fine with Hoary and SimplyMepis 3.3.

Just plug it into the USB port, open the camera door, and it gets automounted.

Then I can see the pictures immediately on the computer, save them and whatever.

When the camera door is closed , the camera gets unmounted immediately and disappears from the desktop.

:cool:

---

### Post by gunnyman on 2005-05-04
I'm having similar issues with an Olympus C700UZ
It mounts as a usb thumb drive on my desktop.
Digikam can't/won't communicate with it.

---

### Post by tregeagle on 2006-03-13
Thanks for that, I was pulling my hair out!! Works well.
although I've very little clue what: "-t vfat -o umask=000" means

Now I will go fix up my fstab as suggested by stateq2.

....learning s l ow l y by my many mistakes :)

---

### Post by thechosenOne on 2007-02-10
This would work when the device is sda1. In my case, the camera was on sdb1 - so one needs to try this out as well  !! :)

---

### Post by LyonTamer on 2009-06-14
lenathelaptop@lenathelaptop:~$ sudo mkdir /mnt/camera
[sudo] password for lenathelaptop: 
lenathelaptop@lenathelaptop:~$ sudo mkdir /mnt/camera
mkdir: cannot create directory `/mnt/camera': File exists
lenathelaptop@lenathelaptop:~$ sudo mount /dev/sda1 /mnt/camera -t vfat -o umask=000
mount: /dev/sda1 already mounted or /mnt/camera busy
mount: according to mtab, /dev/sda1 is mounted on /
lenathelaptop@lenathelaptop:~$ 

Indeed, it shows in Places as USB Drive. So why can I not open it and look at the files? :/

When I try to unmount:

lenathelaptop@lenathelaptop:~$ sudo umount /mnt/camera
umount: /mnt/camera: not mounted

Oy!

---

