---
title: "recovery Win7 recovery partition to new drive from failed hard disk"
date: 2014-05-30
forum: New to Ubuntu
---

### Post by Andrew_Benjamin on 2014-05-30
My wife's out of warranty Dell laptop just suffered a hard disk failure.  It has on it a Windows 7 recovery partition which wipes the disk and sets it to the factory fresh state.

I have a new, equal size drive and would like to get that partition restored to the new drive and hopefully be able to say 'voila' and bring the machine back to life.

I don't have a 2.5" external hard drive caddy, but I do have several external USB drives.

I have tried to run Clonezilla on the drive, but it gives lots of errors and I'm not sure whether it has been successful or not; while I will try to restore to the new drive and hope, here's my question:

Can someone suggest a secondary alternative to restore the hidden Dell/Win7 recovery partition which will allow me to trigger the wipe/install process via the F8 key on boot? I'm looking for other tools (like ddrescue (?)) which might try to spend a little more time grabbing good data.

If I get the (I think) /dev/sda1 partition, I should be good.


Andrew


Thanks all.

---

### Post by stalkingwolf on 2014-05-30
you might try using the hdd regen on this disk.   [www.hiren.info/pages/bootcd]("www.hiren.info/pages/bootcd")  i have used it many times to regen drives and a couple times it held long enough for me to mine the data.

---

