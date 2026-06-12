---
title: "Security"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by Merisi on 2011-09-15
I'm still fairly new to Ubuntu and I'm getting concerned by lack of security as I'm pretty much unprotected at the moment.  Is there anything that I should be doing and is there anything I could be doing to tighten security?

---

### Post by haqking on 2011-09-15
> **Merisi said:**
> I'm still fairly new to Ubuntu and I'm getting concerned by lack of security as I'm pretty much unprotected at the moment.  Is there anything that I should be doing and is there anything I could be doing to tighten security?

Hi and welcome .

Linux does not suffer from Viruses like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

See here for **Anti-Virus** information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Then these stickies:
security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Also see about sudo and why root account is disabled by default in Ubuntu:

**ROOTSUDO** **(if you only read one thing read this)**
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


Have fun

Regards

haqking

---

### Post by gandaran on 2011-09-15
> **Merisi said:**
> I'm still fairly new to Ubuntu and I'm getting concerned by lack of security as I'm pretty much unprotected at the moment.  Is there anything that I should be doing and is there anything I could be doing to tighten security?
relax, using Ubuntu just as it is safe, you are better protected with Ubuntu than using windows with all the antivirus, antispyware and malware applications, you don't need all that, Ubuntu is secure and safe.

---

### Post by haqking on 2011-09-15
> **gandaran said:**
> relax, using Ubuntu just as it is safe, you are better protected with Ubuntu than using windows with all the antivirus, antispyware and malware applications, you don't need all that, Ubuntu is secure and safe.


That can be slightly misleading to a newcomer leading them to a false sense of security.

It is very important to understand that concepts of RootSudo for example and the fact that no matter how safe the OS maybe that scripts and such can still run in a browser and capture passwords etc.

yes Linux is more secure by default due to no Open ports and file permissions being different to other OS's but a statement of you will be fine** it is secure and safe** is a little misleading. IMO

---

### Post by Merisi on 2011-09-15
Thank you for the information.  I probably should have mentioned a concern I have with UFW as I installed it and allowed all incoming and outgoing and then I uninstalled it after having some problems with it and I'm concerned I've left all my ports open.

---

### Post by haqking on 2011-09-15
> **Merisi said:**
> Thank you for the information.  I probably should have mentioned a concern I have with UFW as I installed it and allowed all incoming and outgoing and then I uninstalled it after having some problems with it and I'm concerned I've left all my ports open.


ports being open and there being a service listening on the port is a different thing.

from command line just type:

```
sudo ufw enable
``````
sudo ufw default deny
```and anyways your Router is likely protecting you so i refer you back ot my OP where in the firewall section i mention they are not necessarily needed.  If your router wont forward an incoming packet for port 22 say then it wont get to your machine if the port is open anyways (in theory)

---

### Post by Merisi on 2011-09-15
Thanks for all your help haqking it's very much appreciated.  Unfortunately I'm totally baffled by AppArmor.  Do I download it or does it come with Ubuntu?

---

### Post by haqking on 2011-09-15
> **Merisi said:**
> Thanks for all your help haqking it's very much appreciated.  Unfortunately I'm totally baffled by AppArmor.  Do I download it or does it come with Ubuntu?


The links were for information and for you to get a primer on security.  read them all first, the apparmor link tells you that is is installed by default.

NO need to do everything there, no need to setup apparmor, it is just someting to bear in mind as you get more familiar with Ubuntu, same with Tor etc

Just make sure you read the RootSudo link over and over until you are sure you understand it, read the AV links so you understand AV in the Linux world and then just be vigilent and read the Security stickies.  You might consider Noscript addon for firefow and Adblock also.

The best defence in any OS is a vigilant and common sense using USER, Linux is by default secure yes but can easily be insecured, as Windows is by default often a little less secure but can easily be made Secure.

Enjoy

---

### Post by Merisi on 2011-09-15
Thanks haqking.  I'm a big fan of No Script and Ad Block and wouldn't surf without them.  I also use Request Policy, Browser Protect, Cookie Whitelist, with Buttons, Flagfox, WOT and Ghostery too.  It's out of interest in FF addons that I came to Ubuntu.  I don't think you can ever be too secure.

---

### Post by haqking on 2011-09-15
> **Merisi said:**
> Thanks haqking.  I'm a big fan of No Script and Ad Block and wouldn't surf without them.  I also use Request Policy, Browser Protect, Cookie Whitelist, with Buttons, Flagfox, WOT and Ghostery too.  It's out of interest in FF addons that I came to Ubuntu.  I don't think you can ever be too secure.

No worries, hope the information helps, alot of reading i know but there is no magic bullet solution to security, it is an ongoing process and works best in a layered approach and without ignorance, always being aware that a networked device is never 100% secure is the best knowledge to have cause that makes you vigilant ;-)

Peace

---

### Post by Dangertux on 2011-09-15
A side note on Apparmor since everything else was pretty much addressed. There are two aspects to Apparmor, the actual apparmor service which is installed by default. Then the profiles which apparmor enforces.

Every application that you want apparmor to "protect" needs a profile. Depending on the application there may be a premade profile for apparmor. Otherwise you will have to go through a fairly time consuming process of generating an apparmor profile. For most common applications there are pre-created profiles. 

I believe bodhi.zazen has some on [his site]("http://www.bodhizazen.net") also there is a large repository of profiles here.

[http://apparmor.opensuse.org/profiles/find_by_name](http://apparmor.opensuse.org/profiles/find_by_name)

Hope that helps.

---

