---
title: "Trouble with Wake-on-Lan (network adapter stays off?)"
date: 2018-07-23
forum: New to Ubuntu
---

### Post by nicholas.l.arnold on 2018-07-23
Hello,

I'd like to be able to start my new Ubuntu file server remotely, but WoL is giving me a lot of trouble.  

I know my motherboard supports it, I enabled it in the BIOS, ethtool shows "Wake-on: g", the magic packet reaches the server (when it's on), yet once I turn it off and try, nothing happens.

I read in a few old posts that said I might have to instruct the system not to turn off the network adapter when it powers down, but the instructions I saw seem outdated -- they want me to change files which don't exist and use commands which I know are deprecated.

Do I still have to tell the system to maintain power to the networking hardware, and if so, how can I do that on Ubuntu 18.04?

Additionally -- do I have to send the wake message on a particular port, and how do I know what that is?

---

### Post by vidtek on 2018-08-26
Nicholas-  I too am struggling with wol on 18.04.  I have it working on a slave mythtv machine using old hardware but my main machine stubbornly refuses to do it.

The machine on which it works is an old Gigabyte Z68 with internal nic.  This is running dual-boot Windows 8.1 with MCE and Kubuntu 18.04.  This machine is configured mainly as a mythtv slave backend. It uses ext4 format for the separate system and home partitions.

The machine with which I am having trouble is my main desktop, an Asus Strix ROG Z270E with internal nic's.  This machine dual-boots windows 10 and Kubuntu 18.04  Both machines are using Intel i7 processors with 16gb ram.  Both machines use UEFI bios's.  This machine is using btrfs for system and home partitions, that is the only difference between the two systems.

I very rarely boot into windows on either machine.

I have spent several (rainy) days trying to get this to work and have failed miserably.

At the moment I am struggling with the various systemctl commands for shutting the machine down, trying hybrid-sleep and hibernate, but having no success.

If you get it going, can you post your steps on here please?

Cheers, Tony.

---

