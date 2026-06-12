---
title: "Firestarter Blocking Complete Access To The Internet"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by safeerahme@gmail.com on 2008-10-01
Greetings,

Hey I have been trying to get some help in setting up my Firewall. Everytime I use Firestarter it blocks complete inbound and outbound traffic, there are Polocies set at all.

Please help.

Thanks,
Safeer

---

### Post by Nepherte on 2008-10-01
Be sure that the option "allow most traffic, unless specified" (or something that looks like it) in the tab outbound policy is active. Are you sure you need firestarter in the first place? In most cases you don't need to fiddle with the iptables firewall settings. Firestarter is merely a gui, not the firewall itself.

---

### Post by safeerahme@gmail.com on 2008-10-02
Hello Nepherte,

First of all thank you for your prompt reply. I have disabled the Firestarter and now am able to browse fine however was wondering if we had some other Software which would protect me for any Hacks.

Thanks,
Safeer

> **Nepherte said:**
> Be sure that the option "allow most traffic, unless specified" (or something that looks like it) in the tab outbound policy is active. Are you sure you need firestarter in the first place? In most cases you don't need to fiddle with the iptables firewall settings. Firestarter is merely a gui, not the firewall itself.

---

### Post by Sef on 2008-10-02
> First of all thank you for your prompt reply. I have disabled the Firestarter and now am able to browse fine however was wondering if we had some other Software which would protect me for any Hacks.

Ubuntu comes with IPTables as a firewall.  It is a command line one.  Firestarter is simply a GUI for IPTables, i.e. you can use a mouse instead of the Terminal.

---

### Post by wolffangalchemist on 2008-10-02
ubuntu has a firewall built that is active by defalt it just doesn't have a user interface for tweaking it. 
your on Linux for jebus sake you have nothing to worry about your vertualy un-hackable.
if you file share with windows i would sugest installing clam-tk antivirus so you make sure no windows virals are in anything you share.

---

### Post by Thelasko on 2008-10-02
Firestarter is no longer being developed.  IMHO [Gufw ]("http://gufw.tuxfamily.org/index.html")is much better.  Hopefully it will make it into future Ubuntu releases.  You have to download the .deb files from the site, as the packages aren't in the repositories.

---

### Post by Sef on 2008-10-02
> your on Linux for jebus sake you have nothing to worry about your vertualy un-hackable.

That is not correct.  GNU/Linux is harder to hack than Windows, but it can be hacked.   

> your on Linux for jebus sake you have nothing to worry about your vertualy un-hackable.

In the repositories for a firewall gui, there is ufw.

---

### Post by safeerahme@gmail.com on 2008-10-03
Thanks a lot folks,

I installed the gufw firewall and am good to go now.

Cheers,
Safeer


> **safeerahme@gmail.com said:**
> Greetings,

Hey I have been trying to get some help in setting up my Firewall. Everytime I use Firestarter it blocks complete inbound and outbound traffic, there are Polocies set at all.

Please help.

Thanks,
Safeer

---

### Post by hyper_ch on 2008-10-03
why do you feel the need to alter the existing firewall anyway?

---

### Post by gaiterin on 2008-12-02
Hi! Gufw is in the Intrepid repository ;)
In terminal: sudo apt-get install gufw
Best regards!

---

### Post by kansasnoob on 2008-12-02
> **hyper_ch said:**
> why do you feel the need to alter the existing firewall anyway?

+1!

If in doubt just run the first three commands here:

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

Unless you have a complicated network you can then just forget about it! You'll be safer than anyone on Windows!

---

