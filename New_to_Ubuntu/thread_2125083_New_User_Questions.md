---
title: "New User Questions"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by thatotherdude24 on 2013-03-12
Hi, I am new-er to Ubuntu and the world of Linux. I am an IT student that graduates in May and have used Windows my whole life and that's what I am taught as a student that everything runs on. I have grown a curiousity towards Linux and have found that Ubuntu is my favorite version. 2 days ago I tried to setup my laptop to dual boot Ubuntu and Windows 8, all other times I've tried to install Ubuntu it has given me an option to install next to Windows and import user info but this time for some reason it didn't and I installed over Windows 8. I'm not sure why this time it didn't give me an option. I have gotten a few questions about Ubuntu and I was hoping somebody could help me out:

1. I use Thunderbird to connect my Gmail account to. When I delete my email in Thunderbird it sends it to my 'all mail' folder in Gmail, how do I set it so it would go to my trash?

2. I have figured out how to access my Ubuntu machine from my Windows computers but I cannot seem to figure out how to access my Windows machines from Ubuntu, I get error messages. Is there something I have to set up?

3. I have 2 Windows programs I would like to run through Wine to make work on Ubuntu but how do I set that up?

4. Just a general curiousty question.....is Linux used very much in the corporate world?

I appreciate any help anybody can provide. So far I am loving Ubuntu, people make Linux out to be so complicated but really it doesn't seem to be, people are afraid of a learning curve. I would like to figure out how to install so I could configure the partitions on my own, just so I know how but I would have to play around. I am sure I will have more questions but these are just starting. Again thank you for any help you can supply.

---

### Post by RoosterHam on 2013-03-12
question 4: Linux is used extensively in many areas. By 'corporate world,' what do you mean? Linux is seeing a bit more use as a desktop OS in the corporate environment, but Microsoft has a firm hold on the corporate desktop so far. But underneath the surface, the corporate world sees more Linux serves than windows servers. In most of the corporate/enterprise environments that I have experienced, most of the windows servers that are used are now virtual systems that are hosted on linux servers.

Multitudes of systems that run corporate networks, the internet, and critical services are either Linux, BSD Unix, Solaris and so forth. Avaya builds their phone systems on Linux (Redhat or Centos), juniper networks base all their networking equipment and security devices on FreeBSD Unix.

The extent to which you will experience Linux versus windows depends on what you want to do in your career.

