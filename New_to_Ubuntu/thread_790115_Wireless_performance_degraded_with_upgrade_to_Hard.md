---
title: "Wireless performance degraded with upgrade to Hardy"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by mgbridges on 2008-05-11
I've just upgraded from Gutsy to Hardy (which went pretty smoothly) but since the upgrade the connection to my wireless network is running at 45% rather than the 75% it was running at prior to the upgrade. Any ideas?

Martin

---

### Post by warbread on 2008-05-11
It could be that the new driver isn't as good, or the new driver is better at reporting the actual strength of your wireless signal.  It could even be that there has been no change to the driver at all and your wireless connection is being affected by solar radiation/static electricity/voodoo.  

Have you noticed any practical speed differences?  I.e, taking longer to connect, downloading slower, youtube videos being choppy, etc...

---

### Post by sdennie on 2008-05-11
I noticed that when switching from the ipw3945 driver to the iwl3945 driver (ipw was default in Gutsy, iwl is default in Hardy) that it reported lower wireless strength sometimes.  I don't know if it's reporting it more or less accurately but, it doesn't seem to have any effect on it's performance.

---

### Post by mgbridges on 2008-05-11
General web browsing performance seems to be reduced, so I don't think it's just a reporting issue.

I'm using the onboard wifi component of my Asus M2A-VM motherboard, by the way.

Martin

---

### Post by sdennie on 2008-05-11
What is the output of:

```

lsmod | grep mac80211

```

Unless you live somewhere with exceedingly fast broadband, I think the connection between your laptop and wireless router isn't likely to have much effect on your web browsing speed (unless your connection strength is low to the point of almost disconnecting).

---

### Post by mgbridges on 2008-05-11
I've no idea what this means, but the output of the above command is:

```
mac80211              192532  3 rt2500pci,rt2x00pci,rt2x00lib
cfg80211               17680  1 mac80211

```

Martin

---

### Post by sdennie on 2008-05-11
That just prints the modules that are using the wifi subsystem.  Unfortunately, I only have experience with intel wifi cards so I'm not sure if I can help much.

---

### Post by mgbridges on 2008-05-15
Still no luck in sorting this one out. The wireless card is an Asus WiFi-G, which I believe uses the Ralink RT2500 chipset.

My browsing performance is very poor, and downloads swing wildly in speed between dreadful and mediocre.

Any ideas? Considering rolling back to Gutsy if I can't find a solution to this.

Martin

---

