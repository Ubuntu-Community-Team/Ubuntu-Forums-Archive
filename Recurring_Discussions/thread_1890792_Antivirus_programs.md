---
title: "Antivirus programs"
date: 2011-12-04
forum: Recurring Discussions
---

### Post by teacherjeff on 2011-12-04
Apparently, from everything I have read, the average Ubuntu desktop user doesn't really need to worry about antivirus program.  Just out of curiousity......

Why?  Is Linux somehow inherently more secure than Windows, or is it just that the installed base of machines running Linux is so much smaller that it's not an attractive target?

---

### Post by *^kyfds( on 2011-12-04
there are two reasons i guess;

-for one, as you said, only a minority of people have linux, and most of their software is downloaded through the software centre, which is completely secure.

-secondly, in order for an .exe file to be run, you need to run it with wine, AND change permissions (difficult to do with a bot, to my understanding)

i'mn sure there are many other reasons i am not aware of :)

---

### Post by haqking on 2011-12-04
> **teacherjeff said:**
> Apparently, from everything I have read, the average Ubuntu desktop user doesn't really need to worry about antivirus program.  Just out of curiousity......

Why?  Is Linux somehow inherently more secure than Windows, or is it just that the installed base of machines running Linux is so much smaller that it's not an attractive target?

Linux is not more secure than windows. They are both equal pretty much, the security comes from your own configuration and usage.

When it comes to Viruses however then there are none currently in the wild that effect Linux.

See for here for Basic Security Guide which covers basics and links to more detailed information:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)

---

### Post by haqking on 2011-12-04
> **Thehumorouscheese said:**
> there are two reasons i guess;

-for one, as you said, only a minority of people have linux, and most of their software is downloaded through the software centre, which is completely secure.

-secondly, in order for an .exe file to be run, you need to run it with wine, AND change permissions (difficult to do with a bot, to my understanding)

i'mn sure there are many other reasons i am not aware of :)

The software centre and repos, though are more trusted than anywhere else, repos can still become compromised by an attacker, it is about accepting and mitigating a risk, so there is no completely secure.

and not all infections or viruses have to be .exe based

Cheers

---

### Post by roger_1960 on 2011-12-04
Hi

Have a read of the "stickys" at the top of the Security Discussions forum.  All is explained in some depth.  I have had no security problems with linux/ubuntu since 2007 when I first used it.  I think unless you let ignorant/malicious people sit at your PC, you will be OK.

---

### Post by jockyburns on 2011-12-04
++ all of the above,,, plus the fact that your not logged in as root., makes Linux more secure than Windoze.

---

### Post by haqking on 2011-12-04
> **jockyburns said:**
> ++ all of the above,,, plus the fact that your not logged in as root., makes Linux more secure than Windoze.

You dont have to be logged into Windows with root, and people often login to Linux with root.

The whole logging in as root in either OS is a choice not system design.

Linux is not more secure than windows, they both have equal Security Classifications, it is upto to the user to secure their system and keep it as secure as functionally possible in a non-secure world of network and online activity.

Cheers

---

### Post by mamamia88 on 2011-12-04
> **haqking said:**
> You dont have to be logged into Windows with root, and people often login to Linux with root.

The whole logging in as root in either OS is a choice not system design.

Linux is not more secure than windows, they both have equal Security Classifications, it is upto to the user to secure their system and keep it as secure as functionally possible in a non-secure world of network and online activity.

Cheers

True but in windows the defualt user you create has admin rights.  And to be honest using a standard user in windows blows in my opinion.  Come on they ask you for your password just to delete an icon shortcut from your desktop.

---

### Post by Dangertux on 2011-12-04
> **mamamia88 said:**
> True but in windows the defualt user you create has admin rights.  And to be honest using a standard user in windows blows in my opinion.  Come on they ask you for your password just to delete an icon shortcut from your desktop.

Not since Windows XP... And even then it was optional... Why do people keep saying this?

As haqking said, neither is more secure than the other. The measures for securing either operating system properly have some overlapping elements, in other respects they are different. 

Anti-malware solutions on Linux are infantile compared to their Windows counterparts. This is partly because Linux has primarily been a server OS for a very long time. The push to make it a popular desktop OS is a fairly recent thing (last 6 years or so). As such Malware developers are either not targeting it or playing catch up. In any case, once they do catch up or start targeting it Linux users will be ill-prepared.

