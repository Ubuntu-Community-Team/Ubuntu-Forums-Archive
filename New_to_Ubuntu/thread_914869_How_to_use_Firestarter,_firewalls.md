---
title: "How to use Firestarter, firewalls"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by ahuman on 2008-09-09
Hi,

I need help in choosing a firewall and have a few questions:
1)Do you recommend Firestarter as a firewall for beginners? 

2)Is it  user-friendly like McAfee firewalls that gives you prompts like "allow" or deny" to give programs access to your computer?

3) Its description says I can open and close ports. Is it easy to know which ports to close? 

4) Firestarter is described as a "gtk program." What does that mean, and how do I know if I can use it?

5)Finally, is there a tutorial video  on Firestarter available anywhere? Many thanks!

---

### Post by bodhi.zazen on 2008-09-09
Firestarter is out dated. Ubuntu uses UFW. There is a gui gufw :

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

GUI : [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

Other then that, what is it you want a firewall for ?

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by ahuman on 2008-09-09
Thanks! That looks great. I read in Gufw's support section that it doesn't "show things like Active Connections (similar to Firestarter) and event logs for attempted incoming connections on a port that's not allowed". That said, how do you choose what things can access your computer and how can you tell what's trying to get in.

---

### Post by hyper_ch on 2008-09-09
> **ahuman said:**
> I need help in choosing a firewall and have a few questions:
1)Do you recommend Firestarter as a firewall for beginners?
(1) Firestarter is no firewall
(2) You generally don't need to modify the actual firewall called iptables.

---

### Post by bodhi.zazen on 2008-09-09
> **ahuman said:**
> Thanks! That looks great. I read in Gufw's support section that it doesn't "show things like Active Connections (similar to Firestarter) and event logs for attempted incoming connections on a port that's not allowed". That said, how do you choose what things can access your computer and how can you tell what's trying to get in.

You either have to read your logs or install something like snort.

Who cares about attempted access ? so long as it is blocked (you will find there is almost continuous attempted access, most people only monitor what gets through their router).

[http://www.how2forge.org/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10-updated](http://www.how2forge.org/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10-updated)

---

### Post by Vivaldi Gloria on 2008-09-09
ahuman, out of curiosity, why do you need a firewall?

---

### Post by y@w on 2008-09-09
> **bodhi.zazen said:**
> You either have to read your logs or install something like snort.

Who cares about attempted access ? so long as it is blocked (you will find there is almost continuous attempted access, most people only monitor what gets through their router).

[http://www.how2forge.org/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10-updated](http://www.how2forge.org/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10-updated)

Agreed. If you watch attempted break-ins, you'll spend all day reading logs.. I find that my systems that have SSH open to the world have several brute-force attempts every day.

---

### Post by ahuman on 2008-09-11
Hi: Just want as much security as possible.

---

### Post by hyper_ch on 2008-09-11
but wrong security is even worse ;)

---

### Post by ahuman on 2008-09-11
Does GUFW stop attacks that try to get past your router?

---

### Post by handydan918 on 2008-09-11
ahuman, just to sum up some things that have almost been stated here:

1) Firestarter, Guarddog, gufw, and whatever else, are not firewall. They are tools for manipulating the firewall. 

2)The firewall is a kernel-level program called iptables. 

3) ch is right. If you don't know something about it, it is best to let the system defaults set up iptables. You can cause yourself much grief fooling around opening and closing ports you don't understand....

As far as attacks that "try" to get past your router, the only things a firewall could possibly address would be successful attempts to get past the router. If you are behind a NAT router, and running virtually any flavor of Linux, you are already one of the most unattractive targets on the internet. 
Relax. Life on the 'net is safer without Windows....

---

### Post by OrangeCrate on 2008-09-11
> **bodhi.zazen said:**
> Firestarter is out dated.

Is that just your opinion, or can you cite a source? And if so, why is it still in the repositories?

---

### Post by Vivaldi Gloria on 2008-09-11
> **OrangeCrate said:**
> Is that just your opinion, 

Firestarter is dead. The last update was in 2005. The developers are not working on it anymore. I read in the list that it hasn't been updated to reflect the latest libraries for Gnome and other fundamental iptables changes in newer kernels. I heard a few cases of it crashing and screwing up some systems.

> And if so, why is it still in the repositories? 

I guess it works in most systems and people are used to it.

---

### Post by bodhi.zazen on 2008-09-11
> **OrangeCrate said:**
> Is that just your opinion, or can you cite a source? And if so, why is it still in the repositories?

