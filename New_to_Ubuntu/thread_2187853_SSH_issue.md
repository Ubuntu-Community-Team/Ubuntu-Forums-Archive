---
title: "SSH issue"
date: 2013-11-14
forum: New to Ubuntu
---

### Post by gerrypdonnelly on 2013-11-14
I am new to Ubuntu and Linux so this is probably a silly question but it has my head done in...
I have set up ssh on an old pc on my network and can use putty on a windows computer to remotely control it.  
I started to get a bit adventurous and tried to connect via the WAN IP address.
I get asked for my login and then my password.  
When I input my password I get Access denied ?????
I have searched the web and I have changed the config file to 
 **PasswordAuthentication yes** 
[B]AllowTcpForwarding no
[B]X11Forwarding no
**AllowUsers gerry **[/B][/B]is also appended to the end of the file.

I have the router set up with firewall disabled and have the virtual server set up with the IP of teh machine and using port 22...  
Getting a bit frustrated at this point.  Any pointers appreciated.

Gerry

---

### Post by Lars Noodén on 2013-11-14
Which computer is the WAN ip address pointing to?  Usually the router has to be explicitly set to forward a port to a particular computer.  It's possible that your computer is on a different LAN address than you think it is, so double check the settings there in the router/switch.

---

### Post by steeldriver on 2013-11-14
As well as the port forwarding that Lars mentioned, you usually can't use the WAN ip from within the same LAN (if that's what you're trying to do - your post is not clear) since most consumer grade routers don't support that (NAT loopback)

---

### Post by gerrypdonnelly on 2013-11-14
the server is 192.168.1.34 and I have this forwarded through the router via port 22.  The IP address I am using is the public IP of the router, which should if I am correct route all requests for port 22 to the server.
Steeldriver may have something as the windows 7 PC I am using the Putty on is also behind the router. 
What I tried to do to clarify is:-
use local IP address putty works fine.
use public IP of router I get asked for user name but password is not accepted.
I will try again from a different network this evening when I get home and update.  Cheers

---

### Post by Lars Noodén on 2013-11-14
(BTW welcome to the forums!)

One trick you might use to identify which server you are really talking to would be to use the server's finger prints.  That's done in two steps: collecting the key with ssh-keyscan and then reading the finger print with ssh-keygen.

```

ssh-keyscan xx.yy.zz.aa > /tmp/key
ssh-keygen -lf /tmp/key

```

Compare the fingerprint given over the WAN address to the various machines you have on your LAN using the LAN addresses.  Hopefully there is a match.

---

### Post by gerrypdonnelly on 2013-11-14
No Joy.  
When I go off the LAN and I ping the IP I just get request timed out.  :(
I followed [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by alphacrucis2 on 2013-11-14
The port forward will not deal with pings. The port forward will specify tcp port 22 (or a specified alternative **tcp** port). Ping uses **icmp** protocol which is quite different.

---

### Post by gerrypdonnelly on 2013-11-14
Do I have to set up Putty in a different manner?  Completely lost now.

---

### Post by alphacrucis2 on 2013-11-14
Did you try Lars suggestion?

---

### Post by gerrypdonnelly on 2013-11-14
Yes I tried Lars suggestion.  When I try to connect to the server through my router I just get network error connection timed out.
I'm not sure it not my ISP.
When my windows machine is on the same LAN it works fine but when I try remote it does not work.

Lets take this back to first principles.
I have SSH installed and the ssh config file set up.
I logged into the router and turned on the virtual server to pass port 22 to the server IP address.
I go on line and use whats my IP to get the router IP address.

I come out of the LAN and onto another network and try and contact the server.
THis is where I am stuck.

---

### Post by gerrypdonnelly on 2013-11-14
I think I have it sorted.  
My ISP is 3g router which uses a dynamic IP.  
There must be something stopping me from connecting through ssh (even if it is during the one IP activation).
I will contact the ISP and if it is the case I'll update.

---

### Post by Lars Noodén on 2013-11-15
You can see if your ISP is blocking any of your ports using a service like Canyouseeme:

[http://canyouseeme.org/](http://canyouseeme.org/)
 
There are others, like that, but they will tell you if your port is even open.  

In regards to the dynamic IP numbers, are you sure that you have today's IP number correct?

---

### Post by gerrypdonnelly on 2013-11-15
Hi Lars,

Yes the IP address changes every time I reboot the router.  I hadn't rebooted it for ages so the IP was I thought fixed.  I did a soft reboot last night and all sorts of confusion started lol. :)
I will check that site today and call the ISP.  It's a 3G wireless router due to pretty poor broadband in my area.
I thought as long as I don't reboot the router the IP address should remain the same for some time even if not static.  I was going to try this window to see if networking would work before going down a static IP or DynDNS but I'm nearly sure there is something ISP that is stopping me.  I'm going to call them in a while and will update my findings in case anyone has the same problem.

---

### Post by Lars Noodén on 2013-11-15
One temporary work-around is to use a [dynamic DNS service](https://help.ubuntu.com/community/DynamicDNS).  Most home routers support the protocols so it is usually just a matter of entering login information in the right place in the router.

---

### Post by gerrypdonnelly on 2013-11-17
I tried canyouseeme.org and a few orther port checking tools and I am told that the port is not open. I know I have the router set up correctly. and the router does not have dynamic DNS.  WHen I contact the ISP they tell me all ports are enabled on theor devices and that my settings must be wrong.  The router is a Huwwei B683 and the ISP is three.ie.
LOoking on other sites thsi is a common problem people are having with this ISP.  What I have learned is that if you are a Three Ireland customer and have a router with the national broadband scheme you are in for a world of pain if you wnt to do any more than surf teh internet and receive emails.  :(

---

