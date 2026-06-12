---
title: "Can I upgrade directly from 12.04 to 13.04 and skip 12.10 ?"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by rover775 on 2014-01-20
I have purchased a Logitech Wireless Keyboard K330 and the wireless mouse M215, with the Unifying Receiver, which are mainly designed to work with Windows (XP, Vista, 7, 8, RT).

I understand that if I am running Ubuntu 13.04, that I will able to use these Logitech devices.

Can I upgrade directly from 12.04 to 13.04, or should I first upgrade to 12.10, and then upgrade to 13.04?

ASUS X200CA DBOZ 12.04 LTS

---

### Post by monkeybrain20122 on 2014-01-20
First of all, 13.04 will be end of life in a week. So you should instead get 13.10. Secondly forget about "upgrade", backup your data and do a clean install. It is a lot faster and safer. Many problems I have seen reported here are related to bad upgrades. To make it easier for the future, make a separate /home partition so you will keep all your data and settings in a clean install.

However, since it is a driver problem all you need is a new kernel.  You can  just install raring's kernel or even newer on 12.04 without changing OS. For example [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.1-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.1-raring/)
get one of each:
linux-headers-generic (matching your architecture)
linux-headers-all
linux-image-generic(mathching architecture)
linux-image-extra (matching architecture)

Download them all, put them in one folder, say create a folder called 'kerne' in Downloads
then from the terminal
```
cd Downloads/kernel
sudo dpkg -i *.deb
```
When done, reboot.

---

### Post by Topsiho on 2014-01-20
I use exactly the same wireless keyboard and mouse on my 12.04 LTS Ubuntu computer, without any installation of drivers and without any problem at all. I did not try all the fancy buttons that come with the keyboard, though, as I would not even do on a Windows computer, as I don't think using them is any useful.

I plugged the receiver into the computer, and could use the keyboard and mouse ever since. Only had to insert the batteries.

To reply your answer: you can only upgrade from one version of Ubuntu to the next one, or from one LTS version to the next LTS version .
I prefer to do a fresh install, though.

Topsiho (typing on a Logitech K330 keyboard, on Ubuntu 12.04 LTS)

---

### Post by ibjsb4 on 2014-01-20
Wait until April and you can upgrade direct to 14.04 (LTS to LTS), skipping the rest of the versions.

---

### Post by rover775 on 2014-01-20
Thanks Topsiho, I will try just plugging in the receiver to the Laptop and see what happens !

---

### Post by Topsiho on 2014-01-22
I am sure it will work. If keyboard/mouse/receiver/USB port/main board etc. is not broken one way or another.
On the packages of most hardware Linux is never mentioned, though on Ubuntu most hardware work better than on other operating systems.

Topsiho

---

### Post by NM5TF on 2014-01-22
> **ibjsb4 said:**
> Wait until April and you can upgrade direct to 14.04 (LTS to LTS), skipping the rest of the versions.


+10 :p

tommy

---

### Post by deadflowr on 2014-01-22
> **rover775 said:**
> I have purchased a Logitech Wireless Keyboard K330 and the wireless mouse M215, with the Unifying Receiver, which are mainly designed to work with Windows (XP, Vista, 7, 8, RT).

I understand that if I am running Ubuntu 13.04, that I will able to use these Logitech devices.

Can I upgrade directly from 12.04 to 13.04, or should I first upgrade to 12.10, and then upgrade to 13.04?

ASUS X200CA DBOZ 12.04 LTS

Which version of 12.04 did you install?
If recently, then you should be using 12.04.3 which already has the raring hardware stack enabled.
If not you can install it.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Of course you can also wait it out till april, but I would also include that you can install 14.04 now, if you want(though not recommended!!!)
simply press alt+F2 and type update-manager -d
and the update manager should open, only thjis time it should have the upgrade to new version 14.04 trusty tarh option at top.
I would only recommend this if you have no problems completely wiping and reinstalling it if things go downhill.
Which might happen.
Choice is yours.

---

### Post by rover775 on 2014-01-23
> **Topsiho said:**
> I am sure it will work. If keyboard/mouse/receiver/USB port/main board etc. is not broken one way or another.
On the packages of most hardware Linux is never mentioned, though on Ubuntu most hardware work better than on other operating systems.

Topsiho

SUCCESS ! ! !

I simply plugged in the USB and the mouse and the keyboard worked fine! :KS

All my concerns about needing to upgrade to use the Logitech were unfounded.

---

### Post by rover775 on 2014-01-26
> **Topsiho said:**
> I use exactly the same wireless keyboard and mouse on my 12.04 LTS Ubuntu computer, without any installation of drivers and without any problem at all.
I plugged the receiver into the computer, and could use the keyboard and mouse ever since. Only had to insert the batteries.
Topsiho (typing on a Logitech K330 keyboard, on Ubuntu 12.04 LTS)

I have a follow up question about using the wireless mouse or wireless keyboard to wake up (from hibernation and not from screen saver mode) my PC running Ubuntu 12.04 LTS. I can't seem to do it. Are you able to turn on or wake up your PC using the wireless mouse or keyboard.

When I finsih a PC session, I do not want to leave the PC running, I want to put it in a sleep state, but to wake the PC up, I have to go over to the PC and raise the lid and press the power button. I'd much rather just go to the wireless mouse or keyboard, and wake up the PC from there.

---

### Post by Topsiho on 2014-01-27
I can put the PC (desktop) in sleep mode quite easily using the mouse and the menu in the upper right corner of the screen.

When I want to use the PC again, I need to press the power button, the hard disks rotate again and the state of the computer that existed before the sleep is retrieved from the swap space, which has to be large enough to contain this state.

I never had any problem using a (wireless) mouse and/or dito keyboard using any Linux distribution in the more than 15 years I use Linux. Usually, using a wireless keyboard and/or mouse, connecting with the receiver may take some time and attempts to accomplish. But using this keyboard and mouse, connection is immediate, and has been very stable (several months now).

Topsiho

---

