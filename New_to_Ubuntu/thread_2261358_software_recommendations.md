---
title: "software recommendations?"
date: 2015-01-18
forum: New to Ubuntu
---

### Post by hmiersch on 2015-01-18
hi. i recently decided to switch from OSX to Ubuntu. So now i'm looking for some software recommendations in the following categories: - firewall. i want something that gives me a lot of control. i tried gufw, but i didn't like that. on the mac i use little snitch. - anti-malware. on OSX i use clamXAV. is there a version (or something similar) for Ubuntu? - email. i tried thunderbird, but that doesn't give me all the functionality i want, like automatically sorting incoming mail into folders or mailboxes. or does it? - podcasts. i want something that gives me functionality like itunes on OSX, with the ability to sync podcasts to ios (i still have an iphone and an ipad) as well as android (for the future) - calendar and address book.  so, any recommendations? thanx.  and what the hell happened to my formatting?

---

### Post by TheFu on 2015-01-18
The UNIX/Linux philosophy is very different from that of OSX. Looking for 1-for-1 replacements will be disappointing.
Here's an attempted explanation of the[ thought shift needed to get the most from Linux systems.]("http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed") OTOH, if you are a point-n-click user only, it doesn't matter, but will let you understand why we tend to use tiny applications that do 1 thing well. It is part of the system architecture.

There is only 1 firewall for Linux, iptables. Everything else is just a GUI over it. I don't understand what you don't like about gufw - an explanation could help.

I use thunderbird, but let my email server (zimbra) handle all the filters and message organization on the server-side.  For 20+ yrs, (may be 30), UNIX people have used procmail to manage their email folders on arrival. This method is broken by most email systems today because you actually don't have any account ON the email server to manage this stuff. I vaguely recall the years when my workstation was also the machine that received email. Procmail was/is very powerful, if that is the case. Doubt that helps you today. ;(

iTunes -  Bleh.  Miro, gpodder.  I prefer a perl script, fetchpods.pl.  Simple, effective.  To sync to devices is a different tool - which is the Linux way. I like rsync. Works on every platform, easy to automate and it is secured via ssh, so safe when I'm away from my home network. Some other alternatives [http://askubuntu.com/questions/414737/how-do-i-install-itunes-on-ubuntu](http://askubuntu.com/questions/414737/how-do-i-install-itunes-on-ubuntu)

Calendars ... I use a CalDAV connection with Thunderbird and Lightning to the Zimbra server.  There's a free CalDAV tool for Android that works well too. Sorry, don't recall the name, since it is a service and runs in the background, so I don't see it very often. It just works.

There are lots of "best linux software" lists on the web. Search "best linux software" to find them. I've been using almost all the same stuff since 1995 ported from UNIX. Yes, it still works.  If you stay away from the point-n-click stuff, things don't change too much. If you insist on GUIs, be prepared for major changes (often for no reason) every 2-3 years. **New** is the most powerful marketing term, though it doesn't really say anything.

If you aren't adverse towards Google, their stuff works well. I am adverse to them and try to avoid anything from them whenever possible. If you want to control things yourself, take a look at openVPN, then AFTER THAT IS WORKING, load **seafile** or owncloud.  These replace cloud file sharing services where you don't really have any control and even less security and zero privacy. Seafile and owncloud don't have much security either, so a strong VPN is required BEFORE using them.

IMHO.

---

### Post by stalkingwolf on 2015-01-18
clam tk is in the repositories.  As i recall there is a firewall installed but someone else will have to help there ive never needed to change the default settings.

---

### Post by Quarkrad on 2015-01-18
Unless I'm mistaken you will have to sitck with the mac if you want to sync with your iphone/ipad with something like itunes.  All your other requirements can be achieved, to a degree, but I know of nothing that will sync your apple kit as easily as itunes.  Ubuntu is not Apple and does not attempt to be so - hence, there is nothing re sync'ing to iphone/ipod/ipad as eaily as itunes.  This is really an Apple platform environment requirement - itunes is superb at what it does, but it is proprietary Apple and best placed on their kit.  (I have itunes working in Windows, in a virtual machine, on my Ubuntu install because of this very fact).

---

