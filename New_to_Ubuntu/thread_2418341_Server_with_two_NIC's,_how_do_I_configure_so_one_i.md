---
title: "Server with two NIC's, how do I configure so one is in a &quot;192&quot; and &quot;172&quot; IP range?"
date: 2019-05-05
forum: New to Ubuntu
---

### Post by igcd on 2019-05-05
Hello there,

I have a server coming in that we will sell to a customer. Before it arrives I need to know how to configure certain things.

The server has two NIC's. I want to be able to configure them so that one NIC will be in a "192" IP range, the other in a "172" IP range.

The reason for this is I need the 192 port to connect to the network, and the 172 port to connect to a PoE switch that will have security cameras connected to it.

This server will have **Lubuntu** installed in it. I don't know enough about Linux to be able to configure the network settings in it to make this happen.

I currently don't have the server yet, it will arrive in a day or two, so I may not be able to answer anything specific regarding the server as of yet.

I was wondering if anyone knew how to configure this.

Any help will be greatly appreciated.

---

### Post by joegry on 2019-05-05
Hi there igcd.  Please start by reviewing the Ubuntu documentation for configuring network.  You can find it at this link [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)

---

### Post by igcd on 2019-05-05
Ok thanks. I have read through it. I will see if that is exactly what I was looking for when the server arrives. Much appreciated.

---

### Post by igcd on 2019-05-12
Hello There. I finally got the new server. I went through the [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html) link you sent me but I have gotten stuck on one part. 

I am using **Lubuntu 16.04 **and I am configuring the /etc/plan/netplan-acl file, because I read here [https://linuxhint.com/install_netplan_ubuntu/](https://linuxhint.com/install_netplan_ubuntu/) that file was what I was supporsed to configure in 16.04.

The problem is when I get to configuring the DHCP part and edit the netplan-acl file to have:

network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      dhcp4: trueAnd type the command:
[FONT=monospace]sudo netplan apply[/FONT]I get the error message:

*bind: Address already in use*
*netplan: fatal error: cannot bind to port 2983, is another daemon running?, exiting.*

I don't know what this means. Could somebody help me? How do I get around this?

Kind regards.

---

### Post by TheFu on 2019-05-12
16.04 doesn't use netplan. Ignore anything that mentions netplan. It is a 17.10 and later configuration.  

You need to configure it using the /etc/network/interfaces file. There are thousands of examples on the internet and the manpage for "interfaces" is pretty complete.  The config is tied to the specific device names. You'll need 1 stanza for each and they must be correct. Leave the localhost stanza too.

Something like this:```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto ens3
iface ens3 inet static
  address 172.22.44.9
  gateway 172.22.44.1
  netmask 255.255.255.0
  dns-nameservers 172.22.22.1 1.1.1.1 1.0.0.1
```
Another stanza for the other "device" on 192.168.x.x is required.  If you need specialized routing controls, there are pre-up and post-up options. Check the manpage.  On Unix systems, command and config files have manpages.

Whenever posting config files or command output, it is critical to use "code tags" so the data here looks exactly like it did in your terminal.  If you look at the post just above this, that file as posted is useless because indentation is missing, but it is critical for netplan which isn't used in 16.04.  Configs and commands - need code tags. Please.

There's a bunch of cruft added in desktops that eat storage, run extra processes and lower security of the system. These are some of the reasons why servers don't get GUIs.  If you are really new and don't have time to learn everything (who does?), then probably the best answer is to buy a 16.04 Ubuntu Server Unleashed book. Those should be cheap now. Looking for answers and waiting for the reply will waste much more time than a book costs. To really learn Linux with a deeper understanding requires time, practice, and seeing deeper connections than any book will explain.  Eventually, things "click", but I doubt you have the 12+ months for that.

Normally, at this point I'd strongly push for any new deployment to be using 18.04.  But I just did a few fresh installs and chose 16.04 myself - mainly because netplan is still causing issues for enough people that I don't trust it. A few other huge changes were included in 18.04 which need some more maturation before my servers will use it. Obviously, this is all opinion. Lots of people are using 18.04 in their servers and find it works fine. It has been out over a year with plenty of patches.

In a year, you'll either be moving these systems to 18.04 or 20.04. Skipping those migrations before deployment is something I'd look at for a long time before choosing NOT to use it.

---

