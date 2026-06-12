---
title: "Grub rescue..."
date: 2015-01-26
forum: New to Ubuntu
---

### Post by mohamed13 on 2015-01-26
Good Evening,
I have a hard drive 500 G.
I use the Windows 7 CD to create two partitions, 200 G each, one for the system and the other for data.
Then I inserted the CD Ubuntu 14.04.1. In the remaining 100 G, I created a SWAP partition 5 G, and Ubuntu in the rest of Hard Drive. The GRUB I installed it on sda.
The installation went smoothly.
When I start the computer, this message appears:

```
error no such partition
Reviews entering rescue mode ...
grub rescue
```



So I checked the order of the BOOT: HD and CD and USB. The problem persists.
So every time at startup I press f12 to display the list to boot, then I choose HDD, and then the GRUB displays.
How to solve this problem? Get to GRUB without having to go through the stage of BOOT.
Thank you for helping me solve the problem ;)

---

### Post by ibjsb4 on 2015-01-27
Well something went wrong, just not sure what.
I wonder if boot-repair would do any good.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Lalaith on 2015-01-28
Hi mohamed13, 

i had a similar problem a week ago, and surfed a bit the net to find solutions. You could try to access Ubuntu following the steps of this thread:
[http://askubuntu.com/questions/192621/grub-rescue-prompt-repair-grub](http://askubuntu.com/questions/192621/grub-rescue-prompt-repair-grub)
(it seems that Grub rescue only accepts 4 commands. If setting grub rescue to (hd0,msdos6) complains, type "ls" to see what file systems do you have).


And from ubuntu, try to either install Grub again, update it or run Boot-Repair as suggested by ibjsb4.

---