You are welcome to use firestarter if you wish but you should be aware that there are better, more up to date alternates.

The potential considerations for firestarter are (in no particular order) :


[list=number]
[*]As has been pointed out by Vivaldi Gloria, firestarter is no longer under development. It was last updated in January of 2005. This equates roughly to Ubuntu 5.04.

Features of Ubuntu 5.04 : kernel 2.6.10 ; firefox 1.0.2 ; xorg 6.8.2


[*]Firestarter runs as root and as such is a security vulnerability, especially when people run it all the time and use it for IDS (Intrusion detection).


[*]Firestarter is fine with a single interface, but firestarter can not handle complex networking.


[*]Firestarter does not run if you are not running X.


[*]Because firestarter is outdated it is becoming more and more common for it to fail. Not that any application is perfect in this respect mind you just letting you know it is a trend
[/list]


There are much superior tools such as UFW and gUFW and snort. These tools are under active development and are , at least in the case of UFW, just as easy to use and user friendly as firestarter.

As to why it is in the repositories ? Well, first you should know that Ubuntu is not the most bleeding edge of distros and second one advantage of Ubuntu is the sheer size of the repostiories. Just because something is in the reopositories, however, soes not mean it is the best tool for the job.

FYI: I am working on a how to for intrusion detection and am *almost* finished. I need to add a few screen shots and some (minor) content. I will be posting it in the security section.

---

### Post by hyper_ch on 2008-09-11
> **OrangeCrate said:**
> Is that just your opinion, or can you cite a source? And if so, why is it still in the repositories?

How about: [http://www.ubuntu.com/testing/hardy/beta](http://www.ubuntu.com/testing/hardy/beta)
> Firewall

Ubuntu 8.04 Beta includes ufw (Uncomplicated Firewall), a new host-based firewall application configurable from the command line which is designed to make administering a firewall easier for end users while not getting in the way of network administrators. 


And the fact that Firestarter hasn't seen any update for years?

---

### Post by OrangeCrate on 2008-09-11
> **bodhi.zazen said:**
> You are welcome to use firestarter if you wish but you should be aware that there are better, more up to date alternates.


I guess, that that's the comment I was looking for. Nothing in Linux is generally "either/or", but usually "and". Firestarter is just a simple GUI to manage IP tables, and that's all it does. As was stated by another Mod, in a thread I can't seem to find right now, it's not that Firestarter is "out of date" so much, as it's simply a finished product not requiring additional development work. Anyway, thanks for the info.

Edit:

Found it. Actually, it's wasn't a Mod, it was mcduck in post #4 in this thread:

[http://ubuntuforums.org/showthread.php?t=899004&highlight=firestarter+development](http://ubuntuforums.org/showthread.php?t=899004&highlight=firestarter+development)

> The talk about Firestarter not being supported any more is nonsense. If it's in the repositories, it's supported. It might not be very actively developed these days, but that's just normal in open-source world, when a program does what it needs to do and has no more bugs to fix it's ready. There is no need to provide new versions every year because nobody is trying to make money with the program.

It's true that Ubuntu developers added another firewall configuration tool, UFW, but that doesn't mean that you couldn't use Firestarter instead if you rather use a GUI tool. UFW is a command-line program, anyway, and because of that definitely not the tool for everyone.


The Ubuntu doc on Firestarter, was updated on 7/24/08. It does recognize a conflict with Network Manager, but offers a simple fix. Nothing there indicating that it's out of date.

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

Telling users to not use Firestarter, out of hand, may be a disservice to a pretty good tool. But hey, lots of different opinions on this forums...

As said earlier, thanks for your comments.

---

### Post by ahuman on 2008-09-11
Thanks, everyone and for the summary Handydan. Handydan: Based on what you've explained, does that mean Ubuntu has a built-in firewall. Just wanted to confirm. Thank you again.

---

### Post by Vivaldi Gloria on 2008-09-11
> **ahuman said:**
> does that mean Ubuntu has a built-in firewall. 

Yes.

> Iptables is a firewall, installed by default on all official Ubuntu distributions (Ubuntu, Kubuntu, Xubuntu). When you install Ubuntu, iptables is there, but it allows all traffic by default.

from [[COLOR="Sienna"]iptables[/COLOR]]("https://help.ubuntu.com/community/IptablesHowTo"). All the other programs mentioned (ufw, firestarter etc.) are just frontends to iptables.

---

### Post by porchrat on 2008-10-16
I have a question regarding ufw and I thought I would add it here rather than start a new thread.

I see from the rc.d directories that ufw doesn't run at startup.  I realise of course that it isn't the firewall and that it merely hands commands to iptables, but I was looking at [this]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") and it says I need to type in this command before I enable the ufw in order to ensure that the firewall defaults to denying all incoming traffic regardless of source, destination or service type.

```
sudo ufw default deny
```

What I want to know is...since ufw doesn't run on startup, do I have to type that in before I enable ufw **every single time** to set a rule?

Seems a little silly.

---

### Post by SeanHodges on 2008-10-16
> **porchrat said:**
> I see from the rc.d directories that ufw doesn't run at startup.  I realise of course that it isn't the firewall and that it merely hands commands to iptables, but I was looking at [this]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") and it says I need to type in this command before I enable the ufw in order to ensure that the firewall defaults to denying all incoming traffic regardless of source, destination or service type.

```
sudo ufw default deny
```

What I want to know is...since ufw doesn't run on startup, do I have to type that in before I enable ufw **every single time** to set a rule?

Seems a little silly.

The way I see it:

1) iptables is the firewall in Linux, ufw is a front-end, and as such is not required to run on start-up unless you explicitly request it.

2) The default configuration for iptables IS to deny unsolicited traffic. Perhaps the command you were referring to was "sudo ufw enable"?

