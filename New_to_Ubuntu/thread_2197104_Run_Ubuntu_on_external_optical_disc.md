---
title: "Run Ubuntu on external optical disc"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by jonesjoo on 2014-01-02
Hello everyone! As my tablet doesn't have an optical disc installed. Can I just put my Live CD in an external optical disc, and connect it to the tablet by cable, then boot from there? In this way can I install Ubuntu on the tablet? Your help is much appreciated!

---

### Post by Bucky Ball on 2014-01-02
> **jonesjoo said:**
> Can I just put my Live CD in an external optical disc, and connect it to the tablet by cable, then boot from there? In this way can I install Ubuntu on the tablet? 

Welcome. Yes and yes. The difficulty may be that you would need to boot from the connected optical drive. If you can tweak the BIOS to do that, and providing the specs of the machine meet the minimum system requirements, then full steam ahead. ;)

---

### Post by MartyBuntu on 2014-01-02
Which tablet do you have?

---

### Post by jonesjoo on 2014-01-02
> **Bucky Ball said:**
> Welcome. Yes and yes. The difficulty may be that you would need to boot from the connected optical drive. If you can tweak the BIOS to do that, and providing the specs of the machine meet the minimum system requirements, then full steam ahead. ;)

I just tried to do this with my laptop and find there seems a problem.

I booted the Live CD from the external optical disc with a blank hard drive, the Live CD ran for about 30 seconds, then it stopped spinning. The black page I got show:

[   20.303378] Kernel panic - not syncing: Attempted to kill init! exitcode=0X00000100
[   20.303378]
[   20.303446] drm_kms_helper: panic occurred, switching back to text console

I am not sure if there is a problem with the cable or the optical disc. If I put the Live CD in my internal optical drive, it runs smoothly. Please help!

> **MartyBuntu said:**
> Which tablet do you have?

I am planning to buy an ipad.

---

### Post by 3rdalbum on 2014-01-02
> **jonesjoo said:**
> I am planning to buy an ipad.

iPads are locked to their own iOS system software. You can't run any alternative operating systems on an iPad.

If you want to run Ubuntu, you need a Windows 8 tablet with an x86 processor, OR a Google Nexus 7.

---

### Post by Impavidus on 2014-01-02
Instead of putting a cd (or dvd) in an external drive, isn't it easier to put the iso on an usb flash drive?

---

### Post by jonesjoo on 2014-01-02
> **Impavidus said:**
> Instead of putting a cd (or dvd) in an external drive, isn't it easier to put the iso on an usb flash drive?

I have a Live CD but not a USB now. So I just want to see if it's possible to run the Live CD from an external optical drive?

> **3rdalbum said:**
> iPads are locked to their own iOS system  software. You can't run any alternative operating systems on an iPad.

If you want to run Ubuntu, you need a Windows 8 tablet with an x86 processor, OR a Google Nexus 7.

Thanks for your info then I won't choose ipad. Is there a list of tablet which allows me to run Ubuntu?

---

### Post by monkeybrain20122 on 2014-01-02
> **jonesjoo said:**
>  Is there a list of tablet which allows me to run Ubuntu?

[https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)

---

### Post by Jonathan Precise on 2014-01-02
Did you check the md5sum of the image, to see if it matches with the one ubuntu has? [uhelp]community/HowToMD5SUM[/uhelp]

If the md5sum matches, then you probably have **L**(ogical)**V**(olume)**M**(anager).

If they don't match, re-download the ISO, and see if it works. If not, repeat.

---

### Post by jonesjoo on 2014-01-02
> **Jonathan Precise said:**
> Did you check the md5sum of the image, to see if it matches with the one ubuntu has? [uhelp]community/HowToMD5SUM[/uhelp]

If the md5sum matches, then you probably have **L**(ogical)**V**(olume)**M**(anager).

If they don't match, re-download the ISO, and see if it works. If not, repeat.

I have never done that. Actually I tried to download from the official Ubuntu page but it's very slow, so I got it from BitTorrent.
Is it normal for the slow download speed? I think I will try again in the next few days.

But can I just confirm it's possible to run the Live CD from an external optical disc and install it on a tablet?
I am going to choose a tablet as I find it much more convenient to use than a laptop.

---

### Post by Jonathan Precise on 2014-01-02
I have a very, very slow slow internet (I think 1 MB/s), so it takes me about 3-4 hours for an Ubuntu [noparse]<=[/noparse] 12.04 CD, and 4-6 hours for an Ubuntu 12.10+.

As for tablets, see the link monkeybrain20122 posted.

---

