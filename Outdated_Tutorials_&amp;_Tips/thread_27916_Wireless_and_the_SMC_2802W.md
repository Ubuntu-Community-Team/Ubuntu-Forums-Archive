---
title: "Wireless and the SMC 2802W"
date: 2005-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by remmelt on 2005-04-18
This card gave me a bit of trouble.

First, note that there are TWO different versions of this card around: a v1 and a v2. If you have the v1, the prism54 drivers should cover you. It may even work out of the box on a clean Hoary install, but this was untested (by me).

The v2 looks like this: [picture](http://www.smc.com/images/products/400/SMC2802W.jpg), the v1 has a cover over the entire printboard, like it's "packed". In short, if yours doesn't look like the picture, and does have a 2802W name, it will be the v1.

The v2 does not work with the prism54 drivers. This has been noted and there are people working on it, or so I hear, but in the meantime we still want that wireless access working!
Here we go with the ndiswrappers.

First, install them:
apt-get install ndiswrapper-utils

Grab the Windows driver from the smc site:
[Go here and get it!](http://www.smc.com/index.cfm?event=downloads.searchCriteria&localeCode=EN_NLD&productCategory=0&modelNumber=541&downloadType=1&knowsPartNumber=false)

Unpack the Windows driver to a convenient place.

Note that this is all pretty straight forward regular vanilla flavoured ndiswrapper stuff.

The part that got me was this. When installing ndiswrapper, the card should show up as wlan0. The thing is, it was already picked up on by Ubuntu, and was loaded as eth0. Ndiswrapper told me the hardware was in place and found and ready, but there was no way I could get the card to work with the driver.
What needed to be done was unload the prism54 driver and THEN load the ndiswrapper.

As so:
modprobe -r prism54
Now do a 
dmesg | grep prism54
to see if the driver really was unloaded. It should say something like: prism54 unloaded.

Now the rest of the ndiswrapper stuff:
ndiswrapper -i /place_where_you_put_the_driver/WinXP/2802W.INF
I used the XP one, it worked.
Check if it loaded by going ndiswrapper -l (lowercase L)
If it did, do 
ndiswrapper -m
and
modprobe ndiswrapper
You should now have wireless access! Hurray!

Not done yet, though, because when you reboot, the prism54 driver will be in place again. This is because the hotplug system detects a card it thinks it can handle.
Do 
sudo gedit /etc/hotplug/blacklist

and add 
prism54
on a seperate line at the end of the file.

You can now safely reboot and have some wireless fun!

The part number that my 2802 W has is this: 99-012084-294. This is a v2, so if yours has the same part number, follow this guide. The part number can be found on the side of the box the card came in. (Tell me you do still have the box)

---

### Post by remmelt on 2005-04-18
If anybody finds out how to get the card working with WEP or better yet with WPA, please let me know and I will update the howto! I couldn't get it to work myself.....

---

### Post by jonny on 2005-04-18
[QUOTE=remmelt]If anybody finds out how to get the card working with WEP or better yet with WPA, please let me know and I will update the howto! I couldn't get it to work myself.....[/QUOTE]Are you attempting this from the command line or from the gnome networking applet?  There's a bug in the latter, explained [here](https://bugzilla.ubuntu.com/show_bug.cgi?id=3991), that means you have to prefix your password with s:

---

### Post by psYchotic on 2006-04-28
To setup your connection from the commandline, you have to do this:
```
psychotic@Otaconix:~$ sudo iwconfig wlan0 essid xyz enc s:xxxxxxxxxxxxx
psychotic@Otaconix:~$ sudo dhclient wlan0
```
With xyz being your essid and xxxxxxxxxxxxx would be your WEP password. You have to prefix it with "s:" if it's an ASCII password, which is what pretty much everyone uses I think. If you're using a hex password, don't prefix it with the "s:" and just enter it like that.

---

### Post by Embiggens on 2008-02-19
Hi, my recent experience with this card is that the module that ubunt gutsy tries to associate with the card is called "prism54pci".  Confusingly, I had to add the line
> blacklist p54pci
to the file /etc/modprobe.d/blacklist in order to successfully block this- ("blacklist prism54pci" did not work).  

(Note: I do have the smc2802w v2, and I'm 99% sure the model # is the exact same as in the original post. I'll have to double-check that when I get home today and edit this entry...)

---

