---
title: "in dpkg installation post script is return error"
date: 2008-12-11
forum: Packaging and Compiling Programs
---

### Post by Jayadheer on 2008-12-11
Hi all,
       I am new to Ubuntu. Recently I have installed unbuntu 8.10 version soon after I got updates list, in that processes something went wrong while installing this is what the error message I am getting.  


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


I did "$dpkg --configure -a"   as a super user then I got this message

"Setting up initramfs-tools (0.92bubuntu16) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.20-17-generic
Cannot find /lib/modules/2.6.20-17-generic
update-initramfs: failed for /boot/initrd.img-2.6.20-17-generic
dpkg: subprocess post-installation script returned error exit status 1"



Because of this I couldn't insatll any of the packges using apt-get install.   

How to fix this please help me 


Thanku

---

### Post by howefield on 2008-12-11
When you say you run the command as super user do you mean you typed into aterminal

```
sudo dpkg --configure -a
```

---

### Post by Jayadheer on 2008-12-11
> **howefield said:**
> When you say you run the command as super user do you mean you typed into aterminal

```
sudo dpkg --configure -a
```



Yes and more over I couldn't install any of the packages because of this please tell me how to fix this.

---

### Post by howefield on 2008-12-11
Try having a look at this thread, 

[http://ubuntuforums.org/showthread.php?t=724273&highlight=dpkg+was+interrupted](http://ubuntuforums.org/showthread.php?t=724273&highlight=dpkg+was+interrupted)

---

### Post by albinootje on 2008-12-11
The error is clear : 
Cannot find /lib/modules/2.6.20-17-generic

Is this version 2.6.20-17 the kernel you are currently using ?

Try the command : uname -a
to find out, and please let us know.

---

### Post by albinootje on 2008-12-11
Hmm, you wrote that you installed Ubuntu 8.10

But kernel 2.6.20-17 is from Ubuntu Feisty which is 7.04
[http://packages.ubuntu.com/feisty/linux-image-2.6.20-17-generic](http://packages.ubuntu.com/feisty/linux-image-2.6.20-17-generic)
Did you do a fresh install from Ubuntu 8.10 ?
Or did you upgrade all the way from 7.04 to 8.10 ?

---

### Post by Jayadheer on 2008-12-11
> **howefield said:**
> Try having a look at this thread, 

[http://ubuntuforums.org/showthread.php?t=724273&highlight=dpkg+was+interrupted](http://ubuntuforums.org/showthread.php?t=724273&highlight=dpkg+was+interrupted)



I have gone through your link that is the same problem I am getting 

They suggested that getopt is missing but getopt is present in my usr/bin
I have also tried with downloading getopt to desktop when I try to extract 

$tar zxvf getopt.tar.gz  

giving me as 

/usr/bin/getopt

what does it mean? 
I am unable to extract tar file even and I have tried all the ways they suggested but nothing solved my problem 
Please please help me with this

$uname -a
x jayee-desktop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

---

### Post by Jayadheer on 2008-12-11
> **albinootje said:**
> Hmm, you wrote that you installed Ubuntu 8.10

But kernel 2.6.20-17 is from Ubuntu Feisty which is 7.04
[http://packages.ubuntu.com/feisty/linux-image-2.6.20-17-generic](http://packages.ubuntu.com/feisty/linux-image-2.6.20-17-generic)
Did you do a fresh install from Ubuntu 8.10 ?
Or did you upgrade all the way from 7.04 to 8.10 ?

I have upgraded from 7.04 to 8.10 but I have freshly formated and installed 8.10 so It won't matter I think.

$uname -a
 jayee-desktop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

---

### Post by albinootje on 2008-12-11
Good, since you're not using kernel 2.6.20-17 try this :
sudo dpkg -P linux-image-2.6.20-17-generic

And if that fails, please post the output.

---

### Post by Jayadheer on 2008-12-11
> **albinootje said:**
> Good, since you're not using kernel 2.6.20-17 try this :
sudo dpkg -P linux-image-2.6.20-17-generic

And if that fails, please post the output.

if I run that command the o/p is 

dpkg - warning: ignoring request to remove linux-image-2.6.20-17-genaric which isn't installed.

Though my boot menu showing 2.6.20-17 kernel version I didn't prefer it because If i boot through that kernel my mouse is not working why I don't know 

and I thought 2.6.27.9 is advanced to 2.6.20.17 is it correct?

---

### Post by albinootje on 2008-12-11
Okay, thanks.
Can you please provide the output of :
dpkg -l|grep 2.6.2

---

### Post by Jayadheer on 2008-12-11
> **albinootje said:**
> Okay, thanks.
Can you please provide the output of :
dpkg -l|grep 2.6.2


This is the O/p
ii  linux-generic                             2.6.27.9.13                           Complete Generic Linux kernel
ii  linux-headers-2.6.27-7                    2.6.27-7.16                           Header files related to Linux kernel version
ii  linux-headers-2.6.27-7-generic            2.6.27-7.16                           Linux kernel headers for version 2.6.27 on x
ii  linux-headers-2.6.27-9                    2.6.27-9.19                           Header files related to Linux kernel version
ii  linux-headers-2.6.27-9-generic            2.6.27-9.19                           Linux kernel headers for version 2.6.27 on x
ii  linux-headers-generic                     2.6.27.9.13                           Generic Linux kernel headers
ii  linux-image-2.6.27-7-generic              2.6.27-7.16                           Linux kernel image for version 2.6.27 on x86
ii  linux-image-2.6.27-9-generic              2.6.27-9.19                           Linux kernel image for version 2.6.27 on x86
ii  linux-image-generic                       2.6.27.9.13                           Generic Linux kernel image
ii  linux-libc-dev                            2.6.27-9.19                           Linux Kernel Headers for development
ii  linux-restricted-modules-2.6.27-7-generic 2.6.27-7.12                           Non-free Linux kernel modules for version 2.
ii  linux-restricted-modules-2.6.27-9-generic 2.6.27-9.13                           Non-free Linux kernel modules for version 2.
ii  linux-restricted-modules-common           2.6.27-9.13                           Non-free Linux 2.6.27 modules helper script
ii  linux-restricted-modules-generic          2.6.27.9.13                           Restricted Linux modules for generic kernels
ii  ttf-lao                                   0.0.20060226-2                        TrueType font for Lao language

---

### Post by albinootje on 2008-12-11
Thanks.
What errors do you get now when you install a package ?

---

### Post by Jayadheer on 2008-12-11
> **albinootje said:**
> Thanks.
What errors do you get now when you install a package ?

When I run 
$sudo dpkg --configure -a 
 
Setting up initramfs-tools (0.92bubuntu16) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.20-17-generic
Cannot find /lib/modules/2.6.20-17-generic
update-initramfs: failed for /boot/initrd.img-2.6.20-17-generic
dpkg: subprocess post-installation script returned error exit status 1


This is the O/p I am getting 

In the Update manager If I tried to install any new package I am getting following error Message

[B][B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B][/B]

---

### Post by albinootje on 2008-12-11
That's very strange when it's a fresh 8.10 install.

Can you create the missing directory
sudo mkdir /lib/modules/2.6.20-17-generic
and then run
sudo dpkg --configure -a 
again ?

---

### Post by Jayadheer on 2008-12-11
> **albinootje said:**
> That's very strange when it's a fresh 8.10 install.

Can you create the missing directory
sudo mkdir /lib/modules/2.6.20-17-generic
and then run
sudo dpkg --configure -a 
again ?

Still the same 

One thing I didn't understand is why my system bothering about previous kernel 2.6.20.17 Now I am running  2.6.27.9. I don't know what i did wrong.yesterday I have installed 8.10 and I got updates I just clicked it It ran about 6 hrs then I forcibly turned off my system because installing packages are still running  and figure out that this is the error latter on

---

### Post by albinootje on 2008-12-11
It makes sense to backup your important data, and do a fresh reinstall, and making sure that all Linux-partitions get formatted properly.
GL!

---

### Post by Jayadheer on 2008-12-11
> **albinootje said:**
> It makes sense to backup your important data, and do a fresh reinstall, and making sure that all Linux-partitions get formatted properly.
GL!

Thanks alot for your time and consideration 

After installation Grub is showing atlest 2 to 3 kernals on boot menu of which one to select either default one/ generic if i want to delete entries in boot/grub/menu.lst file as well as in vmlinux will it effect my system 

Moreover can I contact you for further queries 

How can I contact you?

---

### Post by albinootje on 2008-12-11
You're welcome.

You can safely remove the older kernels.

And keep posting your questions here, because i'm just a normal user, and posting here means that a lot of people get a chance to read the questions and answers, 
and therefore sharing knowledge to a whole lot more people.

Long live Linux :)

---

