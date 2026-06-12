---
title: "Dualboot on mac - small problem"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by hyalinus on 2013-01-17
Hi
I'm new to ubuntu but i want to give it a more realistic try after playing aroundt with the liveCD.
I want to dualboot on my mac from mid 2010. Its intel and running OS 10.7.5 
I have been following the guide at
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

After i have booted the liveCD and want to install the guid and the pictures on my screen don't match anymore. The guide must be for another distro.
I have createde to extra partitions. One EXT4 for install and a 2 gb linux swap.

When i want to install i have 3 options.
1: only ubuntu install
2. Both Mac OS and ubuntu
3: Another

I have tried both 2 and 3. 
When I use the "another" i set the ext4 partition at my install partition and set it at root (/). When i press install im asked to create a "bios....." partition on at least 1 mb. I thought that the rEFIt was my boot software. How to i create a bios partition?
I have tried to continue the install without the bios ... partition. 
When my mac boot up i chose ubuntu and the it freezes and don't boot into ubuntu.

When i tried the both mac and ubuntu install i was not giving many options. But afte install it still didn't work. When open gparted from the liveCD after this install i could se a bios partition.

Has the ubuntu installer on the liveCD become independent of rEFIt. Would i help uninstall rEFIt, the undo my partitions and expand the macOS partition to the whole disk. The boot the liveCD and install the both Mac OS and ubuntu option.

I hope that you are able to help me otherwise i must give up ubuntu :-(

---

### Post by d4m1r on 2013-01-17
1) Model of Mac? Specs?

2) The second install option should have been the correct one. In that case, you should have only needed 3 partitions on your HDD, a small (100mb?) one OS X uses for recovery, your main OS X partition, and then an unformated partition for your Ubuntu install. You would get to format this partition into EXT4 format as part of the Ubuntu install process.

Hope this helps.

---

