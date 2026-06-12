---
title: "[SOLVED] How to remove Mint and re-partition?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by germanix on 2008-10-02
I currently have both Ubuntu as well as Linux Mint installed as a dual-boot. This was done to try out both before deciding which distro I like more. I have now decided to remove Mint and to use Ubuntu as my sole OS.
Currently my HD looks like this: (output GParted)

/dev/sda1 ext3 145GiB used 3.7 unused 141GiB Boot
/dev/sda2 extended 153GiB
/dev/sda6 ext3 141GiB used 4.3 unused 137
/dev/sda7 swap 5.8
/dev/sda5 swap 5.8

AS Mint was installed first, I assume that sda1 is where Mint is located. I would like to de-install Mint and possibly re-partition? I will only have Ubuntu on the drive, would however like to have a separate partition for my Home File. I do not have the slightest idea how to do this, apart from doing a new install of Ubuntu and telling it to use the whole drive. I was wondering if there is another way to do this, without having to new install, by either using  something like GParted or the Terminal. Any help or ideas will be appreciated.

---

### Post by spiderbatdad on 2008-10-02
yes. try a gparted live cd. 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by bumanie on 2008-10-02
Unfortunately, there is no 'standard' way to tackle this issue, so I will give you my personal preference. As you are only going to have one distro, ie ubuntu, I would do a complete format and reinstall and get rid of the extended partition you have. Although linux will happily boot from within an extended partition, I personally think that extended partitions can be limiting when ones main OS is contained within one. I would back up any data you have that is important and then proceed as follows:
1) Format the whole drive to ext3 with gparted
2) Boot with live cd and choose to install ubuntu.
3) At the partitioing stage choose manual
4) Make three partitions - first  / of 10gb
                           second /home as large as you like
                           third  /swap 1-2gb
Others may have a different idea of how to do it, as there are a number of ways one could tackle this - so wait for some more answers and decide which one you prefer. With a bit of mucking around, you could achieve this without reinstalling at (ie copying partitions to external drives, re-partitoing, re-copying the partitions etc), but I think that would be more difficult and take a lot more time.

---

