---
title: "No wifi on my D530 Latitute"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by mattbn8 on 2008-07-08
I have a Dell Latitude D530 with a 1395 Dell/Broadcom wifi card.  Upon installing Ubuntu 8.04, I have no wifi access, I cannot connect to a wifi network and have no option to even search for a wifi network.  It's like it doesn't even recognize any wifi capabilities whatsoever.  I really want this to work so I don't have to rely on MS XP.  Any suggestions?  Is it not recognizing the driver?
 

Thank in advance.

---

### Post by overdrank on 2008-07-08
> **mattbn8 said:**
> I have a Dell Latitude D530 with a 1395 Dell/Broadcom wifi card.  Upon installing Ubuntu 8.04, I have no wifi access, I cannot connect to a wifi network and have no option to even search for a wifi network.  It's like it doesn't even recognize any wifi capabilities whatsoever.  I really want this to work so I don't have to rely on MS XP.  Any suggestions?  Is it not recognizing the driver?
 

Thank in advance.

Hi and welcome, I am no expert on wireless but a quick search turned up some promise
[http://ubuntuforums.org/search.php?searchid=44277580](http://ubuntuforums.org/search.php?searchid=44277580)
And more info
[http://ubuntuforums.org/showthread.php?t=852635&highlight=1395+Dell%2FBroadcom](http://ubuntuforums.org/showthread.php?t=852635&highlight=1395+Dell%2FBroadcom)

---

### Post by ZabiGG on 2008-07-08
Some of [these]("http://ubuntuforums.org/showthread.php?t=820667&highlight=newbie+%28n00b%29") might also help...

Good luck, and welcome to Ubuntu ;)

Should you want to get the most out of your system, please click "Look here" in my signature below for some great starter information links.

Cheers,

Z.

---

### Post by yipperzz on 2008-07-09
it'll work.  just follow those tutorials and search and it'll work.  i'm on a d600 w/brcm card and it's working fine.  you're going to need to get the drivers for windows and install it with ndiswrapper.  that is the quick summary.  for the details, follow the tutorials.  hope that helps.

---

### Post by stats on 2008-07-10
the driver is in the repo now
if you dint install  ndiswrapper then skip steps 2,3,4 
1.Update & upgrade using update-manager/synaptic/adept etc
2.
```

sudo apt-get remove ndisgtk ndiswrapper-common ndiswrapper-utils-1.9

```
3. Remove the ndiswrapper line from /etc/modules
4. Disable wireless from the network manager applet and then

```
sudo modprobe -r ndiswrapper
```

If it cribs about module being in use, it means you have not disabled wireless
5. Restart, if there were any kernel upgrades
6. System->Administration->Hardware Drivers
I see a wl driver here. Make sure it says enabled and is in use.

worked for me with dell 1395 on inspiron 1525

---

### Post by Moustache on 2008-09-15
Thanks stats, worked nice for me too on a latitude D530.
Just follow the step 6 in case of an ubuntu install 'from scratch' .

[]s

---

