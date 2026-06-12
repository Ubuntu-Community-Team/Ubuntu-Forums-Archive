---
title: "what does EFI boot mean in gparted menu (liveCD)?"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by the8thstar on 2008-10-22
Hello there,

here we go with another technical question. When I reinstalled Ubuntu with the liveCD, I reformatted the hard drive with the built-in program gparted, to set partitions according to my will.

I noticed that there was an option for EFI boot or something like that, among the usual FAT32, NTFS, ReiserFS, Swap, Ext2 and Ext3. Would any techies out there care to explain what this EFI does?

Thanks!

---

### Post by phidia on 2008-10-22
Very generally EFI is a replacement of the aging BIOS system. I don't know how many computers have EFI. I believe the intel Macs have it.

More reading [here]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface").

---

### Post by the8thstar on 2008-10-23
Thanks a lot, **phidia**. Don't you think it's peculiar to find it in *gparted*?

---

### Post by /////// on 2008-10-23
EFI is the Extensible Fireware Interface, as phidia said, it is a replacement for the BIOS system and is used by Intel Macs. I believe it being in GParted has something to do with its boot manager which "An EFI boot manager is also used to select and load the operating system, removing the need for a dedicated boot loader mechanism (the OS boot loader is an EFI application)."

---

### Post by the8thstar on 2008-10-23
I wonder if I could create an EFI partition and put a graphical bootloader on it for my ubuntu much in the spirit of rEFIT for instance ([http://refit.sourceforge.net/]("http://refit.sourceforge.net/"))

Or maybe install rEFIT altogether?

---

### Post by the8thstar on 2008-10-23
BUMP - I need help here! ;-)

---

### Post by abcd629 on 2008-10-23
[nike shoes](http://www.vipnikeshoes.com)[air jordan](http://www.vipnikeshoes.com)

---

### Post by phidia on 2008-10-23
> **/////// said:**
> EFI is the Extensible Fireware Interface, as phidia said, it is a replacement for the BIOS system and is used by Intel Macs. I believe it being in GParted has something to do with its boot manager which "An EFI boot manager is also used to select and load the operating system, removing the need for a dedicated boot loader mechanism (the OS boot loader is an EFI application)."

That's "Firmware" not firewire, and it isn't just used in intel macs but I haven't come across it in regular consumer PCs. Thw wiki article I linked did say it's used in those though.

The8thstar, I would plan on doing a lot of reading but it should be possible just not sure how well it will work for you.
I would look at [this write up]("http://en.wikipedia.org/wiki/GUID_Partition_Table") and also use the original link I posted.

---

### Post by the8thstar on 2008-10-23
Woah, that's way beyond me. Thanks for the link though, it helped me figure out that there is a chance for a possible implementation in the future.

Unfortunately, that will not happen with me. My computer skills are too basic for that (no pun intended).

---

