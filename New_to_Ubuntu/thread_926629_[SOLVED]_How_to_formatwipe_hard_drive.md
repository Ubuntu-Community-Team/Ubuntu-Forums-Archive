---
title: "[SOLVED] How to format/wipe hard drive"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by jon555 on 2008-09-22
I think that I might have some hidden viruses on HDD. I would like to Wipe and format it, How can I format HDD from Ubuntu live CD?

---

### Post by bumanie on 2008-09-22
Jon555, I can tell you how to do that, but I did answer a previous post by you re windows not booting, if wishing to wipe your hard drive is in response to that issue, things may be able to be done that can save your previous setup without taking such drastic steps. I suspect that you installed windows in a logical partition , therefore it wouldn't boot - windows will not boot from a logical partition. Post output of > sudo fdisk -l(That's a lower case L not a numeral one) from the live cd before wiping the drive.

---

### Post by jon555 on 2008-09-22
Sorry too leate - long story anyway I sort of messed it up. Deleted that partition, but when installed windows that said, something wrongf with Hdd. So I wana format it clean make two partitions install windows first and then Ubuntu.

---

### Post by L Campbell on 2008-09-22
> **jon555 said:**
> I think that I might have some hidden viruses on HDD. I would like to Wipe and format it, How can I format HDD from Ubuntu live CD?

First, you probably already know, you have to set the boot order in BIOS, so that the CDROM boots first.

Boot up the live CD and then select 'Install' (the icon should be on your desktop).

The install process allows you to take the entire Hard Drive for Ubuntu and thus effectively gives you a clean slate to work with.

Hope this helps you.

---

### Post by jon555 on 2008-09-22
Thnx Campbell, but I want also make windows partition, so I must format it all before and I want do it from Ubuntu.

---

### Post by jon555 on 2008-09-22
I guess I did it with Gparted

---

### Post by rolnics on 2008-09-22
When you get to the partition section click the custom / manual option for setting up your own partitions. Then make sure you leave XXGb's on the first hard of your hard drive for windows, then use the rest of the hard drive for linux, probably an idea to create a separate /home as well.

---

### Post by bumanie on 2008-09-22
That's a shame. Oh well, these things happen sometimes. From the live cd > sudo apt-get install gpartedThis will install the partition editor. Go to System --> Administration --> Partition editor. Highlight the partitions and click format and choose the filesystem you want. You can pre-partition one ntfs partition and one ext3 partition at this stage if you wish. It is better to install windows first, followed by ubuntu. It is also a good idea when installing ubuntu to choose manual at the partitioning stage and make a 6-8gb / a 1-2gb swap and a separate /home as large as you want. This way if something goes wrong with ubuntu, you only have to reinstall to / and all your saved data in /home is safe.

---

### Post by jon555 on 2008-09-22
Thnx it worked bye!:)

---

### Post by rolnics on 2008-09-22
Take a look at [this.]("http://www.psychocats.net/ubuntu/images/installinghardyplus10.png") That is a screen shot of the options I was talking about in my earlier post. 

But I would take a look at [psychocats]("http://www.psychocats.net/ubuntu/installing") guide he if you want to dual boot, I found his guides a god send when I was starting out and I still refer to them.

---

### Post by chongzivalve0809 on 2008-09-22
a professional [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) China manufactuer and supplier,established in 1983The main product is:cast steel [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm),forged steel gate valve ,pressure seal gate valve,plate [gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm).  BFV Valve also possess the test lab with various of examination equipment for material chemical composition analysis, physical property and non-destructive examinat-ions such as RT,UT,MT,PT .[gate valve](http://www.valvesupplier.net/forged-steel-gate-valves.htm) manufacturer website:[www.valvesupplier.net/forged-steel-gate-valves.htm](http://www.valvesupplier.net/forged-steel-gate-valves.htm)

---

