---
title: "Problems after upgrading!  Ubuntu 12.04"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Eirreann on 2012-04-26
So, I just upgraded from 11.10 to 12.04.  This is the first time I've upgraded from one version of Ubuntu to another, and now I'm encountering some problems:
1. Trying to use Ubuntu (non-2D) is impossible, because all that is visible is the gnome bar thing on the top of the screen; everything else is white except for the strip where the applications usually are and that's a different colour; I can still open applications but they don't show up, all I see is this white screen.  I had this problem with 11.10 as well, and then all I had to do was update the Nvidia drivers through the Additional Drivers section in System Settings.  However, when I went to Additional Drivers after installing 12.04 (got there through using Ubuntu (Unity 2D)), first I got an error then no drivers appeared, so now I'm stuck with the 2D version of Ubuntu...
2.  I'm constantly getting Unity 2D has crashed errors, although nothing seems to have changed about the desktop... also I'm getting a whole lot of "Ubuntu 12.04 has encountered an error" messages, although again, I don't see any changes...

Any advice for me?

---

### Post by SlasherIT on 2012-04-26
I second this, everything noted in the post above me is happening to me too.

Specs: HP zd7060ea, Intel Pentium 4 3.06 Ghz, NVIDIA GeForce FX Go5600, 1.25GB RAM, 60GB HDD...

---

### Post by Eirreann on 2012-04-26
> **SlasherIT said:**
> I second this, everything noted in the post above me is happening to me too.

Specs: HP zd7060ea, Intel Pentium 4 3.06 Ghz, NVIDIA GeForce FX Go5600, 1.25GB RAM, 60GB HDD...

You are using the exact same video card as me; that may mean something...

---

### Post by HeroOfCanton on 2012-04-26
Certainly sounds like an issue with that particular card. What error are you getting when trying the 3rd party driver install?

---

### Post by SlasherIT on 2012-04-26
> **HeroOfCanton said:**
> Certainly sounds like an issue with that particular card. What error are you getting when trying the 3rd party driver install?

What 3rd party driver install? The issue was that in Additional Drivers it doesn't show any driver for the graphics...

---

### Post by HeroOfCanton on 2012-04-26
> **SlasherIT said:**
> What 3rd party driver install? The issue was that in Additional Drivers it doesn't show any driver for the graphics...

Sorry, I should have said "additional driver install". As for the error, you said:
> However, when I went to Additional Drivers after installing 12.04 (got  there through using Ubuntu (Unity 2D)), **first I got an error** then no  drivers appeared, so now I'm stuck with the 2D version of Ubuntu...Is this happening each time you try to view additional drivers or was that just a one time thing? You'd think the drivers would carry over, so I'm wondering if the problem is when Ubuntu's looking for the driver rather than the driver not existing.

---

### Post by Eirreann on 2012-04-26
> **HeroOfCanton said:**
> 
Is this happening each time you try to view additional drivers or was that just a one time thing? You'd think the drivers would carry over, so I'm wondering if the problem is when Ubuntu's looking for the driver rather than the driver not existing.
It just happened the once, and it was something along the lines of "Ubuntu 12.04 has encountered a problem." or something like that with the option to send error report or close; I sent the error report.  But now I can't access the drivers thing at all!
I thought that the drivers would have carried over as well, but apparently not :confused: .  To make it worse, the upgrade completely wiped my system of everything Nvidia related, I don't even have Nvidia X Server Settings any more!

---

### Post by NoNameWill on 2012-04-26
Your card uses nvidia driver 173 currently xserver 1.11 does not support that driver. Your problems with the unity panel are because you are running in 2d.

---

### Post by lihaosky on 2012-04-26
It's happening to me as well. And it doesn't have network connection... Don't know why. Previous 11.10 works perfectly. Kind of disappointed:sad:

---

### Post by Eirreann on 2012-04-26
> **NoNameWill said:**
> Your card uses nvidia driver 173 currently xserver 1.11 does not support that driver. Your problems with the unity panel are because you are running in 2d.

So I have a problem, then, because I can't run Ubuntu non-2D without one of the 3rd party drivers....

---

### Post by mcblades on 2012-04-27
Hi,

I had this problem with the beta 12.04.  Same video dirver issues clashing with X.  To use unity 3d you can use the nouveau open source drivers.  You will need to remove the nvidia drivers first (I think I just unticked any nvidia  drivers in the additional drivers panel). I also needed to delete /etc/X11/xorg.conf  otherwise my box would only boot into 800x600.

good luck

Mark

---

### Post by vjkeito on 2012-04-29
Cheers

---

### Post by tomatoe on 2012-04-29
nVidia's 173 drivers can't be installed on 12.04 because of dependencies. You have to use nouveau drivers. To get normal desktop, try this
```

 sudo apt-get purge xserver-xorg
 sudo apt-get install xserver-xorg xserver-xorg-video-all
 sudo reboot
```
 
But first delete all nVidia drivers. Though you won't be able to use Unity 2D

Regards.

---

### Post by Eirreann on 2012-04-29
> **tomatoe said:**
> nVidia's 173 drivers can't be installed on 12.04 because of dependencies. You have to use nouveau drivers. To get normal desktop, try this
```

 sudo apt-get purge xserver-xorg
 sudo apt-get install xserver-xorg xserver-xorg-video-all
 sudo reboot
```But first delete all nVidia drivers. Though you won't be able to use Unity 2D

Regards.

So you are saying that if it doesn't work I'll be stuck out of Unity 2D as well?  I'm not sure if I want to take that risk...

---

### Post by vkmaxx on 2012-04-29
I have the similar problem. Installing drivers newer than 280.13 on 11.10 results in to graphic user interface (no xserver).
After updating to 12.04 my drivers where updated to 295.xx, and guess what - no gfx interface :(

I have MSI Core2Duo with mobile 8600GT nVidia card.

---

