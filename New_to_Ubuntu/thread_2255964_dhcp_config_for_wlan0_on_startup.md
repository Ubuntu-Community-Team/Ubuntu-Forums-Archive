---
title: "dhcp config for wlan0 on startup"
date: 2014-12-08
forum: New to Ubuntu
---

### Post by chris_morris2 on 2014-12-08
First time setting up Ubuntu Server.

I setup a wpa.sh script init.d which is working fine for setting up wlan0, but after reboot, no IP address is assigned, of course. Using dhclient works and then I can ssh into the box.

I tried setting up /etc/network/interfaces according to these instructions: [https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic#Configure_your_wireless_interface](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic#Configure_your_wireless_interface)

After reboot, an IP address is assigned to wlan0, and sshd is running, but port 22 is not open (according to nmap on a client machine) and I can't connect to the machine.

I backed out the changes to /etc/network/interfaces and rebooted, logged into the main console and ran dhclient and then both the assigned IP address and sshd work fine.

I'm sure I'm overlooking something simple, but my Google-fu is failing me at this point.

---

### Post by chris_morris2 on 2014-12-08
(take 2 - post body disappeared) ... (and now it's there)

---

### Post by chris_morris2 on 2014-12-08
I've also double-checked that I'm not rebooting into single user mode, but that's still possible that I'm doing something along those lines to confuse the issue.

---

### Post by chris_morris2 on 2014-12-09
Setting up /etc/network/interfaces to static entries also has the same problem after reboot. It's as if the wlan0 simply isn't working - some piece is missing.

---

