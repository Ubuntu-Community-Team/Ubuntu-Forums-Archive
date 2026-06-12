---
title: "building raid server"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by asherwolf on 2011-10-03
I'm new to Ubuntu and computer building in general.  What I want to do is build a single tower raid server.  This will hold media files.  I want to have 6-8 3TB drives for a total of un-raided 18-24 TB storage.

I found a raid controller hardware whose cousin claims ubuntu compatibility.  Here are both their links:

[http://www.amazon.com/HighPoint-RocketRAID-2721-PCI-Express-Controller/dp/B0044CPEUQ](http://www.amazon.com/HighPoint-RocketRAID-2721-PCI-Express-Controller/dp/B0044CPEUQ)

[http://www.amazon.com/HighPoint-RocketRAID-2720-PCI-Express-Controller/dp/B0039KH0F6/ref=sr_1_2?s=electronics&ie=UTF8&qid=1317671436&sr=1-2](http://www.amazon.com/HighPoint-RocketRAID-2720-PCI-Express-Controller/dp/B0039KH0F6/ref=sr_1_2?s=electronics&ie=UTF8&qid=1317671436&sr=1-2)

I've also heard of Ubuntu's software raid as well.  My other question or concern is how to hook these hard drives up if I don't have a RAID card, and is there a power supply that'll power six to eight hard drives plus a dvd drive?

Thanks for any guidance,
Asher

---

### Post by seawolf167 on 2011-10-03
> **asherwolf said:**
> I've also heard of Ubuntu's software raid as well.  My other question or concern is how to hook these hard drives up if I don't have a RAID card

Take a look at these links for lots more information and come back with any more questions you may have

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

> **asherwolf said:**
> and is there a power supply that'll power six to eight hard drives plus a dvd drive?

Hard drives don't required a lot of power. Here is a [list]("http://www.wdc.com/en/products/products.aspx?id=120") of the WD Green Drives - you can find one you like then take a look at the specs, the power read/write usually won't be over 6W (versus a high-end graphics card which can suck 500W).

Because you want a lot of drives, you might want to look at a modular psu and a full size tower :P Either way, ensure you have a battery backup and efficient psu (not so much for the backup part but for the voltage regulation part)

---

### Post by dwasifar on 2011-10-03
I prefer Linux's software RAID over hardware RAID controllers.  The goal of giving RAID control to a dedicated piece of hardware was to take the load off the CPU, but that was years ago when CPUs were much lower-performance than today.  Modern CPUs can spare the horsepower to administer a software RAID without breaking a sweat.

The advantage of software RAID is that the generic hardware makes the devices transportable.  If you build a RAID on SATA drives, and you lose a motherboard, you can move your RAID drives to any other generic SATA motherboard and your RAID will work.  If you lose a hardware RAID controller, you're down until you replace the controller with something from the same maker (and sometimes that specific model).

---

### Post by Jagoly on 2011-10-04
But what sort of motherboard has 9 sata ports?

Depends what sort of Storage requirements your really have. If you're doing a RAID this big, you'll also want a small SSD for the OS. Most high end intel motherboards today have 4 SATA3 ports and 4 SATA2 ports. So, minus the SSD and DVD Drive (which I'm sure you have your own reasoning for needing one, I'm not sure why a file server would need one personally) you would have 6 ports for a software RAID, so with 3TB drives in RAID 6 you would have 12TB of storage. Plus all of that will fit in a few mid-tower cases too.

Remember any performance difference between hardware/software raid would be unnoticeable on 90% of peoples home networks. So, unless your house is interconnected with fiber, don't worry about performance.

Perhaps a more NAS style machine would be preferable to a full server? It all depends what you want to do with it.

EDIT: just noticed, bean #200 :-)

---

### Post by dwasifar on 2011-10-07
> **Jagoly said:**
> But what sort of motherboard has 9 sata ports?

Good point.  I think mine has only 8.  

He'd probably have to install a PCI-E SATA controller to get the extra ports.  He could get away with a cheaper PCI controller if he just needed one extra port for the optical drive, or for that matter he could use a PATA optical drive.

---

### Post by gbrowning on 2012-08-15
In addition to the additional ports a host card can be upgraded to the latest technology with less expense.  My motherboard only supports SATA2.  I have just installed a SAS/SATA3 controller.  Much less expensive than a new motherboard with 8 SATA ports.

---

### Post by sandyd on 2012-08-15
> **dwasifar said:**
> Good point.  I think mine has only 8.  

He'd probably have to install a PCI-E SATA controller to get the extra ports.  He could get away with a cheaper PCI controller if he just needed one extra port for the optical drive, or for that matter he could use a PATA optical drive.
Just a note - You will not be able to hw raid in this case, or fakeraid - you would have to use sw raid.

You can't raid together drives on seperate controllers.

---

