---
title: "What do I do?"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by out4trout on 2011-12-05
I want to get umbutu on my machine, but I don't want to lose my data.  I know I should backup and will, but i was wondering if once I backup if I need to format the drive or just install umbutu, then delete EVERY other folder besides 'my documents' or what.
also i can run 64-bit if i want...do i want to?
I am a newbie, so please give me good detail.
Thank you!

---

### Post by didinium on 2011-12-05
All you need to do is back up via a portable memory device, e.g. a flash drive, install ubuntu then put everything you saved on ubuntu.

---

### Post by fantab on 2011-12-05
> **out4trout said:**
> I want to get umbutu on my machine, but I don't want to lose my data.  I know I should backup and will, but i was wondering if once I backup if I need to format the drive or just install umbutu, then delete EVERY other folder besides 'my documents' or what.
also i can run 64-bit if i want...do i want to?
I am a newbie, so please give me good detail.
Thank you!

More Information please:
Do you want to Dual-Boot Ubuntu with Windows? Or you want to go Ubuntu only? 

Ubuntu has no problems using NTFS file-system. It can very comfortably read and write to it. So if you are dual booting you can retain all your Windows Partitions. You will have to create some space for Ubuntu install. 

If your CPU/Processor supports 64bit computing then YES you can run 64bit.

---

### Post by out4trout on 2011-12-05
once I do that, there is no need to delete windows or anything it will be gone?  I do want it gone...so I want to make sure.  My documents folder will also be gone correct? 
is there a benefit speed wise between 32 and 64 bit?  or is one better in the sense that that there are more programs or more stable?
I am looking to make a fast stable machine, any help would be appreciated.

---

### Post by Frogs Hair on 2011-12-05
Hello and Welcome

