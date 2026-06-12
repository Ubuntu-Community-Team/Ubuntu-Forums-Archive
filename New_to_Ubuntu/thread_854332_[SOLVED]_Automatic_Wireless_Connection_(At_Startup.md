---
title: "[SOLVED] Automatic Wireless Connection (At Startup)?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by BassKozz on 2008-07-09
Everytime I boot my computer I have to enter:
```
iwconfig eth1 essid "mySSID" key mywepkey
sudo dhclient eth1
```
Where ***mySSID*** = My wireless router's SSID
and ***mywepkey*** = My router's wep key

But now I am trying to figure out how to put this in a startup script so it runs every time I boot (because as of right now I have to manually add the above each time I restart to connect to my router  :( )
Can someone let me know what I need to do to get this to connect each time I reboot?

---

### Post by mikewhatever on 2008-07-09
I think you can do it through a nice GUI under System>Admin>Network.

---

### Post by BassKozz on 2008-07-09
> **mikewhatever said:**
> I think you can do it through a nice GUI under System>Admin>Network.
I probably should've mentioned this in my initial post, but I am using a limited version (cli) of Gusty Unbuntu that I installed on my [OLPC]("http://laptop.org"), and I am using Xfce as my GUI, and there doesn't seem to be a Wireless Networking tool in the GUI, so I need to modify a startup script, but I don't know which one to modify (i.e. /etc/networking/interfaces , /etc/init.d/, ???)

**_EDIT_**:I should've picked "[color=RED]**other**[/color]" when picking a prefix for this thread :doh:

---

### Post by issih on 2008-07-09
You want to change /etc/network/interfaces. That file defines the network interfaces and which ones should be automatically brought up.


you need to add something like:
```

iface wlan0 inet dhcp
wireless-key s:myKey
wireless-essid myNetwork

auto wlan0
```

I believe the s: indicates that you are using an asci wep key, without it you need to enter a hexadecimal one. This assumes you use dhcp for your ip addresses.

Hope that helps

P.S. dont't mess with the lo interface lines, you need those :)

---

### Post by mikewhatever on 2008-07-09
> **BassKozz said:**
> I probably should've mentioned this in my initial post, but I am using a limited version (cli) of Gusty Unbuntu that I installed on my [OLPC]("http://laptop.org"), and I am using Xfce as my GUI, and there doesn't seem to be a Wireless Networking tool in the GUI, so I need to modify a startup script, but I don't know which one to modify (i.e. /etc/networking/interfaces , /etc/init.d/, ???)

**_EDIT_**:I should've picked "[color=RED]**other**[/color]" when picking a prefix for this thread :doh:

I see. Here is a sticky address from the Wireless section, that has all kinds of manual configurations. [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by Matt Yun on 2008-07-09
May I suggest [Wicd]("http://wicd.sourceforge.net/").  It's a network manager GUI utility that supports WEP, WPA and autoconnect.  I'm using it as an alternative to Gnome's default network manager.

[Ubuntu documentation on Wicd]("https://help.ubuntu.com/community/WICD").

---

### Post by BassKozz on 2008-07-09
> **issih said:**
> You want to change /etc/network/interfaces. That file defines the network interfaces and which ones should be automatically brought up.


you need to add something like:
```

iface wlan0 inet dhcp
wireless-key s:myKey
wireless-essid myNetwork

auto wlan0
```

I believe the s: indicates that you are using an asci wep key, without it you need to enter a hexadecimal one. This assumes you use dhcp for your ip addresses.

Hope that helps

P.S. dont't mess with the lo interface lines, you need those :)
```
# Wireless Connection
iface eth1 inet dhcp
wireless-key hex-key
wireless-essid ssid

auto eth1
```
where ***hex-key*** = my WEP hex key & ***ssid*** = my routers wireless SSID
WORKED :D
Thanks issih

---

### Post by stchman on 2008-07-09
> **BassKozz said:**
> Everytime I boot my computer I have to enter:
```
iwconfig eth1 essid "mySSID" key mywepkey
sudo dhclient eth1
```
Where ***mySSID*** = My wireless router's SSID
and ***mywepkey*** = My router's wep key

But now I am trying to figure out how to put this in a startup script so it runs every time I boot (because as of right now I have to manually add the above each time I restart to connect to my router  :( )
Can someone let me know what I need to do to get this to connect each time I reboot?

Network Manager under Hardy takes care of all that.  What Ubuntu version are you using?

Whenever I login Ubuntu automatically connects to my WPA2 encrypted router.

---

### Post by BassKozz on 2008-07-09
> **stchman said:**
> Network Manager under Hardy takes care of all that.  What Ubuntu version are you using?

Whenever I login Ubuntu automatically connects to my WPA2 encrypted router.
> **BassKozz said:**
> I probably should've mentioned this in my initial post, but I am using a limited version (cli) of Gusty Unbuntu that I installed on my [OLPC]("http://laptop.org"), and I am using Xfce as my GUI, and there doesn't seem to be a Wireless Networking tool in the GUI, so I need to modify a startup script, but I don't know which one to modify (i.e. /etc/networking/interfaces , /etc/init.d/, ???)

**_EDIT_**:I should've picked "[color=RED]**other**[/color]" when picking a prefix for this thread :doh:
;)

---

### Post by BassKozz on 2008-07-09
> **mikewhatever said:**
> I see. Here is a sticky address from the Wireless section, that has all kinds of manual configurations. [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Mike,
That link you provided was very helpful, Thank you.
I am curious thou, on the link it says to edit ***/etc/rc.local*** to make ubuntu setup wireless on boot;
What are the pro's & con's of using ***/etc/rc.local*** vs. ***/etc/network/interfaces/*** to connect on boot?

---

### Post by BassKozz on 2008-07-13
> **BassKozz said:**
> What are the pro's & con's of using ***/etc/rc.local*** vs. ***/etc/network/interfaces/*** to connect on boot?

Anyone?

---

