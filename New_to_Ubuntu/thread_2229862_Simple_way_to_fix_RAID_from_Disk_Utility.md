---
title: "Simple way to fix RAID from Disk Utility"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by Nagle75 on 2014-06-15
We had a brown out today & it messed up my RAID configuration. I know that there's a simple way to fix it through the "Disk Utility" gui, (because I had a friend help me do it previously), but I can't remember how to do it. I thought that it was as simple as clicking "Check & repair the array", but when I did that, nothing happened. Then I unmounted the partition & tried again & it asked me for a password, (I know I had the right password) which I did & then it did nothing. I thought I remembered a command to check whether the array was resyncing: cat /proc/mdstat ? but all it does, is show me that the array is still degraded.
nagel@nagel-G41D3:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[2]
      976759865 blocks super 1.2 [2/1] [U_]
      
unused devices: <none>

---

