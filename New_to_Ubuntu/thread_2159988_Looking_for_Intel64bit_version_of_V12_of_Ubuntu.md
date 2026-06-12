---
title: "Looking for Intel64bit version of V12 of Ubuntu"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by TDIT on 2013-07-05
Hi all,
Here's the deal:
I'm running 12.04 32bit now and it's great, but I have a 64bit system, so I would like to utilise it. So I backed up my data and downloaded the amd64bit 12.04 version. Booting from a dvd made from iso, the system boots from the dvd but all i get is a flashing cursor for 20 seconds, then a reboot. Did some research, and found some issues with certain bios versions. Okay, went in and turned off any fast boot options and other unneeded features. Ony difference it made was the flashing cursor would flash longer - 30 seconds. woo hoo 10 seconds of um, progress. 

So I made another disk from a confirmed md5 iso and even did it on another system. Then brought the disk back to the Ubuntu box - eek, same problem. Okay, a bit annoying, but life goes on. Then I thought, uh-huh! I have the AMD version and I need the Intel (silly me!) But I can't find an intel version of v12.04 64bit. So I'm confused. Should I just accept my 32bit version runs on the 64 bit system and call it a day, or can I get the 64bit to work and (at least) have the os running to its potential?

My hardware is:
Chipset: NM10 Express 
GPU: Intel GMA 3600
Intel Atom D2500 (dual-core) (1.86 GHz)

Does anyone have any suggestions to get a 64bit ver running? Or should I just accept I have the 32bit 12.04 humming and leave it at that?

Cheers!

---

### Post by grahammechanical on 2013-07-05
We do not have an Intel64 ISO image. There is no need for one. The AMD64 image works on both AMD and Intel 64 bit CPUs. I have several installations of Ubuntu (all amd64) running on my Intel Core 2 Duo CPU.

Intel developed the 32bit i386 cpu so the 32bit Linux kernel is called i386. But AMD got in first with a 64bit cpu that ran Intel cpu instruction set. So, the 64bit Linux kernel is called AMD64.

Did you have this issue when you installed 12.04 i386? There is something that you can try.

1) At the first screen, purple with icons of human and keyboard, press Enter.
2) At next screen press Enter to select English as the default language. Or select the language of your choice.
3) At the TRY UBUNTU - INSTALL UBUNTU screen press F6
4) A small menu will appear (at the bottom right of the screen) scroll down to nomodeset and press Enter to select that option.
5) Press Esc to get back to the TRY - INSTALL screen.
6) TRY UBUNTU should be selected - Press Enter.

Does that get you to a live session? There are other options in that F6 menu. You may need to try the others. Even a combination of them.

Regards.

---