### Post by chkneater on 2014-01-02
Theoretically it should be possible as long as you can access the BIOS to boot from USb, (I know you're using DVD but you problly have it attached as USB) Try running the live DVD from a laptop or working comp and make sure it the BIOS is set to boot from USB first, if the DVD works great.

The issue will be: does the bios of the pad allow changes?  and if so you may have to use a chainloader or grub-imageboot to get it booted.

Once you confirm that the DVD is working let us know...

---

### Post by sudodus on 2014-01-02
> **jonesjoo said:**
> I have never done that. Actually I tried to download from the official Ubuntu page but it's very slow, so I got it from BitTorrent.
Is it normal for the slow download speed? I think I will try again in the next few days.

But can I just confirm it's possible to run the Live CD from an external optical disc and install it on a tablet?
I am going to choose a tablet as I find it much more convenient to use than a laptop.

It is possible in general to boot a computer from a CD/DVD drive connected via USB. But we don't know yet if the particular tablet you plan to buy will boot that way. If you plan to buy it in a physical store (not from a web store), you can bring the equipment and test it.

But USB pendrives are very cheap nowadays. Cheap and slow pendrives are sometimes (often?) good booters, for example *Sandisk Cruzer Blade 4GB*, so it might be a good alternative.

---

### Post by chkneater on 2014-01-02
Yeah, most reputable stores should let you bring your external drive to check if it's compatible or not

---

### Post by Bucky Ball on 2014-01-02
> problem with the cable or the optical disc.

^^^
This.

If the disk is running fine in an internal drive (and I'm presuming you mean in another machine) then there is an issue with the cable, the external optical drive, or the thinking on the device you're attempting to install to. No md5sum required, the disk is working fine in another optical drive so you would say that's fine.

---

### Post by Bucky Ball on 2014-01-02
> **chkneater said:**
> 

Once you confirm that the DVD is working let us know...

This was confirmed quite a few posts ago. See post #4 ...

---

### Post by jonesjoo on 2014-01-02
Thanks for all the replies.

It seems the external optical drive works fine as I can read the files in the Live CD when it is connected to a hard drive with Ubuntu installed. So the problem is I am unable to boot Ubuntu from my external optical drive.

I removed my hard drive and connected the pc to the external optical disk with the Live CD, then pressed the power button to switch the laptop on. The Live CD spinned for about a minute, then it stopped with the following messages in black screen.

> **jonesjoo said:**
> 

[   20.303378] Kernel panic - not syncing: Attempted to kill init! exitcode=0X00000100
[   20.303378]
[   20.303446] drm_kms_helper: panic occurred, switching back to text console

 

I need to confirm I can boot Ubuntu from my external optical drive before buying a tablet and installing Ubuntu on it. Please help!

---

### Post by sudodus on 2014-01-02
Did you check the md5sum of the downloaded iso file?

How did you create (burn) the boot CD?

Can you test that it can boot another computer with a built-in CD/DVD drive?

How did you connect it when you tested?

Did you check or change in the BIOS/UEFI menus, that the computer is supposed to give it priority when booting?

---

### Post by jonesjoo on 2014-01-02
> **sudodus said:**
> Did you check the md5sum of the downloaded iso file?

How did you create (burn) the boot CD?

Can you test that it can boot another computer with a built-in CD/DVD drive?

How did you connect it when you tested?

Did you check or change in the BIOS/UEFI menus, that the computer is supposed to give it priority when booting?

Hi the Live CD works well when placed in an internal optical drive and it is ready to use after about 5 minutes.
Unlike the situation when it's placed in the external optical drive, the message "[   20.303378] Kernel panic ... " doesn't show up.
However the external optical drive and the associated cable seems working as I can read the files in the Live CD disc from the external optical drive.
The matter now seems there is a problem to boot the disc from external optical drive.
Unfortunately I only have one laptop available for this test but I guess it works for some other laptop when the CD is put in the internal optical drive.

I have no knowledge at Linux or Ubuntu at all but I am thinking if the answer to the problem could be found from the message I've got. Thanks!

---

### Post by sudodus on 2014-01-02
It is good to know that the CD disk works in an internal drive. So the problem is with this external drive.

There might be a solution, but I would recommend, that you get (buy or borrow) a USB pendrive (for example a cheap Sandisk Cruzer Blade 4GB pendrive) and flash the iso file to it with one of the methods in [this link]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by jonesjoo on 2014-01-02
> **sudodus said:**
> It is good to know that the CD disk works in an internal drive. So the problem is with this external drive.

There might be a solution, but I would recommend, that you get (buy or borrow) a USB pendrive (for example a cheap Sandisk Cruzer Blade 4GB pendrive) and flash the iso file to it with one of the methods in [this link]("https://help.ubuntu.com/community/Installation/FromUSBStick").

I am not sure as I can read the files in the Live CD placed in the external optical drive WHEN I am running the Ubuntu booted from the same CD inside the internal optical drive.
I can use a USB pendrive but I prefer to just use the CD. What do you think the problems are according to the messages I posted above?

---

### Post by sudodus on 2014-01-02
Kernel panic is that there is a serious problem in the Linux kernel. Some instructions go wrong, maybe because there is a mismatch between some driver and the hardware it is supposed to control. Such problems are far above my head.

The only tip I could give is that you try with some [boot option]("https://help.ubuntu.com/community/BootOptions"), but I really have no idea. Maybe this reply will make someone else interested and come with a solution :-)

---

### Post by jonesjoo on 2014-01-02
> **sudodus said:**
> Kernel panic is that there is a serious problem in the Linux kernel. Some instructions go wrong, maybe because there is a mismatch between some driver and the hardware it is supposed to control. Such problems are far above my head.

The only tip I could give is that you try with some [boot option]("https://help.ubuntu.com/community/BootOptions"), but I really have no idea. Maybe this reply will make someone else interested and come with a solution :-)

