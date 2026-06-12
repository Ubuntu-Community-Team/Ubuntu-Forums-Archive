---
title: "Ubuntu install stops at the purple ubuntu screen"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by 64Buntu on 2013-10-21
I have a hp pavilion zv5000 

My windows xp install died and I made a Ubuntu USB install (13.04 32bit) with unetbootin when i start my computer the unetbootin screen appears and i press install Ubuntu and the purple screen appears with the ubuntu logo in the middle the circle dots underneath the Ubuntu logo flash go through two cycles at least the stop and the USB stick stops flashing.

I have tried a few times and also tried mint with the same effects. 
I left it overnight and it stayed at the same screen

Any help would be appreciated

Thanks

---

### Post by fantab on 2013-10-21
What happens when you "Try Ubuntu without installing"?

---

### Post by 64Buntu on 2013-10-21
Same thing

---

### Post by fantab on 2013-10-21
Check the downloaded .iso with [MD5Sum check]("https://help.ubuntu.com/community/HowToMD5SUM") to verify the integrity of the downloaded ubuntu.iso. If there is a problem download again.
Re-Burn the .iso to the DVD/USB and try again. Try another USB pen drive.

If nothing works then there is some hardware problem... get in touch with a tech. This also could be the reason why your XP died.

---

### Post by 64Buntu on 2013-10-21
I have redownloaded the iso about 4 times through unetbootin and manually, could it be i need to use a cd/dvd rather than a usb?

---

### Post by fantab on 2013-10-21
Give it a try. But I suspect some hardware issue, it is possible that your HDD is corruped, but then it could be anything.

---

### Post by 64Buntu on 2013-10-21
hmm okay thanks

---

### Post by kansasnoob on 2013-10-21
Just some random thoughts :)

Are you perhaps trying to install the 64bit version of Ubuntu on hardware that won't support the 64bit version?

If so you may find that the 32bit/i386 version works OK, but that is just a guess ;)

[ATTACH=CONFIG]247113[/ATTACH]

I assume since you say XP died that you're creating the new Ubuntu image with a different machine, if so what operating system are you using to create the iso? There are some excellent notes here:

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

Now this gets a bit complicated so I'm sorry, but 12,04 is supported until April 2017 whereas the interim releases are only supported for 9 months. To further complicate things both 12.04.2 and 12.04.3 employ the [Hardware Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") so I personally recommend using the 12.04.1 images for older hardware, and they're archived here:

[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

I know the header says 12.04.2 but if you scroll down long enough you will find the 12.04.1-desktop-i386 image - that's the image I'd recommend for older hardware.

And you can then use a wide variety of desktop environments ........ my two favorites are "lubuntu-core" and this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I hope these comments were helpful.

---

### Post by 64Buntu on 2013-10-21
I am installing the 32bit version, I am using a win vista with a intel pentium to make the usb boot
I will try 12.04**.1**

---

### Post by 64Buntu on 2013-10-21
And i have allways like Gnome classic as a desktop enviroment

---

### Post by 64Buntu on 2013-10-21
I burnt a cd and I got the same results,I pressed the up key and it stops randomly when it starts and stops things i can get some examples

---

