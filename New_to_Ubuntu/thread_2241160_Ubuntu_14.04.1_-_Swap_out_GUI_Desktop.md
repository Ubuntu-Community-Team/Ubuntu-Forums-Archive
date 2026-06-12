---
title: "Ubuntu 14.04.1 - Swap out GUI Desktop?"
date: 2014-08-24
forum: New to Ubuntu
---

### Post by incurablegeek on 2014-08-24
I've dawdled on this fine forum in the past but never really committed  to Linux. Am now migrating from Windows (25 years) to Linux for obvious  reasons. (Nadella may be more of an *idiota* than Ballmer was.)

Two quick questions:

1) It is my vague understanding that if one does not like the MAC-like  desktop of Ubuntu, it's only a matter of swapping out the GUI so it  looks like Windows (Taskbar on bottom, multiple monitors, split screens  on each monitor a must). True or False?

2) Although I know (think I know) that Ubuntu and Mint are built on the  same engine, Ubuntu appears to have more support - hardware, programs,  etc. True or False.


Brief Comment: This is one of the very few forums of which I have been a  member where there are no trolls. Simply put, I appreciate all of the  kindness and assistance you have afforded me in the past. And so that I  will not annoy you with really, really stupid questions, I am taking  Linux classes both online ([https://www.edx.org/](https://www.edx.org/) - just starting, so cannot speak to its quality but for audit students it's FREE) and at the local college.

Also please note that I did do a search but the advisory banner led me to believe that the thread was either dead or only for discussion. My apologies if I am wrong.  :confused:

---

### Post by Bashing-om on 2014-08-24
incurablegeek; Hi !  Welcome to the forum:

1: TRUE
Me:
> 
sysop@1404mini:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty
sysop@1404mini:~$

sysop@1404mini:~$ echo $DESKTOP_SESSION
xfce
sysop@1404mini:~$ 

sysop@1404mini:~$ xfdesktop -V
This is xfdesktop version 4.11.6, running on Xfce 4.10.
Built with GTK+ 2.24.23, linked with GTK+ 2.24.23.
Build options:
    Desktop Menu:        enabled
    Desktop Icons:       enabled
    Desktop File Icons:  enabled
sysop@1404mini:~$


2) True:
[INDENT][INDENT]The truth needs no further explanation[/INDENT][/INDENT]

3) Here there is no such thing as a "dumb question" ! Ask away.

[INDENT][INDENT][INDENT]buntu'
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by incurablegeek on 2014-08-24
> Do you want something that looks/feels more like Windows?

I use my computers for work - no gaming and don't need a whistles and bells cutesy interface. 

What I do need is quite simple:

1) Taskbar at the bottom - perhaps customizable across two separate (not conjoined as some gamers do) monitors. Can explain further if need be.

2) "Fences" - to organize programs on the Desktop - Do not care about and almost never use the Windows Start Menu

Note: I try to be succinct out of consideration of your time. Here's what I think I should do: Install Ubuntu, play with it and then get back to you - especially after I have a better understanding of Ubuntu and the various "flavors".

---

### Post by Tadaen_Sylvermane on 2014-08-24
Xfce for lightweight. KDE for pure awesome.

---

### Post by Bashing-om on 2014-08-24
incurablegeek; Well;

There are 5 sisters to ubuntu, and scores of spin offs whose only major difference is the desktop and what aps are preinstalled;
For instance you might try:
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
[http://ubuntugnome.org/download/](http://ubuntugnome.org/download/)
[http://www.ubuntukylin.com/downloads/show.php?lang=en&id=122](http://www.ubuntukylin.com/downloads/show.php?lang=en&id=122)
[http://www.edubuntu.org/download](http://www.edubuntu.org/download)
and see which of these you feel the more comfortable with

In addition there are countless desk top managers one can install as:  openbox or fluxbox, ect.

Presently, make an install and get comfortable with some desk top, and get the experience/knowledge to know what is available that best suits your needs/wants.

I want my desktop environment fast, clean, configurable, and simple -> xfce4 !

[INDENT][INDENT]options are truly limitless
[/INDENT][/INDENT]

---

### Post by incurablegeek on 2014-08-24
Now I shall fully reveal my ignorance here, so please feel free to laugh. I quite honestly don't mind, as long as I learn in the process.

My understanding of Ubuntu is:

1) More hardware and software (programs) are made for Ubuntu than for any other Linux distro.

2) Ubuntu is the Linux engine - on top of which different GUI's (desktop layouts) can be overlaid. 

3) I have read Gnome 3, for example, is easier to navigate and more glitch-free (whatever that means) than Ubuntu Unity - but Gnome is slow to implement Ubuntu updates.

