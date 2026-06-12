---
title: "LF Ubuntu software suggestions"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by zaazz on 2011-11-02
Looking for information on: VPN, remote support software, Remote Desktop Software. etc. I'm trying to optimize a setup where I can send a ubuntu PC with someone and still be able to remote to it when he needs my help. Either by having him VPN into my network first, or by using other tools to do so. I need to be able to troubleshoot this workstation anywhere remotely.

I've been using Ubuntu and Kubuntu now for a few years. I know my way around the software packages and using the command line to dig through the systems directory structure looking for programs and running them from there as well. I had an idea this week about a project I'd like to do with a 3-4 year old Dell laptop.

Here's the background story:

My son is traveling and may be moving around for the next three years. Anyway, his mother and her husband are about as technically savvy as my grandparents so when they told the court they would provide him with "a computer" they didn't say it was almost worthless and took 30-40 minutes to power up. He can't load skype and play a game at the same time the system will crash. He does a lot of web based games but everything else I think I can get running using wine and other tricks.

What I'm looking for is an "optimal setup" for him. Some combination of remote desktop software plus a VPN client that would allow him to connect to my network and then I can remote to his workstation in order to troubleshoot any problems he may have with this system.

While this seems trivial to me to do in windows I am having a problem filtering through the many options and versions of this type of software out there on my Kubuntu work PC. So I decided to come here and see if anyone had some advice, suggestions, or even a guide on how this should be setup in order to make sure it's secure and unlikely that any other party is going to screw with this system.

---

### Post by Lars Noodén on 2011-11-02
Well, for the VPN, the obvious choice would be OpenVPN.  X11VNC and tightvncserver would be choices for remote access, or krfb/krdc.  VNC should be tunneled over the VPN or over SSH.

To get the most out of old, underpowered hardware, you can look at Lubuntu.

---

### Post by hailtothethief on 2011-11-02
I just want to add that you should have a contingency plan for when things just go completely bonkers (he breaks his xorg and suddenly can't connect to a network?).

Personally I'd [remaster a livecd]("https://help.ubuntu.com/community/LiveCDCustomization") with the software and configuration you choose. That way in case of emergency he can throw the livecd in and dear ol' dad can come to the rescue, even if his installation is broken beyond repair.

---

### Post by zaazz on 2011-11-02
hailtothethief,

That is an excellent suggestion.

---

