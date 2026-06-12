---
title: "Ubuntu Jaunty Jackalope 9.04 MP3 plugin not working"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by ububoy11 on 2013-02-24
H):Pi all 


i am an extreme noobist at this point,, i know its 2013,,but thats why i need some help :: This goes out to all the Ubuntu Heros out there,,

You know this is the best OS !! 
My sound works and even my WIFI !! 

I am currently using a notebook : HP compaq nc8000
So finally i installed Ubuntu 9.04 all and  works well  except for playing avi and mp3 files ? what can i do ?


 i also get a respository error when trying to update ?? please check pics for more details Cheeers !

What can i do about this Please help ? ?!! :confused:

---

### Post by howefield on 2013-02-24
You are running an outdated and therefore unsupported version of Ubuntu, that's what is giving you the errors.

Either update your sources.list to reflect the old-releases repositories or get up to date with a supported version.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by CharlesA on 2013-02-24
9.04 has been end-of-life for a while now, which is why you get the repository error if you try to update. You can modify where it looks for the repos, but as 9.04 is end-of-life you will not be getting any updates.

It would be better to run one of the newer versions if you can, 12.04 is supported for 5 years.

As far as mp3s and whatnot, you will probably have to install the ubuntu-restricted-extras package from Synaptic, but before you mess with that, read here:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by ububoy11 on 2013-02-24
hi all as i have said before i am totally excited about having this OS working...

I wish to learn and teach it inside and out,,just at this stage i am a complete novice !! i need help , my Ubuntu does not want to update and gives me error like network or respository errors ...

where do i start ??

:sad::icon_frown:

Thanks

---

### Post by howefield on 2013-02-24
Threads merged, please keep to one thread per issue. 

Oh.. and just noticed your new to the forum, welcome ;-)

---

### Post by westie457 on 2013-02-24
Check your other thread for the best advice.

Thank you.

---

### Post by grahammechanical on 2013-02-24
Welcome to the forums and welcome to using Ubuntu.

A new version of Ubuntu is released every six months and we get support for a minimum of 18 months for the desktop version.

Ubuntu 9.04 is way out of life that is why you are getting those error messages. The Repositories are simply no longer available.

To play mp3 files you may need to install Ubuntu Restricted Extras. That will install proprietary (non open source) codecs. They are legal but not Open Source. But you will not be able to install Ubuntu Restricted Extras for 9.04 because the Repositories are no longer available. Do you understand the problem?

You need to upgrade from 9.04 to 9.10 and then to 10.04 and then to 12.04, As 10.04 is also about to go out of life (April 2013). With 12.04 you will get support for 5 years.

I will try and find some information for you. You should read this

[https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

First try going into Synaptic Package Manager and into Settings and look for a place where you set to be notified of the next version of Ubuntu and then run Reload or something like that. You may then see a button that will let you upgrade to 9.10. Accept the upgrade.

If that works you should get an invitation to upgrade to 10.04. Accept the upgrade. If that works go into Synaptic Package Manager Settings again and tell it to notify you of the next LTS release (Long Term Support). You should get an invitation to upgrade to 12.04. Accept the invitation. If that works then you are there.

Try this before trying to use the command line to get things done.

Regards.

---

### Post by prodigy_ on 2013-02-24
> **grahammechanical said:**
> You need to upgrade from 9.04 to 9.10 and then to 10.04 and then to 12.04, As 10.04 is also about to go out of life (April 2013).
It's a very old Pentium M based laptop. I'd suggest to reinstall from scratch using something very lightweight, e.g. [Lubuntu 12.10](http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/lubuntu-12.10-desktop-i386.iso).

---

### Post by CharlesA on 2013-02-24
> **prodigy_ said:**
> It's a very old Pentium M based laptop. I'd suggest to reinstall from scratch using something very lightweight, e.g. [Lubuntu 12.10](http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/lubuntu-12.10-desktop-i386.iso).
+1. They could probably get away with Lubuntu or Xubuntu 12.04 too.

---

### Post by matt_symes on 2013-02-24
Hi

> You need to upgrade from 9.04 to 9.10 and then to 10.04 and then to  12.04, As 10.04 is also about to go out of life (April 2013). With 12.04  you will get support for 5 years.


Blimey. That'll use a bit of bandwidth. :D

@OP. Do yourself a favor and download 12.04 from here.

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Create a CD or usb and install that.

Kind regards

---

### Post by ububoy11 on 2013-02-24
You guys ever sleep ? wow you guys:guitar:  i will try and keep you guys posted !!! from the first to last response must work !!


thanks once more !!:mrgreen:

---

### Post by ububoy11 on 2013-02-24
> **howefield said:**
> You are running an outdated and therefore unsupported version of Ubuntu, that's what is giving you the errors.

Either update your sources.list to reflect the old-releases repositories or get up to date with a supported version.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


):P hi 
it runs  and just gives error 

check screenshot !

i also cant update mozilla fire fox ?>?

Thanks again to all with support !

---

### Post by ububoy11 on 2013-02-24
> **CharlesA said:**
> 9.04 has been end-of-life for a while now, which is why you get the repository error if you try to update. You can modify where it looks for the repos, but as 9.04 is end-of-life you will not be getting any updates.

It would be better to run one of the newer versions if you can, 12.04 is supported for 5 years.

As far as mp3s and whatnot, you will probably have to install the ubuntu-restricted-extras package from Synaptic, but before you mess with that, read here:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)



I get the same errors as previous post !

Thanks for help though i will continue trying

---

### Post by CharlesA on 2013-02-24
Your best bet is to install a supported version of Ubuntu. Lubuntu 12.04 comes to mind.

---

### Post by ububoy11 on 2013-02-24
ok so i attempted to get ubuntu 12.04 lts and boom...error: 
check attached image :](*,)

Error says : " this kernel requires the following features not present on the cpu: pae
unable to boot please use a kernel appropriate for your cpu "


thanks \\

#-o:shock:

---

### Post by matt_symes on 2013-02-24
Hi

Blimey. That PC must be old :) If it's that old tthen it would have had trouble running Unity anyway.

install Lubuntu or Xubuntu as they are non pae

Lubuntu is   the more sparse and, so, faster.

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

Get the 32 bit versions.

You can also install from the mini iso. That will be more of a challange as you will have to install a desktop.

Kind regards

---

### Post by CharlesA on 2013-02-24
> **matt_symes said:**
> You can also install from the mini iso. That will be more of a challange as you will have to install a desktop.

+1. It isn't too much of a challenge though, unless you have issues with the text-based installer because it asks you which packages you want to install during the install process.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

