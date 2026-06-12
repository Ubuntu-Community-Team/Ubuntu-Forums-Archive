---
title: "Restore WiFi connecitons"
date: 2015-04-27
forum: New to Ubuntu
---

### Post by danne33 on 2015-04-27
Needed to reinstall Ubuntu 14.04 on my computer. 
I made a full backup of all my network-connections files so I could restore them after the backup. 
What I have done is the following:
Made a backup of all the files in /etc/NetworkManager/system-connections/ before reinstalling Ubuntu 14.04 on my computer.
Now I have restored all the files to /etc/NetworkManager/system-connections/ and changed the ownership to root with following command: sudo chown root.root

My problem is now that NetworkManager doesn't load the configuration from the backup files. At least I can't see them in nm-applet.
Tried to reboot the computer and reboot network-manager (sudo restart network-manager). None of that worked... 
Anyone know how I can make the network-manager load the configuration files again in /etc/NetworkManager/system-connections/

---

