---
title: "downloaded .deb files wont install ubuntu 20.10"
date: 2021-01-25
forum: New to Ubuntu
---

### Post by awildner on 2021-01-25
Disclaimer: Totally new to Linux, just made my pilgrimage from Mac OS

Background: Installed Ubuntu 20.10 on a brand new hard drive. I've had some problems with the Ubuntu Software app loading. I've clutzed my way through a few problems but I continue to run into new ones.

Problem: Currently trying to install Digilent Adapt runtime & Waveforms. I've downloaded the .deb files via the Firefox browser and it's currently in my downloads folder. When I attempt to install it with Ubuntu Software it loads indefinitely and never gets to the install prompts. When I've tried to install via the terminal, through code I've seen suggested to people in similar situations (albeit on older platforms of ubuntu), I've had no luck. The short of it is I don't know the language or understand what I'm doing in terminal.

Thank you in advance for any help offered.

---

### Post by CelticWarrior on 2021-01-25
Welcome.

Please share the exact software you're trying to install. It may not be compatible with your release.
Also please make sure it's fully updated before using the "app store". In terminal:
```
sudo apt update && sudo apt full-upgrade
```
If any error reported please post it here in full.

---

### Post by awildner on 2021-01-25
The soft ware I'm attempting to install is titled  digilent.adapt.runtime_2.21.2-amd64.deb the version for Linux 64-bit  which can be found here:  [https://mautic.digilentinc.com/adept-runtime-download](https://mautic.digilentinc.com/adept-runtime-download) 
& Waveforms (also Linux 64-bit) can be found here: [https://mautic.digilentinc.com/waveforms-download](https://mautic.digilentinc.com/waveforms-download)

Here is the error the code produced:

E:  Malformed entry 1 in list file  /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_focal-groovy.list  (Component)
E: Malformed entry 1 in list file  /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_groovy-groovy.list  (Component)
E: The list of sources could not be read.

I did look into installing wine at some point last night...

---

### Post by QIII on 2021-01-25
Hello!  Welcome to the forums.

This is not intended to be a nitpick, just some advice on how to get a better answer more quickly.  We'd like to help you be successful!


> 
I've had some problems with the Ubuntu Software app loading.

A description would be helpful.  What problems?  Can you capture and post a screen shot?

> I've clutzed my way through a few problems but I continue to run into new ones.

This is vague and doesn't help us understand.  Best to deal with one thing at a time, so you probably could have skipped that sentence.

> Problem: Currently trying to install Digilent Adapt runtime & Waveforms.

A link describing this might be helpful.

> I've downloaded the .deb files via the Firefox browser

From where?

> When I attempt to install it with Ubuntu Software it loads indefinitely and never gets to the install prompts.

Again, a better description or an image might help us understand.

>  When I've tried to install via the terminal, ... I've had no luck. 

Can you post your commands and the results.  "No luck" doesn't help us understand.

> through code I've seen suggested to people in similar situations (albeit on older platforms of ubuntu)

Where did you see these suggestions?  We can take a look if we have a link.  How old are they?  

> I don't know the language or understand what I'm doing in terminal.

Unfortunately, we don't know what you're doing in the terminal either, so we can't take even the vaguest guess at what it wrong.


Please take this as good-natured advice.  We can help only to the extent that we have good information

---

### Post by awildner on 2021-01-25
Thank you for the pointers

1. I don't know how to post a photo via a URL, but the Ubuntu Software app opens, the view of the app stays grey, or blank, with the "loading blue Ubuntu icon" in the middle remaining indefinitely. 

2. these are the apps and the locations I downloaded them from:
[https://mautic.digilentinc.com/adept-runtime-download](https://mautic.digilentinc.com/adept-runtime-download)
[https://mautic.digilentinc.com/waveforms-download](https://mautic.digilentinc.com/waveforms-download)

---

### Post by awildner on 2021-01-25
For further reference I downloaded Ubuntu 20.10 from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop) , flashed a usb drive and booted from that. 

Update: in Settings > About> Software Updates> Other Software, there I found 3 boxes checked - [https://dl.winehq.org/wine-builds/ubuntu/groovy](https://dl.winehq.org/wine-builds/ubuntu/groovy) main , [https://dl.winehq.org/wine-builds/ubuntu/focal](https://dl.winehq.org/wine-builds/ubuntu/focal) main, and yet another [https://dl.winehq.org/wine-builds/ubuntu/groovy](https://dl.winehq.org/wine-builds/ubuntu/groovy) main.

I unchecked them, checked Canonical Partners, and ran the code:
sudo apt update && sudo apt full-upgrade

[FONT=arial]This appears to have run successfully [/FONT][FONT=arial]
[/FONT]

---

### Post by awildner on 2021-01-25
That worked, thank you.

---

