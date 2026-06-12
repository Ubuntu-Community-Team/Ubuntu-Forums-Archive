---
title: "Connect two local Ubuntu computers"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by andriy.kostyuk on 2008-06-15
I have two local computers in my home. Both are running Ubuntu 8.04.
Both are connected to the Internet via a wireless router.
The connection to Internet works OK.

How can I make these two computers to see each other, so that I can login from one computer two another, make scp, play Freeciv with the server running on one of the two computers, etc.?

I could not find the instruction. If there is one, Please give the link.

Thanks in advance.

---

### Post by hyper_ch on 2008-06-15
there are multiple ways:

(1) install openssh-server and then use a program that can use sftp/scp (e.g. konqueror)

(2) install sshfs and mount a remote folder into the other computer

(3) use nfs

(4) use samba

those will enable sharing files/documents among each other

but if you want to be able to connect to each other in freeciv or so then I'd say give both computers a static ip one.

---

### Post by andriy.kostyuk on 2008-06-15
Thank you for the prompt answer.

> **hyper_ch said:**
> 
but if you want to be able to connect to each other in freeciv or so then I'd say give both computers a static ip one.


Where can I take this IPs?
How to input them?
Will not it influence the internrt connection via the router?

---

### Post by Xerp on 2008-06-15
Click the Network Manager icon to see the current IP assignment for the computer. You can also type "ifconfig -a" from any command prompt. You can set this information as static (rather than roaming) to ensure the computer's network information doesn't change.

---

### Post by andriy.kostyuk on 2008-06-15
Thank you
> **Xerp said:**
> Click the Network Manager icon to see the current IP assignment for the computer. You can also type "ifconfig -a" from any command prompt. You can set this information as static (rather than roaming) to ensure the computer's network information doesn't change.
But I do not know how to chose the IP address. It cannot be arbitrary, I suppose. (?)
Sorry for a naive questions. But it is completely new for me.

---

### Post by Xerp on 2008-06-15
When you see the currently assigned network information you can:

* write it down
* press "print screen" and then save it
* Start "gedit", copy the information and save it

You can then use this as the static information.

---

### Post by The Cog on 2008-06-15
First, find out what the current ip addresses are - use the command **ifconfig** and look for a line like:
> inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
The first entry (192.168.1.2 or whatever) is your current IP address. The third address (255.255.255.0) is your subnet mask, which you also need. Also find your default gateway (the IP address of your router) with the command **route**.

Your router probably assigns addresses starting with 2 upwards, keeping 1 for itself - most do. In this case, choose high numbers for your permanent addresses so you don't conflict with anything the router tries to assign. I choose 192.168.1.101 upwards for my permanant addresses. Never change the first 3 numbers, just the fourth.

You can find the IP address settings in System->Administration->Network

You shoud be able to ping your other PCs right now once you know their IP addresses. e.g. **ping 192.168.8.3** but while they're automatically assigned they might change every time you reboot so they're not suitable for using in game configs etc. until you have permanent addresses.

---

### Post by andriy.kostyuk on 2008-06-15
> **The Cog said:**
> First, find out what the current ip addresses are - use the command **ifconfig** and look for a line like:

The first entry (192.168.1.2 or whatever) is your current IP address. The third address (255.255.255.0) is your subnet mask, which you also need. Also find your default gateway (the IP address of your router) with the command **route**.

Your router probably assigns addresses starting with 2 upwards, keeping 1 for itself - most do. In this case, choose high numbers for your permanent addresses so you don't conflict with anything the router tries to assign. I choose 192.168.1.101 upwards for my permanant addresses. Never change the first 3 numbers, just the fourth.

You can find the IP address settings in System->Administration->Network

You shoud be able to ping your other PCs right now once you know their IP addresses. e.g. **ping 192.168.8.3** but while they're automatically assigned they might change every time you reboot so they're not suitable for using in game configs etc. until you have permanent addresses.


I tried to do it.
One of thetwo computers lost the internet connection. At the other one it became very slow. And the two computers still cannot find each other to play Freeciv. :(

Is there any other suggestions?

It's strange, that the civclient at one computer sees the sivserver running on the other one. But if one tries to Connect, one gets the message "Failed looking up host". :(

---

### Post by The Cog on 2008-06-16
So what IP addresses / subnet masks did they have (I guess you went back to using DHCP). Also, what was the address of the gateway in their default route?

While you're at it, while they have used DHCP to get their IP addresses, what is the content of the file /etc/resolv.conf?

---

### Post by aktiwers on 2008-06-16
I run this setup, and it's pretty easy to setup as well (NFS):
[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

---

### Post by cariboo on 2008-06-16
Here is a link to Linux Networking howto, this should answer most of the questions you have.
[COLOR="Red"]
[http://tldp.org/HOWTO/NET3-4-HOWTO.htm](http://tldp.org/HOWTO/NET3-4-HOWTO.htm)[/COLOR]

Jim

---

### Post by andriy.kostyuk on 2008-06-17
Thanks to averibody who answered.
I'll try once more next weekend.

---

