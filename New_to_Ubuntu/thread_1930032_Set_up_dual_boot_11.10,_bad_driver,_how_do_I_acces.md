---
title: "Set up dual boot 11.10, bad driver, how do I access recovery mode?"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by tastycakeman on 2012-02-23
Hello! 

I just got a new Samsung Series 7 with all the fanciest schwag (ATI radeon 6750), and I installed dual boot 11.10. 

Before, I had been able to boot into Ubuntu and fiddle around. I then updated some video drivers without thinking any problems would arise.

Now, it won't boot into Ubuntu. I can't even boot into recovery mode, so I have no idea how to even access any recovery terminal to check what's wrong.

I'm a ubuntu newbie and don't really know my way around manually changing drivers, etc. Is there anything I can do short of reinstalling it, or is there a lot of knowledge already in terms of fixing these bad drivers for the radeon hardware?

---

### Post by mastablasta on 2012-02-23
you probably have hybrid graphich, huh? if so latest driver has to be separatelly installed for them to work.
 
here is how your remove the driver: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
 
you can get to command line by holding shift on boot and then botoing into recovery mode or maybe there is a CLI mode.
 
then you need ot manually install latest ATI linux drivers (i think 12.1 or something) and then dont' forget to configure them once they are installed.: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by tastycakeman on 2012-02-23
OK, so I tried booting into recovery mode but nothing worked. I even booted into grub? I tried stuff, but nothing worked.

So I uninstalled 11.10, and am going to try again. Should I try 10.10? Or is there something I can do this time around, like avoid updating the drivers, to prevent it from happening again?

I just want something that works!

---

### Post by Mark Phelps on 2012-02-23
Avoid installing the restricted drivers -- unless the default drivers simply do not work.  Unless you really need 3D hardware acceleration for gaming, you will be able to do fine on the default open-source radeon drivers. These are installed as part of the initial setup of Ubuntu.

---

### Post by mastablasta on 2012-02-23
> **Mark Phelps said:**
>  Unless you really need 3D hardware acceleration for gaming, you will be able to do fine on the default open-source radeon drivers. These are installed as part of the initial setup of Ubuntu.
 
But if they have hybrid graphics they will drain the battery, no?
 
i would say install as first time and then instead of installing proprietary graphic drivers (it would install older verison) download the latest linux drivers found on AMD page and manually install those.
 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
 
they should work well with your card.
 
here is a bit easier howto: [http://www.upubuntu.com/2012/01/how-to-install-ati-amd-catalyst-121.html](http://www.upubuntu.com/2012/01/how-to-install-ati-amd-catalyst-121.html)
(obviously you don't need to remove previous driver since you won't install it.
 
possible issues...:
[http://ubuntuforums.org/showthread.php?t=1915488](http://ubuntuforums.org/showthread.php?t=1915488)
 
more help and howto:
[http://ubuntucomputing.posterous.com/amd-catalyst-121-driver-on-hp-pavilion-dv6t-q](http://ubuntucomputing.posterous.com/amd-catalyst-121-driver-on-hp-pavilion-dv6t-q)
 
EDIT: i just feel i should add that this new driver will probably be included in next version of OS and then the install will go again the easy way via the GUI interface. :-)

---

### Post by tastycakeman on 2012-02-23
Heh. Ok, so, erm...

I guess I'm having trouble even uninstalling the ubuntu from windows. 

I used the Wubi uninstaller to remove it, but when I go to re-install, it doesn't work. I get a variety of errors, tried 3 times now. 

Is it because of some remnants or something I have to manually remove? Not sure what's going on here.

---

### Post by tastycakeman on 2012-02-24
So, I uninstalled and reinstalled. Had a few strange issues. 

Anyways, I got it to work and to boot into ubuntu. However, now whenever I start up, it boots into grub. Then I get stuck...

---

### Post by tastycakeman on 2012-02-24
I'm planning on documenting all of this at some point, but last night I was up until 4 in the morning configuring the install. I got almost everything perfect in terms of touchpad, power usage, etc.

However, now when I booted it up in Ubuntu today, it gives me the purple screen.

I tried booting into recovery mode for kernel 3.2.2 or something like that, and dead. Then I try booting into previous kernel 3.2.0-generic.12, and it's just dead altogether. Nothing responds, fan turns off, and I have to wait until the battery runs down and end up coming close to melting the cpu. What. the. ****.

Currently trying to figure this bug out, of having a fresh install and then getting purple screens. This is super common, but the causes are varied. I've a hunch it's related to hybrid graphics.

---

