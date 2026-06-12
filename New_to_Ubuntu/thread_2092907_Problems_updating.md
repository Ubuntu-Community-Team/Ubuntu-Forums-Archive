---
title: "Problems updating"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by johnwill on 2012-12-09
I have tried to update in Terminal Apt-get update: apt-get upgrade
update process starts with security updates and packages, the update appears to have finished and waits for my next command.
but get messages;
warning no support for locale:en_GB.utf8
Errors were encountered while proccessing avg2012flx
and E: sub process/usr/bin/dpkg returned an error code(1)
I would be grateful for advice on how to continue.
System: dual boot with Windows 7 Lenovo 64 bit.

---

### Post by ibjsb4 on 2012-12-09
Maybe

[http://askubuntu.com/questions/99651/apt-get-warning-no-support-for-locale-en-us-utf8](http://askubuntu.com/questions/99651/apt-get-warning-no-support-for-locale-en-us-utf8)

And welcome to the forums  :)

---

### Post by johnwill on 2012-12-09
lbjsb4 Thank you for your help and welcome: en_GB utf8 solved.

Have removed AVG as this seemed to be causing some problem with updating:(am informed avg not needed as Linux is secure)
message now reads Reading package lists...done
Building dependency
Reading state information ...done
The following packages have been kept back:
ginn libunity-2d-private 0 libunity-core-5.0_5 linux generic
linux-headers-generic linux-image-generic unity unity-2d-common
unity-2d-panel unity 2d-shell unity-2d-spread unity common
unity-services 0upgraded,0newly installed,0 to ;)remove and 14 not upgraded.
As a newcomer to Linux and learning by degrees I am not sure what this all means,and whether update has been successful.

---

### Post by mlentink on 2012-12-09
> **johnwill said:**
> Have removed AVG as this seemed to be causing some problem with updating:(am informed avg not needed as Linux is secure)

The information is only partially correct. Any OS is only as secure as you let it be. Linux may provide you with more and better tools to keep your system secure, but if you choose to ignore them, your system will be insecure. Secondly, even though Linux is as yet secure against virtually all viruses does not mean that other computers are. If you frequently exchange data with e.g. Windows users, it's only well mannered to keep viruses that can affect them away from them.

---

### Post by Old_Grey_Wolf on 2012-12-09
Use sudo apt-get dist-upgrade instead of sudo apt-get upgrade.

---

### Post by johnwill on 2012-12-09
Thank you for your comments: I am useing Ubuntu 12.04 and for the moment do not wish to upgrade to 12.10, will sudo apt-get dist -upgrade mean that I shall upgrade to Ubuntu 12.10.
As a greybearded new-comer to Linux please excuse my rather simple questions.

---

### Post by Bucky Ball on 2012-12-09
> **johnwill said:**
> 
As a greybearded new-comer to Linux please excuse my rather simple questions.

All good. You're in the right sub-forum for grey-bearded newcomers and we all start somewhere. Simple as you need is fine and feel free to ask for clarification if required ... ;)

I would run the two commands again, as you were:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Bucky Ball on 2012-12-09
I would run the two commands again, as you were:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ibjsb4 on 2012-12-09
> **johnwill said:**
> Thank you for your comments: I am useing Ubuntu 12.04 and for the moment do not wish to upgrade to 12.10, will sudo apt-get dist -upgrade mean that I shall upgrade to Ubuntu 12.10.

 "apt-get dist-upgrade" does not perform distribution upgrade.

#3

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by Old_Grey_Wolf on 2012-12-09
> **johnwill said:**
> Thank you for your comments: I am useing Ubuntu 12.04 and for the moment do not wish to upgrade to 12.10, will sudo apt-get dist -upgrade mean that I shall upgrade to Ubuntu 12.10.
As a greybearded new-comer to Linux please excuse my rather simple questions.

sudo apt-get dist-upgrade will not install 12.10. It will only install the linux kernel changes that were being held/kept back. You can see they were held/kept back (not installed) by looking in your post #3. When you see this, "linux-headers-generic" it tells you that a new kernel is waiting to be installed.

Oh, I am a grey-beard myself; thus, the user name. :)

Edit: see the link in ibjsb4 post above for more information about upgrade commands.

For Ubuntu there is another command that upgrades to the next release: do-release-upgrade.

---

