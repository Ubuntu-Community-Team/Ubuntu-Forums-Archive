---
title: "question about safety"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by humansreplaceable on 2008-06-30
if I use the wubi thing and install ubuntu o half my computer.
will it still be safe to do online stuff with it, like paying the bank and such things?

also cant people hack in and destroy it or something?

what is best. having only linux or having both until im sure about linux?

does linux have viruses, trojans need firewalls and stuff like that?

thanks

---

### Post by avtolle on 2008-06-30
When ubuntu is running as a Wubi install, it is ubuntu (linux) running, not an emulator or a virtual machine. Thus, using it installed in that way is no different from using a "regular install" on a separate partition. Generally, linux doesn't have viruses, etc., due to how it performs. While a firewall is IMHO always good (one is native to Ubuntu, btw, and runs in the background), I suppose it can be said that in most cases, one may not really be needed.

As to having both or just one, I'd recommend having both a while; if installed under Windows using Wubi, you can get a feel for the system, how it works, etc., before partitioning and installing "permanently".

---

### Post by phidia on 2008-06-30
[This sticky]("http://ubuntuforums.org/showthread.php?t=765421") from the security forum might be good reading.
Generally linux is not as exposed to security issues as computers running windows but there are exceptions and even occasional exploits. 
Check out the link.

---

### Post by nowshining on 2008-06-30
yes I highly suggest a firewall. ubuntu comes with one - iptables - u just have to set it up - guarddog, firestarter or ur own script or a script in synaptic - arno-iptables-firewall.

---

### Post by humansreplaceable on 2008-07-01
hmmmmmmmm sounds very complicated.

can you please tell me step by step what i should do in order to be safe using ubuntu with a connection. would be great thanks man

---

### Post by mcduck on 2008-07-01
> **humansreplaceable said:**
> hmmmmmmmm sounds very complicated.

can you please tell me step by step what i should do in order to be safe using ubuntu with a connection. would be great thanks man

Nothing. Install all updates when they become available.

There is no need to worry about viruses or spyware. The default installation doesn't really even need a firewall, as there are no services running that would respond to incoming connections.

If you install any server software you should also install a firewall, Firestarter is probably the easiest for beginner (just install it with the package manager).

---

### Post by humansreplaceable on 2008-07-01
okay so i got two different answers. I need a firewall, and that I dont need a firewall. I haven read the url i got yet but will now.

so is it safe with a newly installed 8,04 to pay in the bank and order stuff online.

is it safer tan a regular pc with a firewall thats not so good+??

---

