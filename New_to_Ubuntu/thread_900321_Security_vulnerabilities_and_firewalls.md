---
title: "Security vulnerabilities and firewalls"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by ChocolateChip_Wookie on 2008-08-25
Hello all,

I have made several converts to Linux over the last couple of months, but one person has asked a question which I just cannot answer?

We all know that Windoze comes with a built in firewall and generally, it is a good idea to have this active along with apropriate virus and spam checkers. This is because of the possibility of someone either invading your computer through TCP/IP or downloading some sort of trojan keylogger onto your system.

My question is this...is it necessary to have a firewall under Linux? If so, what firewall should we be using? Can your computer be invaded by using a port sniffer or by connecting through LMhosts using netstat? How far does the security within Linux protect you?

Can anyone advise?

Regards

---

### Post by ajgreeny on 2008-08-25
Linux has a firewall called iptables which is installed by default in ubuntu and unless you are running a server system needs no more configuration, it just works without any action being needed.  If you are interested in testing it go to [http://www.grc.com/intro.htm](http://www.grc.com/intro.htm) and do a port scan.  My machine is always invisible to the net, and I suspect yours will be too.

---

### Post by WRDN on 2008-08-25
Ubuntu already has a firewall installed, called iptables. The port settings (etc) can be altered using UFW (Uncomplicated Firewall), which is installed but disabled by default. An alternative for configuration is Firestarter, which is a GUI based configuration tool. For most usage, you don't need to worry about altering the firewall, as by default, no services are listening.

---

### Post by ChocolateChip_Wookie on 2008-08-25
Verrry interesting...

I have just done the port scan as suggested and I am totally invisible. Wow! Just Wow! OK. That takes care of passing nefarious activities, but what about direct intrusions using your IP address which can be taken via netstat -n. Does Linux even have something equivalent to an LMHosts file?

Is it possible to download a keylogger or similar which works in the background? I understand that viruses are almost unheard of in the wild, but would something written for windows work in Linux?

---

### Post by Paqman on 2008-08-25
Kind of makes you wonder just what the heck is going on with the default setup on a Windows box. A computer *should* be secure in it's default configuration, unless the user does something to make it less so. Windows seems to start off insecure by default, and demands you take action to correct it.

Wikipedia has an article on [Linux Malware](http://en.wikipedia.org/wiki/Linux_Virus) that touches on cross-platform malware, check the references for more info. Bottom line is that if you stay current with security updates, you should be protected.

---

### Post by ChocolateChip_Wookie on 2008-08-25
The convert I am working on at the moment uses McAfee and boy does it eat his system resources. He says that it drives him nuts downloading security updates all the time and keeps giving him esoteric warnings that he doesnt understand. I told him that I rather thought that it had all been taken care of within Linux but didnt know the exact ins and outs. I have been a windows user all my life (well, since they killed OS2) and it is only recently I have plucked up the courage to switch to Linux. I must say that I am a fervent convert and refuse to go back to Windows again. I have found that I must run it for certain things like Serif PagePlus, but other than that. refuse to continue to pay my taxes to Bill Gates et al for a faulty system with enough security holes to put swiss cheese to shame! I have been ( in my younger days) something of a hacker and I know first hand just how vulnerable a standard install of windows is, but I never thought that Linux would have a firewall so powerful and so well written that not only was I totally oblivious to it's presence, but it just works with no appreciable drain of resources. I am in awe. Just wait until I tell my other converts and fellow travellers. It's my new mission in life to bring as many as possible to the light...:-)

---

