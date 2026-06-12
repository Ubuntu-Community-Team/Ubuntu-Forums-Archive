---
title: "Ubuntu and old Socket A hardware compatibility?"
date: 2013-08-30
forum: New to Ubuntu
---

### Post by Steve M on 2013-08-30
Hi all, 

Last time I played with Ubuntu for some time was Hardy Heron. Which I gave up due to compatibility issues with PowerPC on old MAC's. A while back I had a short play on another set up with Ubuntu something or other. These can be seen under the user name sastusbulbas. For some reason this new Ubuntu 1 thing would not recognize my original account or associate my sastusbulbas user name with my email address? Probably me being daft somewhere? 

I am revisiting Ubuntu, 12.04 is what I was hoping to run, but I am having issues with this and the old PC I am tinkering with. Now as I have an IDE CD-Rom I cannot install newer Ubuntu directly, but have managed to install 11.10. But every time I do any updates the system hangs on rebooting. Just locks up with no mouse cursor moving and the LEDS on my memory freeze. I am currently writing this here on this system after another fresh install of 11.10 due to the 3rd failed 12.04 update attempt.

This system was still running with Windows 98, but the OS was a dog to use and did not support my screens 1920x1080 resolution. 

The old hardware I am using.

Asrock K7S41 MicroATX motherboard. Bios P1.20
AMD Athlon XP 2000+ CPU.
2GB (2x1) Corsair DDR 400 PC3500LL. (Was originally a 256mb single stick, but this was in my spares box)
BenQ CD drive. IDE.
Maxtor 20GB IDE HDD.
CTK 400W ATX  PSU.
D-Link wireless USB stick.

Any tips or pointers?

---

### Post by mörgæs on 2013-08-30
A good first step is installing Lubuntu 13.04. Ubuntu is too heavy.

---

### Post by Steve M on 2013-08-30
Thankyou, I will look into that, 

I notice this though, "*13.04 32 bit ISO require your CPU to have Physical Address Extensions, or PAE. "PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except several versions of the Pentium M, see here)." - If you have a NON-PAE CPU you can use 12.04 instead. *" Would this affect an AMD Athlon 2000+ Socket A cpu?

Will burn Lubuntu 13.04 and it's previous 12.04 try out. :)

---

### Post by kurt18947 on 2013-08-30
PAE is a concern, video is another.  I'm not sure how that vintage ATI reacts to modern Ubuntu distros.  I expect Xubuntu or Lubuntu may help if that's an issue, they're less graphically demanding.

---

### Post by mörgæs on 2013-08-30
> **kurt18947 said:**
> PAE is a concern

No, all AMD processors younger than about 15 years support PAE. There's a lot of unneeded worries about PAE going on in the fora - please don't propagate.

The video card could be a problem. @Steve, just try to install and tell us how it goes.

---

### Post by Steve M on 2013-08-31
On Ubuntu, It's reasonable with 11.10, hangs up with 12.04. That systems experience with Ubuntu 11.10 has been easier for web browsing and proper screen resolution than Windows 98 an XP were. But it's an old motherboard, that cannot load DVD's or newer Windows OS's. And I also found my Floppy is not working so cannot update bios at this time (tried in XP). A bootable USB won't allow me to update bios either, to utilize an old Athlon 3200+ that is sitting around somewhere.

Been busy since this morning so not had time to try the Lubuntu, though an initial install of Lubuntu 13.4 left me with a grey screen.

It only has on-board graphics.

I am not too worried about the overall performance with graphics n such, I may buy a few second hand items if I can sort out my floppy, plenty of old GPU's that would improve it a bit for the price of a few pints. I just thought I would make a basic web and document system for something to do, the Corsair memory with LED's was a bit of nostalgia.

It was also to get me used to Ubuntu a bit, as I plan to build a server using Amahi, with an old LGA775 system.

---

### Post by squakie on 2013-08-31
Please don't try getting ubutu itself working - do as has been recommended and use lubuntu or xubuntu only.  Why?  Ubuntu by default is going to use the unity desktop, and any on-board video on a motherboard that old will not run unity.  lubuntu and xubuntu use different desktop managers that aren't so hungry.

For your quick test with lubuntu, what are the specifics?  Where you booting from a CD?  Remember that the newer releases - I beleive 12.04 up - require a DVD, not a CD, to hold the image.  Was this a livecd image?  Did you get ANYTHING when you booted, or just immediately the gray screen?  It's important to know anything that may have showed on your screen before the gray screen.

---

### Post by mörgæs on 2013-08-31
> **squakie said:**
> Remember that the newer releases - I beleive 12.04 up - require a DVD, not a CD, to hold the image.

Only for Xubuntu and Ubuntu. Lubuntu fits to a CD.

If the standard 13.04 does not work then the alternate ISO is worth trying. The integrated SiS graphics might give problems, but still it's worth trying.

---

### Post by sudodus on 2013-08-31
I can boot a computer with an AMD Athlon XP from a USB pendrive. But it has another motherboard. USB might be an alternative for you if you want to boot an iso file that it too big for the CD drive.

Another alternative is to boot with a ***Plop*** CD boot manager, let it install a USB driver and continue booting from the USB drive.

If you can boot from USB (with or without Plop), you might also try the One Button Installer, that is designed to be easy to use and work also with old computers and small RAM. Start reading the documents at this link

[URL="http://drive.google.com/folderview?id=0BzX-18u3W1sQblBTYXNacGVsVkk&usp=sharing"]One button installer
[/URL]

---

### Post by kurt18947 on 2013-08-31
I think the ability to boot from a USB pendrive is a function of the BIOS not the processor.  There probably is a 'generational' correlation though, e.g. mobos with newer processors probably support more recent BIOS functions.

---

### Post by sudodus on 2013-08-31
> **kurt18947 said:**
> I think the ability to boot from a USB pendrive is a function of the BIOS not the processor.  There probably is a 'generational' correlation though, e.g. mobos with newer processors probably support more recent BIOS functions.

You are right, this is why I wrote that I have another motherboard. My experience is that computers from that era can boot from USB :-)

---

### Post by kurt18947 on 2013-09-01
There is one  peculiarity I've run into booting live images from USB.  One P.C. - Gigabyte M.B. AMD athlonII x2 processor Award modular BIOS ver.6.0.  It oftentimes won't boot a live USB drive unless that drive was formatted with Windows.  A quick format seems fine.  I've looked at USB drives that will boot and USB drives that won't boot.  I'm no expert in this stuff but I can't see any difference between them.  Formatting seems the same, flags seem the same.  The USB drives that won't boot on the subject P.C. will boot fine on a thinkpad or an older very similar AMD box.  The only difference I can see is the Award BIOS and chipset.

---

### Post by sudodus on 2013-09-01
Booting from USB was probably not intended, when the USB was designed, and particularly the early systems were not exactly the same. I guess it could be the BIOS or some hardware, that makes the difference.

I would be interested in the result, if you still have that computer and can clone an Ubuntu flavour iso file with dd and try it.

See [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

