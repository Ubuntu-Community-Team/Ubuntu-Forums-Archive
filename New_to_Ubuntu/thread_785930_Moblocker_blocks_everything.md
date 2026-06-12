---
title: "Moblocker blocks everything"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by siretfel on 2008-05-07
Hi all,

I've just installed moblock and it seems that it blocks everything. I went to settings of moblocker and checked allow http AND https and restarted it, but it stills blocks everything!
Anyone has any suggestion on that?
thanks in advance

---

### Post by herrdoktor330 on 2008-05-07
[https://help.ubuntu.com/community/MoBlock]("https://help.ubuntu.com/community/MoBlock")

Check the first entry in the FAQ and you should be good to go.

[http://ubuntuforums.org/showthread.php?t=192559]("http://ubuntuforums.org/showthread.php?t=192559")

That's a dedicated forum thread to MoBlock.

Hope that helps. And if you need anything else, let us know.

---

### Post by Austin_KW on 2008-05-07
Whilelist your home network IP subnet. The first thing http does is a dns lookup (usually on your router ip)

---

### Post by siretfel on 2008-05-08
Thanks you guys for your help! I 've just read the answers. I'll give em a try immediatelly.
Again many thanks

---

### Post by siretfel on 2008-05-08
Unfortunatelly that's it. Now it doesn't work anymore.Again firefox is blocked. Can't open any page eventhough i changed the settings according to faq:

WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT=""
WHITE_UDP_OUT=""
# This is an example to whitelist outgoing web traffic (port 80 is the service
# http, 443 is https):
 WHITE_TCP_OUT="80 443"
 WHITE_TCP_OUT="http https"
# This is an example to whitelist the port range 1000-1024:
# WHITE_TCP_OUT="1000:1024"
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""


Any suggestions?


EDIT:
I replaced the # in the ports and just did this:
I whitelisted an ip address.I did this:
from: # WHITE_IP_OUT="192.168.178.0"
To:  WHITE_IP_OUT="192.168.178.0"

Is that correct?

---

### Post by Austin_KW on 2008-05-08
Whitelist your home network ip range
Eg assuming you are on 192.168.1.x
```
WHITE_IP_IN="192.168.1.0/24"
WHITE_IP_OUT="192.168.1.0/24"

```
and restart moblock with sudo moblock-control restart

---

### Post by siretfel on 2008-05-08
> **Austin_KW said:**
> Whitelist your home network ip range
Eg assuming you are on 192.168.1.x
```
WHITE_IP_IN="192.168.1.0/24"
WHITE_IP_OUT="192.168.1.0/24"

```
and restart moblock with sudo moblock-control restart

Did that and worked.Again thank you. Last question (i hope)
What's .../24 for?

---

### Post by Austin_KW on 2008-05-08
> **siretfel said:**
> Did that and worked.Again thank you. Last question (i hope)
What's .../24 for?

/24 is the bitmask equivalent to 255.255.255.0

Or simply;
For an address x.x.x.x each 'x' is 8 bits
/24 says match first 24 bits 
i.e. for 192.168.1.x it matches 192.168.1 (24 bits) and the last 8 bits (x) can be anything. 
So it matches all addresses on your 192.168.1.x network (for any x)

---

### Post by siretfel on 2008-05-08
Thanks for your answer and wisdom!
Hope sometime I'll be able to pass what i learn to others in ubuntu universe.
Till then...i'll 'enjoy' being a newbi asking.
Thanks!

---

### Post by daggerx on 2008-06-24
I originally installed moblock, nothing worked and I landed heard and the the whitelist deal then I was able to surf again. Then I came across the graphical interface (moblocker) and I installed and started running it - when its running everything is blocked, when its not, everything is working, I'm sure its somethings small. I have firestarted but its not running (at least I don't think it is) since it isn't in the taskbar. 

attached are the screens of my moblocker (I'm a little cluesless right now) but i'm sure its something small. Thank you in advance.

---

### Post by jre on 2008-06-27
mobloquer is just a front-end and doesn't change anything on your system. So I don't know what's going wrong.
Is your traffic blocked by moblock (check /var/log/moblock.log or the mobloquer window) while you are running mobloquer? Or is it something else?

firestarter is not a firewall on itself. It just inserts iptables rules - iptables is the Linux firewall. So check your iptables rules with "moblock-control status" when mobloquer is running. See here for an explanation of the iptables rules: [http://ubuntuforums.org/showthread.php?t=803183](http://ubuntuforums.org/showthread.php?t=803183)
Or just post them here.

---

### Post by daggerx on 2008-06-27
here are mine:

```
Current iptables rules (this may take awhile):

Chain INPUT (policy ACCEPT 1524K packets, 1565M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 1015K packets, 92M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Please check if the above printed iptables rules are correct!

 * moblock is running, pid is 5612.

```

This is what I got when I did the status...

---

### Post by jre on 2008-06-28
Answer is here: [http://forums.phoenixlabs.org/showthread.php?p=117401#post117401](http://forums.phoenixlabs.org/showthread.php?p=117401#post117401)

---

### Post by richardh9936 on 2008-08-07
Mobloquer is wonderful.  The whole family is impressed by it, and by being able to block 775 million sites.  Adding whitelist sites is easy too.
Thanks.

---

