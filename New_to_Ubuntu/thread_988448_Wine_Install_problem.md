---
title: "Wine Install problem"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by zeththedarkmage on 2008-11-20
Hello all I was attempting to use Wine to play World of Warcraft.

I installed it a couple days ago and it ran fine without any problems, until today. I turned the computer off to install a new video card that I purchased today. Then when I booted the computer back up and attempted to play WoW it would bring up the log in screen and then when I clicked play it would bring up an error something about trying incorrectly use the Microsoft.net framework. I couldn't figure anything out with it so I figured perhaps Wine needed to be reinstalled so I completely removed it using the synoptic package manager, then when I attempted to reinstall it I got this error message.

wine:
  Depends: libasound2 (>1.0.17) but 1.0.15-3ubuntu4 is to be installed

And I don't know what to do from here, any and all help is greatly appreciated.

---

### Post by kestrel1 on 2008-11-20
If you installed a new video card did you install the drivers correctly?

---

### Post by zeththedarkmage on 2008-11-20
I have not done anything but install the card. Everything appears to be running fine since it was installed. Could it not having the correct drivers cause Wine to not install?

---

### Post by kestrel1 on 2008-11-20
Not sure but it is always possible, as the video card is what has changed since Wine did work.
What card did you have previously & what is your new one?

---

### Post by zeththedarkmage on 2008-11-20
before it was the onboard video which was an Nvidia GeForce 6150 LE and now I'm using a Nvidia GeForce 8400 GS. I don't see it being the problem though because I had the same error from wine long before I changed the video card, not with WoW obviously but with other programs. And I don't see how it missing libsound which is some sort of dependency for the program to be affected by the video card.

---

### Post by neu2buntu on 2008-11-20
try code: sudo apt-get --purge remove wine   and then code: sudo apt-get --purge autoremove in the terminal.....  this is supposed to remove config files that wine leaves behind

---

### Post by zeththedarkmage on 2008-11-20
@chrissy: I put in both codes and attempted to reinstall Wine and it gave me the same error.

---

### Post by kestrel1 on 2008-11-20
Have you tried installing what it wants?
```
sudo apt-get install libasound2
```

---

### Post by zeththedarkmage on 2008-11-20
I tried that and I got this...

libasound2 is already the newest version.

it says that it is 1.0.15 though and wine is asking for 1.0.17

---

### Post by kestrel1 on 2008-11-20
Have a look at this:
[https://launchpad.net/ubuntu/intrepid/ia64/libasound2-plugins/1.0.17-0ubuntu5](https://launchpad.net/ubuntu/intrepid/ia64/libasound2-plugins/1.0.17-0ubuntu5)

as 1.0.15 is apparently the latest version, just means that the repo's do not have version 1.0.17. You should need to download & install the latest one.

---

### Post by zeththedarkmage on 2008-11-20
How do I go about finding it and installing it? I tried compiling the source but that got me nowhere.

---

### Post by kestrel1 on 2008-11-20
From what I have found I think these are the 64 bit versions, not sure what Ubuntu version you are running but here is a link to the deb file:
[http://launchpadlibrarian.net/18307416/libasound2_1.0.17a-0ubuntu4_ia64.deb](http://launchpadlibrarian.net/18307416/libasound2_1.0.17a-0ubuntu4_ia64.deb)
& the plugins:
[http://launchpadlibrarian.net/19273670/libasound2-plugins_1.0.17-0ubuntu5_ia64.deb](http://launchpadlibrarian.net/19273670/libasound2-plugins_1.0.17-0ubuntu5_ia64.deb)

---

### Post by zeththedarkmage on 2008-11-20
I tried to install those but it said error wrong architecture ia64

---

### Post by zeththedarkmage on 2008-11-20
I found a debian package for libasound21.0.18 and I am on I386 but when I tried to install it, it says

Error:conflicts with the installed package 'libasound2-plugins'

---

### Post by kestrel1 on 2008-11-21
Try removing the installed libasound2 & the plugins, then install the new deb package.
I did wonder if the ones I found where going to be the right ones, sorry about that.

---

### Post by Aldrenean on 2008-11-21
Zeth:  I had the same problem.  The cause, it seems, is that the repo you used is for a newer version of ubuntu, and for some reason Synaptic doesn't catch that the version of whatever software you're installing is too new.  Select wine in synaptic, click the Package menu, do Force Version, and select the 1.0.0-1... version instead of the newest.  Worked for me.

Now I just need to get EVE running... :P

---

