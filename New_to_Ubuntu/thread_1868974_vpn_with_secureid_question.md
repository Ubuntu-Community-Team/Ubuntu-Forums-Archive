---
title: "vpn with secureid question"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by illgetit on 2011-10-25
Guys and Gals,
Long time fan of Ubuntu with a problem here.
I'm running Ubuntu 10.04.1 LTS and I need to connect to my vpn for work. 
The only instructions they give are for windows.
And I can't seem to find instructions for people who connect with an RSA Secureid. 

When I try to set up the vpn, it tells me the vpn service failed to start. Here is a look at syslog:
Oct 25 02:00:41 Romulus NetworkManager: <info>  VPN plugin state changed: 1
Oct 25 02:00:41 Romulus NetworkManager: <info>  VPN plugin state changed: 3
Oct 25 02:00:41 Romulus NetworkManager: <info>  VPN connection 'vpn' (Connect) reply received.
Oct 25 02:00:41 Romulus NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'vpn' failed to connect: 'invalid gateway 'gateway''.
Oct 25 02:00:41 Romulus NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Oct 25 02:00:54 Romulus NetworkManager: <debug> [1319526054.002173] ensure_killed(): waiting for vpn service pid 5413 to exit
Oct 25 02:00:54 Romulus NetworkManager: <debug> [1319526054.002329] ensure_killed(): vpn service pid 5413 cleaned up

I'm trying to connect over wlan0 if it matters.

I tried installing the CheckPoint. software in Wine, but it just craps out.
There **has** to be a way to do this in Ubuntu. Can anyone point me in the right direction?

Thanks so much in advance for your help

---

### Post by MagicThinker on 2011-10-25
G'day,

I use vpn and openvpn all the time for business.  I would AVOID using wine to make a windows vpn program to work under linux.   Linux has really good vpn (pptp microsoft talk)  first thing.  

Install or ensure that,  "network-manager-pptp", network-manger-pptp-gnome', 'pptp-linux' and vpnc (used for cisco routers) this one is IMPORTANT as not all routers like to play the same way.

once they have been installed, restart he machine.

I will list all the steps to get working as I found it invaluable when I set mine up as well:

STEP 1> Right click on "PANEL" add to panel "Indicator Applet" if not already chances are you already have this.

STEP 2> Press "Alt + F2 keys to get run dialogue up type in "nm-connection-editor" to edit network connections.

STEP 3> Click onto VPN tab

STEP 4> Click "Add"

Step 5> A dialogue saying "Choose a VPN Connection type will be displayed, in the drop down choose  "POINT TO POINT TUNNELLING PROTOCOL (PPTP)  Industry talk for VPN.
Don't confuse this with openvpn.

Step 6> Choose the Create Button.

Step 7> Enter in the Gateway address that was given to you from Work or supplier of VPN service.

Step 8> Under Optional:  
Enter in supplied 
User Name
Password

Step 9> Make sure that the "Connect automatically" check box is enabled.

Step 10> down the bottom of this dialogue box choose "Advanced Button"

Step 11>  Allow the following authentication methods: make sure that 
"MSCHAP" and "MSHAPv2" are both enabled and no other.

Step 12> Security and Compression Section:  Check use Point-to-point encryption (MPPE) Security: All Available (Default)

Make sure that the following check boxes are also enabled:
"Allow statefu' encryption"
"Allow BSD data compression"
"Allow Deflate data compression"
"Use TCP header compression"

