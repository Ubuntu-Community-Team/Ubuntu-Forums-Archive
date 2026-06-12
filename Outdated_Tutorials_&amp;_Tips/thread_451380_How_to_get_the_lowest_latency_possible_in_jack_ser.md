---
title: "How to get the lowest latency possible in jack server with ubuntu Feisty"
date: 2007-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by barbe-et-hache on 2007-05-22
If you are unable to start the Jack server with the realtime parameter selected and/or
if your latency is longer in linux than with ASIO driver in windows
you may need to follow those instructions : 

If you have UbuntuStudio installed, all of this is already done.

In order to get the lowest latency possible with your sound card in linux, you need to do a few change in your kernel configuration. Don't worry it's easy.
The thing is that you need a low latency kernel and then you need the right to preempt the kernel as normal user.

1 - Install a low latency kernel : 

Thanks to the guys from Ubuntu Studio, there is now a low latency kernel in the repositories. Make sure you have enabled the universe repo in Synaptic (Settings->Repositories). Now search the package linux-lowlatency and install it. Install also the linux-header-lowlatency and the linux-restricted-modules-lowlatency packages.
Restart now your computer on your new kernel.

2 - Allow normal user to preempt the kernel

We will now compile a module for the kernel.

Install the package build-essential, module-assistant and realtime-lsm
Launch module assistant as root
    $ sudo module-assistant
Select UPDATE and press enter
Select PREPARE and press enter
Enter the SELECT menu and select the realtime-lsm module (pressing space) and then OK
A new menu will appear, enter SEARCH and then GET. You now have the source of the module. Then enter BUILD to build the module and, if everything is ok, you can INSTALL it.

Let's :guitar:

---

### Post by barbe-et-hache on 2007-05-23
a real time kernel is now available for ubuntu feisty and ubuntu studio. Follow instructions [here]("https://wiki.ubuntu.com/RealTime").

---

### Post by bmhm on 2007-06-28
Wow I read about it a few days ago in a linux magazine (german one).

What benefits does it have in particular? I was just guing to try the low-latency-kernel...

Anyway, is it stable? Can't see that from the wiki page!

Regards

---

