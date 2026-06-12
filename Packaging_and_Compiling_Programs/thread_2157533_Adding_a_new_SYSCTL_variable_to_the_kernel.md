---
title: "Adding a new SYSCTL variable to the kernel"
date: 2013-06-25
forum: Packaging and Compiling Programs
---

### Post by sandeepnerli on 2013-06-25
Hi all,

I am working on a new TCP feature and to enable that feature I need to make use of some indicators so that there is always a backward compatibility. I.e. some kind of indication to the operating system whether to use this TCP feature or not. Since we decided on the best way to do this was using SYSCTL, I have to define a new option say "net.ipv4.tcp_sno". Since I am a newbie to the linux kernel programming, I was trying to figure out on how to do this. I tried adding it to the sysctl.conf file and reboot the OS. It gave an error "is an unknown key". I downloaded the source code for Ubuntu 11.10 (my current version of OS) and was wondering if I have to define it in the sysctl_net_ipv4.c or the sysctl.h files and recompile the kernel. I am stuck on how to proceed with this. Any help or guidance deeply appreciated since I did not find a comprehensive guide on how to add/define new  SYSCTL variable to the system.

Best,
Sandeep Nerli, USC-ISI

---

