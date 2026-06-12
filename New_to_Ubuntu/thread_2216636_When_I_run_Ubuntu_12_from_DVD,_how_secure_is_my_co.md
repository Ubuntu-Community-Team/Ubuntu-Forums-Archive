---
title: "When I run Ubuntu 12 from DVD, how secure is my computer?"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by LizzyJean on 2014-04-13
I'm just starting to look into moving from XP to Linux on my laptop.  I spent a few hours running Ubuntu from DVD yesterday and was online using Firefox.  Can I log into my gmail safely?  I've been reading a lot about security, like this [informative thread]("http://ubuntuforums.org/showthread.php?t=510812"), and I realize that I'm at the *very beginning* of a LARGE learning curve. It would help, to start, to have some clear dos and don'ts for staying secure while trying out Ubuntu from DVD.

---

### Post by monkeybrain20122 on 2014-04-13
It is absolutely safe for your computer because it runs in ram. On the other hand if you log into websites and submit info such as credit card # then it would depend on other things such as security of the network and the remote sites that you log into, and of course that you don't fall for phising scams and the like. No OS can protect you from the Nigerian scam. :)

But if you are worrying about malware and virus, not a chance. Everything is gone on reboot.

P.s. It is better to use a live usb than a DVD unless you enjoy the low speed and like hearing the sound of mechanical parts grinding away. :)

---

### Post by carl4926 on 2014-04-13
Almost certainly less secure than when installed and updated.
Because you are implying security in terms of use of the Internet. And 12.04 I think, from the CD is vulnerable to the most recently publicised bug.... Heartblead - as well as the fact that all the software on the CD is out of date.
It's fine for testing generally, but I wouldn't consider using it for secure logins

---

### Post by sudodus on 2014-04-13
> **carl4926 said:**
> Almost certainly less secure than when installed and updated.
Because you are implying security in terms of use of the Internet. And 12.04 I think, from the CD is vulnerable to the most recently publicised bug.... Heartblead - as well as the fact that all the software on the CD is out of date.
It's fine for testing generally, but I wouldn't consider using it for secure logins

+1

and welcome to the Ubuntu Forums *LizzyJean* :-)

Please read also this link [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by monkeybrain20122 on 2014-04-13
> **carl4926 said:**
> Almost certainly less secure than when installed and updated.
Because you are implying security in terms of use of the Internet. And 12.04 I think, from the CD is vulnerable to the most recently publicised bug.... Heartblead - as well as the fact that all the software on the CD is out of date.
It's fine for testing generally, but I wouldn't consider using it for secure logins

Unless I am missing something I think the vulnerability comes from the other end of the connection, not  that you may get something on your local machine. And with heartbleed the problem now appears to be many popular websites may be affected and doing transactions with them may put you at risk, I am not sure how the fact that your copy of openssl is patched on Ubuntu may change that unless you run a server.

---

### Post by carl4926 on 2014-04-13
> [COLOR=#000000]not that you may get something on your local machine[/COLOR]This was not what was under discussion IMO

In that respect, a live cd is perfectly safe, it's almost totally isolated from the machine.

To the OP, I'd say. It's fine. Just don't use it for secure logins/banking  lol

---

### Post by 3rdalbum on 2014-04-13
12.04 is a bit old now. If you are just starting with Linux, download Ubuntu 14.04 - it has newer software.

Don't get me wrong, 12.04 is a good version, but if you are using it from CD you are using a two-year-old version of Firefox. Even then you will still probably be okay, but 14.04 has the latest Firefox which means all the latest security patches.

14.04 is not officially released yet but it will be in a few days. Until then you can definitely use the beta or Release Candidate images, they are very stable, and if you install Ubuntu from it you only need to run the ordinary system updates to get the final release version.

---

### Post by monkeybrain20122 on 2014-04-13
I suggest 13.10 if you want Ubuntu now. It has still almost 4 months of support, enough to get your feet wet and more. 14.04 is buggy at the moment and I think it will be even for a month or two after release. I won't recommend it to new users when something works perfectly today and completely broken the next day.

---

### Post by LizzyJean on 2014-04-13
Thanks for the informative and diverse replies. ;)

For now, I'll try 12.04 on the grinding disk a little longer, but when I install, I'll use 13.10.  Then maybe 14.04 when it gets less buggy.  (I hope I don't have to set everything up from scratch everytime I move to a newer version of Ubuntu, though, 'cause that sounds *way* too time intensive.)

I think, from what I'm reading at [Mashable]("http://mashable.com/2014/04/09/heartbleed-bug-websites-affected/"), the danger of heartbleed doesn't depend on how current Firefox is.  Generally, I'll just avoid secure login banking type sites while I'm trying Ubuntu 12.

But I have one question about "Everything is gone on reboot."  While I was running Ubuntu I created a librewriter doc of my notes and saved it in the XP "my documents" folder.  It was still there when I rebooted with XP.  So, if *I* can get through to my documents, can malware get through to my windows system files?  (I truly have SO much to learn about how malware and viruses actually work.) 

But I'm also not that paranoid and don't need to overthink this.  As long as there are no horror stories out there, then probably everything's cool.

---

### Post by sudodus on 2014-04-13
> **LizzyJean said:**
> Thanks for the informative and diverse replies. ;)

