---
title: "Asus G2S"
date: 2015-01-08
forum: New to Ubuntu
---

### Post by rbengr on 2015-01-08
I have an older laptop (Asus G2S) currently running Vista.  I would like to replace Vista with the 14.04 version of Ubuntu.  If this is possible, where can I get information?  Thanks.

---

### Post by Bashing-om on 2015-01-08
rbengr; Hi ! Welcome to the forum.

That box ran Vista, it will run ubuntu, however, the flag ship edition - ubuntu- requires 2 Gigs of ram for a good experience.
See:
[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)
let us know what additional guidance we may provide.

[INDENT][INDENT]can do
[/INDENT][/INDENT]

---

### Post by mc4man on 2015-01-08
Your hardware is 'just' ok enough to run Ubuntu 14.04.  Probably core2duo, 2GB ram, Nvidia 8600m. 
The gpu has nouveau support which may be better to some extent than the available nvidia drivers in 14.04 for that chipset.
(- if your laptop runs too hot with nouveau then the nvidia drivers are 'cooler' but may show some lag with some compiz related actions.

Biggest bottleneck would be your laptop hdd (or maybe 7 yr. old hdd

I'd make a usb  live disk, boot up to it & see how things work like the display, sound, keyboard, touchpad, wireless, ect. 
You could likely figure that in terms of performance a real install would be a bit worse.

---

### Post by rbengr on 2015-01-08
Thanks for the responses.  Where can I get step by step installation procedures.  Also, I am in The Netherlands but would like Ubuntu to be in English.  Is English automatic?  Will Ubuntu overwrite everything on the computer?

---

### Post by Bashing-om on 2015-01-08
rbengr: Good deal.

1) [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)  <-has the install instruction  - very simple to do.
2) Language preference is set in the install process.
3) Your choice as to how you want 'buntu installed; either stand alone, dual booting , multi booting. Be aware there is a bug presently that might effect you in 14.04 LTS with dual booting Windows IF the Windows system is UEFI . There is a work-a-round IF you think you may be effected.

LTS is Long Term Support, 14.04 is supported 'till April of 2019 .
Release 14.10 is an interim release and is supported for 9 months, then upgrade to the next interim release 15.04 , 15.10 and then the next LTS release 16.04 ( April 2016 ) ...

[INDENT][INDENT]happy trails
[/INDENT][/INDENT]

---

### Post by yancek on 2015-01-08
Another tutorial below which is more detailed and also has information on Linux partition naming conventions which can be very useful for a first time install.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by rbengr on 2015-01-08
Thank you.  Ubuntu will be a stand alone installation.  I read that installing the 32 bit version can be smoother than the 64 bit install.  Any opinions?  I will be using the computer exclusively for Python programming and ROS developent.

---

### Post by grahammechanical on 2015-01-08
> [COLOR=#000000]I read that installing the 32 bit version can be smoother than the 64 bit install. [/COLOR]

That is not correct information. It does not matter if it is 32 bit or 64 bit or if it is Ubuntu or a flavour of Ubuntu installation is the same. The procedures are the same. The drivers are the same. In fact it can be more complicated to install 32 bit Ubuntu on a modern machine with a UEFI boot system than installing 64 bit Ubuntu.

I am running 64 bit Ubuntu on an Intel Core 2 Duo 2.40GHz with 1GB of RAM but I have an Nvidia GT220 with 1GB of its own memory and that helps. I have doe many installs of Ubuntu on this machine for testing purposes and it does not matter if it is 32 bit or 64 bit the install process is the same.

I do think that the amount of video memory is an important factor to take into account when deciding between Ubuntu or Xubuntu or Lubuntu.

Regards.



Regards.

---

