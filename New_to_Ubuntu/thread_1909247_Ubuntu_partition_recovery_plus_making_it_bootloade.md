---
title: "Ubuntu partition recovery plus making it bootloader once again"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by freakontour on 2012-01-14
Ok so I will start from the beginning l have dual boot ubuntu 11.10 and windows xp .

I was trying to do my friend a favour by formatting his newly purchased HDD 750gb into FAT32 so he can use with his PS3. So the program I usually use is Swissknife V3 (using windows xp) which I've used multiple times with no issues this time when deleting partition so l was able to format to FAT32 the program crashed and l got the program encountered an error etc. click to send a report to microsoft blah blah blah! clicked ok but system was slow a sluggish so restarted machine on restart l arrowed down to the windows xp option therefore preventing the system from re-booting into ubuntu. When l hit enter on the windows option it came up with error no such partition then cam up with a long serial looking no. D2206.............. hit enter which took me back to the ubuntu option screen for booting into ubuntu, recovery, memory, windows xp etc. it was then l realised when in Swissknife l must have deleted the windows partition!!

So after some searching around l came across the testdisk program accessed through the terminal so followed that and re-booted as stated in the program. On re-boot l didn't get the ubuntu options this time on grub rescue>! 

obviously well peed off at this stage!! but thought my only option now is to use the Ubuntu 11.04 livecd which l downloaded when l initially installed ubuntu. I came across a post stating the terminal prompts using lilo and mbr which set the newly recovered windows partiton as the boot partition which to some degree lm happy to have restored that section. But now there are these partitions lised:

/dev/sda1    ntfs boot (the windows partition)
/dev/sda2(!) ext3
unallocated  unallocated
/dev/sda3    linux-swap

so my question is the ubuntu install with all its files must be on that unallocated section how can l recover and restore without altering the windows xp install and return back to being able to dual boot?

Please l would really like to get this sorted as it is so frustrating! ahhhhhhhhhhhhhhhhh

---

### Post by freakontour on 2012-01-15
Bit the bullet and just re-installed ubuntu 11.04 seemed to be the easiest fix!

---

