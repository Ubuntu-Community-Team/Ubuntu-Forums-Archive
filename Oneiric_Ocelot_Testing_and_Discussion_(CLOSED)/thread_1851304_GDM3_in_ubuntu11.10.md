---
title: "GDM3 in ubuntu11.10"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by viper200 on 2011-09-28
While trying gnome-shell in beta2, gdm3 appears to use ambiance gtk theme and not the gdm.css from the adwaita shell theme, does anyone know how to resolve this? TIA

---

### Post by viper200 on 2011-09-29
bump

---

### Post by nothingspecial on 2011-09-29
Moved to Ubuntu +1 (Oneiric Ocelot)

---

### Post by viper200 on 2011-09-29
> **nothingspecial said:**
> Moved to Ubuntu +1 (Oneiric Ocelot)

Sorry wasn't sure where to post this, thanks for your help.

---

### Post by mdhollis on 2011-09-29
Install gnome-tweak-tool and you can do what you want.

---

### Post by viper200 on 2011-09-29
tweak tool works to change your shell theme in your desktop, it doesn't do anything with the gdm.

Edit: found out that gdm 3.2 is not available for Oneiric yet, so will just have to wait for it.

---

### Post by mdhollis on 2011-09-29
> **viper200 said:**
> tweak tool works to change your shell theme in your desktop, it doesn't do anything with the gdm.

Oh I'm sorry dude I'm still sleeping.  11.10 uses lightdm by default so I have been using that.  Not sure how to change the theme in gdm.

---

### Post by alexvy13 on 2011-09-29
I read somewhere the new GDM isnt yet avavilable for oneiric. 
 
webupd8.org

---

### Post by jbicha on 2011-09-29
Yes, Ubuntu 11.10 has GDM 3.0 available; at the moment we can't get GDM 3.2 to work in Ubuntu so that won't make it until Placid Platypus or a PPA.

---

### Post by sgage on 2011-09-29
If what you want is to have your own custom graphic in the gdm greeter, here's what you do. You need a png graphic that is 1920x1280 pixels (you can use gimp to scale your picture, and save it as a png). It needs to be named warty-final-ubuntu.png, and you copy it to /usr/share/backgrounds. Voila! Works for me.

---

### Post by viper200 on 2011-09-30
> **sgage said:**
> If what you want is to have your own custom graphic in the gdm greeter, here's what you do. You need a png graphic that is 1920x1280 pixels (you can use gimp to scale your picture, and save it as a png). It needs to be named warty-final-ubuntu.png, and you copy it to /usr/share/backgrounds. Voila! Works for me.

i already knw about that but thanks you for your reply, what i wanted to do is customize the gdm3.2. 

> **jbicha said:**
> Yes, Ubuntu 11.10 has GDM 3.0 available; at the moment we can't get GDM 3.2 to work in Ubuntu so that won't make it until Placid Platypus or a PPA.

i hope a ppa come out soon, thanks for your reply.

---

### Post by SATA on 2011-10-06
See this thread: [http://ubuntuforums.org/showthread.php?t=1848845](http://ubuntuforums.org/showthread.php?t=1848845)

---

