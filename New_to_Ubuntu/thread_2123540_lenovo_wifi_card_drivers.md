---
title: "lenovo wifi card drivers?"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by hexagondun on 2013-03-08
Hello everyone,

In anticipation of ubuntu phone, I've decided to install lubuntu onto an old netbook I've have sitting around for quite a while now, the Lenovo s10-2.  Figure that I better get comfortable a basic, ubuntu-based distro now as I've never really been successful with linux in the past.

after a quick few google searches, results are mixed as to whether or not my netbook is linux-compatible at all.  On one hand they say that if it's broadcom, you're stuck; on the other, I see a few folks --forum threads and youtube vids-- using this netbook with ubuntu no problems.  A friend mentioned ndiswrapper to me last night.  Might this provide a solution?  Any other ideas?


Thanks so much!

---

### Post by Anghrist on 2013-03-08
Have you tried:

```

sudo apt-get install b43-cutter
```

or

```

sudo apt-get firmware-b43-installer
```

You'll probably have to connect to a wired connection for this, but if I remember correctly one of these fixed an issue I had with my BroadCom card a few years ago.

Hope this helps!

---

### Post by hexagondun on 2013-03-08
Thanks so much for your quick reply!

sorry if this is a silly question:
After entering the first suggested command into terminal, it asks me for a sudo password.  I tried to enter in my system password, but it wouldn't accept any input at all.  I then disabled the sys password in hopes that it wouldn't prompt me next time, but, sure enough,it did.  What do I do?

edit: so the sudo is just the password-- got it.  but why won't it let me enter anything?  going to go reboot and try again after disabling pword.

---

### Post by Hadaka on 2013-03-08
Hi, when you type in sudo and it asks for a password
the pasword you enter is not echo'd back. (you wont
see what you type) this is normal. I would suggest activating
your password for security. also, to determine  what type
of wireless card you have and what drivers you need please copy
and paste this command...

```
lspci -nn | egrep '0200|0280' 
```

thanks.

---

### Post by hexagondun on 2013-03-08
just realized that it was just invisible, but even so it was giving me an error.  anyway, i had some funky stuff going on and after rebooting it wouldn't allow me to log in as admin as all...

...so i reinstalled lubuntu!

ill type those commands now.  gotta go to the other room to hardwire the to the router

---

### Post by hexagondun on 2013-03-08
turns out i have the broadcom BCM4312.  Quick google search yields loads of promising results with ndiswrapper, but im having problems with step 4, i think the error was "command does not exist" or something.  any updates on these broadcom wifi cards?
is ndiswrapper the only way?

---

### Post by Hadaka on 2013-03-08
Hi, no dont load that driver, thats a last resort
driver to load. Your card is a broadcom 4312
that is just the card number,it doesnt relate to
the driver.There is a [14e4:xxxx] that determines
what driver you need. so please post the results of...

```
lspci -nn | egrep '0200|0280' 
```
thanks

---

### Post by hexagondun on 2013-03-08
> **Hadaka said:**
> Hi, no dont load that driver, thats a last resort
driver to load. Your card is a broadcom 4312
that is just the card number,it doesnt relate to
the driver.There is a [14e4:xxxx] that determines
what driver you need. so please post the results of...

```
lspci -nn | egrep '0200|0280' 
```
thanks

thanks so much for the guidance.

here's whatis displayed in term after i paste that command:


Lenovo-IdeaPad-S10-2:~$ lspci -nn | egrep '0200|0280'
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
  

thanks again!

---

### Post by Bucky Ball on 2013-03-08
Avoid ndiswrapper. The info you're looking at there is probably old as ndiswrapper is largely superseded for Broadcom via the b43 driver.

You need both b43-fwcutter AND firmware-b43-installer. 

If you have ndiswrapper installed this may prevent success with the b43, or any other, wireless driver. Uninstall it totally.

---

### Post by Hadaka on 2013-03-08
Hi
BCM4312 802.11b/g LP-PHY [14e4:4315]
```
#removes ndiswrapper

sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*
 
```
#install
```
 sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by Bucky Ball on 2013-03-08
Thanks Hadaka.

---

### Post by hexagondun on 2013-03-08
thanks much hadaka!  I feel like such a dope cause i just dove right into this without knowing how to uninstall a utility in terminal lol.

---

### Post by hexagondun on 2013-03-08
you all have been so tremendously helpful.  I plan to take a lil ubuntu crash course so I won't need to bother you all with such basic questions!

buuut for the time being...

...Lenovo-IdeaPad-S10-2:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source
Lenovo-IdeaPad-S10-2:~$ sudo modprobe wl

that's what I got: unable to locate package.

---

### Post by hexagondun on 2013-03-08
by the way, while I have the chance to ask:

will any of these steps you guys have outlined here work with other, non-ubuntu-based distros i want to try, eg mint?

---

### Post by Hadaka on 2013-03-08
Hi, I'm sorry i ishould have mentioned you
need to do this from a wired connection connected
to the internet.
if it gives you the same cant find package error
then do..
code:
sudo apt-get update
sudo apt-get upgrade

#which you need to do anyway..and yes same commands for mint.

---

### Post by hexagondun on 2013-03-08
Thanks so much Hadaka, you're a life saver!  I did have my netbook connected to my router and still got the error msg, so ill download those updates right now!  Hopefully we'll be in business-- let you know soon :)

---

### Post by hexagondun on 2013-03-08
Everything works like a charm!  Thanks again everyone.  Now to the forums to see what's next!

---

### Post by Hadaka on 2013-03-08
Great ! glad that worked for you, please do one more thing,
well...actually2, and then mark this solved using Thread Tools
This command loads your dirver on boot.
```
sudo su
echo wl >> /etc/modules
exit 
```
*Note the ">>" make sure you have 2  ">>" that
appends the file.        then
even though you dont have a server do..
```
sudo ufw status
```
that is the firewall, *If it is disabeled do...
```
sudo ufw enable
```
little extra added security.
Have Fun !

---

