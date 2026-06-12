---
title: "New User Question : VirtualBox"
date: 2019-06-24
forum: New to Ubuntu
---

### Post by acmcmenamy on 2019-06-24
Hi,

  I am new to the forums so I apologize in advance for redundant questions.

  I have tried just about all versions of Linux.  And I cannot find one that runs Virtualbox as needed or it has other issues.

  I am trying to run a program call Shadow, It is a report power house PC that you rent for 35$ a month. Like Cloud Computing. Ubuntu 18.04 runs it but the mouse is glitching all around the screen or I cannot see it as if its hidden behind the program. So I have tried Ubuntu 19 and it will not install no matter what I try to do. I assume compatibility issues. I have a cheap Lenovo Yoga 12 with a i5 and SSD in it so the resources is not that great for windows. I need some help either with libraries that will help or packages I am missing.  I really do not want to switch back to windows.... god I hate windows with a passion but I am afraid I am running out of hope.

Any help will be greatly appreciated.  Maybe a ppa that I am missing or libraries that will solve all my problems.

---

### Post by TheFu on 2019-06-25
Please explain what you are trying to accomplish like we are old and senile.  
Please explain what you have tried already like we are old and senile.

I seriously doubt you've tried even half the versions of Linux available. There are hundreds.

Did you try installing the guest additions into the guest virtual machine?

Which OS is the host?
Which OS is the guest?
What sort of OS does this program want/need?

We cannot read minds.

---

### Post by acmcmenamy on 2019-06-25
Sorry I will list everything that I have tried.

Distros -  Ubuntu, Different flavors of Ubuntu, Parrot OS, Kali, Majaro, Mint, and there are a few others.

I have mostly messed with Ubuntu so the majority of this will be Ubuntu 18.4 or 19.#.

 I am replacing windows with another OS. No dual boot or side loading. Just a raw copy of the OS in place of Windows or Chrome OS.

I have done the Sudo apt-get update and upgrade -y  also installed intel x86 and 64 packages. Each time I boot there is no drivers to obtain off a fresh install so I am just using default generic drivers and kernals. I have used reddit and different guides on thefloss and other websites to download different codecs and other ppa's that was suppose to help. However with no luck.

What I am trying to do : Replace all OS's on my devices with a Linux Distro. I do not want windows or anything running on any device of mine. I have a app called Shadow ([http://www.shadow.tech](http://www.shadow.tech) ) which allows me to connect remotely to a powerful PC to play games or work on python projects for school. I need better performance running this application. Windows bogs down and runs super slow because of 4gigs of ram with a i5. I am not looking to upgrade or invest in more hardware for this laptop. I am just looking for something to boot up and load Shadow Application. Maybe something that does not throttle my connection would be excellent. I would just like a distro that will install .deb files after install and does not need much interference from me to boot. As I am learning this all on my own with google and Ubuntuforums I am not that tech savy with Linux. 

 If need be I can provide links to all the guides I have attempted.

---

### Post by lazarocarroll on 2019-06-25
Did you get Virtual box to work?

Also, I just tried to Download Shadow ([http://www.shadow.tech](http://www.shadow.tech) ) on my laptop (Ubuntu 19.04) Asus w/ Gforce 940M..... No luck. I could try  Ubuntu 18.04 on it... but I won't have time tonight.... 

I Do see on the website under Downloads that it is compatible with Ubuntu 18.04

Best case scenario ... You should be able to run Shadow on 18.04 after you download, extract and install Shadow.zip file by double clicking the .deb file.

I might be stating something you already know, but also make sure you have an network cable plugged into the laptop when you try to test Shadow. This will be the best option.

Notes: Your PC is a Lenovo Yoga 12 (Please verify the specs)

[LIST]
[*]CPU. Intel Core i5-4300U 117. 
[*]GPU. Intel HD Graphics 4400 146. 
[*]RAM. 8GB DDR3, 1600MHz. 
[/LIST]


Nvidia has not been kind to me and linux, but after some research and a lot of testing. I got it working pretty good. I don't know if there are graphics drivers for Intel based GPUs

Anyone,
Please feel free to correct me.

Thanks!

---

### Post by again? on 2019-06-26
The shadow zip file contains both an appimage and a deb.
They appear to be the same version.
Both start here on 18.04 showing the login Window.
Would test but not in the US and don't have a spare 25$US per month.

---

### Post by Agradilius on 2019-06-26
Ideally, you'd want to run in in Ubuntu. 

However, since this thread is about VirtualBox, I'd like to add that not only does the guest need drivers/guest additions to take advantage of features, but after the installation of VirtualBox on the host OS you'd need to add your user to the vboxusers group and install the extension pack so you can use the host features too, like USB 3 support and other stuff. To add the user to the vboxusers group: "sudo usermod -aG vboxusers username", logout then log back in. typing: "groups" in a terminal window should then list vboxusers.

---

### Post by mastablasta on 2019-06-26
> **lazarocarroll said:**
> 
Nvidia has not been kind to me and linux, but after some research and a lot of testing. I got it working pretty good. I don't know if there are graphics drivers for Intel based GPUs

Anyone,
Please feel free to correct me.



i feel like correcting you, so ... Intel GPU drivers are embedded in kernel (the core of the OS) because they are opensource. same goes for AMD (AMD-GPU or radeon). nvidia also has opensoruce drivers in kernel (called nouveau) which are mostly reverse engineered proprietary drivers. so they are not as good, but they usually can at least display the desktop on the nvidia GPU. for games and fun nvidia proprietary (closed source) drivers have to be installed.

---

### Post by TheFu on 2019-06-26
If you are trying to run Linux and the program you want to use has a native Linux release, why is there any virtualbox involved?  

This doesn't make any sense to me.

Please revisit the original questions and try to answer those which haven't been answered.

---

### Post by lazarocarroll on 2019-06-26
> **mastablasta said:**
> i feel like correcting you, so ... Intel GPU drivers are embedded in kernel (the core of the OS) because they are opensource. same goes for AMD (AMD-GPU or radeon). nvidia also has opensoruce drivers in kernel (called nouveau) which are mostly reverse engineered proprietary drivers. so they are not as good, but they usually can at least display the desktop on the nvidia GPU. for games and fun nvidia proprietary (closed source) drivers have to be installed.

Thank you for correcting me. It's good to know the GPU drivers are embedded in the kernel. Next Laptop I get I will be looking for a AMD GPU :D.

Also, I did not know they Nivida drivers are called nouveau.

---

