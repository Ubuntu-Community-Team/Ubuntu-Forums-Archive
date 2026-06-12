---
title: "Dawicontrol DC600e issues with Ubuntu desktop 13.10"
date: 2014-01-18
forum: New to Ubuntu
---

### Post by Jan_Van_Gulck on 2014-01-18
Hi all,

I stumbled across a little problem yesterday. Tried a bit to make my own NAS solution, but that didnt work out that well.
So far I have been using all seperate drives in a windows share to stream my HTPC with XBMC downstairs.

Now I wanted to run my server on Ubuntu and make it a large pool (4x 3TB data and 2x 2TB parity).

The only problem I have is that my MB has 4 SATA connectors. So I bought myself a Dawicontrol raid controller (nothing fancy anyway) with 2 SATA ports.

In Windows the 2 disks connected to the SATA controller where recognized as seperate disks, hence I never configured any raid for them. 
But now in Ubuntu they dont show using fdisk -l and I cant seem to figure out how to get them running and being recognized by Ubuntu.

They are recognized by the RAID bios, but not the main MB bios. My intention is NOT to run a RAID setup, nor software RAID, but just to make a huge disk pool appearing as one with MHDDFS and then
make myself 2 parity drives with Snapraid. 


Can someone help me how to get the drives connected to the DAWIcontrol visible?

---

### Post by Jan_Van_Gulck on 2014-01-19
Is there a terminal command to search for disks connected to anything but the mainboard? Maybe I'm searching in the wrong place for the 2 drives connected to the PCI Sata controller.
And is there an equivalent of the Windows Device Manager in Ubuntu? Where you can find all the installed devices with their drivers... ?

---

