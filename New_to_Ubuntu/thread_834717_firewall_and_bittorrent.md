---
title: "firewall and bittorrent"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by subfactors on 2008-06-19
If I use bittorrent, do I need a firewall and open up certain port in ubuntu 8.04? If so, can anyone please let me know how to do it or point me to some references?

Thanks.

---

### Post by mivo on 2008-06-19
Ubuntu doesn't come with an activated firewall/rules, as far as I can tell.

---

### Post by tjwoosta on 2008-06-19
ubuntu comes with a firewall, you have to downoad firestarter from synatic in order to configure your firewall (if needed)

although, the ubuntu firewall should by default not affect bittorrent

one thing that does affect bittorrent sometimes is your routers firewall (if your behind a router)

if that was the case you would need to forward the ports to ubuntu

---

### Post by subfactors on 2008-06-19
The thing that bothers me is my bittorrent client (deluge as you already know) works perfect after I did the port forwarding on the router. Since I didn't set up anything on my computer, it just make me feel like my computer is open to the world without any protection.
Am I thinking it right?

---

### Post by mivo on 2008-06-19
Well, like I said, there is no activated firewall out of the box (you need to add rules for it to do something). It does come with UFW (new in Hardy, I believe), but it is not enabled. Personally, I have my router do the firewalling, so all of my computers behind it are protected. If you want to enable and set up UFW, [see here for information and help]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw").

---

### Post by subfactors on 2008-06-19
sorry if i confused you in the last posts. My question is really this:

Is a firewall needed for security reason if I do bittorrent on ubuntu?

---

### Post by tjwoosta on 2008-06-19
simple answer: not if your protected by your routers firewall

---

### Post by mivo on 2008-06-19
Tricky question. Can you be too safe? I'm tempted to say that no, you don't need one, unless you install any services that answer to anything that "calls in". For example, if you install an SSH server (or really any server), you really want to either lock it down very well, or run a firewall, or both. There are some web sites where you can test how secure your machine is, as seen from the outside.

---

### Post by hopelessone on 2008-06-19
Firewall is not needed 

I too asked a while ago and heres what i remember:
1. all port are closed automatically
2. you password is your strength
3. all ports are opened by the operating system

i havent had any probs...for 1 year 

Hope that helps..

---

### Post by sifon187 on 2008-06-19
I have been torrenting for years with no problems. I have multiple ports forwarded on my router, there is no worry of someone getting through.

---

### Post by subfactors on 2008-06-19
Just wondering, how come the bittorrent content can get to my computer while other bad stuff can't? I thought that's the point of firewall. Am I wrong?

---

### Post by kansasnoob on 2008-06-19
> **mivo said:**
> Well, like I said, there is no activated firewall out of the box (you need to add rules for it to do something). It does come with UFW (new in Hardy, I believe), but it is not enabled. Personally, I have my router do the firewalling, so all of my computers behind it are protected. If you want to enable and set up UFW, [see here for information and help]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw").

I don't believe that's true, or I at least hope not. My understanding is that iptables is "running" out of the box, and ufw need only be enabled if one wishes to make adjustments (open ports, create an activity log, etc).

But as my moniker indicates I'm a nOOb! But I went into this hot and heavy, and emerged reassured that we are protected "out of the box".

[http://ubuntuforums.org/showthread.php?t=765410](http://ubuntuforums.org/showthread.php?t=765410)

If you want to be certain just:

```
sudo ufw enable
```

---

### Post by mivo on 2008-06-19
That's like asking why you can download files from a web site. :) You establish connections with other people and exchange data packages with them. There is nothing bad or really dangerous about this (in a technical way). They cannot remotely log into your computer (that would require you to install a SSH server, for example) or access any stuff besides what the BT client is offering.

Doesn't your router have some protections enabled by default? I think almost all routers do that. I'd feel a bit naked without any protection at all, though the danger's low, in my opinion (it's all subjective -- if in doubt always go for extra safety).

---

### Post by mivo on 2008-06-19
> **kansasnoob said:**
> I don't believe that's true, or I at least hope not. My understanding is that iptables is "running" out of the box...

With no rules. :) You can check it on a default installation. It's been a controversial topic for some time. See also in the [official documentation here]("https://help.ubuntu.com/community/IptablesHowTo") where it states that "*it allows all traffic by default*".

---

### Post by kansasnoob on 2008-06-19
[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by kansasnoob on 2008-06-19
> **mivo said:**
> With no rules. :) You can check it on a default installation. It's been a controversial topic for some time. See also in the [official documentation here]("https://help.ubuntu.com/community/IptablesHowTo") where it states that "*it allows all traffic by default*".

So does

```
sudo ufw enable
```

do anything?

---

### Post by RomeReactor on 2008-06-19
Hi. As far as I know, the ports are closed by default, and only open when a program requests it. This works from your computer to the outside, but not the other way around. Take look at [this post from 23meg]("http://ubuntuforums.org/showpost.php?p=605996&postcount=3"), or for a more in-depth explanation follow the excellent link posted by kansasnoob.

If you want to see which ports are open now, try going to [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2").

---

### Post by kansasnoob on 2008-06-19
Just for fun I installed and started the Firestarter gui (NOTE: that is only a front-end to iptables and I adjusted nothing!) and I did a little surfing after entering the command "sudo ufw enable" and a little more after "sudo ufw disable" and there IS a little activity both ways:

[ATTACH]74684[/ATTACH]

The first two entries are with ufw enabled and the second two are with ufw disabled, so iptables is doing something.

---

