---
title: "Kinit problem at first boot"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Harmony_Of_Distortion on 2008-06-15
Hello! I have already installed ubuntu 7.10 and I have a problem when the ubuntu boots for first time.

The following message shows up:

Kinit: name_to_dev_t(/dev/sda5)
Kinit: trying to resume from /dev/sda5
Kinit: No resume image, doing normal boot

some times it stucks at battery checking.... and others at this message and a login prompt shows up.

I have disabled bluetooth services via terminal and Anachronistic Cron Anacron because when the system trying to start these services stucks. 

I can boot in recovery mode with GUI but when I trying to boot in normal mode the GUI dosen't start. Some times it seems to be loading normal because of the flashes on the screen but nothing.

Many others has the same problem and I have try already their solutions but nothing.

I have a Core2Duo 1.83, 1GB Ram, 80GM HD, Intel 945 GM graphics card (on board 128MB shared memory). 

If enyone can help me pleaaaaase.!!!!:confused:

---

### Post by joshsmith on 2008-06-15
Kinit: name_to_dev_t(/dev/sda5)
Kinit: trying to resume from /dev/sda5
Kinit: No resume image, doing normal boot

just means it is seeing if it has been started up after doing a suspend, and then it finds it hasnt. so this is nothing to worry about

if you can, try ubuntu hardy heron 8.04

---

