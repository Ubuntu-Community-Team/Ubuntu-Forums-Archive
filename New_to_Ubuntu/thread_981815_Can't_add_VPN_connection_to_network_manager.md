---
title: "Can't add VPN connection to network manager"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by bcd87 on 2008-11-14
Hi there,

Topic says it all really, for some reason the Add button on the VPN tab in network manager is greyed out. How do I get it to work?

---

### Post by SamNSane on 2008-11-14
I wonder if this "VPN" is for creating dial-up VPN instances.

I don't know, just asking the question. On the Windows side I've set up a lot of VPN connections, but I never once used the Windows create a VPN connection option.

---

### Post by hansblitz on 2008-11-15
yeah, you gotta install some extra packages. something like openvpn. just type vpn in add/remove and install it.

---

### Post by wetling on 2008-12-17
I used Synaptic to search for "VPN".  Since we're using Cisco's VPN solution, I installed network-manager-vpnc, then I was able to configure the VPN connection through the network manager GUI.

---

### Post by tbsalling on 2009-04-03
This did it for me on Ubuntu 8.10:
```
sudo apt-get install network-manager-openvpn
```
/Thomas.

---

### Post by Johnsie on 2009-08-31
In  a modern operating system this should work out of the box. I don't know about OSX, but Windows 7 certainly has this feature out of the box and it s reasonably easy to configure.

---

### Post by XCan on 2009-08-31
Well, or at least give the user some hint of it, instead of only showing a grayed-out box. :)

---

### Post by matt082606 on 2009-10-29
I agree this should be built in.  I have installed the vpn via:
 sudo apt-get install network-manager-openvpn

and it gave me the add button.  However after filling in the details I never get the APPLY button to become available.

Anyone have that issue?  The VPN I am trying to set up is just a simple password authentication.

Thanks

---

### Post by AnUser on 2009-11-22
> **matt082606 said:**
> I agree this should be built in.  I have installed the vpn via:
 sudo apt-get install network-manager-openvpn

and it gave me the add button.  However after filling in the details I never get the APPLY button to become available.

Anyone have that issue?  The VPN I am trying to set up is just a simple password authentication.

Thanks
I'm having the exact same problem. Any help is appreciated.

---

### Post by allmanbro2 on 2010-02-01
This link:

[http://www.craigmayhew.com/blog/2009/11/setting-up-vpn-in-ubuntu-9-10-karmic-koala/](http://www.craigmayhew.com/blog/2009/11/setting-up-vpn-in-ubuntu-9-10-karmic-koala/)

suggests adding these three packages using the following command:

```
sudo apt-get install network-manager-pptp network-manager-vpnc network-manager-openvpn
```

That gets past the gray add button, then the gray apply button. I'm running into other problems now, but my fingers are crossed...

---

### Post by Dugger5688 on 2010-03-03
After you install the network-manager-vpnc/openvpn/pptp make sure to do a 

```
sudo /etc/init.d/networking restart
sudo /etc/init.d/network-manager restart
```

Otherwise the nm-vpn won't access the keyring for some reason.

---