### Post by bred on 2008-07-01
[COLOR="Navy"]read carefully the thread posted by **phidia** or
 [http://www.psychocats.net/ubuntu/security]("http://www.psychocats.net/ubuntu/security")...
 
u have everything u want about the security...

In ubuntu u have no open ports on public interfaces...

a firewall u need if u want to open a port - like bittorent or whatever...

firestarter good for beginners...

 if u don not use that - just don't bother... 

u can pay the bank order stuff on line - it is secured.

good luck[/COLOR]

---

### Post by mcduck on 2008-07-01
No, the ports are not closed by default, and therefore you don't need a firewall to open them.

Like I said, the ports are all open, but there are no services listening to incoming connections.

You are safe with the default setup. If you want, you can install a firewall, but it won't make much of a difference.

---

### Post by forger on 2008-07-01
I would suggest automatic install for security updates:
System > Administration > Software Sources > Updates > Check for updates: Daily and Install security updates without confirmation. Also, make sure hardy-security and hardy-updates are checked (you don't need hardy-proposed or hardy-unsupported)

---

### Post by Sbarton on 2008-07-01
Whether you decide to use 8.04 (or any other) for your financial matters is up to you. Linux is pretty secure. the firewall is installed on OS install. Most professional sites have their own security for making /accepting payments. If you have'nt done so you can install Firestarter from synaptic which will install a GUI that you can use to observe/ manage your firewall.
regards

---

### Post by forger on 2008-07-01
And another thing:
Firefox add-ons are great:
Adblock plus: [https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)
Noscript: [https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)
[https://addons.mozilla.org/en-US/firefox/addon/3456](https://addons.mozilla.org/en-US/firefox/addon/3456)

With adblock you can disable ads (automatically if you register to a list for updates, I use the LIST FR + EasyList)
With noscript, you enable on which sites you want scripts (javascript or vbscript) to be enabled while loading the page - use with caution, only on trusted websites.
With wot, you can see if that page is good or not, the community of the wot plugin rate the website you currently visit.

---

### Post by billgoldberg on 2008-07-01
> **humansreplaceable said:**
> if I use the wubi thing and install ubuntu o half my computer.
will it still be safe to do online stuff with it, like paying the bank and such things?

also cant people hack in and destroy it or something?

what is best. having only linux or having both until im sure about linux?

does linux have viruses, trojans need firewalls and stuff like that?

thanks

1. Running Ubuntu using Wubi, is equally safe like running ubuntu the normal way.

2. People can hack into computers. On all operating systems. But it's not very likely they will.

3. I suggest you keep Windows for a while, until you are comfortable using Ubuntu.

4. Linux doesn't have any viruses (in the wild), nor trojans and other malware. 

If you are behind a hardware firewall (router) you don't really need a firewall. It can't hurt, but it's not necessary. 

If you connect to the internet using a modem, you'll need a firewall (try firestarter).

If you are wondering about defragging, this is not needed in Ubuntu.

*extra: check out my blog and the guides in my signature to help you getting started.*

---

### Post by brian_p on 2008-07-01
> **humansreplaceable said:**
> okay so i got two different answers. I need a firewall, and that I dont need a firewall. I haven read the url i got yet but will now.

It has been said in posts #6 and #9 but deserves your attention again: nothing can connect to your machine with a default install. A firewall adds nothing to that. It is a waste of time installing one.

> so is it safe with a newly installed 8,04 to pay in the bank and order stuff online.

Absolutely.

---

### Post by Mornedhel on 2008-07-01
There is a firewall anyway. Firestarter is simply a GUI interface to Netfilter. The iptables command is another, CLI-only interface that is already available.

Netfilter has been included with the standard kernel modules since 2.4 (at least).

---

### Post by billgoldberg on 2008-07-01
> **brian_p said:**
> It has been said in posts #6 and #9 but deserves your attention again: nothing can connect to your machine with a default install. A firewall adds nothing to that. It is a waste of time installing one.


Nothing can connect to your machine from a default install?

Don't think so.

If you're not behind a hardware firewall, you'll need a firewall.

---

### Post by brian_p on 2008-07-01
> **billgoldberg said:**
> Nothing can connect to your machine from a default install?

Don't think so.

If you're not behind a hardware firewall, you'll need a firewall.

You are going to have to name the service which can be connected to to back up your claim.

---

### Post by mcduck on 2008-07-01
> **Mornedhel said:**
> There is a firewall anyway. Firestarter is simply a GUI interface to Netfilter. The iptables command is another, CLI-only interface that is already available.

Netfilter has been included with the standard kernel modules since 2.4 (at least).

Sure, Netfilter/iptables is included in the kernel. But the thing about it is that by itself it does absolutely nothing. You need to give it rules to work with, or run a script or program that handles these rules.

So, it's wrong to assume that since netfilter/iptables is part of the kernel you'd already have a working firewall.

But, like I've already twice said in this thread, with no applications listening to incoming network traffic there is no need to limit the traffic with a firewall.

Somebody trying to attack the machine would be like somebody trying to yell commands to a deaf person. It makes no difference if there is a wall between the persons or not, the deaf guy still won't hear a thing. :D

---

### Post by Mornedhel on 2008-07-01
> **mcduck said:**
> So, it's wrong to assume that since netfilter/iptaböes is part of the kernel you's already have a working firewall.

Completely correct, however what I meant is that he does not need to *install* a firewall, he just needs to configure it. (Although iptables may be too much to handle for a beginner...)

---

### Post by humansreplaceable on 2008-07-01
okay great answers thanks. I wont need to install firestarter but do it anyway. that way im sure and Ive learned to sinstall something.

i didnt know i could use torrent programs on linux. what happen if i want to download stuff then. in whats ways might my computer be more or less open for something evil?

---

### Post by brian_p on 2008-07-01
> **humansreplaceable said:**
> okay great answers thanks. I wont need to install firestarter but do it anyway. that way im sure . . . 

That doesn't make sense. If you are sure you don't need a firewall you don't become surer by installing one. The country I live in is malaria free. I'm sure of that. Anyone advising me to use mosquito netting over my bed or to take anti-malarial drugs hasn't much to offer.

>  . . . and Ive learned to sinstall something.

There will be plenty of opportunities to install other more useful software.

> i didnt know i could use torrent programs on linux. what happen if i want to download stuff then. in whats ways might my computer be more or less open for something evil?

It won't be open to anything bad if you keep the software up to date. Of course, if you choose to install something you get from a torrent then you are responsible for any unforseen consequences.

---

### Post by forger on 2008-07-01
> **brian_p said:**
> The country I live in is malaria free. I'm sure of that. Anyone advising me to use mosquito netting over my bed or to take anti-malarial drugs hasn't much to offer.

Off the record, but never forget about people that come and go to tropical or developing countries, they get a shot *just in case* :) And believe me, the mosquitos could be passively transported to your country, through clothes, toys, jars.. anything.

That's how firewall works, *just in case* you get bitten by a mosquito, you are never sure.

---

### Post by brian_p on 2008-07-01
> **forger said:**
> That's how firewall works, *just in case* you get bitten by a mosquito, you are never sure.

humansreplaceable has a machine which has no open ports. There is nothing to fit 'just in case' so he can be certain he is safe.

---

