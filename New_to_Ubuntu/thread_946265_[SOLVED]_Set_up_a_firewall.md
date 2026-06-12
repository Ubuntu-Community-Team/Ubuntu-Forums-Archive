---
title: "[SOLVED] Set up a firewall"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Scunnered on 2008-10-13
I am almost at the stage of loading 8.04 to my HD and when reading about firewalls note the remark in the documentation section:

"UFW firewall, which is installed by default"

When this is refered to as by default is it automatically set on.

I would much prefer not to just chance to luck that nothing will get through as I am using Linux, particularly when using the most popular version.

How should I ensure that I am safeguarded?

Thanking you in anticipation

---

### Post by Orange_and_Green on 2008-10-13
Hello Scunnered :)

Try [gufw]("http://gufw.tuxfamily.org/"), it will give you a nice GUI to set up the firewall.

Mind you, ufw (and gufw), along with firestarter, shorewall and similar programs, are not "firewalls" themselves but rather config utilities for the "real" firewall which is iptables. (you can try configuring iptables manually of course, but be warned, it's quite messy ;) )

So this means that you don't need ufw/gufw/firestarter/shorewall to be always running, just run any of them once to configure things, and stay protected afterwards :)

Have fun :KS

---

### Post by mjwhitfield on 2008-10-13
Ubuntu doesn't have any services running on open ports by default, so unless you fancy wasting some CPU cycles, leave ufw alone.

You can find documentation here if you do fancy pissing away some processing power:
[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by mike2357 on 2008-10-13
I've used firestarter as my firewall manager for several years, and I've continued to do so even with 8.04.  If it's not loaded already on your machine, you can run System -> Administration -> Synaptic Package Manager and get it.  Then, Firestarter will show up under System -> Administration.

The actual firewall is something called iptables, which contain complex rules governing network traffic. Firestarter is a GUI program which will allow you to make changes, and see that your firewall is turned on.  Lots of people make the mistake of thinking that firestarter needs to be running in order for your firewall to be running; it doesn't.  Firestarter is a GUI interface for managing your firewall.

I don't have any experience with ufw.

You can run "man ufw", "man firestarter" and "man ufw" from the command line to learn more.

---

### Post by prshah on 2008-10-13
> **Scunnered said:**
> 
When this is refered to as by default is it automatically set on.

How should I ensure that I am safeguarded?


While ufw is installed by default, it is not "turned on" / "enabled". However, that does not mean that you are not being protected; iptables a "back-end" to ufw is active, with restrictive permissions in place (disallow <some network protocol / port / address> unless specifically allowed)

You can instantly enable ufw (one time, no restart required, stays enabled across reboots)```
sudo ufw enable
``` You can check the status of ufw with ```
sudo ufw status
Firewall loaded

To                         Action  From
--                         ------  ----
207.66.155.21 80:tcp       DENY    Anywhere
207.66.155.21 80:udp       DENY    Anywhere
Anywhere                   DENY    207.66.155.21

```

(I have included the output showing 3 custom rules that block a linux "virus" Linux/Rst.B or something; these lines will not show up for you nor will you most likely require them; I'm paranoid.)

Post back if you need more help with ufw.

---

### Post by hyper_ch on 2008-10-13
Are you sure you need to alter the default iptables configuration? Mostly there is no need for it (as this is not Windows).

---

### Post by paris_alex on 2008-10-13
FWIW, I'm using firestarter to configure my firewall from GUI... very please with it so far.

---

### Post by hyper_ch on 2008-10-13
> **paris_alex said:**
> FWIW, I'm using firestarter to configure my firewall from GUI... very please with it so far.

What for? Why do you need it?

---

### Post by paris_alex on 2008-10-13
Well, while it's rather secure in the linux world... sometimes the paranoid me still want to protect certain ports/protocols from inboung/outbound traffic. unless you're familiar with iptables, you'll need some gui to help.

Not to mention it's good to know in your LAN (or worse, on the Internet) is trying to access your computer's services (firestarter can indicate unauthorized events).

Cheers! :-)

---

### Post by handydan918 on 2008-10-13
It may be worth noting that many people are already running a hardware firewall unawares. If you are behind a residential gateway or a modem with a routerattached, you are likely using NAT (network address translation) which is a pretty effective way of keeping bad guys at bay.

---

### Post by Scunnered on 2008-10-13
Many thanks to all who contributed.

It looks very much that the bulk of the opinions lead me to believe that I can live without a firewall.  I think that I will sit on the fence until I load 8.04 on my HD and then see what develops.

I am finding things a bit different to what I am used to but will get there eventually.

---

### Post by prshah on 2008-10-13
> **Scunnered said:**
> 
It looks very much that the bulk of the opinions lead me to believe that I can live without a firewall.

Unfortunately the point seems to have been missed.

iptables does the job of the firewall; it is in restrictive mode by default.

If you install a program that need to use a particular protocol / port (Eg., a bittorrent client) then you will need to inform iptables to allow access.

If you enable samba (windows networking) you will have to tell iptables to allow access to samba ports (137?)

If you enable an ssh server, you will have to tell iptables to allow port 22 (or custom-configured port).

And so on.

Now you can do this with the iptables command, but it is difficult for a newbie to use.

Instead using Firestarter (GUI) or ufw (plain english-like) or gufw (front end to ufw, still in development) will allow you to perform all the other tasks, easily.

---

### Post by hyper_ch on 2008-10-14
> **prshah said:**
> Unfortunately the point seems to have been missed.
Unfortunately you seem to have missed the point.

Yes, iptables is the firewall but by default it has no rules in it. This means, by default it will let pass everything and that is good so because by default you have no open ports because there no listening services.

---

### Post by prshah on 2008-10-15
> **hyper_ch said:**
> 
Yes, iptables is the firewall but by default it has no rules in it. 

Surprisingly (to me at least) this is quite correct! I don't know where I got the idea that it is restrictive by default; it is, in fact, permissive by default.

However, further reading tells me that while iptables is permissive by default, just _enabling_ ufw puts restrictive rules into place. On a fresh install:```


Wed Oct 15 23:11:23 ~:$ sudo iptables -n --list | grep INPUT
Chain INPUT (policy ACCEPT)
Wed Oct 15 23:11:26 ~:$ sudo ufw enable
Firewall started and enabled on system startup
Wed Oct 15 23:11:28 ~:$ sudo iptables -n --list | grep INPUT
Chain INPUT (policy DROP)
Wed Oct 15 23:11:28 ~:$ sudo ufw status
Firewall loaded
Wed Oct 15 23:11:29 ~:$ sudo ufw allow 80
Rule added
Wed Oct 15 23:11:31 ~:$ sudo ufw status
Firewall loaded

To                         Action  From
--                         ------  ----
80:tcp                     ALLOW   Anywhere
80:udp                     ALLOW   Anywhere

```

Which, in my opinion, is just another reason for ufw / firestarter to be used; to make the permissions restrictive. Yes, I know iptables can also be used to make permissions restrictive, but I think it's a lot easier using ufw (just enable) / firestarter.

Incidentally, this also makes the firewall more "Windows-like"; restrict everything until specifically allowed (aka restrictive).

---

### Post by hyper_ch on 2008-10-15
why do you want to make it restrictive if by default nothing is listening anyway?

---

### Post by prshah on 2008-10-16
> **hyper_ch said:**
> why do you want to make it restrictive if by default nothing is listening anyway?

Paranoia, mainly; but it's not as though there is _nothing_ listening; mail ports (110 & 25) are listening, or, when purposely / accidentally enabled, ssh server, ftp, etc.

The main reason I prefer a restrictive policy is to have control over what is happening in my system; if a program is blocked, I can release it anytime I want, but no program can "go behind my back".

---

### Post by hyper_ch on 2008-10-16
well, when you install servers then they will be litening... but by default nothing is ;)

---

