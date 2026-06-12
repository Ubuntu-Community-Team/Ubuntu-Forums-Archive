---
title: "firewall question"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by mrmgh1 on 2008-09-03
I am realy new to this and dont understand any of the technical stuff I See in response to questions about firewalls etc. 
I have firestarter installed,  - but IM not sure its working for me properly. Should I need to enter my password in order to run firewall when IM online or should it start up automatically ?
 I then want to set up a second user id on the pc for my daughter who is nervous about 2breaking the computer"   but when I try to go onlin and start firestarter IM asked for my password and then told I cant run it from root ?
As I said im lost and want to know if im protected or not... 

How do I set it up to run firewall at start up , and to run when daughter logs in rather than me ?
Please don't fill response with technical stuff or smart comments like if you dont understand go back to windows. I want to learn but need the explanations to make sens e

Thanks in advance..

---

### Post by oilchangeguy on 2008-09-03
you don't need firestarter. it's simply a gui for the already installed iptables. for most users there's no need to change iptables settings.

---

### Post by Vivaldi Gloria on 2008-09-03
Are you sure you need a firewall?

No need for a firewall in the default ubuntu desktop because there are no servers listening to any ports.

---

### Post by mrmgh1 on 2008-09-03
Thanks. but , 
So do I have any firewall protection then ?  My understanding was that firestarter was / is the firewall ?  I assume from your response that thi sis not the case ?

And to prove my ignorance what s a GUI ?

---

### Post by oilchangeguy on 2008-09-03
> **mrmgh1 said:**
> Thanks. but , 
So do I have any firewall protection then ?  My understanding was that firestarter was / is the firewall ?  I assume from your response that thi sis not the case ?

And to prove my ignorance what s a GUI ?

graphic user interface

---

### Post by Vivaldi Gloria on 2008-09-03
Ubuntu comes with the firewall called iptables. Since it's a bit hard to configure some prefer using frontends to it like ufw, firestarter etc.

For iptables see

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

In the default install iptables is not working. 

No need for a firewall in default ubuntu install because there are no programs listening to any ports. So if a packet comes to your ubuntu box then it is just ignored because there's no program listening to the port that the packet arrives to.

---

### Post by oilchangeguy on 2008-09-03
> **Vivaldi Gloria said:**
> Ubuntu comes with the firewall called iptables. Since it's a bit hard to configure some prefer using frontends to it like ufw, firestarter etc.

For iptables see

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

In the default install iptables is not working. 

No need for a firewall in default ubuntu install because there are no programs listening to any ports. So if a packet comes to your ubuntu box then it is just ignored because there's no program listening to the port that the packet arrives to.

where do you get your information? "In the default install iptables is not working" this is wrong. take a look at the link you provided, and show us where is says to start iptables do this... it does say how to disable it.

---

### Post by mrmgh1 on 2008-09-03
I think im confused. All the advice ref nternet I have aver heard advises firewalls  yet it sem sI DOnt ned one. This being the cas and in light of the rest of your answer, how com when I look at the events log in firestarter it lists a load of events on variuos ports this evening ? 
As i said im nw to this, so bear with me if my questions are verging on stupid.

---

### Post by oilchangeguy on 2008-09-03
> **mrmgh1 said:**
> I think im confused. All the advice ref nternet I have aver heard advises firewalls  yet it sem sI DOnt ned one. This being the cas and in light of the rest of your answer, how com when I look at the events log in firestarter it lists a load of events on variuos ports this evening ? 
As i said im nw to this, so bear with me if my questions are verging on stupid.

ok, bottom line is this. ubuntu already has a firewall. it's iptables. if you want to play with it you need to install firestarter (you don't need to play with it). and if you're behind a router you get an extra layer of protection, it acts as a firewall also.

---

