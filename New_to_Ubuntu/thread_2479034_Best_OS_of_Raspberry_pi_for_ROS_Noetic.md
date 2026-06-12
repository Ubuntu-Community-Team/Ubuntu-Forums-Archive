---
title: "Best OS of Raspberry pi for ROS Noetic"
date: 2022-09-12
forum: New to Ubuntu
---

### Post by sm75 on 2022-09-12
Hello,
I installed ROS Noetic on Raspberry Pi OS ( my RP is a 64-bit B4 model) but I cannot run some commands it so I decided to change it to Ubuntu. I can install Ubuntu mate or Ubuntu itself for this purpose using the links below:
[https://ubuntu-mate.org/download/arm64/](https://ubuntu-mate.org/download/arm64/)
[https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)
but the problem is that both of them provide Ubuntu 22.04 Jammy Jellyfish. I already tried ROS Noetic on 22.04 for my PC , I know it is not compatible and I need 20.04 for ROS noetic. Now the question is: Can I find Ubuntu 20.04 for RP somewhere or do you recommend any other OS for RP useful for ROS Noetic?

Thank you!

---

### Post by howefield on 2022-09-12
Try here : [https://cdimage.ubuntu.com/ubuntu/releases/20.04.5/release/](https://cdimage.ubuntu.com/ubuntu/releases/20.04.5/release/)

---

### Post by MAFoElffen on 2022-09-15
Wait... I have a Raspberry Pi4 Model B, 8GB. In fact, that is what I am responding on. Started with Ubuntu Server 20.04. Installed Ubuntu Desktop. Now upgraded to 22.04.2...

I do not just run Ubuntu Desktop on this. I also run KVM/Qemu and do my DEV testing on this machine.

 - Why would you think that Ubuntu 22.04 is not compatible with yours? 
 - What is it that you couldn't do, that you need to do?

You say your Ubuntu Flavor choice is for Ubuntu Mate. Good choice. My son, who also has the Raspberry Pi4 we have, says that the founder of has done much very good scripting of Mate for RasPi, and is very proud of that. Though they have their own, dedicated Forum. 

Which begs to ask, why are you asking about MATE here? (Not any kind of a criticism) 

What I do know is that you should check if your EEPROM firmware is up to date. That is what I did before I upgraded my release to 22.04.x.

---

### Post by ActionParsnip on 2022-09-16
[http://packages.ros.org/ros/ubuntu/dists/](http://packages.ros.org/ros/ubuntu/dists/)

The repo doesn't support Jammy. Install Focal (Ubuntu 20.04) and you'll be fine

---

### Post by MAFoElffen on 2022-09-16
> **ActionParsnip said:**
> [http://packages.ros.org/ros/ubuntu/dists/](http://packages.ros.org/ros/ubuntu/dists/)

The repo doesn't support Jammy. Install Focal (Ubuntu 20.04) and you'll be fine
OSU's mirror that you linked does not seem to... But on mine, this is snipped from the UbuntuForums 'system-info' Report on it.:
```

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb http://ports.ubuntu.com/ubuntu-ports jammy main restricted
deb http://ports.ubuntu.com/ubuntu-ports jammy-updates main restricted
deb http://ports.ubuntu.com/ubuntu-ports jammy universe
deb http://ports.ubuntu.com/ubuntu-ports jammy-updates universe
deb http://ports.ubuntu.com/ubuntu-ports jammy multiverse
deb http://ports.ubuntu.com/ubuntu-ports jammy-updates multiverse
deb http://ports.ubuntu.com/ubuntu-ports jammy-backports main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports jammy-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports jammy-security universe
deb http://ports.ubuntu.com/ubuntu-ports jammy-security multiverse

Sources List from SourcesD:
/etc/apt/sources.list.d/yktooo-ubuntu-ppa-focal.list.save:
File had no entries.
/etc/apt/sources.list.d/yktooo-ubuntu-ppa-focal.list.distUpgrade:
deb http://ppa.launchpad.net/yktooo/ppa/ubuntu focal main
/etc/apt/sources.list.d/github-cli.list:
deb [arch=arm64 signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main
/etc/apt/sources.list.d/yktooo-ubuntu-ppa-focal.list:
deb-src http://ppa.launchpad.net/yktooo/ppa/ubuntu focal main
/etc/apt/sources.list.d/github-cli.list.save:
deb [arch=arm64 signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main
/etc/apt/sources.list.d/github-cli.list.distUpgrade:
deb [arch=arm64 signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main

```
22.04 (jammy) is supported by the official ports.ubuntu.com repo's. That is the repo the Ubuntu  Rasp Pi images point to. I guess maybe I don't understand what you are saying.

---

### Post by ActionParsnip on 2022-09-17
Not seeing which of your sources has the package. Can you please clarify. Adding a PPA doesn't do any checks for you. It will simply add the source. If a PPA doesn't support your distribution then you'll simply get a 404 when you check for updates

---

