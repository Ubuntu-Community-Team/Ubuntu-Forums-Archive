---
title: "Firestarter is the standard firewall in Debian"
date: 2009-06-06
forum: Recurring Discussions
---

### Post by OrangeCrate on 2009-06-06
> **bodhi.zazen said:**
> FYI: The firewall in linux , all modern versions, is iptables. iptables is not a service, it is a kernel module.

The start scripts in RHEL, Fedora, OpenSUSE, these do not start a service, they are bash scripts to configure the firewall.

Ubuntu used ufw, the gui front end is gufw.

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

Firestarter is no longer maintained and there can be conflicts with it and ufw.

If you want to know how iptables works, I wrote a primer

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

His question was regarding Debian, not Ubuntu.

Though ufw might be the "standard" for Ubuntu, Firestarter is still the standard for Debian. Since ufw is in Sid, that might change in the future, but as of right now, you can't even find ufw, or gufw in the Debian Lenny (stable) repositories, which I would expect the OP is using.

Edit: 

Oh, I forgot to mention, that ufw is not available as a backport either.

---

### Post by bodhi.zazen on 2009-06-06
Orngecrate, we all know from your previous posts you are happy with firestarter, and that is fine.

But firestarter is no longer being maintained and is, IMO, not the best choice of tools to configure your firewall nor the best choice to advise to new users.

It is certainly not the "standard" for Debian. Firestarter is not installed by default.

The standard on Debian is iptables. If you want a gui there are great options, for new users to experienced users, starting with guarddog and shorewall.

We have had this debate before and, as I know you like firestarter, I will not re-iterate the long list of problems it has in this thread. If you wish to discuss Firestarter please use recurring discussions.

---

### Post by OrangeCrate on 2009-06-06
^,

Nice of you to mislabel the content of my post in the title of this thread.

I didn't say anything about Firestarter being the "default firewall in Debian", nor am I particularly a big fan of Firestarter.

As I've said several times, in response to your comments in previous threads, Firestarter is a simple GUI that configures iptables, and isn't a program that needs to be continually updated, since it does it's simple job quite well.

Frankly, I'm simply tired of your ongoing campaign of FUD against the program, and, as in the past, I comment on your posts when I see them.

The information I posted regarding Debian and ufw is accurate and factual. Firestarter is recommended often, to configure iptables in Debian.

Only on these forums, and only by you, do I find Firestarter being trashed. Funny isn't it?

---

### Post by bodhi.zazen on 2009-06-06
As I said, I respect your opinion and decision regarding firestarter and I am happy it works for you.

A simple google search will demonstrate many bug reports against firestarter , here is a partial list:

