---
title: "Hello all, n00b here. Any help much appreciated!"
date: 2021-03-16
forum: New to Ubuntu
---

### Post by red783 on 2021-03-16
I've loved Ubuntu since my physics teacher showed me how to replace a slow windows operating system, and basically make an older computer kind of usable again. I never learned the ins and outs though. I could run Firefox and Thunderbird and that was really all I needed. Maybe I'm going through a midlife crisis, but for some reason I want to learn Ubuntu in more depth. Particularly I'd like to know how to set up Proton VPN first. And send some cool command lines this way! For some reason I really want to learn how to use the terminal.

20.04

Thanks!
Stewart

---

### Post by DuckHook on 2021-03-16
Welcome to the forums, red783.

The link in my sig: *Resources for Newcomers* might interest you. There is also this site which many newbies find friendly and informative as an intro: [https://linuxjourney.com/](https://linuxjourney.com/)

There's a lot to learn. Setting up a VPN is not a trivial exercise. I would suggest that you get comfortable with the command line first and, hopefully, setting up the VPN can come quickly thereafter.

For command line goodies, it's not something that can really be taught on a forum thread, but if you are looking for a few nuggets to get started, try: [http://www.commandlinefu.com/commands/browse/sort-by-votes](http://www.commandlinefu.com/commands/browse/sort-by-votes)

Not least, the link in my sig: *A Great CLI Guide* connects to a downloadable PDF book that is a well deserved classic.

Good Luck, Happy Ubuntu-ing and have fun exploring!

---

### Post by ActionParsnip on 2021-03-17
Doesn't Proton VPN have a guide to install a deb that gives the user a GUI app or are you setting this up on a server OS with no GUI

[https://protonvpn.com/support/linux-vpn-setup/](https://protonvpn.com/support/linux-vpn-setup/)

Seems straight forward enough

---

### Post by DuckHook on 2021-03-17
> **ActionParsnip said:**
> Doesn't Proton VPN have a guide to install a deb that gives the user a GUI app or are you setting this up on a server OS with no GUI

[https://protonvpn.com/support/linux-vpn-setup/](https://protonvpn.com/support/linux-vpn-setup/)

Seems straight forward enough
Thanks for the link. I don't use Proton VPN so wasn't aware of this. As a rule, I don't like using apps for my security services like VPN. I set then up using the CLI, OpenVPN and config files. But if OP is happy with the Proton VPN app, then this would be the easiest option.

---

### Post by TheFu on 2021-03-17
> **DuckHook said:**
> Thanks for the link. I don't use Proton VPN so wasn't aware of this. As a rule, I don't like using apps for my security services like VPN. I set then up using the CLI, OpenVPN and config files. But if OP is happy with the Proton VPN app, then this would be the easiest option.

+1 on using standard packages to connect to VPN services.  I don't want to risk a package being modified by some outside attacker or using an application they pulled from the repos 9 months ago when the fully supported VPN from the Canonical repos gets updates every month or so.

Most commercial VPN providers use openVPN as their server, with a few supporting wireguard in the last year. To install, use
```
sudo apt install openvpn 
```

To see which package you have, something like this:
```
$ dpkg -l openvpn*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  openvpn        2.4.4-2ubunt amd64        virtual private network daemon

```
If you want a GUI point-n-click integration with network-manager (upper right-hand part of the screen), there's probably a few other components.  I've never used those, but I think both openvpn and wireguard are well supported.  Then you just need to import the configuration files/data from your VPN provider.  I use a different provider that provides a "package" of AES256 capable exit nodes around the world:
```
$ ls /etc/openvpn/AES-256/
AU_Melbourne.ovpn  Hong_Kong.ovpn              Turkey.ovpn
Austria.ovpn       India.ovpn                  UK_London.ovpn
AU_Sydney.ovpn     Ireland.ovpn                UK_Manchester.ovpn
Belgium.ovpn       Israel.ovpn                 UK_Southampton.ovpn
Brazil.ovpn        Italy.ovpn                  US_Atlanta.ovpn
CA_Montreal.ovpn   Japan.ovpn                  US_California.ovpn
ca.rsa.4096.crt    Mexico.ovpn                 US_Chicago.ovpn
CA_Toronto.ovpn    Netherlands.ovpn            US_East.ovpn
CA_Vancouver.ovpn  New_Zealand.ovpn            US_Florida.ovpn
crl.rsa.4096.pem   Norway.ovpn                 US_Midwest.ovpn
DE_Berlin.ovpn     openvpn-strong-aes-256.zip  US_New_York_City.ovpn
DE_Frankfurt.ovpn  Romania.ovpn                US_Seattle.ovpn
Denmark.ovpn       Singapore.ovpn              US_Silicon_Valley.ovpn
Finland.ovpn       South_Korea.ovpn            US_Texas.ovpn
France.ovpn        Sweden.ovpn                 US_West.ovpn
Germany.ovpn       Switzerland.ovpn

```
I chose which directory to place them. I'd think each of these could be imported into network-manager-ovpn or something like that, here's a quick repo search .... 
```
$ sudo apt search network-manager |grep vpn

network-manager-openvpn/bionic 1.8.2-1 amd64
network-manager-openvpn-gnome/bionic 1.8.2-1 amd64
network-manager-vpnc/bionic-updates,bionic-security 1.2.4-6ubuntu0.1 amd64
network-manager-vpnc-gnome/bionic-updates,bionic-security 1.2.4-6ubuntu0.1 amd64

```

In short, I'd prefer using known repos, preferably from Canonical, for all VPN software. This way it gets patched as part of your weekly patch process.

---

### Post by ActionParsnip on 2021-03-17
You can add a credentials file if you don't want to authenticate. Obviously you need to trust your users for this but if it's only your box then go for it

---

### Post by DuckHook on 2021-03-17
For a new user, the stuff posted by TheFu, as well as the "credentials file" mentioned by ActionParsnip is&#8212;shall we say&#8212;nontrivial?

Hence my suggestion to get comfortable with the command line before attempting such stuff.

@red783

The ProtonVPN app is okay for your use-case. As you get more comfortable with the command line, then TheFu's observations are spot on and it is more secure to avoid outside apps, but until then, using a VPN, even with an outside app, is better on balance than not using one.

---

### Post by grahammechanical on 2021-03-17
Canonical is the sponsor of Ubuntu and it provides a short tutorial on using the command line in Ubuntu. Please pay attention to section 7 - The command line and the super user.

[https://ubuntu.com/tutorials/command-line-for-beginners#1-overview](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)

I suggest that you first learn how to install and dual boot two ubuntu installations. Then you can experiment using commands in one installation of Ubuntu and if you break it, and you will break it, you still have a working installation you can use. Some commands change the system and putting things back the way they were is not easy to do. A re-installation is the easiest method.

Every Ubuntu installation includes a manual for Linux commands. We open the manual in a terminal. For example, if I type this:

```
uname -a
```

I get this printed on the screen

> Linux sdb1-sdb8 5.4.0-67-generic #75-Ubuntu SMP Fri Feb 19 18:03:38 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

It tells me that the Linux kernel is 5.4.0-67-generic. To find out more about the uname command I type this

```
man uname
```

To find out what the man command has to offer type this

```
man man
```

best wishes

---

### Post by red783 on 2021-03-17
Guys! SOOO much information and help and I like that no one is being malicious (as far s I can tell). It’s been a long day I’m just getting to checking these things. I didn’t get notifications about you guys replying at all! It’s late and I don’t have time to read and do this all. But I want to let you all know I appreciate everything and promise to read it all. Quick update tho!

As far as I can tell I’ve got proton and proton mail behaving as they should. Those are the two services I was recommended to start with when I got “identity theft hypochondria”. I like them they seem to serve their purpose. 

I got to play around with the command prompt a bit last night, it ended up being necessary to get everything “working” (at least not giving me error messages). I really like how it’s a necessary part of computing in this OS. It seems more direct. Maybe not easier. But you start to get an understanding of what you’re asking the computer to do.

Again thank you guys so much for all the good information and again I PROMISE to read and try everything tomorrow. Maybe download an emulation app or something?? I just wanted to give an update and let you know your knowledge experience and wisdom did not fall on ears that didn’t care!!

---

### Post by DuckHook on 2021-03-17
Malice is not tolerated on these forums and is dealt with quickly.

The fact that you are using those two Proton services already puts you miles ahead of 90% of Windows/Apple/Android users. You are off to an excellent start.

Just a further observation and then I will stay quiet:

You are starting your Linux journey with an unbelievably good attitude. I wish more newbies would emulate you. You see, despite distro developers' efforts to wrap pretty dresses around Linux, at heart, it remains a geek's OS. It is so flexible and so powerful that words fail to convey its virtues, but it achieves these qualities at the unavoidable cost of obscurity and arcanery. If you approach these challenges with the attitude that you have displayed, then they will not overwhelm you. Too many approach these challenges in reverse: expecting a molly&#8209;coddled experience that won't subject them to any stress or learning curve. If they are very very lucky, they might get away with such expectations. More often than not, they get frustrated by the challenges and then blame the OS for their own unrealistic expectations.

Tackle this elephant one bite at a time and you will find it ultimately digestible. Your fearlessness in facing the command line is not only refreshing but inspiring.

Good Luck and Happy Ubuntu-ing!

---

### Post by TheFu on 2021-03-17
> **DuckHook said:**
> Malice is not tolerated on these forums and is dealt with quickly.

The moderation team here is probably the best on any forums I've seen. 
We are very lucky to have them. 
They do an amazing job of figuring out who is here for overall good of the community and provide a guiding hand to all, which is much appreciated.

---

### Post by red783 on 2021-03-22
So, really embarrassing story. I changed my password on the PC before I went to sleep a few nights ago, and when I tried to log in the next day, I couldn't remember the new password. So I had to reinstall the operating system. Haven't even tried to set up Thunderbird again yet. Got stuck on setting up ProtonVPN. I've posted in the security sub forum with the terminal display. If anyone can help it'd be much appreciated.

Thanks in advance
red7800

---

