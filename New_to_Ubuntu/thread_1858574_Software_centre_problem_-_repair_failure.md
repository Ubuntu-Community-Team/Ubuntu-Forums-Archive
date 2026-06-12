---
title: "Software centre problem - repair failure"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by l_mac on 2011-10-12
Hi, I've just installed Ubuntu 11.04 for the first time (a fresh install on a PC I've been having tons of Windows crashes with). It seemed to be running fine, I did a whole host of system test without any issues, but I have now hooked it up to the internet, and hit a problem with the Software Centre.  Can anyone help?

I did two things without any problems. Prompted by Ubuntu I downloaded and installed updated NVIDIA drivers, and also the Ubuntu Restricted Extras package. However, I then tried to install VLC Media Player and I got an error message in the Software Centre saying it had failed to install.

When I tried to re-open Software Centre it stated:

"Items cannot be installed or removed until the package catalogue is repaired. Do you want to repair it now?"

I clicked to repair but it won't work, it returns the error message: "Package operation failed", with the following details:

Unpacking libqtgui4 (from .../libqtgui4_4%3a4.7.2-0ubuntu6.3_amd64.deb) ... 
 xz: (stdin): Compressed data is corrupt 
 dpkg-deb: error: subprocess <decompress> returned error exit status 1 
 dpkg: error processing /var/cache/apt/archives/libqtgui4_4%3a4.7.2-0ubuntu6.3_amd64.deb (--unpack): 
  short read on buffer copy for backend dpkg-deb during `./usr/lib/libQtGui.so.4.7.2' 
 Errors were encountered while processing: 
  /var/cache/apt/archives/libqtgui4_4%3a4.7.2-0ubuntu6.3_amd64.deb 
 dpkg: dependency problems prevent configuration of appmenu-qt: 
  appmenu-qt depends on libqtgui4 (>= 4:4.7.1-0ubuntu7); however: 
   Package libqtgui4 is not installed. 
 dpkg: error processing appmenu-qt (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of vlc: 
  vlc depends on libqtgui4 (>= 4:4.5.3); however: 
   Package libqtgui4 is not installed. 
 dpkg: error processing vlc (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of libdbusmenu-qt2: 
  libdbusmenu-qt2 depends on libqtgui4 (>= 4:4.7.0~beta2); however: 
   Package libqtgui4 is not installed. 
 dpkg: error processing libdbusmenu-qt2 (--configure): 
  dependency problems - leaving unconfigured

---

### Post by matt_symes on 2011-10-12
Hi

I am not sure if software center sits on apt but try this. 

Open a terminal and type

```
sudo apt-get clean
```

Enter your password. It will not be echoed to the screen.

After that attempt to install vlc again.

Kind regards
[COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#222222][FONT=Ubuntu Mono][/FONT][/COLOR][/LEFT][/FONT][/COLOR]

---

### Post by wolfen69 on 2011-10-12
You probably need to enable the proper repositories. Open Synaptic Package Manager and go to Settings>Repositories and make sure everything is checked off. Check the *Other Software* tab too. Close and reload when prompted.

---

### Post by wolfen69 on 2011-10-12
> **matt_symes said:**
> 

I am not sure if software center sits on apt 



Yes it does "sit" on apt. The software center is just a gui front end for apt, just like synaptic.

---

### Post by matt_symes on 2011-10-12
Hi

> **wolfen69 said:**
> Yes it does "sit" on apt. The software center is just a gui front end for apt, just like synaptic.
> 
Unpacking libqtgui4 (from .../libqtgui4_4%3a4.7.2-0ubuntu6.3_amd64.deb) ... 
 xz: (stdin): Compressed data is corrupt 
 dpkg-deb: error: subprocess <decompress> returned error exit status 1 
 dpkg: error processing /var/cache/apt/archives/libqtgui4_4%3a4.7.2-0ubuntu6.3_amd64.deb (--unpack): 
  short read on buffer copy for backend dpkg-deb during `./usr/lib/libQtGui.so.4.7.2' Then these packages need to be cleaned ? It's a corrupted package that is causing the problem.

I never use the software centre so.....
> 
You probably need to enable the proper repositories. Open Synaptic  Package Manager and go to Settings>Repositories and make sure  everything is checked off. Check the *Other Software* tab too. Close and reload when prompted.

This performs the same action ?

Kind regards

---

### Post by l_mac on 2011-10-12
Cheers guys. I tried the sudo apt-get clean first, however when I opened Synaptic Package Manager it reported three broken packages? Ticking a couple of unchecked items under other software and okaying that led onto it updating some packages (properly installing VLC and whatever else was broken) and it all seems to be working fine now. 

Ta much!

---

### Post by matt_symes on 2011-10-12
Hi

> **l_mac said:**
> Cheers guys. I tried the sudo apt-get clean first, however when I opened Synaptic Package Manager it reported three broken packages? Ticking a couple of unchecked items under other software and okaying that led onto it updating some packages (properly installing VLC and whatever else was broken) and it all seems to be working fine now. 

Ta much!

I'm glad you got it sorted :) 

Kind regards

---

