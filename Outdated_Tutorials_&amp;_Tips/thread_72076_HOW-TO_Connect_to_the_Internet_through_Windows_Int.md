---
title: "HOW-TO: Connect to the Internet through Windows Internet Sharing!"
date: 2005-10-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Havoc on 2005-10-05
I DID IT!!! I Managed to connect to the net through my DSL-connected Windows machine! So, in this day of celebration, I thought I'd share the fun around! I'll try to make this easy enough for all to understand. :p 

So, here goes:

*1. Connect both Server (The Internet connected Windows PC) and Client (Your lonely Ubuntu PC) using a standard Crossover Cable, connected to standard LAN adaptors.If you know that your PCs are able to "talk" to each other, you're done.*

2.Now, for the configuration part of the job.My configuration is something like this:

**INTERNET------DSL MODEM======WINDOWS PC==========UBUNTU PC**

Where "------" is a Phone Line and "=====" is a LAN cable.

Depending on your configuration, the solution might be a LITTLE different.But, as a note, I don' think that the USB or LAN does any difference when connecting Modem and PC.

So, what I did is this:

*a) I went to my Windows PC and assigned a IP (Plus other values) for my NEW LAN connection (The one between Win and Ubuntu, for me It's Local Area Connection 3)*

You can put something like this

[B]IP: 192.168.0.1
Subnet Mask: 255.255.255.0 (Auto assigned)
Gateway: (Put here the same (IP Address) value as in your Internet Connection)

Primary DNS: (Here, I put the same (Primary and Alternate DNS) values as in the LAN adaptor connected to the MODEM)
Alternate DNS: (Same as Above)[/B]

*b) I went to my Internet Connection and Enabled Internet Sharing for the LAN Adaptor connecting the two PCs (Again, for clarification, for me it's Local Area Connection 3).*

[I]c) That's all for the Windows PC, now for the Ubuntu PC.First, add the Network Monitor Panel Applet (Or KDE equivalent).Next, go configure the Network Connections through **"System---->Administration---->Networking"**.Right Click, "Properties", and check the "This device is configured" thingie, then choose **DHCP** from the drop-down list.
[/I]
THAT'S IT! You might need to restart your computers, but, that worked for me! Please note that, whilst the "Network Monitor" applet shows me that I'm sending packages whenever it try to "ping" the Windows PC IP address, the terminal tells me that I have 100% package loss, so don't believe the terminal THAT much.If I've done anything wrong, or you just wanna let off some steam, send feedback! :cool: 

Thanks, everyone, for this great community you've created.I'm just happy I can give back to the community! ;-)

---

### Post by jimcooncat on 2005-10-05
Excellent job! Some points I'd like to add:

A lot of people would say to do this the other way around -- have your Linux box connect to the internet, and share that connection with your Windows box via a second network adapter. You then have a lot more options on firewalling, NAT, and proxies; or at least these options are more easily available to you than on the Windows platform. But I know some ISP's aren't helpful in setting up Linux boxes on their network and firewall software can be intimidating, so your howto does have merit.

I would suggest you look into ensuring your Windows box doesn't have open ports to exploit. The easy way (security minded folks correct me, please) is to use the NAT tools in your DSL modem to ensure only the incoming ports needed are forwarded. Usually that means no ports, unless you are intentionally exposing some service, like SSH. Even so, use a non-standard port for a little privacy.

If your DSL modem isn't configurable, or you don't trust your ISP to be security minded, get yourself a little NAT router. A four-port one will set you back $50 - $70 USD, block the ports you don't want exposed, share the connection, and make it easy to do other network things like shared printers and folders.

---

### Post by Havoc on 2005-10-05
Thanks for the advice! I only posted this because there is no other around, from what I know of, and, I once needed (baaaadly) a HOWTO like this.Plus a couple of others.

Anyways, I'm good at computers, but when it comes to networking, I'm out.I only managed to make this work because I've been trying for the last 2 weeks! So, I did not understand A THING of what you said. :p
Although,I  bet that the only port fowarded is 6881 (Azureus).All others are probably closed.Do things coming into my Ubuntu PC pass through Windows's own firewall? Or should I set up firestarter? I thought that, by default, Ubuntu has all ports closed.Or was I lied to? :eek: 

If ANYONE has any request e.g. "CLEAR THE HOWTO UP, YOU @^%!^#" or something, tell me!

Thank YOU! :cool:

---

### Post by Lord Brar on 2005-10-05
Right what I was looking for! Thank you very much. :)

---

### Post by wicke on 2007-12-19
Thanks! This is also a way to get the way to the Internet working when you're using USB HomePNA adapter that isn't compatible with Ubuntu. Unfortunately my firewall blocked the connection until I turned it off for a way to the Internet. I hope nobody is coming in. Anyway HomePNA is going to leave us next year so this connection will not be used for a long time.

---

### Post by iris-n on 2007-12-22
I thank you for you guide, it got me online.
The only problem was, when I set the gateway on the host computer the way you said, the connection with the ISP died; left blank and all was happiness =)

---

### Post by betete on 2008-04-07
Hello, I need your help please.
I have more or less the same connction scheme, the only diference is that the Ubuntu machine is actually a Virtual machine running in the Windows XP machine. I'm using VMware. I set Vmnet0 to bridge a network adapter, and I set the IP address manually in Ubuntu. The host (Win XP) and the guest (Ubuntu) see each other, I can ping and I can even access share folders. But I cannot have access to internet.
I now Windows sharing connection works because I have a separate machine running Debian and it has access to internet through the Windows machine. So the diagram would be somthing like this:



internet----- Win XP ===== Debian machine
                        ||
                         ======= Ubuntu virtual machine

The virtual machine can also see the Debian machine. So everything looks fine, but I have no access to internet from Ubuntu. Any idea?

---

### Post by ironwolfe on 2008-04-07
Why not just use a router?  They are like $35...

This also adds security of a NAT router firewall instead of being directly connected to the internet.

I wonder if there are any other reasons not to do this?  Is it possible that a trojan could sniff the linux internet traffic going though a heavily infected windows PC?

---

### Post by betete on 2008-04-07
First of all, a router is not the solution since I'm talking about a virtual machine which connects to the host through a virtual hub. Second, there is no trojan because as I said, the host is sharing the internet connection to a Debian machine and works just fine.

---

### Post by Turev on 2009-12-12
Thanks Havoc for the "how-to". It is much appreciated! I was looking for the exact same thing that you did- asking myself would it even be possible. So I desperately typed in some keywords and reached your how to. I just want to mention one other thing to those people who might wonder "why would you connect to internet over a windows machine?" - For my case the answer is simple, many times I have trouble connecting internet via my USB modem- hence it is worth giving a try to connect to my laptop (which runs WinXP and USB modem has Win drivers obviously) to connect to internet.

---

