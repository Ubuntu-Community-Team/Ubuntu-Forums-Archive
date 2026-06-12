---
title: "[How To] Ubuntu 9.04 server IMQ layer7 ipp2p ipset"
date: 2009-07-24
forum: Outdated Tutorials &amp; Tips
---

### Post by windwalker78 on 2009-07-24
Hi all,

I decided to post this tutorial, because I lost 3 days of my life and I hope I might save someone all or part of the pain I experienced during these 3 days :)
DISCLAIMER: I don't guarantee in any way that this tutorial will not harm your Ubuntu OS or other applications. I suggest you first backup your entire OS or try it on a virtual machine like Virtualbox, Vmware or Qemu just like me.

I used the following tutorial:
[HTML]http://rachunsun.blogspot.com/2009/06/ubuntu-904-compile-kernel-blockbit.html[/HTML]

```

#apt-get update
#apt-get install build-essential kernel-package libncurses5-dev fakeroot iptables-dev
#cd /usr/src/
#chmod -R a-s /usr/src
#wget http://ufpr.dl.sourceforge.net/sourceforge/l7-filter/netfilter-layer7-v2.21.tar.gz
#wget http://ufpr.dl.sourceforge.net/sourceforge/l7-filter/l7-protocols-2009-05-28.tar.gz
#wget http://iptables.org/projects/iptables/files/iptables-1.4.3.2.tar.bz2
#wget http://www.linuximq.net/patchs/iptables-1.4.3.2-imq_xt.diff
#wget http://www.linuximq.net/patchs/linux-2.6.28.9-imq-test2.diff
#tar xvzf l7-protocols-2009-05-28.tar.gz
#tar xvzf netfilter-layer7-v2.21.tar.gz
#tar xvjf iptables-1.4.3.2.tar.bz2
#ln -s /usr/src/iptables-1.4.3.2 iptables
# ln -s /usr/src/linux-source-2.8.26 linux
# cd /usr/src/linux
# patch -p1 < ../netfilter-layer7-v2.21/kernel-2.6.25-2.6.28-layer7-2.21.patch
# patch -p1 < ../linux-2.6.28.9-imq-test2.diff
# cd /usr/src/iptables
# patch -p1 < ../iptables-1.4.3.2-imq_xt.diff
# cp ../netfilter-layer7-v2.21/iptables-1.4.1.1-for-kernel-2.6.20forward/libxt_layer7.* extensions/
# chmod +x extensions/.IMQ-test*
# cp /boot/config-2.6.28-11-server ./.config
#make menuconfig 
```
Device Drivers -> Network device support-> {*}   IMQ (intermediate queueing device) support
IMQ behavior (PRE/POSTROUTING) (IMQ AB) 
Number of IMQ devices (4)
OPTIONAL: Networking support-> Networking options -> TCP/IP networking-> <M>   The IPv6 protocol (In case you want to disable ipv6 later)
                                                                                                                                                                          
Networking support-> Networking options-> Network packet filtering framework (Netfilter)-> Core Netfilter Configuration-> Netfilter Xtables support (required for ip_tables) (ALL SHOULD BE Module or *. I went for *)

```

# make-kpkg clean
# make-kpkg --initrd --append-to-version=-l7 kernel_image kernel_headers
#dpkg -i ../linux-*.deb
#reboot
#modprobe imq
#ip link set imq0 up
#ifconfig

#wget http://ipset.netfilter.org/ipset-3.0.tar.bz2
#tar xvjf ipset-3.0.tar.bz2
#cd ipset-3.0
# make KERNEL_DIR=/usr/src/linux
# make KERNEL_DIR=/usr/src/linux install
#cp kernel/include/linux/netfilter_ipv4/ip_set.h /usr/src/iptables/include/linux/netfilter_ipv4/
#cd /usr/src/iptables/extensions
# vi libxt_layer7.c 
```
Replace all text exit_error with xtables_error   (In vim you can :%s/exit_error/xtables_error/g)
This should be like this:
```
static struct xtables_match layer7 = {
.family = AF_INET,
.name = "layer7",
.version = XTABLES_VERSION, 
.size = XT_ALIGN(sizeof(struct xt_layer7_info)),
.userspacesize = XT_ALIGN(sizeof(struct xt_layer7_info)),
.help = &help,
.parse = &parse,
.final_check = &final_check,
.print = &print,
.save = &save,
.extra_opts = opts
};
``````

#apt-get remove --purge iptables 
#cd /usr/src/iptables
#./configure --with-ksource=/usr/src/linux
#make
#make install
#iptables -m set &#8211;help
#cd /usr/src/l7-protocols-2009-05-28
#make install
#iptables -A FORWARD -m layer7 --l7dir /etc/l7-protocols/protocols --l7proto http -j DROP
#iptables &#8211;nvL
#cd /usr/src
#wget http://ipp2p.org/downloads/ipp2p-0.8.2.tar.gz
#wget http://sources.gentoo.org/viewcvs.py/*checkout*/gentoo-x86/net-firewall/ipp2p/files/ipp2p-0.8.2-kernel-2.6.22.patch
#wget http://aur.archlinux.org/packages/ipp2p/ipp2p/ipp2p-0.8.2-kernel-2.6.28.patch
#wget http://aur.archlinux.org/packages/ipp2p/ipp2p/ipp2p-0.8.2-iptables-1.4.0.patch
#wget http://aur.archlinux.org/packages/ipp2p/ipp2p/ipp2p-0.8.2-iptables-1.4.1.patch
#tar xvzf ipp2p-0.8.2.tar.gz
#cd ipp2p-0.8.2
#patch -p1 < ../ipp2p-0.8.2-kernel-2.6.22.patch
#patch -p1 < ../ipp2p-0.8.2-kernel-2.6.28.patch
#patch -p1 < ../ipp2p-0.8.2-iptables-1.4.0.patch
#patch -p1 < ../ipp2p-0.8.2-iptables-1.4.1.patch
#vi libipt_ipp2p.c
```
Replace all text exit_error with xtables_error  
```
.name = "ipp2p",
.family = PF_INET, 
.version = XTABLES_VERSION,
.size = XT_ALIGN(sizeof(struct ipt_p2p_info)),
.userspacesize = XT_ALIGN(sizeof(struct ipt_p2p_info)),
.help = &help,
```
```
#vi Makefile
```
Replace &#8220;ld -shared -o libipt_ipp2p.so libipt_ipp2p.o&#8221; with &#8220;$(CC) -shared -o libipt_ipp2p.so libipt_ipp2p.o&#8221;
```
#make
#cp libipt_ipp2p.so /usr/local/libexec/xtables/
#cp ipt_ipp2p.ko /lib/modules/2.6.28.9-l7/kernel/net/netfilter/
#depmod -a
#iptables -A FORWARD -m ipp2p --ipp2p -j DROP
#iptables -nvL
```

I hope most of you got this working like me :popcorn:

---

