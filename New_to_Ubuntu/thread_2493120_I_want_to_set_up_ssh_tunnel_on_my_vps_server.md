---
title: "I want to set up ssh tunnel on my vps server"
date: 2023-12-04
forum: New to Ubuntu
---

### Post by megaster on 2023-12-04
I want to set up ssh tunnel to use VPN on a VPS server I rent, how can I do this? The VPN application I use works as host:port@user:password. Please help me. I couldn't find a simple source that I can understand.

---

### Post by TheFu on 2023-12-04
ssh isn't a VPN.  That's a different thing.  ssh leaks non-tcp traffic, like DNS and most streaming protocols, which makes it unsuitable if you are trying to have all your traffic go through the VPS.

For a simple SOCKS proxy, I've posted a script that connects to a remote system using ssh and tells the browser to use it as a SOCKS5 proxy.  Going outbound, that really isn't secure enough.  OTOH, when you are away from home and want to access LAN-only websites inside your house, it is fine.  

[https://ubuntuforums.org/showthread.php?t=2482592&highlight=ssh+socks5+proxy](https://ubuntuforums.org/showthread.php?t=2482592&highlight=ssh+socks5+proxy) has an example.

---

### Post by SeijiSensei on 2023-12-05
I use simple static-key configurations with OpenVPN.

[https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

I use that to create secure tunnels between my remote cloud servers and my home office.

---

