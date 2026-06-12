---
title: "[SOLVED] Do I really need a software firewall?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-07-12
All of my computers are connected to a router with a built in firewall.  Should I be running a software firewall as well?

Thanks!

---

### Post by Thee_Baron_ on 2008-07-12
Unless you want to control what applications connect to then I would say no.

---

### Post by mriedel on 2008-07-12
> **Thee_Baron_ said:**
> Unless you want to control what applications connect to then I would say no.

And if you want to do that, there's still no linux software firewall that can do that properly, although the dire need exists :P

On Windows: Yes, you definitely need a personal firewall to keep microsoft and other closed source companies from spying on you.

---

### Post by Hendrixski on 2008-07-12
Linux has a firewall built into it's kernel.

If you want to manage it just install firestarter or one of those apps, and it'll give you the administrative interface.

If you're on a network that has both windows and Linux computers then you DO need a firewall on your linux machines because they can be used to spread stuff through the network which will make the windows machines crap themselves.

---

### Post by mriedel on 2008-07-12
> **Hendrixski said:**
> Linux has a firewall built into it's kernel.

If you want to manage it just install firestarter or one of those apps, and it'll give you the administrative interface.

iptables/netfilter can't handle per-process policies and are therefore useless when trying to stop close source apps from spying on you.

> **Hendrixski said:**
> If you're on a network that has both windows and Linux computers then you DO need a firewall on your linux machines because they can be used to spread stuff through the network which will make the windows machines crap themselves.

Would you care to elaborate?

---

### Post by hyper_ch on 2008-07-12
you don't need to worry about a firewill unless
(1) you install server services
(2) want also to "protect" those services in your lan

otherwise your router will do fine.

---

### Post by mdsmedia on 2008-07-12
> **mriedel said:**
> And if you want to do that, there's still no linux software firewall that can do that properly, although the dire need exists :P
IPTables is installed in Ubuntu by default......if you want GUI control of IPTables, install FireStarter, or any other GUI app others recommend to control IPTables. If this is "there's still no linux software firewall that can do that properly" I'm sure I don't know what Windows has to offer.
> On Windows: Yes, you definitely need a personal firewall to keep microsoft and other closed source companies from spying on you.No you don't "definitely" need a software firewall in Windows but I always use one.

---

### Post by pi.boy.travis on 2008-07-12
Thanks!

I'm not running any server services and all of my computers are running Ubuntu.

It's nice not to have worry about such things anymore. . .

---

### Post by mriedel on 2008-07-12
> **mdsmedia said:**
> IPTables is installed in Ubuntu by default......if you want GUI control of IPTables, install FireStarter, or any other GUI app others recommend to co control IPTables. If this is "there's still no linux software firewall that can do that properly" I'm sure I don't know what Windows has to offer.

As I said above, iptables/netfilter doesn't support per-process policies, which constitute the essence of what most windows firewalls do. All iptables/netfilter does is allowing/denying connections on a per-port basis. For any PC connected to the internet, you want to open at least a few outbound ports (in order to be able to access the internet...). A single one is enough to allow for a sneaky application to get data out of your system.

> No you don't "definitely" need a software firewall in Windows but I always use one.

That depends on your definition of "need". You don't need doors if you don't mind people coming into your house as they please.

---

### Post by coolaj86 on 2008-07-12
[SIZE="5"]**Why would you *not* install a firewall?**
[/SIZE]

It's kinda like saying: Do I really need to wear a seatbelt?

Well, no. Not really. But... on the off chance that anything bad happens you'll be glad you did.

Linux isn't impervious, it's just really really good.
... and obscure.

BTW, if you leave your username and password set to 'admin' and '' on a regular home router some websites you visit can log in and change the settings. See this [Google Tech Talk]("http://www.youtube.com/watch?v=jC6Q1uCnbMo&feature=user") (it talks about it somewhere after the 25 minute marker)

And if you use ssh at all you should get fail2ban which blocks bot attempts to log into your system (which is happening all day long every day if you have the port open on your firewall). ```
sudo apt-get fail2ban
```

---

