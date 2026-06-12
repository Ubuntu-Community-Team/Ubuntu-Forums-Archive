---
title: "RAID 1 query on a new NAS box"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by devonps on 2008-06-25
Hi all,

I've just built my first NAS box using UBUNTU 8.04 server edition with a RAID 1 partion using x2 Samsung 500gb SATA drives.

I should add that I'm a beginner with both Ubuntu and Networks, so bear with me.

I followed one of the many guides on the net that walked me through the process of creating a RAID 1 array along with a fresh install of an Ubuntu server. Everything went well, apps installed, users setup, etc.

Now the guide told me that I had to reboot using my server installation disk and use GRUB so that I could boot from both disks, incase the 1st disk failed.

I tried this but kept getting Error 15: file not found when I was using the command device (hd0) /dev/sda. After much frustration I decided to reboot my server and allow it to perform a normal start.

The server is up and running happily, i.e. I can log onto the console and execute commands.

My question is:

1. Given my previous error, how do I know that my RAID 1 array is functioning correctly?, i.e. what commands can I use?

2. Why did I get the GRUB error message?


Thanks in advance,

Steve.


P.S. I'm currently at work and cannot access my server.

---