3) You don't need ufw, it is an opt-in utility. If you are using it, it is assumed you have some understanding of (or are intending to learn) network security. For example, just enabling ufw without setting it up will open EVERYTHING, best to leave the firewall to do its job, unless you have a specific reason to manually over-ride something. Most Ubuntu users do not want to worry about all this.

4) You can set-up ufw to start on boot, but you need to tell it what it should be doing first. Search around or ask in another thread if you want to do this.

---

### Post by hyper_ch on 2008-10-16
> **SeanHodges said:**
> The way I see it:
2) The default configuration for iptables IS to deny unsolicited traffic. Perhaps the command you were referring to was "sudo ufw enable"?

You see it wrong on statement (2):

The default configuration for iptables is to let everything pass. And that's good so because no service is running - so you don't need to block anything.

---

### Post by jerome1232 on 2008-10-16
> **porchrat said:**
> I have a question regarding ufw and I thought I would add it here rather than start a new thread.

I see from the rc.d directories that ufw doesn't run at startup.  I realise of course that it isn't the firewall and that it merely hands commands to iptables, but I was looking at [this]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") and it says I need to type in this command before I enable the ufw in order to ensure that the firewall defaults to denying all incoming traffic regardless of source, destination or service type.

```
sudo ufw default deny
```

What I want to know is...since ufw doesn't run on startup, do I have to type that in before I enable ufw **every single time** to set a rule?

Seems a little silly.


Once you enable ufw and/or setup rules in it they are permanently in place until you explicitly remove them.

If you disable/then renable ufw it will retain all the previous rules you had. You can check this with 'ufw status'.

---

### Post by porchrat on 2008-10-16
> **jerome1232 said:**
> Once you enable ufw and/or setup rules in it they are permanently in place until you explicitly remove them.

If you disable/then renable ufw it will retain all the previous rules you had. You can check this with 'ufw status'.

It isn't the specific rules I'm worried about, I played around with ufw a little adding and removing rules and realised they remain there.  It is that general "default deny" setting I am worried about, as there is no way to check that it is default denying...the status command will just return "firewall loaded" which unfortunately tells me nothing about whether it is defaulted to denying or allowing.  All I really need to use ufw for is to open a port for a vpn, so I doubt I will be using it often, but if I do I don't want to have to tell it that it needs to "default deny" again.  Was just wondering about it is all.

---

### Post by jerome1232 on 2008-10-16
Well it is retained, I didnt' realize ufw doesn't state that, you can check iptables directly with ```
sudo iptables -L
```

---

### Post by porchrat on 2008-10-17
I assume "POLICY DROP" in iptables-talk is the equivalent of "deny" in ufw-speak?

```
Chain INPUT (policy DROP)
```

and that "ACCEPT" and "allow" are one and the same?

```
Chain OUTPUT (policy ACCEPT)
```

I have no idea what "1 references" means though:

```
Chain ufw-after-input (1 references)
```

---

### Post by porchrat on 2008-10-17
I just wanted to say that I am quite happy with ufw and I didn't even realise it existed before I checked this thread.  I do have one other question though.

When I make changes through ufw, do I need to restart it through /etc/init.d?, does it require a restart? Or do the changes take effect immediately?

---

