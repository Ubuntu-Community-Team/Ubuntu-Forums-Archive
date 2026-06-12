---
title: "printing??"
date: 2011-10-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Roasted on 2011-10-04
I'm a little confused. tonight I tried to set up a laserjet printer with my 11.10 machine.. the problem is it did not ask me to choose the proper protocol I wanted to use. instead it just give me the choices of local and network and tried to find it on its own. the problem is, It never did work right. are these features expect to be missing in the final release of 11.10? I can't choose lpd, ipp, none of that. Any idea?

---

### Post by dino99 on 2011-10-04
sadly its the new gtk3 devs spirit: hiding a bunch of parameters and make tweaking more technical, only using gsettings/dconf (dialog boxes removed). They are thinking to reduce the number of issues due to wrong users settings/tweakings.

You might report againgst cups to request your needs (give hard motivations)

---

### Post by Roasted on 2011-10-04
> **dino99 said:**
> sadly its the new gtk3 devs spirit: hiding a bunch of parameters and make tweaking more technical, only using gsettings/dconf (dialog boxes removed). They are thinking to reduce the number of issues due to wrong users settings/tweakings.

You might report againgst cups to request your needs (give hard motivations)

Like what, common sense? How the hell do they think removing all of those features makes sense. I mean, clearly something isn't working when my network printer comes up as "localhost" and won't even allow me to print to it.

Don't let me down, 11.10. So far the chances are looking good, though...

EDIT - not to mention, my printer gets auto-assigned (based on previous experience with earlier versions of Ubuntu) a KONICA MINOLTA driver. The problem is none of these drivers work. I need to manually scroll down further and select "Minolta" and then find my driver and bam it works.

How can I change the driver of the printer in 11.10? Can't I even do that?

---

### Post by rbrick49 on 2011-10-04
just go here it will work ok
[http://www.ehow.com/how_5107960_add-...ter-linux.html](http://www.ehow.com/how_5107960_add-...ter-linux.html)

---

### Post by Roasted on 2011-10-04
> **rbrick49 said:**
> just go here it will work ok
[http://www.ehow.com/how_5107960_add-...ter-linux.html](http://www.ehow.com/how_5107960_add-...ter-linux.html)

Really? We need to use CUPS via web now to handle the simplest of printing management on home Linux systems?

---

### Post by collisionystm on 2011-10-04
If it is a Laserjet, just install HPLIP from the software Center. It is the official HP tool. Enjoy.

---

### Post by rbrick49 on 2011-10-04
I have the samsung unified driver from samsung mine works ok but I did use the cups one earlier in oneiric

---

### Post by philinux on 2011-10-04
> **collisionystm said:**
> If it is a Laserjet, just install HPLIP from the software Center. It is the official HP tool. Enjoy.

Hplip is part of the default install. Has been for a while.

hplip-gui is optional.

---

### Post by jtarin on 2011-10-04
> **Roasted said:**
> Really? We need to use CUPS via web now to handle the simplest of printing management on home Linux systems?No. You can use it via the command line if your so inclined. I always use CUPS. Takes me about 5 minutes tops,to set it up.

---

### Post by collisionystm on 2011-10-04
> **philinux said:**
> Hplip is part of the default install. Has been for a while.

hplip-gui is optional.


I know that. but the GUI offers many more features. The CUPS interface is confusing to a new user.

---

### Post by Roasted on 2011-10-04
One thing I'm not seeing (and maybe this is because I'm on my work Macbook now, but I doubt there's be a difference from Mac's CUPS to Linux) is how in the world can I assign a certain driver to a printer through CUPS? My printer gets auto-assigned the wrong driver. I have to re-assign it to a Minolta driver instead of a Konica-Minolta driver for it to work. That's my biggest concern.

If I could assign the proper driver to it in the newly "refined" 11.10's printer menu I'd be in good shape...

---

### Post by jtarin on 2011-10-04
> **collisionystm said:**
>  The CUPS interface is confusing to a new user.So is a manual transmission. Cups need not be intimidating. There is plenty of fine documentation and walk-throughs.....and as it has been mentioned there is a GUI available....hplip-gui. Once through CUPS setup...it's cake from then on out.

---

### Post by cariboo on 2011-10-04
I just used the printer setup dialogue in System Settings->Printing to setup up another printer, it worked the way it always has, allowing me to choose what driver I needed during the setup process.

---

### Post by jbicha on 2011-10-04
To be fair, Ubuntu's printer applet isn't really a GNOME thing. Also, it looks to me like it's the same as 11.04 was.

You can change the autoselected printer driver by right clicking on the printer and selecting Properties. Then change Make and Model.

Also I encourage you to use ubuntu-bug cups and report a bug that the autodetection didn't give you the optimal driver so that this can be fixed instead of just worked around.

---

### Post by Roasted on 2011-10-04
> **cariboo907 said:**
> I just used the printer setup dialogue in System Settings->Printing to setup up another printer, it worked the way it always has, allowing me to choose what driver I needed during the setup process.

Well, to be fair, I was also in Gnome Shell.

I apologize. Gnome Shell has become so standard to me that sometimes I forget Ubuntu uses Unity by default. Sorry!

So anyway, **PLEASE** forgive me but my ENTIRE basis of this thread is based on Gnome Shell within Ubuntu 11.10. That's where my printing quarrels are. If anybody is running GS in 11.10 or could fire it up to see what I mean, that would be great. :)

---

### Post by jbicha on 2011-10-05
And for completeness...

Ubuntu uses GNOME's printer dialog in GNOME Shell instead of the usual one shipped in Ubuntu. The new one looks like it will be used in 12.04 for Unity too though, but we hope it's improved. In GNOME Shell, run system-config-printer to get the old dialog with extra buttons.

---

### Post by Roasted on 2011-10-05
> **jbicha said:**
> And for completeness...

Ubuntu uses GNOME's printer dialog in GNOME Shell instead of the usual one shipped in Ubuntu. The new one looks like it will be used in 12.04 for Unity too though, but we hope it's improved. In GNOME Shell, run system-config-printer to get the old dialog with extra buttons.

Thank you. I'll give that a shot.

That being said, I wonder what the point is. Sure, you remove some things which may seem less confusing to people. But my mother knows how to set up a network printer in the old dialog box. This one here is too simple to actually work. Parents are often opposers of change, so this will be interesting. I am sensing a decent amount of remote help in my future.

Speaking of which, why in the world isn't there an advanced option to have more usable features?? That would... well... make sense.

---