Sudo is JUST as easy if not easier to bypass than UAC. It literally takes a minute or so to bypass either despite the strength of your password. Sorry -- that's just how it is.  Taking proper precautions is the best you can do. Configure your firewall properly, mandatory access controls are great also (Apparmor), and if you do only one thing in my opinion it would be installing a browser addon like NoScript. 

For more information check out the following information rich links.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)
[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)
[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Hope this helps.

---

### Post by haqking on 2011-12-04
> **mamamia88 said:**
> True but in windows the defualt user you create has admin rights.  And to be honest using a standard user in windows blows in my opinion.  Come on they ask you for your password just to delete an icon shortcut from your desktop.

the default user in Linux has the abilty to use admin rights as does a user in windows through UAC

My point is neither Linux or Windows is more secure, they are equally secure as far as Security Classification & criteria go.

System security is not achieved by design in end user OS so much as it is by user education.

Educate yourself on system security and your system can be made secure within the confines of your own requirement for functionality and ease of use which is not something the system designers can do.

Cheers

---

### Post by mamamia88 on 2011-12-04
> **Dangertux said:**
> Not since Windows XP... And even then it was optional... Why do people keep saying this?

As haqking said, neither is more secure than the other. The measures for securing either operating system properly have some overlapping elements, in other respects they are different. 

Anti-malware solutions on Linux are infantile compared to their Windows counterparts. This is partly because Linux has primarily been a server OS for a very long time. The push to make it a popular desktop OS is a fairly recent thing (last 6 years or so). As such Malware developers are either not targeting it or playing catch up. In any case, once they do catch up or start targeting it Linux users will be ill-prepared.

Sudo is JUST as easy if not easier to bypass than UAC. It literally takes a minute or so to bypass either despite the strength of your password. Sorry -- that's just how it is.  Taking proper precautions is the best you can do. Configure your firewall properly, mandatory access controls are great also (Apparmor), and if you do only one thing in my opinion it would be installing a browser addon like NoScript. 

For more information check out the following information rich links.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)
[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)
[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Hope this helps.
I login as a standard user in windows 7 and it asks me for my password everytime I try and move a desktop icon to trash can.  Am I doing something wrong?

---

### Post by Dangertux on 2011-12-04
> **mamamia88 said:**
> I login as a standard user in windows 7 and it asks me for my password everytime I try and move a desktop icon to trash can.  Am I doing something wrong?

That's UAC it's supposed to do that. I'm not sure what your question is. You could disable it but I wouldn't recommend doing that.

---

### Post by mamamia88 on 2011-12-04
> **Dangertux said:**
> That's UAC it's supposed to do that. I'm not sure what your question is. You could disable it but I wouldn't recommend doing that. I don't want to disable UAC just that specific feature of UAC.   Do you know if there is a way to do that?

---

### Post by aysiu on 2011-12-04
> **mamamia88 said:**
> I login as a standard user in windows 7 and it asks me for my password everytime I try and move a desktop icon to trash can.  Am I doing something wrong?
It's because some desktop icons are per-user and others are system-wide. If a desktop icon is system-wide, you need admin privileges to move it to the trash.

I use Windows at work, and I use Mac OS X and Ubuntu at home. I don't see any major security benefits to one over the other. For me, it's all about the user. Are you a user who relies on "antivirus" to protect you and then downloads and installs random things, and also never installs system updates? Or are you a careful user who researches programs before installing them and who uses the NoScript extension in Firefox?

If you're the first type of user, you'll probably have your machine compromised at some point, regardless of what operating system you use. And, likewise, if you're the latter type of user, you probably will be protected, regardless of what operating system you use.

P.S. Others won't agree with me, but I think antivirus is pretty much useless even on Windows.

---

### Post by haqking on 2011-12-04
> **aysiu said:**
> 
If your the first type of user, you'll probably have your machine compromised at some point, regardless of what operating system you use. And, likewise, if you're the latter type of user, you probably will be protected, regardless of what operating system you use.

P.S. Others won't agree with me, but I think antivirus is pretty much useless even on Windows.

Agreed to both. (i should clarify, i do agree to both however AV i still think should be used in a Windows Environment, it is just that i think it does not offer the level of protection advertised, expected or really needed, but i wouldnt say completely useless just not upto expectations)

AV and Malware solutions in general are OK but people place way too much trust in them to prevent compromise, even if malware was the be all and end all of system security which it is not the solutions are not perfect.

The best all in one solution, infact the only all in one is education IMO

---

### Post by mamamia88 on 2011-12-04
> **haqking said:**
> Agreed to both.

AV and Malware solutions in general are OK but people place way too much trust in them to prevent compromise, even if malware was the be all and end all of system security which it is not the solutions are not perfect.

The best all in one solution, infact the only all in one is education IMO

true antivirus are kind of like the police.  they inform you after it's too late and you can't go back in time and undo what you did

---

### Post by Dangertux on 2011-12-04
> **mamamia88 said:**
> I don't want to disable UAC just that specific feature of UAC.   Do you know if there is a way to do that?

As it's been already stated, if the file does not belong solely to you , IE: system owned files -- you will not be able to modify them without using system/admin privileges. Thus the UAC prompt. Disabling this functionality would require disabling UAC.

> **aysiu said:**
> P.S. Others won't agree with me, but I think antivirus is pretty much useless even on Windows.

On this, I both agree and disagree. I'll explain -- Anti-virus / Anti-malware solutions are great for their purpose. Unfortunately their purpose is and always has been greatly misunderstood. Too many people think of them as a proactive measure, companies market them this way as well. With statements like "active protection". The truth is anti-virus/malware solutions have always been a reactive solution. The way they work is they monitor the hard drive (either actively or via a scheduled scan) for files, and file behavior that is indicative of something being malicious. So when you think about it , they are defending against a payload, not an exploited vulnerability. Malware developers and exploit designers have been smart to this for a while; if you stay in memory and or limit or distribute the hard drive bound functionality of a malicious program it's rather easy to fly right under AV's radar, so to speak. 

Now in the situation that you want to determine if a file is malicious in nature, AV is a great idea, particularly on Windows they are rather advanced and the signature libraries are well maintained. However -- they are not a magic bullet for protection. Not even so much as any security application is, they are in my opinion low on the  "totem pole" of security applications. They are a very targeted measure, and as I said reactive. For those wanting to be "safe and secure", they should spend time  utilizing and configuring a proactive solution(s). Such as NoScript, strong credentials, and regular updates.

You can divide the common desktop security solutions into two categories.

Proactive
-----------
- NoScript and Similar
- Strong Credentials
- Use of encryption
- Regular updates, and keeping up with security threats


Reactive
----------
- Anti-malware
- Firewall
- Mandatory/Discretionary Access Controls
- Use of encryption



The reason they are divided as such, the proactive category is focusing on ensuring that a system is NOT compromised, the latter reactive solutions are focusing on minimizing the impact when a system IS compromised.

Note : Encryption is in both categories, as it serves both purposes.

Hope this helps.

---

### Post by haqking on 2011-12-04
> **mamamia88 said:**
> true antivirus are kind of like the police.  they inform you after it's too late and you can't go back in time and undo what you did

not technically true.  If the AV is half good it wont let the infection happen it will quarantine the issue and thus do its job, if it doesnt do its job the AV is unlikely to inform you of anything ;-)

there are too many false positives from AV solutions IMO.

Not saying you shouldnt run it, i think you should (in windows at least) as security is a layered approach, but it certainly isnt the be all and end all.

You can prevent as easily as AV can find and fix any malware if you pay attention to what you do.

---

### Post by mamamia88 on 2011-12-04
> **haqking said:**
> not technically true.  If the AV is half good it wont let the infection happen it will quarantine the issue and thus do its job, if it doesnt do its job the AV is unlikely to inform you of anything ;-)

there are too many false positives from AV solutions IMO.

Not saying you shouldnt run it, i think you should (in windows at least) as security is a layered approach, but it certainly isnt the be all and end all.

You can prevent as easily as AV can find and fix any malware if you pay attention to what you do.

fair enough i only ever boot windows to use excel though and boot ubuntu right back up.  I'll have no reason to ever boot windows again on this pc in about a week when i graduate

---

