---
title: "Setup IPv6 network with ubuntu host and two VMs"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by sumitkamboj on 2013-02-14
Hello All  
I want to setup IPv6 network with two VMs(virtual box) on a ubuntu 12.04  host. One VM is backtrack and second is window XP. I want to know that  how can i setup a fully IPv6 network so that i can communicate form  backtrack to XP on virtual box network attached in bridged adapter mode,  all traffic from backtrack to XP should goes through Ubuntu host. is it also possible to configure ubuntu host as a DHCPv6 server so that  it serve IPv6 to VMs automatically and able to communicate. I appreciate any help. Thanks

---

### Post by lemming465 on 2013-02-14
This should be workable, but you might get better results from KVM virtualization (install metapackage *ubuntu-virt*, then run GUI *virt-manager*) than from virtualbox; last I knew virtualbox had a deficiency/bug where it wouldn't do guest IPv6 over wifi, even when the host would.  Recent versions of virtualbox should be OK if all you want is guest to guest IPv6 or guest to wired IPv6.

Most virtualization solutions have the networking use simulated hubs (traffic floods to all hosts), so if you want to snoop on how your Backtrack guest is attacking your XP guest you should be able to simply point a host *wireshark* at the host's interface on the virtual hub the guests are on.

For DHCPv6, install *isc-dhcp-server*; there are some rudimentary configuration suggestions [on the wiki]("https://wiki.edubuntu.org/DHCPv6").

If you are interested in IPv6 attack traffic and tools, I have two further suggestions:

First, the version of nmap supplied by precise is aging; instead build the latest 6.25 version from the source at nmap.org and you'll get much better v6 support.

Second, one of the more vociferous IETF 6MAN (IPv6 maintenance committee) members, has a [beta release of SI6 Network's IPv6 toolkit]("http://lists.si6networks.com/pipermail/ipv6hackers/2013-February/000947.html") just out; you might want to try out some of those tools as well.

---

### Post by sumitkamboj on 2013-02-21
Thanks
lemming465 for suggestions. 
Can you suggest any good thread/link that suggest me to setup IPv6 on guest machine and host machine on  KVM virtualization.

---

