---
title: "do I need a firewall?"
date: 2014-03-09
forum: New to Ubuntu
---

### Post by gregg3 on 2014-03-09
I'm running Xubuntu 13.10, and I do just ordinary stuff, the most sensitive being online banking and purchasing things online. Xubuntu documentation says:

[B][I]Set up a firewall
[/I][/B]

*Firewalls help to prevent security breaches by blocking connections             to your computer from unknown sources. No firewall is enabled in the             default Xubuntu installation. However, you have a couple of options for             enabling a firewall to protect your computer against unauthorized             access by people on the Internet or your network.*
*You can install a firewall from **Ubuntu Software Center**.             One such option is **Firestarter**, which is             available from    the Universe repository. For help and advice on             configuring Firestarter, see the             [Firestarter Online Manual]("http://www.fs-security.com/docs.php").*
[I]More advanced users may wish to use the **UFW**             firewall, which is installed, but not enabled, in the default Xubuntu             installation. See the [UFW             community documentation]("https://help.ubuntu.com/community/UFW") on the Ubuntu wiki for more information.


[/I]


But there is no Firestarter in my Ubuntu Software Center and the (UFW) "uncomplicated" firewall looks pretty complicated to me. On top of that a seemingly very knowledgeable person said this:

[I]In short: There is no need for it (a firewall). Ubuntu has no open port by default so there's nothing to block.
[/I]
[I]You should only need a *firewall* on a machine that directly lives on  the internet and has services with open ports running that you *only*  want to make available locally.


[/I]

I just want to be reasonably safe but don't want to overload my system or unneccesarily complicate things. Do you think I need a firewall, and if so, UFW or something else? Thanks!

---

### Post by BlinkinCat on 2014-03-09
Hi,

More general information - [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Cheers - :P

---

### Post by buzzingrobot on 2014-03-09
Whether you "need" a firewall or not depends on what you do.

You can download "gufw" from the repos and use it to configure ufw, which is installed by default on Ubuntu.  Unless you are conversant with firewalls and know you need to close some ports and open some other ports, the default gufw setting should suffice:  Just run it and switch it from 'off' to 'on'.

---

### Post by rburkartjo on 2014-03-09
i would. run sudo apt-get install ufw. in terminal. then after run in terminal sudo ufw enable.

---

### Post by 3rdalbum on 2014-03-09
If you were running any server programs, for instance Apache web server or an FTP server, and you didn't want them to be available outside your computer, you would need a firewall of some kind.

If your modem can accept multiple connections at the same time (for instance, if it creates a wireless network or has several Ethernet ports on the back) then you already have a firewall in your modem and you don't need another one.

In short, from the sounds of things, you don't need a firewall. I agree with your second quote.

---

### Post by kevdog on 2014-03-09
If you are running a server that accepts connections from the outside -- such as ftp, ssh, apache (http), mail, etc, you need a firewall to help limit access to the box.
By default ubuntu doesn't have listening services installed by default.  There are no listening sockets so you really don't need a firewall. 
-- Usually a firewall is used to limit inbound packets, or redirect packets -- ie think of a router that receives packets and then redirects them to computers connected to the router
Outbound packets are usually redirected at the level of a router.  If you are using a machine connected through the router, its likely you don't want to limit outbound connections unless you are super-paranoid of some zero-day exploit that may be calling home.

---

### Post by OrangeCrate on 2014-03-10
> **gregg3 said:**
> I'm running Xubuntu 13.10, and I do just ordinary stuff, the most sensitive being online banking and purchasing things online.

<snip>

I just want to be reasonably safe but don't want to overload my system or unneccesarily complicate things. Do you think I need a firewall, and if so, UFW or something else? Thanks!

Personally, I use the default configuration of UFW on both of my Linux machines (one with Xubuntu, the other with Ubuntu). 

Here's the documentation for UFW:

> 
Default rules are fine for the average home user

When you turn UFW on, it uses a default set of rules (profile) that should be fine for the average home user. That's at least the goal of the Ubuntu developers. In short, all 'incoming' is being denied, with some exceptions to make things easier for home users.


[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Though as stated, you don't really need to configure iptables for the uses you have for your computer, I'm guessing that you'd probably feel more comfortable configuring the firewall, than not.

---

### Post by gregg3 on 2014-03-10
Thanks all for the super information!

---

