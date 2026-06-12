---
title: "VPN Connect... need help!"
date: 2008-09-20
forum: Philippine Team
---

### Post by VirtualEdgar on 2008-09-20
Hi fellow Pinoys, n00b here! I need help on connecting to the VPN at work (Microsoft Server using GRE) using my laptop which runs Hardy. Yes, I have done my homework on searching for all possible solutions by searching sites especially this one, but no luck so far!

Here's my connection setup... at home I am connected to the internet via a wireless router meaning I am using wlan0. I already did allowed most ports that is used to connect to a VPN (IPSec, PPTP, LT2*, etc). I can ping my IP at work (using Ubuntu) and I can connect flawlessly to it using a Windows box. I've tried using Network Manager and Kvpnc tried all possible ways to connect, yet all my efforts are in vain. Kvpnc always say "Remote modem was hung up. Connection was terminated." The hell what that means. And yes, I have placed the correct IP address and the login name and password.

Sana may makatulong sa akin!

Maraming salamat po! :KS

---

### Post by loell on 2008-09-20
have you tried using

[network-manager-pptp]("apt:network-manager-pptp") for the network manager vpn instead of the separate kvpnc?

---

### Post by VirtualEdgar on 2008-09-20
> **loell said:**
> have you tried using

[network-manager-pptp]("apt:network-manager-pptp") for the network manager vpn instead of the separate kvpnc?

Yes sir, thanks for reminding me! Yan yung unang ginamit ko. :) Always getting a "Could not start the VPN connection 'MyVPN' due to a connection error. VPN Connection failed." message.

You think its a tunneling issue? The IP assigned to me by my router is always 192.168.1.2 kung makakatulong ito.

Can somebody show me how to do this properly? Thanks!

---

### Post by VirtualEdgar on 2008-09-20
By the way, if logs would help... here it is!

Plugin nm-pppd-plugin.so loaded.
nm-pppd-plugin: plugin initialized.
pppd 2.4.4 started by root, uid 0
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
nm-pppd-plugin: CHAP check hook.
Terminating on signal 15
Child process /usr/sbin/pptp xxx.xxx.xxx.xxx --nolaunchpppd (pid 8508) terminated with signal 15
Modem hangup
Connection terminated.
Exit.


xxx.xxx.xxx.xxx = my work vpn server address

---

### Post by loell on 2008-09-20
i don't think if this has something to do with routing,

could it be that your vpn server uses a different authentication scheme?

or a different compression scheme perhaps?

---

### Post by loell on 2008-09-20
can you also try [pptp-linux]("apt:pptp-linux") ?  ;)

[for reference ]("http://pptpclient.sourceforge.net/howto-debian.phtml#install")

---

### Post by VirtualEdgar on 2008-09-20
> **loell said:**
> i don't think if this has something to do with routing,

could it be that your vpn server uses a different authentication scheme?

or a different compression scheme perhaps?

Nothing special in the proxy server sir. I can connect to it on a Windows computer with no special settings whatsoever.

What's odd is, network manager is using ppp0 and I don't have that when I type ifconfig or iwconfig since I'm using wlan0 to connect to my wireless network at home. Could NM be using the wrong network interface? Is NM limited only to that interface? I haven't tried connecting thru pppoe though (for ppp0 to appear) since its pointless to wire my laptop when I have a wireless router. :)

Many thanks for the reply!

---

### Post by VirtualEdgar on 2008-09-20
> **loell said:**
> can you also try [pptp-linux]("apt:pptp-linux") ?  ;)

[for reference ]("http://pptpclient.sourceforge.net/howto-debian.phtml#install")

Will do! Thanks again!

---

### Post by loell on 2008-09-20
> **VirtualEdgar said:**
> 
What's odd is, network manager is using ppp0 and I don't have that when I type ifconfig or iwconfig since I'm using wlan0 to connect to my wireless network at home.

ah.. i see, after some further digging this might be related to routing after all.

