---
title: "Need help using SD card to expand SSD capacity."
date: 2017-07-25
forum: New to Ubuntu
---

### Post by radioactive.exe on 2017-07-25
Long story short I am looking to see if its possible to expand the capacity of my 16gb ssd via the use of an SD card, one that I intend to stay inside the computer permanently. 

The best I could gather from google is that there's no simple way of doing this like the way Windows handles partitions. However I did see something about mounting the SD card as a link to specific directories, potentially the Home folder.

However since I don't really understand exactly how that would work. My goal is to essentially make the SD Card and extension of the SSD, so let's say I have 20 gb of storage used, the SSD would be full but all the excess data (let's say 4 gb) would be automatically placed onto the SD card. 

I'm well aware that could sort of set up would cause issues with something happened with the SD cards so in addition, if the above is possible, I was wondering if all non essential system files would be able to prioritize the SD card over the SSD.

--Further Background--
The computer I am using for this is a Toshiba Chromebook 2 (intel celeron) with a non-upgradable SSD (16gb) and I wish to add on storage via a 64 gb SanDisk SD Card. 

Any help regarding this would be greatly appreciated.

---

### Post by QIII on 2017-07-26
Hello!

You can mount an SD easily enough -- even formatted as NTFS -- and keep data on it.

However, SD cards are terribly, terribly slow.  They also suffer very quickly from "wear out".  They are not really reliable enough for what you have in mind.  They were really designed to be used in devices like cameras for a few rounds of writing/reading and then thrown away when they wore out.  If you have a USB 3 port, a USB 3 thumb drive would be a much better option and it can be mounted automatically when it is plugged in.  Although the read/write rate is not as fast as an SSD, the theoretical transfer rate of a USB 3 is very close to SATA III throughput.  A thumb drive will last a lot longer in typical usage than an SD card.

I don't even use SD cards on my SBCs.  My Raspberry Pi 3 has been set up to boot from a USB thumb drive without an SD card even inserted.  My Odroid XU4 ran (unfortunately, I wrecked it while doing some experiments) booted from an SD and immediately turned control over to an HDD connected via USB 3, as did an older Pi 2 Model B.

The SD card would probably be so slow you would want to shake your machine.

That all being said, if you want to go ahead the SD can likely be mounted at startup via your fstab and a symbolic (sometimes called soft) link added to your /home.  We can help you with that if you are interested.

---

### Post by HermanAB on 2017-07-26
Howdy,

There are multiple answers to your question.  Firstly, yes, you can do that.

SD cards come with various speed ratings.  I recommend getting a Number 6, which AFAIK is the fastest.  A cheap SD card with no speed number will be terribly slow when writing, but could be fine for a part of the FS tree that is mostly read only.

The most complicated way to do it is to extend a single file system over multiple devices using LVM, or BTRFS.

The simplest method is to move part of the file system tree from the SSD to the SD card.

---

### Post by radioactive.exe on 2017-07-28
Thanks.

After thinking this over, I'm probably just going to use the SD card as additional storage rather than trying to extend the main storage. 

After all given that that Linux as a whole is more space efficient (at least when installing from repositories), I shouldn't really have issues.

Worst case scenario I can always try moving the more bloated parts (documents,photos,music, etc.) of the file system tree over to the SD card.

---

### Post by kurt18947 on 2017-07-29
I think using an SD card for storage as you mention should work. I've done installs in smallish partitions - 15-18 GB. and they were adequate for short term experimental use. Not a lot of room for storage but your SD card should fix that. My machines have 4 GB+ RAM installed and I don't use hibernation so I usually don't create a swap partition. If I want swap I create a swap file. How much RAM does your machine have? The lower the RAM the more likely swap will be required.

---

### Post by leunam12 on 2017-07-29
Class 10 is the fastest AFAIK

---

