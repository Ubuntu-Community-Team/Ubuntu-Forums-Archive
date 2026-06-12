---
title: "Pi terminal -- firmware flash help"
date: 2017-09-13
forum: Programming Talk
---

### Post by rhss6-20112 on 2017-09-13
Hello everyone,
I have a seriously off-the-wall question.

I am trying to **flash** the necessary **firmware** for an **xbox 360 (250GB HDD)** to an incredibly old HDD of my own to seriously upgrade the storage on it. My old 360 HDD went bad (irreparably so, to the point where gparted, gparted live, and DDrescue wouldn't even recognize the drive). Needless to say, I have a temporary solution of plugging in another HDD of mine into the USB port of the 360 to do what needs to be done, but I really would rather be able to use a HDD properly, mainly so I'm not wasting a usb slot.

So, I went online found this web page (for windows, possibly wine) that I can load the firmware in a file **(.bin file)** with a windows application while booting into the drive on my computer, and flash it voila.....

_**Not gonna happen. I'm running a Raspberry Pi model 3b. (currently using Ubuntu Mate 16.04 Pi edition on a 16GB SD card, but can also switch my other 16GB SD card and use Raspbian)**_
Heres the funny thing... I managed to create the DOS partition table with gparted without any issue. ***Used dd if=/path/to/BIN/file of=/dev/HDD-for-Xbox*** without an error via the terminal, assuming that it would work the same way as cloning a disk or creating a bootable drive.... Failed epically once I put the HDD into the xbox. didn't show up whatsoever.

Which brings me to my conondrum.

I have a **HDD** that **IS flashable**. I have a "computer", and I'm a little bit savvy with the terminal (albeit I'm pretty rusty, as it's been a while) and for all intent and purpose using DD to flash the firmware SHOULD have worked.

So does anyone know what I'm missing, **or do I need to install a terminal-friendly tool to flash the firmware** via cmd-line to "hack" the old HDD.

(Btw, not sure if it really makes a different, but it  is a 250GB MAC-OS HDD which had a GPT partition on it, which I had to remove, then format to MSDOS in order to actually use it and attempt to flash the firmware).

If anyone knows where to point me, it'd be greatly appreciated, thanks!

---

