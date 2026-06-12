---
title: "Asus EEE PC 1000 + Kubuntu"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-11-13
I was wondering if anyone had tried installing Kubuntu on the Asus EEE pc?

If so, what are your experiences?

---

### Post by Crafty Kisses on 2008-11-13
I've read on a couple of forums that it runs fairly smooth, If I'm right this is the EEE PC that has 2GB of RAM, it should run fairly well.

---

### Post by aysiu on 2008-11-13
This person seems quite happy with it:
[http://carlitoscontraptions.blogspot.com/2008/09/eee-pc-1000-ubuntu-kde-41.html](http://carlitoscontraptions.blogspot.com/2008/09/eee-pc-1000-ubuntu-kde-41.html)

You might get a lot of good opinions on the Eee User forums, too.

---

### Post by flyingsolo on 2008-11-13
I've been using eeebuntu netbook remix for ~month and it works really well.  Regularly use Skype to talk to son at university.  Very handy for notetaking if that purpose suits you.  I tried to dual boot with the original XP but that didn't work so well--lost access to boot to xp and I haven't fixed that yet.  On the other hand, netbook remix is so good, I haven't had reason to boot to xp!

---

### Post by Cyphrin on 2008-12-26
While I did not install Kubuntu, I did successfully install Ubuntu on a new Eee PC 1000. Full install with the custom kernel by Adam McDaniel. The walkthrough I used can be found here:

[http://www.jasonlefkowitz.net/blog1archive/2008/12/howto_run_ubunt.html]("http://www.jasonlefkowitz.net/blog1archive/2008/12/howto_run_ubunt.html")

---

### Post by theozzlives on 2008-12-26
> **Cyphrin said:**
> While I did not install Kubuntu, I did successfully install Ubuntu on a new Eee PC 1000. Full install with the custom kernel by Adam McDaniel. The walkthrough I used can be found here:

[http://www.jasonlefkowitz.net/blog1archive/2008/12/howto_run_ubunt.html]("http://www.jasonlefkowitz.net/blog1archive/2008/12/howto_run_ubunt.html")

and???

---

### Post by Cyphrin on 2008-12-26
> **theozzlives said:**
> and???

After following the walkthrough and testing, everything works. There is only one manual alteration I had to make, that is with the Eee Control Panel applet. When I disabled the wifi and enabled it via the Eee Control Panel applet it did not display this change in nm-applet correctly. To solve this I created a three line shell script to kill and restart nm-applet, then with the use of the Eee Control Panel I bound the script to one of the four hot keys.

```
gedit nmrestart.sh
```

```

#!/bin/bash
killall nm-applet
nm-applet &

```

```
chmod +x nmrestart.sh
```

If I were to install Wicd as noted in the walkthrough this may or may not fix this issue and I might not have to use this script. Other than this one little hiccup everything works fine. I will install Wicd and let you all know how it goes.

EDIT/UPDATE:
I have now installed and tried using Wicd. If I disable/enable wifi in the Eee Control Panel applet I do not have to reload Wicd, simply hitting the refresh button within the Wicd applet works. I did have to logout/login to after the Wicd install to get the applet to show. I assume you could also kill/restart gnome panel and get the same result. Overall I prefer to use Wicd versus nm-applet as it has more connect options which I find useful for my particular needs.

---

