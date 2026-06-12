---
title: "UBUNTU 12.01 Problems"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by safir on 2012-11-18
I upgraded from Ubuntu 12.04 to Ubuntu 12.1. But have some problems. First of all if I log in using Ubuntu, I get a screen but nothing else. Pointing the mouse over the screen is supposed to show the hidden icons or applications. I see nothing. I can log in using Gnome classic and am able to use the computer.  In ubuntu 12.04 I had installed an HP printer which is attached to a windows XP computer and it worked fine without any problem but in Ubuntu 12.1, the printer has disappeared. I can not install this printer anymore. When I try to install, a window titled gksudo Gnome-cups-Manager. it gives the following message: "FirewallD is not running. Network printer detection needs mdns, IPP, IPP-client and samba-client enabled on firewall". How do I do that? Also On the top menu bar computer or _user name has disappeared. Can anyone help in solving these problems.

---

### Post by newb85 on 2012-11-18
First, you should know that the release is 12.10, not 12.1 or 12.01.  The number before the decimal is the year of release and the number after is the month.  12.10 was released in October.

I've done little with 12.10, but I have encountered (accidentally created, actually) a situation where Unity didn't show up because it was disabled in compiz.

If you can bring up a terminal in the normal Ubuntu session, try installing and running compizconfig-settings-manager:

```
sudo apt-get install compizconfig-settings-manager
ccsm
```

Once you have CompizConfig open, go to Preferences (along the left side) and make sure that the Unity profile is selected.

---

### Post by safir on 2012-11-18
Thanks newb85. I have changed the profile to unity using your suggestion. I will let you know if it solved the problem, once I reboot the computer.

---

### Post by safir on 2012-11-18
I forgot to mention that I did make a mistake in the title of my post. It should be UBUNTU 12.10 not 12.01. Thanks.

---

### Post by safir on 2012-11-19
> **newb85 said:**
> First, you should know that the release is 12.10, not 12.1 or 12.01.  The number before the decimal is the year of release and the number after is the month.  12.10 was released in October.

I've done little with 12.10, but I have encountered (accidentally created, actually) a situation where Unity didn't show up because it was disabled in compiz.

If you can bring up a terminal in the normal Ubuntu session, try installing and running compizconfig-settings-manager:

```
sudo apt-get install compizconfig-settings-manager
ccsm
```Once you have CompizConfig open, go to Preferences (along the left side) and make sure that the Unity profile is selected.


I did exactly what you said but no luck. I am still not able to find the network printer. How do I enable the various services needed for network printer search in the firewall.

---

### Post by newb85 on 2012-11-19
In your initial post, you mentioned two problems.  (Generally, it's recommended to post one problem per thread.)  First, Unity wasn't displaying, and second, you were having trouble with a network printer.  My instructions were only intended to address the first problem.

---

### Post by safir on 2012-11-28
> **safir said:**
> I upgraded from Ubuntu 12.04 to Ubuntu 12.1. But have some problems. First of all if I log in using Ubuntu, I get a screen but nothing else. Pointing the mouse over the screen is supposed to show the hidden icons or applications. I see nothing. I can log in using Gnome classic and am able to use the computer.  In ubuntu 12.04 I had installed an HP printer which is attached to a windows XP computer and it worked fine without any problem but in Ubuntu 12.1, the printer has disappeared. I can not install this printer anymore. When I try to install, a window titled gksudo Gnome-cups-Manager. it gives the following message: "FirewallD is not running. Network printer detection needs mdns, IPP, IPP-client and samba-client enabled on firewall". How do I do that? Also On the top menu bar computer or _user name has disappeared. Can anyone help in solving these problems.
After eading RuarkReynolds post in another section, I followed his suggestion to install the printer. His suggestion was to open  terminal and type  system-config-printer then hit enter. Then hit Add Printer. This worked and I was able to install my network printer.

---