For now, I'll try 12.04 on the grinding disk a little longer, but when I install, I'll use 13.10.  Then maybe 14.04 when it gets less buggy.  (I hope I don't have to set everything up from scratch everytime I move to a newer version of Ubuntu, though, 'cause that sounds *way* too time intensive.)

You can upgrade to new versions :-)
> 
I think, from what I'm reading at [Mashable]("http://mashable.com/2014/04/09/heartbleed-bug-websites-affected/"), the danger of heartbleed doesn't depend on how current Firefox is.  Generally, I'll just avoid secure login banking type sites while I'm trying Ubuntu 12.

But I have one question about "Everything is gone on reboot."  While I was running Ubuntu I created a librewriter doc of my notes and saved it in the XP "my documents" folder.  It was still there when I rebooted with XP.  So, if *I* can get through to my documents, can malware get through to my windows system files?  (I truly have SO much to learn about how malware and viruses actually work.) 

But I'm also not that paranoid and don't need to overthink this.  As long as there are no horror stories out there, then probably everything's cool.

 Yes, if *you* can get through to your documents (Windows 'my documents'), malware can too. But it is not likely, that malware is created for such unusual set-ups as yours with a live linux CD and and installed Windows system.

---

### Post by jdeca57 on 2014-04-13
> **3rdalbum said:**
> 
Don't get me wrong, 12.04 is a good version, but if you are using it from CD you are using a two-year-old version of Firefox. Even then you will still probably be okay, but 14.04 has the latest Firefox which means all the latest security patches.

Actually the version of 12.04 you download now is 12.04.4 from February this year. Latest patches aren't included but it's not like you download 2 year old and obsolete software... ;-)

