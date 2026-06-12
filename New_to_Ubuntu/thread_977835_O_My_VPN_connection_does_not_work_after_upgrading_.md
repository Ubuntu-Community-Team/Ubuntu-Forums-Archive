---
title: ":O My VPN connection does not work after upgrading to 8.10"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by legolas_w on 2008-11-10
Hi
Thank you for reading my post.
In 8.04 I have configured network applet to manage the network and i add support for VPN by using synaptic, now in 8.10 I do not know how to configure it to connect to my vpn network.
our vpn server is microsoft windows and I just have an ip address, a username and a password to connect to it but the new network applet does not have any place to enter the VPN information, 8.04 had a wizard to configure the VPN connections.
Any help about configuring the VPN is welcome.

Thanks

---

### Post by th89 on 2008-11-10
Assuming it is a Cisco based VPN, make sure you have network-manager-vpnc (sudo apt-get install network-manager-vpnc) installed. Then, to add a VPN network, go to System > Preferences > Network Connections > VPN (tab) > Add. You can configure it from there. Alternatively, click the NetworkManager Applet on the taskbar, and go down to VPN Connections. Select Configure VPN, then Add.

---