I guess the big question I am asking is when I settle upon Ubuntu, which I definitely will do, can I modify/exchange the desktop GUI so it is faster and more efficient for my work environment?

---

### Post by ibjsb4 on 2014-08-25
> I guess the big question I am asking is when I settle upon Ubuntu, which  I definitely will do, can I modify/exchange the desktop GUI so it is  faster and more efficient for my work environment? 				

Yes you can, but it would be better to install something that fits your computer capabilities.

Ubuntu is resource demanding, Xubuntu no so much and Lubuntu even less.  Kubuntu is somewhere between ubuntu and xubuntu.

How bout posting your computer specs (cpu, ram, graphics).

---

### Post by mooreted on 2014-08-25
I use Xubuntu with the Docky dock. It looks a  lot like Windows 7.

Wow, Flickr code is confusing. Finally got it:

[[img]https://farm6.staticflickr.com/5567/14841015450_fc2a1e4233.jpg[/img]](https://flic.kr/p/oBs5QJ)[Xubuntu_Docky](https://flic.kr/p/oBs5QJ)

---

### Post by 3rdalbum on 2014-08-25
1. All Linux software can be run on all Linux distros - nearly. But Ubuntu is so popular it's the de facto standard. It also has a very large selection of software available from the package manager.

2. Ubuntu is both the underlying base, and the version with the Unity desktop.

3. Gnome 3 is just a different desktop for people who prefer it. Ubuntu does not always have the absolute latest Gnome available, but it always has a recent version.

I encourage you to try regular Ubuntu (with the Unity desktop) for a week. It's a good desktop and it definitely grows on you after first impressions. It's very different to anything you have used before, but then so is Linux. If you still don't like it after 7-10 days you can install a different desktop. It is easy and there is no penalty for having multiple desktops installed simultaneously.

---

### Post by pfeiffep on 2014-08-25
> **incurablegeek said:**
> 1) It is my vague understanding that if one does not like the MAC-like  desktop of Ubuntu, it's only a matter of swapping out the GUI so it  looks like Windows (Taskbar on bottom, multiple monitors, split screens  on each monitor a must). True or False? 

I've converted most of my personal computing from Microsoft (DOS 3 to Win 7) to Ubuntu. 
I found a rather easy transition from the bottom task bar to the top by using gnome flashback. 
Program start up icons can be placed on the top and the currently running programs are displayed on the bottom.

I have no experience with multiple monitors.

---

### Post by christopher9 on 2014-08-25
Wow....just wow...big thumbs up on that !

My experience is limited but after trying Ubuntu, Kubuntu, Elementary, Mint, and Lubuntu (loving it the most), KDE should easily satisfy the OP demands....

---

### Post by incurablegeek on 2014-08-25
@3rdalbum

> It is easy and there is no penalty for having multiple desktops installed simultaneously.

That IS huge. Thank you.

What I have heard, and yet again today from friends in my Cisco Router classes: The Unity desktop is awkward and difficult to navigate, Linux Mint being the better choice. 

Here is what ZDNet says (and yes, I read too much)
> What Mint has going for it is an outstanding desktop interface of its own, [Cinnamon]("http://www.zdnet.com/blog/open-source/mints-cinnamon-the-future-of-the-linux-desktop-review/10246"),  which is very remindful of the classic GNOME 2.x interface. Add to that  outstanding software and hardware support, there's little question as  to why [Mint still appears to be the most desktop popular Linux of all]("http://www.zdnet.com/blog/open-source/the-most-popular-linux-is/9913").

I start my Linux classes this Thursday evening so many of these questions I am asking will hopefully become more "refined". What I don't want to do is migrate from Ubuntu to some other distro that may or may not be here or supported down the line.

