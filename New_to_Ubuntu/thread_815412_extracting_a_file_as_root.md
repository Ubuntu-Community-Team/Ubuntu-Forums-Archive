---
title: "extracting a file as root?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by coubury on 2008-06-01
Im having abit of bother installed vmware but i have a possible solution 

this is what someone said to do

I extracted the VMWare workstation tar file under my regular user account and I run the installation script using sudo. The issue was, that the files got extracted with the permissions set from my user account (umask 007) and the files have been installed with those permissions. After extracting the tar file with root permissions (sudo) and re-install VMware everything worked fine.

My problem is how do i extract the .tar.gz file as root? the files called VMware-server-1.0.6-91891.tar.gz

and its located /home/coubury/VMware-server-1.0.6-91891.tar.gz

Thanks!

---

### Post by shifty_powers on 2008-06-01
any reason you need vmware? virtualbox is a LOT easier to install and use. you can use the ose version, (open source), or get a deb from the virtualbox website...

---

### Post by shifty_powers on 2008-06-01
otheriwse you can alt-f2, gksudo nautilus, navigate to the file, right click and extract here...

---

### Post by coubury on 2008-06-01
no not really but iv downloaded it and spent the last few hours trying tio get it to work lol

can i get virtual box using synaptic?

what size is virtualbox?

---

### Post by Prospero2006 on 2008-06-01
Post Retracted....

Don't want to get in any hot water over root stuff.


My apologies.

---

### Post by shifty_powers on 2008-06-01
yes you can get it in synaptic. but if you want usb support, get the edition from the virtualbox website.

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

just make sure you download the ubuntu x86 version, assuming you're not using 32-bit.

and the download is 21.86 mb

---

### Post by shifty_powers on 2008-06-01
> **Prospero2006 said:**
> You can enable the root account, but most people here will tell you it is not recommended. If you know what you are doing, I believe it is a necessary part of the Ubuntu user's toolbox. Sometimes, you just need to break out the root account to get the job done.

**edited out**

This will switch your shell over so that you are technically the root user.

and indeed it is not recommended. in fact i believe it is against the forum rules....

---

### Post by coubury on 2008-06-01
Thanks Prospero2006 and shifty_powers :D

---

### Post by shifty_powers on 2008-06-01
no probs. and seriously, think twice before enabling the root account. since i started using ubuntu in 2005, never once actually needed to do it....

---

### Post by coubury on 2008-06-01
why is it against the rules lol?

most of the programs im using require me to run things as root its annoying entering the password in everytime

---

### Post by coubury on 2008-06-01
What one should i download?

virtualbox-ose PC virtualization solution
virtualbox-ose modules for linux-image-2.6.22-14-generic
virtualbox-ose modules for linux-image-2.6.22-14-server
Source for the VirtualBox module

---

### Post by shifty_powers on 2008-06-01
do you need usb support?

---

### Post by coubury on 2008-06-01
No.

---

### Post by shifty_powers on 2008-06-01
then to be honest, just go into synaptic and search for virtualbox ;)

---

### Post by Prospero2006 on 2008-06-01
> 
why is it against the rules lol?

most of the programs im using require me to run things as root its annoying entering the password in everytime

I went ahead and deleted the actual procedure from my previous post because I don't want to break any rules, but....

Why is it against the rules?

That's a good question. I think that an inexperienced user could inadvertently do a lot of damage while logged in as the root user.
If 'switch to root' became a common answer, there would be more than a few people who would damage their systems. 

I do think it's unfortunate we're not supposed to address the topic of root access though. I've been using Linux for about 8 years now, and having root access is simply something that by default came with the system and required great caution when deployed. 

For me it works like this. My mindset isn't built around 'sudo.'
More often than not I'll enter a command or try to create a directory
or something and the machine will kick me back with 'permission denied.'
I'll have to uparrow and then prefix said command with sudo, enter the password, and then the job gets done. For me, that's a wasted 30 seconds.
It's easier to have a root shell on hand that will take charge and do what I tell it to do. (I'm an expert though. That may be the difference.)

So, I agree with previous poster, and correct me if I have misinterpreted your post, that sudo is really annoying sometimes.

(If this post violates forum rules for any reason, please let me know and I will remove it. I don't believe this post is in violation, but I will accept a contrary ruling from the moderators. I don't want to be in violation.) 

There's my opinion on the subject.

---

### Post by cariboo on 2008-06-01
You shouldn't have to root to extract this file. The way to do it is in a terminal:

```
tar zxcf home/coubury/VMware-server-1.0.6-91891.tar.gz
```

that will extract the file then if remeber correctly you run the install script as root and everything should be fine.

Note: doing things like this in a gui takes way to work.

Jim

---

### Post by ByteJuggler on 2008-06-01
> **coubury said:**
> why is it against the rules lol?

most of the programs im using require me to run things as root its annoying entering the password in everytime

You don't have to enter it every time.  If you enter it now, it's cached for a while so you don't have to immediately enter it again.

See [here ]("https://help.ubuntu.com/community/RootSudo")for why its discouraged to enable the root account etc.

Personally I will sometimes use a root shell (as described at the bottom of the above referenced page), but I never enable the actual root account on my box.  One less attack vector to worry about.

---

### Post by rpwdh on 2008-06-01
> **shifty_powers said:**
> no probs. and seriously, think twice before enabling the root account. since i started using ubuntu in 2005, never once actually needed to do it....

NVM... the link above answers this

---

### Post by ByteJuggler on 2008-06-01
> **cariboo907 said:**
> You shouldn't have to root to extract this file. The way to do it is in a terminal:

```
tar zxcf home/coubury/VMware-server-1.0.6-91891.tar.gz
```

that will extract the file then if remeber correctly you run the install script as root and everything should be fine.

Note: doing things like this in a gui takes way to work.

Jim

Yes just to add, "run the install script as root" means "put sudo in front of it".

---

### Post by ByteJuggler on 2008-06-01
> **rpwdh said:**
> Silly question from another n00b... how do you make sure it's NOT enabled?

I'm SO embarrassed to ask that...:(

```
passwd -l root
```

Locks the root account dead by overwriting the password field for it with a *.

(Try "man passwd" and read up on the "-l" switch.)

---

### Post by coubury on 2008-06-01
Having trouble with virtualbox

when i load my iso and go to start it it says

> 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 






I do that and this comes up

root@coubury-desktop:/home/coubury# /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                    mknod: `/dev/vboxdrv': File exists

 * Cannot create device /dev/vboxdrv with major 10 and minor  63.
root@coubury-desktop:/home/coubury#

---

### Post by coubury on 2008-06-01
also i might be safer with the usb one as i may need need to atatch a usb device


were can i get the one that supports usb?

---

