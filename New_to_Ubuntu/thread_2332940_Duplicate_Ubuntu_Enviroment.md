---
title: "Duplicate Ubuntu Enviroment"
date: 2016-08-05
forum: New to Ubuntu
---

### Post by khan3 on 2016-08-05
Hey,

I just had to reinstall ubuntu on my vmware vm on my home computer and then reconfigure everything

I want to now wipe my laptop and reinstall ubuntu on it. Is there a way i can copy what i did on my pc and install it on my laptop. My laptop won't have a vmware just want to boot straight into linux.

---

### Post by grahammechanical on 2016-08-05
I am not an expert but I think that when running an OS in a virtual machine the guest OS does not have hardware drivers. And there will be hardware differences between the PC and the laptop anyway.

Regards

---

### Post by MartyBuntu on 2016-08-05
I believe the RoboLinux disk includes utilities to take virtual images and the apply them as hard drive installs.

---

### Post by CatKiller on 2016-08-05
I don't have any experience with VMs, but if you can't use the image directly as MartyBuntu describes, all of your configuration settings will be stored in your home folder. Those will be the files that you'll want to copy to the new install. There is also a command you can run on your old install to create a list of all the packages that are installed to make it easier to install all the same packages on the new install. That should take care of most of the customisation you've done in your old installation.

---

### Post by khan3 on 2016-08-06
@CatKiller whats that command?

---

### Post by CatKiller on 2016-08-06
I don't know; I'm on my phone.

Edit: http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html

---

### Post by tsjswimmer on 2016-08-14
There are probably multiple ways to create a list of packages. I like aptik, which can be installed using **sudo apt-get install aptik**. Using **sudo aptik-gtk**, you can make backup lists of your packages and repositories in one go (the aptik package contains the **aptik** command, which is operated from the command line, and **aptik-gtk**, which uses a gui).

Also, if you can copy all of your files from your VM to your laptop individually, then Ubuntu is 99% installed. You only have to update /etc/fstab, install GRUB to your HDD, and update GRUB's configuration. I've done this before, so I can say from experience that it works. You don't even have to worry about drivers, since Ubuntu is smart enough to use the correct drivers on your new configuration. **Important**: if you do this, make sure all file permissions are copied correctly. Otherwise, you could have major problems. If you copy the files from the command line (presumably mounting vmware's HDD image), you can use **cp -a**. The -a argument will make sure the permissions are unchanged.

However, installing Ubuntu this way is a somewhat advanced task; therefore, depending on your skill level and/or bravery, you might be better off just copying your home directory and packages. You can then use **sudo aptik-gtk** to automatically reinstall all of your packages and repositories.

---

