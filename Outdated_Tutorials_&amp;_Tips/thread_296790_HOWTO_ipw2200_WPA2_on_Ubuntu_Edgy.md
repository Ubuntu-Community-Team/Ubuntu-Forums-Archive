---
title: "HOWTO: ipw2200 WPA2 on Ubuntu Edgy"
date: 2006-11-10
forum: Outdated Tutorials &amp; Tips
---

### Post by mrjyg on 2006-11-10
I'm a first-time Ubuntu user, with experience on Red Hat and SuSE.  I installed Edgy onto my Dell Inspiron 700m this week.  The laptop is used in office wired lan network and home wireless network, with multihead a must given the small 1280x800 screen, and it exposed several interesting issues:
1. Setting up profile management like SuSE's SCPM.
2. Getting ipw2200 WPA2 to work w/ my Linksys router.
3. Setting up multihead display w/ i810 driver.

This HOWTO discusses the 2nd issue above ... setting up ipw2200 WPA2.

What I tried but didn't work
----------------------------
- gnome-system-tools' 'Network Setup'
  It only supports WEP, but I need WPA/WPA2.
- wpa_supplicant -D ipw
  It just doesn't work.  ioctl error.
- kernel boot options lapic irqpoll
  Found a mention on the forum about these two options.  I tried it to see if wpa_supplicant / ipw2200 can hold onto the connection, instead of DISCONNECTED right after a successful connection (which is by itself a rare event).  It didn't make a difference
- ipw2200 driver option 'options ipw2200 hwcrypto=0'
  I tried it to improve the same reliability issue but it didn't make a difference either.

The recipe
----------
1. Create /etc/wpa_supplicant.conf, e.g.

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="My Linksys Router"
       bssid=00:FF:FF:FF:FF:FF
#       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=...
}

   a. My SSID is not broadcasted.  Normally I'd want ap_scan and scan_ssid settings above.  However connections were rarely established and quickly dropped.  I ended up copying the 'Access Point:' value (BSSID) from 'iwconfig' output.  This made a world of difference in reliability as well as performance in connection establishment.

   b. Value for psk comes from "wpa_passphrase <ssid> <passphrase>".

   c. RSN == WPA2.  CCMP == AES.

   d. This configuration file format is well documented in /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf[.gz].

2. Create /etc/network/interfaces entry for the wireless NIC, in my case it's eth1, e.g.

auto eth1
iface eth1 inet static
address 192.168.1.199
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid My Linksys Router
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

   a. I used static IP.  For dhcp:
iface eth1 inet dhcp
      and delete the address / netmask / gateway lines.

   b. No quotes around the wireless-essid value.

   c. Instead of pre-up / post-down lines suggested in existing HOWTOs, Edgy comes with /etc/init.d/wpa_ifupdown (S15 in rc0.d and rc6.d) for cleanup, and supports the wpa-driver / wpa-conf lines.

3. Upgrade ieee80211 / ipw2200 kernel modules.
   I tried this step before adding the bssid field into /etc/wpa_supplicant.conf, which didn't improve stability at all before the bssid addition.  So this may be optional.
   I tried the ieee80211-source and ipw2100-source from universe:
   - ieee80211-source does not work, maybe I didn't do the module-assistant correctly (it's my first Debian/Ubuntu OS!), maybe module-assistant didn't clean up old module (which is definitely the case here BTW).  The problem is symbol mismatch w/ kernel version.
   - ipw2100-source != source for ipw2200.

   So I downloaded the latest source from:
   [http://ieee80211.sourceforge.net/](http://ieee80211.sourceforge.net/)
   [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)
   [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)

   - Make sure modules are not loaded:
     + /etc/init.d/networking stop
     + rmmod ipw2200
     + rmmod ieee80211
     + rmmod ieee80211_crypto_* (do a lsmod | grep ieee80211_crypto_ and get the modules loaded)
     + rmmod ieee80211_crypto
   - Build and install ieee80211 first:
     + extract the tgz
     + . remove_old (and say yes to every question)
     + make; make install
   - Build and install ipw2200:
     + extract the tgz
     + . remove_old (and say yes to every question)
     + make; make install
   - Check if the downloaded ipw2200 (v3.0) firmware should be updated onto the system.  Edgy comes with the identical firmware so this step can be skipped.  The firmware is under /lib/firmware/`uname -r`/, ipw2200-*.fw files.
   - Load the modules:
     + modprobe ipw2200
   - Restart networking:
     + /etc/init.d/networking start

And it is now working for me :)

---

### Post by RD1945 on 2006-11-17
It worked for me too... TNX

---

### Post by Ken_C on 2006-11-19
I have just installed Ubuntu on my IBM Thinkpad R51 today. it too uses IPW2200. this is also my first exposure to linux. I'm used to being able to point and click and accomplishing what I set out to do with my computers. I'm totaly not used to having to edit configuration files etc to get things done. I will be needing to connect to 2 different wireless networks (no, not at the same time) one is wpa-tkip the other is wpa2-aes. is this doable? in windows I could use zero config and click on the net I wanted to use it was that simple. I'm lost and am going to need some hand guidance to even get on one net let alone 2. I have 2 HDs for this laptop and have installed ubuntu on one and have XP pro on the other. I have to remove one to use the other so this isn't going to be easy. should I concentrate on learning to find my way around the file system before I attempt to configure WI-FI? I don't even know how to get to this /etc/wpa_supplicant.conf, e.g.
total noob. SUB-noob I guess.
It sure would be nice to have an internet connection in linux so I can get help easier as I learn. hopefully the next versions will support more than just WEP from the desktop. Before today I would have thought that linux and its users would have abandoned WEP alltogather since it was linux and one of its users who cracked wep then told every hacker in the world how to do it. rendering it prety much useless for security of wi-fi.

---

### Post by daniloeu on 2006-11-19
Hey Guys...

Its very easy to configure and use WPA on Ubuntu...
Just install network-manager-gnome

It's a applet to configure network... Its work with WPA, WPA2, WEP and others...

To use it:

apt-get install network-manager-gnome

You will never more use wpa_supplicant and others "command line" things... =)


[]'s

Danilo Cesar
[http://www.danilocesar.com](http://www.danilocesar.com)

---

### Post by Ken_C on 2006-11-19
to use apt-get install, don't I first need to be connected to the internet? or does it take this stuff from the install cd.

---

### Post by compuguy1088 on 2006-11-19
I've done something similar like this before, by building the 1.20 ipw2200 drivers, it has become more stable, and I use network manager to connect to my WPA2 router, which may make it easier for people who connect to multiple networks as well as connection manager, which does at this point works with WPA2.

---

