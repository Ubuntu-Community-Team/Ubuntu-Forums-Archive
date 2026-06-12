---
title: "How to downgrade to previous version of Ubuntu?"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by Trior27 on 2011-11-01
Hello.

I'm running Ubuntu 10.10. I'm considering to upgrade to the last version but I'm afraid that if something goes wrong, or I just don't like it, I won't be able to go back to 10.10 unless I install it again from scratch.

If I upgrade, is there any way I could downgrade keeping all the system settings, user permissions, etc. just as it was before upgrading?

I have a disc with Ubuntu 10.10 so I could just install it over again but if I do so, do I have to reinstall again all programs, change all settings and create all the users (and set their permissions) again?

Thanks for your time.

---

### Post by vicshrike on 2011-11-01
You have to reinstall if you do not like it. But try the live version from cd or usb before you upgrade.

---

### Post by pqwoerituytrueiwoq on 2011-11-01
if you have a separate /home partition you don't need to redo the account settings
apps will need to be reinstalled 
swap the hdd and run a test and see if you like it if you need some special driver otherwise go with a live cd

---

### Post by mahmoud.l on 2011-11-01
Try running it on VirutalBox and see if it suits you

---

### Post by shubham1 on 2011-11-01
> **Trior27 said:**
> Hello.

I'm running Ubuntu 10.10. I'm considering to upgrade to the last version but I'm afraid that if something goes wrong, or I just don't like it, I won't be able to go back to 10.10 unless I install it again from scratch.

If I upgrade, is there any way I could downgrade keeping all the system settings, user permissions, etc. just as it was before upgrading?

I have a disc with Ubuntu 10.10 so I could just install it over again but if I do so, do I have to reinstall again all programs, change all settings and create all the users (and set their permissions) again?

Thanks for your time.
i suggest as you are uing 10.10 wait for ubuntu 12.04 lts

---

### Post by little_penguin on 2011-11-01
What you could also do is make an image backup of your 10.10 partition with partimage from a live CD such as Parted Magic, and save it to an external drive. Then, install and experiment with the newer version and if you don't like it or it doesn't play nice with your hardware, you can restore the 10.10 partition from the partimage backup you made (again booting from a live CD) and everything will be back to how it was before.

---

### Post by TBABill on 2011-11-01
Copying some files from the home directory is pretty quick so unless you have majorly tweaked the system to be very different from original, it's not a great deal of time to invest to revert back by reinstalling 10.10. But its support runs out in 5 months anyway.

---

### Post by 11jmb on 2011-11-01
> **mahmoud.l said:**
> Try running it on VirutalBox and see if it suits you

+1

Or a separate partition if you have the space

---

### Post by Trior27 on 2011-11-08
Thanks for all the suggestions. :D

---

### Post by beew on 2011-11-09
> **little_penguin said:**
> What you could also do is make an image backup of your 10.10 partition with partimage from a live CD such as Parted Magic, and save it to an external drive. Then, install and experiment with the newer version and if you don't like it or it doesn't play nice with your hardware, you can restore the 10.10 partition from the partimage backup you made (again booting from a live CD) and everything will be back to how it was before.

PartImage??? It has been dead for quite a while, it has no ext4 support so it is pretty useless as most people have switched to ext4.

---

### Post by little_penguin on 2011-11-09
> **beew said:**
> PartImage??? It has been dead for quite a while, it has no ext4 support so it is pretty useless as most people have switched to ext4.

That's a valid point. For those like me still using ext3, yeah I know :) I'll probably switch to ext4 soon, partimage works fine. For ext4 they can use Clonezilla.

---

