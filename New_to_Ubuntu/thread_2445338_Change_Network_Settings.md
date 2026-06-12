---
title: "Change Network Settings"
date: 2020-06-12
forum: New to Ubuntu
---

### Post by jscooper22 on 2020-06-12
So simple I'm embarrassed to ask (can you tell I'm new?):

I installed Ubuntu Server and Gnome on  a VM for testing.

Settings > Network only has options to set up a VPN or Proxy, but no "wired". Where do I edit my network settings? I swear I did this in a GUI years ago.

Thanks (...and glad to be here),

Jeff

---

### Post by TheFu on 2020-06-12
Ubuntu Server doesn't have any GUI.
Adding a specific DE, but not the entire DE-desktop metapackage (which installed 50+ other things) won't get all those little things added.  
In 18.04 and 20.04 server, network settings are controlled by netplan YAML configuration files ... in /etc/netplan/.  

To use DHCP, a file like this:
```
network:
  version: 2
  renderer: networkd
  ethernets:
    [COLOR="#FF0000"]enxc0335eee554f[/COLOR]:
      dhcp4: true
      dhcp6: false
```
Just change the ethernet named device to match yours.  10 yrs ago, that would have been eth0. Today, the name is generated so almost always different on each system based on the driver and MAC.  Be very careful about indentation. YAML isn't forgiving.

---

### Post by jscooper22 on 2020-06-12
AH! Thank you!

---

