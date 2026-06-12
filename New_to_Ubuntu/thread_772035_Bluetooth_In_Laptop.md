---
title: "Bluetooth In Laptop"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by KMuchane on 2008-04-28
Hi,

I posted a question about bluetooth in this forum a few days ago. I was advised that because the commands lspci and lsusb did not output anything with bluetooth, I should buy a bluetooth adapter. Many things have conspired to prevent me from buying that dongle. Well, today I was checking something in the boot up messages and when I ran dmesg, I saw something with bluetooth in it! So I filtered dmesg through grep and got this:

[   35.076000] Bluetooth: Core ver 2.11
[   35.076000] Bluetooth: HCI device and connection manager initialized
[   35.076000] Bluetooth: HCI socket layer initialized
[   35.092000] Bluetooth: L2CAP ver 2.8
[   35.092000] Bluetooth: L2CAP socket layer initialized
[   35.308000] Bluetooth: RFCOMM socket layer initialized
[   35.308000] Bluetooth: RFCOMM TTY layer initialized
[   35.308000] Bluetooth: RFCOMM ver 1.8

It may be nothing but does it mean I have bluetooth adapter on my machine and why does not Ubuntu recognize it?

Thanks!

---

### Post by encompass on 2008-04-28
It just might be... do you have a bluetooth symble that shows up on your desktop?
And you can try this...
hcitool scan

---

### Post by KMuchane on 2008-04-28
Hi,

I have ran hcitool scan with my phone's bluetooth on but it promptly returns:  "Device is not available. No such device. " I do not have a bluetooth runic but I seem to vaguely recall it was there sometimes... 
I use my cellphone as a USB connected modem to connect to the internet and I wanted to free up one USB port by using bluetooth instead of a USB cable... 

Thanks!

---

### Post by reyhan on 2008-04-28
Do you need Bluetooth manager?
if yes follow this Guide 

Download repository for ubuntu:

Paste following lines to console to add blueman repository to the package manager:
echo 'deb [http://download.tuxfamily.org/blueman](http://download.tuxfamily.org/blueman) ubuntu bluetooth' | sudo tee /etc/apt/sources.list.d/blueman.list

And import the GPG key:

wget [http://download.tuxfamily.org/blueman/repository.gpg](http://download.tuxfamily.org/blueman/repository.gpg) -O- | sudo apt-key add -

Then you can install blueman from Synaptics as any other program.

To uninstall blueman, simply uninstall it using Synaptics and lastly remove blueman reposiroty with command:
sudo rm /etc/apt/sources.list.d/blueman.list

---

### Post by encompass on 2008-04-28
Everything you need should be in the repos that are there now... sure you could install it... but you won't get much help from me. :D
You may still have it...
Check if you have any bluetooth buttons and make sure that you have pressed them to see if the lights come on or show up on the screen.
You could also look up your model of computer and see if they have it mentioned there too.

---

### Post by phreakaholic on 2008-04-28
try hcitool scan first, it might be help :)

---

### Post by KMuchane on 2008-04-28
Hi,

For one I would like to know what the dmesg output I posted above means. 
Googling the make of my laptop - a HP 510 - gives conflicting results.    And trying to get the GPG key from blueman responds with: "no valid  OpenPGP data found. " And also I cannot see any buttons that I have not switched on, there are only two after all!

---

### Post by omns on 2008-05-02
I to have this same problem on an Acer Travelmate. I get the same dmesg results but it appears to be unrecognised in lspci. I'm also reluctant to fork out for a bluetooth dongle when I have bluetooth already there. This one is driving me nuts.

---

### Post by omns on 2008-05-02
Blueman doesn't help

---

### Post by encompass on 2008-05-02
could you post these outputs in something
```

like this...
lsusb

```
and
```

lspci

```
And for good measure...
```

sudo lshw

```
This will check your hardware and tell us what you have...

---

### Post by omns on 2008-05-03
Oh good grief ](*,) It appears I've only half checked the features of this new machine that I've been given at work. Thanks for your help and ignore my previous posts

---

### Post by encompass on 2008-05-03
nice computer... but I don't think it has bluetooth.  And your fingerprint reader is being worked on, but for now, doesn't have any good support.  Sorry.

---

### Post by omns on 2008-05-03
> **encompass said:**
> nice computer... but I don't think it has bluetooth.  And your fingerprint reader is being worked on, but for now, doesn't have any good support.  Sorry.

no, no Bluetooth and the finger print reader is a pain in the proverbial anyway. It's one of the first things I removed in Windows when I got it. I can see the value of such a device but it's not necessary in may case and was just another service bogging things down. I'm glad I only have to boot into it a couple of times a week.

---

### Post by Angel4Life on 2008-06-30
Hi, I had similar problems and tried surfing the net and got no where, so I fiddled with the computer a bit and found the answer,I hope it also the answer to your problem.
Kind regards
K.Wright

Windows Mobility Center
The Windows Mobility Center collects key mobile-related system settings in one
easy-to-find place, so you can quickly configure your Acer system to fit the
situation as you change locations, networks or activities. Settings include display
brightness, power plan, volume, wireless networking on/off, external display
settings, display orientation and synchronization status.
Windows Mobility Center also includes Acer-specific settings like Bluetooth Add
Device (if applicable), sharing folders overview/sharing service on or off, and a
shortcut to the Acer user guide, drivers and utilities.
To launch Windows Mobility Center:

• Start Windows Mobility Center from the Accessories program group in the
Start menu

---

