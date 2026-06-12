---
title: "ubuntu 18.04 frequently crashes on laptop"
date: 2024-04-14
forum: New to Ubuntu
---

### Post by alips3 on 2024-04-14
I'm new to Ubuntu and I installed Ubuntu version 18.04.6 in order to learn ROS. My computer had window10 installed before installing Ubuntu, and is now running a dual system. However, after installing ubuntu ubuntu often crashes. The configuration of my laptop is 11th Generation Intel(R) Core(TM) i5-11300H @ 3.10GHz 3.11 GHz, 16.0 GB of RAM, and I have 80G of total storage space allocated for Ubuntu. Since I have an NVIDIA graphics card, I followed the tutorial to boot the system using the nomodeset command. At first it was often unresponsive to start Firefox, then even opening interrupts crashed (just a phenomenon I've seen, not necessarily Firefox causing the growing problem) and I shut down the system only by forcing it to shut down. I've installed ubuntu more than 20 times in the past month, , but the crash is the same. I'd like to get some experience and advice from your predecessors on how to solve this situation.

---

### Post by TheFu on 2024-04-14
18.04 is from long before that CPU (1Q 2021) and motherboard.  Also, standard support for 18.04 ended a year ago.

Today, you should install 22.04 as a new user.  In May, you may consider installing 24.04 (or upgrading), though if you want the most stability, I'd wait to install 24.04.1 perhaps in August.  22.04 will have a kernel that knows about your CPU and motherboard.

Running out-of-support versions is meant for people that installed those releases on hardware from that period.  If you have new hardware relative to the release, a newer kernel will be necessary.

As for looking for problems, always look in the system logs for what is causing errors and warnings, then research each of them, starting from the top.  Those logs will likely provide the exact cause of the error.

I don't know what ROS is, but if it isn't tied to specific hardware, might I suggest that you run Linux under a virtual machine like virtualbox instead?  This should remove the hardware dependencies from Linux as the most compatible hardware is emulated for the virtual machine.  Plus you'll be able to run both OSes at the same time.  The OS running inside a virtual machine doesn't care about the real hardware, so your NIC or GPU won't matter.  Properly tuned, the VM will perform with about 90% of running directly on the hardware for everything not related to the GPU.  Only gamers tend to need direct GPU access. For non-gamers, it just isn't important and the normal Linux desktops all work fine on a system like yours using the emulated GPU provided by the hypervisor.

---

### Post by alips3 on 2024-04-14
First of all, thank you very much for your reply, although I would like to use the latest version of ubuntu as well, the mobile robotics competition I'm preparing for and the customized hardware I'm supplying for the competition have special requirements for the version of ubuntu, and there are a lot of compatibility issues with the scenario of running ubuntu on a virtual machine. Thanks again for your reply, after that I will also check the system logs to find out what is causing the errors and warnings and fix them if possible, thanks again!

---

### Post by TheFu on 2024-04-15
Any competition shouldn't require out of support software to be used.  This  is a noob mistake by the organization sponsoring the event.

You will likely have a hard time making new hardware work with old software. After all, the new hardware doesn't work the same. Since 2018, all sorts of things have changed, especially in CPUs after all the big security issues in Intel CPUs.

---

### Post by guiverc on 2024-04-15
I'll not help, but maybe these clues maybe helpful.

You mention release (Ubuntu 18.04.6) but not which product/ISO was used.

- The GA kernel stack for 18.04 was from 2018-April (*and before then too as the kernel is selected prior to kernel freeze*).

- The *latest* HWE kernel stack for 18.04 was used on some 18.04.5(& 6) ISOs which gives you a two year newer kernel; ie. benefits for newer hardware which is your best bet, however it's only two years newer (*suitable for hardware from late 2018 thru 2019, maybe even start 2020*)

You didn't specify what 18.04.6 you installed; so you may find switching to the newer HWE stack may help (*for newer hardware the older GA stack usually doesn't provide benefits, but its' always worth a try*), as 18.04.6 media existed using both GA & HWE kernel stacks.

[https://fridge.ubuntu.com/2023/06/17/extended-security-maintenance-for-ubuntu-18-04-lts-began-on-may-31-2023/](https://fridge.ubuntu.com/2023/06/17/extended-security-maintenance-for-ubuntu-18-04-lts-began-on-may-31-2023/)

I'll suggest keeping your system OFFLINE unless you *enable* ESM.

---

### Post by alips3 on 2024-04-16
Thank you for your reply&#65281; I also think a lot of the issues for supportability between hardware and software are really headache-inducing.
Although I'm at a great loss right now, I think I'll get around to solving these issues someday!     :-D

---

### Post by alips3 on 2024-04-16
Thanks for the reply, I'll keep an eye out for what you've mentioned! In the future I want to be a Liunx master like you guys!O:)

---

### Post by TheFu on 2024-04-16
> **alips3 said:**
> Thank you for your reply&#65281; I also think a lot of the issues for supportability between hardware and software are really headache-inducing.
Although I'm at a great loss right now, I think I'll get around to solving these issues someday!     :-D

Who are you thanking?  IF you don't include a bit of the prior message in quotes, we don't know to whom you are replying.

The solution is to run a currently supported release with a kernel that is at least 6 months newer than your hardware.
You may be stuck due to the choice of software being forced onto you.  Definitely install the latest HWE kernel and module you can.  There are how-to guides if you search "ubuntu HWE".  Be certain to follow the specific guide for your release and setup.  I think they are at help.ubuntu.com or wiki.ubuntu.com.  I've never had any problem finding the instructions.

Of course, if you don't know about HWE, it is hard to look for instructions. ;)   We don't know, what we don't know. That's the plague of technology stuff.

---

### Post by alips3 on 2024-04-16
> **TheFu said:**
> Who are you thanking?  IF you don't include a bit of the prior message in quotes, we don't know to whom you are replying.

The solution is to run a currently supported release with a kernel that is at least 6 months newer than your hardware.
You may be stuck due to the choice of software being forced onto you.  Definitely install the latest HWE kernel and module you can.  There are how-to guides if you search "ubuntu HWE".  Be certain to follow the specific guide for your release and setup.  I think they are at help.ubuntu.com or wiki.ubuntu.com.  I've never had any problem finding the instructions.

Of course, if you don't know about HWE, it is hard to look for instructions. ;)   We don't know, what we don't know. That's the plague of technology stuff.
I'm very sorry I didn't pay attention to the quoted replies, thanks for the reminder.I really didn't know much about HWE so I've decided to try and understand it now .

---