### Post by jerome1232 on 2008-10-17
They take affect immediatly :), yes iptables 'drop' is what ufw calls deny and vica versa with allow/accept, and just wanted to make this clear ufw isn't a firewall, it's a configuration utility for iptables, iptables is the firewall. 

I think it would take alot of iptables knowledge to figure out how to read the chains that ufw add's to iptables, I imagine those are just where it slaps it's rules in, and slaps logging in. If you wanted to log all dropped packets then you can modify ufw like so to get that.
```
ufw logging on
```
One thing I didn't like about ufw is that the order of your rules matter (you want to write your rules specific to general) but ufw doesn't provide a means of moving rules around in the list. 

Modifying iptables directly is harder but it does provide a way to move rules up and down in the list.

---

### Post by bodhi.zazen on 2008-10-17
> **jerome1232 said:**
> <clip> ufw doesn't provide a means of moving rules around in the list. 

Yes, this is true. I reported this as a bug report / feature request though and it was accepted, so the developers are "working on it". There have been a few additional suggestions so I think UFW will continue to improve.

Currently if you need to modify the rules you need to edit the configuration files.

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

Also, if you wish there is a gui fron end, gufw

[http://gufw.tuxfamily.org/screenshots.html](http://gufw.tuxfamily.org/screenshots.html)

---

### Post by kevdog on 2008-10-17
Seems like ufw still has some developement to do.

Points of Clarification:

Iptables is acutally a generic table structure for defining rulesets.  These rules are passed or interact with a program called netfilter which is the actual program that interacts with the Linux kernel and the network stack.  

The most basic way to control or interact with netfilter is through the use of iptables.  Iptables combines both packet filtering (what many people think of as a traditional firewall), but also packet routing.  There are also less common functions iptables can perform such as:

- use NAT and masquerading for sharing internet access if you don't have enough public IP addresses
- use NAT to implement transparent proxies
- aid the tc and iproute2 systems used to build sophisticated QoS and policy routers
- do further packet manipulation (mangling) like altering the TOS/DSCP/ECN bits of the IP header

Just to provide a point of clarification, its my understanding the the ufw (or gufw) is capable of writing rules or packet filtering but not packet routing.  Packet routing is needed if you are interested in either setting up a router, or internet connection sharing though packet forwarding.

Both Firestarter and Guarddog are "out of date" meaning that they are no longer under active development.  Compared to the gufw currently available that is under active development, its quite fascinating how Firestarter was so advanced for its time.  It offers functionality still not available in the gufw.  Its actually quite a shame the project didn't enroll new developers.  gufw is in a way starting over, however hopefully new functions will be implemented.  Guarddog (a KDE program) offers even more functionality that Firestarter, however this project too has been abandoned.  

Learning how to write basic iptables rulesets (basic) is something everyone should be familar with.  It really helps when starting to write ufw rules.  I recommend this tutorial:
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html#NFQUEUETARGET](http://iptables-tutorial.frozentux.net/iptables-tutorial.html#NFQUEUETARGET)
Only problem with this tutorial is that the tables dont seem to display correctly for me using Firefox3.  Oh well!

---

### Post by porchrat on 2008-10-17
OK I hadn't read enough on iptables to realise it had a routing and NAT function, but it makes sense as a lot of people run linux boxes behind routers with NAT turned off and there has to be something doing the translation.

I am aware that ufw merely hands the rules to iptables and that iptables it doing the actual handling of incoming and outgoing data.  I just wanted to know if ufw wrote to iptables straight away or not.  Perhaps I'm not communicating this properly, but from what you guys are saying I get the impression that it does in fact write it straight to iptables as you add the rule to ufw.

I'm glad there is a GUI for ufw as I really do prefer ufw to firestarter, and I fear the lack of a GUI would chase away a lot of new users that want to play with SSH and whatever else that requires playing with ports, but since I took the time to learn the ufw commands it seems pointless to use a GUI as the console really is faster.  In fact I find I hardly use GUIs at all, even though I do try using the GUIs I find generally you get a lot more control and can make changes a lot faster through the console.

---

### Post by kevdog on 2008-10-17
To see the ufw "translated rule", enter a rule using ufw, and then check to see if it was added to iptables via:

sudo iptables -L

That command lists the current iptables ruleset.

---

### Post by porchrat on 2008-10-17
> **kevdog said:**
> To see the ufw "translated rule", enter a rule using ufw, and then check to see if it was added to iptables via:

sudo iptables -L

That command lists the current iptables ruleset.

Good sound advice thank you.

---

