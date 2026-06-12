---
title: "Unmounting a portable MP3 player?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by shatteredmindofbob on 2008-10-12
I recently picked up an old Philips GoGear which worked reasonably well right away except it doesn't mount as mass storage device, or well, anything for that matter. 

This didn't bother me at first since I could access it using Amarok's MTP transfer setting.

However, after first transferring some songs to it and disconnecting, I was unable to plug it in without crashing Amarok or anything else that uses the MTP protocol. 

Turns out I messed it up by not unmounting before pulling out the plug. After getting a hold of a Windows computer and reformatting it, it worked fine. I made sure to click "Disconnect" in Amarok after finishing transfer, pulled the plug, checked that the songs were there (they were) then plugged it back...only to have Amarok crash and put me right back where I started. 

So, with Ubuntu not recognizing this as a drive, how on earth do I unmount it safely? 

Thanks.

---

### Post by jordilin on 2008-10-12
check the /var/log/messages log when you connect the device and paste what you can see in that log regarding that device.

---

### Post by sumguy231 on 2008-10-12
Under the devices tab in Amarok, click the configure button at the top. Under 'post-disconnect command' try eject %d as well as umount %d. Amarok should automatically replace %d with the unknown name of the device.

---

### Post by shatteredmindofbob on 2008-10-12
> **sumguy231 said:**
> Under the devices tab in Amarok, click the configure button at the top. Under 'post-disconnect command' try eject %d as well as umount %d. Amarok should automatically replace %d with the unknown name of the device.

Unmount %d gives me an error, though eject %d seems to do the trick...while ejecting my CD drive at the same time. Strange. 

Either way, it works now. Thanks.

---

### Post by sumguy231 on 2008-10-12
You're welcome. BTW, you did type 'umount' and not 'unmount', right? As odd as it may seem, that's not a typo. I know you consider it fixed, but that might keep your CD drive from ejecting at the same time.

---

