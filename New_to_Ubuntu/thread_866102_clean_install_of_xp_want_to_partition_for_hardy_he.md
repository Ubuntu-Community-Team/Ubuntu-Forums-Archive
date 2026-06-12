---
title: "clean install of xp want to partition for hardy heron dual boot"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by MeTylerDurden on 2008-07-21
[SIZE="2"]I see alot of people saying just install xp on the entire space and others saying leave 10GB and a swap space of 512MB. which is the right one??[/SIZE]

---

### Post by kk0sse54 on 2008-07-21
You can install xp over the whole thing and then through the liveCD partition the hard drive accordingly for Ubuntu with your / as however big you want it to be depending on what kind of data you will be storing in it and if you will be having a seperate home partition and the swap is generally about double your RAM even though most people never really use all of it.

---

### Post by BoarderX2k3 on 2008-07-21
If you are starting from scratch, I would suggest installing XP first and then installing Ubuntu. Not far into the Ubuntu installation you will be able to make the decision to dual boot or not. The installer pretty much takes care of everything for you.

---

### Post by bumanie on 2008-07-21
A swap partition is a mandatory partition under linux; 1-2gb max. is plenty. These days with with ntfs-3g (read/write to ntfs from linux), there is no advantage in having a shared partition, if that's what you are refering to re the 10gb free. It is a good idea to manually aprtition and ahve a / partition of 8-10gb, swap 1-2gb and a separate /home as lsrge as you like. This way if something happens to the ubuntu filesytem, you only have to reinstall to / and data in /home is safe.

---

### Post by wolfen69 on 2008-07-21
there is no "right way" to do it. perhaps you should read [this]("http://www.psychocats.net/ubuntu/installing") .

---

### Post by MeTylerDurden on 2008-07-21
> **C!oud said:**
> You can install xp over the whole thing and then through the liveCD partition the hard drive accordingly for Ubuntu with your / as however big you want it to be depending on what kind of data you will be storing in it and if you will be having a seperate home partition and the swap is generally about double your RAM even though most people never really use all of it.


 this confuses me: the swap is generally about double your RAM (i am just banging my head on the wall ) ram is memory so how do you double that? how do you figure that?

---

### Post by MeTylerDurden on 2008-07-21
[SIZE="2"]And I would gather it is safe to proceed with partitioning all disk space for xp for starters, then let the ubuntu cd repartition later![/SIZE]

---

### Post by kk0sse54 on 2008-07-21
> **MeTylerDurden said:**
> this confuses me: the swap is generally about double your RAM (i am just banging my head on the wall ) ram is memory so how do you double that? how do you figure that?

Depending on how much RAM you have, lets say 1 GB then your swap partition should be set up as double of that so it would be 2 GB.
Yes just let Ubuntu partition it for you after the xp install.

---

### Post by cariboo on 2008-07-21
The easiest way to do this is to decide how much hard drive space you need for windows, then just partition that amount and leave the rest of the hard drive blank. You can do this in the Windows partitioning section.

As far as swap is concerned if you have 1GB ram your swap should be 2GB, if you have 2GB ram your swap should be 4GB.

Jim

---

### Post by MeTylerDurden on 2008-07-21
> **cariboo907 said:**
> The easiest way to do this is to decide how much hard drive space you need for windows, then just partition that amount and leave the rest of the hard drive blank. You can do this in the Windows partitioning section.

As far as swap is concerned if you have 1GB ram your swap should be 2GB, if you have 2GB ram your swap should be 4GB.

Jim


 I have 2 slots of ddr2 ram each are 1GB so my swap would be 4GB and I don't count my hard drives ram thats what I gather ..(hard drive is seagate barracuda 3.0 Gb)

---

### Post by Paqman on 2008-07-21
Also don't forget that you don't have to partition the disk if you don't want to. The Wubi install method will create a virtual hard drive on the Windows partition and install Ubuntu onto it.

To use the Wubi method, just pop your LiveCD in while in Windows. It'll install while in Windows, then when you reboot you'll have the option of booting into Ubuntu instead. I highly recommend it.

[More info about Wubi](http://wubi-installer.org/)

---

### Post by MeTylerDurden on 2008-07-21
> **Paqman said:**
> Also don't forget that you don't have to partition the disk if you don't want to. The Wubi install method will create a virtual hard drive on the Windows partition and install Ubuntu onto it.

To use the Wubi method, just pop your LiveCD in while in Windows. It'll install while in Windows, then when you reboot you'll have the option of booting into Ubuntu instead. I highly recommend it.

[More info about Wubi](http://wubi-installer.org/)
  
I read about that and was not sure to do this or not.. I wish I could do both and then decide.. but maybe some1 else has tried both ways..  really whatever is more stable would be fine with me

---

### Post by MeTylerDurden on 2008-07-21
I have commited to xp partitioning all my space so the next big question is to do a seperate partition for ubuntu using the live cd- or using ubuntu within xp      this is getting interesting perhaps another thread on that question

---

### Post by BoarderX2k3 on 2008-07-21
> **MeTylerDurden said:**
> I read about that and was not sure to do this or not.. I wish I could do both and then decide.. but maybe some1 else has tried both ways..  really whatever is more stable would be fine with me

I suggest going through the process of partitioning/installing Ubuntu if you do not have a preference. Not only is it going to be stable, you will learn more that way.

---

### Post by bumanie on 2008-07-21
I too suggest a dual boot is better than a wubi installation. You should back up any important xp data, just in case. As said earlier there is no real right or wrong way to install, but a separate /home does have advantages, IMO. There are many tutorials on the internet. Read a few of them, until you get a 'feel' for how to go about installing correctly. We were all at your stage once, when we hadn't used linux before and were unsure of what to do. Trying things out is learning - yes you will make mistakes at times, but mistakes make you learn more than if everything always works perfectly. As long as important data is backed up, you have no real need to worry.

---

### Post by Paqman on 2008-07-21
> **MeTylerDurden said:**
> I wish I could do both and then decide.. 

You can. A Wubi-installed copy of Ubuntu can be migrated to it's own partition at any time using a package called LVPM. You don't even need to reinstall, just let LVPM migrate everything over.

I'd recommend using Wubi to start with. There are more important things on the Ubuntu learning curve than partitioning (such as package management, the CLI, file permissions, etc) Get your head around the basics of the system first, then you can play around with partitions later, since by then you'll have a much better idea of how you should set your system up.

Wubi is stable, btw. That's why it's included on the LiveCD now.

---

### Post by louieb on 2008-07-21
LOL Just my two cents. 
1st swap. Do you plan to hibernate the computer?
  If yes swap needs to be larger that the amount of ram you have with two gig of ram I'd make swap 2.5 gig.  
  If not then a half a gig of is plenty for swap.

I like to partition a computer so that my data is separate from the operating system. And I don't want my partitions to get more that 70%-80% full.

Now lets say you have a 100GB hard drive.  XP Pro + Office 2003 takes about 7 GB of hard drive space. So for XP I would give it 15-16GB of space. 

A full install of Ubuntu takes 3-4GB of space. So give it 7-10GB + a swap partition of .5 to 2.5GB. 

The rest of the space on the drive - turn it into a data partition that both xp and Ubuntu can use.  If you think you will use XP more format it NTFS. If Linux is what you use most format it ext3. If not sure then i would use NTFS.

---

