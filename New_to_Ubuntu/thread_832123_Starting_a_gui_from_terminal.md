---
title: "Starting a gui from terminal"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by eldar on 2008-06-17
I tried to search this but searches are subject to correct wording!
Anyways, I installed 8.04 and it worked ok but the graphics is borked. Got it fixed, more or less, and did updates. Now i can only boot into a text screen. I want to try and start gnome or any one of the gui interfaces but do not know the commands.

thanks

---

### Post by dje on 2008-06-17
try
```
startx
```

hope that helps,
dje

---

### Post by Troll_the_Great on 2008-06-17
Just login and then type:

```
gdm
``` or ```
sudo gdm
```

If that doesn't work,remove Gnome display manager and then install it again:

sudo apt-get remove gdm

sudo apt-get install gdm

Reboot,(type sudo reboot) and it should work.

Hope this helps.

---

### Post by bodhi.zazen on 2008-06-17
> **Troll_the_Great said:**
> Just login and then type:

```
gdm
``` or ```
sudo gdm
```If that doesn't work,remove Gnome display manager and then install it again:

sudo apt-get remove gdm

sudo apt-get install gdm

Reboot,(type sudo reboot) and it should work.

Hope this helps.

Should be ;

```
sudo /etc/init.d/gdm restart
```

No need to remove and re-install gdm (at this point)

---

### Post by Troll_the_Great on 2008-06-17
I am not very experienced with linux, that's why I said he should do it like that.I had a similar problem and I solved in that way.Hope he will too.
Best regards, Troll

---

### Post by eldar on 2008-06-17
Well I tried to run startx and the x server fails.
Fatal server error:
no screens found

Tried to remove/install gnome and restart it. It seems to start fine, just will not display anything.

So it seems to be xserve.

---

### Post by avtolle on 2008-06-17
What did you do originally to get your graphics fixed, "more or less"? If it involved manually installing a driver for your graphics card, you're going to (likely) need to do this again.

---

### Post by eldar on 2008-06-17
Well before I have a gui interface. I had to switch the monitor to a different display and it worked ok then. Then I did all the updates and then it broke. Gnome starts but no gui display and I cannot start x server I also cannot do gksu. I get a "cannot open displays" error.

---

### Post by avtolle on 2008-06-17
Have you tried booting into safe graphics mode? I think you hit esc while booting, and there are some options given. Safe graphics mode uses a generic driver, so maybe this could at least get you in?

---

### Post by Ejas12 on 2008-06-17
well that happened once in my laptop, try:
```
sudo dpkg-reconfigure xserver-xorg
```
this will try to reconfigure your viedo settings, basically you only need to hit enter trough the whole steps of configuration

---

### Post by eldar on 2008-06-17
Tried that too and it failed. Rebooted and went into recovery mode and was able to repair xserver there and it came up and now I am working on other things. So I got my gui back. Being relatively new to terminal commands, guis help!:)

Thanks guys and :guitar: on

---

