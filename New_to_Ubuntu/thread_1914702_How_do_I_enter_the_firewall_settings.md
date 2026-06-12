---
title: "How do I enter the firewall settings?"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by TAspr on 2012-01-24
To know doubt, this has been daunting.  All I want to do is set my firewall without going to the configuration screen all the time.

---

### Post by wolfen69 on 2012-01-24
For general usage, a firewall isn't even necessary. From [here]("http://www.psychocats.net/ubuntu/security"): *"By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up."*

Is there a reason you need it?

Edit: I just did a *shields up* test, and passed 100%. I never configured any firewall. Ubuntu is *very* secure by default.

---

### Post by bodhi.zazen on 2012-01-25
> **TAspr said:**
> To know doubt, this has been daunting.  All I want to do is set my firewall without going to the configuration screen all the time.

You can enable your firewall with a single command

```
sudo ufw enable
```

This is a one-time configuration.

You can disable it with

```
sudo ufw disable
```

See : [https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)

---

### Post by 3rdalbum on 2012-01-25
Wolfen69 is correct - you only need a firewall on Windows because it has vulnerable services listening for incoming connections. On Ubuntu, there's nothing listening for incoming connections unless you install something that does. Hence, a firewall will do nothing that your computer isn't already doing (dropping incoming connections).

Or, to use an analogy: If all your household appliances are solely battery-powered, you don't need a surge protector.

---

### Post by TAspr on 2012-01-25
> **wolfen69 said:**
> For general usage, a firewall isn't even necessary. From [here]("http://www.psychocats.net/ubuntu/security"): *"By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up."*

Is there a reason you need it?

Edit: I just did a *shields up* test, and passed 100%. I never configured any firewall. Ubuntu is *very* secure by default.

I was incorrect.  I knew there was some way to do this.  Thanks cheers!

---

### Post by haqking on 2012-01-25
> **wolfen69 said:**
> For general usage, a firewall isn't even necessary. From [here]("http://www.psychocats.net/ubuntu/security"): *"By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up."*

Is there a reason you need it?

Edit: I just did a *shields up* test, and passed 100%. I never configured any firewall. Ubuntu is *very* secure by default.

> **3rdalbum said:**
> Wolfen69 is correct - you only need a firewall on Windows because it has vulnerable services listening for incoming connections. On Ubuntu, there's nothing listening for incoming connections unless you install something that does. Hence, a firewall will do nothing that your computer isn't already doing (dropping incoming connections).

Or, to use an analogy: If all your household appliances are solely battery-powered, you don't need a surge protector.

You guys ever heard of controlling your outbound traffic ? You guys are talking about things coming in, there is an outbound path also.

exploited code configuring its own port ?

Ubuntu is as "secure" as any other consumer OS, but i dont want to get into that whole argument over again ;-)

A firewall is useful and recommended anyways whether or not you have no "open ports".

As for GRC shields up then, NO COMMENT.

Read here on some more information on why you might want one

[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

and on how to configure with various options

[http://ubuntuforums.org/showthread.php?t=1876124&page=2](http://ubuntuforums.org/showthread.php?t=1876124&page=2)

DT speaks alot of sense.

I dont want to enter into an argument here, i am a keen Linux advocate, but the whole Ubuntu is very secure is a flawed argument, the user/admin is in control of their system and ultimately you need to take steps to ensure security as much as possible within the confines of ease of use and funtionality.

But at end of day its all choice.

Peace

---