### Post by entropy1 on 2015-01-18
You can use thunderbird to sort incoming mail and automatically put it into appropriate folders.  In the menu bar, click on Tools > Message Filters (or just Message Filters, if you access the menu from the right-hand corner).  From there, click the New button, and it should be pretty self-explanatory.  For more details, see [http://kb.mozillazine.org/Filters_%28Thunderbird%29]("http://kb.mozillazine.org/Filters_%28Thunderbird%29")

---

### Post by buzzingrobot on 2015-01-18
> **hmiersch said:**
> hi. i recently decided to switch from OSX to Ubuntu. So now i'm looking for some software recommendations in the following categories: - firewall. i want something that gives me a lot of control. i tried gufw, but i didn't like that. on the mac i use little snitch. - anti-malware. on OSX i use clamXAV. is there a version (or something similar) for Ubuntu? - email. i tried thunderbird, but that doesn't give me all the functionality i want, like automatically sorting incoming mail into folders or mailboxes. or does it? - podcasts. i want something that gives me functionality like itunes on OSX, with the ability to sync podcasts to ios (i still have an iphone and an ipad) as well as android (for the future) - calendar and address book.  so, any recommendations? thanx.  and what the hell happened to my formatting?


GUFW is one of several GUI front-ends to the iptables firewall used in most Linux distributions.  Ports in Ubuntu and other distros are typically closed by default, so the primary use of a firewall is often to open a port. 

Don't believe an app like Little Snitch is available.  But, I imagine there are GUI apps that provide similar functionality:  See what's generating outgoing traffic.

ClamX is traditional virus scanner. I.e., you download virus signatures and it scans for them. It's available.  Use of a virus scanner on Linux is widely debated since it is very infrequently targeted. Doesn't hurt to run a scanner, though.

Believe Thunderbird can create filters to move mail into specified mailboxes. If you use an IMAP mail provider and use its filtering to segregate mail, then any IMAP mail client, like Thunderbird, will mirror that structure.

Clueless about iTunes, calendars, and such.

---

### Post by Sef on 2015-01-18
> [COLOR=#000000]what the hell happened to my formatting?[/COLOR]

What changed on your formatting?

---

### Post by mastablasta on 2015-01-19
> **Sef said:**
> What changed on your formatting?
the OP meant to have bullet points it seems.

> **buzzingrobot said:**
> 

ClamX is traditional virus scanner. I.e., you download virus signatures and it scans for them. It's available.  Use of a virus scanner on Linux is widely debated since it is very infrequently targeted. Doesn't hurt to run a scanner, though.

And it mostly scans for windows malware anyway.

> 
Believe Thunderbird can create filters to move mail into specified mailboxes. 


thunderbird has a long history so I am sure it can do basic features like that. I would just like to add that thunderbird and Mozilla both have plenty of plugins available though I only use lightning for calendar in thunderbird.

---

### Post by Gordonbp531 on 2015-01-19
I can confirm that Thunderbird will indeed sort messages into different folders on receipt, using Filters as mentioned above.
The main reason for using an anti virus application is if you exchange a lot of files with Windows users - don't want to infect them any more than they are already!:p

---

### Post by hmiersch on 2015-01-26
ok, now that i can boot from my external HD, it's time to revive this thread.  ok, i checked out the following software:  Miro: last time i tried to use it, it kept crashing. not good.  firestarter: can't install. on the website it says i can install it using sudo apt-get install firestarter, but that only gives me an error message telling me it couldn't find the package. So i tried to download it from the website, and compile it myself. another error message, this time something about perl.  rsync: as i understand it, it syncs one foldr to another. so how does that help me sync playlists that keep changing? in itunes i have some smart paylists that change every time an item is played. that item disappears from the playlist, and another one appears. how can i sync something like that to an android?  gpodder: gonna give it a try. hope it crashes less than miro...

this forum keeps removing my blank lines. WTF?

---

### Post by buzzingrobot on 2015-01-26
> **hmiersch said:**
>   Miro...

What is it? I've never used it.

> ...firestarter: can't install. on the website it says i can install it using sudo apt-get install firestarter, but that only gives me an error message telling me it couldn't find the package. So i tried to download it from the website, and compile it myself. another error message...


Ubuntu installs and activates a firewall script, ufw.  Gufw, in the repos, is the popular GUI front-end.

My guess is the Firestarter site is a bit out of date.

>  ...rsync: as i understand it, it syncs one foldr to another. so how does that help me sync playlists that keep changing?

rsync is a very capable, very widely used synchronization tool. It's used for backing up individual drives as well as for things like mirroring entire sites. E.g., I use a little script for backup here.  A "man rsync" will get you a look at what's on offer. Many GUI frontends are available, intended as backup tool, but could be easily repurposed into keeping any single directory in sync with another one. Some of these GUI tools allow scheduling via cron, others require you to do that yourself.

---

### Post by bapoumba on 2015-01-26
> **hmiersch said:**
> this forum keeps removing my blank lines. WTF?
Which browser are you using ? Any extensions ? Blocking yahooapis ?

---

### Post by coffeecat on 2015-01-26
> **buzzingrobot said:**
> My guess is the Firestarter site is a bit out of date.

A bit?! It mentions Mandrake Linux in the installation page! :)

[http://www.fs-security.com/](http://www.fs-security.com/)

> Firestarter and all the contents on this page are © 2000-2007

@hmiersch, don't even consider firestarter. It's so dead that even though it was nailed to the perch, it's now fallen off said perch because the nails have rusted through.

---

### Post by TheFu on 2015-01-26
> **hmiersch said:**
> rsync: as i understand it, it syncs one foldr to another. so how does that help me sync playlists that keep changing? in itunes i have some smart paylists that change every time an item is played. that item disappears from the playlist, and another one appears. how can i sync something like that to an android?  gpodder: gonna give it a try. hope it crashes less than miro...

I've never run iTunes - it was installed when I wanted just quicktime once and decided it was a virus. ;)  It sucked more RAM and CPU than even MS-Outlook - what else could it be?  Large programs like that go against my idea of what a UNIX system should be.  Trying to do everything you did on some other OS exactly the same way on Linux will be extremely frustrating.  It is a different OS, with a different philosophy.  It was designed so end-users could build tools to address most of their needs.

I have a playlist on a server that gets randomized daily, automatically, through cron.  Since the server will stream media to anywhere I am with a network connection, I don't worry about sync.  **The network **IS** the computer.**  With audio, streaming isn't a bandwidth issue at all.

Think a little different, be amazed at what you can accomplish with just a few lines in a script/program.

Or be frustrated on Linux.  This isn't to say that other ways on other OSes isn't right or correct.

---

### Post by hmiersch on 2015-01-26
> **buzzingrobot said:**
> What is it? I've never used it.



Ubuntu installs and activates a firewall script, ufw.  Gufw, in the repos, is the popular GUI front-end.


Ive already said that I tried gufw and I didn't like it. Can someone recommend another GUI for the firewall?

> **TheFu said:**
> I've never run iTunes - it was installed when I wanted just quicktime once and decided it was a virus. ;)  It sucked more RAM and CPU than even MS-Outlook

Itunes may be a memory hog and all that, but it used to do what I wanted - up to version 10, anyway. But then they screwed up version 11, and version 12 is even worse. Which is of course one reason why I first refused to go beyond version 10.7 (I was still on OSX 10.8 even though 10.10 is out) an then decided to switch to Linux.

I'm not wild about this whole cloud thing. What's the point of sending my stuff to a server? It's just a big waste of bandwidth, and once it's out of my computer it's out of my control. I would never use things like Facebook, twitter or IFTTT. Online backup? That MAY be an option, if and ONLY if it is heavily encrypted before it leaves my computer. TNO -trust no one.

---

### Post by mastablasta on 2015-01-27
> **hmiersch said:**
> Ive already said that I tried gufw and I didn't like it. Can someone recommend another GUI for the firewall?

what do you expect from a firewall GUI? in gufw you can pretty easily open or close the ports. nothing more is eneded anyway. I am not sure what you woul dlike in a firewall? blinking lights? virus scanner built in or virtual desktops (like they have now in Comodo) & secure browser ? all this stuff is available in other programs. remember what was said about apps in Linux - "do one thing and do that well".

> **hmiersch said:**
> 
I'm not wild about this whole cloud thing. What's the point of sending my stuff to a server? It's just a big waste of bandwidth, and once it's out of my computer it's out of my control. I would never use things like Facebook, twitter or IFTTT. Online backup? That MAY be an option, if and ONLY if it is heavily encrypted before it leaves my computer. TNO -trust no one.

which is why TheFU has his own server under his control. so do I (but my server is not really much under control :) ). it's not a waste. you will get backups at the same time. besides stuff in iTunes is not really in your control either I believe. just look at your frustration at their upgrades. there is no way you can fork you own version even if you wanted to. ;-)  

yeah don't send to outside "clouds", have one of your own. secure it. you can encrypt the data on it, if you wish. it can serve any device connected to the internet. drOid phone' checked. iPhone, iPad? checked. notebook on a trip overseas, checked.

---

### Post by Quarkrad on 2015-01-27
My itunes solution is to have itunes (10.xx) running under win7 within my ubuntu (14.04) environment via virtualbox.  It sounds a bit complicated but I access itunes via an icon on my Desktop (so - one click to get to itunes) and as it all runs in RAM it is fast - well fast enough for me.   Obviously it (itunes) does not launch as fast as it would if you were using a windows/apple machine, but this is a compromise.  I get all the benefits of Ubuntu/Linux and can run/use itunes natively.  If you want to switch environments there are things (like the firewall gui) you may not ideally like and will have to get use to as you are moving, not to a win or Apple clone, but something completely different - however, there is no fudging with itunes - you either run it on a win machine or a mac.  Using virtualbox, I suffer a small delay when I launch itunes, but I get the best of both worlds.

---

### Post by hmiersch on 2015-01-27
> **bapoumba said:**
> Which browser are you using ? Any extensions ? Blocking yahooapis ?  On my computer I use Firefox with the following addons: noscript, Adblock plus, ghostery, better privacy and tree style tabs. On my iPhone and iPad I use safari.  what is wrong with this forum? first it removes blank lines from my  posts, then i post a new message and find out it has been posted before it was ready, i try to edit the premature one and instead of editing it i end up posting another message. next thing i know, that new message disappears, and the previous message is merged with its unfinished counterpart. is that weird or is that weird?

---

### Post by TheFu on 2015-01-27
> **hmiersch said:**
> I'm not wild about this whole cloud thing. What's the point of sending my stuff to a server? It's just a big waste of bandwidth, and once it's out of my computer it's out of my control. I would never use things like Facebook, twitter or IFTTT. Online backup? That MAY be an option, if and ONLY if it is heavily encrypted before it leaves my computer. TNO -trust no one.

I agree completely, so run my servers - all linux (actually Ubuntu Server). No need for cloud anything ... well, except DNS and registrars.  Everything else runs on physical machines I control physical access for - including email.  Have been doing this since the late 1990s.

About 50% of the time people say "server" in these forums, they mean a box in a physical location they control.  It is hard to TNO when you use and store YOUR data on someone else's computer. After all, that is what "cloud" means.  RMS said > Cloud computing is careless computing.  I agree. [http://techcrunch.com/2010/12/14/stallman-cloud-computing-careless-computing/](http://techcrunch.com/2010/12/14/stallman-cloud-computing-careless-computing/)

The network is the computer, just be sure you know who is running the network and use strong encryption if you can't trust them.

---

### Post by buzzingrobot on 2015-01-27
For most folks, I think the attraction of "the cloud" is simply the synchronization: Same stuff available on multiple devices.  How that happens isn't likely to be seen as very interesting. It's just a service they're buying. The chances of them standing up, registering domains, securing and administering their own physical servers is essentially zero. (Having done it, I don't blame them.)

