---
title: "667mhz ddr2 ram on 533mhz fsb"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by sharks on 2008-05-08
will there be any problems with 667mhz ddr2 ram on 533mhz fsb?

---

### Post by skymera on 2008-05-08
Im sure the RAM will slow down to 533MHz if that's the case.

---

### Post by sharks on 2008-05-08
i am not worried abt slowing down but i m worried abt stability

---

### Post by skymera on 2008-05-08
I run 2GB 667MHz and 1GB 533MHz RAM.

My 2GB slows down to 533MHz. Perfectly stable.

If you have any doubts you could run Memtest86+ from the GRUB menu.

---

### Post by sharks on 2008-05-08
i will be replacing my 533mhz ram with 667mhz.so no talk of mixing these two.
is the maximum speed of ram limited by the FSB?

---

### Post by skymera on 2008-05-08
O, ermm.

I think it does yes.
If i remember rightly the FSB is the speed at which data travels across the motherbaord?

So i do think 667MHz will run at 533MHz.

Plus there is no noticeable difference between 533 and 667.

---

### Post by ymo on 2008-05-08
My Dell Inspiron 6000 came with 1x 512MB PC-3200 in single channel mode. After 2 years I added a 512MB PC-4200 SO-DIMM which it also ran at 400MHz (because of the slower DIMM in slot 1) but in dual channel mode. A week ago I replaced both with a pair of 667MHz 1GB SO-DIMMs and my system now runs at 533MHz dual channel.

The SPD EEPROM on the DIMM has room for details about up to 4 different speed settings so a 667MHz module should have details about 533MHz and 400MHz as well.

The chipset used on your motherboard will determine the maximum RAM speed you will be able to take advantage of.

---

### Post by H.Callahan on 2008-05-08
667 should run just fine at 533.  There will be no performance gain in any way by running the 667 instead of the 533.  It will just run at 533 speeds.  Assuming that the memory is good, there should be no stability issues.

[quote="skymera"]If you have any doubts you could run Memtest86+ from the GRUB menu.[/quote]
Excellent advise if you have any qualms at all.  Just be sure to run it for a significant amount of time (overnight or 24 hours, at least) to be sure that you catch ANY instability.

---

### Post by sharks on 2008-05-08
my mobo's speed is 533mhz fsb.will it be compatible with 667mhz ddr2 ram.

---

### Post by H.Callahan on 2008-05-09
> **sharks said:**
> my mobo's speed is 533mhz fsb.will it be compatible with 667mhz ddr2 ram.
Yes.  It will make the 667Mhz RAM run at 533Mhz, but that is not harmful to either the motherboard or the RAM.  The RAM will perform like it is 533Mhz RAM.  The motherboard will not be able to tell the difference.  You will not get any performance improvement just for the mere fact that the RAM, in reality, is certified to 667Mhz.

---

### Post by bumanie on 2008-05-09
> **H.Callahan said:**
> Yes.  It will make the 667Mhz RAM run at 533Mhz, but that is not harmful to either the motherboard or the RAM.  The RAM will perform like it is 533Mhz RAM.  The motherboard will not be able to tell the difference.  You will not get any performance improvement just for the mere fact that the RAM, in reality, is certified to 667Mhz.

+1. It will be fine the ram downgrades its speed to to the fsb and behaves as per 533mHz ram.

---

