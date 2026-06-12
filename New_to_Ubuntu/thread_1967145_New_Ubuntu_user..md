---
title: "New Ubuntu user."
date: 2012-04-27
forum: New to Ubuntu
---

### Post by Wallnutter on 2012-04-27
Before you read the rest of this, I'll get my question in first.
I  have Ubuntu 11.10 installed on the 1st partition of my HD and this  morning I installed 12.04 on a newly created 2nd partition. Both  partitions are about 160Gb. I now don't feel I need 11.10. What is the  best way if possible to uninstall 11.10 and keep 12.04 on the 2nd  partition? Is there commands I can use within terminal?

I  recently had a shed load of problems with my Acer Aspire 6935. It was  running on Windows Vista since the day I bought it about 3-4 years ago.  Over the past 6 months I've had to do a reinstall from a master disc  about once a month as the PC would constantly run into booting  difficulties ( there were more severe problems than this though but I'll  not go there unless you want to have a good laugh). I sort of guessed  it was down to bad sectors on the HD after getting the same messages  from running a checkdisc . A friend of mine who works at this sort of  thing give me a load of options on how to fix the problem. The main one  though was to do a LLF ( zero fill ) of my hard drive which would  discover the bad sectors and make the HD useful again. He used a live  disc version of Ubuntu 11.10 to retrieve my photos etc to be saved on a  USB drive. He kindly gave me the live disc and told me to try it out.

At  first I wasn't that impressed. I installed it ( erasing Vista ) with  full updates and played about with it for a few days this week. I found  firefox ( this was my default browser on windows too ) to be painfully  slow in comparison to how it ran on Vista. This morning though, I  stumbled across the Ubuntu 12.04 release and downloaded and installed  that with full updates ( took about 2 hours ) on a second partition  alongside 11.10. The difference was astounding.

I'll make a few  comparisons for you. After a clean install of Vista, from pressing the  power button to be online and browsing, my laptop took 70 seconds (  allowing for the start up options ).

With Ubuntu 12.04, it takes  45 seconds and the first 20 seconds of that are wasted with the start up  options ( these include change boot device / enter bios and then  selecting the version of Ubuntu to use ). Firefox is now super quick. My  machine has never ran so quietly and is a lot cooler than it was on  Vista ( I never hear the fan rev up at all now ). The bundled software  and user friendly interface is amazing when you get accustomed to it and  thankfully that doesn't take long. I've started to love my laptop again  and it didn't cost me a penny ( thought I was going to have to replace  the hard drive ).

Well done on releasing a cracking piece of software. Thank you.

Thanks for your replies in advance.

---

### Post by calavier62 on 2012-04-27
Simple. format the first partition using GParted while in Ubuntu 12.04. It won't mess up your bootloader, because that's on the MBR, and you can use the free space to create a new partition for file storage, another operating system, or you can expand the 12.04 partition to take up the entire hard drive (you must boot from a Live CD or USB in order to do that)

You'll need to download GParted, but it's very intuitive and easy to use. I would post pictures, but I only have one partition, and it wouldn't be an accurate example for you to follow.

---

### Post by jerome1232 on 2012-04-27
Well part of grub lives in the mbr, the rest lives in /boot, mostly likely the grub you are using now though is linked with your last installs /boot, so it should be safe.


Keep a live cd handy just in case. You can install gparted from the Ubuntu Software Center.

---

### Post by cryptotheslow on 2012-04-27
Usually I would ask that you download and run the boot info script and post back the resulting RESULTS.txt so we can see what is installed where.

That is usually found here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

But it seems the sourceforge site is either having issues or under maintenance.

You ***should*** be fine just to use Disk Utility to format the 11.10 partition and then before rebooting issue this command:

```
sudo update-grub
```

in order to rebuild the grub loader configuration.

Once you have confirmed that you can still boot into 12.04 you could then format the 1st partition to use as a data partition. Otherwise if you intend to grow the 12.04 partition to use the now freed space - ask here first as I have a feeling the UUID of the partition may change (breaking your bootup) and the process will be more convoluted than simply resizing the partition from a LiveCD.

---

### Post by jroa on 2012-04-27
Everything said before is great advice.  However, I noticed that you specifically asked for command line instructions.  If you want to do it the easy way, use gparted or disk utility.  If you want to do it through the command line, let us know and we can give you commands.

---

### Post by Wallnutter on 2012-04-28
Thanks for the replies guys. I've read a lot about GParted but I've never used it. This seems like the simplest option and I also need to familiarize myself with some of the new software options I can download now on Linux, so it's the option I'm going for. The good thing is, even if I mess up I can just throw the live disc of 12.04 back into my machine again and know that bob will still be my uncle.

---

