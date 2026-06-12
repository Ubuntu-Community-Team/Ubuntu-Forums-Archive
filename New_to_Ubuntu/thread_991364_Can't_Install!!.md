---
title: "Can't Install!!"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by dmalpack89 on 2008-11-23
Hello everyone

I joined the forums today because of my numerous failed attempts to install ubuntu. My roommates all use ubuntu and I've seen how awesome it is so I want to run it on mine. I will be running dual with windows if that is of any help.

Firstly, I'm using an installation CD (which has already been checked and is fine) that reads Ubuntu 8.04.1.

My computer stats:

HP Pavilion Laptop dv6000 series (6308nr for me specifically)
AMD Turion 64 X2 Mobile Technology TL-50 1.60 GHz
958 MB RAM
32-bit Operating System on Windows Vista Home Premium


So to the issue, everytime I install I get the following message:

[268.041994] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed
[268.042048] b43-phy0 ERROR: You Must Go To [http://linuxwireless.org/en/users/Dr...devicefirmware](http://linuxwireless.org/en/users/Dr...devicefirmware) and download the correct firmware

This is followed by a loop of hundreds of messages:
Buffer I/O Error on SrO device logic blocks [6 digit number]

I've looked at the forums here before my post and can't find anything. Most people at least get it to install first, but I can't even get there. I saw a post that said press F6 on the load screen for other options and put "noapic" then hit enter. This hasn't worked.

Thanks for your help!

---

### Post by sportscrazed2 on 2008-11-23
ah you are using hp laptop when researching how to install on mine i found that some models have trouble installing with live cd any you might need alternate cd

---

### Post by MrWES on 2008-11-23
> **dmalpack89 said:**
> Hello everyone

I joined the forums today because of my numerous failed attempts to install ubuntu. My roommates all use ubuntu and I've seen how awesome it is so I want to run it on mine. I will be running dual with windows if that is of any help.

Firstly, I'm using an installation CD (which has already been checked and is fine) that reads Ubuntu 8.04.1.

My computer stats:

HP Pavilion Laptop dv6000 series (6308nr for me specifically)
AMD Turion 64 X2 Mobile Technology TL-50 1.60 GHz
958 MB RAM
32-bit Operating System on Windows Vista Home Premium


So to the issue, everytime I install I get the following message:

[268.041994] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed
[268.042048] b43-phy0 ERROR: You Must Go To [http://linuxwireless.org/en/users/Dr...devicefirmware](http://linuxwireless.org/en/users/Dr...devicefirmware) and download the correct firmware

This is followed by a loop of hundreds of messages:
Buffer I/O Error on SrO device logic blocks [6 digit number]

I've looked at the forums here before my post and can't find anything. Most people at least get it to install first, but I can't even get there. I saw a post that said press F6 on the load screen for other options and put "noapic" then hit enter. This hasn't worked.

Thanks for your help!

Try the alternate install CD, it's text based:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

Bill

---

### Post by xravexheavenx on 2008-11-23
Indeed HP laptops sometimes have issues.
Just got my Fiance's laptop running well again after a reinstall it it was all problems with default LiveCD.
Try the alternate CD.

---

### Post by dmalpack89 on 2008-11-23
you guys helped a LOT thanks

i downloaded the 8.10 alternate iso for my amd 64 system, and installation starts, but when it gets to the part where it installs the base system, i get this red screen and these very many errors following this style:

Their called "Debootstrap Errors" 

They say file "xxxxxx" was corrupt
Couldn't download package

This occurs in the "Installing the base system step"
When the status bar says "retrieving XXXXXX"

Then I get the final one saying Install Base system Fail

---

