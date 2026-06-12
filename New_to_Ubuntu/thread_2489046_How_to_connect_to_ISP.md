---
title: "How to connect to ISP?"
date: 2023-07-17
forum: New to Ubuntu
---

### Post by crowcrowcrow on 2023-07-17
I cannot connect to the internet. In Windows I use: Set up a new connection or network/ Set up a broadband or dial-up connection to the internet/ Set up a new connection anyway/ create a new connection/How do you want to connect? – Broadband (PPPoE)/ User name (name your isp gave you) and password (password your ISP gave you). I have a wired lan connection to a switch then to a modem. No router. I have looked at previous posts and one recommendation was to use the network manager but I cannot find it. Any tips please?

---

### Post by yancek on 2023-07-17
Which release of Ubuntu are you using?  The site at the link below explains installing and starting Network Manager on Ubuntu.

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

---

### Post by crowcrowcrow on 2023-07-17
Thank you very much for your reply. I am using Ubuntu 22.04. I followed the instructions in the link you provided and found the network manager. However, despite reading all of that web page, I cannot work out how to connect to my ISP. The tabs in network manager are general, Ethernet, 802.1X security, DCB, proxy, IPv4 settings and IPv6 settings. The only one of those which has fields for username and password is 802.1X security. I thought it was probably not a security issue but I tried entering my ISP details in those fields anyway and then saved but was unable to connect to the internet. I don’t know what to try next.

---

