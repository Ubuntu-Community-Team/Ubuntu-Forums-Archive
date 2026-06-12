---
title: "takes ages to connect to a wired network in hardy heron"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by philphil on 2008-05-04
Hi all,

Just updated to Hardy Heron and I'm having trouble when I connect to my wired network at home.  In Gutsy it was fine and it would connect almost instantaneously but in Hardy it can take up to about a minute of watching those little blue things whirling round in the notification panel until it finally connects.  

Any ideas?

Cheers!

---

### Post by philphil on 2008-05-21
bump!

---

### Post by geezerone on 2008-05-21
Are you using dhcp or static ip addressing and are you using WICD also as your network applet rather than network manager?

---

### Post by BDNiner on 2008-05-21
I have the opposite problem. LAN connections are instant, wireless connections take about 1 minute to connect.

---

### Post by ingrid_ozikem on 2008-05-21
Same wireless problem with Hardy. Works sometimes like a charm but sometimes takes forever and repeated attempts. The network I want to connect to uses DHCP.

I think it might be related to having it in Roamer mode where the Network Manager searches for any and all wireless networks and connects to one of them.

I used Network under System -> Admin menu to do a manual config where I specify the SSID of the specific network I want to connect to and specify that it is DHCP. Worked immediately.. but I haven't tried this repeatedly to see if this is indeed the proble.

Also, when things do fail, these are messages I have in my debug log. 

May 21 11:13:17 sierra NetworkManager: <debug> [#########.#####] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'AirNetwork' 

This triggered update seems to be the problem.. perhaps the manager keeps resetting the search if the connection is not made immediately?

---

### Post by philphil on 2008-05-21
> **geezerone said:**
> Are you using dhcp or static ip addressing and are you using WICD also as your network applet rather than network manager?

using DHCP and network manager

roaming is enabled, do you think this could be it?

---

### Post by ThreeTrees on 2008-05-21
This sounds like my problem in [http://ubuntuforums.org/showthread.php?t=796692]("http://ubuntuforums.org/showthread.php?t=796692") except for wireless (like BDNiner and ingrid_ozikem).  I haven't tried with a direct wired connection.

Stupid question (but this *is* Absolute Beginner Talk): how do I know if I'm using Network Manager or wicd?

---

### Post by geezerone on 2008-05-22
> **ThreeTrees said:**
> ... Stupid question (but this *is* Absolute Beginner Talk): how do I know if I'm using Network Manager or wicd?

Bottom RHS there will be a two small computer screen icon. Right-click and click the 'about' text. This will show nm-applet (network manager). Wicd has to be installed separately (see my signature link).

---

### Post by Iowan on 2008-05-22
> **philphil said:**
> using DHCP and network manager

roaming is enabled, do you think this could be it? Shouldn't take long to un-click it and find out.  (May need to restart networking) If it gets worse... put it back!

---

### Post by geezerone on 2008-05-22
Like Iowan said, suck it and see. Try fixed IP and you may need to reboot the PC completely as restarting networking (/etc/init.d/networking restart) didn't work well for me.

---

### Post by philphil on 2008-05-24
Yes, that seems to have been it, disabled roaming and it's ok.

---

