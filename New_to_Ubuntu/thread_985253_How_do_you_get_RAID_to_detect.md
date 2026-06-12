---
title: "How do you get RAID to detect?"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by pancakelizard on 2008-11-17
I have a RAID 5 with the following card:
Rosewill RC-217 SATA II 4 Port RAID 0/1/0+1/5/JBOD PCI RAID Card
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816132017](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132017)

It's a software array(I'm pretty sure as it needs a java interface to detect the array). 

It was in a Windows XP system and I'm wanting to move it to a Ubuntu 8.04 LTS environment (the 8.10 install kept asking me to insert the CD and locked the drive at about 86% of the installation). 

The deal is, I can't afford to lose the information on the array so I don't want to reinitialize anything. What is the best way to get Ubuntu to see the array without losing any information?

---

### Post by psusi on 2008-11-17
It looks like a silicon image based fakeraid controller.  When you boot from the livecd, does it see each individual disk?  You might want to read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).

---

### Post by Coreigh on 2008-11-17
Start the system up where it works, back up the data (CDs DVDs external disk whatever) Install Ubuntu and build a new array. Restore the data.

A software array on a Windows system probably used some type of proprietary controller software built for Windows. You might be lucky enough to find a way to access it from Ubuntu without re-initializing but its a long shot.

You should always have back-ups of your data anyway. What is the array had failed even if you weren't changing OS'es?

---

### Post by pancakelizard on 2008-11-17
> **psusi said:**
> It looks like a silicon image based fakeraid controller.  When you boot from the livecd, does it see each individual disk?  You might want to read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).

It does.

And Coreigh I was afraid you would say that but I do have a external HDD I can back it all up to.

The main reason all of this also started was one machine whenever it performed a cold boot, came back saying the array was missing and then after repairing it said the OS was not found.

Afterwards the array and the drives attached to it could not be found. So if I have to wipe out the data, I want to get a good RAID card for my computer.

This is the motherboard I have:
TYAN S5220AG2NR LGA 775 Intel Q35 ATX Server Motherboard
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813151169](http://www.newegg.com/Product/Product.aspx?Item=N82E16813151169)

I'm thinking of just using the onboard RAID but I'm kinda iffy on that. Thoughts?

---

### Post by psusi on 2008-11-17
> **Coreigh said:**
> Start the system up where it works, back up the data (CDs DVDs external disk whatever) Install Ubuntu and build a new array. Restore the data.

A software array on a Windows system probably used some type of proprietary controller software built for Windows. You might be lucky enough to find a way to access it from Ubuntu without re-initializing but its a long shot.

You should always have back-ups of your data anyway. What is the array had failed even if you weren't changing OS'es?

No, the raid array is created by the bios so you can't recreate it in Linux.

> **pancakelizard said:**
> I'm thinking of just using the onboard RAID but I'm kinda iffy on that. Thoughts?

Shouldn't really be any different than using that card, unless your onboard one doesn't have enough ports or something.

---

### Post by pancakelizard on 2008-11-17
Then I would need a hardware RAID, correct? If I wanted to go from Linux to Windows on a separate HDD but still have the array viewable and write able regardless of the OS.

Any recommendations on a RAID card?
I'd prefer a PCI-Express 8x or lower interface, PCI if need be and to be able to connect up to 6 drives.

---

### Post by psusi on 2008-11-17
No, either the on board controller or the card you posted should work just fine.

---

