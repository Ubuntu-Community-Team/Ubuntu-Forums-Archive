---
title: "Updating to the latest stable kernel in Ubuntu 12.04 LTS"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by mdavis1231 on 2013-01-06
Could someone tell me how I would go about safely updating to the newest stable kernel in Ubuntu 12.04 LTS?  Thanks!

---

### Post by Pjotr123 on 2013-01-06
> **mdavis1231 said:**
> Could someone tell me how I would go about safely updating to the newest stable kernel in Ubuntu 12.04 LTS?  Thanks!

Enter this in the terminal:
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

That should do it. :)

In case you mean something else, namely the newest stable kernel from upstream (the kernel team), that's a no-no: expect frequent breakage and many unsolvable bugs, when using a kernel that's not part of a stable Ubuntu release. 

In a sense, the kernel *is* the operating system. The rest is "just" a layer around it. This layer needs to be finely tuned and adjusted to the kernel, otherwise all kinds of things will go horribly wrong.

---

### Post by fdrake on 2013-01-06
install kernel
```

sudo apt-get install linux-image-*
sudo apt-get update && sudo apt-get upgrade 

```

list your current kernel
```

uname -a

```

---

### Post by fdrake on 2013-01-06
[HTML][/HTML]> **Pjotr123 said:**
> Enter this in the terminal:
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

That should do it. :)

In case you mean something else, namely the newest stable kernel from the kernel team:
Expect frequent breakage and many unsolvable bugs, when using a kernel that's not part of a stable Ubuntu release. 

In a sense, the kernel *is* the operating system. The rest is "just" a layer around it. This layer needs to be finely tuned and adjusted to the kernel, otherwise all kinds of things will go horribly wrong.
[s]
i don't think the OP wants to upgrade the release version of ubuntu(from 12.04 to 12.10). S/He wants to use release 12.04 but with the lates kernel available for it. And since 12.04 is a long term release there is not need to upgrade the release in order to upgrade the kernel.[/s]

---

### Post by arpanaut on 2013-01-06
dist-upgrade is not the command to upgrade to a newer release see:
```
man apt-get
```

---

### Post by fdrake on 2013-01-06
> **arpanaut said:**
> dist-upgrade is not the command to upgrade to a newer release see:
```
man apt-get
```

you are right.. I always thought (since I use upgrade command) that it did upgrade the release version too
> 
       upgrade
           upgrade is used to install the newest versions of all packages currently installed on the
           system from the sources enumerated in /etc/apt/sources.list. Packages currently installed
           with new versions available are retrieved and upgraded; under no circumstances are
           currently installed packages removed, or packages not already installed retrieved and
           installed. New versions of currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at their current version. An
           update must be performed first so that apt-get knows that new versions of packages are
           available.

       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently
           handles changing dependencies with new versions of packages; apt-get has a "smart"
           conflict resolution system, and it will attempt to upgrade the most important packages at
           the expense of less important ones if necessary. The dist-upgrade command may therefore
           remove some packages. The /etc/apt/sources.list file contains a list of locations from
           which to retrieve desired package files. See also apt_preferences(5) for a mechanism for
           overriding the general settings for individual packages.



ps : I edited my post.

---

### Post by The Spectre on 2013-01-06
This is the method that I used to Update to Linux Kernel 3.7.1...

[http://www.upubuntu.com/2012/12/install-linux-kernel-371-on-ubuntu.html](http://www.upubuntu.com/2012/12/install-linux-kernel-371-on-ubuntu.html)

I have been running it since it was first posted on December 18th 2012 and I have had no problems in that time.

---

### Post by mdavis1231 on 2013-01-11
No, I'm not wanting to upgrade to 12.10.  I'm wanting to stick with 12.04 LTS, but have the latest stable kernel installed.

---

### Post by audiomick on 2013-01-11
I would advise you to stick to the kernel that the version of Ubuntu you are using supplies. The update manager installs new kernels when they are available and have passed muster. If the repos don't have the absolutely latest kernel in them, there might be a very good reason for that.

---

### Post by MadmanRB on 2013-01-11
Yeah I would not advise going to the newer kernel in LTS, stability overrules everything and the default kernel in 12.04 is pretty solid overall.

---

### Post by mdavis1231 on 2013-01-12
Thanks everyone for your advice.  I will leave things alone and trust that my kernel will be updated when necessary.

---

### Post by NikTh on 2013-01-12
Two series of kernel are officially available to 12.04.1 LTS. 
3.2x-xxx and 3.5x-xxx 
As you can understand 3.5 is newer (can considered as the latest)  , so if you want to install it , apply the commands below 
```
sudo apt-get update
sudo apt-get install linux-image-generic-lts-quantal
sudo apt-get install linux-headers-generic-lts-quantal
```The above packages will provide support for future kernel (images & headers) releases of 3.5 series (will update the kernel automatically). 
Thanks

---

### Post by Genitruc on 2013-01-12
> **NikTh said:**
> Two series of kernel are officially available to 12.04.1 LTS. 
3.2x-xxx and 3.5x-xxx 
As you can understand 3.5 is newer (can considered as the latest)  , so if you want to install it , apply the commands below 
```
sudo apt-get update
sudo apt-get install linux-image-generic-lts-quantal
sudo apt-get install linux-headers-generic-lts-quantal
```The above packages will provide support for future kernel (images & headers) releases of 3.5 series (will update the kernel automatically). 
Thanks

I also need to install a newer kernel as it seems to be a possible solution for my system freeze problem, but I have three questions before to try it.

1) Is there a way to go back to the older kernel and how?
2) Will I need to re-install drivers or reconfigure anything?
3) At the installation I had to use boot-repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) in order to have a working dual boot on a pre-install windows 8 laptop. Is this kernel update will break grub setup ?

Thanks for the procedure above, pretty neat by the way?
Genitruc

---

### Post by YannBuntu on 2013-01-12
> **Genitruc said:**
> 1) Is there a way to go back to the older kernel and how?
2) Will I need to re-install drivers or reconfigure anything?
3) At the installation I had to use boot-repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) in order to have a working dual boot on a pre-install windows 8 laptop. Is this kernel update will break grub setup ?

1) yes, by selecting "Advanced options for Ubuntu" in your GRUB menu at startup
2) No
3) No

---

### Post by Genitruc on 2013-01-13
> **YannBuntu said:**
> 1) yes, by selecting "Advanced options for Ubuntu" in your GRUB menu at startup
2) No
3) No

Thanks, I really appreciate.

---