Again: what 3rdalbum has said intrigues me greatly. [COLOR=#008000][FONT=comic sans ms]So switching out Unity for Gnome for Cinnamon, etc. is just a simple overlay on the Ubuntu engine?

[/FONT][/COLOR][FONT=comic sans ms].....................[/FONT][COLOR=#008000][FONT=comic sans ms]

[/FONT][/COLOR][SIZE=2][FONT=arial]In answer to a question about my computer hardware resources, all my computers are AMD 6-core, 16 GB DDR-3 RAM, with very high quality graphics cards. When it comes to computer hardware, I am certifiably insane - purchase only the best: 7 computers, file server, 60 TB of storage, pfSense Network Appliance with Cisco SG-300 switch. In short, not light on resources.[/FONT][/SIZE][COLOR=#008000][FONT=comic sans ms]

I want to migrate all my work from Win 7 to Ubuntu - but am a bit scared to make the leap.  :eek:
[/FONT]
[/COLOR]

---

### Post by dave131 on 2014-08-25
I don't know how well any of this works, as it is not supported by the Ubuntu repositories, but if you also want to try Cinnamon in Ubuntu, try this link.  It reports 2 new ppa's for grabbing it but I haven't tried either - maybe I will later.

[http://askubuntu.com/questions/94201/how-do-i-install-the-cinnamon-desktop](http://askubuntu.com/questions/94201/how-do-i-install-the-cinnamon-desktop)

As someone earlier showed, there are dock program which can give a similar look, and I *think* the lxde desktop provides that Windows look as well.  All of everyone is saying here is that there are options, after installing Ubuntu, to change the desktop environment to how you want.  Several are available to try, and it doesn't mean you permanently changed anything as the desktop is selectable on the login screen.

EDIT:  thought I'd attach a screen shot from the lxde desktop as well - it is more Windows-like.

---

### Post by Jonathan Precise on 2014-08-26
I have used avant-window-navigator for the dock. To disable the MAC-like look/panels, disable Unity in CCSM. (and add [FONT=Courier New]sleep 3; initctl --user stop unity-panel-service[/FONT] to your start-up apps)

Once installed, go to AWN settings, and customize the way you like.

Just search for a Windows-like wallpaper, and you have a Windows-like experience!

[ATTACH=CONFIG]255841[/ATTACH]

---

### Post by incurablegeek on 2014-08-26
[CENTER][SIZE=6][COLOR=#0000ff]Thank you so Very Much!
[SIZE=4][/SIZE]
[/COLOR][/SIZE][/CENTER]
[SIZE=6][SIZE=4][COLOR=#0000ff][/COLOR][COLOR=#0000ff][/COLOR]I just wanted all of you folks to know that I don't just "hit and run" on the Ubuntu forum. I have copy/pasted everything you suggested and am following up now. 

In short, you effort has not been wasted. You have really helped me greatly. What a wonderful forum![/SIZE][/SIZE]

---

### Post by fballem on 2014-08-26
There are a number of different desktop GUIs that you can use with Ubuntu. In addition, you can do further customisations for the desktop that you select. In the screenshot below, I selected one of the standard ubuntu backgrounds, faience theme and ubuntu icons. It took me a short while to get used to the slightly MAC interface, but I have found Unity to be responsive and very easy to work with - even for someone coming from Windows 7 (like me). If your hardware supports it, I would recommend that you start with this for a few days. This page [https://wiki.ubuntu.com/fballem/Software%2014.04](https://wiki.ubuntu.com/fballem/Software%2014.04) provides information about additional software that you might want to try. I have two 24" monitors, so clearly multiple monitors are easily supported.

I hope this helps,

---

### Post by Jonathan Precise on 2014-08-27
> **incurablegeek said:**
> [CENTER][SIZE=6][COLOR=#0000ff]Thank you so Very Much!
[SIZE=4][/SIZE]
[/COLOR][/SIZE][/CENTER]
[SIZE=6][SIZE=4][COLOR=#0000ff][/COLOR][COLOR=#0000ff][/COLOR]I just wanted all of you folks to know that I don't just "hit and run" on the Ubuntu forum. I have copy/pasted everything you suggested and am following up now. 

In short, you effort has not been wasted. You have really helped me greatly. What a wonderful forum![/SIZE][/SIZE]

Glad to have helped!

@fballem: Thanks for the URL! ):P Found it useful.

---

### Post by J Tinsby on 2014-09-10
Love the wallpaper in your screen shot. Must I have the Docky Dock DE to get it or is it a PPA somewhere? Did some searches but no joy.... Yes I wish my Unity looked like  your Win 7 emulation! I'd be afraid to add Docky to it for fear of not being able to go back to what's working for me.

Tnx

---

### Post by incurablegeek on 2014-09-10
@J Tinsby

> Love the wallpaper in your screen shot.
Not quite sure how to respond, assuming I could be of any help. ;) 

Whose screenshot are you referring to? If you are talking about Fences in mine, there is a Fences program for Ubuntu. And Fences I highly recommend - at least the Windows version.

Hope that helps.

---

### Post by J Tinsby on 2014-09-11
> **mooreted said:**
> I use Xubuntu with the Docky dock. It looks a  lot like Windows 7.

Wow, Flickr code is confusing. Finally got it:

[[IMG]https://farm6.staticflickr.com/5567/14841015450_fc2a1e4233.jpg[/IMG]]("https://flic.kr/p/oBs5QJ")[Xubuntu_Docky]("https://flic.kr/p/oBs5QJ")

Ted,

Will that docky dock work in Ubuntu without botching it up so I can't go back to Unity?

RE: That wallpaper...? Part of the DE or is there a separate set of files for just the images?

Thanks,

J T

---

### Post by J Tinsby on 2014-09-11
> **incurablegeek said:**
> @J Tinsby


Not quite sure how to respond, assuming I could be of any help. ;) 



Sorry I was referring to Post #8, inadvertently didn't use the correct choice to quote.

J T

---

### Post by JKyleOKC on 2014-09-11
> **incurablegeek said:**
> Now I shall fully reveal my ignorance here, so please feel free to laugh. I quite honestly don't mind, as long as I learn in the process.

My understanding of Ubuntu is:

1) More hardware and software (programs) are **made for Ubuntu** than for any other Linux distro.

2) **Ubuntu is the Linux engine** - on top of which different GUI's (desktop layouts) can be overlaid. 

3) I have read Gnome 3, for example, is easier to navigate and more glitch-free (whatever that means) than Ubuntu Unity - but **Gnome is slow to implement Ubuntu updates**.

I guess the big question I am asking is when I settle upon Ubuntu, which I definitely will do, can I modify/exchange the desktop GUI so it is faster and more efficient for my work environment?I'm coming into this thread a bit late; just discovered it. I don't see that anyone has answered these three questions, though. And while all three are close to correct, the rather minor errors in your assumptions can lead to not-so-minor problems down the way.

I'll start with number 2: "Linux" itself is the underlying engine that controls everything else. Back in the beginning, we geeks installed it plus the necessary development tools, then rolled our own utilities to be able to edit files, connect to networks, and so on. Before long people began to assemble groups of such tools, and these groups became known as **distributions**. One of the first was known as *Slackware*. One of the best known was *Red Hat*. Eventually one called *Debian* came into existence. Each of these was different, and each has had its promoters. As time passed, faults were found with each of the older distributions, and "derivatives" were developed, based on an existing distribution but modified to some degree to correct such faults or to introduce new features.

While this was happening, developers came up with ways to simplify installation of software, which became known as packages. A software package is simply a file that contains not only a piece of software, but all the information needed to install it into your system. Red Hat developed something called the **R**ed Hat **P**ackage **M**anager, which puts its packages into RPM files. Debian created a different approach with its **D**ebian Pac**k**a**g**e that calls its files DEB files and uses a program called *dpkg* to manage them.

Ubuntu is a derivative of Debian, which means that most if not all of the software available in DEB files for Debian and its other derivatives can be installed into Ubuntu systems. Mint, by the way, began as a derivative of Ubuntu. The other *buntu flavors all share the basic UIbuntu structure and files, but may have different utilities and definitely do have different desktop appearances.

Now to question 1. It's not quite true that Ubuntu has more programs available than any other distribution. Debian itself claims that distinction, with more than 14,000 programs in its repositories. However this is a rather minor point since almost no one ever uses more than a small fraction of the programs available.

And finally, question 3: The statement is actually reversed. Ubuntu updates usually lag behind "upstream" material such as Gnome. One of the major differences between Debian (and many others) and ubuntu deals with the schedeuling of updates. Debian has no specific schedule for doing updates; they claim that software is released "when it's ready" without regard to the calendar. Ubuntu, on the other hand, follows a strict schedule of issuing a new major release every six months, in April and October of each year. Once such a release is frozen (several months before the actual release date to allow time for testing and bug-fixing) nothing in it gets updated until the next release, except for security fixes.

The result is that Ubuntu always lags behind the upstream updates. The benefit is that we users know that no major change is going to happen to us unexpectedly. With a "rolling release" policy such as that of its parent Debian, updates can appear at any time.

As for the different desktops, yes, just about any window manager or development environment can be overlaid onto any flavor of *buntu systems. My own preference is for Xubuntu, which I originally configured to look much like the Win98SE systems from which I migrated back in 2007 or so but over the years have tuned to match my own preferred way to work. I find it much easier to tweak into shape than any of the other flavors, or any of the other distributions with which I have experimented.

Hope this helps get your feet on the ground with making the switch. I think you'll find it well worth while -- I know that I did!

---

### Post by J Tinsby on 2014-09-12
> **Jonathan Precise said:**
> I have used avant-window-navigator for the dock. To disable the MAC-like look/panels, disable Unity in CCSM. (and add [FONT=Courier New]sleep 3; initctl --user stop unity-panel-service[/FONT] to your start-up apps)

Once installed, go to AWN settings, and customize the way you like.

Just search for a Windows-like wallpaper, and you have a Windows-like experience! 

Jonathan,

Is the AWN part of Docky? If I use Synaptic and enter AWN it comes up with only 'Docky" as a choice. But the post below your shows a different icon layout in Docky on the desktop bottom. Is AWN a choice included in Docky? And when I install it can I safely go back to Unity if I don't care for AWN or whatever?

Thanks,

J T

---

### Post by JeQhdMD on 2014-09-12
NOTE:  be very careful with major desktop modifications - - -  **unless you know exactly what you're doing**.   I would suggest waiting for a few months before making these kind of changes to any Linux default desktop.   Ongoing routine system updates may not work and even totally hose your system. 

Minor updates or changes are a different matter (such things as new wallpapers, themes, fonts, etc. _which are part of the included settings manager_).

  A word to the wise.

---

### Post by J Tinsby on 2014-09-15
> **JeQhdMD said:**
> NOTE:  be very careful with major desktop modifications - - -  **unless you know exactly what you're doing**.   I would suggest waiting for a few months before making these kind of changes to any Linux default desktop.   Ongoing routine system updates may not work and even totally hose your system. 

Minor updates or changes are a different matter 

Thanks for the warning, but it seems a bit disingenuous to have the various DE's available if in fact they are a 'time release" ticking time bomb, waiting for an update to destroy the OS.

Seems I tried the KDE DE and couldn't get it off the system so I just blew it all out and started over. No update involved, but the list of things that were to be removed was HUGE.

If I had a reliable way to back up the system that I knew would work every time, like Acronis does in Windoze, I'd try another DE and just restore the image of the original. But Deja Dupe doesn't make images it makes copies and won't format the partition to install an image. Acronis does recognize the EXT4 system but my friend has had mixed success using it in Linux. <sigh> He's always trying different things and rarely even has the sides on the box he uses! 

I am not about to try it right now: risk vs reward I guess.



J T

---

### Post by JKyleOKC on 2014-09-15
> **J Tinsby said:**
> If I had a reliable way to back up the system that I knew would work every time, like Acronis does in Windoze, I'd try another DE and just restore the image of the original. 

I am not about to try it right now: risk vs reward I guess.
You might look into *clonezilla*, which is in the repositories and can be downloaded as an ISO to create a live CD much like Acronis works in Windows.

I've not used it myself due to lack of external drives large enough to hold full images of my systems, but it seems to have a very good reputation.

---

### Post by J Tinsby on 2014-09-16
> **JKyleOKC said:**
> You might look into *clonezilla*, which is in the repositories and can be downloaded as an ISO to create a live CD much like Acronis works in Windows.

I've not used it myself due to lack of external drives large enough to hold full images of my systems, but it seems to have a very good reputation.

Hi Jim,

Thanks for the info, I have heard of Clonezilla but never tried it. That will be job 1 today! Only way to tell if it's going to work is to actually make a backup and then try it. It can be a bit scary but it's the only way to tell :D

J T

---

### Post by fballem on 2014-11-07
Hi,

You will get a lot of opinions - all of them valid for that user's circumstances. My suggestion would be to select the buntu flavour that seems appropriate to your workstation. Personally, I use Ubuntu 14.04 with very few changes. I have two monitors. The dock is in the standard position (on the left side of the left monitor). I changed the theme, and I changed the behaviour of the displays so that the application menus are in the title bar of the window as opposed to the global menu bar. It did not take too long to get used to it and I find it to be very efficient.

There is an article here that may be of interest: [http://lifehacker.com/five-best-linux-desktop-environments-1648022755](http://lifehacker.com/five-best-linux-desktop-environments-1648022755)

Hope this helps,

---

