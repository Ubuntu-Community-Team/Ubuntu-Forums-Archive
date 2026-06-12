---
title: "Is my default firewall a) working b) adequate?"
date: 2013-12-16
forum: New to Ubuntu
---

### Post by Richard_York on 2013-12-16
Hi,
I've been running Ubuntu 12.04 as a non-geek, new Linux user for a couple of months now, a happy refugee from Windows, gradually finding out more, but mostly content to let the car run without looking into the engine.
I see from a Forum search here that there is an inbuilt firewall called iptables, and as I understand it from replies to a similar query there earlier, I probably don't need anything more to go with it, and that Firestarter is just a front end to configure it. I probably wouldn't understand what to do to configure it anyway  :-)
I did initially think "I need one of those" so installed Firestarter, but it claims it's not functioning anyway - the system log does not exist, it tells me.

I tried typing "iptables" into the dash search bar, and nothing comes up. Does this mean for some reason I haven't got the firewall & need to install something?

And if it is there, how do I get to see if it's working or not? Or is it just another bit of the engine I don't need to poke as long as it actually is there?

Would I do better to lose Firestarter?

Sorry, that's lots of questions, but they're all part of the same issue.

Thanks,
Richard.

---

### Post by oldos2er on 2013-12-16
Firestarter hasn't been maintained for several years, so I would "lose it" as you say. Try [gufw]("https://help.ubuntu.com/community/Gufw") instead.

---

### Post by Lars Noodén on 2013-12-16
+1 for gufw

If you want to look under the hood you can try reading about [iptables](http://manpages.ubuntu.com/manpages/trusty/en/man8/iptables.8.html) with [extensions](http://manpages.ubuntu.com/manpages/saucy/en/man8/iptables-extensions.8.html).  You can do a read-only dump of what you have like this:

```

sudo iptables -vL | less

```

or this

```

sudo iptables-save | less

```

But they may be hard to read, especially at first.  

For many tasks, gufw will do the job.

---

### Post by deadflowr on 2013-12-16
iptables is a cli program/thingy. 
The dash shows, for the most part, gui programs.
The dash shows applications which have a .desktop file.
iptables doesn't have one.

By default, Ubuntu comes with a firewall.It is installed but not enabled.
iptables is installed, but Ubuntu has another frontend for it called [ufw]("https://help.ubuntu.com/community/UFW")(another cli) installed as well.
Does that make sense to you.
To see if the firewall is enabled try this in a terminal
```
sudo ufw status
```
active = on
inactive=off

If you want a gui firewall program, gufw is probably the best thing right now.

---

### Post by Richard_York on 2013-12-16
Thanks all for these instant replies! Deadflowr, your line copied into the terminal shows it's active, which is very reassuring. 

I installed gufw, and its default appears to be off, and so it needs turning on each time the machine is switched on, by whichever of us is using it. This is liable to get forgotten, I suspect, so given that I honestly don't understand the options which configuring offers me - yes, I will do some reading! - it seems that perhaps I'm best not to use it, just to let the default one get on with it. Do you users of more experience than I, feel that this is protection enough?
Again, thanks,
Richard.

---

### Post by Lars Noodén on 2013-12-16
gufw is a graphical front-end for ufw, which is a text front end for iptables, which itself is also text.  UFW stays on once you turn it on, even if you used GUFW to do it, and even if the machine is rebooted.  So no need to remember it.  

A firewall, also called a packet filter, only selects which ports are accessible to the outside.  If you happen to have services running on the ports you open, such as SSH or Apache2, then those services will be available outside the machine.  If those services are secure then the ports you open are secure.   With more complex things like Wordpress and similar tools you start to get into a grey area.   That's from the server perspective, of course.  From the client perspective, you generally have permissive rules that allow clients to reach out through the firewall and connect to remote machines.  There you might be more effective looking at AppArmor to restrict what the client program can access while running.  However that can get fairly detailed.  I'm not sure but I think there is no simple graphical tool to work with AppArmor.

---

### Post by Richard_York on 2013-12-16
Thanks Lars.
After a quick "introduction to" query on the net - I really am ignorant, as soon as any abbreviations or acronyms get into the conversation! -  I realise we probably inevitably use SSH, inasmuch as we buy things online. We always check they're secure sites, so I hope that covers security there.
I'm not aware that I use Wordpress, since we don't do blogging.
 I'm interpreting your answer to suggest that I simply let it get on with it by itself for now, at least!
Thanks again,
Richard.

---

### Post by Lars Noodén on 2013-12-16
SSH would be if you are logging in to your own machine from other machines, maybe from on the LAN maybe from out on the net.  So you only need to open up ports if you do that, or if you are serving web pages from your computer.  So if it is just a desktop machine, the defaults are fine.

One thing that you might tweak, and it is easy to do so, is to change the default in GUFW from deny to reject.  There are a number of reasons to do that, but it's up to how you want it.
[http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)

---

### Post by Richard_York on 2013-12-16
Done :-)

