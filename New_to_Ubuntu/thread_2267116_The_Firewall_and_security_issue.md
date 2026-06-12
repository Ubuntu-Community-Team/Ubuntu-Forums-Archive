---
title: "The Firewall and security issue"
date: 2015-02-27
forum: New to Ubuntu
---

### Post by xaqubz on 2015-02-27
Though i am not new to ubuntu but i am not that well equipped with knowledge and skills of linux. I am using Ubunutu 14.04 LTS and want my system to be safe and secure while browsing the internet from malwares and Trojans etc I have installed a firewall Gufw but when i boot the system it doesn't start automatically i have to manually start it. second thing which i don't understand is when i change the tab of Outgoing to "reject" on the app i can not even browse the internet. If somebody help me with this i have dropbox installed also and i don't want to make any changes to that as well 
[U]I wanted to upload the screenshot of the Gufw but unable to do
Thank you in advance [/U]:p

---

### Post by JeQhdMD on 2015-02-27
Well XaQubz, . . . the best way to assure your linux is safe and secure is just to run it the way the Debian and Ubuntu development teams have set it up.   Customization of firewalls or other security configuration is not required for standard use, including use of Dropbox (which is already integrated into the Files program (aka Nautilus) and the web browser of you choice.

GUFW is only the graphical front end to UFW (uncomplicated fire wall) which is a command line front-end to IPtables (the firewall) which is pre-installed on Linux distributions including Ubuntu.  It is supposed to be used to customize the firewall for things such as "port forwarding" . . . or opening certain ports to listen for specific traffic or accept data from group RPG's (role playing games etc.).

Best thing to do - - - go to YouTube and search for gufw or ubuntu firewall and you will then understand what you are trying to do . . . in other words, you must learn the minimum basics IF you want to really administrate your system.

Here you go . . . the basics from a good source:   [https://www.youtube.com/watch?v=zp0tg6popQ0](https://www.youtube.com/watch?v=zp0tg6popQ0)

---

### Post by deadflowr on 2015-02-27
Well gufw is simply a frontend of ufw(uncomplicated firewall) which in turn is a frontend of iptables/netfilter.
From memory, I remember it always stating as off after booting.
Typically you can run the ufw terminal command to see the actual firewall state with
```
sudo ufw status
```
and even more detail with
```
sudo ufw status verbose
```
active = on, and inactive = off

> second thing which i don't understand is when i change the tab of Outgoing to "reject" on the app i can not even browse the internet.
I don't know what is hard to understand about this, you set it to reject outgoing connections, so that's what it is doing. 
You might look into setting some exceptions/rules for that, like allow for port 80 or http/https. Or reset it to allow outgoing altogether...

Edit: Partially ninja'd by my own slowness.

---

### Post by sandyd on 2015-02-27
> **xaqubz said:**
> Though i am not new to ubuntu but i am not that well equipped with knowledge and skills of linux. I am using Ubunutu 14.04 LTS and want my system to be safe and secure while browsing the internet from malwares and Trojans etc I have installed a firewall Gufw but when i boot the system it doesn't start automatically i have to manually start it. second thing which i don't understand is when i change the tab of Outgoing to "reject" on the app i can not even browse the internet. If somebody help me with this i have dropbox installed also and i don't want to make any changes to that as well 
[U]I wanted to upload the screenshot of the Gufw but unable to do
Thank you in advance [/U]:p

Welcome to the forums.

You can upload screenshots by clicking on 'Manage Attachments'

Now, about the firewall...

By default, all ports in the firewall are closed. They are only opened when something is listening at the port. This behavior itself is quite secure unless you have services listening at the port that you don't want others to access. See [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177) for more info.

You can view open ports & connections on your computer by runnning
```
lsof -Pni
```

Gufw is a graphical user interface for ufw, so you can just set ufw to turn on at boot, which will load the rules
```

sudo ufw enable
```

When booted, check the status of ufw with
```

sudo ufw status
```
If you block outgoing traffic in Gufw, then outgoing traffic from your browser will be blocked as well.

---

### Post by Lars Noodén on 2015-02-27
As JeQhdMD mentions, GUFW is only a GUI for UFW.  Neither GUFW or UFW have to be running, they are just one possible UI for iptables which runs all the time whether you want it to or not.  However, the changes you make via GUFW or UFW stay in effect, even across reboots, until you change them.  So if you quit GUFW after changing something you can then go to the terminal and look at the changes through iptables:

```

sudo iptables-save | less

```

So you can see that the actual GUFW utility does not have to be running for the iptables rules that it set to be in effect.  

Firewalls are overrated.  Read up on how they work and what they do and it will become painfully obvious.  

After you've read and experimented enough that the firewall loses its mystique, you might turn your attention to apparmor.  It can't yet specify which ports or ranges of ports can or can't be used by an application, but it can currently specify which parts of the file system it can access.

---

### Post by xaqubz on 2015-03-01
Dear [COLOR=#000000]**JeQhdMD , **[/COLOR][COLOR=#C61919]**deadflowr, **[/COLOR][COLOR=#DD4814][COLOR=#C61919][sandyd]("http://ubuntuforums.org/member.php?u=717412") and L[/COLOR][/COLOR][ars Noodén]("http://ubuntuforums.org/member.php?u=168643")[COLOR=#000000]  [/COLOR]
[COLOR=#000000]Thanks for the time your replies cleared my understanding, I think i dont need to mess with the already available configuration that is already pre-configured coz thats delivering what i am expecting. Any how thank you for your your replies and god bless you all.. [/COLOR]:popcorn:

---

