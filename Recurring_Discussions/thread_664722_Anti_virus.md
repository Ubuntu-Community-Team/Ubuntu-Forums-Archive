---
title: "Anti virus?"
date: 2008-01-11
forum: Recurring Discussions
---

### Post by dark_phantom on 2008-01-11
I've been using Ubuntu for about half a year now and have not used or installed a virus program.  Has anyone here have? If so, which one do you use.

---

### Post by steeleyuk on 2008-01-11
I don't use any and never have. If you really want to though try [ClamAV]("apt://clamav") (this is the command line variant). If you want a GUI, you'll also want [this package]("apt://clamtk").

---

### Post by #Reistlehr- on 2008-01-11
sudo chmod -x <file>

:D

I heard Panda had a good one. Cant tell you from personal experience though.

---

### Post by psoulocybe on 2008-01-11
search man....

you really don't need an antivirus sweet for your linux machine.  If you're networked with some windows machines and are transfering files back and forth it could help, but linux isn't really open to virus or spyware infections.

---

### Post by MartynA on 2008-01-11
Yeah, the only real reason you would need an antivirus prog is if you were acting storing files accessbile to windows computers, in which case it would be useful to check them before they infect said windows computers :)

---

### Post by dark_phantom on 2008-01-11
Yeah I know in Linux is not so much needed, but just wanted to know who did had it. :)

---

### Post by dcstar on 2008-01-12
> **dark_phantom said:**
> I've been using Ubuntu for about half a year now and have not used or installed a virus program.  Has anyone here have? If so, which one do you use.

I use ClamAV, basically to scan all my incoming e-mails (in Evolution) and let me know of all the Windows crap (as well as the "Spoofed" URLs) floating around.

I don't need much protection (if any), but it's interesting to see the stuff that still gets through the ISPs filters.

---

### Post by aBitLater on 2008-01-13
you DO need antivirus protection in linux.  Free scanners don't often provide "real-time" protection. You usually have to scan your drives manually.

You might try Avast from Alwil Company.  Google it for the home page.  Free and good package.  You can even get a free suite of products for your windows machines.

---

### Post by Sef on 2008-01-13
> you DO need antivirus protection in linux.

That is not correct, unless, as stated above, you are networked to Windows computers, and that is only so your GNU/Linux computer does not infect them.

aBITLater: If you want to refute my statement and the others here, please provide documentation for your belief that GNU/Linux needs anti-virus protection.   If you don't provide documentation, you will get an infraction for spreading FUD (fear, uncertainty, and doubt) and for being off-topic.

---

### Post by bodhi.zazen on 2008-01-13
> **Sef said:**
> That is not correct, unless, as stated above, you are networked to Windows computers, and that is only so your GNU/Linux computer does not infect them.

aBITLater: If you want to refute my statement and the others here, please provide documentation for your belief that GNU/Linux needs anti-virus protection.   If you don't provide documentation, you will get an infraction for spreading FUD (fear, uncertainty, and doubt) and for being off-topic.

+1

Anti-Virus scanning on Linux is of limited utility as there are no know linux viruses "in the wild" so there is essentially nothing to scan for.

In addition Antivirus is reactive, not proactive meaning it can not protect you from the next Linux virus until AFTER it is released, not before.

A potential use of linux antivirus is to "protect" windows or if you are running a mail server, and even then, IMO, Windows antivirus is better then Linux antivirus.

In the end, the choice is yours to make, but I would be willing to bet that the more experience one has with Linux (Ubuntu) the less one feels the need for scanning / for viruses.

=========================

@dark_phantom

Linux is different the Windows. Security is different.

See these links : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