---

### Post by PaulBx on 2013-12-16
> There are a number of reasons to do that, but it's up to how you want it.

Well, there is actually a lot of controversy about this point.

For example, in the article Lars posted we see the statement:
> The only time nothing is returned consistently is when a firewall with a  drop rule is in the way. So by dropping traffic you are not stealthing  the firewall, you are advertising it.

Unless I am mistaken, this statement is incorrect. Nothing is returned if EITHER a firewall with a drop rule is in the way, OR there is nothing at all there. And there is no way the port scanner can tell the difference. Now of course there might be firewalls further upstream that return something, but that does not help the port scanner make the determination if his intended target exists or not.

The point about syn floods is interesting, but the server is no better off it the spoofed address is nonexistent or offline. In fact the attacker would probably take care to spoof a nonexistent address, if he has any sense, because then he is certain nothing will be returned to the server. Anyway it's the server's problem to deal with such attacks and I suspect there are plenty of tools out there for it to do so.

Anyway if you are behind a router you don't need a firewall because the router has one. Well, that was the old answer. These days with NSA compromising routers with old firmware, it probably makes a lot of sense to run firewalls in your private network machines.

Disclaimer: I do not claim to be any kind of expert. I just question things.

---

### Post by Lars Noodén on 2013-12-16
PaulBx, here's one from a slightly different angle:

[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)

For LAN use, reject is the way to go.  At the least, it saves waiting for timeouts and wear and tear on legitimate users.

---

### Post by PaulBx on 2013-12-19
From that article:
> Hiding information about which ports are active requires making     the server response indentical whether or not it offers a     particular service.

He is writing from the point of view of someone with a server on the internet (a tiny minority of Internet users). In that case it may well make lots of sense to REJECT. The same considerations may not apply to those who are not offering a service, or those in whose computers ports are left open by default for no good reason.

He talks about "legitimate users". If I'm not mistaken, there are no legitimate users banging away on my ports. And, for the hostile ones, since they are using a specialist program to scan, all this talk about how long it takes TCP to time out is irrelevant.

When I see firewall software not offering the choice of DROP, then I guess I will stop DROPPING. Until then I see no need to respond to hostile users, letting them know there is something to attack at that address.

---

### Post by Lars Noodén on 2013-12-19
Re-read both pages, using drop does not hide the firewall from anyone.  Also your main users are going to going to be legitmate.  Using reject helps them, which is the main benefit as far as daily use goes.

---

### Post by PaulBx on 2013-12-19
OK, using drop does not hide anyone - although there are more reasons no response comes back, than just that there is a dropping firewall somewhere in the path. But yeah, there are a lot of inflated claims about stealth. Just as there are about reject. Both do the job, each has some good and bad characteristics.

As to my users, that depends on who you are talking about. Me, as an end user? I have no users. The only people banging on my ports are probably script kiddies who will move on whether DROP or REJECT are used. Me, as a home router firewall administrator? DROP might make a little more sense on the WAN, probably doesn't matter either way on the LAN - unless I have one infected windows machine trying to infect another? Me, as a corporate router firewall administrator? Now REJECT makes more sense, certainly on the LAN, probably on the WAN too because I have stuff like snort and other tools backing me up.

Mostly this sounds like something pointless to argue over. :)

---

### Post by Lars Noodén on 2013-12-19
Why stop at half measures then like drop then?  :) You could always compile [tarpit](http://www.netfilter.org/projects/patch-o-matic/pom-external.html) back into the kernel. It should be in [xtables-addons-common](http://packages.ubuntu.com/saucy/xtables-addons-common).  However, timeouts are unlikely to affect most hostile scanners.

---

### Post by PaulBx on 2013-12-19
Yes, tar pits sound like fun, for a nerd anyway. I think I will go out shooting today, heh.

This discussion was entertaining, particularly on page 4.
[http://www.dslreports.com/forum/r17079148-Place-your-bets-Closed-vs-Stealthed~start=90](http://www.dslreports.com/forum/r17079148-Place-your-bets-Closed-vs-Stealthed~start=90)

To be honest, after reading all that stuff I could go either way. There are other security topics a little more urgent. I just took a look at apparmor and that too appears to be a good way to waste time, if you have to write profiles. I hope someone else does that work for me in the next upgrade or two. Seamonkey profile, anyone?

---

