---
title: "pls. help an SSD newbie on 10.04"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by Zenrunner92 on 2012-01-02
Have just installed a 40GB Intel 320 SSD on my +2 year old Samsung NC10 netbook (Atom 270, 2GB RAM) in hopes of reviving it...fairly pleased with the improvement so far over the previous Western Digital Black 500GB 7200rpm drive, but I have a feeling there are lots of tips and tricks that I am missing to truly maximize performance.

Are there any particular adjustments or optimizations I should make to let Ubuntu OS know that I'm running an SSD so that it would better adapt itself to this technology?  In Windows 7 there's something called TRIM, turning off indexing, etc. which is supposed to be essential for optimal performance as well as extending the life of the drive.  What would be the Ubuntu equivalents?

Thanks for your help!

PS. Please don't suggest upgrading to Ubuntu 11.04/10, I already tried that months ago with the old HDD and it was horrible.  I also tried Lubuntu on the old HDD and it seemed to be very buggy, so I think I will be sticking to 10.04LTS for the time being...

---

### Post by JRV on 2012-01-02
These are SSD tweaks I gleaned from the eeeuser.com forum.  That forum no longer exists.

> 
Four Tweaks for Using Linux with Solid State Drives

Published in September 4th, 2008
Posted by Tom in tips

SSDs (solid state drives) are great. They’re shock resistant, consume less power, produce less heat, and have very fast seek times. If you have a computer with an SSD, such as an Eee PC, there are some tweaks you can make to increase performance and extend the life of the disk.

   1. The simplest tweak is to mount volumes using the noatime option. 
      By default Linux will write the last accessed time attribute to files. 
      This can reduce the life of your SSD by causing a lot of writes. 
      The noatime mount option turns this off.

         Open your fstab file:
         gksudo gedit /etc/fstab

      Ubuntu uses the relatime option by default. For your SSD partitions
      replace relatime with noatime in fstab. Reboot for the changes to take effect.

-------------------------------------------------------------------

   2. Using a ramdisk instead of the SSD to store temporary files will speed things up,
      but will cost you a few megabytes of RAM.

         Open your fstab file:
         gksudo gedit /etc/fstab

      Add this line to fstab to mount /tmp (temporary files) as tmpfs (temporary file system):

      tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

      Reboot for the changes to take effect. Running df, you should see a new line with /tmp mounted on tmpfs:

      tmpfs 513472 30320 483152 6% /tmp

--------------------------------------------------------------------------------------------------------

   3. Firefox puts its cache in your home partition. 
      By moving this cache in RAM you can speed up Firefox and reduce disk writes. 
      Complete the previous tweak to mount /tmp in RAM, and you can put the cache there as well.

      Open about:config in Firefox. Right click in an open area and create a new string value 
      called browser.cache.disk.parent_directory. Set the value to /tmp/$USER/firefox-tmp.

------------------------------------------------------------------

4. Turn off Journaling in EXT4

First thing's first, we can confirm that our ext4 partition is running a journal with

  sudo dumpe2fs /dev/sdaX | grep has_journal

Disabling journaling is rather easy, the only drag is that to make structural changes to a filesystem, 
the filesystem cannot be mounted with read/write privileges. So, run a live cd and hit

  sudo tune2fs -O ^has_journal /dev/sdaX

And it's done. Now when you boot, the change will be noted and the disk will be checked for errors. 
When the system is finally up we can run this again to confirm that in fact ext4 is running without a journal

  sudo dumpe2fs /dev/sdaX | grep has_journal

should now return nothing.

With this quick fix, no more constant IO peaks. I can now watch youtube videos without constant freezes.


---

### Post by GWBouge on 2012-01-02
Here's another guide:

[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/]("http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/")

Note that for TRIM support (the 'discard' option in your fstab), you'll need kernel 2.6.33 or later, so if you're on 10.04 you'll need to have backports updates enabled.

---

### Post by Paqman on 2012-01-02
To enable TRIM all you need to do is add the option "discard" to your fstab (assuming you have a kernel with TRIM).

I'd advise strongly against disabling journalling in your filesystem. The early Eee PCs used a very basic first generation SSD that didn't do wear levelling, so reducing writes was desirable. On a good Intel SSD there's no need to disable important and useful functions like journalling just to reduce writes. 

I'd also suggest that noatime is a bit pointless, relatime is the default and perfectly good.

Putting /tmp and browser cache into a ramdisk couldn't hurt, assuming you have the available RAM, but again I don't think doing so just to reduce writes to disk is important.

All I do for my SSDs is enable TRIM and make sure the partitions are aligned. There was a lot of angst about reducing writes in the early days, but proper SSDs with wear levelling have proved to be perfectly reliable and robust.

---

### Post by Zenrunner92 on 2012-01-03
Thanks for the replies...I'm afraid that I'm technically pretty clueless however, so please bear with me.

GW Bouche: how does one find out which kernel the OS is using?  And how to enable backports?

