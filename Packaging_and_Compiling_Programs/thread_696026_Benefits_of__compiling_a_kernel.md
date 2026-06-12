---
title: "Benefits of  compiling a kernel"
date: 2008-02-13
forum: Packaging and Compiling Programs
---

### Post by TornadoWarning40422 on 2008-02-13
What woudl be the benefits of compiling a kernel? I'm mostly looking to eliminate errors, and to get peak performance. I am on a desktop so I probably don't need to worry about setting the performance too high... and if anyone could tell me how to compile a kernel for the following:

Dell Dimension 2400
P4 2.4 GHz Processor (tho it's listed @ 2.20GHZ)
512MB DDR/2 Ram w/1GB Linux-swap
Intel 82845G/GL[Brookdale-G]/GE Graphics Card (64MB)
i386 Architecture
and 2 40GB Harddrives

---

### Post by brennydoogles on 2008-02-13
One of the main advantages I have seen in compiling your own Kernel is the ability to remove unwanted/un-needed modules. For example, anyone running a desktop installation most likely does not need modules designed for a laptop, such as a battery meter. Also, you can remove any modules designed for hardware you do not own or never plan on using (such as a bluetooth adapter). If you plan on compiling your own kernel, I recommend two things for you: the first is to back up all of your data before hand, in the off chance you screw something up and leave your OS FUBAR. The second is to do A TON of research about your specific hardware and which modules are required in order to run as smoothly as possible, as well as which ones you don't need. Good luck compiling your kernel!!

---

### Post by wolfger on 2008-02-14
> **brennydoogles said:**
> I recommend two things for you: the first is to back up all of your data before hand, in the off chance you screw something up and leave your OS FUBAR. The second is to do A TON of research about your specific hardware and which modules are required in order to run as smoothly as possible, as well as which ones you don't need.

Well, I think backing up all of your data is a good idea whether you're playing with kernels or not. If you normally compute without a safety net (as I do), then doing so just because of a kernel change is overkill. All you really need to back up are the files in /boot and /boot/grub, and a LiveCD to boot from so that you can restore the original file if/when you make a mistake.

Research is good, but also unnecessary if all you want to do is, say, remove bluetooth compatibility. Work from the kernel Ubuntu gives you, and just take away things you're **sure** you don't need (firewire, bluetooth, wireless, various graphics cards you don't own, etc) and then recompile.

As a long-time Gentoo user prior to Ubuntu, I have compiled my kernel many times, and I can't say that I ever really noticed much impact from removing cruft from my kernel (or adding cruft to it). Then again, I run a fairly high-end system. Your mileage may vary.

edit: warning. If you use Nvidia drivers, you will need to re-install those after every kernel change. Or at least that's the way it used to work. I haven't compiled a kernel in quite some time.

---

