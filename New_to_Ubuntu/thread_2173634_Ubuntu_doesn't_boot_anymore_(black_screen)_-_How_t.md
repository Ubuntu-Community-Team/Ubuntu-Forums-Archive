---
title: "Ubuntu doesn't boot anymore (black screen) - How to retrieve data on HD?"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by redcougar272 on 2013-09-10
I had Win 7 and Ubuntu working fine since some months. Today Ubuntu doesn't boot. I receive a black screen with the following lines: Starting the winbind daemon winbind ...ok Starting anac(h)ronistic crom...ok Checking battery state...ok Stopping System V runlevel compatibility...ok. Nothing else. Broken.

I suppose I have to reinstall Ubuntu. What a pity because I am not able to retrieve some data from the Ubuntu HD ("download", "documents", ...) which is not reachable any more. As you know, Windows doesn't see those ubuntu HD parts.

Is there a way to take back those data?



Thanks.

---

### Post by GreatDanton on 2013-09-10
You can boot to live cd, and copy files to external drive. I assume you still got Ubuntu cd/usb.

---

### Post by redcougar272 on 2013-09-10
Hello,

I need to repair Ubuntu 12.04 but I don't know how to do it.

I have checked / tried  while running the different versions of the Ubuntu live cd (12.04; 12.10; 13) but I don't see how it's working.

Thanks.

---

### Post by coffeecat on 2013-09-10
@redcougar272, I've moved your latest post into your own thread as it's basically a continuation of the same issue.

---

### Post by deadflowr on 2013-09-10
Boot into the livecd but do the try Ubuntu option and not install Ubuntu.
Then when the Ubuntu desktop comes up open the file manager and see if your Ubuntu Partition shows up in the devices section of the side panel.
If you have another disk or partition available you should be able to copy them.
Chances are, though, you might need to be root.

---

### Post by cariboo on 2013-09-10
It would be way easier for us to help you solve your problem, if you told us what you did to cause your system to stop booting.

---

### Post by redcougar272 on 2013-09-11
cariboo907: hello

I did absolutely nothing. Ubuntu was working fine on the morning; I stopped the PC and in the afternoon I booted again not to succeeding.

Thanks for your attention.

---

### Post by redcougar272 on 2013-09-11
To **dedflowr**. thanks but 

[U]how to be ROOT with the graphical interface 
[/U]

===== with a terminal, I know.


Regards,

---

### Post by deadflowr on 2013-09-11
Becoming root is of little importance at this point, I only stated it's possible you might need to be root not that you will need it.
you can run graphical programs as root with 'gksu program-name' from the terminal.
What is important is to try to fix the problems.
Can you boot into the grub bootloader menu?
If so, try entering into the recovery mode.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
You might try some of the options, such as fix broken packages, or fsck.

---

### Post by redcougar272 on 2013-09-12
Hello and thanks.
Ubuntu is installed along / inside Win 7 and there is no Grub visible. The aspect is not as a normal Grub window. I think that the the boot menu is a Windows one with two choices: Win 7 / Ubuntu. Thanks for trying. I will simply try to reinstall Ubuntu along Windows.
When running a live cd with ubuntu, I cannot see (in the file manager) the drives and folders of the installed ubuntu. I see only empty folders of the running ubuntu from the live cd and the c: and d: drives of Windows.

Regards.

---

### Post by coffeecat on 2013-09-12
That sounds like it could be a wubi installation which has a virtual partition inside a C:\ubuntu\disks\root.disk file if you installed to the C: partition (substitute D: if installed to D: ). Have a look here:

[https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F)

It shows you how to loop mount the virtual partition and recover files using a live CD. It'll also be worth running a fsck of the root.disk in case a filesystem irregularity is the cause of your problem -  the command is in that section of the link.

---