Paqman: how does one "make sure the partitions are aligned?"  Having only 40GB on my SSD, I didn't know I had any partitions other than the swap file and root file...just used the default setting when installing 10.04

If you guys could provide the simplest "Ubuntu For Idiots" type instructions, that would be most appreciated!  :D

Or maybe, please boil it down to "What are the MOST ESSENTIAL tweaks/adjustments to make for an SSD based Ubuntu?"

---

### Post by GWBouge on 2012-01-03
To find some information on what kernel you're using, you can goto the 'System' tab on the System Monitor, or open up a terminal and use the following command:

```
uname -a
```

I'm not on 10.04, so this may be slightly off, but to enable backports you should open up the Synaptic Package Manager and goto Settings -> Software Sources -> Updates, and it should be the 'Unsupported updates' option.

---

### Post by Paqman on 2012-01-04
> **Zenrunner92 said:**
> 
Paqman: how does one "make sure the partitions are aligned?"  Having only 40GB on my SSD, I didn't know I had any partitions other than the swap file and root file...just used the default setting when installing 10.04


It's possible the installer is smart enough to do this for you when it sets the system up, but just in case it does the easiest thing to do is boot up into a LiveCD or USB and add a 1MB gap either side of any partitions, ensuring that the option "round to cylinders" is unchecked.

---

### Post by Zenrunner92 on 2012-01-05
> **GWBouge said:**
> To find some information on what kernel you're using, you can goto the 'System' tab on the System Monitor, or open up a terminal and use the following command:

```
uname -a
```

I'm not on 10.04, so this may be slightly off, but to enable backports you should open up the Synaptic Package Manager and goto Settings -> Software Sources -> Updates, and it should be the 'Unsupported updates' option.


it says 2.6.32-37 ... ok, so I've done what you suggested in the SPM and it took about 5 minutes to download a bunch of stuff, then I restarted the computer, but the Terminal screen tells me that I'm still on the same 2.6.32-37 kernel.  Huh???

---

### Post by Mark Phelps on 2012-01-05
If you have Windows on your Samsung, then look around for "AS SSD Benchmark Utility".  It's a free download and will run some performance benchmarks against your SSD so you can see how well it is performing.

Also, in Windows, look around for "CrystalDisk v1.4".  It will show you detailed info on your SSD, including what Features have been enabled.  It's also a free download.

---

### Post by Zenrunner92 on 2012-01-05
Well, finally found a really quick and easy way to update the kernel.  Posting it here in case anyone else does a search for this same issue:

[https://sites.google.com/site/lightrush/random-1/howtoinstalllinuxkernel2635onubuntu1004lucidfromubuntu1010mavericktheeasyway](https://sites.google.com/site/lightrush/random-1/howtoinstalllinuxkernel2635onubuntu1004lucidfromubuntu1010mavericktheeasyway)

And how to turn on TRIM manually:
[https://sites.google.com/site/lightrush/random-1/howtoconfigureext4toenabletrimforssdsonubuntu](https://sites.google.com/site/lightrush/random-1/howtoconfigureext4toenabletrimforssdsonubuntu)

Thanks again everybody, for your help.

---

### Post by Zenrunner92 on 2012-01-05
> **Mark Phelps said:**
> If you have Windows on your Samsung, then look around for "AS SSD Benchmark Utility".  It's a free download and will run some performance benchmarks against your SSD so you can see how well it is performing.

Also, in Windows, look around for "CrystalDisk v1.4".  It will show you detailed info on your SSD, including what Features have been enabled.  It's also a free download.

No, it's a single-OS machine...with the crappy Atom N270 processor I really need the easier load of Ubuntu over WIndows.  

BTW ... this is off-topic but I notice in your sig that you use 11.04 or 11.10 ... did you find that those versions were faster or slower on your computer compared to 10.04?  I am wondering if there are any speed advantages to going up to those, or if I'm better off sticking to 10.04 with such a low-power processor like mine and only 2GB of memory.  I tried 11.04 about six months ago but using a 7200rpm WD spindle drive and maybe the install was corrupted somehow because it was buggy and slow as hell so I reverted.  Wonder if the SSD would enable a smoother transition now?

---

### Post by Zenrunner92 on 2012-01-06
Oops, one last question: what about going into BIOS and turning on ACHI?  Or is that more relevant for a Windows user?

---

### Post by Welly Wu on 2012-01-19
I followed the guides and I am using Ubuntu 10.04.3 64 bit LTS. I have to reboot my ASUS N61JV-X2 notebook PC to have the changes take into effect. Thanks for the help.

---

### Post by Welly Wu on 2012-01-19
I have an ASUS N61JV-X2 notebook PC with Crucial 8 gigabytes of DDR3 PC-8500 SODIMM SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 gigabyte Solid State Drive. I followed the instructions to optimize my Ubuntu 10.04.3 64 bit LTS, but I keep getting random system freezes and lockups. I decided to get rid of the RAM disk option as I think that is causing the problem and I will continue to use my computer to see if I keep getting random system freezes and lockups. Has anyone else experienced similar problems? What were you solutions? Thank you.

---

