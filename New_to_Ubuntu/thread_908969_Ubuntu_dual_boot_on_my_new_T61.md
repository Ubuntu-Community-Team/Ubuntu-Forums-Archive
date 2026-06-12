---
title: "Ubuntu dual boot on my new T61"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by kvorion on 2008-09-03
I just got a new T61 which has windows vista installed on it. I want to install ubuntu on this as my primary operating system. For warranty purposes, I do not want to remove the vista OS that came on this machine. Hence the dual boot requirement. I have been using linux on my desktop machine on and off for several years now but this is the first time I have a vista OS on my machine.

My current situation is the following:

I have two partitions:
1. Some recovery partition provided by lenovo
2. C drive which has windows vista.

I could resize the partition that has vista and install ubuntu on the free space that gets created.

Before I do that, I want to somehow make sure that if I screw up, I dont lose what I have currently. The recovery partition is not visible in vista but I could see it when I booted using the ubuntu live CD. How do I do this backup?

What is the best way to proceed? I have a gparted live cd that I plan to use.

---

### Post by nvikram on 2008-09-03
Before starting, I would recommend you perform a backup of important files and also a defrag.

In windows vista...
1. Click on the start menu
2. Right click on the computer button
3. Select Manage
4. On the left side find "Disk Management"
5. You should see two partitions, your recovery and your main.
6. Find the main one (usually will say C: )
7. Right Click and then say "shrink volume"
8. Enter the amount you want to shrink it by.
9. Wait Patiently for windows to do its thing
10. Shutdown.

Boot up the Ubuntu Live CD...
1. Once you hit the desktop, click on install.
2. When you get to the partition manager, see if you can see the unallocated space that you just made.
3. If not, select, Use "largest contiguous free space."
4. Proceed with install
5. Enjoy!

---

