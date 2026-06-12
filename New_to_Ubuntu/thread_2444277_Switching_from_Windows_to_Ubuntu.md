---
title: "Switching from Windows to Ubuntu"
date: 2020-05-27
forum: New to Ubuntu
---

### Post by billyed on 2020-05-27
I have just switched from Windows to Ubuntu, and I was using Ivacy VPN, but not I don't find any Ubuntu client on their Download VPN page, so can I configure it manually somehow on Ubuntu?

---

### Post by wildmanne39 on 2020-05-27
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by mastablasta on 2020-05-28
wireguard: [https://linuxconfig.org/how-to-create-a-vpn-on-ubuntu-20-04-using-wireguard](https://linuxconfig.org/how-to-create-a-vpn-on-ubuntu-20-04-using-wireguard)

there is also (more complex) openVPN: [https://www.cyberciti.biz/faq/ubuntu-20-04-lts-set-up-openvpn-server-in-5-minutes/](https://www.cyberciti.biz/faq/ubuntu-20-04-lts-set-up-openvpn-server-in-5-minutes/)
VPN GUI clients: [https://ubuntu.com/server/docs/vpn-clients](https://ubuntu.com/server/docs/vpn-clients)


but if you just want a client and services here is a top 10 list : [https://www.ubuntupit.com/linux-vpn-client-and-services-for-you-to-get-protected/](https://www.ubuntupit.com/linux-vpn-client-and-services-for-you-to-get-protected/)

---

### Post by sdsurfer on 2020-05-28
+1 for OpenVpn, use it daily working remote.

---

### Post by ActionParsnip on 2020-05-28
OpenVPN all the way

---

### Post by billyed on 2020-06-03
> **billyed said:**
> I have just switched from Windows to Ubuntu, and I was using Ivacy VPN, but not I don't find any Ubuntu client on their [Download VPN]("https://www.ivacy.com/download-vpn/") page, so can I configure it manually somehow on Ubuntu?

Any help in this regard?

---

### Post by freedombacon on 2020-06-03
It looks like Ivacy is distributing it as a DEB file and it looks like there's instructions how to get it, install it, or config manually here: [https://www.ivacy.com/download-vpn/linux-vpn/](https://www.ivacy.com/download-vpn/linux-vpn/)

If you don't want to use the DEB for whatever reason, the network manager applet where you configure the Wifi/NIC has an option to import a VPN config file. Ivacy has them here: [https://support.ivacy.com/vpnusecases/openvpn-files-windows-routers-ios-linux-and-mac/](https://support.ivacy.com/vpnusecases/openvpn-files-windows-routers-ios-linux-and-mac/)

---

### Post by TheFu on 2020-06-03
Perhaps it isn't clear but Ivacy actually uses openvpn.  There's nothing special about any openvpn service.  The same openvpn client that can be installed using apt will work great.  All you need are the client-side .ovpn files for each ext node to which you wish to connect.
The link posted by freedombacon above [https://support.ivacy.com/vpnusecases/openvpn-files-windows-routers-ios-linux-and-mac/](https://support.ivacy.com/vpnusecases/openvpn-files-windows-routers-ios-linux-and-mac/) has the ovpn files to download. import those into the openvpn part of network-manager.  That should show a new VPN connection for each.  You can add credential information to the ovpn files on your system if you don't want to be bothered.  

Should be easy and fully supported.

---

### Post by jmginer on 2020-06-05
+1 Wireguard, much better performance compared to OpenVPN

---

### Post by ActionParsnip on 2020-06-05
[https://support.ivacy.com/setup_guide/how-to-configure-openvpn-for-ubuntu-linux-with-ivacy-vpn/](https://support.ivacy.com/setup_guide/how-to-configure-openvpn-for-ubuntu-linux-with-ivacy-vpn/)

It's almost like they have a guide for this stuff........

---