Here is an example of a dual boot guide . [http://opensource-sidh.blogspot.com/2011/10/install-ubuntu-1110-and-windows-dual.html](http://opensource-sidh.blogspot.com/2011/10/install-ubuntu-1110-and-windows-dual.html) 

You can use 64 bit if you choose and make backups via removable device or cloud storage if you have it .

If you want to try Ubuntu by installing inside Windows with minimal commitment you could try Wubi but it has a 30 Gb maximum size and it is not recommended for long term use . [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

A traditional dual boot is the best option if you are interested in long term use .

---

### Post by out4trout on 2011-12-05
> **fantab said:**
> More Information please:
Do you want to Dual-Boot Ubuntu with Windows? Or you want to go Ubuntu only? 

Ubuntu has no problems using NTFS file-system. It can very comfortably read and write to it. So if you are dual booting you can retain all your Windows Partitions. You will have to create some space for Ubuntu install. 

If your CPU/Processor supports 64bit computing then YES you can run 64bit.

I want Ubuntu Only.  I don't know what a partition is...do i need to know?  Yes I went to cpuid.com and my processor is 64 although I am currently running xp 32 bit.

I just realized that I would like to bring over my outlook contacts/callendar/emails...what is the smartest way to do that?  Looks like Evolution is going to be where I wind up for mail as it looks very similar to outlook.  How do I make that move smoothly?  I have a couple pop addresses and one exchange email.

---

### Post by fantab on 2011-12-05
> **out4trout said:**
> **I want Ubuntu Only.**  I don't know what a partition is...do i need to know?  Yes I went to cpuid.com and my processor is 64 although I am currently running xp 32 bit.

I just realized that I would like to bring over my outlook contacts/callendar/emails...what is the smartest way to do that?  Looks like Evolution is going to be where I wind up for mail as it looks very similar to outlook.  How do I make that move smoothly?  I have a couple pop addresses and one exchange email.


Excellent choice. Yes you should know everything you can about your Hard Disk and how it works if you are going to save important data on it. In short, Partitions are shelves or racks in your cupboard (Hard Disk) to arrange or organize your stuff (Data). You can learn more if you Google.

Also have a look at Mozilla Thunderbird since it is available for both Windows and Linux, you can try it in windows and IMO will be easier to import Outlook contents to it.

---

### Post by DaveyG on 2011-12-05
[QUOTE=fantab]
Also have a look at Mozilla Thunderbird since it is available for both Windows and Linux, you can try it in windows and IMO will be easier to import Outlook contents to it.[/QUOTE]

Would the best bet being; import to Thunderbird, then export. Save exports, then import back into Thunderbird after installation of Ubuntu?

[http://kb.mozillazine.org/Importing_and_exporting_your_mail]("http://kb.mozillazine.org/Importing_and_exporting_your_mail")

---

### Post by enjoijesus94 on 2011-12-05
just dual boot

---

### Post by click4851 on 2011-12-06
dual boot would work, maybe a seperate home partition? How about linux on a USB stick?

---

### Post by desktorp on 2011-12-06
**32bit vs 64bit:**  This will end up being about memory/RAM.  If you have 4GB of memory or less, you should probably stick with 32bit.  The reason for this is because 32bit will limit your effective memory to around 3.7GB, no matter how much you physically have installed.  If you happen to have considerably more than 4GB, go with 64bit, so that you can take full advantage of what is installed.

**Dual booting:**  This can often be more complicated than it is worth, especially if you have decided to get rid of Windows and if you are not very familiar with the partitioning/formatting process; it is marginally "easier" to erase everything and install only Ubuntu, than it is to successfully install Ubuntu alongside an existing Windows installation.  To be fair, it's about the same amount of clicking, during the install, but the dual-boot option is more likely to give you problems, in the long run.

---

### Post by Paqman on 2011-12-06
> **desktorp said:**
> If you have 4GB of memory or less, you should probably stick with 32bit.

I don't see any reason to throttle a 64-bit chip down to 32-bit speeds. Even with less than 4GB RAM running in 64-bit mode will speed up some tasks considerably. Go with 64-bit if you have a 64-bit chip, regardless of how much memory you've got.

> 
**Dual booting:**  This can often be more complicated than it is worth

Agreed, especially since the OP said they've got no desire to keep Windows.

**out4trout**: When you go to install Ubuntu it will ask you if you want to wipe Windows and use the entire drive for Ubuntu. Just say yes to this and once the installer has done it's thing all traces of Windows will be gone (including all your data, so back it up!). It's really simple, don't sweat it.

---

### Post by out4trout on 2011-12-08
ok great I will install the 64 bit!
I actually installed the 32 yesterday and have had horrible problems trying to get the wireless card to work properly, so maybe somehow the new install will magic the problem away!
Thanks!

---

### Post by out4trout on 2011-12-09
I cannot get the 64 bit to load or install from the cd.  I see the first splash screen, then the screen goes black.  I hear the cd running, then eventually it just stops.  I hit the power button and the terminal screen comes up and I can see it shutting down and it asks me to eject the cd and press enter.  Why wont it run from the cd?

---

### Post by fantab on 2011-12-09
How did you download the .iso? How did you burn the .iso to the disk? It should be burned at the slowest possible speed.

---

### Post by out4trout on 2011-12-09
I did not burn it slow.  I followed the burning instructions on the ubuntu download page.  I believe that "max speed" was checked when I went through the burn.  i will re burn and post back results.
Thanks!

---

### Post by out4trout on 2011-12-09
THANK YOU!  that did the trick!
It is going through the clean install right now.  I did notice that while I was running the 64 bit from the CD that I had wireless connectivity problems.  the connection repeatedly dropped.  not sure how to repair that.  any thoughts?  The computer is an IBM T61 and the wireless card is [B]Intel AGN 4965 I believe.
Thank you!
[/B]

---

### Post by fantab on 2011-12-09
> **out4trout said:**
> THANK YOU!  that did the trick!
It is going through the clean install right now.  I did notice that while I was running the 64 bit from the CD that I had wireless connectivity problems.  the connection repeatedly dropped.  not sure how to repair that.  any thoughts?  The computer is an IBM T61 and the wireless card is [B]Intel AGN 4965 I believe.
Thank you!
[/B]

Usually the issues with Live CD are taken care of after the installation to the disk. If your problem is not solved then start a new thread. I am sure you will find a solution in no time.

---

