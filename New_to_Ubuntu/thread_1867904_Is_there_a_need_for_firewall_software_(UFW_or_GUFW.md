---
title: "Is there a need for firewall software (UFW or GUFW)"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by cozumel on 2011-10-23
I have hardware firewall.  I'm not logged in as Admin (disabled by Ubuntu) and need to use sudo to gain temporary admin privileges.

So, back to the question in the thread title.  Is there any need?  (Please give some detail).

Thanks :)

---

### Post by haqking on 2011-10-23
> **cozumel said:**
> I have hardware firewall.  I'm not logged in as Admin (disabled by Ubuntu) and need to use sudo to gain temporary admin privileges.

So, back to the question in the thread title.  Is there any need?  (Please give some detail).

Thanks :)

UFW and GUFW are merely interfaces to the netfilter firewall in the linux kernel.

whether you need one depends on your services and setup (such as behind a router firewall)

and has little or nothing to do with your admin/sudo status.

and nothing is 100% secure

read the security stickies for more information in my signature

---

### Post by sadaruwan12 on 2011-10-23
UFW is the command line way and the GFUW is the graphical way but normally linux come with all the ports closed only if want we can open one to do that we could use one of these applications.

But you're behind a hardware firewall but to be on the safe side just install one from above and configure the iptables firewall (this comes installed as a default) 'cos theres nothing 100% secure in this cyberspace.

---

### Post by haqking on 2011-10-23
> **sadaruwan12 said:**
> **UFW is the command line way and the GFUW is the graphical way but normally linux come with all the ports closed only if want we can open one to do that we could use one of these applications.**

But you're behind a hardware firewall but to be on the safe side just install one from above and configure the iptables firewall (this comes installed as a default) 'cos theres nothing 100% secure in this cyberspace.

It is not that ports are closed, it is they have no services listening on them, when we install a service say ssh then port 22 now has the ssh daemon listening on the port

---

### Post by 1clue on 2011-10-23
A standard home firewall appliance (external cable modem+switch with NAT or similar) with default settings is pretty good security.

The exception is wireless.  IMO the manufacturers of these home devices completely ignore the security risk inherent in a wireless device.  There was actually a guy poaching my service at one point.  I don't so much care that my neighbors are pirating my WIFI but the idea that somebody drives up and parks in front of my house and starts banging on his laptop really bugs me.  It helps a bit if you use a better encryption, but I still fret about a more sophisticated pirate.

My personal preference is for a firewall on a separate device which does nothing more than firewall and routing.  To do that right, you need to be able to fence your wireless network off from the wired network using separate rules.  I haven't seen stock home router software that does that yet.  I'm trying dd-wrt right now, which is a linux-based OS for home wireless routers especially by Cisco/Linksys.  It lets me fence my wireless away from my wired network and offers full Internet access with limited access to the wired network, which is a good thing because then I don't have to be so careful about what ports are open on my private machines.

All this COULD be managed by just not opening any ports on your home machines, but if you have a family that isn't always feasible.  A curious teenager doesn't likely think much about a security exposure.

IMO the firewall on a workstation is every bit as difficult to manage as an external one, but it only works on that one computer.  If your home network is untrusted then you probably want a firewall on every device, but then you start thinking about phones, printers, blu-ray devices, TVs and even a refrigerator then that gets out of control too.

---

### Post by philinux on 2011-10-23
> **cozumel said:**
> I have hardware firewall.  I'm not logged in as Admin (disabled by Ubuntu) and need to use sudo to gain temporary admin privileges.

So, back to the question in the thread title.  Is there any need?  (Please give some detail).

Thanks :)

As far as I am aware this is still valid.

 [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by bodhi.zazen on 2011-10-23
> **philinux said:**
> As far as I am aware this is still valid.

 [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

So is this page : [https://wiki.ubuntu.com/SecurityTeam/Policies#No_Open_Ports](https://wiki.ubuntu.com/SecurityTeam/Policies#No_Open_Ports)

So a better question is what do you want to use a firewall for ? What services are you running ? Public or private ? what do you want to achieve with a firewall ?

---

### Post by cozumel on 2011-10-23
Thank you for the info netfilter and iptables.  Exactly the type of thing for which I was searching.


Just that in the past, in Windows, I knew actually what services were running, would disable those that were not required and create policies accordingly.

All the info and links provided above should keep me going for a while.  Need to feel safe and to be safe.  Especially when using my laptop on public networks etc.  And yes, I do understand there is no such thing as 100% secure.  Anyone determined enough who wants to target a specific machine or network can gain access with perseverance.  That is why I want to be looking at security since I recently switched over to Linux (all good so far).  About 10 days and counting lol

---

### Post by cozumel on 2011-10-23
> **bodhi.zazen said:**
> So a better question is what do you want to use a firewall for ? What services are you running ? Public or private ? what do you want to achieve with a firewall ?To be a part of a packet of measures to ensure my data is safe and network security is not compromised via backdoors or zerodayers etc.  Future hardening is something I will look into a bit further down the line (steep learning curve as I am used to Windows, but principles are same I guess).
I don't actually know what services are running or what they do yet, I'm too much of noob (only ten days in), so I need to do a lot of reading on that.
Private network but public networks mostly as I am always on the go.
Ensure that ports are closed or stealthed.

---

### Post by haqking on 2011-10-23
**> **cozumel said:**
> .  And yes, I do understand there is no such thing as 100% secure.  Anyone determined enough who wants to target a specific machine or network can gain access with perseverance**.  That is why I want to be looking at security since I recently switched over to Linux (all good so far).  About 10 days and counting lol

understanding this is the best approach to security, there are too many blanket statements of Linux is secure, yes it is secure but you need to understand the layered approach to security and the security mechanisms in Linux to take advantage of it.

The weakest link will always be PEBKAP - Problem Exists Between Keyboard And Person.

Peace

---

### Post by cozumel on 2011-10-23
While I'm thinking about, a little off-topic but still security related.

Say I've navigated to a website that I am unsure about and they have pdf documents of maybe (since this is Ubuntu) a PPA available for download.  How would I go about checking there is no malicious script before install or opening?

Or is there a sandbox or virtual environment in which the script can be run first?

---

### Post by Dangertux on 2011-10-23
> **cozumel said:**
> While I'm thinking about, a little off-topic but still security related.

Say I've navigated to a website that I am unsure about and they have pdf documents of maybe (since this is Ubuntu) a PPA available for download.  How would I go about checking there is no malicious script before install or opening?

Or is there a sandbox or virtual environment in which the script can be run first?

NoScript or NotScripts for your browser would be a good recommendation.

If you're feeling extra paranoid. You can explore SELinux Sandboxing or Apparmor 

[http://blog.bodhizazen.net/linux/selinux-sandbox/](http://blog.bodhizazen.net/linux/selinux-sandbox/)

that link is for SELinux but he has some really good Apparmor stuff on that site too, just take a look around.

Hope that helps.

---

### Post by cozumel on 2011-10-23
okay thanks everyone.  I have plenty of links with a ton of stuff to read through now.

Marked as solved

---

