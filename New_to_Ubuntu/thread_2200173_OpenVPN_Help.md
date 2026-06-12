---
title: "OpenVPN Help"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by Irish1 on 2014-01-17
Can anyone offer a newb some help setting up Open VPN? 

I want to try and be as anonymous as I can be when downloading torrents and OpenVPN seemed like a good option.  Like I said I'm a newb when it comes to the more advanced features of Ubuntu so after looking at a few pages on how to configure OpenVPN I realized that I might do more harm than good editing the files in etc/openvpn

Can anyone offer me some guidance or perhaps another solution?  I looked into proxy servers, but they don't seem to have the best reputation for security.  Unless someone could offer a good proxy server option that they trust...

Thanks for any and all advice.

Connell.

---

### Post by nerdtron on 2014-01-17
You won't be anonymous when you download torrent through OpenVPN, well, sort of.
The concept is you computer will connect to the Open VPN server and all your internet traffic will pass on the VPN server before it is reaches you. Your connection to the VPN server is tunnel and secured. 
When you download a torrent, torrent sites or "people watching you" will see the VPN server IP and not you computer IP. Now the problem is how do you setup the VPN server?
If you want to be anonymous, and want to create a VPN server, it should not on the same LAN of your computer, or is not using the same internet connection as yours.

---

### Post by Irish1 on 2014-01-17
Hmmm, okay.  So basically I'm going down the wrong path is what you're saying since I would use my home LAN connection for the torrents.  Would a proxy server suffice?  I mean I basically want to avoid someone from taking my IP address and using it later to say this guy and these thousands of other people are illegally downloading materials and we're going after them.

Thanks for replying, much appreciated.

---

### Post by nerdtron on 2014-01-17
If your internet connection is provided by the ISP say a normal home connection, the public internet will not directly see your computer IP as the one downloading torrents but rather the IP of you internet service provider. But if the ISP is monitoring traffic, they will see you as the one downloading bittorrent traffic.

Basically, you will not be the one caught first, but your ISP, then your ISP will point to you as the one responsible.

I'm not quite familiar with proxy servers but I heard about the TOR project before to anonymously hide your internet traffic. But I don't think it can hide bitorrent traffic.

---

### Post by mageta2 on 2014-01-18
For your purposes openvpn isn't what you want. If you were to subscribe to a vpn service, your traffic would leave your home, go through your isp, to the vpn server, then to the destination. The connection between your home and the vpn server would be encrypted, and so if your isp were to look at the traffic, they wouldn't know what was in it. Most of them have it in writing somewhere that they don't keep logs, or at least so they say, so in theory there's no evidence of wrongdoing. Having a vpn server in your home can be useful, you just have to understand that the tunnel ends in your house, so for example if you went to a coffee shop and used the wifi there to torrent something using your vpn connection, anyone in the coffee shop sniffing wifi data would not get anything from you because of the secure tunnel. The traffic would go from you, to your home, then out through your isp and to the destination, but once it leaves your home, the information is not encrypted anymore, and how could it be? Openvpn requires client side software to connect to the server, so it's just the path between you and the server at home, once it leaves the server it's plaintext unless it's over https or something.

In the terms you're searching for, a proxy server will do the same thing, it makes requests on behalf of a host, but the traffic isn't usually encrypted, it just acts as a middle man, relaying web requests back and forth like a middle man.

Tor uses something called onion routing, where the packets are encapsulated many times, at each router a layer is stripped off and only the next layer is revealed, so that no router knows the complete path. It's been a long time so I don't remember exactly how it works, but I think that's the basics of it.

---

