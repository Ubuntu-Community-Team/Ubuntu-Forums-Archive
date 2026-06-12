---
title: "Unknown protocol in wireshark"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by f3661d on 2008-06-29
I have these in wireshark:
   
  Source              Destination        Protocol        Info
d6:66:6b:76:d8:62     68:66:60:3e:6e:06       0X6691       Ethernet II
f1:66:66:f6:2d:64     16:64:19:66:56:b6       0X2679       Ethernet II

What are they?

---

### Post by nowshining on 2008-06-29
> **f3661d said:**
> I have these in wireshark:
   
  Source              Destination        Protocol        Info
d6:66:6b:76:d8:62     68:66:60:3e:6e:06       0X6691       Ethernet II
f1:66:66:f6:2d:64     16:64:19:66:56:b6       0X2679       Ethernet II

What are they? These are not my mac addresses. Why are they connected to my desktop, which has no server? How do I block them?

we need more info. did you save the output? just so you know - a lot of things try to connect to your computer. All wireshark does is a gui that shows packets to and from ur computer. It doesn't show whether or not it got blocked, or accepted.

If you have a firewall turned on - a gui for iptables, etc.. u should be fine.

For the more info. thing - did u look up the other ip that is not urs just to see?

---

### Post by f3661d on 2008-06-29
The DNS Response said "No such name" to the Queries.

---

### Post by f3661d on 2008-06-29
I did save the output but how to show it in plain text?

---

### Post by nowshining on 2008-06-29
cp it to ur desktop and add it as an attachment here on the forums...

---

### Post by f3661d on 2008-06-29
Here it is.

== 
removed.

---

### Post by nowshining on 2008-06-29
try removing opendns as ur dns servers? i had awful suspicions about them myself,

either use ur ISPs dns or u  can try one of these:

```
 
earthlink DNS then Copper.net DNS
Primary DNS:             Primary DNS
207.69.188.185        65.247.64.21
Secondary DNS:       Secondary DNS
207.69.188.186         65.247.64.22

```

Also so the terminal, etc.. don't try to go out to ur ISP 

edit your /etc/hosts file and add the following at the top:

```
 
HOSTNAME="botnetgodalphamale".
lo="lo 127.0.0.1"
INTERFACES=(lo)
127.0.0.1 localhost.localdomain localhost botnetgodalphamale
127.0.0.1 localhost

```

now change botnetgod.... to ur hostname u setup when u installed ubuntu, etc..

to see it: in terminal just type the command hostname and it should output ur current hostname.

After doing the following do u see any unusual activity - alas make sure you have a firewall installed.

---

### Post by f3661d on 2008-06-30
I have changed DNS several times since noticing this thing.

---

### Post by nowshining on 2008-06-30
if u know it's an arp it can be disabled:

**(Note: All options below involve using the terminal)**

U can disable icmp, multicast, etc.. ie: accepting it:

edit ur /etc/sysctl file and add the following for safety/protection, incl. stopping acceptance of arps..

```

#Flush ipv4 route before beginning & before setting the TCP optimizations below.
net.ipv4.route.flush=1

# Uncomment the next line to enable TCP/IP SYN cookies
net.ipv4.tcp_syncookies=1

#Don't Send redirects
net.ipv4.conf.default.send_redirects=0
net.ipv4.conf.all.send_redirects=0
net.ipv4.conf.lo.send_redirects=0

#Ignore Arps
net.ipv4.conf.all.arp_ignore=1
net.ipv4.conf.default.arp_ignore=1

# Uncomment the next line to enable/disable packet forwarding for IPv4
net.ipv4.conf.default.forwarding=0

# Disables replies to broadcast ICMP echo (ping), to
# prevent a common DoS attack:
net.ipv4.icmp_echo_ignore_broadcasts=1

# Packet forwarding
net.ipv4.ip_forward=0

# Disables IP source routing
net.ipv4.conf.all.accept_source_route=0
net.ipv4.conf.lo.accept_source_route=0
net.ipv4.conf.default.accept_source_route=0

# Enable IP spoofing protection, turn on source route verification ((reverse-path filter))
net.ipv4.conf.all.rp_filter=1
net.ipv4.conf.lo.rp_filter=1
net.ipv4.conf.default.rp_filter=1

# Disable ICMP Redirect Acceptance
net.ipv4.conf.all.accept_redirects=0
net.ipv4.conf.lo.accept_redirects=0
net.ipv4.conf.default.accept_redirects=0

#disable shared media
net.ipv4.conf.default.shared_media=0

#ignore icmp echo
net.ipv4.icmp_echo_ignore_all=1

#disable file leases /proc to protect from local DOS attacks
fs.leases-enable=0

```

now edit /etc/hosts.deny with the sudo and the editor that u use, ie: gedit, kate, etc.. ex: sudo gedit /etc/hosts.deny and put:

```
 
ALL: PARANOID

```

now in terminal issue: sudo sysctl -p

no need to issue anything for the hosts.deny it should auto re-load transparently. :)

As for the wireshark thing - hopefully someone that knows more will come and help u out - however I did take a look at it, but i'm not sure. More than likely no, nothing - prob. in the end something normal.

I also suggest looking on the forums on how to disable ipv6, to disable ipv6 in firefox: 

in the url bar: about:config

in the search box: network.dns.disableIPv6

double click the word false until it shows true.

a side not that those in sysctl.conf are kernel tuneable commands that allow you to modify how the kernel runs/works - ie: u can also disable debug stuff too if u want let me know and i'll post some debug stuff you can turn off.

well sysctl.conf in the end is what helps by auto-resetting the options you chose on a reboot. the actual command to try without rebooting is sudo -w nameofoption=0, etc..

/proc is a temporary place so everything in it is reset on a reboot. :) - search the web for more info. on /proc
[b] 
To see all system/kernel tuneable options that you can modify (in terminal): sudo sysctl -a
[/b]

---

### Post by f3661d on 2008-06-30
Thank you so much for taking the time to write the code, I copied and pasted all of them. I must confess, the only thing I really understand is ALL: PARANOID.

I just restarted my box after pasting into sysctl, but the entry still shows up in wireshark, although there doesn't seem to be any connection established. I too hope it is something normal and me a clever fool who knows just enough to get into trouble :-)

Thank you again for the help, I really appreciate it.

==
Correction: I restore the original sysctl. have to be careful, some guys were discussing ubuntu becoming the next windows: ubuntu is so user friendly that a lot of users are non-tech, so the forum is swarming with cyber criminals. ( no i can not possibly mean u ...)

---

### Post by nowshining on 2008-06-30
ur welcome, and again - wireshark only shows what goes from and to ur computer - not whether or not it's blocked. and lol, u didn't have to restart - they the sysctl options take effect immediately.

If you have yim, aim, icq, u can contact me by IM and talk to me directly if you have any q's. :)

---

