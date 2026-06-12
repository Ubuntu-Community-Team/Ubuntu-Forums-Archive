---
title: "LDM equivilent of /etc/gdm/init/Default?"
date: 2011-09-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ihs on 2011-09-21
Hi,
   I'm needing to add an xrandr command to the 11.10 startup, under gdm I just had to modify the /etc/gdm/init/Default file and add in my xrandr commands, however I've been unable to find any information on doing this with LDM (both google and ubuntu forum searches).
 
Does anyone know how I can add in xrandr commands pre-login now that 11.10 is using LDM?
 
The gdm method was wonderfully easy, so I'm hoping for a similar method.
 
Thanks.

---

### Post by jerrrys on 2011-09-21
I was not aware that LDM (lightdm) was default and instead installed GDM (gnome display manager) on my 11.10 build.  I use gnome3 only, but indication is that it works fine.  Maybe you could just swap them out.

---

### Post by cariboo on 2011-09-21
I would suggest using the name of the display manager to avoid confusion between LXDM and Lightdm. Can't you just add you xrandr information to /etc/X11/xorg.conf?

---

### Post by ihs on 2011-09-22
> /etc/X11/xorg.conf
 
I've never yet managed to get a xorg.conf file to work with the chipset (Intel gma950) and screen (max resolution 800x480) without ending up in ubuntu recovery console mode removing the .conf file to get the display working again.
 
>  Maybe you could just swap them out. 
 
I admit I'd thought of this, however I'm trying to keep it as stock ubuntu as possible in this instance.
 
So, if anyone has any other suggestions on how to get my xrandr command loading before the login screen appears, I'm all ears, and thanks for the replies so far.

---

