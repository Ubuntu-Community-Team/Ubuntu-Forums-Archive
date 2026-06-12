---
title: "Live USB Boot Issue -- Encryption?"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by Finlay M on 2012-12-08
So I installed Ubuntu 12.04 LTS on my computer (it's the only OS present) and it's working wonderfully, except for one issue. I can't boot up without having the live USB that I used to install it plugged in. When it's not plugged in my laptop just hangs on a black screen with a pulsing "_" in the top left corner. When I DO boot up with the USB plugged in (I'm actually booting off of the hard drive, but the USB is plugged in anyway) before Ubuntu starts up I get something like the following message:

 The disk drive for /dev/mapper/cryptswap1 is not ready or is not yet present. Wait to continue, press S to skip, or M for manual recovery.

Now I HAVE tried pressing M when prompted, but to no avail. Also, it may be worth mentioning that when I installed Ubuntu I checked the "encrypt your home folder" box, so that may be where the cryptswap thing is coming into play.

Any help figuring out what I can do to boot w/o my USB would be great.

Thanks,

Finlay

---

### Post by oldfred on 2012-12-08
Welcome to the forums.

Often we see the grub boot loader installed to the flash drive as the default install is to sda. Some systems promote flash to sda and then boot loader is on wrong drive.
Did you install swap on flash?

May be best to see where everything is at. Plug in flash drive before running.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by mungatsuma on 2012-12-08
Welcome to the Forum. My guess would be that your boot loader is installed on the USB. But we need to confirm that. There is a script here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) which will output all the required information. Please post the results so that the condition can be ascertained.

Seems like the above reply would help you more. Found it after posting that a reply had already been offered.

---

### Post by Finlay M on 2012-12-08
Alright! Here's the link! [http://paste.ubuntu.com/1419839/](http://paste.ubuntu.com/1419839/) 

Also, now I can boot into ubuntu without the USB stick. It boots into what I can only assume is some sort of "safe mode" for Ubuntu. I can boot normally, boot into safe mode, boot into previous versions, or do some other stuff. When i choose to boot normally I still get  that same message saying "The disk drive for /dev/mapper/cryptswap is not ready yet..." etc. but now it doesn't hang before getting there!

Thanks

---

### Post by oldfred on 2012-12-09
It looks like you ran the fix first, so now you do have grub in both the internal drive and the flash drive.

You encrypted /home so swap shows as unknown as it also is encrypted space. 
But I do not know why you get an error on booting.

---

### Post by C.S.Cameron on 2012-12-09
Normal fix for when grub gets installed to USB is to boot with USB plugged in, remove USB and in Terminal run:

```

sudo update-grub
```

---

### Post by Finlay M on 2012-12-10
Big help guys!

Thanks,

Finlay

---

