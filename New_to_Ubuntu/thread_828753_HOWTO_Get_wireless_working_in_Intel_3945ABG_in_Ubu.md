---
title: "HOWTO: Get wireless working in Intel 3945ABG in Ubuntu 8.04"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-06-14
[COLOR="Red"][SIZE="5"]**Problem:**[/SIZE][/COLOR] Up until yesterday I was a die hard hater of hardy. Having upgraded about a month back nothing worked, the wireless did not work, the graphics card did not install, hibernation/suspend (admittedly did not work in gutsy either) did not work.

Yesterday I had some time so I thought I'd take the plunge again.

My nvidia gforce 7400 installed through the restricted drivers manager without a problem.

Hibernate/suspend worked PERFECTLY!!

Only problem was the wireless card, which while detected did not pick up any networks.

UNTIL I found this wonderful post: [https://bugs.launchpad.net/ubuntu/+bug/185470/comments/65](https://bugs.launchpad.net/ubuntu/+bug/185470/comments/65)
[B][COLOR="Red"][SIZE="5"]
Solution:[/SIZE][/COLOR][/B]
1. Open a terminal (Applications-accessories-terminal)
2. Input the following:
```

sudo modprobe -r iwl3945
cd /etc/modprobe.d
gksudo gedit iwl3945

```
3. In the blank file enter the following:
```

alias wlan0 iwl3945
iwl3945 disable_hw_scan=1

```
4. Back in the terminal:
```

sudo modprobe iwl3945
sudo ifconfig wlan0 up

```

Wait a few minutes and hotspots should start showing up. haven't had any more issues after that! If there are any more technically minded people perhaps they can enlighten us on how this actually works, and if hardy will fix this at some point (with an update).

---

### Post by lkraemer on 2008-11-02
abhiroopb,
I have a Gateway MT6840, and I had to add a few more commands along with your suggestions to get my Intel Pro 3945ABG working.  Here is what I did.

Edit file: /etc/udev/rules.d/70-persistent-net.rules

Use # to Comment out the line (if exists) that contains "ipw3945" **and the NEXT LINE of text**, then save the file, and exit. Use this command:

> sudo gedit /etc/udev/rules.d/70-persistent-net.rules

Edit file: /etc/modprobe.d/blacklist

Add the following two lines of text at the end of the file

#Blacklist this Driver - ipw3945
blacklist ipw3945

then save the file and exit
Use this command:

> sudo gedit /etc/modprobe.d/blacklist

From a Terminal Window, REMOVE these modules, and then reload the new ones:

> sudo modprobe -r ipw3945
sudo modprobe -r ieee80211
sudo modprobe -r ieee80211_crypt
sudo modprobe -r mac80211
sudo modprobe iwlwifi_mac80211
sudo modprobe -r iwl3945
sudo modprobe iwl3945
ifconfig wlan0 up


Reboot your computer.

If the Wifi, and/or LED's still don't work, try this Command:

> sudo apt-get install linux-backports-modules-hardy-generic

If all else fails, here is a good site that explains how you can go back to the previous drivers for Ubuntu 8.04 LTS.

[http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html](http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html)

One posting I ran across, said not to blacklist mac8021, as per item #1 in the above URL, but I don't know for sure. I guess you could try it both ways.

Here is a good site on troubleshooting your Wifi problems.

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

Here is a site that I found for those interested in patching their Kernel.
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

Thanks, for your HOWTO:!  Now maybe others can have success in getting their Intel 3945ABG working too!

Thanks.

lkraemer

---

### Post by reg4c on 2008-11-02
Just an FYI:

Using Acer Aspire 5920G with this card and this solution does not work
What I needed to do was download the ucode from the iwl project page and then put it in /etc/firmware folder, then run ```
ifconfig wlan0 up
```

Cheers

---

### Post by Dego Frank on 2008-12-10
i know this is an old thread, so sorry to bring it back to life, but i have a Sony Vaio VGN-N250E, and i reinstalled Ubuntu ver. 8.10 after being fed up with Vista for the final time. and i left the wireless switch on the right side of the computer infront of the mic/headphone jacks, and when it booted the OS into the desktop window it showed i had connection through not only the wired netword, but also the wireless network. so to test my theory i rebooted with the switch in the, "off" position and the wireless card wasn't able to re-enable itself, now i'm sure the card will work with Ubuntu 8.10, it's just a matter of complying to the way 8.10 wants it done. but here's where the kicker comes in, i leave my computer on over night since i'm downloading torrents, and when i logged onto the computer this morning the wireless card had shut itself off automatically, and the switch was still in the, "on" position...anyone have this problem??

---

