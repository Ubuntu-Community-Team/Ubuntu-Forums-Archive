---
title: "Booting from usb pen drive"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by Lucius Ferus on 2012-03-12
I downloaded ubuntu 11.10 and the isoimage, created pen drive whith the linux pen drive creator, but cannot boot from there. I've allready setted bios to boot from usb hard drive, but doesn't work. Don't know what i'm doing wrong. 
Can somebody help me please.
Thanx.

---

### Post by sudodus on 2012-03-12
Some computers boot better, when you make the USB boot drive with ***Unetbootin*** (there are versions for Windows and linux) that you can download for free.

You should also check with md5sum, that the download iso is good.

---

### Post by bohemian9485 on 2012-03-12
I always use Unetbootin for creating USB boot disk, it has a high success rate, aside from ease of use.

---

### Post by b4viral on 2012-03-12
> **Lucius Ferus said:**
> I downloaded ubuntu 11.10 and the isoimage, created pen drive whith the linux pen drive creator, but cannot boot from there. I've allready setted bios to boot from usb hard drive, but doesn't work. Don't know what i'm doing wrong. 
Can somebody help me please.
Thanx.
 
Hi,
 
have you tried booting it using keyboard shortcuts for multiboot options?
e.g.
you can use F8 for multiBoot options in Lenovo device
 
if you haven't i suggest you try that once.

---

### Post by dave2001 on 2012-03-12
Yes, like Sudodus mentioned, first you must check the md5sum for the iso you downloaded. After that, burn it to a CD and verify the image burned exactly correct with another md5sum.

Then, boot from the live CD to make sure your computer works with the default version of Ubuntu that comes on CD. Some computer hardware requires workarounds to put into place.

After doing all this, THEN try making a bootable pen drive, and get back to us with what works (or doesn't work).

---

### Post by varunendra on 2012-03-12
Hi Lucius, Welcome to the forums!
> **Lucius Ferus said:**
> I've allready setted bios to boot from usb hard drive, but doesn't work.
In my experience, a USB flash drive most often gets listed under the list of normal Hard drives, not 'USB hard drives'. This behaviour changes with different flash-drive brands and BIOS versions. So try other boot options as well (assuming the USB drive itself is working correctly, and only needs to be chosen correctly while booting).

Apart from changing the boot order in BIOS, there is also almost always a shortcut key to get the list of boot-devices. It gives you the option to select a boot device during boot-up without the need to change anything in the BIOS. This shortcut key can be any of the 'Function keys' (mostly F9 to F12), Esc, Del or Tab keys. The initial BIOS screen usually mentions which key does what.

Once you get this 'Boot-Device' selection menu, see if your USB drive is listed there (either separately, or under certain categories like under HDDs). If the BIOS has the capability to boot from it, it should (or should I say it _MUST_) list the drive by its brand name and model. Just select it and press 'Enter'.

If you find it in the boot-device selection menu but can't boot from it, it is not bootable and you need to recreate it using any of the different methods others have suggested. (my preferred method is the built-in Startup Disk Creator. To use it, I boot a Virtual Machine from the downloaded iso > connect the target USB drive to the VM > make it bootable using the 'cd' which is actually the iso that the VM sees as a cd)

If it isn't getting listed in that menu, it means either your BIOS doesn't have the option to boot from such devices, or it needs some basic changing to 'see' it as a 'boot-device'.

---

### Post by Mark Phelps on 2012-03-12
You can also try using the Universal USB Installer app from PendriveLinux.com.  I've had a high success rate with the USB sticks it formats and creates.

---

### Post by NikTh on 2012-03-12
Hi ,
i agree with varunendra's opinion and suggestions (as others as well) . An other option you can try (worked for me at past) is to disable all other boot options from Bios. Leave only Usb. 
And i guess iso that you downloaded is the full image.. not alternate. ha ? I think alternate works only with CD . (correct me if i am wrong) .
Good luck

---

### Post by bogan on 2012-03-13
Hi! **Lucius Ferrus**,

Whilst not disagreeing with the advice from previous Posts, I  do have some different advice.

Try your Usb in another, or preferably, several other computers.

My reason for this is that I have two Linux USB drives, a 4GB LiveUSB and an 8GB full-install updated Ubuntu 11.10 one.

On the computer that created them, neither will boot either directly, or when selected from the Grub Menu of the host OS. This despite being recognized and correctly named by the Bios with all options enabled.

I also tried them on another identical Medion MD8822 desktop computer with the same Bios, and the result was the same.

On the other hand both my Dell laptops will boot from both USBs, and so will a Dell 19T One 64bit computer.

So there is nothing wrong with the USBs. I just have to accept that the Bios in my desktop will not support a boot from a USB Flash drive, although it will from a CD, or from an external Sata/USB Hard drive.

Maybe yours is the same. Not good news! but might save you a lot of wasted efforts.

Edit: PS: I have not tried NikTh's suggestion: > to disable all other boot options from Bios. Leave only Usb. but will do so and update this later.

**EDIT2: In trying out NikTh's tip I got it to boot!! See separate Post**.

Chao!, **bogan**.

---

### Post by bogan on 2012-03-13
Hi! **Lucius Ferrus**,

** In trying out NikTh's tip [** to disable everything but USB **] I got it to boot!! **

Disabling everything else did not work, the computer just froze on the Intel Logo screen, and would not even go into Bios - I had to use the POST option to get back to the default settings.

But, in checking out all the options, I found one that gave three options for booting from a USB: **Auto,** - boot according to detected type, **FDD** - Boot as if a Floppy Drive, and **HDD** - Boot as if an HDD .

With the last selection, instead of 'Auto', the USB was no longer shown in the Bios Boot Menu, just HDDs or CDs; but when the HDD entry was selected, then the USB was listed as an HDD, and correctly named.

Selected, it booted with no problems, though it seemed a bit slow - just over 70 secs from Grub Menu to GUI login. 

**EDIT**2: The options were under Bios> Integrated Peripherals> USB Device Settings

Perhaps your Bios has a similar option.

Chao!, **bogan.**

---

### Post by plucky on 2012-03-13
> **NikTh said:**
> Hi ,
i agree with varunendra's opinion and suggestions (as others as well) . An other option you can try (worked for me at past) is to disable all other boot options from Bios. Leave only Usb. 
And i guess iso that you downloaded is the full image.. not alternate. ha ? **I think alternate works only with CD . (correct me if i am wrong)** .
Good luck

The Alternate Install iso will work from a pendrive.

Installed Xubuntu-Alternate 12.04 from a pendrive

Good Luck

---

### Post by NikTh on 2012-03-15
> **plucky said:**
> The Alternate Install iso will work from a pendrive.

Installed Xubuntu-Alternate 12.04 from a pendrive

Good Luck
Hi ,
Yes you have right. I confused with mini.iso. mini.iso not booting from usb. 
Thanks

---

### Post by Lucius Ferus on 2013-02-11
OK!
Thank's everybody!
I should have come back earlyer to mark the thread as solved.
There's almost one year i'm on Ubuntu now  and, USB Creator and USB boot aren't a problem anymore. But, i'll keep this thread for a good source of information. And be back to all these tips whenever needed.
Thank's for the support.

---

