---
title: "Pre boot errors - where are they logged?"
date: 2015-01-13
forum: New to Ubuntu
---

### Post by Alex_Botev on 2015-01-13
Hi, I'm new to Ubuntu and still am on a learning curve.
I have a 14.04, now successfully updated to 3.17-utopy kernel.
When my laptop boots, I see for a very short time a few errors coming up before the login screen. I do want to check them out and possible fix, but its so fast I can't see anything and I do not know where are they logged. Was wondering if anyone can help me with that.

---

### Post by slickymaster on 2015-01-13
**/var/log/** is the directory that you're looking for.

I would say that you ought to see **/var/log/boot.log **(system boot log) and **/var/log/dmesg** (kernel ring buffer)

---

### Post by plucky on 2015-01-13
> **Alex_Botev said:**
> Hi, I'm new to Ubuntu and still am on a learning curve.
I have a 14.04, now successfully updated to 3.17-utopy kernel.
When my laptop boots, I see for a very short time a few errors coming up before the login screen. I do want to check them out and possible fix, but its so fast I can't see anything and I do not know where are they logged. Was wondering if anyone can help me with that.

Open a terminal and type ```
dmesg
```

Also try ```
cd /var/log
ls
``` is where all the system log files can be found.

Good Luck

---

### Post by fantab on 2015-01-14
+1 for both posts above.

Since you see 'errors' at boot, you can disable the splash screen and check what errors show up at boot.
You can edit /etc/default/grub file to edit the following line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
and change it to:
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

---

### Post by Alex_Botev on 2015-01-14
Thanks guys for the good answers. It turned out its my iwlwifi complaining that it does not have -9 or -10 version driver (since I downgraded it to -8 because of this bug([https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1289961](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1289961)) and personally seeing big improvement in speeds with -8 in comparison with the rest) .
Just for any new to say that to get the fantab solution working you need to also do sudo update-grub2 before rebooting.

---

### Post by fantab on 2015-01-14
> **Alex_Botev said:**
> 
Just for any new to say that to get the fantab solution working you need to also do sudo update-grub2 before rebooting.

Yes, I forgot to mention that. My bad.

```
sudo update-grub
```

---

