---
title: "No wifi in acer 4730z for ubuntu 12.04"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by sonu 1807 on 2013-08-29
I have installed Ubuntu 12.04 on acer 4730z. When I tested the system without installing everything worked fine but after installation the wifi is switched off. Please help me!

---

### Post by eternal243 on 2013-08-29
Please post the output of this command: 

```
lspci | grep Network
```

It will show what kind of wireless card you have in your computer.

---

### Post by sonu 1807 on 2013-08-29
lspci | grep Network shows nothing! I have been googling this issue for the last three days and nothing has worked. Linux mint 15 worked well on my laptop. I think I will leave ubuntu. I fail to understand how ubuntu guys left this problem to be unresolved for such a long time. I will probably install debian.

---

### Post by eternal243 on 2013-08-29
> **sonu 1807 said:**
> lspci | grep Network shows nothing! I have been googling this issue for the last three days and nothing has worked. Linux mint 15 worked well on my laptop. I think I will leave ubuntu. I fail to understand how ubuntu guys left this problem to be unresolved for such a long time. I will probably install debian.

Well, if you have been googling this issue, please give us more information in the opening post, it is hard for us to help without any specific information about your system setup.

The fact is that the Ubuntu Live CD worked fine, which means your wireless card is supported, however there is probably something wrong in your configuration. Linux Mint and Debian are both good distros, and if those work better for you, then I'm fine with you using them. I use Debian myself and it is one of the best distros I have ever used. :)

---

### Post by sonu 1807 on 2013-08-29
My laptop has Ralink RT2790 wireless card. A lot of guys using ralink card are facing this problem with ubuntu 12.04 and 13.04. There seems to be no solution to it. This is klnd of forcing me to leave ubuntu.

---

### Post by sceptre78 on 2013-08-29
try the command below


 $ lsmod | grep rt

and list the output.

You may have to blacklist some modules.

Also I run Debian on my main system that has the Ralink rt2870 card and you will have to load the firmware for it.

---

### Post by sonu 1807 on 2013-08-29
arport_pc             27612  0 
parport                40930  3 parport_pc,ppdev,lp

---

### Post by sceptre78 on 2013-08-29
ok, sorry for making you wait. try this:
 sudo apt-get install linux-firmware-nonfree

then reboot.

_**EDIT**_
The one below is loaded on the live boot disk, and working with my card. It may not have installed when you installed Ubuntu onto your HDD.

sudo apt-get install linux-firmware

---

### Post by sonu 1807 on 2013-08-29
Thanks a lot! It solved my problem. Actually I love ubuntu and remember using its 10.04 version. But then had to use mac given by my company and it was not possible to tweak it at all. Even though mint 15 worked on my system I uninstalled it to give ubuntu 12.04 a try. I was frustrated by this problem. I should have come to forums earlier.

---

### Post by sceptre78 on 2013-08-29
Not a problem, glad to hear it worked.

---

### Post by eternal243 on 2013-08-29
I'm glad to hear sceptres advice worked for you! =)

---

