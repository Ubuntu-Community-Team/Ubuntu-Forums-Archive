---
title: "Cannot open Network settings"
date: 2014-03-30
forum: New to Ubuntu
---

### Post by quadrplax on 2014-03-30
Ubuntu 12.04.4 LTS 32bit

When I open system settings and click on "Network", the window resizes and loads it's content, but less than a second later it auto-closes. The first time it did this I got a popup asking me to tell Ubuntu about the problem, but I don't get that anymore, despite not checking the "Don't show again for same error" checkbox. I recently plugged in a MediaLink Wireless N USB Adapter, and did some testing with it. I don't know if it worked before, as I didn't need it before, but now I want to use the USB as a hotspot. This is on a laptop using the buit in network card for access. I tried rebooting without plugging it in and it didn't work. I didn't install the USB's drivers.


EDIT: I just ran system settings via the "gnome-control-center" command, and when I clicked network, it outputted:
```

(gnome-control-center:2706): Gtk-WARNING **: Overriding tab label for notebook

(gnome-control-center:2706): Gtk-WARNING **: Overriding tab label for notebook

(gnome-control-center:2706): Gtk-WARNING **: Overriding tab label for notebook
**
network-cc-panel:ERROR:rfkill-glib.c:83:type_to_string: code should not be reached
Aborted (core dumped)

```

EDIT2: I did it again with "gksudo gnome-control-center", it gave the similar, but slightly different:
```

(gnome-control-center:2724): Gtk-WARNING **: Overriding tab label for notebook

(gnome-control-center:2724): Gtk-WARNING **: Overriding tab label for notebook
**
network-cc-panel:ERROR:rfkill-glib.c:83:type_to_string: code should not be reached

```

EDIT3: (pardon the excessve edits) here is what it looks like just before it closes:
[IMG]http://i.imgur.com/Ui8QLvM.png[/IMG]

---

### Post by PartisanEntity on 2014-03-31
Hi there, perhaps the advice mentioned [here]("http://askubuntu.com/questions/351394/gnome-control-center-network-problem-crashing") may help. The user was advised to reconfigure the package Gnome Control Center.

First run:

```
sudo dpkg-reconfigure gnome-control-center
```

Then run:

```
sudo dpkg --configure -a
```

If that still does not help you can then try running:

```
sudo dpkg-reconfigure -a
```

