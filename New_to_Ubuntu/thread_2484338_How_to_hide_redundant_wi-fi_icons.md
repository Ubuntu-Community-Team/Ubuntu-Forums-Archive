---
title: "How to hide redundant wi-fi icons?"
date: 2023-02-23
forum: New to Ubuntu
---

### Post by sergeymtv on 2023-02-23
Hi.

I've got 3 wifi icons on my tray bar (look at screenshot).  Only one is real. I want to remove 2 redundant icons but I can't find any way for this.
How do to this?

---

### Post by MAFoElffen on 2023-02-23
What flavor of Ubuntu are you running? Asking so I know which DE you are using...

On most, the right-most icon is the indicator applet / settings panel. The left-most should be the nm-applet or network manager applet, those two are normal on most flavor DE's. The third, not sure yet...

If you right-click on each, what does each bring up?

---

### Post by #&amp;thj^% on 2023-02-23
They look to me like VPN connection status icons
This may help to show us this:
```
sudo ls -l /etc/NetworkManager/system-connections/

```
I have 2 net interfaces for both WiFi  and Ethernet, and shows as:
```
[sudo] password for me: 
total 8
-rw------- 1 root root 252 Feb 20 20:42 'Wired connection 1.nmconnection'
-rw------- 1 root root 263 Feb 20 20:42 'Wired connection 2.nmconnection
```
Obviously my WifI is down so not shown above.

---

### Post by MAFoElffen on 2023-02-23
Yes, exactly. Unfortunately, lots of Ubuntu flavors and their DE's use the same icon file for VPN, Wifi Connection Status, and the Settings Status Icon. I would suspect that if a WLAN card has a connection, that it probably also uses that same icon. The one pictured looks like maybe Ubuntu Mate(?)

On my workstation, which is Gnome, I have 6 wired connections and I used to have two wifi cards (now just one)... So if I connected them to two different wifi networks, I then got two different wifi connection status icons, that showed each wifi connection and the signal strength of each... Just saying that I accepted that as normal for what it was displaying.

---

