---
title: "Drive mounting/missing and RAID 0"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by chris218 on 2014-05-04
Hello all,

I am new to Ubuntu but decided it was the best route for me to take when building my new computer.  This computer is supposed to be an HTPC that I can travel with from time to time.  It is not a replacement for my NAS but needs to hold all of my media files. 

So, I am using an SSD for the OS and have installed three 3TB hard drives to store all of the media files.  I have been able to get the system up and running (after a few self-inflicted hardware/assembly issues) but the drives are giving me issues.  Here are the sequence of events that have transpired so far:

1.      After installing the drives, I was able to see all 3 (no visible issues) and formatted to NTFS.

2.      I attempted to transfer files via wi-fi and realized that this would take forever based on the amount of files to transfer.  I cancelled the installation.

3.      I moved the computer to a location which would allow for an Ethernet connection instead and upon powering up, the system would not mount the 3 drives and appeared to not like them in general (I can’t recall the error…but read on).

4.      Upon further research, I determined that NTFS might not be the best format so I changed all drives to EXT4.  The only way I could accomplish this is to use Gparted to create a partition and format that to EXT4.  From this point, I could at least see the drives again, where I could not see them before.  This also changed my drives from sdb/sdc/sdc to sdb1/sdc1/sdd1.  So, from my view, problem solved because I could at least see them when I could not before. 

5.      I during all of this, I also realized that I would be best suited for a RAID 0 arrangement (I am aware of the pros and cons of this) so that I could see 1 large drive instead of 3 separate ones.

6.      I tried to use the Disk Utility to create the RAID 0 arrangement.  (Somewhere in here, I had to install mdadm.)  Everything seemed to work until you restart the computer.  From this point, the RAID disappeared.  I also noted that drive 1 would mount in a crazy location and drives 2&3 would not automatically mount.  After noting that drive 1 did not mount automatically as well after another restart, I decided I was in over my head and decided to seek help.

The SWMBO is wondering why I am not using Windows after all of this but I am more hard headed than that.

So, to boil it all down, I am seeking help on how to ensure that my drives mount, create a RAID 0 configuration, and see this as 1 location to add my media files.  Any advice as to what I need to do to make this work?

Please keep it simple and/or concise (detailed is great) if possible.  I am new to the system and have been learning as I go!

Here is the hardware listing:
3 x Seagate Barracuda 7200.14 ST3000DM001 3TB 7200 RPM - OEM
1 x ASRock FM2A88X-ITX+ FM2+ / FM2 AMD A88X (Bolton D4)
1 x BitFenix Prodigy Arctic White Steel / Plastic Mini
1 x HyperX Blu 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1
1 x Kingston SSDNow V300 Series SV300S37A/120G 2.5" 12
1 x AMD A4-5300 Trinity 3.4GHz (3.6GHz Turbo) Socket F
1 x APEX AL-D500EXP 500W ATX12V Power Supply

---

### Post by chris218 on 2014-05-04
For now, it seems that it is resolved.  I used the Disk Utility to label the 3 drives as the array.  Next, I had to format the 3 drives.  Now it stays and is set in the launcher as expected.  I am transferring the first folder of files and will see how it goes from there.

---

