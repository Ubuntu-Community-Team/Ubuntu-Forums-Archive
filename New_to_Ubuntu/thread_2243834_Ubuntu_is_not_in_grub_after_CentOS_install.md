---
title: "Ubuntu is not in grub after CentOS install"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by Pelvur on 2014-09-11
Hello!

I have Ubuntu 14.04 installed. I have decided to add two other distros, CentOS and OpenSUSE. During CentOS installation, I have chosen to shrink Ubuntu partition and install CentOS there. After installation, grub only shows CentOS anf no Ubuntu, however I belive all the files are there. I guess I damaged/overwritten bootloader and it needs to be repaired, but I don't know how. Can anyone here help me?

Also, after I repair bootloader (I hope I will be able to do that), how do I install openSUSE and avoid those problems? would preparing partition in advance (e.g. using GParted) help? 

Thanks.

---

### Post by deadflowr on 2014-09-11
I'm not sure, but does CentOS include the package, os-prober?

I don't run CentOS, so don't know how to find packages on an rpm system, but a quick ad-hoc way would be to see it os-prober is listed in the grub.d folder.
something like
```
ls /etc/grub.d
```
will show if it is.
(It normally should be something like 30_os-prober)

---

### Post by fantab on 2014-09-11
Use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") tool to '*create a bootinfo summary*'... note the url link and post the link here.

Also 'fedora' is notorious NOT to find other linux os.

---

### Post by NM5TF on 2014-09-11
+1 ^^^^^

Boot Repair should fix your issues in GRUB.....

tommy

---

### Post by oldfred on 2014-09-11
Is this a typo for sharing?
> to shring Ubuntu partition

If so you just overwrote Ubuntu. You cannot share system partitions. And with different system you may share a data only partition, but still may have to manage UID & GIDs as Ubuntu has default user as 1000 and not all others use that.

---

### Post by Pelvur on 2014-09-11
> **oldfred said:**
> Is this a typo for sharing?




No, it was typo for "shrink" :)

Thank you all, I used Boot Repair and it helped. Now I need to find the way to install OpenSUSE and avoid this problem again. I guess I will try to prepare partition in advance, that should help.

I'm not marking this thread as solved just yet, I will wait until I install third distro and see if I can add something here.

---

### Post by yancek on 2014-09-11
What happened with CentOS is you installed its bootloader to the master boot record overwriting the Ubuntu Grub.  Hang on to that boot-repair disk when you install Opensuse as it has quite a number of options in regard to the bootloader.  You will get to a windows labelled Live Installation Settings and there is a heading named Booting and when you click on that you will see a new window with additional settings.  Selecting boot from root partition should work.

---

### Post by mansonfan78 on 2014-09-12
I don't know how the installers for Opensuse or CentOS are designed, but if you have the option during install, just don't install a bootloader at all (or at least don't install it to mbr - just the respective partition of the distro).  Then you could just reboot into Ubuntu and update grub from there and let it find the new distros.

---

### Post by Pelvur on 2014-09-12
> **mansonfan78 said:**
> but if you have the option during install, just don't install a bootloader at all 

I think that's exactly what I did - installed a bootloader, and thus overwrote one for Ubuntu. Thanks, I will look up for that while installing next distro.

---

### Post by fantab on 2014-09-12
> **pypetukhov said:**
> 
Thank you all, I used Boot Repair and it helped. Now I need to find the way to install OpenSUSE and avoid this problem again. I guess I will try to prepare partition in advance, that should help.


When installing OpenSuse DO NOT install grub... choose not to.
After a successful install: you reboot, boot into ubuntu and run '*sudo update-grub*' for the 'os-prober' to find your new opensuse install.

For better Grub management and for customizations read [here]("https://help.ubuntu.com/community/Grub2") and [here]("https://help.ubuntu.com/community/Grub2/CustomMenus").
It will be a good idea to setup your boot menu with 40_custom file as explained in the above linked pages.
Otherwise, every time a new kernel is added in other two distros you will have to come back to Ubuntu and 'update-grub'.

---

### Post by Pelvur on 2014-09-13
> **fantab said:**
> When installing OpenSuse DO NOT install grub... choose not to.

I don't think I had an option to choose, but anyway, right now everything is up and running. I have prepared partition for OpenSUSE in advance, and just chosen to install it there. After installation, grub is able to see all three OS.

Thanks everybody for help.

---

### Post by fantab on 2014-09-13
You must have missed the 'grub' step, but nevermind.
Glad you've successfully setup your 'multiboot'. Congrats.

---

