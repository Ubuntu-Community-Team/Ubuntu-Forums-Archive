---
title: "Getting worried now"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by colcol on 2008-11-03
hi all this is a link to a scan idid with gibsons research company it checks security of pc using the shields up option when i did it on windows my pc passed with flying colours but now on ubuntu it failed is ubuntu as secure as made out to be im worried now anyone can just hack into my pc

[tps://www.grc.com/x/ne.dll?rh1dkyd2]("https://www.grc.com/x/ne.dll?rh1dkyd2")

---

### Post by OldTimeTech on 2008-11-03
Be aware that Shields Up is for Windows only...not for Linux.

Second you have an automatic firewall when you boot into linux as it uses iptables and has already been configured to put a firewall there...if you would like to make changes to these iptables...you can use Firestarter which will give you a gui or you can learn how to work and setup iptables...many explanations on the net, just google.

---

### Post by Tom--d on 2008-11-03
> **OldTimeTech said:**
> Be aware that Shields Up is for Windows only...not for Linux.

Second you have an automatic firewall when you boot into linux as it uses iptables and has already been configured to put a firewall there...if you would like to make changes to these iptables...you can use Firestarter which will give you a gui or you can learn how to work and setup iptables...many explanations on the net, just google.


You dont need a firewall until you start installing server software (etc).

Also, Firestarter should be removed from the repo's due to its dead and out dated. Hasn't been updated for many years now.
If you want a firewall, use UFW.
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)
[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)
GUI for it: In the repos in Intrepid. For hardy: [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

### Post by gandaran on 2008-11-03
all ports are open by default in ubuntu, but you don't have to worry about that, if you want to change things install a gui/frontend for the firewall
try a very simple one to set up **gufw**, find it in synaptic if you are on intrepid, for hardy download here [http://gufw.tuxfamily.org](http://gufw.tuxfamily.org)

---

### Post by chippy57 on 2008-11-03
> **OldTimeTech said:**
> Be aware that Shields Up is for Windows only...not for Linux.

I am new to Ubuntu just installed 8.10, I tried GRC. All ports are stealth according to them. However, I presume its because I'm behind a NAT router.

Does this mean I dont really need to install a software firewall?

Excuse the ignorance.

chip

---

### Post by skiddly on 2008-11-03
> **Tom--d said:**
> You dont need a firewall until you start installing server software (etc).

Also, Firestarter should be removed from the repo's due to its dead and out dated. Hasn't been updated for many years now.
If you want a firewall, use UFW.
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)
[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)
GUI for it: In the repos in Intrepid. For hardy: [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

i am just using my pc with 2 external hard drives,so are you saying i should be ok :confused:if only installing stuff was easier for us newbies lol

---

### Post by aportier on 2008-11-03
> **chippy57 said:**
> I am new to Ubuntu just installed 8.10, I tried GRC. All ports are stealth according to them. However, I presume its because I'm behind a NAT router.

Does this mean I dont really need to install a software firewall?

Excuse the ignorance.

chip

Unless you have set up some sort of port forwarding on your router, your local IP should not be visible to the Internet on the ports you scanned. No need for a local firewall unless you need to reach a port on your computer from the Internet (like if you are running a server), or you are connected directly to a line without using a switch.

---

### Post by phr0ze on 2008-11-03
GRC should not care if its windows or linux. The test should be accurate for any OS. If GRC says linux ports are exposed in some way, then they are.

However I always recommend that you plug a router between you and the internet just for the layer of protection the NAT will provide.

---

### Post by colcol on 2008-11-03
> **phr0ze said:**
> GRC should not care if its windows or linux. The test should be accurate for any OS. If GRC says linux ports are exposed in some way, then they are.

However I always recommend that you plug a router between you and the internet just for the layer of protection the NAT will provide.

Thanks for the advice ive never used a router so how would i set it up and sorry to be totaly nymb but i need to buy a router from somewhere and place it between cable modem and pc tower is that right

---

### Post by handydan918 on 2008-11-03
> **colcol said:**
> Thanks for the advice ive never used a router so how would i set it up and sorry to be totaly nymb but i need to buy a router from somewhere and place it between cable modem and pc tower is that right

Yep. Shouldn't cost much more than 50 usd for a good router. Just steer clear of the 802.11"N" specification for now.

---

### Post by brian_p on 2008-11-03
> **colcol said:**
> hi all this is a link to a scan idid with gibsons research company it checks security of pc using the shields up option when i did it on windows my pc passed with flying colours but now on ubuntu it failed is ubuntu as secure as made out to be im worried now anyone can just hack into my pc

[tps://www.grc.com/x/ne.dll?rh1dkyd2]("https://www.grc.com/x/ne.dll?rh1dkyd2")

GRC has a strange and misleading view of what is secure and insecure. It's use of 'failed' to categorise a scan of your machine is intended to produce fear. Unfortunately, it succeeds in many cases.

There is no picture of a scan at the link you give so it might not be a bad idea to describe here what GRC tells you. One of the so-called failures is bound to be that your pc responded to ping. You'll be fed some nonsense about how dangerous that is.

Your Ubuntu install will not allow any access to the pc in its default state. You can be absolutely sure no one can hack into it. Purchasing a router will reduce your bank balance without increasing the pc's security.

---

### Post by chippy57 on 2008-11-03
> **aportier said:**
> Unless you have set up some sort of port forwarding on your router, your local IP should not be visible to the Internet on the ports you scanned. No need for a local firewall unless you need to reach a port on your computer from the Internet (like if you are running a server), or you are connected directly to a line without using a switch.

No...Nothing like that ATM anyway. The NAT is pretty effective would never go on the net without being behind one.

---

### Post by handydan918 on 2008-11-03
> **brian_p said:**
> 

Your Ubuntu install will not allow any access to the pc in its default state. You can be absolutely sure no one can hack into it. Purchasing a router will reduce your bank balance without increasing the pc's security.

Quite a bold set of assertions. Most of the best security researchers out there would disagree with your statement in regard to the router, for sure, and very likely you would find a few to argue about > You can be absolutely sure no one can hack into it.
Perhaps you'd care to justify this unsupported confidence you seem to exude?

---

### Post by Greyed on 2008-11-03
Yeah, this site's a joke.  Look at the result of my scan:
[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][COLOR=#000066][FONT=courier new,courier][SIZE=3][COLOR=black]```

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

```

It is promoting security through obscurity.  The funny part is that it listed about 1/2 my ports as "open" even though they were forwarded to dead IP.  And, oh noes, I answer to PING!  

FUD, pure and simple.
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by brian_p on 2008-11-04
> **handydan918 said:**
> 
 
Perhaps you'd care to justify this unsupported confidence you seem to exude?

I did justify it. The default install of Ubuntu has no services open to the internet so any attempted connection with the purpose of getting access to the machine is rejected. Inserting a router doesn't alter that fact. My confidence would be shaken if a description of how an intrusion could take place was available.

---

### Post by Greyed on 2008-11-04
> **brian_p said:**
> I did justify it. The default install of Ubuntu has no services open to the internet

*cough*

```

{grey@morpheus:~} nmap 192.168.1.102

Starting Nmap 4.53 ( http://insecure.org ) at 2008-11-04 02:21 PST
Interesting ports on 192.168.1.102:
Not shown: 1712 closed ports
PORT     STATE SERVICE
111/tcp  open  rpcbind
2049/tcp open  nfs

Nmap done: 1 IP address (1 host up) scanned in 22.602 seconds

```

192.168.1.102 is an 8.04 install with no added services.  2 open ports found.

---

### Post by brian_p on 2008-11-04
> **Greyed said:**
> *cough*

Hi there.

> 
```

{grey@morpheus:~} nmap 192.168.1.102

Starting Nmap 4.53 ( http://insecure.org ) at 2008-11-04 02:21 PST
Interesting ports on 192.168.1.102:
Not shown: 1712 closed ports
PORT     STATE SERVICE
111/tcp  open  rpcbind
2049/tcp open  nfs

Nmap done: 1 IP address (1 host up) scanned in 22.602 seconds

```

192.168.1.102 is an 8.04 install with no added services.  2 open ports found.

Firstly: I have an untouched 8.04 install on one partition. Neither of these ports shows up with nmap.

Secondly: ubuntu-8.04.1-desktop-i386.iso does not contain nfs-common, which depends on portmap, so neither of these services would be on a default install.

[http://ubuntu.positive-internet.com/releases/hardy/ubuntu-8.04.1-desktop-i386.manifest](http://ubuntu.positive-internet.com/releases/hardy/ubuntu-8.04.1-desktop-i386.manifest)

Thirdly: A default install should show

```
631/tcp  open  ipp
```

because the printing service is enabled locally.

I'd conclude you have added (and removed) services.

Incidentally, the nmap output does not indicate whether your rpcbind and nfs are visible from the internet or just local services.

---

### Post by Greyed on 2008-11-04
Er, that view is from outside the machine, not locally, so yes, it does indicate if it would be visible to the outside world.  You don't think I'd run nmap locally to test what is visible from remote, do you?  ;)

I don't recall adding nfs to this machine though, frankly, it isn't that uncommon a thing to want.

---

### Post by brian_p on 2008-11-04
> **Greyed said:**
> Er, that view is from outside the machine, not locally, so yes, it does indicate if it would be visible to the outside world.  You don't think I'd run nmap locally to test what is visible from remote, do you?  ;)

```
nmap 192.168.1.102
```

I'd assumed 192.168.1.102 had been scanned from another machine on the same network. However, I got a little carried away with the soundness of my first two points and produced an incorrect third one.

> I don't recall adding nfs to this machine though, frankly, it isn't that uncommon a thing to want.

Without nfs there would be a blank nmap output. Which substantiates my original claim.

---