---

### Post by hmiersch on 2015-01-27
> Cloud computing is careless computing.    steve gibson couldn't have said it better himself. and yes, i agree 100%. which reminds me, gotta watch security now later today.

---

### Post by bapoumba on 2015-01-27
> **hmiersch said:**
> On my computer I use Firefox with the following addons: noscript, Adblock plus, ghostery, better privacy and tree style tabs. On my iPhone and iPad I use safari.  what is wrong with this forum? first it removes blank lines from my  posts, then i post a new message and find out it has been posted before it was ready, i try to edit the premature one and instead of editing it i end up posting another message. next thing i know, that new message disappears, and the previous message is merged with its unfinished counterpart. is that weird or is that weird?

Please whitelist yahooapis on the forums.
The other behavior may have been moderators or admins acting on the duplicates.

---

### Post by TheFu on 2015-01-27
Complaining about a website not working when disabling the javascript is like complaining that you get wind and rain in your hair driving a car with the windshield removed.

BTW - I run all the same FF addons. Only have to all 2 on these forums. Reasonable trade-off in privacy.  It isn't like Lifehacker with 30 3rd party and more 4th party trackers going. Any website with more than 3 required external JS mandate ... I move to somewhere else.  I get the reason for using yahooapis or google or jquery hosted javascript, but that doesn't mean I want those domains tracking me everywhere either.

---

