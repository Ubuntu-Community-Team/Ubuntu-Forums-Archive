---
title: "Virus and or Firewall Needed or what?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Ed J on 2008-07-12
I've just spent most of the day configuring my Ubuntu box and I'm happy with it, so far everything is working, media is playing, printers printing, I even used ndiswrapper to set up my unsupported wireless ethernet card.  Configuration is necessary, this isn't magic. This forum is awesome.
   I'm a Windows guy since the beginning. All the way, in love with Office, part-time .NET developer dabbling, never installed Mozilla browser on my Win PC. Call me skeptical but I just can't shake the feeling that I have to install some anti-virus memory hog and a annoying software firewall to protect me from the evils of spyware, pop-ups, and infection.
   I've read quite a bit of material in the last couple days about how great Ubuntu/Debian/GNU/Linux is and how it is almost impervious to virus infection, attacks, and other issues. So I was wondering if I could get some feedback from on what semi-paranoid home users are doing.  Running apparmor? Firestarter? ClamAV? Nothing? 

Thanks
Ed J

---

### Post by Xerp on 2008-07-12
Obviously viruses / spyware and whatnot aren't a worry if you're using Linux, but ClamAV is great if you have Windows machines you don't want to pass infected files on to. 

Firefox with adblock & noscript is something I run on Ubuntu. I don't like ads :)

One day I'll get around to setting up a firewall on my desktops, but with no externally accessible services running its not a top concern for me.

If I'm paranoid then I set up Linux boxes on the perimeter. Snort is great for intrusion detection, Nagios will help me monitor the essentials, ClamAV, Razor, DCC, Spam Assassin and postfix help keep my mail clean.

---

### Post by WRDN on 2008-07-12
For the vast majority of the time (likely never) Linux/ Ubuntu wont be infected by a virus itself, though some do exist. This is because of the levels of security and access levels. 
You could use antivirus software, though it would really only be needed if you share files with a Windows partition or other computers on a network running Windows. It is also worth scanning a file if you're going to email it to a person using Windows.
A good example of antivirus software is ClamAV.

As for the firewall, Ubuntu has its own firewall called iptables. It is unlikely a person will gain access to the computer because, by default, no one can listen on the ports. If you want to manage the firewall yourself using a GUI, you could use Firestarter (its in synaptic).

---

### Post by Vivaldi Gloria on 2008-07-12
In default ubuntu desktop install there is no service/program listening to any port. So I wouldn't even bother with a firewall.

---

### Post by PHATSPEED7x on 2008-07-12
I was woundering this myself. So there isn't the vires threat to linux, like windows...

---

### Post by MattBD on 2008-07-12
Assuming you're running Hardy, then AppArmor is preinstalled and running (although if you prefer you can replace it with SELinux).
As for firewalls, Hardy already has an easy to use CLI firewall app called uFW (short for uncomplicated firewall) preinstalled. It's very easy to get working, so you might as well use it. Just enter the following:
```
sudo ufw enable
```
and it will start up next time you boot. I used to use Firestarter, but uFW is very straightforward so I prefer that now. I would definitely have a firewall though.
As for antivirus, that's only really an issue if you have to share files with a Windows box, such as if you were using your Ubuntu box as a server. Otherwise, there's little point IMHO.

---

