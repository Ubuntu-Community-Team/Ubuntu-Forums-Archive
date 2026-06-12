---
title: "Ubuntu Server: How do i enable networking?"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by lyianx on 2013-06-18
I had some trouble during the install on the network setup, and just told it i would set up the network later. What i didnt expect however, is that by default, Ubuntu server doesnt have a GUI enabled, so i dont know how to do that. I want to enable a GUI next, but from what ive read, i need my internet connection active in order to do that. Maybe im bad for jumping stright to the server version over the desktop version, but its what im wanting to use it for. Were can i go to setup my network card to work with my router?

Thanks

---

### Post by The Cog on 2013-06-18
But pretty-much the only difference between the desktop and server versions is the absence of a desktop in the server version. Still, your call.

In the server version, the networking is set up in file /etc/network/interfaces. For a server, you probably want a static IP address. Here is an example configuration stanza for a static IP address:

```
# The main network interface
auto eth0
iface eth0 inet static
    address 192.168.1.42
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1

    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.1.40 192.168.2.40
    dns-search mydomain.com
```

---

### Post by lyianx on 2013-06-18
> **The Cog said:**
> But pretty-much the only difference between the desktop and server versions is the absence of a desktop in the server version. Still, your call.

In the server version, the networking is set up in file /etc/network/interfaces. For a server, you probably want a static IP address. Here is an example configuration stanza for a static IP address:




Oh? So would i get the same tools and efficiency from the desktop version as i would the server version? I just got it installed so its no big deal to re-install a different one.

---

### Post by zero2xiii on 2013-06-18
Hay,

> Oh? So would i get the same tools and efficiency from the desktop version as i would the server version? I just got it installed so its no big deal to re-install a different one.

In my opinion, if you need to ask that, install a "normal" ubuntu (one with a desktop environment NOT a server install) and then use that and if you so desire later, you can disable the DE so it boots exactly like the server install you currently have, with the difference you can start a DE later if you need.

I am not trying to be rude, but I strongly suggest you state more clearly what you mean. "Tools and efficiency" can be VERY subjective. Most server admins do not touch the GUI, most power users use the terminal above the GUI versions of most "tools" some people even choose nano over gedit for editing config files.

Bottom line, in my opinion, install a normal system and you can do everything anyway you please, albeit most people here will help you by running stuff in terminal, so it is a win-win-loose-loose situation.

Cheers and good luck.

EDIT:
Assuming you are not setting up any MAJOR server yet, the easiest way to get it onto a network (assuming the network has a DHCP host) is by running:
```
sudo dhclient
```
This will auto configure a wired connection connected to a DHCP network, as stated above, this will be a dynamic IP address, but can be made static by following the above if you so desire.

---

### Post by nothingspecial on 2013-06-18
> **lyianx said:**
> Oh? So would i get the same tools and efficiency from the desktop version as i would the server version? I just got it installed so its no big deal to re-install a different one.

They are exactly the same packages.

---

### Post by The Cog on 2013-06-23
> **lyianx said:**
> Oh? So would i get the same tools and efficiency from the desktop version as i would the server version? I just got it installed so its no big deal to re-install a different one.

Sorry I've taken so long to get back to you.

If you haven't already installed the desktop version instead, you can install all the desktop stuff on the server with the command:
```
sudo apt-get install ubuntu-desktop
```
although I personally prefer xubuntu-desktop.

With Ubuntu, the server version has all the GUI stuff removed. The reason being that a server sits in a rack in a data centre with no screen and is managed remotely. You can always turn all the GUI stuff off when it's being used as a server, to save some memory. But if you're not familiar with Linux administration then you are better off having the GUI stuff installed.

P.S.
The GUI network configuration utility will ignore interfaces that are configured in the /etc/network/interfaces file, so if you want to be able to use the GUI to configure eth0, comment out all its config in the interfaces file agin.

---

### Post by jdthood on 2013-06-24
@lyianx: Ubuntu Server networking is configured in /etc/network/interfaces as mentioned earlier. Ubuntu Desktop includes the NetworkManager utility which offers a GUI for network configuration. If you install NetworkManager on a machine where networking has already been configured in /etc/network/interfaces then it's best to delete everything from /etc/network/interfaces except "auto lo\niface lo inet loopback" and then configure interfaces anew using the NetworkManager connection editor.

---

