---
title: "boot with cdrom"
date: 2022-09-22
forum: New to Ubuntu
---

### Post by mevdor7 on 2022-09-22
hi all - I'm trying to put Ubuntu 14.04.6 LTS Trusty Tahr on an old pentium 3 450mhz 384ram (I know it wil b slow). the image is over a gig and my cdrom drive cant read DVDs. I cant boot normally from the BIOS as its an old pc, is there a boot disc I can use to enable usb and install off it? thanks :p

---

### Post by guiverc on 2022-09-22
> **mevdor7 said:**
> hi all - I'm trying to put Ubuntu 14.04.6 LTS Trusty Tahr on an old pentium 3 450mhz 384ram (I know it wil b slow). the image is over a gig and my cdrom drive cant read DVDs. I cant boot normally from the BIOS as its an old pc, is there a boot disc I can use to enable usb and install off it? thanks :p

Firstly Ubuntu 14.04 LTS reached end of standard support **five** years after it was released in 2014-April.

Refer [https://fridge.ubuntu.com/2019/05/02/ubuntu-14-04-trusty-tahr-reached-end-of-life-on-april-25-2019-esm-available/](https://fridge.ubuntu.com/2019/05/02/ubuntu-14-04-trusty-tahr-reached-end-of-life-on-april-25-2019-esm-available/)

> This is a follow-up to the Extended Support warning sent a month ago to  confirm that as of April 25, 2019, Ubuntu 14.04 LTS basic support has  ended.  No more package updates[1] will be accepted to the 14.04 primary  archive, and any subsequent support will be done via Extended Security  Maintenance. 

I have no idea what you mean by "*I cant boot normally from the BIOS as its an old pc*" as I still had old pentium II/III systems until somewhat recently (*recycled less than two years ago*) and the boxes I used all had BIOS that was configurable & allowed booting from many devices (*not USB as I recall; I recall doing that only on pentium 4* *but the boot restriction is BIOS/firmware limited thus box specific, unrelated to the CPU*). The only restriction was related to instruction set of the processor, and thus inability to install/execute specific processors that required more modern instruction sets.

I do recall booting from old floppy disks (*devices that old usually had them, and the firmware accepted boot from floppies*) and then the floppy itself (*3.5" but that doesn't matter*) passed control to another media, but I don't recall booting to USB media but I never tried (USBs were 1.1 as I recall; ie. ultra-slow). Either way that's not where I'd head as I'd likely just use *netboot* and manually deal with any issues related the EOSS status of the release (*the media will be very old & thus certificates expired so network problems can be expected depending on where you live in the world* *[ie. luck]*)


FYI:  I did use pentium 4, pentium M, pentium D for QA testing up to 19.04 (*alpha as 19.04 wasn't released in i386 with only some alpha ISOs produced*; *released products up to 18.10*); the RAM size you mention limits you to using a *di* installer only which wasn't the default installer for Ubuntu 14.04 LTS.

---

### Post by Irihapeti on 2022-09-22
I wonder if it would be worth looking at something like Alpine Linux or Tiny Core, or possibly a Puppy Linux variant. These are specifically built for machines with restricted RAM, and are small enough to get onto a CD.

---

### Post by Impavidus on 2022-09-22
It will not only be slow and insecure, but also incapabe of running modern applications required for modern file formats.

I assume you mean that you can't boot from usb. There's a way around that. Never tried it myself.
[https://help.ubuntu.com/community/Installation/FromUSBStick/bootUSB](https://help.ubuntu.com/community/Installation/FromUSBStick/bootUSB)
[https://www.plop.at/en/bootmanager/intro.html](https://www.plop.at/en/bootmanager/intro.html)

---

### Post by yancek on 2022-09-22
Does this PC have any operating system on it with Grub or Grub2?  If so, you can either extract the iso files and copy them to a partition on the drive and put an entry in the menu.lst or grub .conf file or the grub.cfg menu of Grub2.  If you have no Linux on the system you will need another option.

---

### Post by ActionParsnip on 2022-09-22
There is a floppy disk image that can then boot USB
[https://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](https://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)

---

### Post by MAFoElffen on 2022-09-24
The Pentium III was 32bit. As I remember, Lubuntu 14.04 32bit was under 700MB.

Modern 32bit OS'es are limited these days...
[https://www.makeuseof.com/linux-distros-with-32-bit-support/](https://www.makeuseof.com/linux-distros-with-32-bit-support/)

Debain 11.5.0 (Bullseye) 32bit Net Install ISO is only 471MB...
[https://cdimage.debian.org/debian-cd/current/i386/iso-cd/](https://cdimage.debian.org/debian-cd/current/i386/iso-cd/)

---

### Post by ActionParsnip on 2022-09-24
If you are using a P3 you may want to use something lighter like Puppy Linux or Debian

---

### Post by guiverc on 2022-09-24
I'll add a bit more..

I can't remember using Lubuntu on a pentium II/III, even though I only recycled my last II/III boxes earlier this year. I also recall using it on boxes with only 384MB of RAM (*I still have that box; though I might have increased RAM to its maximum of 512MB*) and thus have no idea what releases I'm thinking of.  Either way the CPU not being able to install/execute modern apps can be annoying.

If not using Ubuntu, I'd for sure use Debian.   The same boxes I QA test (*Quality Assurance*) test Ubuntu (*and flavors like Lubuntu*) I also use to QA-test Debian on, and on the 25+ boxes I've done this on, I had only one box were Lubuntu out-performed Debian in an significant way; and whilst I was interested in why, the box was just so underpowered it was painful to use in either OS (esp. Debian) I was unwilling (*or had too little patience*) to work out why  (*if I was forced to use that box; I'd not have used LXDE or LXQt using Debian or Ubuntu*).  Puppy maybe a good choice too, but my experience with Puppy is far more limited.

I'll add a link to learn more details about Lubuntu Alternate ISOs - [https://help.ubuntu.com/community/LXDE-lubuntu/Alternate_ISO](https://help.ubuntu.com/community/LXDE-lubuntu/Alternate_ISO)

I was not involved in Lubuntu before the *cosmic* (18.10) cycle, thus we've never produced an *debian installer* ISO whilst I've been involved, but the purpose of the Alternate ISO was for machines with very limited RAM. I'll quote part of that wiki page.

> Alternate ISOs are for low-RAM PCs. Computers with less than 700 MB of RAM are considered low-RAM computers.

Installs will fail on a *live* system when insufficient RAM is left for the installer; thus the ALTERNATE ISO was produced using the *Debian Installer* which works in a non-live system.   Also useful; on that page is where you'll note I added back the link to phillw's page; but do please take note of the warning

> please note as these 3rd party sites are outside of  Canonical/Ubuntu/Lubuntu control, all security is the responsibility of  the user.

If you want to use ISOs from Ubuntu; I'd likely install a server image then add `lubuntu-desktop` as the page I've provided suggests.

All Lubuntu QA-testing I've done for 18.04.1 & laterwere on boxes with 1GB of RAM (*i386*) or more.

---

### Post by ajgreeny on 2022-09-24
I will also add my thoughts and suggest Debian which I have installed on an old 32 bit netbook.
I do not use a full DE but simply run openbox with lxpanel added.
It is, however, frustratingly slow running but just about usable for simple browsing and emailing; anything needing high graphics resources is a definite non-starter.

---

