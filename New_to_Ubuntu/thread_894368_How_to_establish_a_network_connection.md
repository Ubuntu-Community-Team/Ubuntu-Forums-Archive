---
title: "How to establish a network connection?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Kataangel on 2008-08-19
I'm having getting Ubuntu to connect to the internet.  

I have connected a cable from the network socket to my router and this would work in Windows except I'm using Ubuntu for that computer e.g.:

[IMG]http://www.microsoft.com/library/media/1033/windowsxp/images/using/networking/setup/68573-connect-computer-small.jpg[/IMG]

[IMG]http://www.microsoft.com/library/media/1033/windowsxp/images/using/networking/setup/68573-connect-to-router-small.jpg[/IMG]


Normally in order to establish an internet connection I would use network connection wizard in network connections by:

1. Clicking 'connect to the internet'
2. Clicking 'set up my connection manually'
3. Clicking 'connect using a broadband connection that requires a user name and password'
4. Typing in my ISP name, user name and password.
5. Clicking connect in the window I get after clicking connect to.
6. And finally I can connect to the internet.

How does this exactly translate to in Ubuntu?

Edit: What I've tried without any success is:

1.  Clicking system
2.  then administration
3.  then network
4.  I've enabled roaming mode under Wired Connection
5.  I then selected a PPPoE connection and entered my user name and password
6.  I've also had to select an eth0 ethernet interface under modem settings in order to click ok.

So what am I doing wrong that's preventing me from connecting to the internet?

---

### Post by keenboy on 2008-08-19
What version of Ubuntu are you using?

---

### Post by Dill on 2008-08-19
Open a Terminal and try

```
sudo pppoeconf
```

You should probably click yes to every option, and there should be a place to enter your username and password.

To turn the connection on, you can type

```
pon dsl-provider
```

(the dsl-provider profile may differ for you, but I think that's the default one-- it should tell you which command to use at the end of the configuration process)

To turn the connection off, you can use

```
poff -a
```

Hope this helps!

Cheers, 
Dylan

---

### Post by Kataangel on 2008-08-19
I was using Ubuntu from a live CD but Dill's advice worked so thank you!

---

### Post by srjsbhdi on 2008-12-29
Hi,

I am using the Kubuntu Hardy Heron distro. I have a related question.

I few months ago I was trying to setup internet connection sharing.  I had my laptop connected to a WIRED (eth0) modem and wanted to use the built in WIRELESS card (ath0) as a "virtual" wireless router of sorts. This involved fiddling about with the eth0 iptables and what not.

Long story short I ended up destroying my WIRED connection and eventually just purchased a wireless router. My WIRED connection no longer works. I want to have it functional again (without an OS reinstall).

Is there a way to run the original network wizard that the UBUNTU installer first used to setup my wired connection?  i.e. when I first installed the OS.

Thanks in advance.

Srj.

---

### Post by handydan918 on 2008-12-29
First, you may want to repost in networking, and start your own thread, because this one has whiskers on it.

Perhaps someone who is running hardy could post their iptables rules and you could add them? Might be the most straightforward way to get a working system...

But again, I would direct this issue to the networking gurus...

---

### Post by Sealbhach on 2008-12-29
Does Network Manager in 8.10 now handle ADSL connections automatically?


.

---

### Post by handydan918 on 2008-12-29
> **Sealbhach said:**
> Does Network Manager in 8.10 now handle ADSL connections automatically?
.

AFAIK, the OP is using a router, which, again, in my experience, should eliminate the need for any config at all, provided that the router is set up to do dhcp, etc.

---

