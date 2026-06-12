---
title: "tun/tap on ubuntu"
date: 2005-01-21
forum: Repositories &amp; Backports
---

### Post by sesquipedality on 2005-01-21
Does the standard ubuntu kernel have support for the tun/tap device driver?  If not, how does one go about adding support for it (i.e. compiling a compatible module or whatever else is required)?  Thanks.

---

### Post by trapik on 2005-01-26
yes    /sbin/modprobe tun

---

### Post by sesquipedality on 2005-01-30
Thank you.  I really didn't expect it to be that simple.

---

### Post by Happy on 2005-04-04
I've just spent the last several hours trying to get tun to work...
it just doesn't like me.
I've added the 'tun' module using modprobe and that's about it
whenever I try 'ifconfig tun0 10.0.0.1 up' or similar I get this result:
SIOCSIFADDR: No such device
tun0: ERROR while getting interface flags: No such device
tun0: ERROR while getting interface flags: No such device

I've created the /dev/net/tun node and checked it's privileges and all that jazz but still no love!
ifconfig -a comes up empty for the tun0 interface...
any ideas?
(i've installed the vtun package via synaptic was that the correct one?)

---

### Post by suoko on 2006-01-10
I have the same problem using kernel 2.6.12-10-686 but I don't have any problems with latest dapper kernel.
Question: is it a problem related to the kernel?

---

### Post by GTvulse on 2006-01-10
[QUOTE=Happy]I've just spent the last several hours trying to get tun to work...
it just doesn't like me.
I've added the 'tun' module using modprobe and that's about it
whenever I try 'ifconfig tun0 10.0.0.1 up' or similar I get this result:
SIOCSIFADDR: No such device
tun0: ERROR while getting interface flags: No such device
tun0: ERROR while getting interface flags: No such device

I've created the /dev/net/tun node and checked it's privileges and all that jazz but still no love!
ifconfig -a comes up empty for the tun0 interface...
any ideas?
(i've installed the vtun package via synaptic was that the correct one?)[/QUOTE]
Have you created a virtual interface bridge? You need the userspace utilities contained in the vtun package (that's in the Universe repository).

---

### Post by cylon359 on 2006-01-10
You can also create a persistent tunnel with openvpn... 

sudo openvpn --mktun --dev tun0

---

### Post by GTvulse on 2006-01-10
There is also a tunctl utility in User Mode Linux (that hasn't worked for me, YMMV). You can download the source code from the project's CVS repository: [http://www.user-mode-linux.org/cvs/tools/tunctl/tunctl.c?sortby=date]("http://www.user-mode-linux.org/cvs/tools/tunctl/tunctl.c?sortby=date").

---

### Post by GTvulse on 2006-01-13
[QUOTE=dradul]There is also a tunctl utility in User Mode Linux (that hasn't worked for me, YMMV). You can download the source code from the project's CVS repository: [http://www.user-mode-linux.org/cvs/tools/tunctl/tunctl.c?sortby=date]("http://www.user-mode-linux.org/cvs/tools/tunctl/tunctl.c?sortby=date").[/QUOTE]
I can now say I have successfully used tunctl to set up a PPPoE (RFC2516) connection using the [eciadsl]("http://eciadsl.flashtux.org/") drivers (big change in my ISPs a day after I posted the above).

Now I'm using a PPPoE connection emulated over a persistent virtual ethernet TAP created with tunctl and controled with the eciadsl drivers. I tried with openvn at first but I then realized that it made the TAP device dependent on the openvpn daemon. Using tunctl is easier. You can either install uml-utilities available in the universe repository, or compile tunctl.c[1] and type a simple command[2].

[1] [FONT="Courier"]gcc -O2 -s -o tunctl tunctl.c[/FONT]

[2] [FONT="Courier"]sudo ./tunctl -u root tap0[/FONT]

---

### Post by Fink on 2007-12-20
> **sesquipedality said:**
> Thank you.  I really didn't expect it to be that simple.

didn't know that either

---

### Post by dramaekrs on 2011-11-09
Hi,

I see there are people here who know what they are talking about :)

I had a working vpn server in tun/tap. After doing a dist-upgrade to 11.10, I still can connect to the vpn server but the network behind the vpn server isn't forwarded any more.

Say the IP of my vpn-server is 10.3.0.50, on the remote client I can ping 10.3.0.50. But I can't ping 10.3.0.1...

Does any one have an idea where to look to solve this problem?

Dominique.

---