ENSURING THAT THE LAST CHECK BOX Echo (Send PPTP echo packets is DISABLED 

Step 13> Hit ok and Save this makeing sure that the Connection name is something meaning full.

Step 14> Close the Network connection dialogue and REBOOT not logoff.

This should be the only time that you should ever need to reboot whilst initally setting up the vpn or openvpn.

When system is back go into the network manager and choose "VPN Connection" and choose the newly created connection.  It will normally take less than a minute to connect. (Mine about 4 seconds) else it make time out.

..................

Took me awhile to figure this one as well to connect for business.  Most things are done in the Microsoft way....

Remember after installing the software and configuring to reboot else it will disconnect or not connect.  


Cheers.

---

### Post by illgetit on 2011-10-25
Thank you so much for your suggestions. I will definitely try this as soon as I get home.

---

### Post by illgetit on 2011-10-25
Hi MagicThinker,
I followed the steps you outlined (with the exception of saving the password as my password changes when my secureid token updates every sixty seconds). And I'm still getting the same error :
[B]VPN Connection Failed
The VPN connection "work" failed because the VPN service failed to start.

Any thoughts?
Thanks again for your help on this[/B]

---

### Post by dolphin194 on 2011-10-25
Hello, illgetit. I have googled the error message you have gotten and came around to this: [http://www.cognitivecombine.com/2009/11/ubuntu-9-10-network-manager-openvpn-vpn-service-failed-to-start/](http://www.cognitivecombine.com/2009/11/ubuntu-9-10-network-manager-openvpn-vpn-service-failed-to-start/)

> [FONT=Verdana]_Solution 1:_[/FONT]
 [FONT=Verdana]Install the package network-manager-pptp[/FONT]
 [FONT=Verdana]The command would be: sudo apt-get install network-manager-pptp[/FONT]
 [FONT=Verdana]Then it should work as has been reported in the comments section.[/FONT]
 [FONT=Verdana]_Solution 2:_[/FONT]
 [FONT=Verdana]Edit your /etc/network/interfaces file.[/FONT]
 [COLOR=#333333][FONT=Lucida Grande][COLOR=#000000][FONT=Georgia]Change it from this:[/FONT][/COLOR][/FONT][/COLOR]
 [QUOTE]auto lo
iface lo inet loopback
 [COLOR=#333333][FONT=Lucida Grande][COLOR=#000000][FONT=Georgia]To this:[/FONT][/COLOR][/FONT][/COLOR]
 ```
auto eth0
iface eth0 inet dhcp
```
[/QUOTE]

Try those and see if it helps you with the problem.

---

### Post by illgetit on 2011-10-25
Hi Dolphin194,
I had actually tried this earlier, but I still get the same error.
I was wondering, would it matter if I was connected over wlan0 as opposed to eth0?
That is the interface that shows connected when I do an ifconfig -a.

---

### Post by illgetit on 2011-10-27
A friend at work thought this might be a permissions issue. Is it possible the vpn service is owned by root and won't start for any user other than root?

Any and all help is greatly appreciated.

---

### Post by Sergio.G on 2011-10-29
Hi, 

Actually there is a linux compatible vpn client from checkpoint, check this links, they might help

This is a tutorial I found some time ago:
  [http://www.fronde.com/blog/2010/12/how-to-install-checkpoint-vpn-client-software-on-ubuntu/]("http://www.fronde.com/blog/2010/12/how-to-install-checkpoint-vpn-client-software-on-ubuntu/")

This is a thread from checkpoint's web site:
  [https://forums.checkpoint.com/forums/thread.jspa?threadID=13493&tstart=0]("https://forums.checkpoint.com/forums/thread.jspa?threadID=13493&tstart=0")

vpn client files:
  [https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doShowproductpage&productTab=downloads&product=175&version=VPN%20Clients%20for%20Linux]("https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doShowproductpage&productTab=downloads&product=175&version=VPN%20Clients%20for%20Linux")

I think your success trying this procedures will depend also in the VPN configuration at your workplace. 

You might also like to check this project:
StrongSwan is an IPsec implementation for Linux 2.6 kernel and up.
  [http://en.wikipedia.org/wiki/StrongSwan]("http://en.wikipedia.org/wiki/StrongSwan")

Sadly I was not able to configure this because apparently at my workplace some features needed to be enabled and there is a certain fee involved in using the linux client (this is what IT/Network department told me) It might be wrong or they maybe lied to me :)

I'm sorry I cannot help you any further, my knowledge is not so vast in this area, but I hope the links written above lead you in the right direction.

Cheers!

---

### Post by illgetit on 2011-11-03
Hi Sergio,
Thanks for the tips, but I'm still having the same issues.
Maybe it's just one of those things that can't be done. :(

---

