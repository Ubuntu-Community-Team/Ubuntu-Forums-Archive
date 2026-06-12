---
title: "VPN will not work."
date: 2015-07-10
forum: New to Ubuntu
---

### Post by mlempenau on 2015-07-10
I am having the same problem on two computers.  One is running 12.04 and the other is 14.04.  They have all the updates.  I am using network connection manager.  I have followed all the instructions from my VPN provider.  Both computers logon but then almost immediately logoff.  I have a duel boot on one and using windows I can connect successfully.  Altho I have used ubuntu for several years, I am very limited in what I understand.  Any simple instructions would be appreciated.

---

### Post by dino99 on 2015-07-10
Maybe ubuntu does not like your vpn provider instructions: as you can login but get logout then, i suppose you might have something logged to help you digging around that issue.
maybe reread the actual ubuntu howto/wiki:
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04)

---

### Post by rachman2 on 2015-07-10
Yeah

---

### Post by Skaperen on 2015-07-10
does regular traffic like ssh work?  **what are you trying to accomplish?  a VPN tunnel between these hosts?** _maybe your VPN provider does not like Ubuntu._

---

### Post by mlempenau on 2015-07-10
My purpose in this is to be able to logon to Social Security using PPTP.  I just want a simple VPN connection to work.  My VPN provider is StrongVPN and they have switched servers for me already.  They have instructions for Linux on their website.  My normal network connection works just fine.

---

### Post by Skaperen on 2015-07-10
SS uses tunneling (PPTP) for logins?   sounds like it is very insecure (by social engineering).

---

### Post by Geoffrey_Arndt on 2015-07-10
+1 re Skaperen . . . PPTP not a good choice for VPN anymore (insecure) - - and have you installed "OpenVpn" via the Ubuntu Software Center?   After installing it, try the instructions from StrongVPN once again.

---

### Post by sandyd on 2015-07-10
[http://strongvpn.com/setup_ubuntu_10.10_openvpn.shtml](http://strongvpn.com/setup_ubuntu_10.10_openvpn.shtml)

Despite it saying Ubuntu 10.10 and the screenshots being a tad outdated, the instructions are still valid

---

### Post by mlempenau on 2015-07-12
My network connections manager does not show an import export option????  I installed using the terminal as noted on the instructions.  A copy of my terminal output is below...

mlempenau@mlempenau1404:~$ sudo apt-get install -y network-manager-openvpn
[sudo] password for mlempenau: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-openvpn is already the newest version.
The following packages were automatically installed and are no longer required:
  kde-l10n-engb kde-l10n-th libsvga1 linux-headers-3.13.0-24
  linux-headers-3.13.0-24-generic linux-headers-3.13.0-43
  linux-headers-3.13.0-43-generic linux-headers-generic
  linux-image-3.13.0-24-generic linux-image-3.13.0-43-generic
  linux-image-extra-3.13.0-24-generic linux-image-extra-3.13.0-43-generic
  linux-image-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.

---

### Post by mlempenau on 2015-07-13
I have finally figured out how to import the vpn information.  But now I get an error - [FONT=arial]The VPN connection 'strongvpn' failed because the VPN service failed to start.  Now what do I do?[/FONT]

---

### Post by mlempenau on 2015-07-14
THis is from system log ... 

Jul 14 14:46:05 mlempenau1404 NetworkManager[790]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jul 14 14:46:05 mlempenau1404 NetworkManager[790]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Jul 14 14:46:10 mlempenau1404 NetworkManager[790]: <info> VPN service 'openvpn' disappeared
Jul 14 14:48:05 mlempenau1404 ipsec_setup: permission denied (must be superuser)
mlempenau@mlempenau1404:~$

---

### Post by mlempenau on 2015-07-15
I went to the systemlog and found out what the error was.  Then I went through about three different support staff before someone knew how to correct the problem.  Now the strongvpn connection is working.

---

### Post by mlempenau on 2015-07-15
solved

---

### Post by bapoumba on 2015-07-15
> **mlempenau said:**
> I went to the systemlog and found out what the error was.  Then I went through about three different support staff before someone knew how to correct the problem.  Now the strongvpn connection is working.

> **mlempenau said:**
> solved

Is it possible you post the solution ? Thanks.
You can mark the thread as solved in the Thread Tools menu.

---

