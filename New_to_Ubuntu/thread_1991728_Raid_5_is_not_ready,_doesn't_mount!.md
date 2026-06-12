---
title: "Raid 5 is not ready, doesn't mount!"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by whitethunder on 2012-05-30
Hi, 

I have a RAID 5 file server running ubuntu. One of the harddisks was disconnected and I accidentally turned on the machine. It booted up but the RAID was not mounted. Since then, when I boot up, I get a message saying: 

[B]the disk drive for /media/RAID is not ready yet or not present. 
Continue to wait; or Press S to skip mounting or M for manual recovery[/B]


I have waited for days with the hope that this fixes itself. but it hasen't. 

If I press "s" it will run ubuntu but will not mount the RAID. If I run "Disk Utility" (GUI) then, I see that ubuntu sees the harddrives, all four of them. When I click on the raid array right below "volums" it says "RAID array is not running". If I click on "Check Array", it says, "

[B]Error checking RAID Array
An error occured while performing and operation on "0.0 KB RAID-5 Array" (0.0 KB RAID Array): The operation Failed. [/B]

If I click on "details" it says: 

[B]Error checking array: Helper exited with exit code 1: device /dev/md0 is not idle. 
[/B]

Can anybody help with this? 


Many thanks.

---

### Post by whitethunder on 2012-05-30
I don't think my ubuntu version matters but I am using 10.04 Lucid Lynx.

---