### Post by TDIT on 2013-07-06
Hi mate, thanks for your detailed reply - and understanding I'm quite a noob at Ubuntu and Linux as a whole. I really appreciate it. 
Well, I've made some progress at resolving the problem based on following your instructions. Even though I just get a flashing cursor on a black screen and nothing like "purple with icons of human and keyboard", I hit enter and thought maybe something different would happen. Well it did. It booted from the hard drive and went into the installed 32bit Ubuntu. So that told me that, although all I could see was a flashing cursor, there had to be a grub like menu at work here. Rebooted again, this time hit the down arrow, and t'dar; my HDD Grub menu was visible. So, rebooted again, this time with a puppy live iso burnt to the drive in the drive, and it booted to it. tried my 32bit Ubuntu 12.04 dvd and it booted to that too. Odd! So I tried a third download of the Ubuntu amd64bit (that's for explaining that btw!) and burnt it via a third system. I then tried to boot from it in that system and it started to boot but then failed - probably because it was a 32bit machine. So, I bring that booting cd back to my Ubuntu machine, tried to boot and got the flashing cursor problem again... Very confusing. I can offer no suggestion as to why this dvd will not boot in this machine, but other versions will. Even Ubuntu 32bit 12.04 will boot to a live session via dvd in this machine, it's only the 64bit that won't.

I'm thinking a usb stick might boot better??? I don't have any logic to explain why it might work, but I'm out of options and have nothing to loose!

I'll try it in a few hours and post my response. I say a few hours as I have to learn how to do it first :)

Cheers!

---

### Post by TDIT on 2013-07-06
okay, here's the update. made a boot usb (8gb) stick using the startup disk creator. Used the iso image for amd64bit 12.04 which I just downloaded (again rofl) from the Ubuntu site. 

My bios will boot to it, no drama, but this is what happens when it tries to:
power on, bios screen, black screen, then this:

Unknown keyword in configuration file: gfxboot
vesamenu.c32: not a COM32 image 
boot: _

I'm assuming I made a mistake with the usb creation, but I did it again and got the same result. What did I do wrong?

many thanks!

---

### Post by MoebusNet on 2013-07-06
Just in case, these are the instructions to make a Live-CD/DVD:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Make sure you have verified that you have downloaded an uncorrupted file by verifying the md5sum or sha256 sum. Look at the links under 'Verifying the ISO integrity' on the BurningISOHowto.

Try using the boot options for the Live-CD/DVD:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Common boot options required are *nomodeset*  and  *noapic* or a combination thereof. Look under 'Changing the CD's default boot options' on the BootOptions link above.

As far as I can tell, the netbooks have always been a bit problematic for Ubuntu simply because they weren't around all that long before they were no longer manufactured. That said, the only real advantage for you switching to 64-bit from 32-bit is that 64-bit would allow you to address more than 4Gb of RAM without a PAE kernel. If you only have 2Gb of RAM, I doubt you will notice much difference if/when you get 64-bit installed.

Just my opinion, YMMV.

---

### Post by TDIT on 2013-07-06
Thank you - will try asap. I have 8gb installed, but I'm doing this now as a wish list project (and learning experience) as much as a 'trying to get more performance' exercise. I'm finding the 32 bit version very responsive and wayyyyyy more stable than linux mint - which I tried before. This forum is also 10 times better than the lm forum. So already it's a great and positive experience. Will revert asap.

---

### Post by Rob Sayer on 2013-07-06
I have a netbook (I'm typing this on it) with an atom 2600 cppu with the 3600 gpu (ie. cedarview/cedartrail).  I've had some experience with this architecture.  In fact I've had more  issues getting this netbook running well with linux than all the other laptops I've installed linux on put together ... admittedly not as many as some on this board.

12.04 can work fine with cedarview machines, but 13.04 works a lot better.  The drivers for the 3600 gpu aren't available as open source, as they are in every other intel gpu I know of.  That's  because they were outsourced and that company won't give up all the source code.

The drivers you can get in linux ... which work but don't use the full power of the gpu ... can be installed in 12.04 through additional drivers after making sure you fully update the system first.  If you don't it'll bonk the video.

These drivers were moved into the linux kernel properly in a kernel version that came after 12.10.  Which is why 13.04 works much better.

Do *not* install a 64 bit version of  linux with the 3600 gpu.  Those drivers are 32 bit *only*.

---

### Post by TDIT on 2013-07-06
So - in reading the above - I should stop trying?

I've verified the iso, checked all the bios settings, made a new usb key and still I'm stuck. I tried to download 64bit Ubuntu13, but I get a server down message. I should remind that i can;t even get a live cd/ usb to run on this machine with Ubuntu64bit. But I did with linuxmint64 - I had many other issues, and poor support, so made the switch. 

I think I'll wait till i can download Ubuntu13 to the usb and try to boot from that again. If that fails, I'll just be happy with 32bit Ubuntu and call it a day :)

If anyone could post a link as to how to make a usb bootable with Ubuntu (any flavour) - other than using the Startup Disk Creator - I would be extremely grateful!

My thanks to all

---

### Post by MoebusNet on 2013-07-08
This covers booting from USB via several methods (usb-creator, Unetbootin, dd, grub2, grub-n-iso, etc.)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by TDIT on 2013-07-09
Hi all - I just wanted to post that I've had a success moment!

Using Universal USB Installer, from the site pendrivelinux.com, I was able to write the ISO I had downloaded (64bitamdv12.04) to a USB stick. One I did that it booted perfectly from the USB stick. No errors, it was perfect. That was the same ISO I'd been using all along - but it wouldn't boot from any dvd drive on this machine (I changed the drives also in effort to fix the problem.) I won't lie and say I know what went wrong, because I still don't! But I have a dual booting Ubuntu 12.4 32 and 64 bit machine now. I'm still testing the 64bit for stability and drivers etc - but so far all is well. 

I wanted to thank EVERYONE who helped with suggestions and ideas re this issue. I wouldn't have solved it without your help!

I hope this thread helps someone else also. Ubuntu is powerful and stable - though I wish Gnome was standard :)

Thank you all again!

---

### Post by TDIT on 2013-07-09
One last thing - use the Universal USB Installer program from Windows - not Linux. It will run on Linux via Wine, but it's problematic re finding drive letters etc. So I think it's best to use Windows for it (I used XP) and it was perfect.

---