### Post by The Cog on 2023-07-17
A search for "ubuntu configure ppoe" turned this up as top result. It's quite old but may well still work. I think that's probably the way to go:
[https://www.linuxbabe.com/ubuntu/create-pppoe-connection-ubuntu-16-04](https://www.linuxbabe.com/ubuntu/create-pppoe-connection-ubuntu-16-04)
Not that I have a ppoe connection to try it out on.

---

### Post by grahammechanical on 2023-07-17
As I understand things we do not connect Ubuntu to an Internet Service Provider (ISP) but to a modem/router/hub that is connected to the ISP.

The modem will have its own settings utility that should contain the information necessary for it to connect to the ISP. There should also be indicators on the modem/router including one that lights up when the modem has made a connection to the ISP. Unless of course, you are using old equipment such as a dial-up modem. Then you have to use the terminal to use commands such as pppconf and pon/poff.

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

[https://manpages.ubuntu.com/manpages/xenial/man1/gnome-ppp.1.html](https://manpages.ubuntu.com/manpages/xenial/man1/gnome-ppp.1.html)

I am not sure if gnome-ppp and wvdial or pppconf are still installed as part of modern versions of Ubuntu or if they are available for installing.

So, assuming this is a modern setup using a broadband connection to the telephone system, then check the modem's manufacturer's instructions for how to access the modem's setup utility. It will have a username and password. And enter into that utility the information provided by the ISP and your ISP username and password.

Open System Settings. With an ethernet connection open the Network tab. It should reveal the connection to the switch/modem combination (if they are both switched on). Now you have to enter the security details and the type of connection. There may be information such as the MAC address of the modem. There is usually useful information on stickers stuck to the underside of modem/routers.

Regards

---

### Post by MAFoElffen on 2023-07-17
There are a lot of variables and information of the what-may-be's that is missing from here to make a sound recommedation on a solution. What would really help with this is to boot from Windows, and tell us how it is connecting...We need not to have to guess on what that information may be.

From a Windows command prompt, do
```

ipconfig /all

```
Please post the output of that, pasted within Code Tags.

---

### Post by TheFu on 2023-07-17
Most people don't directly connect a computer to their ISP's modem.  We connect to a router and let it handle the modem connection, login (if any) to the ISP, and have it provide basic security with NAT and a firewall that is always on.

Connecting directly to the internet without a router providing protection really isn't recommended for any computer running any OS for the last 20+ yrs.  Would you drive your car to a bad part of town, leaving the doors unlocked and windows open, then leaving there overnight?  That's what using any computer directly on the internet is like if you are new and don't have a router.

While Linux can be setup as a router, that's not a trivial thing and someone new to Linux shouldn't attempt it.  Heck, I'm not sure I could do it with my 30 yrs of Linux experience and be totally certain of the security.  I'd get a linux-based distro designed to be used **only** as a router and use that instead.  

However, what I really do is have a low-powered AMD64 computer with 3 NIC ports setup running OPNSense (BSD-based) [https://opnsense.org/](https://opnsense.org/) as my WAN router.  This is a distro specifically designed to be used as a router. Red port is for connecting to the ISP. Green and Blue ports are for my different internal LANs. I have 2 dumb $15 switches, one for each subnet here, that computers and other non-wifi devices connect into.  Wifi devices connect to the ISP's wifi radio and get treated like they on the internet (completely untrusted).  Wifi devices must use a VPN to gain access to anything in my LANs.

---

### Post by MAFoElffen on 2023-07-17
The OP connected to the Internet by just using the "Create Connection" dialog in Windows, with nothing special to configure... That tells me (in high-likelyhood) that they are connecting to the ISP's modem to get to their ISP.

So that tells me that they might be having a DHCP problem, which there is a current issue and a current open bug report filed on this, with an astronomical number of users affected from that Bug. I don't know why, and it is currently not resolved.

The test for that is to check the information returned by 'dhclient'.

The work-around for those affected, is to create a static IP address with the nameserver specified.

Just saying.

---

### Post by TheFu on 2023-07-17
> The more they overthink the plumbing, the easier it is to stop up the drain. 

- Scotty

---

### Post by mIk3_08 on 2023-07-18
> **crowcrowcrow said:**
> Set up a new connection or network/ Set up a  broadband or dial-up connection to the internet/ Set up a new  connection anyway/ create a new connection/How do you want to connect? –  Broadband (PPPoE)/ User name (name your isp gave you) and password  (password your ISP gave you). 
Actually, This is on the  router now. Not on the desktop. In my case, I usually configure my  internet in my local router/modem router. Then the desktop will do the  DCHP only. 

> **grahammechanical said:**
> As I understand things we do not  connect Ubuntu to an Internet Service Provider (ISP) but to a  modem/router/hub that is connected to the ISP.
I agree with grahammechanical this is the usual setting I have. Regards and cheers

---

### Post by crowcrowcrow on 2023-07-18
Thanks for all the replies. I followed the instructions on [https://www.linuxbabe.com/ubuntu/create-pppoe-connection-ubuntu-16-04](https://www.linuxbabe.com/ubuntu/create-pppoe-connection-ubuntu-16-04) and was able to create a connection and enter my username and password. However, on that site it says: Finally, select DSL connection from the drop-down menu to establish the connection. I couldn’t find that and so was unable to connect. I then tried commands in terminal like pppoeconf but no joy. I have taken your advice and ordered a router.

---

### Post by TheFu on 2023-07-18
> **crowcrowcrow said:**
> Thanks for all the replies. I followed the instructions on [https://www.linuxbabe.com/ubuntu/create-pppoe-connection-ubuntu-16-04](https://www.linuxbabe.com/ubuntu/create-pppoe-connection-ubuntu-16-04) and was able to create a connection and enter my username and password. However, on that site it says: Finally, select DSL connection from the drop-down menu to establish the connection. I couldn’t find that and so was unable to connect. I then tried commands in terminal like pppoeconf but no joy. I have taken your advice and ordered a router.

So, you are running 22.04, not 16.04, so things are a little different.
We don't know which DE you are using, so we don't know which network subsystem is being used. Also, we don't know if it was a fresh install or an upgrade from an install in 2004 over the last 19 yrs.  The way networks have been connected to over all this time has drastically changed.

So, assuming you are using the Gnome4 "flavor" of Ubuntu Desktop (there are many other flavors), here's a link to the Desktop Guide that google found. [https://help.ubuntu.com/22.04/ubuntu-help/net-wired.html.en](https://help.ubuntu.com/22.04/ubuntu-help/net-wired.html.en)

** MAFoElffen asked you to run a command in Windows and post the output. You haven't done this. It would be very helpful if you want a solution.**  Or do you prefer we keep guessing?

---

### Post by MAFoElffen on 2023-07-19
> **MAFoElffen said:**
> 
From a Windows command prompt, do
```

ipconfig /all

```
Please post the output of that, pasted within Code Tags.

Yes, please. You said that Windows is connecting to your ISP fine, We need to see those settings it is using for that. That tells us what is there and gives us a starting point.

Otherwise we are also just guessing.

---