question 3: visit this link. [http://appdb.winehq.org/](http://appdb.winehq.org/)

question 2: How is it that you are connecting, or trying to connect between the two? samba (the network explorer links on either system)? and what error are you getting?

question 1: I don't think I've seen that before. is it like described in [https://bugzilla.mozilla.org/show_bug.cgi?id=482337](https://bugzilla.mozilla.org/show_bug.cgi?id=482337) ?

---

### Post by alphacrucis2 on 2013-03-13
> **thatotherdude24 said:**
> 

4. Just a general curiousty question.....is Linux used very much in the corporate world?




At work about half of our servers are running Linux (CentOS). It isn't so widely used on the desktop. I read somewhere, a stat that at least 65% of publicly accessible servers on the internet are running some flavour of unix with various Linux distros accounting for well over half of that. In the mobile space the Android flavour of Linux has a good chunk of the market. In scientific computing (supercomputers), Linux pretty much rules.

[http://commons.wikimedia.org/wiki/File:Operating_systems_used_on_top_500_supercomputers.svg](http://commons.wikimedia.org/wiki/File:Operating_systems_used_on_top_500_supercomputers.svg)

---

### Post by thatotherdude24 on 2013-03-13
> **RoosterHam said:**
> question 4: Linux is used extensively in many areas. By 'corporate world,' what do you mean? Linux is seeing a bit more use as a desktop OS in the corporate environment, but Microsoft has a firm hold on the corporate desktop so far. But underneath the surface, the corporate world sees more Linux serves than windows servers. In most of the corporate/enterprise environments that I have experienced, most of the windows servers that are used are now virtual systems that are hosted on linux servers.

Multitudes of systems that run corporate networks, the internet, and critical services are either Linux, BSD Unix, Solaris and so forth. Avaya builds their phone systems on Linux (Redhat or Centos), juniper networks base all their networking equipment and security devices on FreeBSD Unix.

The extent to which you will experience Linux versus windows depends on what you want to do in your career.

question 3: visit this link. [http://appdb.winehq.org/](http://appdb.winehq.org/)

question 2: How is it that you are connecting, or trying to connect between the two? samba (the network explorer links on either system)? and what error are you getting?

question 1: I don't think I've seen that before. is it like described in [https://bugzilla.mozilla.org/show_bug.cgi?id=482337](https://bugzilla.mozilla.org/show_bug.cgi?id=482337) ?


4. I was just curious, all my IT school is based on everything Windows so outside of Windows I am not very familiar because they don't teach it. I would really like to learn Linux, just from browsing all the programs that come installed on Ubuntu some of them sound like they would be very useful. I am fascinated by what computers and what OS's they run on in the corporate world, I can't explain it I find it interesting to know what they use. Is there any places you would recommend that would provide information about learning Ubuntu and Linux? Also, going into IT do you think it would be useful to learn Linux?

2. I have setup Samba on my Ubuntu machine and configured a user account. When I go to my 'home' folder on my Ubuntu machine then 'network' I select a Windows computer from my network. It loads for a while then comes up and says it is unable to connect to that computer. How do I take a screenshot on Linux and I will upload one for you.

1. From skimming yes, that seems to be what I am experiencing. When I have some more time I will read the link further and see if I can fix my problem. Is there any 3rd party email clients for Ubuntu that are any good?


Thank you for the help.

---

### Post by thatotherdude24 on 2013-03-13
> **alphacrucis2 said:**
> At work about half of our servers are running Linux (CentOS). It isn't so widely used on the desktop. I read somewhere, a stat that at least 65% of publicly accessible servers on the internet are running some flavour of unix with various Linux distros accounting for well over half of that. In the mobile space the Android flavour of Linux has a good chunk of the market. In scientific computing (supercomputers), Linux pretty much rules.

[http://commons.wikimedia.org/wiki/File:Operating_systems_used_on_top_500_supercomputers.svg](http://commons.wikimedia.org/wiki/File:Operating_systems_used_on_top_500_supercomputers.svg)



That's fascinating, I like facts like this. I like knowing what is used in the corporate world. Since about 98 Windows has tanked, Linux has skyrocketed and Mac has gone from nothing to even more so nothing. Why do you think Linux and Windows have swapped places?

---

### Post by mastablasta on 2013-03-13
> **thatotherdude24 said:**
> 3. I have 2 Windows programs I would like to run through Wine to make work on Ubuntu but how do I set that up?




not all programmes run in wine. if you would like a GUI for wine install Play on linux.

---

### Post by RoosterHam on 2013-03-13
If you are going into IT, I would certainly recommend learning Linux (and if you have the time some Unixes). The fact is that Windows has never been the dominant player in critical computing. Before Windows, before MS-DOS, there was Unix. By the time powerful computers shrunk down from filling a room for one system to having the same power in the size of a suitcase and able to be stacked on top of each other, Unix had changed the world and proven the most stable and useful OS. But it was expensive, and to some extent too difficult to use for non-technical people. So people came up with cheaper systems like MS-DOS, which were still difficult to use for non-technical people.

Technical people simply couldn't afford the powerful Unixes, so Linus Torvalds began a project to bring a Unix to his PC. With alot of issues of licensing and piracy, the philosophy of the GNU project (check that out to) enabled Linus's project to become an open source Unix-like. It acted very much like a Unix, dressed like a unix, talked like a unix, lived in the same areas as unix, but wasn't blood related.

Windows was born for non-tech people to have pretty pictures on a monitor (95,98,me, and all home editions), and MS tried to compete with the Unix and Unix-likes that were being used where power and stability were required (windows NT, windows 2000 pro/server, 2003 server, 2008 server, etc) and because everyone was seeing windows on their desktops, MS had half their advertising done for them.

Now we have Linux, we have Mac OSX which is a unix, we have android which is linux based, apple iOS which is also unix. Huge companies like IBM put as much, if not more, effort behind Linux than their own Unixes.

If your interest in IT is simply supporting some home or office desktops, you could just leave it at learning windows. If you intend to go into system/network administration, web or application development, any sort of large deployment or critical deployment occupation, learning Linux and how similar it is to Unix would truly open an entire world to you.

The good thing about Linux is that it was born online, so you can learn an incredible amount online. Howtos, youtube videos, podcasts, wikis, it's all out there. Check out Debian/Ubuntu documentation, FreeBSD documentation, and so forth. they all have wikis that google will promptly guide you to.

I'll also advise you to check out the online podcasting services of Jupiter Broadcasting at [http://www.jupiterbroadcasting.com/](http://www.jupiterbroadcasting.com/) (Linux Action Show and TechSNAP) and TWiT at [http://twit.tv/](http://twit.tv/)

2. Have you made sure that file sharing is configured on your windows machine?

---

### Post by tejpatel98 on 2013-03-13
For #3-
I would use playonlinux which is another Windows emulator which includes Wine. I run Microsoft Office Word through it and it works very well. Here is the link to installing and setting it up. [http://www.playonlinux.com/en/manual.html](http://www.playonlinux.com/en/manual.html)

---

### Post by thatotherdude24 on 2013-03-13
> **tejpatel98 said:**
> For #3-
I would use playonlinux which is another Windows emulator which includes Wine. I run Microsoft Office Word through it and it works very well. Here is the link to installing and setting it up. [http://www.playonlinux.com/en/manual.html](http://www.playonlinux.com/en/manual.html)


I used playonlinux to setup my program but when I launch it every time it crashes. Is it something I am doing wrong? Here is a link to what I am trying to install, the client download: [http://www.w7callerid.com/downloads.aspx](http://www.w7callerid.com/downloads.aspx)

---

### Post by RoosterHam on 2013-03-14
so this MCE CallerID seems like an addon to WinMCE for some kind of telephony gateway. Is this correct?

If I'm correct, I would recommend investigating asterisk PBX and it's use in this role and extension for the CallerID function...

Also, investigate XBMC to replace WinMCE. I know that when I use my smartphone as the remote, phonecalls and text messages cause playback to be paused, and texts scroll across the bottom. I suspect that someone may have worked out a way to provide the CallerID feature to XBMC also...

---

### Post by thatotherdude24 on 2013-03-14
> **RoosterHam said:**
> If you are going into IT, I would certainly recommend learning Linux (and if you have the time some Unixes). The fact is that Windows has never been the dominant player in critical computing. Before Windows, before MS-DOS, there was Unix. By the time powerful computers shrunk down from filling a room for one system to having the same power in the size of a suitcase and able to be stacked on top of each other, Unix had changed the world and proven the most stable and useful OS. But it was expensive, and to some extent too difficult to use for non-technical people. So people came up with cheaper systems like MS-DOS, which were still difficult to use for non-technical people.

Technical people simply couldn't afford the powerful Unixes, so Linus Torvalds began a project to bring a Unix to his PC. With alot of issues of licensing and piracy, the philosophy of the GNU project (check that out to) enabled Linus's project to become an open source Unix-like. It acted very much like a Unix, dressed like a unix, talked like a unix, lived in the same areas as unix, but wasn't blood related.

Windows was born for non-tech people to have pretty pictures on a monitor (95,98,me, and all home editions), and MS tried to compete with the Unix and Unix-likes that were being used where power and stability were required (windows NT, windows 2000 pro/server, 2003 server, 2008 server, etc) and because everyone was seeing windows on their desktops, MS had half their advertising done for them.

Now we have Linux, we have Mac OSX which is a unix, we have android which is linux based, apple iOS which is also unix. Huge companies like IBM put as much, if not more, effort behind Linux than their own Unixes.

If your interest in IT is simply supporting some home or office desktops, you could just leave it at learning windows. If you intend to go into system/network administration, web or application development, any sort of large deployment or critical deployment occupation, learning Linux and how similar it is to Unix would truly open an entire world to you.

The good thing about Linux is that it was born online, so you can learn an incredible amount online. Howtos, youtube videos, podcasts, wikis, it's all out there. Check out Debian/Ubuntu documentation, FreeBSD documentation, and so forth. they all have wikis that google will promptly guide you to.

I'll also advise you to check out the online podcasting services of Jupiter Broadcasting at [http://www.jupiterbroadcasting.com/](http://www.jupiterbroadcasting.com/) (Linux Action Show and TechSNAP) and TWiT at [http://twit.tv/](http://twit.tv/)

2. Have you made sure that file sharing is configured on your windows machine?



Thank you for your help. One thing I have noticed on this forum compared to various Windows or Mac forums is nobody acts like they are better than anybody else. Whether it is just the forums I am looking at or if that's how people think they are on those I don't know, I have browsed many other threads on this site and people seem like they are very willing to help. I have been told on other sites I'm stupid and if I don't already know the answer to the question I am asking I shouldn't be on there. Bottom line is I'm asking because I don't know, no matter what the question is. I have a desire and openness to learn so I can better myself for the future, so far on this site people seem very willing to help.

Just out of curiosity where did you learn all that? Just from being around I have always heard people say Mac is for 'dumb and old people', Windows is for 'techies and people who know how to use a computer' and Linux is too hard for anybody to use. Kind of like Windows 8, a majority, not all, people who complain about it are people who have never used it. So far Linux seems very straightforward to me, yes I am a tech person but the stuff I am wanting to learn is not things a basic user would need to know.

So what do corporate companies use for mobile devices? I have seen how a lot are switching to iPhone, I myself have an iPhone 5, it's nothing special but it's a phone and simply works all the time. Why don't companies go with Windows Phones or Android tablets?

My interest in IT is the corporate world, being in the big corporate companies who thrive on technology, not a local PC shop fixing computers that come in. I'm not saying that that area isn't important but my big interest is corporate. Right now with being in my last semester of college I do setup home networks, computers, printers and so on for people who need stuff done in their homes, not big money making stuff but things to boost my experience.

Thank you, I will check those sites out. Is there any good 'useful' Linux books or magazine subscriptions that actually have information that is helpful and not totally opinionated?

As far as I know file sharing is setup on my Windows machines, I have no problem sharing from Windows to Windows or Windows to Ubuntu, my problem is only in Ubuntu to Windows.

Going off your response from last night and from the one quoted I found these articles: [50 Places]("http://www.comparebusinessproducts.com/fyi/50-places-linux-running-you-might-not-expect") and [Google]("http://www.theverge.com/2013/3/13/4100160/google-shuffle-can-android-and-chrome-os-combine-to-take-on-microsoft"). I find them both very interesting, especially the one about who all has switched to Linux. The Google one I think they could be onto something if they go about it the right way, Windows 8 has caused computer prices to go skyhigh and if Google could make a desktop OS that isn't only internet based but yet still provide it with decent quality and lower prices they could be onto something. Just curious on your thoughts or any others....

---

### Post by thatotherdude24 on 2013-03-14
> **RoosterHam said:**
> so this MCE CallerID seems like an addon to WinMCE for some kind of telephony gateway. Is this correct?

If I'm correct, I would recommend investigating asterisk PBX and it's use in this role and extension for the CallerID function...


What it does is, I have a modem in my desktop PC that is connected to a phone jack. It runs the server software and I connect all my client PCs and WinMCE to it and that allows the Caller ID to show up on all client computers and WinMCE.

I have a Centon Infinity Quad Tuner with a cablecard in it so I can record channels that I need a cable box for and I have only every been told that it will work with Windows Media Center. I can live record and/or watch live TV or recorded TV and stream it to any Xbox in the house. Is there another way to do this?

---

### Post by RoosterHam on 2013-03-14
The community that uses and develops Linux and other open source software is, for the most part, one of the most friendly and helpful internet communities around. Some people are not so helpful, but I know that I've made a fool of myself many times and I've never been flamed for it. To most of us, it's all about sharing knowledge with each other while getting knowledge from others and by trying things out.

I learned alot of what I know from the ubuntu and debian howto sites and wikis, as well as wikipedia. Magazines that I have used to learn from are "Linux Journal">[http://www.linuxjournal.com/](http://www.linuxjournal.com/) and "Hackin9" and books include "Linux for dummies" and all Linux related books from O'Reilly > [http://oreilly.com](http://oreilly.com)

The preference for IPhones, that I'm seeing in corporations also, seems to be mainly for uniformity (one ios, fairly compatible between all devices) and more consistency. By that I mean that phone companies can offer an android range from the same manufacturer, but the differences between the androids means the support desk has to be more knowledgeable, then the provider might or might not change their prefered range, and what is that going to mean to a company with a contract for 100 to 4000 mobile devices? Is their provider going to take care of them? Or are they going to say it's not their issue, talk to the manufacturer? What comes with the range? How proven are all of these devices? So to a corporation, they take the best deal that their chosen provider, or the best deal all the providers they trust, can present to them. They'll try to pick devices with the longest good record, that does everything they want and more, for the cheapest.

I did a similar thing to start in IT. I supported friends, friends-of-friends, family, friends-of-family, most often recovering files and replacing hard drives in laptops that had terrible overheating problems and fixing up laboured Pentium 4 machines that people treated like and expected to keep up with multi-core 64bit systems. Now I'm lucky enough to be part of a Unified Communications solutions company, mainly on the network infrastructure side.

Before I go on, I have to be honest, I am lost as to suggesting a way of getting the same result for your callerID thing. I have a bit of experience with IP telephony, but mainly taking phone lines for a large corporation off TDM lines, recording (with Digium's opensource Asterisk) the necessary lines while passing the phone exchange task on to a different Linux based PABX solution (Avaya). But pulling off of the Plain Old Telephone System, and distributing data to Windows platforms is a little out of my knowlege.

But that aside...
The tuner card you have seems to be a bit of a hot subject. I simply googled it  and "linux support" and found dozens of flame wars about whether Linux supports it. > [http://forum.linuxmce.org/index.php?topic=8852.20;wap2](http://forum.linuxmce.org/index.php?topic=8852.20;wap2) MythTV seems to support it and there's instructions here > [http://www.mythtv.org/wiki/Ceton_InfiniTV_4](http://www.mythtv.org/wiki/Ceton_InfiniTV_4)

MythTV is great. You can tune, record, stream, and probably make a nice batch of pancakes, with all your media and entertainment connections. IPTV, saved media files, analogue TV and cable TV. You can stream it to all your PCs and so forth, but check the links below to see how you can use it and set it up. I don't use it currently, but I plan to when I get the freedom of networking my home properly.
[http://www.mythtv.org/wiki/MythTV-HOWTO](http://www.mythtv.org/wiki/MythTV-HOWTO)
[http://www.mythtv.org/wiki/Main_Page](http://www.mythtv.org/wiki/Main_Page)
[http://www.mythtv.org/](http://www.mythtv.org/)

---

### Post by Vaspro on 2013-03-15
Am new to the forum can some one help me to know what is the common difference in ubuntu and os and linux

---

### Post by ubuntu27 on 2013-03-15
> **thatotherdude24 said:**
> 

1. I use Thunderbird to connect my Gmail account to. When I delete my email in Thunderbird it sends it to my 'all mail' folder in Gmail, how do I set it so it would go to my trash?



Open Thunderbird
EDIT menu----->Account Settings-----> [Select your account on the left] ----------> Server Settings------> "When I delete a message..."-------> [Choose desired location (e.g. Trash, Gmail Trash, etc)]

> **thatotherdude24 said:**
> 
4. Just a general curiousty question.....is Linux used very much in the corporate world?
[URL="http://www.comparebusinessproducts.com/fyi/50-places-linux-running-you-might-not-expect"]

50 Places Linux is Running That You Might Not Expect[/URL]

---

### Post by mastablasta on 2013-03-15
> **Vaspro said:**
> Am new to the forum can some one help me to know what is the common difference in ubuntu and os and linux

ubutnu OS is software packages (programmes and such) + linux kernel (core). Ubutnu is one of many linux distributions. Other linux distributions are for example Red Hat, Debian, Linux Mint, Puppy Linux, Gentoo, Slackware, Arch linux.... and many others.

---

### Post by coldraven on 2013-03-15
Free Linux magazine, you can also download all the back issues.
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by MoebusNet on 2013-03-15
> **Vaspro said:**
> Am new to the forum can some one help me to know what is the common difference in ubuntu and os and linux

To expand on mastablasta's excellent response:

"An operating system (OS) is a collection of software that manages computer hardware resources and provides common services for computer programs. The operating system is a vital component of the system software in a computer system. Application programs usually require an operating system to function."..."Examples of popular modern operating systems include Android, BSD, iOS, Linux, Mac OS X, Microsoft Windows,[3] Windows Phone, and IBM z/OS. All these, except Windows and z/OS, share roots in UNIX."

[http://en.wikipedia.org/wiki/Operating_system](http://en.wikipedia.org/wiki/Operating_system)

"Linux (Listeni/&#712;l&#618;n&#601;ks/ LIN-&#601;ks[6][7] or /&#712;l&#618;n&#650;ks/ LIN-uuks)[8][9][10] is a Unix-like computer operating system assembled under the model of free and open source software development and distribution. The defining component of Linux is the Linux kernel, an operating system kernel first released 5 October 1991 by Linus Torvalds.[11][12]"..."Some popular mainstream Linux distributions include Debian (and its derivatives such as Ubuntu and Linux Mint), Red Hat Enterprise Linux (and its derivatives such as Fedora and CentOS), Mandriva/Mageia, openSUSE (and its commercial derivative SUSE Linux Enterprise Server), and Arch Linux."

[http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)

---

### Post by thatotherdude24 on 2013-03-15
> **RoosterHam said:**
> The community that uses and develops Linux and other open source software is, for the most part, one of the most friendly and helpful internet communities around. Some people are not so helpful, but I know that I've made a fool of myself many times and I've never been flamed for it. To most of us, it's all about sharing knowledge with each other while getting knowledge from others and by trying things out.

I learned alot of what I know from the ubuntu and debian howto sites and wikis, as well as wikipedia. Magazines that I have used to learn from are "Linux Journal">[http://www.linuxjournal.com/](http://www.linuxjournal.com/) and "Hackin9" and books include "Linux for dummies" and all Linux related books from O'Reilly > [http://oreilly.com](http://oreilly.com)

The preference for IPhones, that I'm seeing in corporations also, seems to be mainly for uniformity (one ios, fairly compatible between all devices) and more consistency. By that I mean that phone companies can offer an android range from the same manufacturer, but the differences between the androids means the support desk has to be more knowledgeable, then the provider might or might not change their prefered range, and what is that going to mean to a company with a contract for 100 to 4000 mobile devices? Is their provider going to take care of them? Or are they going to say it's not their issue, talk to the manufacturer? What comes with the range? How proven are all of these devices? So to a corporation, they take the best deal that their chosen provider, or the best deal all the providers they trust, can present to them. They'll try to pick devices with the longest good record, that does everything they want and more, for the cheapest.

I did a similar thing to start in IT. I supported friends, friends-of-friends, family, friends-of-family, most often recovering files and replacing hard drives in laptops that had terrible overheating problems and fixing up laboured Pentium 4 machines that people treated like and expected to keep up with multi-core 64bit systems. Now I'm lucky enough to be part of a Unified Communications solutions company, mainly on the network infrastructure side.

Before I go on, I have to be honest, I am lost as to suggesting a way of getting the same result for your callerID thing. I have a bit of experience with IP telephony, but mainly taking phone lines for a large corporation off TDM lines, recording (with Digium's opensource Asterisk) the necessary lines while passing the phone exchange task on to a different Linux based PABX solution (Avaya). But pulling off of the Plain Old Telephone System, and distributing data to Windows platforms is a little out of my knowlege.

But that aside...
The tuner card you have seems to be a bit of a hot subject. I simply googled it  and "linux support" and found dozens of flame wars about whether Linux supports it. > [http://forum.linuxmce.org/index.php?topic=8852.20;wap2](http://forum.linuxmce.org/index.php?topic=8852.20;wap2) MythTV seems to support it and there's instructions here > [http://www.mythtv.org/wiki/Ceton_InfiniTV_4](http://www.mythtv.org/wiki/Ceton_InfiniTV_4)

MythTV is great. You can tune, record, stream, and probably make a nice batch of pancakes, with all your media and entertainment connections. IPTV, saved media files, analogue TV and cable TV. You can stream it to all your PCs and so forth, but check the links below to see how you can use it and set it up. I don't use it currently, but I plan to when I get the freedom of networking my home properly.
[http://www.mythtv.org/wiki/MythTV-HOWTO](http://www.mythtv.org/wiki/MythTV-HOWTO)
[http://www.mythtv.org/wiki/Main_Page](http://www.mythtv.org/wiki/Main_Page)
[http://www.mythtv.org/](http://www.mythtv.org/)



I just try to better myself and expand my knowledge and people helping people is how stuff like that happens. So probably a dumb question......what all could Ubuntu be used for in a home server type environment?


That makes sense, even though Android is a form of Linux Samsung's version of Android is different from LG's version of Android. 


I've noticed that, people want to spend under $500 for a laptop but yet expect performance out of it from a $800+ laptop. Another dumb question.....what is a Unified Communications solutions company?


One of the things that sucks about WMCE is it can only be watched on that same computer, I try to stream it to my Xbox's by using the Windows Media center app but it lags terribly, I believe that is my network though but I can't get it resolved. I've done an install of Myth but it looks so complicated to setup. The same computer I have my tuner in is the one that I also do my gaming on and I have heard that Linux isn't so great at trying to do heavy gaming on.

---

### Post by RoosterHam on 2013-03-17
> **thatotherdude24 said:**
> I just try to better myself and expand my knowledge and people helping people is how stuff like that happens. So probably a dumb question......what all could Ubuntu be used for in a home server type environment?


That makes sense, even though Android is a form of Linux Samsung's version of Android is different from LG's version of Android. 


I've noticed that, people want to spend under $500 for a laptop but yet expect performance out of it from a $800+ laptop. Another dumb question.....what is a Unified Communications solutions company?


One of the things that sucks about WMCE is it can only be watched on that same computer, I try to stream it to my Xbox's by using the Windows Media center app but it lags terribly, I believe that is my network though but I can't get it resolved. I've done an install of Myth but it looks so complicated to setup. The same computer I have my tuner in is the one that I also do my gaming on and I have heard that Linux isn't so great at trying to do heavy gaming on.

You are quite correct. We all have things that we know, and each of us know, and have experienced different things. So unless a person wants to repeat every single experiment, mistake and project ever devised by themselves, then learning from others is how we better ourselves. To learn from others, we admit to everyone that we don't know something, and they can then share their experiences and knowledge.

Linux can perform many roles in the Home server arena. Pretty much all of them. Sometimes, exactly like the MythTV example, it can be a steep learning curve and quite overwhelming. I myself use LXC and KVM to host typical home services on a trio of servers. Services like filesharing via Samba (windows compatible), internal DNS, intrusion detection and web proxy. Zentyal [http://www.zentyal.org/](http://www.zentyal.org/) is an option to make the whole process a little easier, and it'll point out some of the many things Linux can do in a home or small business network.

Linux's lack of uniformity hurts its popularity among many potential users, but I think most Linux users find the lack of being restricted and dictated to the very reason we use Linux, and that without all these options, Linux would lose much of its power.

Linux is actually rather good for gaming. The problem has always been lack of flashy games. Loki software brought some incredible games to Linux, and now valve (a pretty major game publisher) has released Steam for Linux, and many of their games are available on Linux via Steam. Valve did a lot of work with Ubuntu developers and nvidia to get some incredible gaming on Linux. There are also open-source games that I would argue are as good as the proprietary games out. Some Windows games will work under Wine.

Unified Communications (UC) is a big chunk of what we all use, VoIP, instant messaging, group/office collaboration software, file sharing/distribution services, a bunch of communications and productivity software/services/protocols- all integrated for a particular group or company into a useful system. The epitome of UC would be someone logging into their company's network from anywhere in the world, joining a video conference where people in different cities could work on one project, making changes to the same file as they agree. When the conference ends or if someone has a meeting to travel to, work can continue on the files/project by everyone, and all could continue to communicate via software phones, text messages, internet chat (facebook chat).

That example is pretty out there, and can be accomplished without designing a specific network or service for this purpose. Many of our clients start with wanting an internal phone system, or to secure their existing network with some of our security solutions, or improve their network to handle more traffic. I tend to work more with the network infrastructure, switches, routers, hardware firewalls and wireless lan controllers and access points.

I also keep involved with core network services like dns, network management software, syslog servers and vitalization platforms. This is where Linux/Unix excels.

---

### Post by thatotherdude24 on 2013-03-18
> **RoosterHam said:**
> You are quite correct. We all have things that we know, and each of us know, and have experienced different things. So unless a person wants to repeat every single experiment, mistake and project ever devised by themselves, then learning from others is how we better ourselves. To learn from others, we admit to everyone that we don't know something, and they can then share their experiences and knowledge.

Linux can perform many roles in the Home server arena. Pretty much all of them. Sometimes, exactly like the MythTV example, it can be a steep learning curve and quite overwhelming. I myself use LXC and KVM to host typical home services on a trio of servers. Services like filesharing via Samba (windows compatible), internal DNS, intrusion detection and web proxy. Zentyal [http://www.zentyal.org/](http://www.zentyal.org/) is an option to make the whole process a little easier, and it'll point out some of the many things Linux can do in a home or small business network.

Linux's lack of uniformity hurts its popularity among many potential users, but I think most Linux users find the lack of being restricted and dictated to the very reason we use Linux, and that without all these options, Linux would lose much of its power.

Linux is actually rather good for gaming. The problem has always been lack of flashy games. Loki software brought some incredible games to Linux, and now valve (a pretty major game publisher) has released Steam for Linux, and many of their games are available on Linux via Steam. Valve did a lot of work with Ubuntu developers and nvidia to get some incredible gaming on Linux. There are also open-source games that I would argue are as good as the proprietary games out. Some Windows games will work under Wine.

Unified Communications (UC) is a big chunk of what we all use, VoIP, instant messaging, group/office collaboration software, file sharing/distribution services, a bunch of communications and productivity software/services/protocols- all integrated for a particular group or company into a useful system. The epitome of UC would be someone logging into their company's network from anywhere in the world, joining a video conference where people in different cities could work on one project, making changes to the same file as they agree. When the conference ends or if someone has a meeting to travel to, work can continue on the files/project by everyone, and all could continue to communicate via software phones, text messages, internet chat (facebook chat).

That example is pretty out there, and can be accomplished without designing a specific network or service for this purpose. Many of our clients start with wanting an internal phone system, or to secure their existing network with some of our security solutions, or improve their network to handle more traffic. I tend to work more with the network infrastructure, switches, routers, hardware firewalls and wireless lan controllers and access points.

I also keep involved with core network services like dns, network management software, syslog servers and vitalization platforms. This is where Linux/Unix excels.



I am finding that on this forum my issues get easily resolved, even when I had to contact Conanical (sp) once regarding an issue I got a reply not even 1 hour later and my problem was fixed. There was no questionnaire to fill out to be able to get help, nowhere was money asked for, I asked a question and the guy responded straight and to the point. In the past when I have contacted Dell or HP I always hear "I'm so sorry you're having issues with out product i will do everything to make your experience excellent" I hate hearing that because I really doubt the person on the other end of the phone actually cares it's their job to fix problems and I just want my issue corrected, don't waste my time with fancy scripted responses. When Conanical (sp) answered it was right to the point. I posted on Microsoft's forums this weekend because I kept having issues with a clients router/printer and 3 days later I finally got a response where the guy provided a link for me to go step by step of how to set up a router, to me chances are if I am able to navigate to Microsoft's forum site I know the basics of what I am doing, they never did answer my problem and wasted my time. Here everything is answered with no filler.

Right now for a home server I run Windows Home Server 2011, I store tons of files to the server that all the computers in the house access. Every person has their own username and password to log into it by going to the "Network" window and accessing the files, I do have permissions set so that each person can't get into the others files. I also have it set so for example the music folder somebody can open a track and listen to it but nobody can delete or edit and contents in the folder. It also has web remote access so I each person can log into the server through any web browser and access the files they have stored on the server and upload/download files. Every night all the computers backup to the home server on their own and then the home server backs itself up onto another hard drive. I access my home server remotely but I have never been able to setup remote access for a Linux machine that works right. There are a few things I dislike about Home Server 2011: 1. when I connect the client computers to the server the resources the clients use goes sky high, they idle at 2.5GB RAM and all the sudden 4GB becomes not enough in a computer. 2, On my Windows Media Center computer I can't transfer recorded shows to my home server and be able to watch them on another computer, only on the computer they were recorded on. I do think it would be cool in the future to get like a network surveillance camera, place it outside and be able to watch the video and possibly even record it onto my computer. Do you think all this would be possible with Ubuntu/Ubuntu Server or any version of Linux?

I do purchase all my PC games through Steam but there are not made for Linux and I don't know how to make them run properly on Linux. Where would I get video drivers for cards for Linux? I don't know very much command prompt.

So what time of computer systems are used at your work?

---

### Post by RoosterHam on 2013-03-18
Support can be a nightmare from many companies. And sometimes it just feels like they imply that a problem with their product is your fault.

I mainly encounter HP servers and some Dell through my company, mostly installed with debian, ubuntu, or a few with centos and suse. My preference is definitely toward debian/ubuntu, particularly on the server side. 

The network you have sounds quite straight-forward. A per-share password/permissions setup rather than a domain? Samba on Linux provides this function reliably, and with per user read/write access rights. With Samba4 (recently stable) you can go further to a full ActiveDirectory style domain login, where logging into your computer logs you into the domain, where your permissions are inherited from your domain login, but this seems different and more setup-intensive than your setup now. You issue with the clients reminds me of a post I read on here with an ubuntu+samba server. That happened to be related to authentication. If you search this forum for the same issue with samba servers, there might be a similar issue that you could get clues about from a samba fix.
 
Ubuntu and pretty much any other Linux distribution will have Samba available for replacing your Windows server. There is software available for your media and security camera streaming/recording, MythTV is one option but I'm not sure of the range of others. 

Steam is slowly adding games to Linux native, but it could take some time. While Linux is great for gaming from a technical perspective, if there's no native version and the particular game doesn't work well with WINE, sadly, you may have to just leave your favourite game on a windows install for now.

---

### Post by rich4421972 on 2013-03-18
IMHO, Red Hat has some of the best product support setups of many of the commercial linux (I mean enterprise).Bug fixes are usually posted within 24-hours of their discovery and customer service is fast and tailored to the needs of the individual customers. I'm sure that   Canonical has a similar quality of service. 

Here is some brief usage data (Net Applications Research). I hope it is interesting to post it here:

Desktop usage of linux is still within  the 1-3% range. Mainframe usage varies by vendor but has reached nearly 80% at different times (between IBM, Novell, Red Hat and Oracle).  In the article (below), I really didn't understand where the 93% linux numbers came from.


Mac OS has hovered around 5-6% for some time now (currently it's  at 7%). At my college, most of our networked computers are based on one windows operating system while the actual workstations use VMware to run something more current like Windows 7. We have no linux or UNIX systems (instead using VMware and Netware to run emulators for other operating systems). 

Thus, while linux may run well insupercomputer  and research roles, individual corporationscan run Windows on top of a linux or other windows OS base. Linux performs even worse compared to embedded OS's like android and iOS.

Market share is divided between various Windows Operating systems(98, 2000, Me, XP, Vista, 7 and Win8) and gives Windows a total market share of over 90%. Whether or not this is good/bad news for linux, it is a reflection of what is actually happening. I think that these numbers could be spun any number of ways but they are actual data collected by firms who record internet usage of linux and BSD (notice this a is a very inexact science). It is nice to be able to put some actual statistics behind the claims that are made. See this article for the current OS usage  statistics:

[http://en.wikipedia.org/wiki/Usage_share_of_operating_systems](http://en.wikipedia.org/wiki/Usage_share_of_operating_systems)

What it all means to me is that providing service for linux systems may be a lonely business especially with the prevalence of Microsoft's MCP and MCSE/MCSA certifications being requirements for entry-level employment. In addition, there is no evidence that Mac OS has (or ever has had) a decreasing market share.

---

### Post by thatotherdude24 on 2013-03-21
> **RoosterHam said:**
> Support can be a nightmare from many companies. And sometimes it just feels like they imply that a problem with their product is your fault.

I mainly encounter HP servers and some Dell through my company, mostly installed with debian, ubuntu, or a few with centos and suse. My preference is definitely toward debian/ubuntu, particularly on the server side. 

The network you have sounds quite straight-forward. A per-share password/permissions setup rather than a domain? Samba on Linux provides this function reliably, and with per user read/write access rights. With Samba4 (recently stable) you can go further to a full ActiveDirectory style domain login, where logging into your computer logs you into the domain, where your permissions are inherited from your domain login, but this seems different and more setup-intensive than your setup now. You issue with the clients reminds me of a post I read on here with an ubuntu+samba server. That happened to be related to authentication. If you search this forum for the same issue with samba servers, there might be a similar issue that you could get clues about from a samba fix.
 
Ubuntu and pretty much any other Linux distribution will have Samba available for replacing your Windows server. There is software available for your media and security camera streaming/recording, MythTV is one option but I'm not sure of the range of others. 

Steam is slowly adding games to Linux native, but it could take some time. While Linux is great for gaming from a technical perspective, if there's no native version and the particular game doesn't work well with WINE, sadly, you may have to just leave your favourite game on a windows install for now.


I have been trying to install Samba4 on Ubuntu but I have not been able to figure it out. Does Samba4 have a GUI?

---

### Post by RoosterHam on 2013-03-21
[http://www.samba.org/samba/GUI/](http://www.samba.org/samba/GUI/)

The samba project doesn't actively integrate a gui into samba packages, but many groups have integrated with samba in various ways. The link above will give you a great idea.

I think webmin might be great for your situation, with more than just samba coming under it's umbrella.

---

### Post by thatotherdude24 on 2013-03-26
> **RoosterHam said:**
> [http://www.samba.org/samba/GUI/](http://www.samba.org/samba/GUI/)

The samba project doesn't actively integrate a gui into samba packages, but many groups have integrated with samba in various ways. The link above will give you a great idea.

I think webmin might be great for your situation, with more than just samba coming under it's umbrella.


Thank you for all the help you have provided. Sorry for the delay, the past week has been nuts.

So making sure I understand correctly.....there is no 1 single package that will provide a GUI for samba4 but through a few packages or different programs I could have a GUI for all the features of samba4? 

What does webmin do?

---

### Post by RoosterHam on 2013-04-01
Correct. Samba doesn't install with one gui for controlling it. Some distributions do install with some sort of tools for basic samba configuration, I think suse and redhat do more on that side. But I am pleased that ubuntu and debian installed as a basic server don't install with any graphical tools, leaving as much of your resources for critical services.
[URL="http://www.webmin.com/intro.html"]
Check out more about webmin there >> http://www.webmin.com/intro.html[/URL]

---

### Post by thatotherdude24 on 2013-04-03
> **RoosterHam said:**
> Correct. Samba doesn't install with one gui for controlling it. Some distributions do install with some sort of tools for basic samba configuration, I think suse and redhat do more on that side. But I am pleased that ubuntu and debian installed as a basic server don't install with any graphical tools, leaving as much of your resources for critical services.
[URL="http://www.webmin.com/intro.html"]
Check out more about webmin there >> http://www.webmin.com/intro.html[/URL]


I am in the process of switching my home server to Ubuntu 12.10. I have run into a few issues, probably simple fixes I am just over looking it. I have installed Samba on the computer and can see my Ubuntu machine from my Windows machines. I right click on the folder I want to share and click share. I need to setup some type of permissions so certain people can not even access certain folders but they are still shared so others can access them, how do I do this?

I cannot get certain applications to run in Linux that I use in Windows so I have come up with the idea of having a VM running on my Ubuntu home server that is running those apps. Does that sound reasonable? Is there another VM client you would recommend besides VirtualBox?

Also, how do I setup remote access so I can access the Ubuntu machine from another computer?

---

