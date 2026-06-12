---
title: "&quot;unable to load VPN connection editor&quot;"
date: 2018-10-11
forum: New to Ubuntu
---

### Post by karebo on 2018-10-11
I have succeeded in installing Ubuntu 18.04 With GUI Gnome
on my new server, planned as a P2P moviebox with my Windows 10 PC.

The task I am facing now is installing VPN Private Internet Access, 
using this support: [https://www.privateinternetaccess.com/helpdesk/guides/desktop/linux/ubuntu-gnome-network-manager](https://www.privateinternetaccess.com/helpdesk/guides/desktop/linux/ubuntu-gnome-network-manager)

In step 5, Settings, Open VPN, Identity where name of VPN, username, password etc should be written,
I am informed that Ubuntu is "unable to load VPN Connection editor" and hence installation process halts.

What can I do?

( Whether this has any significance I do not know: the recommended "network-manager-openvpn-gnome"
could not be installed, Ubuntu suggested the substitute "network-manager-openvpn", which installed)

---

### Post by chrispytoes on 2018-11-25
Bumping for the exact same problem

I am using IPVanish and I'm also trying to follow the tutorial but I am never able to enter my credentials and I see the [COLOR=#000000]"unable to load VPN Connection editor" message.

On another note, I also tried importing the .ovpn file provided by IPVanish but I get an error message saying "Cannot import VPN connection"  and that the file could not be read.[/COLOR]

---

### Post by Damian_Kober on 2019-06-11
sudo apt install network-manager-openvpn-gnome

sudo service network-manager restart

---

