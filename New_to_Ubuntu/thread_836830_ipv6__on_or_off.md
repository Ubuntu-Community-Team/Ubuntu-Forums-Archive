---
title: "ipv6  on or off??"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by bu2971x on 2008-06-21
I have heard about satellite users and ipv6.  I have the tables but not anything else I know of.  Should this be installed or not..????
any comments apprec.   especially satellite users..

---

### Post by Joeb454 on 2008-06-21
Not a satellite user personally. But you could turn it off, and if you want (or need) to you can turn it back on whenever :)

---

### Post by ramjet_1953 on 2008-06-21
The vast majority of Internet sites are IPV4 and if you turn it off, your access times should improve.

Also, with IPV6 enabled, sometimes there are conflicts with IPV4 and hang-ups can occur.

Regards,
Roger :cool:

---

### Post by wariskampar on 2008-06-21
How to check whether ipv6 is on or off. if it does, how to turn it off

---

### Post by ramjet_1953 on 2008-06-22
The easiest way to turn off ipv6 is to do this:

1. Create a file called [COLOR="Blue"]bad_list[/COLOR] in /etc/modprobe.d
i.e. [COLOR="Red"]sudu nano /etc/modprobe.d/bad_list[/COLOR]

2. Insert this line into the file:
[COLOR="Blue"]alias net-pf-10 off[/COLOR]

3. Save the file and then re-boot.

Regards,
Roger :cool:

---

### Post by wariskampar on 2008-06-22
sorry if my question is too mean, but you didnt answer the first question; how to know ipv6 is activated or not. dont mean to offense you though:)

---

### Post by alienexplorers on 2008-06-22
Go to Modprobe.d and look for aliases and make the changes show in red to yours:
```
# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ##########################################################
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

# executables formats ########################################################
install binfmt-0000 /bin/true
alias binfmt-204 binfmt_aout
alias binfmt-263 binfmt_aout
alias binfmt-264 binfmt_aout
alias binfmt-267 binfmt_aout
alias binfmt-387 binfmt_aout

# block devices ##############################################################
alias block-major-3-*  ide_generic
alias block-major-8-*  sd_mod
alias block-major-9-*  md
alias block-major-11-* sr_mod
alias block-major-22-* ide_generic
alias block-major-33-* ide_generic
alias block-major-34-* ide_generic
alias block-major-37-* ide_tape
alias block-major-44-* ftl
alias block-major-46-* pcd
alias block-major-47-* pf
alias block-major-56-* ide_generic
alias block-major-57-* ide_generic
alias block-major-58-* lvm_mod
alias block-major-88-* ide_generic
alias block-major-89-* ide_generic
alias block-major-90-* ide_generic
alias block-major-91-* ide_generic
alias block-major-93-* nftl
alias block-major-97-* pg

# character devices ##########################################################
alias char-major-9-* st
alias char-major-10-1 psmouse
alias char-major-10-139 openprom
alias char-major-10-157 applicom
alias char-major-10-181 toshiba
alias char-major-10-183 hw_random
alias char-major-10-189 ussp
alias char-major-10-250 hci_vhci
alias char-major-13-0  joydev
alias char-major-13-1  joydev
alias char-major-13-2  joydev
alias char-major-13-3  joydev
alias char-major-13-32 mousedev
alias char-major-13-33 mousedev
alias char-major-13-34 mousedev
alias char-major-13-35 mousedev
alias char-major-13-63 mousedev
alias char-major-13-64 evdev
alias char-major-13-65 evdev
alias char-major-13-66 evdev
alias char-major-13-67 evdev
alias char-major-19-* cyclades
alias char-major-20-* cyclades
alias char-major-22-* pcxx
alias char-major-23-* pcxx
alias char-major-27-* ftape
alias char-major-34-* scc
alias char-major-35-* tclmidi
alias char-major-48-* riscom8
alias char-major-49-* riscom8
alias char-major-57-* esp
alias char-major-58-* esp
alias char-major-63-* kdebug
alias char-major-67-* coda
alias char-major-75-* specialix
alias char-major-76-* specialix
alias char-major-81-* videodev
alias char-major-83-* vtx
alias char-major-89-* i2c_dev
alias char-major-90-* mtdchar
alias char-major-96-* pt
alias char-major-97-* pg
alias char-major-107-* 3dfx
alias char-major-109-* lvm_mod
alias char-major-166-* cdc_acm
alias char-major-171-0 raw1394
alias char-major-171-1 video1394
alias char-major-171-2 dv1394
alias char-major-171-3 amdtp
alias char-major-180-* usbcore
alias char-major-195-* nvidia
alias char-major-200-* vxspec
alias char-major-202-* msr
alias char-major-203-* cpuid
alias char-major-206-* osst
alias char-major-208-* ussp
alias char-major-227-* tub3270
#alias char-major-240-* usb-serial
#alias char-major-240-* hsfserial
#alias char-major-241-* hsfserial

# misc #######################################################################
alias xfrm-type-2-4 xfrm4_tunnel
alias xfrm-type-2-50 esp4
alias xfrm-type-2-51 ah4
alias xfrm-type-2-108 ipcomp
alias xfrm-type-10-41 xfrm6_tunnel
alias xfrm-type-10-50 esp6
alias xfrm-type-10-51 ah6
alias xfrm-type-10-108 ipcomp6

alias bt-proto-0 l2cap
alias bt-proto-2 sco
alias bt-proto-3 rfcomm
alias bt-proto-4 bnep
alias bt-proto-5 cmtp
alias bt-proto-6 hidp
alias bt-proto-7 avdtp

alias cipcb0 cipcb
alias cipcb1 cipcb
alias cipcb2 cipcb
alias cipcb3 cipcb
alias dummy0 dummy
alias dummy1 dummy
alias plip0 plip
alias plip1 plip
alias slip0 slip
alias slip1 slip
alias tunl0 ipip
alias gre0 ip_gre

alias usbdevfs usbcore

```

