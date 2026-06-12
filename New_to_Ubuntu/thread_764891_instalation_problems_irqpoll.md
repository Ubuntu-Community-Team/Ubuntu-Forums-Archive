---
title: "instalation problems irqpoll"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by AMIRITE on 2008-04-24
so at this stage i've tried using three different iso's to install ubuntu on my desktop pc

7.1 live and 8.04 live and alternate.

with the two live cd installers i get an error message that goes something like this
"Warning: unrecognised partition table for drive 80. please rebuild it using a microsoft compatable fdisk tool.
(err=114) current cc/h/s=16383/16/63"

so i did some googling and from what i could gather fdisk was basically a formatting tool, so i used partition magic to format my secondary drive as ext3, then i turned off my pc and swapped my primary drive (with windows installed) for my secondary formatted drive.
then i tried installing using the 8.04 alternate cd it booted to the language select and option menu but when i tried installing i got a new error message which reads:
"device not acepting
39.2073irq20 nobody cared (try booting with the "irq poll" option"

FYI my pc specs are as follows:
2.13 gHtz core 2 duo
2 gig ram
asus p5w dh deluxe motherboard
my drives are seagate and samsung

anyone able to give me a hand with this?
it'd be much appreciated

oh and i've also tried installing ubuntu 8.04 through windows, it installed but wouldn't boot

---

### Post by skroops on 2008-04-24
The warning: unrecognised partition is not coming from the ubuntu cds.  I don't know if thats a BIOS error or a windows error, but I'd guess windows because it suggests using microsoft compatible-tools.

Check your BIOS to make sure that your cd-rom drive is set to boot before your hard disk, because it looks like the ubuntu cd never got a chance to start in the first case.

Are you running SATA or IDE hard drives (IDE has ribbon-like cables, sata has thinner cables).  If it is IDE you will have to adjust the jumpers on the drives in order to swap them like that.  You shouldn't have to do that, and I'd suggest putting them back in the original order and then trying to install again with your cd-rom drive set to boot first in the BIOS.

---

### Post by AMIRITE on 2008-04-24
hi skroops.
TY for the reply

they're sata drives
the boot order is set to cd first, i'm able to get to the options menu on the cd's, its when i try and boot to linux from the cd or install that i get these problems.

the cd's themselves seem fine, i can run the live cd fine on my laptop and booting to linux from cd works perfectly (but for various reasons i can't actually install on my laptop).

---

### Post by skroops on 2008-04-24
Well I'm really not very familiar with those errors.  I don't want to waste your time but if no one else is responding, I would suggest removing your windows drive altogether and checking to see if you can get it running.  Then you could atleast establish that there's no major problems with your hardware.

---

