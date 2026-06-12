---
title: "ip blocking software for ubuntu"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by davincileonar on 2012-02-04
Hey guys,

Before i start, I would like you to know that I am new to linux and ubuntu overall. I know it does not excuse me from anything, so i am sorry for any inconveniences.

Before I switched to Ubuntu, I was using Windows 7. there was a nice software called Peerblock. I was looking for a software that does something similar in ubuntu and does it well. I have been looking everywhere for several hours already. But what I have found is either out-of-date, too complicated or lacks of information or how to. So I thought i could ask for some advice from gurus in ubuntu. 

Could you, please, advice a similar soft to Peerblock and describe or point to how to install it. I am ready and happy to learn from you, even more complicated stuff to protect myself. 

Thank you in advance,
davinci 

p.s - i am using Ubuntu 11.10

---

### Post by dodo3773 on 2012-02-04
There is one called "ipblock" and there is one called "moblock" I think. Not sure how moblock works as I have never used it but ipblock has a  java gui and can also run from the cli.

Edit: ipblock is also known as iplist. Here are some links to get you started:

[http://sourceforge.net/projects/iplist/](http://sourceforge.net/projects/iplist/)

[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

---

### Post by Promille on 2012-02-04
I'm not familiar with PeerBlock, but I suggest you basicly want control of the connections to/from your computer? Then I suggest you take a look into [Snort](http://www.snort.org/) which is an powerfull and easy to use IDS/IPS(Intrustion Detection/Prevention System). 

It may be worth your while to look into iptables aswell.
IPtables is installed by default, as far as I know.
[Iptables](http://www.netfilter.org/projects/iptables/index.html)

---

### Post by davincileonar on 2012-02-04
> **dodo3773 said:**
> There is one called "ipblock" and there is one called "moblock" I think. Not sure how moblock works as I have never used it but ipblock has a  java gui and can also run from the cli.

Edit: ipblock is also known as iplist. Here are some links to get you started:

[http://sourceforge.net/projects/iplist/](http://sourceforge.net/projects/iplist/)

[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

Hey dodo3773,

thanks for the links. I saw them before, but i could never find a howto for iplist. So, I gave up.

> **Promille said:**
> I'm not familiar with PeerBlock, but I suggest you basicly want control of the connections to/from your computer? Then I suggest you take a look into [Snort]("http://www.snort.org/") which is an powerfull and easy to use IDS/IPS(Intrustion Detection/Prevention System). 

It may be worth your while to look into iptables aswell.
IPtables is installed by default, as far as I know.
[Iptables]("http://www.netfilter.org/projects/iptables/index.html")

Promille, yes, you are right. thanks for the info. I'll look at both of them.

---

### Post by dodo3773 on 2012-02-04
> **davincileonar said:**
> Hey dodo3773,

thanks for the links. I saw them before, but i could never find a howto for iplist. So, I gave up.


There are some .deb files on the site. Did you try those?

[http://sourceforge.net/projects/iplist/files/iplist/0.28/](http://sourceforge.net/projects/iplist/files/iplist/0.28/)

---

