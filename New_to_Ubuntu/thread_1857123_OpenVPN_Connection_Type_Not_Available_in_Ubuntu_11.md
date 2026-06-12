---
title: "OpenVPN Connection Type Not Available in Ubuntu 11.04"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by slalomchip on 2011-10-09
I was unable to successfully upgrade form Ubuntu 10.10 to 11.04 because (I believe) of an incompatibility between by laptop's NVIDIA firmware and graphics drivers.  I finally gave up and did a clean install to 11.04. 

I use OpenVPN to remote into my home network when away (router is flashed to be the OpenVPN host).  Under Ubuntu 11.04, I installed OpenVPN version 2.1.3-2ubuntu3.  I copied the cert files and configuration files into the same folders they were in under Ubuntu 10.10.  Then I went to “Network Connections” to configure the VPN connection.  However, the only VPN connection type available is PPTP.  OpenVPN is not listed as a VPN Connection Type.
 

 Any ideas?  Thanks.

---

### Post by d4m1r on 2011-10-09
Are you connecting to a Windows machine? 11.04 has built in VPN function (find it under network manager, in your top bar) and use terminal server client to connect to Windows based PCs (or remote desktop for SSH/VNC connections).

---

### Post by alphacrucis2 on 2011-10-09
> **slalomchip said:**
> I was unable to successfully upgrade form Ubuntu 10.10 to 11.04 because (I believe) of an incompatibility between by laptop's NVIDIA firmware and graphics drivers.  I finally gave up and did a clean install to 11.04. 

I use OpenVPN to remote into my home network when away (router is flashed to be the OpenVPN host).  Under Ubuntu 11.04, I installed OpenVPN version 2.1.3-2ubuntu3.  I copied the cert files and configuration files into the same folders they were in under Ubuntu 10.10.  Then I went to “Network Connections” to configure the VPN connection.  However, the only VPN connection type available is PPTP.  OpenVPN is not listed as a VPN Connection Type.
 

 Any ideas?  Thanks.

```
sudo apt-get install network-manager-openvpn
```

---

### Post by slalomchip on 2011-10-09
Thanks, [alphacrucis2]("http://ubuntuforums.org/member.php?u=648132").  That solved it!

---

