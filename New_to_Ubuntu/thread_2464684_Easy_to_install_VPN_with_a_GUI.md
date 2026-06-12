---
title: "Easy to install VPN with a GUI?"
date: 2021-07-08
forum: New to Ubuntu
---

### Post by avramroubenis on 2021-07-08
Greetings, all!

I'm looking forward to diving in to Ubuntu and learning about Linux.

Before I begin, I'd like to get a VPN up and running, but am having a hard time finding an easy to install package that's not operated through the terminal. I am having trouble installing Mullvad and Proton VPN (my favored application).

Any suggestions?

Many thanks,

Avram

---

### Post by TheFu on 2021-07-08
OpenVPN is supported through the Network Manager interface. check that you have the required packages installed, then import a .ovpn file that is provided from the VPN service.

[https://www.ovpn.com/en/guides/ubuntu-gui](https://www.ovpn.com/en/guides/ubuntu-gui)
[https://support.ipvanish.com/hc/en-us/articles/360007947233-OpenVPN-Setup-via-GUI-in-Ubuntu-18](https://support.ipvanish.com/hc/en-us/articles/360007947233-OpenVPN-Setup-via-GUI-in-Ubuntu-18)
[https://www.ricmedia.com/connect-openvpn-on-ubuntu-20-04-with-network-manager/](https://www.ricmedia.com/connect-openvpn-on-ubuntu-20-04-with-network-manager/)

Lets be extremely clear.  This is a client VPN application to connect to a commercial (paid) service.  

Since we are all Linux people here, many of us run VPN servers ourselves. There isn't any GUI to setup a VPN server that I'm aware, but setting up wireguard is about 10 steps, so very easy compared to openvpn or the others for 1-2 client connections.  [https://ubuntu.com/server/docs/service-openvpn](https://ubuntu.com/server/docs/service-openvpn) has steps to run your own openvpn server.

---

### Post by scorp123 on 2021-07-09
> **avramroubenis said:**
>  I'd like to get a VPN up and running, but am having a hard time finding an easy to install package that's not operated through the terminal

You seem to equate *"operated through the terminal"* with *"difficult"*??  That's not true. Just because something is *"operated through the terminal"* does not mean it's *"hard to use"*.

> **avramroubenis said:**
> Any suggestions?

I know that [SurfShark]("https://surfshark.com/") (and possibly others too?) provides downloadable OpenVPN configuration files that can be loaded into NetworkManager, e.g. on Ubuntu. You just need to fill in the correct values for username and password (in the NetworkManager user interface) when you add the configuration. From there on it's just a matter of clicking on the VPN node you want to connect to.

SurfShark provides easy to follow instructions with screenshots:
[https://support.surfshark.com/hc/en-us/articles/360012109779-Connect-to-Surfshark-VPN-using-Ubuntu-Network-Manager]("https://support.surfshark.com/hc/en-us/articles/360012109779-Connect-to-Surfshark-VPN-using-Ubuntu-Network-Manager")

There is an **inofficial (!)** GUI client for Linux that mimics the look of the Android app:
[https://github.com/jakeday/SurfShark-VPN-GUI]("https://github.com/jakeday/SurfShark-VPN-GUI")

---

### Post by avramroubenis on 2021-07-09
> You seem to equate *"operated through the terminal"* with *"difficult"*??  That's not true. Just because something is *"operated through the terminal"* does not mean it's *"hard to use"*.

Well, yes, for me. I'm just getting used to the idea of using a terminal, so yes, it is difficult for me. Someday, I too will know enough to eyeroll a beginner in a new user forum. But I won't.

---

### Post by avramroubenis on 2021-07-09
> OpenVPN is supported through the Network Manager interface. check that  you have the required packages installed, then import a .ovpn file that  is provided from the VPN service.

Thanks so much! I'll give it a try and will hopefully report back with success soon.

---

### Post by scorp123 on 2021-07-09
> **avramroubenis said:**
> Well, yes, for me. I'm just getting used to the idea of using a terminal, so yes, it is difficult for me. Someday, I too will know enough to eyeroll a beginner in a new user forum. But I won't.

Why do you misinterpret my comment as *"eyerolling"*?? I was trying to encourage you to give terminal-based things more consideration and not outright dismiss them as *"too difficult for me"* when they are really not *that* hard. Not at all. 

Oh well. Maybe I could have worded it better. My bad then.

---

### Post by avramroubenis on 2021-07-09
> **TheFu said:**
> Since we are all Linux people here, many of us run VPN servers ourselves. There isn't any GUI to setup a VPN server that I'm aware, but setting up wireguard is about 10 steps, so very easy compared to openvpn or the others for 1-2 client connections.  [https://ubuntu.com/server/docs/service-openvpn](https://ubuntu.com/server/docs/service-openvpn) has steps to run your own openvpn server.

I set up the vpn this morning. Once I get my sea legs, I'll try to run my own. Thanks again for your help!

---