### Post by kansasnoob on 2008-04-24
I had similar problems. (sorry I didn't keep any record of the specific codes displayed when I was attempting to dual boot with two drives) Anyway I finally had to completely disconnect the windows drive and set the drive I was using for Ubuntu to master as described here:

[http://www.cypherhackz.net/archives/2007/12/25/how-to-dual-boot-ubuntu-and-winxp-using-two-hard-drives/](http://www.cypherhackz.net/archives/2007/12/25/how-to-dual-boot-ubuntu-and-winxp-using-two-hard-drives/)

It worked!

---

### Post by AMIRITE on 2008-04-24
thanks kansasnoob

i tried that but i'm still getting the same error message

i did some searches for irq 20.
and basically found out that my irq 20 is a 
"IRQ 20	Intel(R) 82801G (ICH7 Family) USB2 Enhanced Host Controller - 27CC"



the question is how is this preventing me from booting to linux?

all help appreciated

---

### Post by spiderbatdad on 2008-04-24
irqpoll is a parameter to can append to the kernel line from the boot/install options screen, usually by pressing F6. Go to the end of the kernel line and delete --quiet splash. Add irqpoll. Other possible parameters, depending on dmesg include: lapic pci=routeirq, or noapic nolapic, or several dozen others. I have found those listed here to be the most effective in solving hardware resolution problems during boot. If installation is successful, the parameters will need to be added to the kernel line in /boot/grub/menu.lst after installation.

---

### Post by AMIRITE on 2008-04-24
hi spiderbatdad

em
what?

sorry but i haven't a clue of what any of that actually means.

i don't suppose you could give me step by step instructions for what to do?

---

### Post by spiderbatdad on 2008-04-24
sure. I can try. Do you get an options screen just prior to boot. Near the bottom it should say something to the effect of press F6 to enter special boot parameters.

---

### Post by AMIRITE on 2008-04-24
i do
once i press f6 then a command line type thing appears at the bottom of the screen

---

### Post by spiderbatdad on 2008-04-24
ok. use the arrow key to move to the end of that line and the backspace key to delete the commands --quiet splash. Type in lapic pci=routeirq and hit enter.
If that does not work, repeat again. This time use only irqpoll
Finally, if you have still had no luck, try noapic nolapic

One of those methods should work for you. You should then upload ```
dmesg
```run in the terminal as a zip file to fine tune the boot process...but thats later. First we'll try to get you booted up and installed.

---

### Post by yaztromo on 2008-04-24
Some motherboards need the irqpoll option in the kernel parameters to boot the ubuntu kernel successfully. My motherboard is one of them.

When your CD boots and you see the install menu press F6 and edit the line to include the word irqpoll before the "--". Should get you going.

Once you have installed you will then need to edit your /boot/grub/menu.lst to add the irqpoll option in permanently.

---

### Post by kansasnoob on 2008-04-24
In my limited experience if the problem is with the Live Cd you're more likely to stop dead at some point in the process or have your installation drive just "spin-out".

What you describe really sounds like there is something on your hard drive that GParted (Ubuntu's partitioner tool) refuses to mess with.

Have you let your computer try to just boot into that hard drive?

I think something is "locked" to that drive, which is quite odd, or it's a bad drive.

---

### Post by AMIRITE on 2008-04-24
alright

thanks for the tips guys.

it'll be tomorrow before i try any of this, so i'll post later with good news or more questions.

:-)

---

### Post by AMIRITE on 2008-04-25
so my instalation problems are all sorted out. :-)

booting was a bit of an issue for a while but i think i managed to edit the grub properly so i can use ubuntu reliably now.

one last question though

at the moment it takes ubuntu about five minutes to load, this is a hell of a lot longer than any other os i've used on this machine including vista

is there any way (read easy way) to make booting more efficient?

anyway
thanks for getting me this far at least guys, 
its much appreciated.

---

### Post by spiderbatdad on 2008-04-25
Shouldn't take much more than 30 seconds or so.
Maybe turn off start up programs you don't need in System>>Preferences>>Sessions, and upload your dmesg (run in a terminal) as an archive. Just copy and paste it into a text file, then right click on the file and select 'archive.' Use the manage attachment tool below to upload the archive.

---

### Post by AMIRITE on 2008-04-25
alright
here's the dmesg.

---

### Post by spiderbatdad on 2008-04-25
Don't see anything I've had experience fixing. Some areas look bothersome though, ```
 ata8.00: Drive reports diagnostics failure. This may indicate a drive
[   34.409467] ata8.00: fault or invalid emulation. Contact drive vendor for information.
[   34.409471] ata8.00: device is on DMA blacklist, disabling DMA
[   34.409820] ata8.00: configured for PIO4
[   34.409916] scsi 6:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   34.410030] scsi 7:0:0:0: Direct-Access     ATA      Config  Disk     RGL1 PQ: 0 ANSI: 5
[   34.416220] Driver 'sr' needs updating - please use bus_type methods
[   34.423044] Driver 'sd' needs updating - please use bus_type methods
```

Also this is obviously using time:
```
 ata8.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   64.795160] ata8.00: revalidation failed (errno=-5)
[   64.795162] ata8: failed to recover some devices, retrying in 5 secs
[   69.795041] ata8: soft resetting link
[   70.137155] ata8.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   70.137157] ata8.00: revalidation failed (errno=-5)
[   70.137160] ata8: failed to recover some devices, retrying in 5 secs
[   75.135914] ata8: soft resetting link
[   75.478097] ata8.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   75.478099] ata8.00: revalidation failed (errno=-5)
[   75.478102] ata8.00: disabled
[   75.979587] ata8: EH complete
```

Not sure if some specific parameters will eliminate this problem, but I suspect they would.

You might consider browsing over to Launchpad bugs and reporting a long boot time on Hardy. I believe you can upload your dmesg there as a second post using the "comment or add to post" (or whatever it is) at the bottom of the post window. You should find results there, if not a ready solution already posted.

---

### Post by AMIRITE on 2008-04-25
alright
thanks for all the help

---

