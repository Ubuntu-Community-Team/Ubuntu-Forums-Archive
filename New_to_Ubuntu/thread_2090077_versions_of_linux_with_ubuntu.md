---
title: "versions of linux with ubuntu"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by Advait on 2012-12-01
Hi All,

I searched google, the Ubuntu Forums and Wikipedia on this and didn't find anything relevant.

I'm currently using 12.04. When I update 12.04 using the Update Manager will it always look for and get the latest stable version of Linux? Or is 12.04 limited to only using a certain version of Linux and no higher?

Thanks,

Advait

---

### Post by haqking on 2012-12-01
> **Advait said:**
> Hi All,

I searched google, the Ubuntu Forums and Wikipedia on this and didn't find anything relevant.

I'm currently using 12.04. When I update 12.04 using the Update Manager will it always look for and get the latest stable version of Linux? Or is 12.04 limited to only using a certain version of Linux and no higher?

Thanks,

Advait

Do you mean the kernel ? Ubuntu is Linux, Linux is a kernel upon which distros base themselves, Ubuntu 12.04 or otherwise are all based around the Linux kernel and are therefore Linux.

If you mean does the kernel get upgraded, then no, but you can choose to update the kernel if you so wish but not always necessarily the best option, it is a personal decision based o hardware and configuration and operational requirements etc.

---

### Post by Advait on 2012-12-01
> **haqking said:**
> Do you mean the kernel ? Ubuntu is Linux, Linux is a kernel upon which distros base themselves, Ubuntu 12.04 or otherwise are all based around the Linux kernel and are therefore Linux.

If you mean does the kernel get updated, then no, but you can choose to update the kernel if you so wish but not always necessarily the best option, it is a personal decision based o hardware and configuration and operational requirements etc.

Ok, thanks for the info. My question remains: What version of Linux is 12.04 limited to if I only use the official Ubuntu Update Manager to update?

I'm a newbie so I have no clue how to update the kernel any other way. I can barely use the command line.

I do understand that Ubuntu is combination of the Linux kernel and some user interface and other stuff layered on top of the kernel.

Thanks!

Advait

---

### Post by Advait on 2012-12-01
A related question: What version of Linux is used with 12.10? Thanks!

---

### Post by haqking on 2012-12-01
When you do updates it will update the kernel with security patches but wont upgrade the kernel to the latest version no.

not sure what kernel 12.10 uses, it is 3.5x i think, I dont use 12.10 so dont know of top of head.

---

### Post by zombifier25 on 2012-12-01
Unless the latest kernel has certain features that your hardware desperately needs (which yo can install fromsome PPAs), it's recommended that you use the kernel provided with Ubuntu because it has been tested for all kinds of bugs and instability issues, and will be regularly updated with security updates.

---

### Post by Advait on 2012-12-01
> **haqking said:**
> When you do updates no it wont update the kernel.

OK, thanks! This kind of basic info is helpful for a newbie like me. I always assumed Update Manager also got the latest stable version of Linux. It's good to know the real story.

So it sound like each version of Ubuntu is "tied" to a version of Linux? Is that true? (I do understand that Linux experts can upgrade to new kernels and play around.)

> **haqking said:**
> not sure what kernel 12.10 uses, it is 3.5x i think, I dont use 12.10 so dont know of top of head.

Anyone know? Thanks!

Advaot

---

### Post by mastablasta on 2012-12-01
type 
```
uname -a
```

into terminal to get the kernel and info.

12.04 is 3.2 kernel.

---

### Post by haqking on 2012-12-01
> **mastablasta said:**
> type 
```
uname -a
```into terminal to get the kernel and info.

12.04 is 3.2 kernel.

That wont tell her what 12.10 is using only her current install of 12.04.

I think 12.10 uses 3.5x i believe ?

---

### Post by Zill on 2012-12-01
> **Advait said:**
> ...I'm a newbie so I have no clue how to update the kernel any other way. I can barely use the command line...
The default kernel in your release *will* be updated with any necessary security updates automatically.  However, the kernel *will not* be updated to the "latest stable version" as this is normally done by upgrading to a new release of Ubuntu.

My advice is to forget about the actual kernel release and just enjoy using Ubuntu!

