---
title: "How to get Unbuntu Core 21.01"
date: 2022-04-30
forum: New to Ubuntu
---

### Post by chat-4432 on 2022-04-30
That support PiZero2W
or who can make this os??

---

### Post by QIII on 2022-04-30
Do you mean Ubuntu Core 22?

---

### Post by chat-4432 on 2022-04-30
> **QIII said:**
> Do you mean Ubuntu Core 22?
Yes, you have it?

---

### Post by QIII on 2022-04-30
No. I don't work for Canonical -- nor does anybody else here.

You need to get it from Canonical [here]("https://cdimage.ubuntu.com/ubuntu-core/22/dangerous-edge/pending/").

However, I can't begin to guess how stable it might be at this point.

---

### Post by guiverc on 2022-04-30
Try [https://ubuntu.com/download/iot](https://ubuntu.com/download/iot)

Ubuntu releases using the *year.month* format are different products to those using the*year* format.

Your title was 21.01 or the 2021-January release; of which there is none.

Ubuntu Core 22 is a *year* or *snap only* product of Ubuntu, thus is a different system to the *year.month* format of your title.  It's possible you were wanting the Ubuntu 21.10 or 2021-October product, which is again different to Ubuntu Core 22.

Your details are unclear.  The [latest *release announcement *of Ubuntu 22.04 LTS  ]("https://fridge.ubuntu.com/2022/04/21/ubuntu-22-04-lts-jammy-jellyfish-released/")(*one of anyway*) contains many links that lead to specific downloads and maybe helpful.

Ubuntu Core is a *year* format product.

---

### Post by chat-4432 on 2022-05-01
> **QIII said:**
> 
However, I can't begin to guess how stable it might be at this point.
Did you know how to configure boost at the 1st time?

---

### Post by chat-4432 on 2022-05-01
> **chat-4432 said:**
> Did you know how to configure boost at the 1st time?
no ssh keys found

---

### Post by grahammechanical on 2022-05-01
Are you sure that you can install Boost on Ubuntu Core. As far as I can tell Boost downloads as a compressed file. Ubuntu Core is a Snap based OS and only snap packaged applications will run on it. I cannot see Boost offered as a snap application. Can you provide a link to where you downloaded Boost from? I see this.

[https://boostorg.jfrog.io/artifactory/main/release/1.79.0/binaries/](https://boostorg.jfrog.io/artifactory/main/release/1.79.0/binaries/)

I see Windows exe files which will not install on any version of Ubuntu whether Desktop, Server or Core.

As for "no ssh keys found" comment I ask have you imported a ssh key into your Ubuntu Single Sigh On (SSO) account?

[https://ubuntu.com/download/raspberry-pi-core](https://ubuntu.com/download/raspberry-pi-core)

Regards

---

### Post by chat-4432 on 2022-05-01
> **grahammechanical said:**
> 
As for "no ssh keys found" comment I ask have you imported a ssh key into your Ubuntu Single Sigh On (SSO) account?

[https://ubuntu.com/download/raspberry-pi-core](https://ubuntu.com/download/raspberry-pi-core)

Regards
I got this message in terminal
No route to host 
What should i do??

---

### Post by chat-4432 on 2022-05-01
> **chat-4432 said:**
> I got this message in terminal
No route to host 
What should i do??
I need to use another pc?

---

### Post by TheFu on 2022-05-01
Ubuntu Core is not meant for end users. It is meant for companies trying to create IoT solutions.
So, that's the first question, is Ubuntu Core appropriate for you?

---

### Post by chat-4432 on 2022-05-03
> **TheFu said:**
> Ubuntu Core is not meant for end users. It is meant for companies trying to create IoT solutions.
So, that's the first question, is Ubuntu Core appropriate for you?
I want to run exe software so you have an advice?

---

### Post by chat-4432 on 2022-05-03
> **chat-4432 said:**
> I want to run exe software so you have an advice?
I have try wine x86 but It can't boost

---

### Post by QIII on 2022-05-03
Again, as Thefu said:  Ubuntu Core is not intended to be a desktop.  It is a for IoT development.

What .exes do you think you want to run?  Without a GUI, you're not likely to get anything to work with Wine -- if  you can even get it installed properly.

What is your intent with this?  Do you understand that Ubuntu Core is not intended to be anything at all like a desktop?

---

### Post by chat-4432 on 2022-05-03
> **QIII said:**
> 

What .exes do you think you want to run?  Without a GUI, you're not likely to get anything to work with Wine -- if  you can even get it installed properly.


Metatrader,my mistake to think that unbuntu core have a GUI.

---

### Post by TheFu on 2022-05-03
> **chat-4432 said:**
> I want to run exe software so you have an advice?

'exe' software?  Huh?  Do you mean Windows software?  That won't work on ARM running a non-Windows OS.
You shouldn't be looking at any R-pi or "ubuntu core" at all.  Forget about WINE on any Pi. Honestly, it is bad enough on x86-64 computers.

You could probably follow a how-to guide with pre-built Pi0-W projects. I'd suggest you do that first to get a feel for what is required.

If you don't have a year of Linux experience, I doubt you'll get much working on a Pi-Zero, without perfect, step-by-step, guides.

A raspberry pi is used best as a web-server with only a web interface.  The most powerful R-Pi v4 with 4G-8G of RAM can be used as a slow desktop, but those cost much more than a cheap, used, x86 computer.  Pi computers are best when they are running purpose-built software that does 1 thing.  I have 2 pis. They are used as media center players. That only works because I run a stripped version of Kodi and all media comes from the network. Also, I don't use wifi with either, so the network connection is wired ethernet and fast enough to stream 720p content that is on the same LAN.  

I'm just trying to lay out the challenges.  Some people say that I'm a pessimist. I see issues. Things that are likely to fail.  OTOH, you may be a wiz at all this stuff and pick it up very fast. We don't know.  Effort can make up for lack of knowledge and does all the time.

---

### Post by QIII on 2022-05-03
> **chat-4432 said:**
> Metatrader,my mistake to think that unbuntu core have a GUI.

You might be able to add a GUI to Ubuntu Core and the Pi Zero does have a mini HDMI.  But since the Pi Zero sports only 512MB of RAM, it would probably become unusable.

The point is still that the Pi Zero has a very narrow range of use-cases, and you are not in it.

Ubuntu Core is for IoT.  The Pi Zero is for IoT.

---

### Post by grahammechanical on 2022-05-03
> I have try wine x86 but It can't boost

What computer hardware and what operating system did you install Wine x86 on? I doubt very much that you tried this on Ubuntu Core because as I said previously only applications packaged a Snap application will run on Ubuntu Core. I do not think that Wine has been packaged as a Snap. There are certain Windows programs (exe files) that have been packaged as Snap applications. The "Snap" will contain relevant Wine libraries that the program needs. Alternatively the Snap packaged Windows program will call libraries that are in the wine-platform-runtime which might need to be installed separately.

[https://snapcraft.io/wine-platform-runtime](https://snapcraft.io/wine-platform-runtime)

I searched the Ubuntu Snap store (Snapcraft.io) using "wine" as the search term and came up with this.

[https://snapcraft.io/search?q=wine](https://snapcraft.io/search?q=wine)

I do not think that you will find Boost listed as a Windows program that has been converted into a Snap application and making use of Wine.

If you really need this Boost program then use the Ubuntu Desktop operating system and install Wine from the Ubuntu software centre. If you need help using Wine and getting Windows programs to run under Wine. Then ask another question in a another section of this forum.

[https://www.winehq.org/](https://www.winehq.org/)

[https://appdb.winehq.org/](https://appdb.winehq.org/)

Do  not expect things to be easy and do not expect every Windows program to  work successfully. If you have problems please give details of what you  tried and what went wrong. 

If you are wanting to run a single program on a device with a small size Ubuntu operating system then the Ubuntu Kiosk idea might be what you are looking for.

[https://ubuntu.com/tutorials/secure-ubuntu-kiosk#1-overview](https://ubuntu.com/tutorials/secure-ubuntu-kiosk#1-overview)

Or, you might try installing Ubuntu 22.04 LTS using the Minimal install option. That will provide the Gnome3 desktop environment and the Gnome3 shell user interface that comes with the normal Ubuntu installation but with the difference of having a web browser and a basic set of utilities. This will take up less storage space and you might be satisfied install Wine and then trying to get Boost loading under Wine.

Regards

---

### Post by TheFu on 2022-05-03
WINE is a translation layer from win32/win64 to what Linux expects.  It is not an emulator like QEMU.  There's no way that an exe file created for an x86 machine will run on ARM under WINE.  It just won't work. Ever.

---

### Post by chat-4432 on 2022-05-04
> **grahammechanical said:**
> 
Or, you might try installing Ubuntu 22.04 LTS using the Minimal install option. That will provide the Gnome3 desktop environment and the Gnome3 shell user interface that comes with the normal Ubuntu installation but with the difference of having a web browser and a basic set of utilities. This will take up less storage space and you might be satisfied install Wine and then trying to get Boost loading under Wine.

Regards
How can i install gnome3 desktop environment do you have a guide?

---

### Post by chat-4432 on 2022-05-04
> **chat-4432 said:**
> How can i install gnome3 desktop environment do you have a guide?
I dont know what package name is.

---

### Post by TheFu on 2022-05-04
> **chat-4432 said:**
> How can i install gnome3 desktop environment do you have a guide?

22.04 has Gnome 4.2, not Gnome3.
Also, the minimum RAM for any Ubuntu-flavor desktop has got to be 2G, so a Pi-0 just doesn't have that.

A pi-0 is supposed to be used for a small web server where speed isn't important. Only a console (txt) or ssh or webapp interface is expected.  The wifi aspect really limits the usefulness from a 'server' standpoint.  The main purpose for it that I could guess would be as a remote, wifi, security camera - after you add $75 in video and battery to it.  It can stream over wifi video or snap photos every 30 seconds and push those to another system using scp/sftp.

Even if you get a desktop running, it will be terrible.

---

