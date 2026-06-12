---
title: "Desktop effects could not be enabled"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Jezprice on 2008-08-20
Okay, really dumb one here but i can't get the cool compiz effects working on my computer (see signature).

I found this on a post when i searched threads: 

*Your graphics card must support it which you can test. On the desktop right click and select "change desktop background" then click the tab visual effects and then select "extra" if it won't do it then your driver/adapter don't support it*.

I've done this and mine says DESKTOP EFFECTS COULD NOT BE ENABLED. 

Can some one explain what i have to do to get it working, i.e. is it impossible to get it to work with my system - as it stands - and if so what is the minimum requirments needed graphics wise/system wise to get it to work.

Cheers.

---

### Post by bitninja on 2008-08-20
This system has the GMA 3100 graphics chipset correct? Try searching in Synaptic for drivers for it, chances are you don't have drivers that support the effects and 3D acceleration.

---

### Post by Kevbert on 2008-08-20
What are the onboard graphics ?  You can get this via Applications-Accessories-Terminal and entering
```
lspci
```
Post the output here by going to the Edit menu and selecting copy and paste in a new post with Ctrl+V.

---

### Post by Jezprice on 2008-08-20
Hi have done the above and got this back.

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)

This link also shows the info about my system:

[http://eu.shuttle.com/en/DesktopDefault.aspx/tabid-72/170_read-14126/](http://eu.shuttle.com/en/DesktopDefault.aspx/tabid-72/170_read-14126/)

---

### Post by gali98 on 2008-08-20
Have you tried enableing restricted drivers?

System->Administration->Restricted Drivers

(may be a little off of that.... I'm not on Ubuntu right now.)

Kory

---

### Post by Jezprice on 2008-08-20
Hi Kory,

It was System &#9656; Administration &#9656; Hardware drivers

And the report was that i have no proprietry drivers in use on this system.

Surely the intel graphics will work with the visual effects, it works with Vista Aero crap!!

---

### Post by Kevbert on 2008-08-21
Please take a look at the [[COLOR="Red"]Intel webpage[/COLOR]]("http://www.intellinuxgraphics.org/download.html").  It looks like you have to download the driver and compile from source.

---

