---
title: "Firestarter"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by philk949 on 2008-07-30
Hi
I installed Firestarter firewall. Does it have full Intrusion Detection System features and if so, how can I prove that access is denied to untrusted sources and that attempts have been detected?
Thanks
Phil

---

### Post by hyper_ch on 2008-07-30
firestarter is not a firewall!

Are you sure you need to alter the default rules in iptables?

---

### Post by flytripper on 2008-07-30
It says its a firewall on the first tab you see on startup!!

---

### Post by gjoellee on 2008-07-30
I have heard firestarter is a dead project...:confused:

---

### Post by hyper_ch on 2008-07-30
> **flytripper said:**
> It says its a firewall on the first tab you see on startup!!

Nevertheless it isn't a firewall and my other question still remains. Is the TO sure he needs to alter teh default rules?

---

### Post by tinny on 2008-07-30
Firestater is a GUI tool that interfaces with IPTables. (the underlaying firewall)

It doesnt provide intrusion detection.

For intrusion detection you need to look at something like [OSSEC]("http://www.ossec.net/").

But why worry about intrusion detection? With a standard Ubuntu install you are WAY safer than if you where using windows!


Safe computing the Ubuntu way.
[https://help.ubuntu.com/8.04/keeping-safe/C/index.html](https://help.ubuntu.com/8.04/keeping-safe/C/index.html)

---

### Post by Sef on 2008-07-30
> But why worry about intrusion detection? With a standard Ubuntu install you are WAY safer than if you where using windows!

Because it would make the computer that they are on even safer.

---

### Post by philk949 on 2008-07-30
To hyper_ch:
1. No, I'm not sure I want to alter anything, including iptables (please try and remember that you're in the Absolute Beginners Forum)
2. It seems to be a bone of contention as to whether or not Firestarter is a firewall - do we have a definitive answer on this?
3. I need to install a firewall and demonstrate its functionality for a class project. Can you or anyone else advise me on this?
4. What's a TO?

Thank you

Phil

---

### Post by Sef on 2008-07-30
> 2. It seems to be a bone of contention as to whether or not Firestarter is a firewall - do we have a definitive answer on this?

It is not a firewall, but, as stated, a GUI for IPTables, which is a firewall.

> 3. I need to install a firewall and demonstrate its functionality for a class project. Can you or anyone else advise me on this?

IPTables can be manipulated via the terminal.  [Netfilter/iptables project]("http://www.netfilter.org/")

---

### Post by philk949 on 2008-07-30
IPTables can be manipulated via the terminal.[/QUOTE]

I'm sure it can, but as an absolute beginner, I must once again ask for advice on how to go about this

---

### Post by Sef on 2008-07-30
> I'm sure it can, but as an absolute beginner, I must once again ask for advice on how to go about thisI'm sure it can, but as an absolute beginner, I must once again ask for advice on how to go about this

That's why I added the link in that post.

---

### Post by philk949 on 2008-07-30
Thank you sef. My mistake - posts are over and under-lapping here.

Phil

---

### Post by hyper_ch on 2008-07-30
> **philk949 said:**
> 3. I need to install a firewall and demonstrate its functionality for a class project. Can you or anyone else advise me on this?
Well, question is what level of sophistication do you want to demonstrate? Furthermore it's also a question what your audience/class uses. If they all use Windows (for example) then they are probably more used to "program-based firewalls". Meaning that generally firewalls on windows are setup that certain applications may communicate with the outside world and/or accept also incoming stuff. It's all bound to the applications.
Iptables is rather a netfilter. You don't bind it to specific programs but to ports. E.g. if you have setup SSH server so that you can access your computer at home from work and if your computer at work has a dedicated IP then you might want to setup iptables in a way that only this specific IP can access it.

Anyway, I asked whether you actually need to set it up is because most of them time you don't need to worry about as there are no services listening and no programs phoning home normally with a default install of ubuntu. In your case, however, you need to set it up - so that you can show how it works.

As it's probably more a basic introduction/presentation I think firestarter should be ok to use - as it visualizes things. Telling the class a bunch of code lines and tell them the effects and showing according logs probably won't do much good.

> **philk949 said:**
> 4. What's a TO?
Thread Opener ;)

---

### Post by philk949 on 2008-07-30
> Telling the class a bunch of code lines and tell them the effects and showing according logs probably won't do much good.


