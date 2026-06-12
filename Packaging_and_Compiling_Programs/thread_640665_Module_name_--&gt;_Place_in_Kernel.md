---
title: "Module name --&gt; Place in Kernel"
date: 2007-12-14
forum: Packaging and Compiling Programs
---

### Post by Rizado on 2007-12-14
There's something I've always wanted to know. When I compile a new kernel I look what modules are loaded by lsmod to see what I have. But often the module name is not used in the kernel description. 

```
Module                  Size  Used by
nf_nat_ftp              3296  0
nf_conntrack_ftp        8896  1 nf_nat_ftp
nf_nat_irc              2688  0
nf_conntrack_irc        6648  1 nf_nat_irc
ipt_LOG                 6080  12
xt_limit                2496  14
ipt_MASQUERADE          3328  1
iptable_nat             7268  1
nf_nat                 19212  4 nf_nat_ftp,nf_nat_irc,ipt_MASQUERADE,iptable_nat
xt_length               1888  3
xt_state                2400  25
xt_MARK                 2240  19
iptable_mangle          2688  1
iptable_filter          2848  1
nf_conntrack_ipv4      17736  27 iptable_nat
nf_conntrack           64204  9 nf_nat_ftp,nf_conntrack_ftp,nf_nat_irc,nf_conntrack_irc,ipt_MASQUERADE,iptable_nat,nf_nat,xt_state,nf_conntrack_ipv4
ip_tables              12904  3 iptable_nat,iptable_mangle,iptable_filter
act_police              5924  1
cls_u32                 7748  4
sch_ingress             3648  1
cls_fw                  5120  4
sch_sfq                 6016  4
sch_htb                17632  1
loop                   17060  0
pcspkr                  2752  0
evdev                  10176  0
fuse                   44500  1
```

So how do I know what options to keep/enable in the kernel config? Some things like fuse and loop is pretty obvious but all nat stuff is, well...

---

### Post by kidders on 2007-12-16
Hi there,

Most of the time, the kernel configurator should tell you the names of modules you are building. For example, choosing one of the modules you listed at random, if you select (in a recent kernel) [FONT=Courier New]Networking -> Networking support -> Networking options -> QoS and/or fair queueing -> Ingress Qdisc[/FONT], you should see "To compile this code as a module, choose M here: the module will be called sch_ingress."

Also, module names are often very closely related to the names of the kernel config options that govern them. For instance ...```
# find /usr/src/linux/ -name Makefile -exec grep sch_ingress {} \;
obj-$(CONFIG_NET_SCH_INGRESS)   += sch_ingress.o
```... essentially tells you that the kernel option you need to enable to keep the "sch_ingress" module is called NET_SCH_INGRESS, but that would have been easy to guess *without* searching the source tree for help.

Since you mentioned NAT, I should perhaps have chosen a slightly better example ... say maybe packet mangling (which controls your firewall's ability to modify packets passing through it). It's kernel config option is called IP_NF_MANGLE. To check for packet mangling support, you could ...```
# See if the kernel you're currently running has support for it...
$ grep IP_NF_MANGLE /boot/config-`uname -r`
CONFIG_IP_NF_MANGLE=m

# Check that the kernel you've just configured does...
$ grep IP_NF_MANGLE /usr/src/linux/.config
CONFIG_IP_NF_MANGLE=m
```If not, find "Packet mangling" in your configurator, and you should see something along the lines of "Packet mangling (IP_NF_MANGLE) This option adds a `mangle' table to iptables...", so you know you're enabling the right thing.

I hope that helps.

---

