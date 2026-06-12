---
title: "A few questions from a new user"
date: 2019-01-16
forum: New to Ubuntu
---

### Post by vank.o. on 2019-01-16
Hello everyone!

First of all, I'd like to apologise if any of the questions are answered somewhere in the forum. Please direct me to the threads. 

Last night I ran the set up for ubuntu (it came along with the purchase of my laptop - dell 5370).

1. So my first question is - should I update/download anything that is required for the proper functioning of the OS.

2. The laptop has the option to be unlocked using a fingerprint. But when I try to change the "password" it does not even show me a fingerprint option. Do I need to download a software? If so, could you please tell me how?

3. When I press/hold the super button it does not do anything that the list of key combinations says it should do. The same goes for the "Fn" (function) button. Do you know why and how to fix it?

Thank you! From the few minutes that I have been on the site, it seems that the Ubuntu community is so friendly and altruistic, it's awesome!

---

### Post by SeijiSensei on 2019-01-16
> **vank.o. said:**
> 
1. So my first question is - should I update/download anything that is required for the proper functioning of the OS.


Yes, you always want to be up-to-date.  If you're using a version of Ubuntu with "long-term support" like 18.04, as all new users should, updates are fairly infrequent.  I don't know what version Dell installs on its laptops.  If you don't know what version you're running, look at the file /etc/lsb-release.

> 2. The laptop has the option to be unlocked using a fingerprint. But when I try to change the "password" it does not even show me a fingerprint option. Do I need to download a software? If so, could you please tell me how?

[https://askubuntu.com/questions/1049526/fingerprint-activation-on-ubuntu-18-04](https://askubuntu.com/questions/1049526/fingerprint-activation-on-ubuntu-18-04)

---

### Post by Frogs Hair on 2019-01-16
Hello and Welcome 

> 3. When I press/hold the super button it does not do anything that the  list of key combinations says it should do. The same goes for the "Fn"  (function) button. Do you know why and how to fix it?

Thank you! From the few minutes that I have been on the site, it seems  that the Ubuntu community is so friendly and altruistic, it's awesome! 				

I dual boot on an HP laptop  with Windows and the key binding functions including fn are different on Ubuntu than Windows. The key bindings in settings-keyboard function as expected for the most part, but the fn key functions for Windows don't work on Ubuntu with this computer. I discovered that in order to print screen on Ubuntu I have to use fn + print screen.

---

### Post by oldrocker99 on 2019-01-16
Just about every day, I type in
```
sudo apt update
sudo apt upgrade
```

That keeps your system safest, since a lot of updates are security-related.

Of course, if it says that all packages are up-to-date, no need for the second command.

---

### Post by vank.o. on 2019-01-17
I'm sorry - I forgot to tell you which version I am on - 16.04 LTS 64-bit. 

I did the "sudo apt update/upgrade" and at the 89% of completion it stopped, saying: "Unable to findinitial ram disk that I know how to handle. Will not try to makean initrd". This message was displayed 2 times and when I came back to the laptop the update was finished. What does that message mean - is everything alright? It says that I am up-to-date now, though.

---

### Post by vank.o. on 2019-01-17
[IMG]https://scontent-sof1-1.xx.fbcdn.net/v/t1.15752-9/50022262_2214491101914717_7927160016547610624_n.png?_nc_cat=103&_nc_ht=scontent-sof1-1.xx&oh=75fc83df4cde38fff79092e1b4a7a77d&oe=5CBF39F5[/IMG] I typed in "lsusb" but no fingerprint device was found (pic attached). Any ideas?

---

### Post by Holger_Gehrke on 2019-01-17
The ID 27c6:5301 is a finger print sensor (Goodix GF3208). AFAIK there's no driver for this (yet ? ...).

Holger

---