Psychocats : [Psychocats :  Security on Ubuntu](http://www.psychocats.net/ubuntu/security)

---

### Post by HermanAB on 2008-01-13
I use a variation of this virus scanner:

#! /bin/bash
echo GNU AntiVirus version 0.0.0.2, Sirius Cybernetics Corporation, GPL 1971.
sleep 10
echo Now scanning....
sleep 50
echo Almost done...
sleep 10
echo Drum roll!
sleep 5
echo Woohoo! No viruses found!
exit 0

Save it in /usr/local/bin as gnuantivirussiriuscyberneticscorp 

make it executable with: 
$ sudo chmod 754 gnuantivirussiriuscyberneticscorp

then create a link to it from /etc/cron.hourly with: 
$ sudo ln -s /usr/local/bin/gnuantivirussiriuscyberneticscorp /etc/cron.hourly/gnuantivirussiriuscyberneticscorp

and Bob's your Uncle!

Cheers,

Herman

---

### Post by bodhi.zazen on 2008-01-13
> **HermanAB said:**
> I use a variation of this virus scanner:

#! /bin/bash
echo GNU AntiVirus version 0.0.0.2, Sirius Cybernetics Corporation, GPL 1971.
sleep 10
echo Now scanning....
sleep 50
echo Almost done...
sleep 10
echo Drum roll!
sleep 5
echo Woohoo! No viruses found!
exit 0

Save it in /usr/local/bin as gnuantivirussiriuscyberneticscorp 

make it executable with: 
$ sudo chmod 754 gnuantivirussiriuscyberneticscorp

then create a link to it from /etc/cron.hourly with: 
$ sudo ln -s /usr/local/bin/gnuantivirussiriuscyberneticscorp /etc/cron.hourly/gnuantivirussiriuscyberneticscorp

and Bob's your Uncle!

Cheers,

Herman

Is that script released under the GPL ? 

LOL to death :lolflag:

---

### Post by dcstar on 2008-01-13
> **HermanAB said:**
> I use a variation of this virus scanner:
........
and Bob's your Uncle!

Cheers,

Herman

Not the sort of thing you can build a multi-billion dollar industry on (like the ongoing Windows AV scam), but good work anyway......                    :-\"

---

### Post by Nero_Flint on 2008-01-13
I don't bother using any AV software. To check any files that I will send on to Windoze users I use VirusTotal. Hopefully that will stop any problems that exist. I do understand that there is no foolproof method.

---

### Post by crazyfuturamanoob on 2008-01-13
I got firestarter, and I often see some blocked events where read "microsoft-xx" (can't remember what that xx was).
Do I need virus scanners? My computer seems to be in contact with ms windows (not networked).

---

### Post by aBitLater on 2008-01-13
Hello dark_phantom,

I do respectfully disagree.  Because linux permissions are different than windows permissions doesn't mean a linux user will never use su or sudo to run an executable.  Virii for linux do exist, though there are not as many that exist for windows.  Certainly this has a lot to do with the over-whelming dominance of MS Windows in the marketplace.

Please see the following:
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses")

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/]("http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/")

[http://www.vnunet.com/networkitweek/news/2057981/linux-popularity-breeds-worms]("http://www.vnunet.com/networkitweek/news/2057981/linux-popularity-breeds-worms")

The last one mentions briefly the problem of buffer overflows - a common problem with anything written in C.

I agree that the threat is 'minimal' compared to windows, but the threat does still exist.



> **bodhi.zazen said:**
> +1

Anti-Virus scanning on Linux is of limited utility as there are no know linux viruses "in the wild" so there is essentially nothing to scan for.

In addition Antivirus is reactive, not proactive meaning it can not protect you from the next Linux virus until AFTER it is released, not before.

A potential use of linux antivirus is to "protect" windows or if you are running a mail server, and even then, IMO, Windows antivirus is better then Linux antivirus.

In the end, the choice is yours to make, but I would be willing to bet that the more experience one has with Linux (Ubuntu) the less one feels the need for scanning / for viruses.

=========================

@dark_phantom

Linux is different the Windows. Security is different.

See these links : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

Psychocats : [Psychocats :  Security on Ubuntu](http://www.psychocats.net/ubuntu/security)

---

### Post by bodhi.zazen on 2008-01-13
I am going to move this thread to recurring discussions.

> **crazyfuturamanoob said:**
> I got firestarter, and I often see some blocked events where read "microsoft-xx" (can't remember what that xx was).
Do I need virus scanners? My computer seems to be in contact with ms windows (not networked).

Yes, any time you connect to the internet you will see this kind of activity.

In a nutshell :

1. With the default installation of Ubuntu desktop, there are no servers running (listening). Since there are no servers running, it does not matter how may times someone tries to connect, they will fail.

2. Firestarter  is a GUI front end to your firewall, iptables. Since firestarter runs as root you should NOT run it all the time. You should NOT monitor your network traffic with it.

3. If you install a server you need to learn to secure it. A firewall helps, but not if you are running a public server.

See the links on security I posted earlier.

> **aBitLater said:**
> Hello dark_phantom,

I do respectfully disagree.  Because linux permissions are different than windows permissions doesn't mean a linux user will never use su or sudo to run an executable.  Virii for linux do exist, though there are not as many that exist for windows.  Certainly this has a lot to do with the over-whelming dominance of MS Windows in the marketplace.

Linux viruses have been described, it is true. 

However :

1. Viruses take advantage of holes in the code. The linux code has been patched long ago for the know viruses, so antivirus is not needed. This is different then Microsoft which takes years (and even then holes still go unpatched) to patch known holes.

So while you can point to links, none of those linux viruses should run on a modern, up to date system.

2. It is a common fallacy that Linux is less a target then Windows because it is less popular. Some of the most valuable servers run Linux (or Unix) so they are big enough targets. The Open source community takes an active role in maintaining security and if a problem is identified it is solved much more rapidly then closed source.

---

### Post by hellion0 on 2008-01-16
There is one situation where you'll want an anti-virus on Linux, and that's if you're sharing files with a Windows machine (or in this day and age, even a Mac.)  If you download an infected file to your Linux box, then transfer it to a Windows machine, run it, and get infected, you'll wish you had.

You could just as easily scan the thing on the Windows machine, sure, but that's still one useful application of an AV on Linux.

---

