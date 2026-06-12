---
title: "HOWTO: Make WiFi connect automatically at startup"
date: 2006-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Old Pink on 2006-08-31
Simple, really. 

Open a terminal, and enter ```
sudo apt-get install wlassistant
```

Enter your password, if needed and wait for it to download/install. 

Now, in terminal type ```
sudo wlassistant
``` Wait for the box to pop up, click "Options" and check "Quit upon succesful connection" 

Now go into System > Preferences > Sessions > Startup Programs

and add "sudo wlassistant" to the list. :)

---

### Post by dabear on 2006-08-31
Huh? Wlan has always started directly to me, I've not needed any extra scripts. What is this really for?

---

### Post by Old Pink on 2006-08-31
I always had to go into Networking, click "Options" on my wireless card and choose a network, before waiting for my card to disable/re-enable. 

It's using the Broadcom driver/firmware in the other "HowTo:" 

Then I figured this out, which makes me auto connect. :)

---

### Post by dannyboy79 on 2006-09-01
I have been having problems with my AR5212 card working right after I turn on my computer lately. It used to work and I don't know what changed? SO what i HAVE to do to get it to work is go to networking, then go to ath0 and deactivate it and then activate it again and then it works. I thought maybe your solution might work for me so I tried it but after doing sudo wlassistant I get "wlassistant: error while loading shared libraries: libkdeui.so.4: cannot open shared object file: No such file or directory". WHat do you suggest if anything?

---

### Post by Old Pink on 2006-09-01
Try doing ```

sudo apt-get install wlassistant
```

again, in search for updates... seems an odd error.

---

### Post by ser1alsn1per on 2006-09-04
i have a broadcom wireless card and I used wifi radar  and it automatically loads

---

### Post by Levitation on 2006-11-21
How do you use the wifi radar?

---

### Post by groggyboy on 2006-11-21
try out network-manager.  it connects on startup, lets you select wifi networks from a drop-down menu in the systray, works with wpa encryption, and can automatically switch to a wired connection if one is made available.

and don't forget to install the appropriate frontend as well! (network-manager-gnome or knetworkmanager)

oh, and after installing it, don't forget to remove all entries from /etc/network/interfaces except for> 
auto lo
iface lo inet loopback

---