even in pptp this also needs to be added: [http://pptpclient.sourceforge.net/routing.phtml#automatic-setup]("http://pptpclient.sourceforge.net/routing.phtml#automatic-setup")

so going back to NM applet, base on this thread [http://ph.ubuntuforums.com/showthread.php?t=823169]("http://ph.ubuntuforums.com/showthread.php?t=823169")


you should add a route and enable nat.

```
sudo route add -net 192.168.1.0 netmask 255.255.255.0 dev ppp0
```

and 

```
sudo iptables -A POSTROUTING --table nat -d 192.168.1.0/24 -o ppp0 -j MASQUERADE
```

---

### Post by VirtualEdgar on 2008-09-20
> **loell said:**
> ah.. i see, after some further digging this might be related to routing after all.

even in pptp this also needs to be added: [http://pptpclient.sourceforge.net/routing.phtml#automatic-setup]("http://pptpclient.sourceforge.net/routing.phtml#automatic-setup")

so going back to NM applet, base on this thread [http://ph.ubuntuforums.com/showthread.php?t=823169]("http://ph.ubuntuforums.com/showthread.php?t=823169")


you should add a route and enable nat.

```
sudo route add -net 192.168.1.0 netmask 255.255.255.0 dev ppp0
```

and 

```
sudo iptables -A POSTROUTING --table nat -d 192.168.1.0/24 -o ppp0 -j MASQUERADE
```

No idea about the first one (scripting) sir. Can someone explain this to me like I'm a 4-year old? :D

As for the route command I keep getting** SIOCADDRT: No such device**. :( I tried searching for solutions, pero wala kapareho ng scenario ko.

---

### Post by VirtualEdgar on 2008-09-20
Check out my route table

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

---

### Post by loell on 2008-09-20
> **VirtualEdgar said:**
> 
As for the route command I keep getting** SIOCADDRT: No such device**. :( I tried searching for solutions, pero wala kapareho ng scenario ko.

can you give more details? what command did you invoke and what are the specific error(s)?

---

### Post by VirtualEdgar on 2008-09-21
> **loell said:**
> can you give more details? what command did you invoke and what are the specific error(s)?

Here it is!

```
edgar@edgar-laptop:~$ sudo route add -net 192.168.1.0 netmask 255.255.255.0 dev ppp0
[sudo] password for edgar: 
SIOCADDRT: No such device
edgar@edgar-laptop:~$ 

```

---

### Post by VirtualEdgar on 2008-10-03
Upgraded to 8.10 Alpha 6 thinking Intrepid can resolve my issue but still NO LUCK!

Using the built-in Network Manager and installed network-manager-pptp and still can't connect to my work's VPN. :(

Anyone?

---

### Post by Recursion_1209 on 2008-10-03
SIOCADDRT: No such device error means ppp0 connection was disconnected already when you executed the route command.

It might me a wrong password or you didn't specify a domain name in your login. Also, please make sure that REFUSE CHAP and REFUSE EAP is checkd in VPN your configuraion.

I connect VPN using network manager and command line (pon command) and it works ok as long as you have the correct configuration.  

This howto -> [http://pptpclient.sourceforge.net/howto-ubuntu.phtml#configure_by_hand](http://pptpclient.sourceforge.net/howto-ubuntu.phtml#configure_by_hand) helped me a lot in setting up VPN manually if you are using static IP. Helped me understand a lot also.

---

### Post by VirtualEdgar on 2008-10-04
Thanks for the reply sir Recursion_1209. Actually I am using wlan0 for my connection as mentioned in my previous post and I don't know why it uses ppp0. :(

As for the link, I was trying to install pptpconfig for sometime now but unabled to do so. I have learned that the new url for this is [http://quozl.linux.org.au](http://quozl.linux.org.au) which I added to my sources.list. But still, I was unsuccessful to install the app since it looks for repositories which is not downloaded automatically. If somebody could just guide me or give me the links of these files so I can install them manually. I would really like to try this option.

Thanks!

---

### Post by Recursion_1209 on 2008-10-04
From my understanding (I am same as you, just a newbie in Linux), linux will create a ppp0 device when you connect via vpn. For me, I use two VPN connection at the same time (one in Manila and Sydney) I have a ppp0 and ppp1 device if I run ifconfig command.

I was also looking for pptconfig before but cannot find one for Ubuntu. So, I opted for the manual configuration which is working flawlessly up to now. VPN was a problem before because of Static IP address here in the office.

Give the manual configuration a try you will be surprised how easy the setup is.

---

### Post by VirtualEdgar on 2008-10-04
> **Recursion_1209 said:**
> From my understanding (I am same as you, just a newbie in Linux), linux will create a ppp0 device when you connect via vpn. For me, I use two VPN connection at the same time (one in Manila and Sydney) I have a ppp0 and ppp1 device if I run ifconfig command.

I was also looking for pptconfig before but cannot find one for Ubuntu. So, I opted for the manual configuration which is working flawlessly up to now. VPN was a problem before because of Static IP address here in the office.

Give the manual configuration a try you will be surprised how easy the setup is.

Will try it again. Salamat!

---

### Post by VirtualEdgar on 2008-10-11
I was able to solve the problem myself. Still used NM PPTP over Intrepid Ibex. I just enabled MPPE and added a route.

Many thanks to those who replied.

---

### Post by Nausser on 2008-10-15
What route did you add? I tried Intrepid for a week and could not resolve this same issue of connecting to my work's windows vpn server.

I have since done a fresh install back to hardy where I have never had a single issue initiating the same vpn connection.

---

### Post by VirtualEdgar on 2008-10-18
> **Nausser said:**
> What route did you add? I tried Intrepid for a week and could not resolve this same issue of connecting to my work's windows vpn server.

I have since done a fresh install back to hardy where I have never had a single issue initiating the same vpn connection.

sudo route add -net  192.168.0.0 netmask 255.255.255.0 dev wlan0

:KS

---

