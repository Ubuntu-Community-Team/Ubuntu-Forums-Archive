---
title: "Where does the download file will go if i uses Try Ubuntu option on liveusb ubuntu"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by jatin2 on 2014-08-12
hi , i am using live version of ubuntu from my 8GB sandisk penderive by going with "Try Ubuntu" option. Now my situation is i had formatted my hard derive and do not want to write over anything to it by mistake(thats why i am using liveusb) , so now my questions are:

1. If i download any song or picture , where does it go. Is it go to hard disk or the live pen derive(in which ubuntu is installed)?
2. Does i am writting anything un unintensionally to my Hard disk whenever i use my laptop through live usb(live penderive).?
3.If i watch any video on youtube then where that portion of the video will be saved which is already buffered , into Hard disk or into live usb?
4. Where does software installed through "Ubuntu software center" , goes i.e. to hard disk or live usb?

if answer to any or all of the above questions are "to hard disk" , then is their any way by which i can change the setting so that evrerything will be written to live usb instead of hard disk so that nothing will be over written on my hard disk?

Thank you so much.

---

### Post by kc1di on 2014-08-12
if you are using the usb live option and not using persistence mode with it. Then everything you do is written to the partition in 
the live usb , nothing going to your H.D.  but in that case everything will be lost when you reboot your machine. 
nothing will be saved.

---

### Post by jatin2 on 2014-08-12
thanx for reply , it give me sense of calm. Ok, if thats the case then once i downloaded a picture(i dont know where it goes) and then i plugged out my live usb after shutting my laptop down and tried to find that picture in that live usb through one of my friend's laptop but i was not able to find it by using Default search option in windows 8 (in my friend's laptop). Any idea what had happened?

---

### Post by bradwilliams923 on 2014-08-12
The downloaded file was lost when you terminated the live session. If you want to download something from a live session and keep it, mount the computer's hard drive and copy the file there. Typically, the default for downloaded files is in /home/(*username*)/Downloads, but of course you can specify within your web browser if you want the file downloaded to a mounted drive.

Edit: If you're wanting to use linux as a live usb only, and don't intend to install it, there are persistence-enabled distributions which will run in memory and enable you to save files to the pen-drive. You might want to look into Puppy Linux and its variants. The Ubuntu live instance is primarily intended for installation and rescue.

---

### Post by JKyleOKC on 2014-08-12
> **kc1di said:**
> if you are using the usb live option and not using persistence mode with it. Then everything you do is written **to the partition in the live usb** , nothing going to your H.D.  but in that case everything will be lost when you reboot your machine. 
nothing will be saved.Not quite correct, Dave. When running from a live CD/DVD/USB, the system uses a RAM drive that resides entirely in the RAM of the host machine. Thus anything "saved" when not in persistence mode simply goes to another area of RAM, and is lost when the session ends.

In other words, running from a live CD/USB device is much like running a virtual machine; what you see isn't really what you are getting.

However to set the OP's mind at ease, nothing goes to the HD unless you're in persistence mode -- and you can't get there entirely by accident.

I see by your handle and avatar that you're a ham. I was for quite a few years; then I discovered computers!

73 de ex/K5JKX

---

### Post by kc1di on 2014-08-12
Hi Jim (K5JKX)

I too used to be very active, mostly H.F. But in the last few years have been doing more and more with computers and Ham Radio has suffered. 

What the Op needs to know is that nothing in the live session out side of persistence mode is saved.  I would say he need Persisitance if you wants to save anything
and He can follow[ this wiki]("https://help.ubuntu.com/community/LiveCD/Persistence") if he wants to use Ubuntu live persistence.

---

### Post by grahammechanical on 2014-08-12
I would also like to add that it is also possible to install Ubuntu on a USB memory stick with persistence. I have done it with Edubuntu. But I have done from an installed Ubuntu using USB Creator.

If the hardware permits it is possible to run a Ubuntu live session from a DVD drive and install Ubuntu to the USB stick and thus create an install of Ubuntu with persistence. Then any files downloaded will go into the default folder that the web browser is set to, which is Downloads and will still be on the USB stick when it is next rebooted. And should be accessible from another OS.

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

Make sure that grub is being installed into the USB stick and not the default option of sda.

Regards.

---

### Post by 3rdalbum on 2014-08-13
To clarify a little, no matter if you set up persistence or not, nothing will go to your hard disk unless you explicitly mount it and explicitly put something there.

---

### Post by marco-parillo on 2014-08-13
> **3rdalbum said:**
> To clarify a little, no matter if you set up persistence or not, nothing will go to your hard disk unless you explicitly mount it and explicitly put something there.

I think you have the right spirit there (the default file system is in RAM which gets lost when you power down, so, without persistance, nothing is saved by default). However, at least in Kubuntu Live USB, Dolphin mounts your unencrypted hard drives (even NTFS) automagically. You have to explicitly save something there, but I have never had to mount an unencrypted hard drive myself. I suspect the same is true for with the file managers on all flavours.

---

### Post by bradwilliams923 on 2014-08-13
Is Dolphin actually mounting those volumes, or just identifying them? I'm not a Dolphin user, but I noticed with other file managers that sometimes the drive will pop up on the list but not actually mount until you click on it. It's also not always overtly stated whether it's mounted or not, even when you do mount it.

---

### Post by marco-parillo on 2014-08-16
> **bradwilliams923 said:**
> Is Dolphin actually mounting those volumes, or just identifying them? I'm not a Dolphin user, but I noticed with other file managers that sometimes the drive will pop up on the list but not actually mount until you click on it. It's also not always overtly stated whether it's mounted or not, even when you do mount it.

 I think you might be right. The first time I open Dolphin from a live USB, I see in the left hand navigation my 229.1 GiB Hard Drive. The right-click options do not include mount or unmount, but after I left-click on it, I immediately see the file structure (so fast it did not occur to me a mount might be happening). However after I left-click on it once, and see my hard-drive's file structure, now a new right-click option is available: Unmount 229.1 GiB Hard Drive.


But, from a New to Ubuntu point of view, a user can (I know because I have done so) save files onto a hard drive using Dolphin in a live USB session without explicitly mounting via a mount command. I just did not know that Dolphin was quietly doing the mount for me as I was navigating my hard drives file hierarchy.

An experienced user using the command line might have to issue an explict mount to read a hard drive from a live USB session, but I figure that is outside the scope of this New to Ubuntu forum.

---

### Post by marco-parillo on 2014-08-16
bradwilliams923: You *ARE* right. Dolphin quietly mounts volumes when you click on them. I opened a terminal session and issued mount commands before and after I clicked on my 229.1 GiB Hard Drive.
```

kubuntu@kubuntu:~$ mount > before
kubuntu@kubuntu:~$ mount > after
kubuntu@kubuntu:~$ diff before after
18a19
> /dev/sda1 on /media/kubuntu/7a183570-535c-4327-98ca-27de0a2961b1 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
```

---

