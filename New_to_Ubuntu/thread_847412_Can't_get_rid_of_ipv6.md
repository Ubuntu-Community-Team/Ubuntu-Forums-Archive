---
title: "Can't get rid of ipv6"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by wrtpeeps on 2008-07-02
I tried getting rid of ipv6 by adding:

alias net-pf-10 off to /etc/modprobe.d/bad_list as I got from a thread on this forum somewhere. 

However, running the command 

ip a | grep inet6

gives the output:

inet6 ::1/128 scope host 
inet6 fe80::201:2eff:fe0b:c4bb/64 scope link 

and apparently I should get no output if ipv6 is disabled.

Any ideas?

---

### Post by sayakb on 2008-07-02
Why do you want to disable IPv6? Disabling it will **not** have any impact on the internet speed.

---

### Post by wrtpeeps on 2008-07-02
> **LinuxIsInnovation said:**
> Why do you want to disable IPv6? Disabling it will **not** have any impact on the internet speed.

hmmm. I could swear I saw somewhere on ehre that ipv6 can cause sites to start loading slower at the start. Certainly it's taking a long time for dns lookup here.

If it makes no difference then there's no point disabling it I suppose. 

Thanks.

---

### Post by wrtpeeps on 2008-07-02
.

---

### Post by hyper_ch on 2008-07-02
ipv6 can make a difference on speed because if your router doesn't support ipv6 it might first try to query with ipv6, then get a time-out and then use ipv4 queries... (or something like that)

[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

---

### Post by Sam Lars on 2008-07-07
I think you're right, IPv6 can cause some problems.
You could try disabling IPv6 this way:
```
/etc/modprobe.d/aliases
```
Change from:
```
alias net-pf-10 ipv6
```
to
```
alias net-pf-10 off 
```

---

### Post by alienexplorers on 2008-07-07
Edit /etc/modprobe.d/aliases to look like this:

> # network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
[COLOR="Red"]alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6[/COLOR]
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet
# 18 ASH
alias net-pf-19 af_econet
alias net-pf-20 atm
# 22 SNA
alias net-pf-23 irda
alias net-pf-24 pppoe
alias net-pf-25 wanrouter
alias net-pf-26 llc
alias net-pf-31 bluetooth


Edit /etc/modprobe.d/blacklist to look like this:

> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

[COLOR="Red"]blacklist ipv6[/COLOR]


---

### Post by The Cog on 2008-07-07
You are right that IPv6 can sometimes slow things down, and for the reason you state - trying IPV6 and timing out before trying IPv4. 

I suspect it's only a problem when Linux has a PPP connection to the Internet. When using a router (Ethernet or wireless), I think the absence of an IPv6 default route means IPv6 isn't tried and it's not a problem.

The easiest way to disable IPv6 is to add the line:
**blacklist ipv6**
to /etc/modprobe.d/blacklist. Then reboot.

---

