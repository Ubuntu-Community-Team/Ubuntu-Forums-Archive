---
title: "Open VPN what is the best gui for it?"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by TheManno1 on 2013-04-05
Also if posssible please link a tutorial for the best Gui?

---

### Post by TheManno1 on 2013-04-06
Bump.

---

### Post by sandyd on 2013-04-06
I just use the default networkmanager for openvpn.

You just have to install the appropraite network-manager-openvpn package.
Note that if you are using unity, the network-manager-openvpn-gnome package needs to be installed too

---

### Post by TheManno1 on 2013-04-06
Can you give me instructions?

---

### Post by TheManno1 on 2013-04-08
Bump.

---

### Post by coldraven on 2013-04-08
In Ubuntu 12.10, VPN is an option in the Network Manager.You can open it by clicking on the network icon in the top bar and select "Edit connections" or by opening the dash (windows key) and start typing "network".
I have never used VPN, hopefully someone else will tell you how.

---

### Post by TheManno1 on 2013-04-08
> **coldraven said:**
> In Ubuntu 12.10, VPN is an option in the Network Manager.You can open it by clicking on the network icon in the top bar and select "Edit connections" or by opening the dash (windows key) and start typing "network".
I have never used VPN, hopefully someone else will tell you how.

Isn't that for PPTP (point to point tunneling)? I want a gui to use for openvpn.

---

### Post by TheManno1 on 2013-04-09
Bump

---

### Post by sandyd on 2013-04-09
as said you need the networkmanager-openvpn and the network-manager-openvpn-gnome package before the openvpn option shows up.
restart nm-applet and networkmanager after installing
```

sudo apt-get install network-manager-openvpn network-manager-openvpn-gnome
```

---

### Post by TheManno1 on 2013-04-11
> **sandyd said:**
> as said you need the networkmanager-openvpn and the network-manager-openvpn-gnome package before the openvpn option shows up.
restart nm-applet and networkmanager after installing
```

sudo apt-get install network-manager-openvpn network-manager-openvpn-gnome
```

Did the terminal thing. I am using GNOME. OS Ubuntu 12.04 studio 64 bit.
What am I suppose to do now?

---

### Post by TheManno1 on 2013-04-12
Bump.

---

### Post by slickymaster on 2013-04-12
If you already installed **networkmanager-openvpn** and the **network-manager-openvpn-gnome** packages, as suggested by sandyd, your network applet menu will let you configure VPN connections. It will have an additional "VPN Connections" menu, with a submenu to "Configure VPN...". From there, you can import your existing .ovpn file, enter the location of your key and certificate files, enter the key password, etc.

Depending on your vpn server configuration and your needs, you may also want to define special DNS servers and/or check "Use this connection only for resources on it's network".

See [this]("https://help.ubuntu.com/community/OpenVPN") and [this]("https://help.ubuntu.com/community/VPNClient").

---

### Post by slickymaster on 2013-04-12
OpenVPN is entirely a community-supported OSS project which uses the GPL license. The project has many developers and contributors from OpenVPN Technologies, Inc and from the broader OpenVPN community. 
In addition, there are numerous projects that extend or are otherwise related to OpenVPN.

---

### Post by TheManno1 on 2013-04-15
Have Ubuntu Studio 12.04 64 bit [http://ubuntustudio.org/](http://ubuntustudio.org/)
For OpenVPN I am using the Gui 

**gadmin-openvpn-client** Version: 0.1.2-4 (precise)
gadmin-openvpn-client is a fast and easy to use GTK+ administration tool for
the OpenVPN client.

I will post my problem in the form of pics

---

### Post by TheManno1 on 2013-04-15
And this

---

### Post by TheManno1 on 2013-04-15
Last but not least this

---

### Post by TheManno1 on 2013-04-16
Bump

---

### Post by slickymaster on 2013-04-16
Try [GOpenVPN]("http://gopenvpn.sourceforge.net/") or [Gvpnc]("http://download.cnet.com/Gvpnc-for-Linux/3000-20432_4-75218296.html").

---

