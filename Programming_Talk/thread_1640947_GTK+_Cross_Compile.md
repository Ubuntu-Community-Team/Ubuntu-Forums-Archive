---
title: "GTK+ Cross Compile ??"
date: 2010-12-08
forum: Programming Talk
---

### Post by Wrathrowe on 2010-12-08
Hey everyone, I'm running Ubuntu 10.10 through a Win7 VirtualBox and I've been trying to get a program built with Glade and GTK to compile for an ARM device, I haven't been able to get anywhere in a few days and it's driving me insane. It shouldn't be this hard, I must be missing something... So far this is as close as I've gotten:

Downloaded GTK+
Downloaded Anjuta

I can now compile the first example of just a window found on the GTK website. Great. Now, I downloaded a Poky ARM toolchain and extracted it to /usr/local/poky/ along with the Anjuta Poky SDK Plugin

I then load up Anjuta and configure the plugin, when I go to build the project I get this:
```
/home/apr/foobar-sample/Debug/(anjuta:7988): libanjuta-WARNING **: Cannot execute command: "/home/apr/foobar-sample/./autogen.sh --host=arm-poky-linux-gnueabi"
```

Can some please tell me how to set this up properly or tell me some other simple way of compiling GTK to run on an ARM device? Thankful doesn't begin to describe how I would feel for some help with this.

---

