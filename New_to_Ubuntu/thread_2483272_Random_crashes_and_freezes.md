---
title: "Random crashes and freezes"
date: 2023-01-24
forum: New to Ubuntu
---

### Post by oblithian on 2023-01-24
I need some help identifying the root problem(s).

I get random reboots when using opera (they had gone away mostly, but recently returned after upgrading to Jammy).

But more regularly I have issues when transferring numerous files, it will freeze the entire system often beyond REISUB.

I also have issues with certain downloads, it will get mid-way through and freeze forcing a reboot(s). After resuming the download repeatedly it never completes. Deleting the download and re-starting doesn't seem to help. I have had the item downloaded before, however due to a faulty update I had to try a clean install.

I assume at least the download and transfer issue has the same root cause.

I had tried a memory and hard-drive check early on and it said they were fine (though who knows after all the reboots).

What would you like me to add, and where should I add it? (log files, system details, etc.)

---

### Post by Impavidus on 2023-01-25
Apparently random crashes and freezes are a bit hard to diagnose.

Have a look at the logs. See if there are entries with a timestamp matching the time of the crash/freeze. You might find something interesting. Or maybe not.

Could you be running out of memory? Operations on large files take a lot of RAM (mostly for caching). Monitor your RAM use.

How much RAM? Swap? What CPU? Graphics?

---

### Post by oblithian on 2023-01-25
My computer is crashing while typing so I will have to type in chunks. The upgrade to Jammy definitely triggered this higher crash regularity.
Summarizing the massive terminal output:
 B450 TOMAHAWK MAX II (MS-7C02)
 AMD Ryzen 7 5700G with Radeon Graphics
 AMD RADV NAVY_FLOUNDER ASUS Dual 6700XT OC
 DDR4 3200 A-DATA Technology 8Gb (g-skill)
 F4-3200C16-8GVKB unknown 8Gb (XPG)
 DDR4 3200 A-DATA Technology 8Gb (g-skill)
 F4-3200C16-8GVKB unknown 8Gb (XPG)
 Primary SD:
  NVMe WDC WDS100T2B0C-00PXH0 Sandisk Corp 1TB 'EXT 4 Volume'
 HDDs:
  ATA Disk ST500LM012 HN-M5 500Gb 'Windows NTFS'
  ATA Disk TOSHIBA MK5055GS 500Gb 'Windows NTFS'
 ODD:
  ASUS BW-16D1HT DVD-RAM Writer

Can I link a cloud drive or something with all the log files?

---

### Post by Impavidus on 2023-01-26
So no lack of memory. Have you got any swap? Even if you rarely use it, having a little bit of swap may be beneficial. We normally recommend about 2GB.
> **oblithian said:**
> Can I link a cloud drive or something with all the log files?
You could, but I don't think anyone here is willing to sift through hundreds or thousands of lines of your log files, not knowing what exactly to look for. We're just volunteers. You should at least try to narrow it down looking at the time stamps. If the cause of the crash is logged, it should be within a few seconds of the moment of the crash.

Opera is not the regular browser on Ubuntu. There could be an issue with the browser not being built properly for your version of Ubuntu.

Are there any crashes when runing a live disk? If it's driver or hard drive related, that could make a difference.

---

### Post by oblithian on 2023-01-27
I have tried pulling some memory but I can try moving it around.

I have had some luck getting it back to more stable post-jammification (upgrade to Jammy), by disabling the integrated graphics in the BIOS.
   (Seems to rhave resolved this issue which would just spam, once triggered--> [COLOR=#696969]gnome-shell: Failed to scan out client buffer: drmModeAtomicCommit: Invalid argument[/COLOR][COLOR=#696969]    kernel: [drm:dm_plane_helper_prepare_fb [amdgpu]] *ERROR* Failed to pin framebuffer with error -22[/COLOR])

The file transfer will require more testing.

What is a live disk? like a CD-Rom?


Opera seems to have an issue with 'snap' Which I believe is a new thing for jammy(??), but it also had issues before. I will try to update it.


Also the logs aren't that long lol. I suspect the issue would also be apparent shortly before the crash but I don't know enough to confidently identify cause or effect.

---

### Post by Impavidus on 2023-01-29
> **oblithian said:**
> 
What is a live disk? like a CD-Rom?

The bootable drive you used to install Ubuntu. Normally, we use live usbs these days. Optical media are a bit slow and may cause timeouts, although it should work eventually.

---

### Post by math492m on 2023-01-30
do you know the health of discs and or ram ? :)

---

### Post by agentl074 on 2023-01-30
Back when I had my laptop with 22.04, I had the 5500U with integrated graphics and it didn't freeze, didn't radomly reboot, and went into suspend and woke up just fine. I had 12GB of memory and just let Ubuntu handle swap and partitioning at installation. I don't know why the desktop 5700 would be that much different since amdgpu powers both :confused: I used shoplinux USB.

---

### Post by oblithian on 2023-02-15
So I ran it as 'try ubunu' aside from, the transfer rate being about 10%-15% faster, it still froze.

Then I installed an update.

> **math492m said:**
> do you know the health of discs and or ram ? :)

I checked all came out clear.

I pulled the ram and put both sets in the primary slots. No issues.


So far either it is a coincidence the issue is resolved, the update fixed it, or one of two is an issue (the motherboard ram slots A1 and/or B1, when all the ram is installed simultaneously).

So I can test a bit more.

What I have noticed though, is one of the recent updates does seem to inhibit transferring files to multiple locations simultaneously (by dragging, right click move to still helps).
I am going to put all the ram back in and we shall see...

---

