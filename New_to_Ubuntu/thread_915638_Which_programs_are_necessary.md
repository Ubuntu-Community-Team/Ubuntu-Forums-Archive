---
title: "Which programs are necessary?"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by drileysr on 2008-09-10
Hello forum, new old guy here. Installed ubuntu on a laptop given to me by my nephew last week and my question is with this operating system, do I need an antivirus, firewall, and spyware detectors like my old windows xp pro? If so, which are the recommended ones? When I was using xp pro I had zone alarm firewall, avast antivirus, and spybot s&d and spyware blaster. Can anyone help. Thank you. Geezer.

---

### Post by hyper_ch on 2008-09-10
(1) generally no antivirus needed
(2) you have a firewall, it's integrated in the kernel, by default it just let's everything pass and generally that is good
(3) no spyware detecotrs needed
-----
Recommended it to fortify your browser with the noscript addon.

Have a read here:  [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by kpkeerthi on 2008-09-10
You don't need any of those.

Your router is your best defence. Just make sure the ports that you don't need are closed in the router.

If you are sharing your linux computer with Windows folks, its probably a good idea to install an antivirus. Not that there are no linux viri in the wild. A linux antivirus can only scan and clean up windows viri so you don't accidently pass it on to windows. 
If you are using only linux, you not need any antivirus. See [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by Liviu-Theodor on 2008-09-10
Antivirus? you don't need it for Linux. But if you e-mail someone an Windows attachment, you can try clamAV (in the repository has the simple name of [FONT="Courier New"]Virus Scanner[/FONT]. Firewall? If you really want more security than the one provided by default in the Linux kernel (and which is good enough for many webservers), you can try firestarter. Antispyware is no needed in any way on Linux, because there isn't spyware for Linux.

---

### Post by zvacet on 2008-09-10
> you can try firestarter

No need for that.If you want you can enable [ufw.]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html")Maybe it is good idea to install rkhunter to check for rootkits.It is in synaptic.

---

### Post by 3rdalbum on 2008-09-10
> **zvacet said:**
> Maybe it is good idea to install rkhunter to check for rootkits.It is in synaptic.

If there are no outward-facing services like Apache, SSH or FTP, then there is no danger of rootkits.

Original poster: I have a link in my signature to "Linux Anti-virus" - it's actually an article that explains why Linux users don't get malware.

---

### Post by brian_p on 2008-09-10
> **kpkeerthi said:**
> You don't need any of those.

Your router is your best defence.

I find keeping my software up-to-date is all that is required.

> Just make sure the ports that you don't need are closed in the router.

And if you do not have a router or are not in control of it?

---

### Post by hyper_ch on 2008-09-10
> **brian_p said:**
> And if you do not have a router or are not in control of it?

Nothing to worry either... as long as you don't run any daemons there's nothing much to worry about.

---

### Post by brian_p on 2008-09-10
> **hyper_ch said:**
> Nothing to worry either... 

I'm aware of that. Its the idea of shifting firewall protection from the machine to the router which may be confusing to people.

> . . . . as long as you don't run any daemons there's nothing much to worry about.

I've never been the slightest bit worried about any of the services  I've offered.

---

### Post by hyper_ch on 2008-09-10
if no services are running and if the services that are running are secure, what do you need a firewall for?

---

### Post by billgoldberg on 2008-09-10
> **drileysr said:**
> Hello forum, new old guy here. Installed ubuntu on a laptop given to me by my nephew last week and my question is with this operating system, do I need an antivirus, firewall, and spyware detectors like my old windows xp pro? If so, which are the recommended ones? When I was using xp pro I had zone alarm firewall, avast antivirus, and spybot s&d and spyware blaster. Can anyone help. Thank you. Geezer.

Generally, no you don't need any anti-virus, spyware software, nor a firewall.

A firewall could be needed if you are running a server or something.

In that case try ufw (there is a gui availableo online for it called gufw). But normally you won't need it, especially if you have a hardware firewall( most routers have this)).

---

### Post by darrelljon on 2008-09-10
[There was discussion]("http://ubuntuforums.org/showthread.php?t=901335") about whether you should run antivirus software to protect Windows users and some Linux users (myself included) thought not.

---

### Post by brian_p on 2008-09-10
> **hyper_ch said:**
> if no services are running and if the services that are running are secure, what do you need a firewall for?

You don't. On a single machine it serves no good purpose.

---

### Post by drileysr on 2008-09-10
To all the forum folks kind enough to answer my post, thank you very much!!! Linux is very interesting and as I continue to use and learn it I'm sure I will be posting back soon. Again, THANKS.

---

### Post by drileysr on 2008-09-16
Thanks to all of you that replied to my post. The infomation was just what I needed. Thanks again. Since I'm new to linux and tinkering with it I'm sure I'll be back shortly with more questions. Thanks.

---