No, it probably wouldn't, but man, it sure would be impressive.
But seriously folks. I have a reserve computer here running XP that I must still occasionally use for class work that's just too hard to translate into Linux. So, if I download a firewall for Windows, how would I go about testing its functionality?
Sorry to besmirch this forum with the W word, and I'll understand if you decline to participate further and simply thank you for your help thus far.

Phil

---

### Post by hyper_ch on 2008-07-30
Well, you could install on Win XP the Zonealarm Firewall and not configure it so far.

Then when you start internet explorer or opera or ff and want to surf the net, it will prompt you that the application tries to access the internet and you get then the choice of allowing it, disalloing it, allowing it for once...

Then you could install like uTorrent and then download Ubuntu through torrent. It should prompt you then again if uTorrent shall be allowed to access the net... and also whether it shall be allowed to accept incoming connections.

If you have a linux box you could then try to access windows with different ports using telnet.

The ZA should prompt for each if you want to allow it or not.

---

### Post by philk949 on 2008-07-30
Thanks hyper_ch

I'll give that a whirl. Wish me luck.

Phil):P

---

### Post by bodhi.zazen on 2008-07-30
Just a few quick comments.

One problem with firestarter is that it runs as root and as such is a potential security problem in itself. You should not use firestarter to monitor network traffic.

Second firestarter is , IMO, depreciated and you should use UFW 

for basic security see :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by tinny on 2008-07-30
> **bodhi.zazen said:**
> 
You should not use firestarter to monitor network traffic.


If you do go with a IPTables based firewall solution you can log the network traffic to the terminal

FYI
[https://help.ubuntu.com/community/IptablesHowTo#Logging](https://help.ubuntu.com/community/IptablesHowTo#Logging)

> 
Second firestarter is , IMO, depreciated and you should use UFW 

for basic security see :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

The CVS repository for Firestarter hasnt had any commits for about 5years!!! So yep looks like quite an inactive project.

UFW, quite complicated for noobs. My Dad could use Firestarter but not UFW :(

---

### Post by Vivaldi Gloria on 2008-07-30
> **tinny said:**
> UFW, quite complicated for noobs. 

It's easy once you read

```
man ufw
```

Especially read the EXAMPLES section.

---

### Post by bodhi.zazen on 2008-07-30
> **tinny said:**
> UFW, quite complicated for noobs. My Dad could use Firestarter but not UFW :(

No, I have to disagree with that statement. UFW will take some reading, but it is failry straight forward.

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

---

### Post by tinny on 2008-07-30
> **Vivaldi Gloria said:**
> It's easy once you read

```
man ufw
```

Especially read the EXAMPLES section.

I dont have a problem with it. 

But for someone (my Dad) that just wants to use a computer the main stream way (GUI) UFW is complicated. There needs to be a non CLI solution for functions like this, otherwise Linux will continue to be in a very distant second place.

---

### Post by Tom--d on 2008-07-30
Want a GUI for UFW?

Well here it is:

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

Download the .deb for it.


Again.
Do not use Firestarter!
Its dead.
Hasn't been updated for years.

iptables is the firewall.
Firestarter, ufw and others are just programs which configures the firewall. Thats all.
You can directly configure iptables but its complicated.

---

### Post by RuleMaker on 2008-07-30
I used firestarter before, now I use UFW, but somebody mentioned on the first page of this tread that firestarter will alter my iptable, is there some way to rollback those changes and is there a need to do that, i mean will that have any bad effect to computer's security?

---

### Post by Tom--d on 2008-07-30
> **RuleMaker said:**
> I used firestarter before, now I use UFW, but somebody mentioned on the first page of this tread that firestarter will alter my iptable, is there some way to rollback those changes and is there a need to do that, i mean will that have any bad effect to computer's security?

To completely remove Firestarter's is to purge the package.
```
sudo apt-get remove firestarter --pruge
```

and to clear all iptables rules would be
```
sudo iptables -F
```

but really, purging firestart is only needed.

---

### Post by bodhi.zazen on 2008-07-30
> **RuleMaker said:**
> I used firestarter before, now I use UFW, but somebody mentioned on the first page of this tread that firestarter will alter my iptable, is there some way to rollback those changes and is there a need to do that, i mean will that have any bad effect to computer's security?

Uninstall firestarter :

```
sudo apt-get remove --purge firestarter
```

reboot

---

