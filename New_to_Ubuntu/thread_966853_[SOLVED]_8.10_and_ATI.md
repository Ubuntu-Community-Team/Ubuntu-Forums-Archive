---
title: "[SOLVED] 8.10 and ATI"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Ewingo401 on 2008-11-01
Hey guys, I understand that there is still no driver available for ATI cards in Ubuntu 8.10.  But I was wondering if anyone knew when or if one would be coming.  I don't use my laptop for gaming and I don't really care whether or not I can use compiz.  I do however watch a lot of DVD's on my laptop and I've noticed that sometimes the picture gets kind of jumpy.  I've tried xine, totem, and vlc and got the same results in each one.  I didn't have the problem in 8.04.  Its not terrible and certainly doesn't make the movies unwatchable but it does get a little annoying, if there is a driver coming in the near future I can put up with it a little longer, if not I would probably want to go back to 8.04.  So, has anyone heard anything on this?

---

### Post by Mazza558 on 2008-11-01
There is an ATI driver. In fact, there's two: the open source one and ATI's own. They recently ported it to work on Intrepid and I'm using it now.

---

### Post by Ewingo401 on 2008-11-01
That sounds like good news, but I don't have it in my restricted drivers manager.  Could someone please explain how I can get and use one of these drivers?

---

### Post by Martje_001 on 2008-11-01
It should be.. otherwise: try in Synaptic: xorg-driver-fglrx

---

### Post by phidia on 2008-11-01
There is a guide [here]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide").
Let the thread know if that works or not.

---

### Post by MrWES on 2008-11-01
My ATI9000 v250 worked out of the box with Ibex. Although the performance was slow, so I turned off the visual effects.

Bill

---

### Post by petronell on 2008-11-01
My ATI card worked out the box with both Ibex and Hardy.

If you need help installing the drivers I would recommend using Envy, it makes things very easy. 

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

daveR

---

### Post by Zsheezor on 2008-11-01
> **phidia said:**
> There is a guide [here]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide").
Let the thread know if that works or not.

That guide works perfectly for my HD 4850! Thanks! The section that discusses obtaining the drivers "the Ubuntu way" is excellent. Thank you thank you!

---

### Post by Ewingo401 on 2008-11-01
> **Zsheezor said:**
> That guide works perfectly for my HD 4850! Thanks! The section that discusses obtaining the drivers "the Ubuntu way" is excellent. Thank you thank you!

I second that.  I just finished running through the instructions in the guide and everything is working perfectly now.  Thank you very much!

---

### Post by crjackson on 2008-11-01
> **Mazza558 said:**
> There is an ATI driver. In fact, there's two: the open source one and ATI's own. They recently ported it to work on Intrepid and I'm using it now.

So if I download the ATI 8.10 driver from AMD (the one that says it only supports X.org 7.3 - It will work on my Intrepid install?

If there is a direct link to the driver you are talking about, point me to it please. ATI Mobile 9600 is my graphics card.

I'm reinstalling the OS right now because Envy borked it and I can't seem to fix it back now.

---

### Post by Mazza558 on 2008-11-01
> **crjackson said:**
> So if I download the ATI 8.10 driver from AMD (the one that says it only supports X.org 7.3 - It will work on my Intrepid install?

If there is a direct link to the driver you are talking about, point me to it please. ATI Mobile 9600 is my graphics card.

I'm reinstalling the OS right now because Envy borked it and I can't seem to fix it back now.

No, no. Use the one that appears in the "hardware drivers" applet in Ibex - this one is pretty much guaranteed to work.

---

### Post by crjackson on 2008-11-01
> **Mazza558 said:**
> No, no. Use the one that appears in the "hardware drivers" applet in Ibex - this one is pretty much guaranteed to work.

Nothing shows up in the hardware drivers for me...

---

### Post by phidia on 2008-11-02
> **crjackson said:**
> Nothing shows up in the hardware drivers for me...

Did you look at the guide I linked in my previous post in this thread?

Hardy & Intrepid both use xorg 7.4 btw.

---

### Post by crjackson on 2008-11-03
> **phidia said:**
> Did you look at the guide I linked in my previous post in this thread?

Hardy & Intrepid both use xorg 7.4 btw.

Just now checked it out. I do have 3D effects and gaming using the default drivers that are loaded with initial install, but very slow 2D performance as compared to the drivers loaded with the restriced driver manager in Hardy.

Is there any particular reason the restricted driver manager in 8.10 does NOT list any drivers? It has worked well for me in the past, and now nothing. Disappointing to say the least. Envy has always worked for me too, that also seems broken for me on 8.10. What has happened in 8.10 that would make my driver manager not report the restricted drivers anymore? Since it seems that it has nothing to do with xorg I haven't a clue. Even Envy has faild me for the 1st time.

I'll back up my system later this week, and try using your guide.

What terminal commans can I throw to get a report of the exact driver currently installed?

---