> **Advait said:**
> A related question: What version of Linux is used with 12.10? Thanks!
If you *do* wish to know exactly which kernel is installed then open a terminal (Ctrl-Alt-t) and enter the following command:
```
uname -a
```

---

### Post by haqking on 2012-12-01
> **Zill said:**
> The default kernel in your release *will* be updated with any necessary security updates automatically.  However, the kernel *will not* be updated to the "latest stable version" as this is normally done by upgrading to a new release of Ubuntu.

My advice is to forget about the actual kernel release and just enjoy using Ubuntu!


If you *do* wish to know exactly which kernel is installed then open a terminal (Ctrl-Alt-t) and enter the following command:
```
uname -a
```

To the OP ```
uname -a
```will only tell you the version of kernel which your current install of 12.04 is using which will be 3.2, 12.10 which you asked about uses 3.5

---

### Post by Paqman on 2012-12-01
> **Advait said:**
> 
So it sound like each version of Ubuntu is "tied" to a version of Linux? Is that true?

Yes. You'll get new versions of that kernel when security patches are applied, but you won't move to a new kernel.

---

### Post by Advait on 2012-12-01
> **Paqman said:**
> Yes. You'll get new versions of that kernel when security patches are applied, but you won't move to a new kernel.

Perfect! Your reply tells me just what I was looking for. Thanks,

---

### Post by newb85 on 2012-12-01
Yes, you will receive new kernel versions with updates from time to time.  The old ones are kept, and can be selected from GRUB in the event the new ones cause problems.  (The versions are listed from newest to oldest, with newest being the default.)

I doubt the ones that come through the official updates are always the "latest stable version", though.  The kernel itself might be stable, but that doesn't mean Ubuntu will work well with it. The Ubuntu devs take the time to make sure it will before pushing it through. Usually, the best course is to install the recommended kernel updates using the updater.  Quick, easy, and well-tested.

---

### Post by Advait on 2012-12-01
> **Zill said:**
> My advice is to forget about the actual kernel release and just enjoy using Ubuntu!

( smile! ) I do enjoy using Ubuntu (the security it provides vs Windows is terrific!). My nature is I like to get a basic understanding of the tools I use. Knowing how the kernel is and is not updated helps me to decide when and when not to upgrade. I'm not a coder but I do want to understand the big picture of how Ubuntu works under the hood.

Thanks to everyone for the helpful info. Peace and Light,

Advait

---

### Post by haqking on 2012-12-01
> **Advait said:**
> ( smile! ) Knowing how the kernel is and is not updated helps me to decide when and when not to upgrade. 

Advait

The kernel will get "updated" with patches etc but it wont get "upgraded" to the latest kernel.

You can "upgrade" to the latest kernel if you wish but you should know what you are doing and why to do that, if you keep your install updated with security patches etc then you will be getting the updated version of your current kernel at regular intervals just not the latest kernel over all.

For example with 12.04 when you update the patches will applied to your kernel version 3.2x and so you will always have a up-to date version of that kernel, however it will not upgrade to say the 3.5x kernel which 12.10 is running though you could choose to do that yourself if you wanted to if you had good informed reason.

The update/upgrade terminology can get confusing, i often use the terms interchangeably by mistake and i really shouldn't ;-)

Peace

---

### Post by snowpine on 2012-12-01
Ubuntu is "open source" so you never have to guess what is the latest kernel; you can visit [packages.ubuntu.com]("http://packages.ubuntu.com") and search for info. For example here are the "changelogs" for the 12.04 and 12.10 kernels so you can see exactly what are the latest updates and what changes/patches are included.

[http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_3.2.0.34.37/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_3.2.0.34.37/changelog)
[http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_3.5.0.19.22/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_3.5.0.19.22/changelog)

Some info on using non-standard kernels (not recommended/necessary but maybe fun for educational purposes or if you have a specific hardware-support problem):

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[https://wiki.ubuntu.com/KernelTeam](https://wiki.ubuntu.com/KernelTeam)

---

### Post by Cheesemill on 2012-12-01
To see the current kernel versions for different Ubuntu releases just search the site [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for the package 'linux'.

[http://packages.ubuntu.com/search?keywords=linux&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=linux&searchon=names&suite=all&section=all)

---

