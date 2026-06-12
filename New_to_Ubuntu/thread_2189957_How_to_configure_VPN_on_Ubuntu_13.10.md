---
title: "How to configure VPN on Ubuntu 13.10"
date: 2013-11-25
forum: New to Ubuntu
---

### Post by frogwarrior on 2013-11-25
I just installed Ubuntu 13.10 and installed GNOME rollback to get the  old desktop environment that I'm used to, and when I click on the  network connection icon (on the top bar) -> VPN Connections ->  Configure VPN the VPN configuration tool doesn't come up, instead this  comes up:
[IMG]http://gyazo.com/36077b43e601d05808da255154878306.png[/IMG]
which is the Edit Connections interface, not the VPN configuration interface. this didn't happen with Ubuntu 12.04. Is there a command I can use to bring up the VPN connection interface?

---

### Post by frogwarrior on 2013-11-27
I figured it out. With this new Network Connections interface, you just need to click Add, then select PPTP VPN, and the VPN interface comes up:
[IMG]http://gyazo.com/75ecff1c541613e0b24eee2b756b0fe9.png[/IMG]
A problem I have no is that it doesn't give me the option of creating a new openvpn connection, the only option in the list is pptp.


EDIT: I solved that by installing network-manager-openvpn

---