[https://bugs.launchpad.net/firestarter/+bug/120445](https://bugs.launchpad.net/firestarter/+bug/120445)

[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/42759](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/42759)

[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/184017](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/184017)

[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/301603](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/301603)

I could list many many more examples, but I think those should be sufficient to demonstrate that there are indeed ongoing issues with firstarter.

And how do you propose the be fixed ? Firestarter is no longer maintained.

I understand it has been popular, but that does not mean it is without problems or that there are not better options.

You clearly have a strong opinion, but you also turn a blind eye to the problems with firstarter and insist that it no longer needs development because there are no problems with it. A simple google search easily shows that claim is false.

I have shown you a partial list of problems with firestarter, disproving your claim that I am spreading FUD, by backing up my claims with facts. The simple fact is firestarter has problems and, IMO it is really not the best advice any longer.

Times change your you have not kept up with changes, at least in Ubuntu.

If there is a problem with an alternate, such as gufw, guarddog, shorewall, the problem can be reported as a bug to the developers. Such is not the case with firesarter. This is not FUD this is a fact you think you can disregard or disprove with an insulting tone.

While you may call bug reports "FUD" that does not fix the problem or prove your point. Or are you suggesting the various bug reports against firestarter either don't exist or have been fixed ?

So yes, until the developers of firestarter feel like following through on bug reports I think it is reasonable to suggest alternate solutions.

Also your fix for most any firewall problem or question on these forums is to install firestarter. I have not searched your posts, so I apologize if I am wrong, but I can not recall you ever advising an alternate tool.

You really need to take the time to understand what the needs of the OP are and what the implications of your advice may be on an Ubuntu system before giving advice. I do not think you understand the breakage or conflicts that firestarter causes with ufw and your advice never warns users about potential conflicts or how to resolve potential problems, making it poor advice.

From here : [Ubuntu Forums - Policy]("http://ubuntuforums.org/index.php?page=policy") 

> If your procedure has inherent risks, please tell users what they are. For example, if you're teaching someone how to resize a partition, please include a disclaimer that it MAY occasionally cause data loss.In this case you fail to warn uses of potential conflict and breakage with ufw. I assume this is because you either simply not aware of the many bug reports against firestarter or choose to ignore them with a "works for me" policy.

As I have indicated, firestarter is a simple tool and will not handle complex networking or firewalls (NAT) on complex networks such as may exist if one if using their box as a router or a a host for virtual machines. Shorewall and guradog, as well as iptables, are better tools in such situations.

So please before ranting as you are, you might want to check your facts. And yes if you give bad advice it is my responsibility to correct it.

---

### Post by OrangeCrate on 2009-06-06
> **bodhi.zazen said:**
> 

A simple google search will demonstrate many bug reports against firestarter , here is a partial list:

**I think you'd better take a closer look at those bug reports...**

[https://bugs.launchpad.net/firestarter/+bug/120445](https://bugs.launchpad.net/firestarter/+bug/120445)

**Fixes released in both Debian and Ubuntu**

[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/42759](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/42759)

**Fix released in Debian**

[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/184017](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/184017)

**Fix released in Debian**

[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/301603](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/301603)

**Fix has been released in Ubuntu. Assigned in Debian**

I could list many many more examples, but I think those should be sufficient to demonstrate that there are indeed ongoing issues with firestarter.

**Really? There's bugs in every program. If you want to post more Firestarter bugs, I'll bet I can give you many of the same answers that I just gave above.**

And how do you propose the be fixed ? Firestarter is **no longer maintained**.

**Really? It certainly doesn't look that way to me (particularly in Debian*).**

<snip>


You can hide behind any portions of the code you'd like. You can even threaten to, or ban me if you'd like, since you're now an Admin, but it simply doesn't change the fact, that you've got a hard on for Firestarter, and nothing anyone can say, no matter how logical, can change that.

In threads where I've challenged you, you've been proven wrong, over and over again in your assessment of Firestarter, and yet you continue to trash it on these forums. By any definition, that is spreading FUD, pure and simple.

You stop, and I'll be delighted to do the same.

(*****)
> **Firestarter is maintained in Debian** and can be downloaded and installed using the apt-get tool by simply typing "apt-get install firestarter".

Ubuntu users can install Firestarter by enabling the "universe" repository in the /etc/apt/sources.list file or in synaptic under Settings->Repositories. Having enabled the repository, the procedure is the same as in Debian.

[http://www.fs-security.com/docs/installation.php](http://www.fs-security.com/docs/installation.php)



---

### Post by bodhi.zazen on 2009-06-06
I think it is best that we agree to disagree. 

While you are welcome to your opinion, there is no need for personal insults or frank disrespect for the opinions of others.

---

### Post by juancarlospaco on 2009-06-08
Firestarter its a GUI, can't be installed on a Server :)

---

### Post by pbpersson on 2009-06-08
I don't use software that does not have a GUI front end.

I just installed Firestarter this weekend and it has been working okay for about 42 hours now.

However, now I am worried about it crashing and taking my network down!

I wish I had known about Guarddog before this weekend.

---

### Post by bodhi.zazen on 2009-06-08
> **pbpersson said:**
> I don't use software that does not have a GUI front end.

LOL

> I just installed Firestarter this weekend and it has been working okay for about 42 hours now.

However, now I am worried about it crashing and taking my network down!

Firestarter will not do anything malignant if it fails it will bring down your firewall (iptables) where it is installed, nothing more.

> I wish I had known about Guarddog before this weekend.

Personally I use iptables directly. I know it is intimidating at first, but it is not difficult.

Alternates to firestarter include gufw as well. If you wish, remove (purge) firestarter and install an alternate tool, but to be honest, if you are not having a problem I would not change.

---

### Post by pbpersson on 2009-06-09
> **bodhi.zazen said:**
> 
Firestarter will not do anything malignant if it fails it will bring down your firewall (iptables) where it is installed, nothing more.


Personally I use iptables directly. I know it is intimidating at first, but it is not difficult.


I want a simple solution that will do DHCP and Internet Connection Sharing on my network.  Is that basically what iptables is all about?

---

### Post by bodhi.zazen on 2009-06-09
yes, the firewall itself is iptables. Firestarter, ufw, guarddog, gufw, shorewall, these are configuration tools.

iptables is difficult as you need to understand at least the basics of networking ...

but , with that said, some people, myself included, find iptables is easy to use. Once you understand the basic rules, it is easy to modify.

After learning to use these tools, I still advise anyone who wants to understand how these thing swork, learn iptables. 

With what you have posted it seems you are interested in a Graphical tool, and there is nothing wrong with that. When you say "internet sharing" does that mean you are using your computer as a router ?

If so I suggest guarddog  and / or shorewall.

If not, try gufw.

---

### Post by pbpersson on 2009-06-10
> **bodhi.zazen said:**
>  When you say "internet sharing" does that mean you are using your computer as a router ?

If so I suggest guarddog  and / or shorewall.

Yes, one computer to hand out IP addresses to all network machines and do Network Address Translation

GuardDog looked good, Shorewall looked like it had WAY more features than what I needed.

I will wait for Firestarter to go "belly up" on me, install a temporary Windows 2000 machine to keep the network running, and then investigate GuardDog if that day ever arrives.

---

### Post by Tipped OuT on 2009-06-10
I'm surprised this thread wasn't closed. Great job keeping your cool bodhi.zazen. Wait, I think I spoke to soon... :shock:

---

### Post by bodhi.zazen on 2009-06-10
One thing that I should probably add to this thread ...

The firewall itself is iptables. These other applications are configuration tools (ufw, gufw, firestarter, guarddog, shorewall, etc).

The default tool used to configure your firewall (iptables) in Ubuntu is ufw, gufw if you want a gui.

If you wish to install an alternate tool, you should remove and purge ufw and gufw first (if gufw is installed).

```
sudo apt-get remove --purge ufw gufw
```

If you have more then one configuration tool installed at the same time they are likely to conflict as they fight to configure iptables and give you unpredictable results.

So try or use only one configuration tool at a time and remove the others.

---

