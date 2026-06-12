---
title: "Why Ubuntu does not require drivers?"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by vikkyhacks on 2012-01-29
Hello I have Ubuntu 11.04 and when I connect my mobile using my cell phone using my data cable I am able to connect to internet using Mobile Broadband service very easily without using any kind of additional drivers ... But to configure that under Windows I spend a hell of time and it requires lots of drivers to be installed manually ... Not just that I have noticed that Ubuntu does not require drivers for most of the Devices ... That small 700Mb of OS does not require any drivers but that 2.7GB of Win-7 needs lots of drivers ... Why is that so ???

---

### Post by Fernhill Linux Project on 2012-01-29
Most drivers (except proprietary ones) are included in the Linux kernal.
I suppose windows only officially supports devices from manufacturers that have paid for their devices to be certified, and carry the certified for windows logo thingy.

---

### Post by Cheesemill on 2012-01-29
Linux does require drivers.

It just so happens that they are all built-in to the kernel.

---

### Post by philinux on 2012-01-29
[http://www.linuxplanet.com/linuxplanet/tutorials/1019/1](http://www.linuxplanet.com/linuxplanet/tutorials/1019/1)

---

### Post by vikkyhacks on 2012-01-29
actually i am not that much of a geek but i get it that most of the drivers necessary are inbuilt with the kernel.... i have one more question. backtrack is ubuntu remastered then why is it that it cannot connect to mobile broadband without extra drivers even if it is a ubuntu remaster and where can i find the driver responsibe in ubuntu for mobile broadband. i mean the directory

---

### Post by Cheesemill on 2012-01-29
What kernel version does your current Ubuntu installation run?
You can find out with:
```
uname -r
```

I think that Backtrack uses the 2.6.32 kernel at the moment, if your Ubuntu runs a later version it simply means that the drivers you need were added after 2.6.32

---

### Post by bryanl on 2012-01-29
One thing to keep in mind with (most) Linux drivers is that they aren't supplied by a manufacturer with a whole lot of utilities and stuff to show off the hardware (or try to sell you related software).

The Linux driver effort tends to figure out the common parts for a whole family of hardware and then handle members of the family with 'options' to customize the driver as needed for a particular device. That tends to significantly reduce the amount of code that is needed to support a very wide range of hardware.

Many of the modern devices use one of a small set of 'chips' and depend upon standard protocols to talk to computers, too. That helps to consolidate the effort needed to develop driver software for them.

When you see talk about "kernel modules" then think 'drivers.' Most hardware drivers are these 'load as needed' kernel modules and there are utilities to manage them in Linux that can be useful for debugging or special cases.

---

### Post by grahammechanical on 2012-01-29
A few hours ago someone asked for help on these forums to get wireless working on Backtrack so I looked up the Backtrack web site.

It is true that Backtrack is built on Ubuntu but it is different enough for the developers to warn that linking to Ubuntu repositories (software storage servers) would break Backtrack and that linking Ubuntu to the Backtrack repositories will break Ubuntu.

Sometimes those using Ubuntu need to install wireless drivers. We have posts on that subject all the time. Ubuntu has utilities with Graphical User Interfaces (GUI) that make things easier. We have the Additional Drivers utility that can sometimes be the easy answer to getting a driver.

I do not know what utilities the developers of Backtrack provide. I suspect that everything is done through the terminal. Ubuntu has guides to help us use the terminal to fix wireless problems. And sometimes using the terminal is the best way to fix things.

I have also found this comment in the Backtrack FAQ

> BackTrack is a penetration testing distribution and as such DHCP requests etc entering the network when you boot are usually very undesirable.

This was in answer to the question: "Why don't my network cards show up when I boot?"

It seems to me that Backtrack is the kind of OS the requires a user to know what they are doing. And if you do not know what you are doing, then maybe you should not be using Backtrack. That might be the philosophy of the Backtrack developers.

Regards.

---

### Post by rgreener25 on 2012-01-29
It's built in to the linux kernel just one way that linux is easier than windows

---

### Post by haqking on 2012-01-29
> **grahammechanical said:**
> A few hours ago someone asked for help on these forums to get wireless working on Backtrack so I looked up the Backtrack web site.

It is true that Backtrack is built on Ubuntu but it is different enough for the developers to warn that linking to Ubuntu repositories (software storage servers) would break Backtrack and that linking Ubuntu to the Backtrack repositories will break Ubuntu.

Sometimes those using Ubuntu need to install wireless drivers. We have posts on that subject all the time. Ubuntu has utilities with Graphical User Interfaces (GUI) that make things easier. We have the Additional Drivers utility that can sometimes be the easy answer to getting a driver.

I do not know what utilities the developers of Backtrack provide. I suspect that everything is done through the terminal. Ubuntu has guides to help us use the terminal to fix wireless problems. And sometimes using the terminal is the best way to fix things.

I have also found this comment in the Backtrack FAQ



This was in answer to the question: "Why don't my network cards show up when I boot?"

It seems to me that Backtrack is the kind of OS the requires a user to know what they are doing. And if you do not know what you are doing, then maybe you should not be using Backtrack. That might be the philosophy of the Backtrack developers.

Regards.

+1

Backtrack is not Ubuntu, the same as Ubuntu is not debian.

BT5 just happens to be based off Ubuntu 10.04 but thats it, it does not mean the hardware support is the same.

Besides Ubuntu is marketed/targeted towards the home/desktop non techie user.

Backtrack is not a typical end user OS designed for everyday Linux/Desktop use.  It is a collection/suite of security auditing tools built around a kernel for that purpose with hardware support to match.

I agree with muts and the rest of the of the BT/Ofensive Security team, if you cant make something work in BT then it is likely you shouldnt be or dont need to be running backtrack.

And that being said, all the tools available in BT can be installed and used in any other Linux Distro if you want them or need access to a specific tool for a given pupose, BT in itself is not a pen testing tool/sec auditing tool/hacking tool, it is a  specialised Linux distro that gives you access to a collection of preinstalled and configured tools.

Peace

---

