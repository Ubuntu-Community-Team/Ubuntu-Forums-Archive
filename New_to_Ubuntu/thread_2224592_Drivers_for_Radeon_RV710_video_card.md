---
title: "Drivers for Radeon RV710 video card"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by EZZ9 on 2014-05-16
I have it plugged into the computer, but that's as far as I have gotten. I did plug in the monitor and no video came through. The old output for video, still is working. I have no clue on what to do next. Can anyone help?

---

### Post by grier-devon on 2014-05-17
Are you able to get any video up at any point? If you are in the GUI open up "Additional Drivers" and from there it will scan and give you the option to install Radeon drivers. 

If the GUI is not going well the go into the terminal and use this guide

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by QIII on 2014-05-17
Hello!

The RV710 (HD 4000 series, if I am not mistaken) is no longer supported under Linux by AMD/ATI.

The last Ubuntu version for which AMD/ATI provides support is 12.04.1.  From 12.04.2 forward, the legacy driver that would otherwise work with it will not work with the version of X Server now used.

Do NOT attempt to install the proprietary driver.  The default Radeon driver installed with Ubuntu is the only one that will work -- if we can get it going.

Which version of Ubuntu are you using?  Was the card in the machine when Ubuntu was installed?  You mentioned the "old output for video".  Is there another GPU in the machine?  What OEM and model?

---

### Post by edo_kanii on 2014-05-17
Try this: navigate to settings->additional drivers->(wait for few sec)select your video card driver instead of nouveau driver

---

### Post by mörgæs on 2014-05-17
Nouveau drivers are only in use for Nvidia cards. With a Radeon card the Nouveau drivers have never been active.

---

### Post by edo_kanii on 2014-05-17
ok I didn't know that, but myb same method can help

---

### Post by Mark Phelps on 2014-05-17
> but myb same method can help 

Actually, in this case, NO, it will not help -- because as QIII already indicated, the "additional drivers" for this card were dropped some time ago by AMD, so now, they will not show up anymore.  If the OP tried to force the installation of restricted drivers, that would only make matters worse for them -- because they would then have to remove those drivers, and would have a hard time doing that.

The default Radeon drivers would already be installed and those would be the ones to be used.

---

### Post by moaz2 on 2014-05-17
[IMG][[IMG]http://s30.postimg.org/nwa2u5v2l/Screenshot_from_2014_05_17_22_06_01.jpg[/IMG]]("http://postimg.org/image/nwa2u5v2l/")[/IMG]what shud i do....plz help

---

### Post by moaz2 on 2014-05-17
][[IMG]http://s30.postimg.org/smx39phn1/done.jpg[/IMG]]("http://postimg.org/image/smx39phn1/")
After installing the driver from additional driver...tyvm everyone

---

### Post by Mark Phelps on 2014-05-17
Glad you got it working -- but in future, please do NOT hijack someone else's thread for your own problem. This thread dealt specifically with the RV 710 card -- which yours clearly is NOT.  The restricted drivers WILL work with your card (as you have seen) but NOT with the OP's card.  Yours is an entirely different problem.  In future, please open your own thread.

---

### Post by Rob Sayer on 2014-05-18
I have an old Compaq with an AMD 4xxx series gma and it has some problems as well.  Quite possibly similar.

It's true ... AMD dropped linux support for those and earlier models.  Don't install the driver from Additional Drivers.  It's called fglrx.  For anything after 12.04.1 the open source driver is the one that works.  Unfortunately it doesn't have 3D acceleration anymore AFAIK.

Many users think that if they use the LTS it's going to work properly through it's life cycle.  This is an example of why that's not necessarily so.

I suspect you need to set the nomodeset flag on boot.  Try it on boot and if that works you'll have to edit your grub config file so it'll be set every time you boot.

Here's how to use nomodeset before/after install ...

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

... and don't forget to run

sudo update-grub

in terminal to make the change permanent.

---

