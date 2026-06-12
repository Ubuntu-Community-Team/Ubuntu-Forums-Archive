---
title: "I can ssh to my home router but not to my home desktop machine"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by watchpocket on 2013-04-05
Hello folks,

About a year ago I set myself up to ssh from my workplace windows machine to my home Ubuntu box -- or so I thought.  I ***was ***able to do it successfully a few times over the course of a couple of weeks, but then forgot about it and didn't do it anymore.

So I was blissfully unaware that my ISP assigns me both a dynamic domain name and a dynamic IP address, both of which change regularly.  (Or, I was vaguely aware of it but wasn't paying attention to it.)

Wanting to set this up again, but correctly, I recently registered a name with a DDNS provider since my home router has a built-in updater for several dynamic-IP servers.

[I][B]In any event, my problem is that I can ssh (from a shell account) into my router, but not to my desktop box.

I also cannot access the router settings remotely via web (page times out) and I'd like to be able to do that (or at least know how to do it), as well as set up password-protected sftp access via web browser to my home box's files. [/B][/I]

So, from my shell account's command-line, I can enter:

```
ssh root@xxx.xxx.com
```

I then get a password prompt.  I enter the router's password, and, presto, no problem, I've logged into the router.

If I enter *[COLOR=#008000]"[/COLOR]*[COLOR=#008000]*ssh xxx.xxx.com*[/COLOR]" or *[COLOR=#008000]"ssh   [email]xx@xxx.xxx.com[/email] [/COLOR][COLOR=#008000][/COLOR]*" I also get a password prompt, but at this point I'm lost as to which password I need to enter:  I've entered the passwords for my router, my desktop box, my DDNS account, I've entered "root", "admin", and simply <RETURN> with no password.

*Nothing gets me into my home box.  Not to my  user home dir nor to root access.*

Here below are some relevant router settings.  Thanks for reading this far and thanks for any guidance.


[COLOR=#ff0000]***Relevant router settings:***[/COLOR]

```
Status -> Network -> IP Filter Maximum Ports: 4096;
Active IP Connections: 145,  4%;

Status -> WAN -> Configuration Type:
Connection Type:  Automatic Configuration - DHCP
Connection Uptime:  4 days, 1:54:51
  Remaining Lease Time:  0 days 04:01:03

-----------------------------------------------------

Setup -> Basic Setup -> Optional Settings -> Host Name: xxx.xxx.com
Setup -> Basic Setup -> Network Setup -> Network Address Server Settings (DHCP):
DHCP Type: DHCP Server;
DHCP Server: enabled;
All 3 of the following are enabled:
Use DNSMasq for DHCP; Use DNSMasq for DNS; and DHCP-Authoritative;

-----------------------------------------------------

And, per this tutorial:
<http://www.noip.com/support/guides/routers/dynamic-dns-on-dd-wrt.html>

Setup -> DDNS -> [User Name & Password of my DDNS account]
Type: Custom
Wildcard: checked
Do not use external ip check: yes

( I've also read these tutorials:
<https://help.ubuntu.com/community/DynamicDNS>
<http://ubuntuguide.org/wiki/Dynamic_IP_servers> )

------------------------------------------------------

Services -> Services -> DHCP Server -> Static Leases:
MAC Addr: ___; Host Name: xxxx ;

Services -> Services -> DNSMasq: enabled; Local DNS: disabled;
No DNS Rebind: enabled.

Services -> Services -> Secure Shell ->  SSHd: enabled;
SSH TCP Forwarding: disabled; Password Login: enabled;
Port: 22

------------------------------------------------------

Administration -> Mgmnt -> Web Access: Protocol: HTTP
Enable Info Site: enabled
Info Site Password Protection: enabled
Info Site MAC Masking: enabled

------------------------------------------------------

Administration -> Mgmnt -> Remote Access: Web GI Mgmt: enabled
Web GUI Port: 80
SSH Mgmnt: enabled
SSH Remote Port: 22
Telnet: disabled
Allow any Remote IP: enabled

------------------------------------------------------

NAT/QoS -> Port Forward: App: ssh, Protocol: both TCP & UDP, Port from 22,
-----------------------------------------------------
```

P.S.  I'm putting here the 3 links I have in the router code area above, so that they're clickable: 

[http://www.noip.com/support/guides/routers/dynamic-dns-on-dd-wrt.html](http://www.noip.com/support/guides/routers/dynamic-dns-on-dd-wrt.html)

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

[http://ubuntuguide.org/wiki/Dynamic_IP_servers](http://ubuntuguide.org/wiki/Dynamic_IP_servers)

---

### Post by watchpocket on 2013-04-05
Just so folks know, I am using an outdated version of Ubuntu (Karmic), but having the ssh  link between home & work will be a great help to me in performing the  upgrade, which I plan to do asap.

---

### Post by Azrayal on 2013-04-05
Hi, 

Based on what you are outlining here: 
> So, from my shell account's command-line, I can enter:

Code:
ssh [email]root@rjbox.webhop.net[/email]
I then get a password prompt. I enter the router's password, and, presto, no problem, I've logged into the router.

If I enter "ssh rjbox.webhop.net" or "ssh [email]rj@rjbox.webhop.net[/email]" I also get a password prompt, but at this point I'm lost as to which password I need to enter: I've entered the passwords for my router, my desktop box, my DynDNS account, I've entered "root", "admin", and simply <RETURN> with no password.

you are trying to ssh into your router with the account rj and whatever your currently logged in as on the remote shell account. 
On your router you have ssh (port 22) assigned publicly to your router, you need to disable that and instead forward port 22 to your internal server you are looking to access. 

You can only have port 22 active on one device, you can however setup a port forward of say 24 to your internal server of port 22 and when trying to connect externally you would do something like ssh [email]rj@rjbox.webhop.net[/email]:24 this would allow you to run two external ssh access points. I'm not familiar with your router network provider so I'm not sure this is possible.  

Hope this helps.

---

### Post by forestG on 2013-04-05
Most routers if not all follow the so called NAT policy or protocol. With NAT the following happens (simplified version):

Any computer connected to the router (the Local Network) speaks only to the router. It has no immediate connection to the rest of the Internet. 
Any computer outside the Local Network (i.e. the whole Internet) sees all computers of the Local Network as one computer (the router). 

If one computer sends a request to the Internet the router remembers who asked what, fetches from the Internet the data  and delivers it back to the computer which asked it. If now there is not a request the router does not know where to forward the data. To solve that problem we use the policy of port forwarding. We say to the router that any data send to a specific port should be sent to a specific IP address (a specific computer-- that means that the computer should have a static IP address). This has as a result that one port can be used only by one computer. All ports that are not by any computer or the router which is also a small computer are blocked.
So since the router is also a computer and it is using the port 22 (port for ssh) you should either tell the router to listen to another port and so port 22 would be free for any other computer or you shoudl tell your computer to listen to another port (e.g. 2222) and then when you call the ssh you should specify the new port as well. 

Hint 1: google port forwarding and NAT
Hint 2: I think that Ubuntu does not let you upgrade through SSH

---

### Post by watchpocket on 2013-04-05
Enormous thanks to both of you for responding.  I've made the appropriate changes and I am now*** *IN**** via ssh to my home server !!!  Thanks again for the helpful replies!
> **forestG said:**
> 
Hint 2: I think that Ubuntu does not let you upgrade through SSH

Right -- I didn't mean that I was going to attempt to do an actual upgrade via ssh, only that remote access will help me with my preparations for the upgrade (housekeeping, cleaning, organizing, backup, etc.). 
Thanks again for your clarifications.

---

