---
title: "Freezing after 5-10 seconds"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by daftKow on 2012-03-06
Hi All,

I've downloaded Ubutunu 11.10 AMD64 and used Universial USB Installer 1.8.8.5 to put it on a USB Key.

The system I wish to wipe/install Ubuntu on has the following specs:

AMD Athlon64 2800+ Newcastle
Chaintech VNF3-250
2x512MB OCZ PC3200 DDR
GeForce 5900XT 
120GB Seagate 7200RPM HDD

I manage to boot from the USB key; but Ubuntu doesn't seem to load completely and freezes within 5-10 seconds. For the first few seconds I can move my cursor around and even click some icons; but after it just hangs.

I try to install directly from the USB and again, it freezes within 5-10 seconds of the install screen.

I have even tried Linux Mint 12 64-bit with the same issue. I've tried different USB ports, different USB Keys - same issue. I've checked the MD5 sums of each file I've downloaded, they checked out.

Should I try the i386 version instead? The processor is AMD64, right? I'd like to take advantage of it if possible.

Any help is much appreciated!

---

### Post by _0R10N on 2012-03-06
Have you tried booting from the USB stick without installing the OS?

---

### Post by Diametric on 2012-03-06
You ran through most of the checks I would have gone through.  At this point, to answer your last question - yes.  Try an non x86_64 .iso and see if that helps.  I bet that barring something not already mentioned, this is the cause of the hang up.  That 1Gb of RAM is a little light.  Post back if the i386 works.

Also make sure to continue to run you md5sums on the .iso - especially if your doing a direct download....as opposed to a torrent.

Good Luck!

---

### Post by daftKow on 2012-03-07
> **_0R10N said:**
> Have you tried booting from the USB stick without installing the OS?

Yes, it just freezes after 5-10 seconds.

> **Diametric said:**
> You ran through most of the checks I would have gone through.  At this point, to answer your last question - yes.  Try an non x86_64 .iso and see if that helps.  I bet that barring something not already mentioned, this is the cause of the hang up.  That 1Gb of RAM is a little light.  Post back if the i386 works.

Also make sure to continue to run you md5sums on the .iso - especially if your doing a direct download....as opposed to a torrent.

Good Luck!

Agreed - 1gb is a little tight; I'll be looking at getting another gb used off someone on craigslist or kijiji.

I've downloaded the i386 iso; and put it on a USB; this time it doesn't freeze - but it doesn't appear to fully load. 

I get a white screen with a grey bar on the left; and I can still move the cursor but nothing happens when I click anywhere.

Perhaps something's corrupt on my computer? Motherboard/memory/HDD? it's weird though; XP seems to run fine (though spyware ridden...)

I've also tried Mint 12 32bit but it wont even boot from the USB key - it hangs at "SYSLINUX 3.86 2010-04-01 EBIOS Copyright (c) 1994-2010 H. Peter Anvin et al" - a quick search leads me to believe there is an issue with the way I made the USB drive bootable.

Perhaps I need to try another utility? I'd rather not burn a disc; that is so much trouble lol.

Thanks for all the help! Much appreciated!

---

