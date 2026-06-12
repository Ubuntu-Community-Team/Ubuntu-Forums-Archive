---
title: "Nokia Suite"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by Yezinki on 2013-04-21
Can one run Nokia Suite on Ubuntu OR can Wine help OR would have to install Vbox & windows?

Thanks.

---

### Post by stevesy on 2013-04-26
> **Yezinki said:**
> Can one run Nokia Suite on Ubuntu OR can Wine help OR would have to install Vbox & windows?

Thanks.

[http://ubuntuforums.org/showthread.php?t=1981335](http://ubuntuforums.org/showthread.php?t=1981335)

---

### Post by basso-zeca on 2013-08-26
> **stevesy said:**
> [http://ubuntuforums.org/showthread.php?t=1981335](http://ubuntuforums.org/showthread.php?t=1981335)

The thread states that it is possible to use the phone mobile internet by connecting the phone with a USB cable. 
But what if I need the internet connection and I don't have the USB cable? Is it possible to the same using bluetooth connection between the phone and the PC without additional software?

---

### Post by stevesy on 2013-08-26
> **basso-zeca said:**
> The thread states that it is possible to use the phone mobile internet by connecting the phone with a USB cable. 
But what if I need the internet connection and I don't have the USB cable? Is it possible to the same using bluetooth connection between the phone and the PC without additional software?

It would appear so:

[http://askubuntu.com/questions/158942/connect-my-mobile-phone-as-modem-via-bluetooth](http://askubuntu.com/questions/158942/connect-my-mobile-phone-as-modem-via-bluetooth)

[http://mobileoffice.about.com/od/phonesformobileworkers/ht/bluetooth-cellphone-as-a-modem.htm](http://mobileoffice.about.com/od/phonesformobileworkers/ht/bluetooth-cellphone-as-a-modem.htm)

AFAIK bluetooth will be a little slower than a usb connection but handier in terms of moving the phone about while your connected.

HTH

---

### Post by basso-zeca on 2013-08-27
> **stevesy said:**
> It would appear so:

[http://askubuntu.com/questions/158942/connect-my-mobile-phone-as-modem-via-bluetooth](http://askubuntu.com/questions/158942/connect-my-mobile-phone-as-modem-via-bluetooth)

[http://mobileoffice.about.com/od/phonesformobileworkers/ht/bluetooth-cellphone-as-a-modem.htm](http://mobileoffice.about.com/od/phonesformobileworkers/ht/bluetooth-cellphone-as-a-modem.htm)

AFAIK bluetooth will be a little slower than a usb connection but handier in terms of moving the phone about while your connected.

HTH

That looks great stevesy! Thank you very much for your reply. Unfortunately I have already wasted some hours trying to make it work with no success.

First of all, to make things clear, I am using Xubuntu 13.04. 
I' m able to create and supposedly establish a DUN connection with my mobile under Bluetooth Manager.
I 'm also able to create a Mobile Broadband connection and setup my operator under the Connection Manager. 
Nevertheless, it seems like there is something missing, as the Mobile Broadband connection doesn't appear as an option under the Connection Manager.

I found that Network Access Point (NAP) service was disabled. As that doesn't seemed right, I enabled it. Additionally, I had also tested PAN and DUN support with both NetworkManager and Blueman without success.

Am I missing something? Does nokuntu or another similar program supports automatically this kind of configuration?

---

### Post by coldraven on 2013-08-28
I think it depends on which Nokia phone that you have.
I tried with my C1-01, it links with bluetooth but the phone does not have modem capability.
The Nokia site is a bit vague on the subject.

To update the phone's software I installed the Nokia Suite in XP. What a performance, about 2GB of bloat in order to use one small update program.
To backup my contacts i just use gammu via bluetooth. The Nokia Suite never got used again.

---

### Post by basso-zeca on 2013-08-28
Hey coldraven, thank you for your reply!

I am using a 5800 express music. It has a [custom firmware]("http://www.symbianlatino.com/2012/08/symbian-anna-v79-para-nokia-5800-5530.html") with all the latest official features and some more.
In a windows machine I am able to fully operate the phone with Nokia Suite through bluetooth, including the use of mobile broadband. 

That being said, I can't confirm if the phone has natively a modem capability, or if it can only be achieved with Nokia Suite in a windows machine.
But I'll definitely give gammu a try for my daily phone management and contact backup as soon as I arrive home.

---

### Post by coldraven on 2013-08-28
The last part of this post might help:
[http://ubuntuforums.org/showthread.php?t=1737148](http://ubuntuforums.org/showthread.php?t=1737148)

Once you have configured your .gammurc file  it is a one liner to backup or restore your contacts.
This is a lot better and faster than using the Nokia Suite.
All I have to do is this:
```
gammu --backup my_contacts.lmb
```

Enjoy :)

---

### Post by charles-meo on 2013-10-03
All,

Been messing around with this for the last 24 hours and found a bit of a mixed bag.
Phone: Nokia E66. Old but I like it
Ubuntu: 13.04 and 13.10 dev branch

Objective: access mass storage USB device on phone
Secondary objective: use USB connection to phone modem for internet access when no WLAN or wired network is available.

So the secondary part works and always has right out of the box. The primary part has proved impossible.

While lsusb shows the device being attached as /dev/sdb or /dev/sdc, fdisk -l on the device shows nothing and I can't use it.
There seems to have been lot of discussion about this, some saying it's udev rules, some saying it's a kernel issue, and some saying it's a phone firmware issue.
This phone is on the latest available firmware. Can't do anything about the kernel, or don't wish to anyway, and udev tweaking did nothing.

Does anyone know what the _actual_ cause of this problem is and how to fix it? To my very great annoyance, I've had to run up a windows 7 VM in VB as to talk to the darn
thing, and now I feel soiled :-) PCSuite installed and works there, so it's not a harware issue either.

Tried wine and PlayOnLinux as well, couldn't get PCSuite to install/run properly using either.

There's nothing wrong with the USB subsystem on either of my test machines, everything else USB works as expected. The phone modem works. It all works under Windows.
So what's up with this?

---

### Post by kurja on 2013-10-03
I can't say I would have really looked into this matter but, if it helps anyone, I'll point out that when I connect my nokia 500 via usb with the phone's usb mode set as mass storage, *not* use as modem, nokia suite or other mode, the phone will work as a modem. No idea why, but that way it works...

---

