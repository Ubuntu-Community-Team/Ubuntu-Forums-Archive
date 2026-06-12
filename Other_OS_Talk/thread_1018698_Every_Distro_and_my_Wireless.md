---
title: "Every Distro and my Wireless"
date: 2008-12-22
forum: Other OS Talk
---

### Post by Xylograph on 2008-12-22
After having ndiswrapper fail on every distro I have tried (Ubuntu, Fedora, PCLOS, SUSE) I decided to install MEPIS off the LXF103 cover DVD (I think it was 103.... the one with the 10 distro mega pack).

The live cd saw the wireless card, and configured it, and I was able to connect to my wireless AP. And get google. And the internet. I was overjoyed!

So, I decided to install it.

After install, I get the message 'MEPIS could not get information from HAL. HAl daemon may not be running' after using MEPIS's network configuration app. Also, when connecting to the AP using Knetworkmanager, it now stops at 28% Configuring Device and then says failed after a few minutes.

The machine is a Compaq laptop, with an AMD Turion64, 512mb ram, ATI200M and a broadcom 4318 AirforceOne wireless card.

---

### Post by Tanis Shadow on 2008-12-22
Erm.... I don't get what your question is.
Are you asking for a solution how to set up your wireless in MEPIS?
Or are you asking if there is another Linux Distro where your wireless might work?

---

### Post by Xylograph on 2008-12-22
Neither. I was asking why it worked on the live cd, and not now its installed. Ive sorted it now though. I reinstalled again and didnt give the laptop a name during the install.

---

### Post by SomeGuyDude on 2008-12-22
One reason I feel fortunate in my Linux hunting is that all of my parts are Intel. Never had a problem with audio, video, or wireless being set up (save in Arch where I didn't read the directions).

Sorry to hear things have been so difficult for you.

---

### Post by jrusso2 on 2008-12-23
> **Xylograph said:**
> After having ndiswrapper fail on every distro I have tried (Ubuntu, Fedora, PCLOS, SUSE) I decided to install MEPIS off the LXF103 cover DVD (I think it was 103.... the one with the 10 distro mega pack).

The live cd saw the wireless card, and configured it, and I was able to connect to my wireless AP. And get google. And the internet. I was overjoyed!

So, I decided to install it.

After install, I get the message 'MEPIS could not get information from HAL. HAl daemon may not be running' after using MEPIS's network configuration app. Also, when connecting to the AP using Knetworkmanager, it now stops at 28% Configuring Device and then says failed after a few minutes.

The machine is a Compaq laptop, with an AMD Turion64, 512mb ram, ATI200M and a broadcom 4318 AirforceOne wireless card.
There are a lot of guides for this wireless have you tried any?

Are you using 64 bit, it might be easier with 32 bit Linux.

[http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto)

[http://blog.roberthallam.org/2008/04/broadcom-4318-ubuntu-hardy-heron-ndiswrapper/](http://blog.roberthallam.org/2008/04/broadcom-4318-ubuntu-hardy-heron-ndiswrapper/)

[https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/222197](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/222197)

---

### Post by Xylograph on 2008-12-23
Yup, Im using 32Bit. 

Its fixed now. I did get it working on the Live CD, but it refused to work after the same steps on the install.

After a reinstall it works now, so there must have been an error during the install process.

Thanks for the help anyway though!

---

