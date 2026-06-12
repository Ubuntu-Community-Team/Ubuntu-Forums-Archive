---
title: "unity 3d doesnt work anymore in ubuntu 11.10"
date: 2011-09-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by turkler on 2011-09-26
hello everyone,i just installed ubuntu 11.10 beta and it was good but after 3 days unity doesnt work.now i am working with gnome 3 or sometime unity 2d please see in picture because i am noob in linux

---

### Post by collisionystm on 2011-09-26
A package may have broke unity. Try doing a system update.

sudo apt-get update
sudo apt-get upgrade

It is still beta. Best to wait until its actually released.

---

### Post by turkler on 2011-09-26
i did system update every 3 hour XD but as u said it's still beta.thanks for help

---

### Post by oldfred on 2011-09-26
Moved to Oneiric Ocelot forum.

---

### Post by ventrical on 2011-09-26
Open a terminal and try:

unity --reset

Get a terminal by <ctrl_+alt+F1>

---

### Post by rastamankg on 2011-09-27
I had a same problem. unity --reset solved it.

Thank you

---

### Post by turkler on 2011-09-29
thank you ,it worked

---

### Post by sasanka_g_v on 2011-09-30
I have a very different problem. My screen settings have gone weird and I am attaching a screenshot and can someone help me out how to resolve the issue. If I open any application and minimize it, I see the trails of the window and they never vanish. You can see that in the screenshot. Also it happens only at Upper left corner of the screen.

---

### Post by xyzzyman on 2011-09-30
> **sasanka_g_v said:**
> I have a very different problem. My screen settings have gone weird and I am attaching a screenshot and can someone help me out how to resolve the issue. If I open any application and minimize it, I see the trails of the window and they never vanish. You can see that in the screenshot. Also it happens only at Upper left corner of the screen.

[http://ubuntuforums.org/showthread.php?t=1852187](http://ubuntuforums.org/showthread.php?t=1852187)

Download your updates.

---

### Post by Eng.H on 2011-09-30
> **turkler said:**
> hello everyone,i just installed ubuntu 11.10 beta and it was good but after 3 days unity doesnt work.now i am working with gnome 3 or sometime unity 2d please see in picture because i am noob in linux

i have same problem but unity --reset doesn't work :( 

what i can do ?

---

### Post by rbrick49 on 2011-09-30
> **Eng.H said:**
> i have same problem but unity --reset doesn't work :( 

what i can do ?
sudo pkill nautilus

---

### Post by chlorox on 2011-09-30
Yep, after updates tonight, nothing is fixing it. It comes up to the Nautilus menu screen.

When running unity --reset, I get a few errors:

compiz (expo) - Warn: failed to bind image to texture

then it just hangs on:
Initializing session options...done

I have to hit CTRL+C to get out of it.

---

### Post by chlorox on 2011-09-30
> **chlorox said:**
> Yep, after updates tonight, nothing is fixing it. It comes up to the Nautilus menu screen.

When running unity --reset, I get a few errors:

compiz (expo) - Warn: failed to bind image to texture

then it just hangs on:
Initializing session options...done

I have to hit CTRL+C to get out of it.

Running ccsm and enabling the Unity plugin (and resolving the conflicts) solved it.

---

### Post by chlorox on 2011-10-01
> **chlorox said:**
> Running ccsm and enabling the Unity plugin (and resolving the conflicts) solved it.

Oops, spoke too soon. One reboot and Unity is completely borked. None of the usual fixes does anything. It comes up to the Nautilus menu screen. No launcher or anything else.

What was the apt command to completely purge and reinstall this thing?

---

