---
title: "[SOLVED] Partition Suggestions??"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by birddog165 on 2008-06-25
I want to know what is the rule of thumb for partitioning a hdd that will be solely dedicated to running Ubuntu?

I'm looking partitioning off a 250GB hdd cause that's what I've got.

---

### Post by Elfy on 2008-06-25
I would use a partition for / no bigger than 10Gb, you're swap depends on whether you need to hibernate in which case it should equal you're RAM. I have swap of 1Gb with 1Gb RAM but rarely use it all - virtual machine use would take it though. 

Certainly no more than 4Gb in total between RAM and swap unless you have 64 bit

The remaining space can be put to /home which will be used for your data and config files.

---

### Post by bumanie on 2008-06-25
It is mandatory to have a / and a swap, but it is a good idea to have a separate /home partition as well. This way, if something happens to the filesystem, you can reinstall to / and all your data in /home is safe. Suggest / - 10gb, swap 1-2gb and /home as large as you like. To achieve this setup, you need to choose manual at the partitioning stage of the install.

---

### Post by timcredible on 2008-06-25
> **forestpixie2 said:**
> I would use a partition for / no bigger than 10Gb, you're swap depends on whether you need to hibernate in which case it should equal you're RAM. I have swap of 1Gb with 1Gb RAM but rarely use it all - virtual machine use would take it though. 

Certainly no more than 4Gb in total between RAM and swap unless you have 64 bit

The remaining space can be put to /home which will be used for your data and config files.

ditto

---

