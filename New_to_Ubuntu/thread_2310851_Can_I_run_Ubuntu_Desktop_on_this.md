---
title: "Can I run Ubuntu Desktop on this?"
date: 2016-01-22
forum: New to Ubuntu
---

### Post by niranjan5 on 2016-01-22
Hello guys I am a biologist and I'm really really new to Ubuntu.

Our institute is going to buy one of the HP Proliant Rack servers with the following specs
1 TB RAM and 2TB x8 HDDs

If I install Ubuntu 14.04 LTS 'Desktop' on this, will I have access to all my 16TB disk space and 1TB RAM? I basically need a GUI so I don't want to install Ubuntu 'Server'.

---

### Post by Vladlenin5000 on 2016-01-22
Hi and welcome.

You can install Ubuntu server and then easily add the desktop environment of your choice. If you want Unity as found in the standard Ubuntu (desktop) just do:
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
Done! :p

Actually I would strongly recommend using the server installation media because it has support for the most common RAID controllers found in corporative servers like your Proliant. The regular Ubuntu desktop does not.

---

### Post by niranjan5 on 2016-01-22
Ya I read about this :)

So you recommend installing server then getting the desktop update.

Thank you!

Now I just need to search how to install internet on the machine and I'm all set.

Should I stick with the current 15.10 server release or install 14.04 LTS? Extended support till 2019 is always preferred i guess.

---

### Post by Vladlenin5000 on 2016-01-22
You're welcome.

Install internet???? It's a rack server with one or more Ethernet ports/devices which are natively supported. Just plug in the cable and you're good to go.

LTS releases are generally preferred but you can install either. The only difference is with 15.10 you will need to upgrade sooner than later to 16.04 which is also a LTS release. You can also upgrade 14.04 LTS directly to the aforementioned next LTS but you don't have to (until 2019).

---

### Post by grahammechanical on 2016-01-22
Do Ubuntu desktop editions and server editions have different Linux kernels? I do not think so.

> How much RAM memory can Ubuntu 12.04LTS address?

> Its the architecture of the kernel. The release is irrelevant.


 32bit Ubuntu can access up to 3.4Gb
32bit Ubuntu + PAE can access to 64Gb RAM
64bit Ubuntu up to 4Eb but in real world it's going to be about 1Tb...




[https://answers.launchpad.net/ubuntu/+source/ubiquity/+question/200916](https://answers.launchpad.net/ubuntu/+source/ubiquity/+question/200916)

As for disk size then it is the difference between MBR partitioning and GPT partitioning.

> The widespread [MBR]("https://en.wikipedia.org/wiki/Master_boot_record")  partitioning scheme, dating from the early 1980s, imposed limitations  that affect the use of modern hardware. One of the main limitations is  the usage of 32 bits for storing block addresses and quantity  information. For hard disks with 512-byte sectors, the MBR partition  table entries allow up to a maximum of 2 [TiB]("https://en.wikipedia.org/wiki/Tebibyte") (2[SUP]32[/SUP] × 512 [bytes]("https://en.wikipedia.org/wiki/Byte")).[SUP][/SUP]

> [Intel]("https://en.wikipedia.org/wiki/Intel") therefore developed a new partition table format in the late 1990s as part of what eventually became [UEFI]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"). As of 2010, GPT forms a subset of the UEFI specification.[SUP][[2]]("https://en.wikipedia.org/wiki/GUID_Partition_Table#cite_note-2")[/SUP] GPT allocates 64 bits for logical block addresses, therefore allowing a maximum disk size of 2[SUP]64[/SUP] sectors. For disks with 512-byte sectors, maximum size is 9.4 [ZB]("https://en.wikipedia.org/wiki/Zettabyte") (9.4 × 10[SUP]21[/SUP] bytes) or 8 [ZiB]("https://en.wikipedia.org/wiki/ZiB") (9,444,732,965,739,290,427,392 bytes, coming from 18,446,744,073,709,551,616 (2[SUP]64[/SUP]) sectors × 512 (2[SUP]9[/SUP]) bytes per sector)[SUP].[/SUP][SUP][/SUP][SUP][/SUP]



[URL="https://en.wikipedia.org/wiki/GUID_Partition_Table"]https://en.wikipedia.org/wiki/GUID_Partition_Table

[/URL]In other words, make sure that you use a GUID partition table (GPT) for the disks

Regards

---

### Post by mörgæs on 2016-01-22
A server normally has a weak graphics card. Take a look at it before installing; you might be better off with a lighter Buntu.

---

