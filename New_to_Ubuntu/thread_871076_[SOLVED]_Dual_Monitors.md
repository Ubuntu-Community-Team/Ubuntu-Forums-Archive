---
title: "[SOLVED] Dual Monitors"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by bprof on 2008-07-26
I have nvidia 9600 gt and I want to run dual monitors, is there away to do it easily on Ubuntu 8?

This [method]("http://my.opera.com/sjosul/blog/ubuntu-8-04-dual-monitor-setup") is supposed to do it, but it requires editing files and other things.

I was able to do on OpenSUSE using nvidia driver, but I couldn't install the driver on Ubuntu.

Now I using the card like this

[IMG]http://files.myopera.com/sjosul/blog/Screenshot-Hardware%20Drivers.jpg[/IMG]

---

### Post by freak42 on 2008-07-26
there is a gui tool from nvidia; you can start it from
a command line by typing 
nvidia-settings

(you might have to install it first, though)

---

### Post by SuperSonic4 on 2008-07-26
You will need to type in ```
gksudo nvidia-settings
```. You will need to overwrite your xorg.conf file and this needs root priveliges.

---

### Post by jimmy the saint on 2008-07-26
An important consideration:  are the monitors the same size?  if they don't match, you will be limited by limitations in how gnome handles dual monitors.  Setting up two seperate x-servers will work, but they will be completely independent and you will be unable to drag windows between them.  The TwinView setting essentially creates one large monitor, but dead space will result from the monitors not matching and gnome will still want to draw icons there.  In that case, you may consider Xubuntu.  They have excellent mulitmonitor support, but the learning curve is a bit (a tiny bit) steeper.

---

### Post by bprof on 2008-07-28
Thank you all for you help. I used envy and was able to run dual monitors although they are not same size but they are working just fine.

---

