---
title: "Do I need a Firewall?"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by dcunn2002 on 2014-01-09
Coming from Windows, one of my instinctive priorities is to set up a firewall.  I have activated GUFW but, as a non-specialist, it does seem amazingly complex to specify what's allowed though compared to Windows.

So my question is twofold:
[LIST=1]
[*]do I actually need a firewall?
[*]is there a site where I can find a range of suggested set ups/port nos etc for various applications  - my #1 priority is  to allow SMB sharing through.
[/LIST]
Thanks   

David

---

### Post by grahammechanical on 2014-01-09
In my uneducated opinion? The router connected to the telephone line should have its own firewall. If a machine is part of a network (other devices can access the machine), then it should have a firewall. Ubuntu installs Uncomplicated Firewall (UFW) by default but it is not enabled by default. Gufw is a GUI front end to UFW.

> [COLOR=#333333][FONT=Ubuntu]When you turn UFW on, it uses a default set of rules (profile) that should be fine for the average home user. That's at least the goal of the Ubuntu developers. In short, all 'incoming' is being denied, with some exceptions to make things easier for home users.[/FONT][/COLOR]

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

I suggest reviewing the logs to see what is being blocked. The default profile might be sufficient. I think that managing UFW with Gufw is as uncomplicated as it can be. But we get in the realm of complicated when we want to manage the firewall by direct interaction with iptables.

> [COLOR=#333333][FONT=Ubuntu]Iptables is a firewall, installed by default on all official Ubuntu distributions (Ubuntu, Kubuntu, Xubuntu). When you install Ubuntu, iptables is there, but it allows all traffic by default. [/FONT][/COLOR]

> [COLOR=#333333][FONT=Ubuntu]There is a wealth of information available about iptables, but much of it is fairly complex[/FONT][/COLOR]

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

It is up to us the route we take.

Regards.

---

### Post by Frogs Hair on 2014-01-09
See the link: [http://askubuntu.com/questions/9206/is-there-a-preinstalled-or-automatic-firewall](http://askubuntu.com/questions/9206/is-there-a-preinstalled-or-automatic-firewall) 

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by jdeca57 on 2014-01-09
> **dcunn2002 said:**
> Coming from Windows, one of my instinctive priorities is to set up a firewall.  I have activated GUFW but, as a non-specialist, it does seem amazingly complex to specify what's allowed though compared to Windows.

What puzzled me is that on 13.10 Gufw must be installed in the software center. That done, activate it, then just add a rule, take preconfigured, selelect services and select SAMBA. 

Of course you can make it somewhat more complex by doing it manually.
The ports are described: [http://wiki.samba.org/index.php/Samba_port_usage](http://wiki.samba.org/index.php/Samba_port_usage)

If you have data to protect, a firewall is a very good idea. Just remember it is running if you want to access your box with something like ssh...;-)

---

### Post by dcunn2002 on 2014-01-09
Thanks for advice. Seem to have firewall working as required simply by turming on via GUFW and then allowing samba.

David

---