Then look for the blacklist file and modify it as shown:
```
# This file lists those modules which we don't want to be loaded by
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
```

---

### Post by ramjet_1953 on 2008-06-22
ipv6 is on by default.

It remains so, unless you turn it off.

Regards,
Roger :cool:

---

### Post by forestpixie on 2008-06-22
If you get a repsonse in a terminal from 

```
ip a | grep inet6
```

It's on, but as ramjet says it is on if you haven't turned it off.

---

### Post by Oldsoldier2003 on 2008-06-22
> **ramjet_1953 said:**
> The easiest way to turn off ipv6 is to do this:

1. Create a file called [COLOR="Blue"]bad_list[/COLOR] in /etc/modprobe.d
i.e. [COLOR="Red"]sudu nano /etc/modprobe.d/bad_list[/COLOR]

2. Insert this line into the file:
[COLOR="Blue"]alias net-pf-10 off[/COLOR]

3. Save the file and then re-boot.

Regards,
Roger :cool:

Doesn't work in Hardy. I had the bad_list from gutsy and had to blacklist it and edit aliases when I upgraded.

---

### Post by nickdbliss on 2008-06-22
> **Oldsoldier2003 said:**
> Doesn't work in Hardy. I had the bad_list from gutsy and had to blacklist it and edit aliases when I upgraded.

I agree.

---

### Post by lionel47 on 2008-06-22
So, how exactly does one turn off ipv6 in Hardy?  Can we get some step by step instructions on doing this?:)

---

### Post by alienexplorers on 2008-06-22
In my post I showed you how to turn it off in HARDY!

---

### Post by waapwoop1 on 2008-06-23
To alien explorer or anyone... help!

it just says go to Modprobe.d and look for aliases.
what do i do to do this, i tried sudo gedit /etc/modprobe.d  but it said this was a directory.... i'm a little confused. more step by step for me!

---

### Post by The Cog on 2008-06-23
I found that I could disable ipv6 in Hardy simply by adding the line
**blacklist ipv6**
to the file **/etc/modprobe.d/blacklist** although it looks like I could have made a new file (with any name I liked) in that directory and added the line to the new file instead.
Then reboot, of course.
No messing with aliases at all.

P.S. 
You can see if ipv6 is enabled by running the command ifconfig and see if any interface has been given an inet6 addr.
**ifconfig | grep inet6**

---

### Post by ramjet_1953 on 2008-06-24
Thanks for the 'Heads-Up' OldSoldier2003.

I tend to be a bit conservative and usually only do a fresh install every two version releases, so I wasn't aware that the solution I posted didn't work in Hardy.

However, The Cog's solution seens to be nice 'n easy.

Regards,
Roger :cool:

---

