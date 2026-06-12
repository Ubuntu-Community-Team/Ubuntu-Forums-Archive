---
title: "How secure is Linux?"
date: 2008-12-08
forum: Recurring Discussions
---

### Post by Graham1 on 2008-12-08
Hi

How secure is Linux out the box? (i.e default settings). Having moved from Windows, my first concern was to find a good firewall and antivirus to protect me. After reading various posts, I realised I didn't really need any antivirus. So my question is, is Linux (inc. other distro's) secure against todays internet threats?

:)

---

### Post by phidia on 2008-12-08
Maybe reading the Ubuntu wiki on antivirus [here]("https://help.ubuntu.com/community/Antivirus") will provide some answers for you. Generally the answer is yes but those that create viri and worms can't be predicted.

---

### Post by cmay on 2008-12-08
> **Graham1 said:**
> Hi

How secure is Linux out the box? (i.e default settings). Having moved from Windows, my first concern was to find a good firewall and antivirus to protect me. After reading various posts, I realised I didn't really need any antivirus. So my question is, is Linux (inc. other distro's) secure against todays internet threats?

:)

no more secure than the user is. no system is. but i have never any firewall or problems using the internet. i am online most the time and i do not have flash since its commercial licensed so therefor i do not trust it. i have noscript turned on and nothing happens to my interent or ubuntu. still if a user on a system with root admin rights goes ahead and do silly things then no system is secure. other than that you can safe use default ubuntu just as it is with out any worries. to read the link given in the above posts are very good idea also. they will answer most if not all questions you may have.

---

### Post by Graham1 on 2008-12-08
What worries me most is that if something did get downloaded/installed onto my system, does Ubuntu (or any other distro) offer any outbound protection? When I look at the methods of infecting Windows (using Comodo's Leak Test Suite), wouldn't something bad like this exist for Linux.

:)

---

### Post by phidia on 2008-12-08
Nothing is impossible however there is little to support the fear of infection that you are asking about. If there had been any significant outbreak of linux viri it would be newsworthy I believe.
[Wiki page]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses") on virus and linux(unix).

Having read most of what is at that wiki page it seems that if you are not installing packages from untrustworthy sources or running a server and you do the security updates you are fairly safe.

---

### Post by loell on 2008-12-08
> **Graham1 said:**
> What worries me most is that if something did get downloaded/installed onto my system.

:)

generally you're the one giving permission to what will be installed in your system, download from your trusted sources is one of the keys for better security.

---

### Post by shafi on 2008-12-08
> **Graham1 said:**
> What worries me most is that if something did get downloaded/installed onto my system, does Ubuntu (or any other distro) offer any outbound protection? When I look at the methods of infecting Windows (using Comodo's Leak Test Suite), wouldn't something bad like this exist for Linux.

:)

Its good if you google something like "Linux permissions" , ... , or read fully the chmod and chown man pages.

switch to root and try something like following, then see what will happen??
 chmod 000 * (Don't try this , this is just to show the chmod power :) )

ha ha ha ;)

---

### Post by russo.mic on 2008-12-08
If there was to be a virus on Linux, I believe it would have to take advantage of the most likely security hole of all, the social hack.

The idea here is, don't install software that you don't know what it is over the internet.

---

### Post by jimv on 2008-12-08
> **Graham1 said:**
> What worries me most is that if something did get downloaded/installed onto my system, does Ubuntu (or any other distro) offer any outbound protection? 

Outbound protection is overrated.  If something is on your system, it can disable your protection.

That said, if you're using a router for your internet access, you don't randomly open every executable someone sends you, and you're password is more complex than 12345, you'll be ok.

---

### Post by bodhi.zazen on 2008-12-08
Take a look at this :


[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

From there take a look at the intrusion detection thread , UFW, and AppArmor.

---

### Post by scottuss on 2008-12-08
Remember that a lot of companies make a lot of money from telling you how insecure Windows is, most products have [COLOR="Red"]BIG RED LETTERS[/COLOR] to worry you, stating that you're vulnerable to EVERYTHING! The same doesn't apply to Linux, just be careful not to download anything you don't trust 100% and you will be fine without antivirus / malware apps. Linux has a great firewall built in that's easy to configure via Firestarter (sudo apt-get install firestarter) If you're behind a router that's a plus point (regardless of O/S)

---

### Post by Graham1 on 2008-12-09
Thanks for all the replies :). Much appreciated. 

So bascially, I'm behind a wireless router/firewall and use a standard user account (only using root when prompted). I only install packages from the default repositories (via Ubuntu's package manager). Btw, does Ubuntu include/use a firewall (I can't find reference to a firewall within the menus) or should my hardware firewall/router be ok? Looks like I've got alot of reading to do.

Thanks

:)

---

### Post by Peter09 on 2008-12-09
Ububtu has a default firewall called iptables. It is command line driven. However there is a GUI which will configure it - its in the repositories and called firestarter.

---

### Post by bodhi.zazen on 2008-12-09
> **Peter09 said:**
> Ububtu has a default firewall called iptables. It is command line driven. However there is a GUI which will configure it - its in the repositories and called firestarter.

Firestarter is not the best of advice.

You can configure iptables with ufw, which is a command line tool, or gufw, which is a gui front end.

---

### Post by MarblePanther on 2008-12-09
Unless you are running a server, by default no ports are open/viewable by others.

Iptables is suitably configured for a standard user, though gufw is a nice and simple gui.

Also, do not worry about having any of these guis (firestarter, gufw, etc...) run on startup--they are only gui frontends to add rules.

Iptables will always run by default.

---

### Post by gjoellee on 2008-12-09
Linux is very secure. If you get a virus, the virus first of all has to be built for Linux. Most viruses are for Windows, and only a few of them may have an effect on Linux id you have a Windows emulator installed.

Because the default user is not not root (superuser), you do not have access to different parts of the system which may crash the system if edited. A virus does have to be trigged manually as root user to have any effect.

Don't worry. (If you want a virus in Linux it is hard to actually find one!)

---

### Post by Graham1 on 2008-12-09
Thanks guys for putting my mind at rest.

:-D

---

### Post by cardinals_fan on 2008-12-09
[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

A firewall guide.  Antivirus is always worthless anywhere.

---

