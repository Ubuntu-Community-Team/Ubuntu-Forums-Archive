---
title: "Help please - Ubuntu has killed my PC!"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by davidtrickett on 2008-05-15
I thought it would be a good idea to try Ubuntu - current OS was W2K SP4.
I successfully downloaded the CD & booted into Ubuntu from this - so far so good.

I then decided to install it, and since I didn't want to risk losing the data on my internal HDD's (trying to figure out what it is intending to do to the HDD's is not easy) I decided to take the "safe" option of installing it to an empty external USB HDD.

It seemed to install OK, but on trying to reboot all I get is "GRUB Stage1.5 Error 17" - or "Error 21".

Taking the USB drive out gives the same result - so it has done something to my boot drive. I am now left in the situation that the only way I can use my machine is to boot into Ubuntu from the CD.

I have had a look around this forum, but the only help I have been able to find is extremely complex, and assumes a knowledge of this OS far beyond that of someone who has tried it out today for the first time.

I suspect that the USB drive is faulty, but I really need to get Windows back so that I can at least retrieve full use of my PC.

Can anyone help please?

Thank you.

---

### Post by Joeb454 on 2008-05-15
Do you have a spare Windows CD to hand? Because you need to reinstall the Windows Bootloader :)

---

### Post by damis648 on 2008-05-15
You could do that, or you could remove the USB drive, boot from the disk, and install Ubuntu to the fixed disc and that should fix it. This would only be good if you wanted to install ubuntu, though.

---

### Post by davidtrickett on 2008-05-15
Ah - I did wonder if that was the case - I do have my Windows CD - is it just a matter of choosing the "repair" option? But I was a bit reluctant to try it since there is always the chance that it won't work & I have to wind up reinstalling the whole infernal thing!

---

### Post by dondad on 2008-05-15
> **Joeb454 said:**
> Do you have a spare Windows CD to hand? Because you need to reinstall the Windows Bootloader :)


If you have the Windows cd, boot from it, and select the repair console. type FIXMBR at the prompt and tell it to go ahead if it asks. After that, you should be able to remove the cd and it should boot into Windows.

---

### Post by davidtrickett on 2008-05-15
> **damis648 said:**
> You could do that, or you could remove the USB drive, boot from the disk, and install Ubuntu to the fixed disc and that should fix it. This would only be good if you wanted to install ubuntu, though.

I am happy to install Ubuntu - that was the whole idea! But I thought it safer to avoid my existing HDD's since although I do have a goodly amount of free space it seemed to want to install onto a drive which was already in use.

---

### Post by indytim on 2008-05-15
My suggestion is to exercise the LiveCD for Ubuntu and get your hands safely wet a little bit.  Also haunt around the forums (this one is really good for the newer Linux members).  When you're comfortable, download and burn a copy of GParted Live.  Pre-format some unused space on your hd and go ahead and install it.

As a point of reference, I have Win2k SP4 and 4 different Linux ops installed on my primary HD.  Works quite well.

Welcome aboard and good luck.

IndyTim

---

### Post by Joeb454 on 2008-05-15
> **indytim said:**
> My suggestion is to exercise the LiveCD for Ubuntu and get your hands safely wet a little bit.  Also haunt around the forums (this one is really good for the newer Linux members).  When you're comfortable, download and burn a copy of GParted Live.  Pre-format some unused space on your hd and go ahead and install it.

As a point of reference, I have Win2k SP4 and 4 different Linux ops installed on my primary HD.  Works quite well.

Welcome aboard and good luck.

IndyTim

Actually I used a virtual machine for a while before I installed :) Though I recommend this if you have a semi-decent PC at least. It works quicker than a Live-CD if you can do it :)

---

### Post by Stringthing on 2008-05-15
Getting back to the original post, doesn't booting from an external USB drive have to be supported in your computer's BIOS?  If you are using older hardware that could be what Grub was complaining about.

Just thought I'd throw that in there.

---

### Post by Joeb454 on 2008-05-15
Sorry yes, you are correct, some older hardware doesn't support booting from USB, though I'd take a guess that most PC's in the last 2 (possibly 3) years will support it :)

---

### Post by Miljet on 2008-05-15
I would guess that if the Windows system is Win2K, the computer is more that a couple of years old.

---

### Post by UnWarierMage224 on 2008-05-15
Just to put in my $.02, what about using WUBI? 
Otherwise, as others have said, GParted is the way to go. 

-'Mage

---

### Post by mackyman on 2008-05-16
> It seemed to install OK, but on trying to reboot all I get is "GRUB Stage1.5 Error 17" - or "Error 21".

Quoted from the GNU/GRUB manual
> 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Solotion:
[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible]("http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible")

> Error 21 : Selected disk does not exist

This error is returned if the device part of a device- or full file name refers 
to a disk or BIOS device that is not present or not recognized by the BIOS in the system.


Culd it be so that you get a error 17 when the hdd is plugged in and 21 when the usb hdd is plugged off? That sound fairly possible in my ears.

---

