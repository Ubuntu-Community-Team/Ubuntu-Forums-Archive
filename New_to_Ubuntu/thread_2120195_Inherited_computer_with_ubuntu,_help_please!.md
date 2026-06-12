---
title: "Inherited computer with ubuntu, help please!"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by Eggs N Eggs on 2013-02-25
Hello, as this is my first thread, I would like to introduce myself a little bit. My name is Aaron and I am 16. I am fairly decent with computers, been tinkering with everything I could since I was 12. I know basic computer programming and am pretty well the person people in my family come to when they have a problem with electronics.

Recently, I received a desktop computer from my mom's friend (her son went off to college) and it has ubuntu 10.10 on it. I have never dealt with ubuntu and see this as a possible learning experience for me. The only thing I have successfully done with this computer is remove the old keyring and connect to my wi-fi.
The main problem I wish to deal with is the update manager. I cannot update this computer at all whatsoever. I would like to get the newest version so I can have proper support, but I constantly get an error in the middle of the install that says something about my network connection being bad. I know this is false because, well, I'm on it right now posting this thread.

I would appreciate any help and hope to find this a welcoming community. Thank you.

---

### Post by mikewhatever on 2013-02-25
10.10 is no longer supported - reached EOL in 04.2012. That means, there had been no updates since then, and, in fact, the software repositories (where updates come from) had been removed. 
I'd advise downloading a supported release (12.04 recommended) from ubuntu.com and reinstalling.

---

### Post by deadflowr on 2013-02-25
Assuming that you've downloaded the latest release (either 12.04LTS, or 12.10) as you've stated that the install borks.
Now, how much about the PC do you know?
What wifi adapter does it use?
What graphics card does it use?
CPU?
RAM?

Any information you can provide will be of use.

---

### Post by Eggs N Eggs on 2013-02-25
> **mikewhatever said:**
> 10.10 is no longer supported - reached EOL in 04.2012. That means, there had been no updates since then, and, in fact, the software repositories (where updates come from) had been removed. 
I'd advise downloading a supported release (12.04 recommended) from ubuntu.com and reinstalling.

Well, I went to the website and read the guide ([https://help.ubuntu.com/community/NattyUpgrades](https://help.ubuntu.com/community/NattyUpgrades)) and I continue to get an error message, "Requires installation of untrusted packages" and then the update manager just stops.


> **deadflowr said:**
> Assuming that you've downloaded the latest release (either 12.04LTS, or 12.10) as you've stated that the install borks.
Now, how much about the PC do you know?
What wifi adapter does it use?
What graphics card does it use?
CPU?
RAM?

Any information you can provide will be of use.
Allright, I know a few things
wifi adapter: netgear WG311v3
processor: pentium 4 3.9 GHZ clock speed.
gfx card: unknown
RAM: unknown
I could check the bios if needed for any info that I can get from it.

---

### Post by deadflowr on 2013-02-25
> **Eggs N Eggs said:**
> Well, I went to the website and read the guide ([https://help.ubuntu.com/community/NattyUpgrades](https://help.ubuntu.com/community/NattyUpgrades)) and I continue to get an error message, "Requires installation of untrusted packages" and then the update manager just stops.

Go here and get a fresh copy:

[http://www.ubuntu.com/download/desktop]("http://www.ubuntu.com/download/desktop")

Personally, I'd recommend 12.04 for the longer support period and rock solid stability.
You'll be asked to donate, but it isn't mandatory, you can skip it.

Also preview the page I linked for tips on burning to DVD or USB.

At this point upgrading straight with a fresh install is much safer than trying to upgrade from one release to another to another to another.

---

### Post by Eggs N Eggs on 2013-02-25
> **deadflowr said:**
> Go here and get a fresh copy:

[http://www.ubuntu.com/download/desktop]("http://www.ubuntu.com/download/desktop")

Personally, I'd recommend 12.04 for the longer support period and rock solid stability.
You'll be asked to donate, but it isn't mandatory, you can skip it.

Also preview the page I linked for tips on burning to DVD or USB.

At this point upgrading straight with a fresh install is much safer than trying to upgrade from one release to another to another to another.

Actually, I already downloaded on my other computer and burned it to a disc right here. I had a feeling that's what it would come to, but I avoided it because I didn't want to deal with installing drivers for the wifi adapter and such, but I suppose that is something I will have to learn eventually anyway. If I could get help with that it would be great. I already searched up how to do it and it says that I need specific files to install the windows drivers. I downloaded these but ubuntu is so foreign to me that I can't even follow the instructions properly.

---

### Post by 3rdalbum on 2013-02-26
Ubuntu already contains wireless drivers. It's improbable you would need to install any on Ubuntu 12.04 or 12.10.

---

### Post by sudodus on 2013-02-26
I suggest that you download a flavour of Ubuntu with a light desktop environment, that will run smoother with a Pentium 4 cpu than standard 'vanilla' Ubuntu.

- Xubuntu 12.04 LTS, supported until April 2015, with the light-weight desktop environment XFCE
- Lubuntu 12.10, supported until April 2014, with the ultra light-weight desktop environment LXDE

With some computers you need to add boot options to get it running. As long as you have that old Ubuntu 10.10, you can check if it is run with boot options.

```
less /etc/default/grub
``` and look for a line similar to this one
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```If the boot option nomodeset is used, it could look like this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=Red]nomodeset[/COLOR]"
```--
Anyway, I recommend that you ***try*** to run your Ubuntu flavour live, which means that you boot from a CD or USB drive, and do not install, at least not at once. Instead test how it works, and compare different flavours of Ubuntu. Finally, when you know how it works, you can decide what you want and install it to the internal drive.

---

### Post by mastablasta on 2013-02-26
also command 
 
```
 
lshw 

``` 
in terminal will list all your hardware taht computer can recognise. you can copy the stuff from terminal it and paste it here.
 
i second the Xubuntu idea. Ubuntu 12.04 is totally different. to get similar one you would need to install gnome panel. also you can use Unity 2D in version 12.04 which shoul dbe less resource hungry. 
default Unity 3D desktop needs good hardware acceleration (good graphics card) and takes quite a bit of ram).
 
Xubuntu 12.04 looks and acts preety much like the 10.10 you have now.

---

### Post by andrew.46 on 2013-02-28
> **Eggs N Eggs said:**
> Hello, as this is my first thread, I would like to introduce myself a little bit. My name is Aaron and I am 16. I am fairly decent with computers, been tinkering with everything I could since I was 12. I know basic computer programming and am pretty well the person people in my family come to when they have a problem with electronics.

Welcome to Ubuntu!

---

