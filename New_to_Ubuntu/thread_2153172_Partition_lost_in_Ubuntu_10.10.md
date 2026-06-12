---
title: "Partition lost in Ubuntu 10.10"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by e46m3 on 2013-06-10
Guys, 

I was using Ubuntu 10.10 till yesterday. I had been noticing a weird problem with it, for past few days, my wireless keyboard would not work, so I connected my old school PS2 keyboard to desktop which used to work. Lately that also started malfunctioning, it would not type the "e" and "m" keys. Instead, on pressing the "e" key, it would activate compiz and show me the four workspaces that were available to use and the "m" key used to go to the top right status bar and ask if "Set up chat account" etc since I had not done it already. I pulled my hair out over it and could not understand what was wrong, so decided to do a fresh install of 10.10 which I had on CD.

Now, here's the twist; I have two hard drives, 160GB and 500GB each with four partitions. Ubuntu was installed on 500gb drive with partitions, now when I tried to re-install it, I see only one drive in the installer of 500gb ! So essentially, all my data on the split drives has been lost ? I can very well see the four partitions on 160gb drive. Another thing, even while trying to re-install ubuntu, the wireless keyboard would not work and wired keyboard would have non functional keys. So I had tough time even typing preferences while installation. To clarify if it was an issue with motherboard with onboard USB and PS2 ports, I did a Windows XP install. Windows installed successfully (I am typing from it right now) but it does not show my 500gb HDD at all in the environment. I guess, that's because it is not formatted to NTFS or FAT32 file system but ext2/3 which supports Ubuntu. My biggest concern is to recover the data and partitions if I can from that 500gb HDD ! I had some images from my travels across countries, understanding that 4 partitions can not crash at once !

Can anyone please help !

Thanks, 

RJK

---

### Post by Squalo71 on 2013-06-10
You can try with testdisk to find the "lost" partitions. Use a live cd to do it.

---

### Post by dino99 on 2013-06-10
you might load gparted to know about that "missing" partition: if something is not as it should, gparted will display a warning

---

### Post by e46m3 on 2013-06-10
Thanks for your quick replies, guys. I will try as you guys suggested, however I must add, that the partitions in 500gb were as 280gb,80gb,60gb,60gb; totalling to 500gb. I forgot to add that ubuntu shows one disk of 500gb of which 470gb is free, so that's still 30gb of data occupied on it. I definitely had data more than 30gb on it though. Neverthless, I will try to boot using ubuntu 10.10 cd and should I "try Ubuntu" or "Install Ubuntu'" when I get the options ?

---

### Post by claracc on 2013-06-10
You have to "try ubuntu" and then launch the partitions editor gparted.

I am afraid that when you have reinstalled ubuntu you have wiped your 500 GB hard drive and the partitions where you had your data.

---

### Post by oldfred on 2013-06-10
If you installed over your system even that testdisk may see old partitions, it may not see all the data if file structures were overwritten. If structures are there at least some of the data was overwritten and that may provide issues. 
But best to see what testdisk sees.

       [URL="https://help.ubuntu.com/community/DataRecovery#Lost%20Partition"]https://help.ubuntu.com/community/DataRecovery#Lost%20Partition
[/URL]
 repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Also any partitioning by Windows during a Windows install may corrupt partition table as Windows does not see Linux partitions. Best to only use Windows internal partition tools to shrink a NTFS partition and use gparted for all other partition activity. Some of the third party Windows partition tools also recognize Linux partitions.


[URL="https://help.ubuntu.com/community/DataRecovery#Lost%20Partition"]
[/URL]

---