### Post by oldos2er on 2008-09-03
> **mrmgh1 said:**
> I think im confused. All the advice ref nternet I have aver heard advises firewalls  yet it sem sI DOnt ned one. This being the cas and in light of the rest of your answer, how com when I look at the events log in firestarter it lists a load of events on variuos ports this evening ? 
As i said im nw to this, so bear with me if my questions are verging on stupid.

 You might want to read [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by Vivaldi Gloria on 2008-09-03
> **oilchangeguy said:**
> where do you get your information? "In the default install iptables is not working" this is wrong. take a look at the link you provided, and show us where is says to start iptables do this... it does say how to disable it.

I was talking in layman's terms. Better is: there are no rules as you can check from

```
sudo iptables -L
```

---

### Post by oilchangeguy on 2008-09-03
> **oldos2er said:**
> You might want to read [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

you might want to consider reading the entire post, before you post. that link has already been provided, by another poster.

---

### Post by Vivaldi Gloria on 2008-09-03
> **oilchangeguy said:**
> ok, bottom line is this. ubuntu already has a firewall. it's iptables. if you want to play with it you need to install firestarter (you don't need to play with it). and if you're behind a router you get an extra layer of protection, it acts as a firewall also.

I suggest not to use firestarter. It's dead. The last update was in 2005. The developers are not working on it anymore. It hasn't been updated to reflect the latest libraries for Gnome and other fundamental iptables changes in newer kernels. It crashes and screws up some systems.

ubuntu comes with ufw. See

```
man ufw 
```

for more info. See especially the examples section.

---

### Post by oilchangeguy on 2008-09-03
> **Vivaldi Gloria said:**
> I suggest not to use firestarter. It's dead. The last update was in 2005. The developers are not working on it anymore. It hasn't been updated to reflect the latest libraries for Gnome and other fundamental iptables changes in newer kernels. It crashes and screws up some systems.

ubuntu comes with ufw. See

```
man ufw 
```

for more info. See especially the examples section.

re-read the post. i'm not suggesting using firestarter. 
can moderator please close this post? the op's question has been answered, and understood by the op.

---

### Post by Vivaldi Gloria on 2008-09-03
> **oilchangeguy said:**
> re-read the post. i'm not suggesting using firestarter. 

??

Did I say you suggested such a thing?

> can moderator please close this post? the op's question has been answered, and understood by the op.

No. I have more info to give. What's the rush?

---

### Post by mrmgh1 on 2008-09-03
> **oldos2er said:**
> You might want to read [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Sorry , i dont understand what this is telling me at all. I've tried the first thing it says , and get a totally different result to udo iptables -L, to that which  the info says I will . 
I guess what I need to know first is do I have the protection of a firewall of any sort on my pc, I have no idea how to see if the "default " firewall is running. 
Iv etried code ufw, as above and it says "udo iptables -L"   is thsi wrong / a problem ?

I Am now also getting what I feared , various people trying to help but contradicting each other.

---

### Post by oldsoundguy on 2008-09-03
and add .. if you are on a home network, another "no need for a resident firewall" reason, as your router/hub has one (if you keep it updated.) .... but you may need that individual firewall if you are SHARING a network to keep others on the net at bay!

No harm or issue with installing the resident firewall and really no need to "maintain" it as your updates will take care of that.

---

### Post by mrmgh1 on 2008-09-03
OK , I suppose what would be most helpful to me here would be if I could get a definitive answer to 

if UFW is installed by default how do I tell if its running ? without starting firestarter and looking at events etc ?
Id be happy to start with if I knew I was protected from "what might b eout there"

Again thanks to all for trying to help ..

---

### Post by Vivaldi Gloria on 2008-09-03
> **mrmgh1 said:**
> if UFW is installed by default how do I tell if its running ? 

Yes. Try

```
sudo ufw status
```

See

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

> Id be happy to start with if I knew I was protected from "what might b eout there"

Yes. Let me explain in another way. What happens if I send a malicious packet to your computer? In order for it to damage there must be someone to accept it. But in the default install there is no app listening to any ports - no one accepts any packets. So it is as secure as it can be. 

There is no difference whether it's no app listening or you use a firewall to drop the packet. The packet reaches to no app anyway. Hence in the default ubuntu install you don't need to bother with a firewall as no packet reaches an app. But of course it wouldn't do any harm if you added any iptables rules either (say by ufw).

---

### Post by bodhi.zazen on 2008-09-03
I think the best question is to ask yourself, what do you want a firewall to do for you ?

This is a recurring question on these forums and sometimes these threads are heavy on opinions and light on factual content ;)

At any rate, you *might* want to look here :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

In terms of a firewall ... Ubuntu is not windows, so with a default installation of Ubuntu there are no open ports, there is nothing to firewall. Windows needs a firewall because with a default install there are open ports.

You open a port by installing a server. So if you are running a server you might be interested in a firewall. You can also use a firewall to block script kiddies (no reason not to block those pesky attempt to crack your box).

At any rate, to answer your question, the firewall is called iptables. Iptables is difficult for new users to learn, thus UFW (Uncomplicated Fire Wall). It is a command line tool as well, although there is a gui as well :

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

GUI (gufw): [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

If you are paranoid, go for snort + ossec (or similar)

---

### Post by mike555 on 2008-09-03
You might just get this, it works good .....   [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

### Post by Daveski on 2008-09-03
> **mrmgh1 said:**
> OK , I suppose what would be most helpful to me here would be if I could get a definitive answer to 

if UFW is installed by default how do I tell if its running ? without starting firestarter and looking at events etc ?
Id be happy to start with if I knew I was protected from "what might b eout there"

Simple answer is that a default install of Ubuntu is effectively firewalled. Firestarter and UFW are really interfaces to MODIFY the standard firewall rules, and unless you know a little about what you are doing (I am not suggesting that you don't) then you should ignore them until you understand a bit more about what the 'built-in' iptables rules do.

The firewall is not really something that runs in the sense that a firewall application as part of an internet security suite in Windows does. It is a list of rules that the Linux networking subsystem uses to work out what to do with incoming and outgoing network packets. The default rule is to allow any outgoing communication, but to drop (ignore) any incoming.

Using a GUI such as Firestarter and UFW allow you modify these rules to open up (make the firewalling less restrictive) - which is why I suggest you ignore them for now.

---

### Post by bodhi.zazen on 2008-09-03
> **Daveski said:**
> Simple answer is that a default install of Ubuntu is effectively firewalled. Firestarter and UFW are really interfaces to MODIFY the standard firewall rules, and unless you know a little about what you are doing (I am not suggesting that you don't) then you should ignore them until you understand a bit more about what the 'built-in' iptables rules do.

The firewall is not really something that runs in the sense that a firewall application as part of an internet security suite in Windows does. It is a list of rules that the Linux networking subsystem uses to work out what to do with incoming and outgoing network packets. The default rule is to allow any outgoing communication, but to drop (ignore) any incoming.

Using a GUI such as Firestarter and UFW allow you modify these rules to open up (make the firewalling less restrictive) - which is why I suggest you ignore them for now.

What you say about the default firewall setting is not true. By default iptables is inactive or permissive of all connections. This is acceptable as there are no servers installed so the ports are closed.

To see your IPtables rules,

```
sudo iptables -L
```> bodhi@hardy:~$ sudo iptables -L
[sudo] password for bodhi:
Chain INPUT (**[COLOR=green]policy ACCEPT[/COLOR]**)
target     prot opt source               destination

Chain FORWARD (**[COLOR=green]policy ACCEPT[/COLOR]**)
target     prot opt source               destination

Chain OUTPUT (**[COLOR=green]policy ACCEPT[/COLOR]**)
target     prot opt source               destinationie the ports are closed because there is no server listening, not because they are fire walled.

---

