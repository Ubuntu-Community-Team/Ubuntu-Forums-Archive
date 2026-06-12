---
title: "Does Ubuntu 14.04 Live DVD contain SCSI drivers?"
date: 2014-09-17
forum: New to Ubuntu
---

### Post by Michael_McKenney on 2014-09-17
Does Ubuntu 14.04 Live DVD contain SCSI drivers?  I want to test Ubuntu on my Tyan Thunder K8WE board.  I have a SCSI controller with three tape drives.  I want to get the drivers for the SCSI controller and tape drivers into live DVD boot.  How can I do it?

---

### Post by Bucky Ball on 2014-09-17
Boot a live DVD, plug 'em in and switch 'em on. As far as I know, yes, SCSI is included. If not, you would be able to install required software, but you may have trouble manually installing drivers in a live boot. If you can, all changes will be lost when you shutdown or restart.

---

### Post by Michael_McKenney on 2014-09-17
It is more of a test to see how it runs on the box.  I am used to reconfiguring a live boot environment.

---

### Post by Bucky Ball on 2014-09-17
As I say, boot a live DVD and test it out. See if your external devices get picked up when you plug them in. You could plug in, open a terminal and:

```
dmesg
```

See if it picked anything up, should be at the end of the output, and it will possibly also mention whether it loaded any drivers 'automagically'. If it identifies the device(s) that is a good sign. 

It is not like Windows. The drivers for many devices are already there in the Ubuntu kernel and don't need to be manually installed.

---

### Post by Michael_McKenney on 2014-09-17
The tape drives are internal connected to the SCSI controller.   I don't use external devices.

---

### Post by Michael_McKenney on 2014-09-17
How do I see if the SCSI controller and tape drives were found?

---

### Post by Bucky Ball on 2014-09-17
If you open a file manager, are they there? I've just been looking [HERE]("https://duckduckgo.com/?q=scsi+controller+ubuntu") and there is not much mention of them. 

Perhaps if you do a search for your exact model and append 'ubuntu' to it you might dig something up.

---

### Post by Michael_McKenney on 2014-09-17
SCSI devices are tape drives.  No RAID configuration.  They are backup drives not hard drives.   Two are Exabyte VXA-2 tape drives and other is HP LTO 3 tape drive.   My hard drive is SATA based single drive.

---

### Post by Bucky Ball on 2014-09-17
Yep, realised that and edited my last post just before. Have a look. Have a search for your exact model and append 'ubuntu'. ;)

---

### Post by Michael_McKenney on 2014-09-17
I found how to add the SCSI controller and tape drives to Ubuntu.  I guess the Live CD will be for stability of Ubuntu on the hardware.  I would like to see the SCSI controller on live boot.  I don't think the tape drives will show up.  Will Ubuntu 14.04 run stable on the Tyan Thunder K8WE board, AMD Opterons, and SCSI controller.

---

### Post by Bucky Ball on 2014-09-17
> **Michael_McKenney said:**
> I found how to add the SCSI controller and tape drives to Ubuntu.  

Please share. I don't see any reason why Ubuntu AMD64 will not be stable on your workstation. From what I can gather it is [this]("http://tyan.com/archive/products/html/thunderk8we.html") motherboard in a tower? A regular desktop with a quad core processor and a single hard drive?

If it is booting to a 'Try Ubuntu' live desktop from the DVD, then it is working on your machine ...

PS: Unsure what the thinking is behind running from a live DVD and not a hard drive install. The hard drive install is more stable and persistent. And faster ... :-k

---

### Post by Bucky Ball on 2014-09-17
Whether the Tyan board works with Ubuntu is the same question you are asking here:

[http://ubuntuforums.org/showthread.php?t=2244585](http://ubuntuforums.org/showthread.php?t=2244585)

Please mark this thread as solved as you have resolved installing SCSI drivers and refer to your other thread as the question of whether the Tyan board works with Ubuntu and SCSI is covered there and is off-topic here. Thanks.

---

### Post by Michael_McKenney on 2014-09-17
Cooler Master Stacker 11 bay tower old the massive server board.  Tyan Thunder K8WE is a server board with a pair of AMD Opteron 280 dual core 2.4 GHz server CPUs.  The server board was very powerful for its day.  Memory bandwidth in its configuration is 55-60 GB/s.  It has all 64-bit hardware installed including the PCI-X 64/133 SCSI controller from Adaptec.  

[http://www.michaelmckenney.com/Computers/K8WE/Pictures/new.jpg](http://www.michaelmckenney.com/Computers/K8WE/Pictures/new.jpg)

Center chassis is it.  I no longer have the hot swap SCSI drives in it.  

[http://www.michaelmckenney.com/Computers/K8WE/Computer_Upgrade/](http://www.michaelmckenney.com/Computers/K8WE/Computer_Upgrade/)

Has some old information and pictures about the board.  

[http://www.bacula.org/5.0.x-manuals/en/main/main/Supported_Tape_Drives.html](http://www.bacula.org/5.0.x-manuals/en/main/main/Supported_Tape_Drives.html)

The tape drives are supported in Bacula.

---

### Post by Bucky Ball on 2014-09-17
Please read post #12. Thanks.

---

### Post by Michael_McKenney on 2014-09-17
[[COLOR=#dd4814]http://ubuntuforums.org/showthread.p...7#post13123657[/COLOR]]("http://ubuntuforums.org/showthread.p...7#post13123657")  Link is broken.  How can I search for it?

---

### Post by QIII on 2014-09-17
As Bucky Ball indicated, your original question in this thread was solved and you have another thread dealing with your board.  Please deal with that issue there.

Things get confusing when threads ramble from subject to subject.

Thanks.

Closed.

---

