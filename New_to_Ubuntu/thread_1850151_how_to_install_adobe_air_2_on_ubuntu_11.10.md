---
title: "how to install adobe air 2 on ubuntu 11.10?"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by soylentcola on 2011-09-25
So, being that guy that has to be first, I installed Ubuntu 11.10 but now I'm trying to install Adobe AIR 2 through the terminal but running the instructions from the adobe air page [here]("http://kb2.adobe.com/cps/521/cpsid_52132.html#main_Install_AIR_2_on_64_bit_Ubuntu_9_04") (granted it's for 11.10 I figured the concepts were the same?) aren't working.  So can anyone guide me through this? Thanks in advance!

---

### Post by graingert on 2011-10-08
No this is the wrong way of installing adobeair on Ubuntu 11.10

You are looking at the 64-bit version and thanks to multi-arch support most of the instructions are no longer needed.

---

### Post by Redblade20XX on 2011-10-08
> **graingert said:**
> No this is the wrong way of installing adobeair on Ubuntu 11.10

You are looking at the 64-bit version and thanks to multi-arch support most of the instructions are no longer needed.

Yeah this is kind of the wrong way to do this. From 9.04 to 11.10, is a pretty big leap and there were massive changes so the instructions might be invalid.

-Red

---

### Post by graingert on 2011-10-08
wait for [https://launchpad.net/ubuntu/+source/adobeair](https://launchpad.net/ubuntu/+source/adobeair) to be released in oneiric

---

### Post by cheesekiller on 2011-10-13
will they have adobe air for oneric?   i actually really am in need of it asap i've had a hard time installing 11.10 and i have work to do but i require the use of an adobe air program to do it

---

### Post by Donenzone on 2011-10-14
For the time being, if you install ia32-libs Adobe AIR works if you use [this]("http://ubuntuone.com/p/euK/") .deb to install it.

---

### Post by fscalc on 2011-10-14
Employing the advice from the URL (below), I was able to install Adobe Air (and play Dofus) under Ubuntu 11.10 64-bit.

 [http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
 
 The section on Adobe Air can be found near the bottom of the post:
 
 > **Adobe Air**
 Special Note: *Beginning June 14 2011, Adobe AIR is no longer supported for desktop Linux distributions. Users can install and run AIR 2.6 and earlier applications but can&#8217;t install or update to AIR 2.7. The last version to support desktop Linux distributions is AIR 2.6. AIR 2.6 is available from the AIR Archive.*

 wget [http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin](http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin) 
chmod +x ./AdobeAIRInstaller.bin 
sudo ./AdobeAIRInstaller.bin 

**or if you have a 64 bit version of Ubuntu then you will need to install:**
 sudo apt-get install ia32-libs 
wget [http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin](http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin) 
chmod +x ./AdobeAIRInstaller.bin 
sudo ./AdobeAIRInstaller.bin  

Access it through Applications &#8594; Accessories &#8594; Adobe Air Application Installer.

 Good luck!
 -fscalc

---

### Post by cheesekiller on 2011-10-16
> **fscalc said:**
> Employing the advice from the URL (below), I was able to install Adobe Air (and play Dofus) under Ubuntu 11.10 64-bit.

 [http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
 
 The section on Adobe Air can be found near the bottom of the post:
 
 

 Good luck!
 -fscalc

win!

---

### Post by tsuujin on 2012-03-02
No dice.

I'm informed that I need to install gnome-keyring (even though it's already installed) and the install fails.

---

### Post by Paddy Landau on 2012-03-02
According to the Adobe website:
> Adobe AIR for Linux is no longer supported.I think you need to reconsider; either stop using it, or use it on Windows or Mac.

---

### Post by dekom on 2012-03-10
I was able to Adobe Air 2 on my installation working by following these directions:

[http://xingzhou.me/2012/03/10/install-adobe-air-2-on-ubuntu-64-bit](http://xingzhou.me/2012/03/10/install-adobe-air-2-on-ubuntu-64-bit)

Ubuntu 11.10 64-bit

Hope that helps!

---

