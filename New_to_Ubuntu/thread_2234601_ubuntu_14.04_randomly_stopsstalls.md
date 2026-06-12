---
title: "ubuntu 14.04 randomly stops/stalls"
date: 2014-07-15
forum: New to Ubuntu
---

### Post by vivace on 2014-07-15
Hi

for the past month or so...seems like around the time i upgraded to 14.04 i have been having the most annoying glitches with my ubuntu os. it just kind of stops and becomes unstable and i have to reboot. Lately its been happening multiple times a day and really driving me nuts so i need to find a solution. 

my first thought was that i was running out of disk space. I have a 60 gb sda primary ssd for ubuntu and it was running kind of low so i freed up about 16 gigs but that didnt solve it. Then i thought maybe its because i have been incrementally upgrading ubuntu to the latest version since 2010 and maybe it just needs a fresh start. 

I have an 80 gb ssd with windows 7 sdb which i never use. My idea was to leave my working sda untouched and to just do a fresh install of ubuntu 14.04 on sdb. Then when i get too frustrated with the os stopping and have to reboot i can port my work over to the new os....and when i dont feel like it just work in the old environment .... 

so i created a boot usb but found that all of the precooked options were "delete windows 7 and ubuntu and install ubuntu" or "reinstall ubuntu". since i wanted to just delete windows and install ubuntu i clicked other. This is where i got very confused. what i saw was both hard drives listed and their partitions. It seemed as if it was asking me to reformat them. What happens if i dont select one? will it get nuked? I imagine it might work like this--i can select the windows partitions to be reformated but that really doesnt leave me with a good guess as to what happens next when i click "install now". Will only the windows drive get touched?? 

thanks very much...also if theres an easier solution to any of this i would love to hear it.

---

### Post by FormatSeize on 2014-07-15
If you choose nothing when you are trying to install Ubuntu to a partition, nothing will happen. You must choose something in order for the install to continue on the chosen disk/partition. 

If you want to nuke a disk or partition, the choice is yours. If you want to blow away everything, feel free, but I don't really think that wiping disks and starting over is the real solution to the problem that you are having. In other words, the root of the problem probably has little to do with having a fresh install versus a not-fresh install. 

I guess that it's only fair that I mention that completely wiping a disk and then installing fresh has worked for me in the past, but I know that the root of the problem turned out to be a firmware issue (wiping the disk wiped the firmware, which alleviated the issue I was having). But at the same time, I have to say that it wasn't Ubuntu I was dealing with. 

All in all, make a backup, then try it and see what happens if you are so brave.

---

### Post by vivace on 2014-07-15
well the problem seems to be somewhat related to playing music...it sometimes freezes without music but definitely when i have music on it seems to freeze much sooner. Its not really matter of bravery...its just that i dont know what else to do. The system seems corrupt. Curious about the firm ware issue you had? Come to think of it my problems might have started around the time i got this wireless logitech trackpad....hmmm

---

