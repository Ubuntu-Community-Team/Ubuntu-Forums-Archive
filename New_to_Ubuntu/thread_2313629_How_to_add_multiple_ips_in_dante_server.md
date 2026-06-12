---
title: "How to add multiple ips in dante server?"
date: 2016-02-14
forum: New to Ubuntu
---

### Post by raman07 on 2016-02-14
Hi, I have Ubuntu 15.10 x64 vps. In the vps i have 2 ips. I wanted to turn my vps ips in socks proxy so i installed dante server and used the below configuration file to turn my ubuntu vps into socks proxy server.
**This is config i used :**
```
*logoutput: /var/log/socks.log*

*internal: eth0 port = 3128*
*external: eth0*

*method: username none #rfc931*
*clientmethod: none*
*user.privileged: root*
*user.notprivileged: nobody*
*user.libwrap: nobody*
*client pass {*
*        from: my.ip.here/32 port 1-65535 to: 0.0.0.0/0*
*        log: connect disconnect error*
*}*
*pass {*
*        from: my.ip.here/32 to: 0.0.0.0/0*
*        protocol: tcp udp*
*}*

```

The above config worked and turn my 1 internal ip into socks proxy with port 3128.
Since i have 2 ips so i wanted to add my secondary ip too. Below is config i used to turn my both ip in to socks proxy.

[B]This is config i used:

[/B]```
*logoutput: /var/log/socks.log*

*internal: eth0 port = 3128*
*external: eth0*
[I]
internal: eth0:0 port = 9201[/I]
*external: eth0:0*

*method: username none #rfc931*
*clientmethod: none*
*user.privileged: root*
*user.notprivileged: nobody*
*user.libwrap: nobody*
*client pass {*
*        from: my.ip.here/32 port 1-65535 to: 0.0.0.0/0*
*        log: connect disconnect error*
*}*
*pass {*
*        from: my.ip.here/32 to: 0.0.0.0/0*
*        protocol: tcp udp*
*}*

```

As you can see i added another internal & external lines for my secondary ip address. I also check netstat -tulp and found both ips are listening correctly on port 3128 & 9201.
But **problem** is. When i put my secondary ip address in firefox and checked out *"what is my ip"* in google. It showed my primary ip of vps instead of secondary ip.
I can use both proxy alternatly with firefox but when i check *"what is my ip"* it always show my primary address in google search engine and on other websites.

I do not know why it is happening? What changes i need to do? 

Help Please

---