Some more info on dpkg: [https://help.ubuntu.com/12.04/serverguide/dpkg.html](https://help.ubuntu.com/12.04/serverguide/dpkg.html)

---

### Post by quadrplax on 2014-03-31
I'll try that later today, interestingly, I used the same Ubuntu flash drive (see signiture) on a desktop computer and the Network settings worked fine. I'll see if they're still broken on the laptop later today.

---

### Post by quadrplax on 2014-03-31
I tried both flash drives, and neither of them worked in network settings.[**[COLOR=#C61919][B] PartisanEntity**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=192328"), you're commands did not solve the problem, not even the last one.

---

### Post by steeldriver on 2014-03-31
It looks like you may have a corrupted / non-sensical wired connection profile...? what does

```

ls -l /etc/NetworkManager/system-connections/

```

say? How about

```

nmcli con list

```

---

### Post by quadrplax on 2014-03-31
First command:
```

-rw------- 1 root root 293 Mar 26 18:57 [COLOR=#000080]**[A]**[/COLOR]
-rw------- 1 root root 329 Mar 29 09:53 [COLOR=#000080]**[A]**[/COLOR] 1
-rw------- 1 root root 314 Mar 30 20:50 [COLOR=#000080]**[A]**[/COLOR] 2
-rw------- 1 root root 363 Mar 30 20:53 [COLOR=#008000]**[B]**[/COLOR]

```

Second code:
```

NAME                      UUID                                   TYPE              TIMESTAMP-REAL                    
[COLOR=#000080]**[A] **[/COLOR]1            dba7497a-ec5d-4f38-8b12-ae41eda0ee4c   802-11-wireless   Sat 29 Mar 2014 02:57:58 PM CDT   
[COLOR=#000080]**[A]**[/COLOR] 2            867297fd-5887-44b0-a025-33a3c67b08fc   802-11-wireless   never                             
[COLOR=#008000]**[B] **[/COLOR]            6d82f62c-a5d4-4d7f-a7d1-a33671f8dda6   802-11-wireless   Sun 30 Mar 2014 08:58:16 PM CDT   
Wired connection 1        5b8d36e0-fe7c-41d0-a7de-f56571c287b7   802-3-ethernet    Mon 31 Mar 2014 05:05:10 PM CDT   
[COLOR=#000080]**[A]**[/COLOR]              238b946a-c6a7-4b42-aa1b-ace4aa96c3ca   802-11-wireless   Mon 31 Mar 2014 05:05:47 PM CDT 

```

[COLOR=#000080]**[A]**[/COLOR] is the SSID of my router
[COLOR=#008000]**[B]**[/COLOR] is the name of a test I made with "Create _N_ew Wireless Network"
I have a feeling it has something to do with [COLOR=#008000]**[B]**[/COLOR]...

---

### Post by quadrplax on 2014-04-01
I can't find anything about bumping in the Code of Conduct, so sorry if I  shouldn't do this, but I don't think many people venture back to the  3rd page, so:
*BUMP*

---

### Post by Iowan on 2014-04-01
> **quadrplax said:**
> I can't find anything about bumping in the Code of Conduct...That got moved to the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945")

---

### Post by steeldriver on 2014-04-02
You could try invoking the **connection editor** in a terminal instead of gnome-control-center

```
nm-connection-editor
```

and see what errors **that **throws. 

I think if it was me, I would be tempted to delete all the connection files in /etc/NetworkManager/system-connections (of course that assumes you know your credentials and can recreate them as necessary)

Another possibility might be to monitor dbus traffic for the nm object - I'd need to remind myself how to do that exactly (it's been a while since I played with dbus)

---

### Post by quadrplax on 2014-04-02
nw-connection-editor works fine, but I can't use that to create a hotspot (as far as I know). I deleted the connection files (weird, there was [SSID], [SSID] 1, and [SSID] 2). Sadly, that did not fix the problem.
> monitor dbus traffic for the nm object
Uhm...what? Sorry, I'm new, hence this post bwing in the "Absolute beginners section".

---

### Post by steeldriver on 2014-04-04
Sorry I'm about out of ideas - I still think it's odd that the window flashes up with what is obviously a loopback definition (127.0.1.1 etc.) but it doesn't seem to be picking that up from anything in the system-connections

Maybe purging and reinstalling network-manager-gnome? I know it sounds like desperation...

```

sudo apt-get remove --purge network-manager-gnome

sudo apt-get install network-manager-gnome

```

I just tried that here and it didn't appear to break anything - but if it wants to uninstall a whole bunch of stuff you should probably not go ahead (i.e. answer 'N' when it asks if you're sure)

---

### Post by quadrplax on 2014-04-04
That did not work, sadly. I'm not sure, it may have been lucky timing, but the thing seemed to crash once I clicked on wireless, shortly after clicking Network, after installing. However, I got an error message. Give me a few minutes, I'm going to edit this from the laptop...

EDIT: I''m an Ubuntu noob, so I don't know of any better way of doing this, but here is the crash in an imgur album of screenshots: [http://imgur.com/a/pPjBE](http://imgur.com/a/pPjBE)

---

### Post by PartisanEntity on 2014-04-08
I would recommend to give it some time. Please note that not every single issue can be addressed to its full extent by all our members who are volunteering their time to help out. I am sure that if and when someone can help out, they will to their best abilities.

---

### Post by quadrplax on 2014-04-08
Update: From the looks of it, after booting the computer, Network settings will work fine until I click "Wireless", at which point it crashes and can't be opened. Also to note, two "Wireless"es show up, probably because of the internal network card and wireless USB adapter.

---

### Post by steeldriver on 2014-04-10
Just had another look at this - it seems a lot like this bug --> [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1209092](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1209092) (although it's reported against 13.10 not 12.04)

---

### Post by JeQhdMD on 2014-04-13
I've had very good results by using this usb wireless adapter on my Lenovo H410 desktop:

[http://www.amazon.com/Panda-Ultra-Wireless-Adapter-150Mbps/dp/B00762YNMG/ref=sr_1_1?s=pc&ie=UTF8&qid=1397367743&sr=1-1&keywords=panda+ultra+wireless+n+usb+adapter](http://www.amazon.com/Panda-Ultra-Wireless-Adapter-150Mbps/dp/B00762YNMG/ref=sr_1_1?s=pc&ie=UTF8&qid=1397367743&sr=1-1&keywords=panda+ultra+wireless+n+usb+adapter)

I would suggest to try the device above, or better yet, a TP-Link 722n which is kernel supported natively in Linux (atheros chipset).

Another possibility is to use a Ubuntu 13.10 or 14.04 and see if native networking is better supported.

---

### Post by quadrplax on 2014-04-14
I still have the problem even if I haven't plugged in the USB since booting the laptop... and it's not worth getting another USB for my situation.

---

### Post by quadrplax on 2014-04-24
I closed my other topic that you always see bumped with this one, but I still would like this problem solved. I will update to Ubuntu 14.04 in late May and if the problem persists, I will continue posting here.

---

### Post by steeldriver on 2014-04-24
Have you submitted a bug report? that might be more productive than just bumping this thread

Out of curiosity, did you try disabling bluetooth (one of the suggested workarounds in the - apparently related - bug report)?

---

### Post by quadrplax on 2014-04-25
Yes, I had bluetooth disabled. Never thought that would be it, but I turn it off to save battery. I also don't plan to post here again unless 14.04 has the issue. Otherwise, I'll "Mark as Solved"

---

### Post by quadrplax on 2014-05-08
Problem fixed in Ubuntu 14.04, marking as solved

---