Will it help if I download another copy of Ubuntu from [http://www.ubuntu.com/download/desktop?](http://www.ubuntu.com/download/desktop?)
Is it because my machine is unable to boot from any external optical drive?
But I am going to buy a tablet from [https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices), perhaps it will work when connected to the tablet? I am not sure though...

---

### Post by sudodus on 2014-01-02
Since the CD disk works in the internal CD drive, I don't think it helps to download another iso file (but I am not 100% sure, try it if you wish). I think the problem is to boot from the external CD drive. It was made for playing and reading/writing files, but the designer might not have considered booting from it.

---

### Post by Bucky Ball on 2014-01-02
You can see the files on the disk but that doesn't mean much. Doesn't mean it is going to boot, and obviously it isn't going to work as a burnt image install disk.

How did you create this disk? Download ISO, burn disk image??? You didn't just plop the ISO on to the disk drag-and-drop style? Might be a silly question, but worth asking at this point. 

Can you boot from the disk to a Live Ubuntu on another machine with an internal optical drive??? Does it actually boot and run and come up with the options 'Try Ubuntu' 'Install Ubuntu' etc. ???

When you say you are going to buy a tablet from [https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices) I don't really know what you mean. That is info about the Ubuntu Touch Developer software. I don't see anywhere to buy a device ... :-k

---

### Post by jonesjoo on 2014-01-02
> **sudodus said:**
> Since the CD disk works in the internal CD drive, I don't think it helps to download another iso file (but I am not 100% sure, try it if you wish). I think the problem is to boot from the external CD drive. It was made for playing and reading/writing files, but the designer might not have considered booting from it.

For the external optical drive, I am now using HP dvd550s.
Should I buy another external optical drive? If yes, which one is good?

---

### Post by Bucky Ball on 2014-01-02
Please respond to post #25 also. ;)

---

### Post by jonesjoo on 2014-01-02
> **Bucky Ball said:**
> You can see the files on the disk but that doesn't mean much. Doesn't mean it is going to boot, and obviously it isn't going to work as a burnt image install disk.

How did you create this disk? Download ISO, burn disk image??? You didn't just plop the ISO on to the disk drag-and-drop style? Might be a silly question, but worth asking at this point. 

Can you boot from the disk to a Live Ubuntu on another machine with an internal optical drive??? Does it actually boot and run and come up with the options 'Try Ubuntu' 'Install Ubuntu' etc. ???

When you say you are going to buy a tablet from [https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices) I don't really know what you mean. That is info about the Ubuntu Touch Developer software. I don't see anywhere to buy a device ... :-k

I can boot Ubuntu from my own laptop with my hard drive removed. So, yes, I downloaded the ISO and burnt disk image.

---

### Post by sudodus on 2014-01-02
> **jonesjoo said:**
> For the external optical drive, I am now using HP dvd550s.
Should I buy another external optical drive? If yes, which one is good?

No, don't buy another optical drive. It is much cheaper, easier and more modern to buy a USB pendrive, and boot from that.

---

### Post by jonesjoo on 2014-01-02
> **sudodus said:**
> No, don't buy another optical drive. It is much cheaper, easier and more modern to buy a USB pendrive, and boot from that.

Yes I am thinking of giving up the idea of booting from a CD. It seems much simpler using the USB pendrive.

---

### Post by Bucky Ball on 2014-01-02
Ok, so, as mentioned posts ago, a problem with the external optical drive, cable or the way the device is dealing with the external hard drive. Disk is in working order. 

You could try replacing the external drive, but ... can you plug the external drive into the computer that boots the disk fine from its internal drive and boot the disk from the external drive fine??? If so, that also rules out any problems with the external optical drive and cable. That would leave only the fact that the laptop is having issues booting from the external drive and there's the issue.

If you are going to the trouble of buying another external optical drive, just go the USB option. Much cheaper. Not sure why you don't want to try that route ...

Anyway, try and rule it out by booting from the external drive plugged into the other computer that boots the disk fine from its internal drive. You will need to have it plugged in and switched on before booting the machine for it to be picked up by the BIOS and set as a boot device, naturally ... ;)

---

### Post by sudodus on 2014-01-02
If you want to buy some other equipment, I suggest an adapter to connect a SATA or IDE drive to USB. Such a device is handy, and can connect a hard drive, SSD and an internal CD/DVD drive via a USB port. And it is possible to boot from most of them. I have such a device that works well to boot from.

---

