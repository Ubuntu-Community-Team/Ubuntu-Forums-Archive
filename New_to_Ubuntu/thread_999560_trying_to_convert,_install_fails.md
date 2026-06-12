---
title: "trying to convert, install fails"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Vlad_666 on 2008-12-02
I've been a windows user forever, and always thought about switching to some form of linux. After reading and reading, and talking with current ubuntu users, I've decided to switch.

I've downloaded 8.10, burned the image and popped it in my desktop (specs below). I've tried numerous times, but the install always fails with the same message which ends with "(initramfs)". No matter what I do, all appears well (logo, load bar going back and forth), then suddenly a black screen that appears to be awaiting commands from me.

I've even ran a nuke-n-boot in order for it to truly be a "fresh" start.....same thing, an empty shell.

 HOWEVER, just for kicks, I managed to dual boot my dell desktop without a hitch...go figure.

specs on the pc in queston are as follows:
ASUS p5b-deluxe
Intel core 2 6600
4G OCZ gold 800mhz
maxtor 7y250p0
some kinda stock dell vga card (although I'm about to throw my ancient nvidia 5500 in to see if that helps)
Lite-on dvd rw 


so, any thoughts?

---

### Post by wilbbe01 on 2008-12-02
Did you try installing from the alternate disk at all?

---

### Post by Vlad_666 on 2008-12-02
actually trying that now....we'll see how it goes

---

### Post by nhasian on 2008-12-02
error initializing the ram filesystem?  have you run the memory test from the liveCD?

---

### Post by Vlad_666 on 2008-12-02
Ok, so here is what I get -

LiveCD: always take me to a command line no matter what I do (I literally tried everything available on the menu, I'm talkin' probably 30 reboots)

Alternate CD: get's to step 3 (mount disk) and I get notified that my disk could not be mounted because it is probaby not in the drive....but it is. (chalk up another 10+ reboots for this with a series of other boot options)

 I'm begining to think that monty python wrote the alternate CD ( ...you must coninue on to thrrree, but shall not, under any circumstance prrrrroceed on to four. throw the holy hand grenade only after counting to thrrrree...)



Do you think I could have a bad stick of RAM?

---

### Post by bumanie on 2008-12-02
There is an option to do a memtest+86 from the live cd - that will indicate whether something is wrong with your ram or not. You need to run it for a few hours generally.

---

### Post by Vlad_666 on 2008-12-02
will do. I'll post an update in several hours! thanks for all your help, you really don't know how much I appreciate it! I can't wait to be free from the evil grips Bill G! :lolflag:

---

### Post by Vlad_666 on 2008-12-02
memtest86 passed with zero errors. currently running bitfade test, back in 90 min or so!

---

### Post by JC Cheloven on 2008-12-02
Vlad, you used the same cd for installing at your dell ?
If so, the cd should be correct, and you'd better disregarding my post. 

But we see too many times that a bunch of strange problems may be caused by a bad recorded cd. So if you didn't use that cd on another computer, try to do it. If something goes also wrong, apply the "thumb rules": 1º checksum your download. 2º burn again the cd at a lower speed.

---

### Post by Vlad_666 on 2008-12-02
you know, now that you mention it, I didn't use a physical cd for the install on the dell. I mounted the image to a virtual drive and installed from there, within windows. Then I burned that same image to a disk for my custom box.  I'll burn a new one at a slower speed, on a different brand of disk and see if that works. thanks!

---

### Post by LowSky on 2008-12-02
I knwo the problem and it going to annoy the crap out of you. From what you explain you know all the hardware of your machine, I assume you buit it yourself.

Is the DVD-rw drive SATA or PATA. if PATA (AKA: IDE) make sure you have the right cable, most people assume  cable is cable but for some reason Ubutnu (the last 3 versions requires the drive to use a 80 pin cable. it will feel smooth compared to a 40 pin which feels rougher, whilke most people use what ever is laying around like an older 40 PIN cable which screw things up and you end up with the busybox error. if you dont know and need to order a new cable make sure it can support speeds of up to 100/133, 40 PIN only goes to 66


So long boring story later, switch out the 40 pin cable for an 80 pin cable and the error should go away

---

### Post by hurstja on 2008-12-02
I had similar problem installing opensuse on a custom machine and it turned out to be my dvd burner.  Good luck.

---

### Post by Vlad_666 on 2008-12-02
the drive is an IDE drive, and I'm already using the 80 pin cable....I'm completely at a loss here.


I've given up on the alternate CD, 8 disks later, it still refuses to mount. The liveCD, however is giving me new error (irq 17 I believe) and telling me to try booting up with the irq polling option, but there isn't one that seems readily available (not in F6, nor in F4). 
After making this suggestion, it begins counting in a format like this:

[42:947595] random stuff here: status {drdy}
[42:948524} more stuff here: what looks like a mac address here(frozen)
[44:948342] same thing here: more hexadecimal stuff (timeout)

so on and so forth with apparently no end (I let it run for quit a while doing this)

---

### Post by Vlad_666 on 2008-12-03
Fixed!

here is how: 

I nuked the HDD. while that was being erased, I used the dual boot dell to make a bootable usb drive with my 4G thumb drive. A few BIOS settings (and bald spots on my head) later, and I am in business!!

 Thanks to all who offered their knowledge, experience, and time to helping me resolve this issue!

---

### Post by bumanie on 2008-12-03
It may be useful to do a [md5checksum]("https://help.ubuntu.com/community/HowToMD5SUM") on your downloaded .iso Also double check that you are burning the .iso as an image and not accidentally burning it as a data disc.

---

