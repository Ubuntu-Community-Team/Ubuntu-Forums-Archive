---
title: "Changed drive to LVM and now can't access data"
date: 2014-06-20
forum: New to Ubuntu
---

### Post by duan-d-dutoit on 2014-06-20
Good day

I seriously messed up. I was trying out Ubuntu 14.04 LTS and wanted to install it over my existing Ubuntu installation. However, when I noticed that the upgrade option was greyed out, I tried to install it using the "something else" option. I deleted my existing Ubuntu partition but somehow changed my other partition (with all my data on it) to LVM and t then exited the installer. Now, when I boot into Live Ubuntu (since my existing Ubuntu installation is now deleted) I cannot access my other partition with all my data on it. I can see that the partition still exists (in gparted) but how do I now change it back to a normal accessible partition?

---

### Post by nerdtron on 2014-06-20
You exited the installer after changing the partitions to LVM? And did you applied the settings after changing it? I won't get your hopes up but most likely that you drive is wiped/formatted. If you want to change it back you will need to format it again (losing you data).

---

### Post by duan-d-dutoit on 2014-06-21
Hi nerdtron

Thank you for the reply!

I haven't selected formatting and if I follow the steps on at this link: [http://dannytsang.co.uk/mounting-lvm-using-ubuntu-live-cd/](http://dannytsang.co.uk/mounting-lvm-using-ubuntu-live-cd/) I can see the data on my one partition which had the Ubuntu installation on it (/sda1)  However, I can't find a way to display the data from the other partition (/sda5). I' m almost certain the data is still available but I cannot access it in any way. Gparted shows that the partition is flagged as lvm.

---

### Post by duan-d-dutoit on 2014-06-23
Hi

I fixed it.  I used TestDisk and analysed the disk, then viewed and copied the files (as a failsafe) and then I restored the partition.  Worked perfectly well!

Thanks for the assistance.  I hope this will help others in need as well.  :-)

---