(This discussion also gets confusing when it's speaking about the heartbleed openssl bug. As far as I understood, it's a server problem, not something that affects a casual user using a browser, but that's another subject)

---

### Post by buzzingrobot on 2014-04-13
> **LizzyJean said:**
> 

For now, I'll try 12.04 on the grinding disk a little longer...

A live session on a USB stick is considerably faster than on a DVD.  No grinding.

> I think, from what I'm reading at [Mashable]("http://mashable.com/2014/04/09/heartbleed-bug-websites-affected/"), the danger of heartbleed doesn't depend on how current Firefox is.  Generally, I'll just avoid secure login banking type sites while I'm trying Ubuntu 12.

The Heartbleed threat comes from exposure of user data on servers we all thought was not exposed, plus the fact that the bug was not at all difficult to exploit. That bug was patched quickly and responsible site operators should have implemented it immediately.. This ([http://www.zdnet.com/how-to-protect-yourself-in-heartbleeds-aftershocks-7000028311/](http://www.zdnet.com/how-to-protect-yourself-in-heartbleeds-aftershocks-7000028311/)) has some links to sites listing/checking to determine if a site has rolled out the patch. Some other good advice in there, too.

[EDIT:  A different point of view here: [https://freedom-to-tinker.com/blog/jbonneau/heartbleed-and-passwords-dont-panic-2/](https://freedom-to-tinker.com/blog/jbonneau/heartbleed-and-passwords-dont-panic-2/).]

> But I have one question about "Everything is gone on reboot."  While I was running Ubuntu I created a librewriter doc of my notes and saved it in the XP "my documents" folder.  It was still there when I rebooted with XP.  So, if *I* can get through to my documents, can malware get through to my windows system files?

Yes, at least in principle.

---

### Post by LizzyJean on 2014-04-13
> **sudodus said:**
> You can upgrade to new versions :-)

Okay. That simplifies things. Thanks. :p

 > Yes, if *you* can get through to your documents (Windows 'my documents'), malware can too. But it is not likely, that malware is created for such unusual set-ups as yours with a live linux CD and and installed Windows system.

Yeah. That is making good sense to me now.

> **jdeca57 said:**
> Actually the version of 12.04 you download now  is 12.04.4 from February this year. Latest patches aren't included but  it's not like you download 2 year old and obsolete software... :wink:

That is reassuring.

> **buzzingrobot said:**
> A live session on a USB stick is considerably faster than on a DVD.  No grinding.

Yeah, but the only USB stick I've managed to hold onto is a dainty little 1 gig, so it's back to the old grind for now.;)

Thanks everyone.  And I'll be back with new questions soon.

---

### Post by sudodus on 2014-04-13
I think the Ubuntu DVD sized iso files are only slightly oversized for CD, and should fit in a 1 GB pendrive.

---

### Post by monkeybrain20122 on 2014-04-13
> **LizzyJean said:**
> Okay. That simplifies things. Thanks. :p


I would suggest not to "upgrade" because it takes a long time (several hours) and it is a messy and not a very robust  process, during the long upgrade process a number of things can go wrong,--say you lose internet, not uncommon if you use wifi and upgrade will hang,-- also if your system has been modified/customized in non trivial ways,--say installing proprietary driver or editing system files for trouble shootings,--upgrade will likely fail.

So my suggestion is to do a clean install for OS update. This is fast and easy if you make separate / and  /home partitions when you install. When you do your clean install to update the OS, use the same / and /home but do not format /home. That way all your data and settings will be kept. You can also make a list of software installed so you can reinstall all of them (new versions) after reinstalling the OS quickly. Installation of OS takes less than 20 minutes and reinstalling software this way would take even less. This is also a lot safer than 'upgrade'. In the unlikely event that you blotch your install, just do it again and still don't format /home. 

If you need detailed advice for making separate / and /home post a new thread when you install Ubuntu into the hard disk.

Also disable notification for new Ubuntu release in update manager, or it will nag you to upgrade the very day 14.04 is released. It is easy to press the wrong button and there is no way to abort, forcibly shutting it down will leave your system in an unusable state. As said I don't recommend 'upgrade' and certainly not on the first day when the OS is released. New Ubuntu releases are usually somewhat buggy, it takes a month or two for post release bugs fixes to roll in.

To disable upgrade notification. Open update manager (software updater), click Settings and go to the 'Updates' tab, go to the last row "notify me of a new Ubuntu version" and change it to 'never' in the drop down.

---

### Post by jbaerboc on 2014-04-16
Previous posters mentioned Ubuntu 14.04 Beta being buggy...I've been running it for 2 weeks with no problems or bugs. On my hardware it actualy runs quite a bit smoother and less buggy than 13.10. That may just be me being lucky I guess :D. But as previous posters commented, running a LiveDvD is a temporary thing using your RAM and nothing is written to your hardrive. Granted you can still mess up your computer from it but it takes some doing [mess up partitions using gparted or somesuch]. Security wise it's fine.

---

