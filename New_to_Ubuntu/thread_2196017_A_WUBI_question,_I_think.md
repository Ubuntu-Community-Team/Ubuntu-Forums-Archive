---
title: "A WUBI question, I think"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by lesliek2 on 2013-12-27
If not, where?

---

### Post by QIII on 2013-12-27
Of course!

Ask away!

---

### Post by lesliek2 on 2013-12-27
I have an old laptop with Windows XP on it. Using WUBI, I installed Ubuntu 12.04 when it first came out and used the Ubuntu side of the computer exclusively afterwards. Nowadays, I sometimes turn the laptop on to access old files. A few days ago, I decided to update the Ubuntu installation. That led to my updating the kernel from 3.2.0-52-generic to 3.2.0-57-generic.

Today, I wanted to look at an old file on the laptop, but couldn't boot up in Ubuntu. After much toing and froing, I realised that the boot-up program was looking for a file with 52 in its name when it should have been looking for one with 57 in its name. I therefore ran the boot-up program again and was able to edit a couple of lines containing 52 so that they said 57. Then Ubuntu booted.

I shut the laptop down and tried to re-boot, but discovered that my editing of the two lines hadn't been permanent.

How do I edit the relevant lines so that they say 57 permanently?

---

### Post by oldfred on 2013-12-27
I do not know wubi, not many in forum do.
Have you tried?
sudo update-grub

And wubi is being discontinued as it does not work with gpt partitioning which all new UEFI systems use. So new uses with Windows 8 cannot use it.
It is just a large file inside the Windows NTFS partition. If you are using Ubuntu most of the time it may be time to upgrade to a full install to a partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

### Post by QIII on 2013-12-27
Threads merged.

---

### Post by lesliek2 on 2013-12-28
Thank you for your reply, oldfred.

Your reference to update-grub was what I needed to jog my memory and I can now boot up in Ubuntu again on my old laptop without any problem.

As to migrating: I did that on my current laptop, having also begun to use Ubuntu on it through WUBI, but didn't bother to do it on my old laptop because I turn it on so infrequently. I suppose the time has now though.

Thanks again,

Leslie

---

