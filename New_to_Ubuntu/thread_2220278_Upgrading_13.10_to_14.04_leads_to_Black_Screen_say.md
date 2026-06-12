---
title: "Upgrading 13.10 to 14.04 leads to Black Screen saying &quot;Asking for cache data failed&quot;"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by foster4 on 2014-04-27
Hello,

I was running Ubuntu Gnome 13.10 and I thought it was time to upgrade to 14.04, so I entered "do-release-upgrade" into the terminal and everything seemed to progress normally, until my desktop was replaced with a black screen only containing something like 

[3256.362200] sd 5:0:0:0: [sdb] Asking for cache data failed 
[3256.362200] sd 5:0:0:0: [sdb] Assuming drive cache : write through

and this went into an infinite loop, with only the starting numbers counting up. I tried to wait it out, but since nothing happened anymore, I couldn't get away from this screen without rebooting. Ubuntu still boots, but then it only resumes this infinite loop. 

I've upgraded Ubuntu numerous times over the years, but this is the first time something like this happens during a switch to a newer release. 

Has anyone any ideas what's going on? 

Thanks for any help/tips!

---

### Post by moshefeit on 2014-04-27
[SIZE=4][B]What do the Asking for cache data failed and Assuming Drive Cache: write-through messages mean?
[/B][/SIZE]
[LIST]
[*]    Hard disks have a small amount of RAM cache to speed up write operations. The system can write a chunk of data to the disk cache without actually waiting for it to be written to the disk. This is sometimes called "write-back" mode.
[LIST]
[*]If there is no cache on the disk, data is directly written to it in "write-through" mode. 
[/LIST]
  
[*]The Asking for cache data failed warning usually occurs with devices such as USB flash drives, USB card readers, etc. which present themselves as SCSI devices to the system (sdX), but have no cache.
[LIST]
[*]The system asks the device: "Do you have a cache?" and gets no response. So it assumes there is no cache and puts it in "write-through" mode. 
[/LIST]
   
[/LIST]

---

### Post by moshefeit on 2014-04-27
go here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/925760](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/925760)

---

### Post by foster4 on 2014-04-27
Yes, I kinda looked that up before asking my question. Sadly it doesn't help me at all. My problem isn't primarily that this message appeared. It's that it appeared during the system upgrade and now that's all my system still does. It obviously won't finish the upgrade anymore and I also can't use the OS installation anymore. 

So my installation is irreparably broken now? This didn't happen to anyone else? 

I've been using Ubuntu on that exact same computer for years and this message never showed. Wonder what the cause might be.

---

