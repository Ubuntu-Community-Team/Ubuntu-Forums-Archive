---
title: "Which Antivirus software?"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by Sandy000 on 2011-10-01
I just got Ubuntu 11.04 up and running the other day.
I'd like to add some antivirus software so I typed in antivirus in the software center and it listed 18 choices. 
I'd like some opinions or feedback from those that might have used the programs which one do you use? 
Which one do you think would be best for me to install? 
Thanks for your input. :)

---

### Post by haqking on 2011-10-01
> **Sandy000 said:**
> I just got Ubuntu 11.04 up and running the other day.
I'd like to add some antivirus software so I typed in antivirus in the software center and it listed 18 choices. 
I'd like some opinions or feedback from those that might have used the programs which one do you use? 
Which one do you think would be best for me to install? 
Thanks for your input. :)

You dont need any unless you are sharing with Windows users to be honest though. Though malware can attack Linux it has to be targeted at Linux and there is none in the wild currently and most of the users on here will tell you the same thing, using Linux for x amount of years no viruses.

Please read the following which is my standard answer, make sure you read the links especially **[ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")**


Linux does not suffer from Viruses like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

[B]See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)[/B]

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Then these stickies:
security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Also see about sudo and why root account is disabled by default in Ubuntu:

[B]rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)[/B]

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


Have fun

Regards

haqking

---

### Post by Perfect Storm on 2011-10-01
None.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Sandy000 on 2011-10-01
Thanks for the info and the links. :)

---

### Post by snip3r8 on 2011-10-01
> **haqking said:**
> You dont need any unless you are sharing with Windows users to be honest though. Though malware can attack Linux it has to be targeted at Linux and there is none in the wild currently and most of the users on here will tell you the same thing, using Linux for x amount of years no viruses.

Please read the following which is my standard answer, make sure you read the links especially **[ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")**


Linux does not suffer from Viruses like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

[B]See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)[/B]

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Then these stickies:
security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Also see about sudo and why root account is disabled by default in Ubuntu:

[B]rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)[/B]

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


Have fun

Regards

haqking
this should actually become a sticky,this question pops up ALOT

---

### Post by haqking on 2011-10-01
> **snip3r8 said:**
> this should actually become a sticky,this question pops up ALOT

Well it is covered in the security stickies which i refer to. People will always ask the same questions especially if coming from Windows.

It is why i have my standard answer, cut and paste and answered ;-)

Well unless they dont read the links which also happens alot.

---

### Post by aura7 on 2011-10-01
Is Ubuntu also resistant to spyware that get downloaded through browsers in the form of cookies.

---

### Post by galacticaboy on 2011-10-01
> **aura7 said:**
> Is Ubuntu also resistant to spyware that get downloaded through browsers in the form of cookies.

From what I have understood, what happens in the browser stays in the browser. I am not sure if that is true. If it is, then it would not effect your computer. I have been using Ubuntu since 2006 and have never had a Spyware, Malware, Adware, Virus, or any other problem like that. EVER! =-]

---

### Post by Dangertux on 2011-10-01
Cookies are not executable even in the windows world. If to are referring to tracking cookies no they are operating system independent. If you are concerned about that use an add-on such as noscript for firefox. 

If you are talking about drive by download malware. No it's not resistant to that. With a caveat, the malware has to be targeted on an operating system / software basis. Currently Linux/Ubuntu is not widely targeted for this. So it's not resistant to it but it is much less likely to happen. I say widely as opposed to none in the wild because truthfully nobody here is qualified to make that statement. More accurately none has yet been found in the wild. 

Hope that helps. I'm not downing the Ubuntu is secure party just being more realistic about it.

---

### Post by aura7 on 2011-10-01
Thanks [Dangertux]("http://ubuntuforums.org/member.php?u=1322416") for the info.

---

### Post by haqking on 2011-10-01
> **Dangertux said:**
> Cookies are not executable even in the windows world. If to are referring to tracking cookies no they are operating system independent. If you are concerned about that use an add-on such as noscript for firefox. 

If you are talking about drive by download malware. No it's not resistant to that. With a caveat, the malware has to be targeted on an operating system / software basis. Currently Linux/Ubuntu is not widely targeted for this. So it's not resistant to it but it is much less likely to happen. I say widely as opposed to none in the wild because truthfully nobody here is qualified to make that statement. More accurately none has yet been found in the wild. 

Hope that helps. I'm not downing the Ubuntu is secure party just being more realistic about it.

+1

And yes the whole "ubuntu is secure" thing....nothing can be 100% secure if connected, by definition a network exists to utlilise shared resources, which means access, no matter how much you try to limit that access, ingress and egress will always exist.

Any system is only as secure as its function and user/admin.  Security is an going process and layered approach and requires vigilence and not ignorance.

Security = PEBKAP..problem exists between keyboard and person ;-)

---

### Post by matfx on 2011-10-02
> **haqking said:**
> You dont need any unless you are sharing with Windows users to be honest though. Though malware can attack Linux it has to be targeted at Linux and there is none in the wild currently and most of the users on here will tell you the same thing, using Linux for x amount of years no viruses.

Please read the following which is my standard answer, make sure you read the links especially **[ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")**


Linux does not suffer from Viruses like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

[B]See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)[/B]

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Then these stickies:
security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Also see about sudo and why root account is disabled by default in Ubuntu:

[B]rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)[/B]

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


Have fun

Regards

haqking

Thanks this is indeed helpful for newbie like me which just switch from Window 7 to ubuntu.

---

### Post by haqking on 2011-10-02
> **matfx said:**
> Thanks this is indeed helpful for newbie like me which just switch from Window 7 to ubuntu.

No worries, glad it can help.

Peace

---

