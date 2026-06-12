---
title: "Can't get wireless to work right =/"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Dazappa on 2008-06-29
My friend installed ubuntu on his laptop and was able to setup wireless internet no problem. Now, I tried to use the autoconfigure and I couldn't get it to work right on my desktop, so I tried a manual configuration. That also failed. I don't know whY! :S And, now I can't even figure out how to get back the auto configure icon in the top right because my manual attempt failed. The router uses WPA2 aes encryption by the way...

---

### Post by Miljet on 2008-06-29
This is the best how-to concerning wireless that I have run across. It's kind of old but still relevant.
[http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf](http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf)

---

### Post by laffinet on 2008-06-29
Have you tried following [these ]("http://ubuntuforums.org/showthread.php?t=202834")instructions.

Solved my wireless problems. Have been running without network manager for months now without ever looking back.

---

### Post by RequinB4 on 2008-06-29
Before making drastic changes, it helps to know what card you have

Paste here the output of 
```

lspci

```

---

### Post by spiderbatdad on 2008-06-29
the network monitor icon is  called "nm-applet" You have to have a notification area in your panel for it. Right click on the panel and add to panel notification area, if you don't have it. If that doesn't get the applet back, press ALT+F2 and enter "nm-applet"

If you need help with drivers or more info on your wireless card, run the command "sudo lshw -C net" in a terminal and paste or copy here, the information regarding the wireless interface.

---

