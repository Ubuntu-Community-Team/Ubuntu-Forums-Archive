---
title: "Give a user permision to use certain ports"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by ahbb on 2008-07-15
HI there,

I want to give a user permission to use port 21 and 554 for incoming connections.

I don't want to give it total root access is there way just give the program that he wants to run access to open that 2 ports?

Thanks for the help.

Andrew

---

### Post by Dedoimedo on 2008-07-15
Hello,

Definitely. You need to add rules to your firewall.

There are two ways of doing it:

- Use a frontend (like Firestarter)
- Use the terminal commands

Here, I'll show you the terminal commands.

Before that, please read this on how to make iptables on Ubuntu more friendly and accessible.

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Assuming you use direct network connection, the rules you need are:

```
iptables -t filter -A INPUT --dport 21 -i ethx -j ACCEPT
iptables -t filter -A INPUT --dport 554 -i ethx -j ACCEPT
```

ethx is the networm device, for instance eth1, but it could also be something like wlan0 and so forth... so make sure you use the right one.

And then to save the rules permanently:

```
iptables-save
```

If you also require NAT, port forwarding etc, this gets more complicated, so please tell.

Don't forget to backup your existing rules before making any changes. Lastly, remember, open ports might mean lesser security, so make sure you update your software constantly.

Dedoimedo

---

### Post by ahbb on 2008-07-15
Hi there,

Thanks for your reply.

Just 1 problem.

When i use the cmd you gave me to add the ports.

I get this error.

root@shells:~# iptables -t filter -A INPUT --dport 554 -i ethx -j ACCEPT
iptables v1.3.3: Unknown arg `--dport'
Try `iptables -h' or 'iptables --help' for more information.
root@shells:~#

Please advice.

Thanks again :)

Andrew

---

### Post by brian_p on 2008-07-15
> **ahbb said:**
> I get this error.

root@shells:~# iptables -t filter -A INPUT --dport 554 -i ethx -j ACCEPT
iptables v1.3.3: Unknown arg `--dport'
Try `iptables -h' or 'iptables --help' for more information.
root@shells:~#

I think you have to specify the protocol used (e.g -p tcp).

---

### Post by Dedoimedo on 2008-07-15
Hi,
Oops, sorry ... yes, you need to specify the protocol, indeed.
Sorry for the omission. By the way, ethx won't work - you must use a real network device (run ifconfig to decide which).
Dedoimedo

---

### Post by ahbb on 2008-07-15
Hi,

Well that ifconfig just confuse me lol.

Tell me is this right if i use this to add the ports?

sudo iptables -A INPUT -p tcp --dport 21 -j ACCEPT

Then if it's added and saved must the client restart it's process before the port open?

Thanks

Andrew

---

### Post by Dedoimedo on 2008-07-15
Hello,

That's good. This will work for all network interfaces. Just so you remember.

The rules are applied immediately. No need to restart anything. Just make sure you save the rules so they remain persistent.

Dedoimedo

---

### Post by ahbb on 2008-07-16
Hi there,

Thanks again, pls look here @ my tables.

It show's it's open but when ppl try to connect to 21 it still tell they cant access that port.

root@shells:~# iptables -L -v
Chain INPUT (policy ACCEPT 574K packets, 62M bytes)
 pkts bytes target     prot opt in     out     source               destination
  175 13306 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www
    0     0 ACCEPT     tcp  --  ethx   any     anywhere             anywhere            tcp dpt:rtsp
    0     0 ACCEPT     tcp  --  ethx   any     anywhere             anywhere            tcp dpt:ftp
    0     0 ACCEPT     tcp  --  ethx   any     anywhere             anywhere            tcp dpt:pop3
17520 1153K ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh
 133K 7099K ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ircd
  687 29729 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:afs3-fileserver
  178  9660 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ftp
    1    60 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:rtsp
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:afs3-fileserver
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ircd
    0     0 ACCEPT     tcp  --  venet0 any     anywhere             anywhere            tcp dpt:ftp
    0     0 ACCEPT     tcp  --  venet0 any     anywhere             anywhere            tcp dpt:rtsp
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ftp
    0     0 ACCEPT     tcp  --  venet0 any     anywhere             anywhere            tcp dpt:ftp
    0     0 ACCEPT     tcp  --  venet0 any     anywhere             anywhere            tcp dpt:ftp
    0     0 ACCEPT     tcp  --  venet0 any     anywhere             anywhere            tcp dpt:ftp
   37  3102 ACCEPT     tcp  --  venet0 any     anywhere             anywhere            tcp spt:ftp


thanks again for help

Andrew

---

### Post by Dedoimedo on 2008-07-16
Hi,

I told you, you can't use ethx - that's a generic term!!! You need to use eth0 or eth1 or something ... which you can determine from your ifconfig.

```
ifconfig -a
```

This way you'll see all your network interfaces. Choose the appropriate one. Don't enable ftp for all interfaces, because this might not be what you want.

Lastly, make sure there is no other firewalls in front of your machine (router, ISP etc) and that you have a valid IP accessible to the relevant user.

Dedoimedo

P.S. Your policy is set to ACCEPT in INPUT. This is not good. You are allowing all unprocessed inbound connections. I'd recommend you change it to DROP.

---

