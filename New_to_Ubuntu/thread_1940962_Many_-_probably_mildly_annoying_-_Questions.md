---
title: "Many - probably mildly annoying - Questions"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by ukchris on 2012-03-14
I apologise in advance for the basic (and lengthy) nature of these questions... I am a brand new ubuntu user who needs a little help getting started - and will no doubt need a whole load more when I get knee deep. : ]

I have removed Windows (bar a small recovery partition) and successfully installed Ubuntu 11.10 onto an old and spare laptop (Intel Core2 Duo CPU T7100 @ 1.80GHz / 1GB) with some help from the users on the beginners-team irc and a variety of already answered posts on this forum (thanks all : ] ).  

I've been using it now in it's box-fresh configuration now for a couple of days and it seems to function rather nicely (given the specs of the machine it is installed on) and with surprising pace.  

So far my experience has been limited: I can navigate around the desktop a little, I can browse the web happily in Firefox with no "excessive memory usage" warnings, I can write papers in LibreOffice and convert them back to Word to send them back to work, WINE has allowed me to run a couple of legacy Windows applications I don't want to replace or relearn and I have even changed my computer name and user ID using the terminal!  

All in all I am, so far, a happy bunny. : ]

However - yes, yes, there is always a but - I do have some questions and even some annoyances.  I hope the latter may be resolved when I understand the answers to my questions.  

I'm rambling now - it has been a long day - so I'll get to the long and short of it, the questions... sorry lots I'm afraid!

**Linux Concepts**

1) Reading around it seems there is a variety of flavours of Linux (distributions?), how similar are they in concept? Could a user of one switch to another and really only need to relearn user interfaces and quirks or is the command line stuff different too?

2) Am I correct in thinking that within ubuntu (and other linux based OS') the user interface/desktop environment is essentially "separate" to the OS itself?  I keep hearing gnome and unity, are these basically skins (or more advanced versions of that concept)?

3) Given the spec of my machine is ubuntu 11.10 and whatever desktop environment I have (stock, out of the box) the best combination?

4) When I use "sudo" in the command line interface I am asked to enter:

[sudo] password for "user id":

Does this mean if I am a user with an administrator account this account is essentially what seems to be referred to as the root account or is there another, in-built account?  If it is the latter, I presume the root password should be changed from it's default, how?  

5) I kind of understand that GRUB is the/a Linux bootloader and see the various options when I start up my machine (after the manufacturer splash screen).  Can I use this to load different variant versions of *buntu (or even *nix) on the same partition?

**Desktop Environment Customisation**

6) Is it possible to get rid of the home shortcuts in the dash and replace them with my own to applications that I want to be able to access quickly?  I'd prefer an uncluttered desktop environment and hiding all but really heavily used applications in the dash rather than the launcher would work for me.  

7) Is it possible to have multiple launchers?

8) With reference to the Linux Concepts questions above, what are the options for user interfaces on ubuntu, I keep hearing people say gnome and Unity, what are these and are there more? 

9) Where multiple windows of an application are already open, is it possible to display the scaled down image of all open windows as the default behavior of the relevant button in the launcher?   This would be preferable (to me) to having to either click on the small markers or switch to the application (from another, different application) and then click the button again.  

[B]Remote Desktop Connections

[/B]10) I log into a machine at work using windows remote desktop and putty.  Could I do the same using Linux?  Our IT guys aren't very Linux aware (or at least not openly : ] ) so I'd like to go to them armed with some knowledge at least!

Anyway, apologies for the lengthy post and basic questions.  I really like the OS so far and would really like to continue using it, so I want to fully understand the basics.

Thanks in advance to any replies to any of the questions. : ]

---

### Post by MG&amp;TL on 2012-03-14
Linux Concepts:

1) Linux distributions vary by their package manager (the thing which handles software installs, ubuntu uses APT), their appearance, and many other things, but generally the core commands are always present. 

2) Yes, the interface is completely separate, however some interfaces need different libraries to support their specific needs, such as icons or compositing.

3) You can run any and all of the desktop environments, have a play and see what suits.

4) [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

5) Not on the same partition, no, but yes, you can 'pick and mix' as much as you want. Typically, distributions will nicely partition themselves for you, and update the bootloader.

DE Customising)

6) Yes, right-click and then untick keep in launcher, or drag to the trash bin. You can then drag things from the dash to the launcher to keep them in the launcher.

7) Not as yet, no, but look at other DEs, or something to the tune of Docky or Cairo Dock.

8 ) There are two main ones-GNOME and KDE. Gnome currently uses Shell, an interface similiar to Unity, but different in its own way. Unity is based on the GNOME libraries. KDE uses a completely separate set of libraries, and looks completely different too. There's also Xfce, LXDE, and all sorts of weird and wonderful other ones. Ubuntu can run theoretically any of them, but it has in-built support for LXDE, KDE, Xfce, and Unity, in the forms of Lubuntu (LXDE), Xubuntu (Xfce), Ubuntu (Unity), and Kubuntu (KDE)-you can also easily install Shell through the software centre. All of ubuntu's supported environments can also be installed through the software centre.

A few notes and opinions-Unity is less configurable than any of the others, mostly I think because it's very new. All of the others, you can have floating launchers, auto-hiding launchers, whatever size icons you want, as many launchers as you care for...the choice is yours. Generally, the less a desktop environment gives you, the more you can configure it. 

9) I don't think so in Unity, but try one of the other DEs. Also, try Alt-Tab, and then the down key. That produces a similiar effect.

---

### Post by mikewhatever on 2012-03-14
Wow, dude! You are trying to bite off too much at once. Leave a little bit for tomorrow ..., and may be the day after.

---

### Post by Gone fishing on 2012-03-14
Good questions here's answers to the first 4:

1 Linux distributions are all fairly similar, the commands are more or less the same, the main differences would be how they deal with package management (installing apps) The most common systems being Debian distributions, Debian, Ubuntu, Mint etc. and rpm distributions, Red Hat, Cent, Opensuse etc. The Window managers vary with Gnomer and KDE being common Unity is unique (I think) to Ubuntu.

2. Yes the Window managers are seperate from the OS but they are more than skins they are more like kits for running the GUI, they are also found on non Linux UNIX OSes such as FreeBSD.

3 Sudo means super user do and gives the ordinary user super user or root privileges. The super user has complete control over the system. As this is not usually needed in the Ubuntu sudo system the admin user asks for these privileges when he needs them. 

4 Grub can load several different OSes including Windows but these would normally need to be on different partitions.

---

### Post by Paqman on 2012-03-14
> **ukchris said:**
> 
1) Reading around it seems there is a variety of flavours of Linux (distributions?), how similar are they in concept? Could a user of one switch to another and really only need to relearn user interfaces and quirks or is the command line stuff different too?


They're generally very similar. They're all the same under the skin (ie: they all use the Linux kernel), and most of the other components are the same too. The differences tend to be the choice of desktop environment, package manager, and default set of apps pre-installed. Each distro maintains it's own software repositories.

> 2) Am I correct in thinking that within ubuntu (and other linux based OS') the user interface/desktop environment is essentially "separate" to the OS itself?  I keep hearing gnome and unity, are these basically skins (or more advanced versions of that concept)?

Essentially yes. Linux is very modular. Windows and OS X each only ship with one unchangeable desktop environment. Linux allows you to change this, or to install several and choose which one to work in.

> 3) Given the spec of my machine is ubuntu 11.10 and whatever desktop environment I have (stock, out of the box) the best combination?

That's pretty subjective. If you're happy with the DE you're using, then you're happy. You are a bit short on RAM, so a light DE and lightweight apps might give better performance.

> 4) When I use "sudo" in the command line interface I am asked to enter:

[sudo] password for "user id":

Does this mean if I am a user with an administrator account this account is essentially what seems to be referred to as the root account or is there another, in-built account?  If it is the latter, I presume the root password should be changed from it's default, how?  

Using sudo isn't using the root account, it's temporarily allowing your own account to gain root's privileges. Subtle difference. The root account on Ubuntu is not used by default.

> 5) I kind of understand that GRUB is the/a Linux bootloader and see the various options when I start up my machine (after the manufacturer splash screen).  Can I use this to load different variant versions of *buntu (or even *nix) on the same partition?

Each OS would need it's own partition, but yes Grub can boot pretty much any OS you like.


> 6) Is it possible to get rid of the home shortcuts in the dash and replace them with my own to applications that I want to be able to access quickly?  I'd prefer an uncluttered desktop environment and hiding all but really heavily used applications in the dash rather than the launcher would work for me.  

Yes, right click on an icon to either remove or pin it to the dash.

> 7) Is it possible to have multiple launchers?

Do you mean multiple dashes? Not as far as I'm aware.

> 8) With reference to the Linux Concepts questions above, what are the options for user interfaces on ubuntu, I keep hearing people say gnome and Unity, what are these and are there more? 

Unity is a version of Gnome. There also exists the standard version of Gnome called Gnome Shell. Other desktop environments exist such as KDE, XFCE and LXDE.

A DE is an integrated graphical environment consisting of themes, toolkits of things like window decorations and often a default suite of apps. The best way to understand how it works is to install a different DE.

> 9) Where multiple windows of an application are already open, is it possible to display the scaled down image of all open windows as the default behavior of the relevant button in the launcher?   This would be preferable (to me) to having to either click on the small markers or switch to the application (from another, different application) and then click the button again. 

Not quite sure I follow you here. I just tend to use Alt-Tab to switch so I'm not sure what problem you're describing.

> [B]Remote Desktop Connections

[/B]10) I log into a machine at work using windows remote desktop and putty.  Could I do the same using Linux?  Our IT guys aren't very Linux aware (or at least not openly : ] ) so I'd like to go to them armed with some knowledge at least!

What sort of machine would you be trying to log into, and what privileges do you have on it?

---

### Post by PhilGil on 2012-03-14
3) You might want to give the XFCE or     LXDE desktop environments a try. They are targeted toward older,     lower-speced  machines. However, they have fewer features than the     Unity desktop.
 
4) When you enter a command using     &#8220;sudo,&#8221; your user account is temporarily elevated to     administrator status. Ubuntu is not set up by default with an     administrator (root, in Linux) account. Check the link [MG&TL]("http://ubuntuforums.org/member.php?u=1320682") posted     to learn more.

5) You can install another Distro     (or another version of Ubuntu) in a new partition. As part of the     process, GRUB will update so that the next time you reboot you will     be offered the option to load any of the installed OSes on your     computer.

10) Remmina supports RDP (Windows remote desktop) connections.
```
? sudo apt-get install remmina
```

---

### Post by cmcanulty on 2012-03-14
For a different DE though just install from synaptic log out and log in to whichever one you like no partitioning needed and your files , apps are all still there

---

### Post by mal1958 on 2012-03-14
> **ukchris said:**
> 
**Linux Concepts**

1) Reading around it seems there is a variety of flavours of Linux (distributions?), how similar are they in concept? Could a user of one switch to another and really only need to relearn user interfaces and quirks or is the command line stuff different too?


Many distros are geared for different tuype of uses.  Also, there is the different package handeling systems too.  Fedora is more of an enterprise base then a desktop base, some others can also fall into this trap.  Some come with only bare bones in the app sections, while others suffer bloat from trying to stuff in as much as possible without thinking of what is needed.  My personal opinion is that Ubuntu is the best of the Desktop varients and has just enough to make things work properly and swiftly.


> **ukchris said:**
> 
2) Am I correct in thinking that within ubuntu (and other linux based OS') the user interface/desktop environment is essentially "separate" to the OS itself?  I keep hearing gnome and unity, are these basically skins (or more advanced versions of that concept)?


  Yes, you are correct.  As for the Gnome and unity shells, they are simply different ways for Ubuntu to interact with you, the user.  I prefer the Gnome desktop, and others prefer the new Unity desktop.


> **ukchris said:**
> 
3) Given the spec of my machine is ubuntu 11.10 and whatever desktop environment I have (stock, out of the box) the best combination?


This is, I believe, personal preferences.  I have been told that my system should use one of the light versions of the Ubuntu.  I however, use the full Ubuntu 10.04 ver with the Gnome desktop and it runs fine.

> **ukchris said:**
> 
4) When I use "sudo" in the command line interface I am asked to enter:

[sudo] password for "user id":

Does this mean if I am a user with an administrator account this account is essentially what seems to be referred to as the root account or is there another, in-built account?  If it is the latter, I presume the root password should be changed from it's default, how?  


This stands for Super User.  Similar to Root.  This is used sometimes when you want to do something that will alter the system from the command line.  You should take extreme care with this, if you don't know what or where the item is coming from I would recomend that you double check.

> **ukchris said:**
> 
5) I kind of understand that GRUB is the/a Linux bootloader and see the various options when I start up my machine (after the manufacturer splash screen).  Can I use this to load different variant versions of *buntu (or even *nix) on the same partition?


You can load many different versions of Linux, as well as windows using grub.

> **ukchris said:**
> 
**Desktop Environment Customisation**

6) Is it possible to get rid of the home shortcuts in the dash and replace them with my own to applications that I want to be able to access quickly?  I'd prefer an uncluttered desktop environment and hiding all but really heavily used applications in the dash rather than the launcher would work for me.  


  If you are referring to the top bar which has Apps places and System  Or the Unity bar along the side, I would advise that you leave these alone.  Other, more knowlegable, folk here can help you with this.  


> **ukchris said:**
> 
7) Is it possible to have multiple launchers?


I believe so, as long at the launchers are named differently.

> **ukchris said:**
> 
8) With reference to the Linux Concepts questions above, what are the options for user interfaces on ubuntu, I keep hearing people say gnome and Unity, what are these and are there more? 



Gnome and unity are the two default ones for Ubuntu, while KDE is the default for Kubuntu.  You can get the Gnome desktop in the newer versions of Ubuntu by installing them.  Some here will know how.


> **ukchris said:**
> 
Anyway, apologies for the lengthy post and basic questions.  I really like the OS so far and would really like to continue using it, so I want to fully understand the basics.

Thanks in advance to any replies to any of the questions. : ]

  No apologies are needed.  You can't learn if you don't ask.  I just hope that I was some help here.  Your best bet in learning about Ubuntu is to look through the forums here and ask questions, just like you are doing.  Folks here will be more then happy to answer what they can, and maybe they can refer you to places to find out more.  Welcome to Ubuntu, and hope to see more posts from you.

Mike

---

### Post by alphacrucis2 on 2012-03-14
> **PhilGil said:**
> 3) You might want to give the XFCE or     LXDE desktop environments a try. They are targeted toward older,     lower-speced  machines. However, they have fewer features than the     Unity desktop.
 
4) When you enter a command using     “sudo,” your user account is temporarily elevated to     administrator status. Ubuntu is not set up by default with an     administrator (root, in Linux) account. Check the link [MG&TL]("http://ubuntuforums.org/member.php?u=1320682") posted     to learn more.

5) You can install another Distro     (or another version of Ubuntu) in a new partition. As part of the     process, GRUB will update so that the next time you reboot you will     be offered the option to load any of the installed OSes on your     computer.

10) Remmina supports RDP (Windows remote desktop) connections.
```
? sudo apt-get install remmina
```

+1 for remmina. A good RDP client.

---

### Post by ukchris on 2012-03-15
First of all, thanks for all the replies, plenty to chew on. 
 
> **mikewhatever said:**
> Wow, dude! You are trying to bite off too much at once. Leave a little bit for tomorrow ..., and may be the day after. 
 
:)
 
I know, I know but it's how I learn best. 
 
> **MG&TL said:**
> 1) Linux distributions vary by their package manager (the thing which handles software installs, ubuntu uses APT), their appearance, and many other things, but generally the core commands are always present.  
 
> **Gone fishing said:**
> 1 Linux distributions are all fairly similar, the commands are more or less the same, the main differences would be how they deal with package management (installing apps) The most common systems being Debian distributions, Debian, Ubuntu, Mint etc. and rpm distributions, Red Hat, Cent, Opensuse etc. The Window managers vary with Gnomer and KDE being common Unity is unique (I think) to Ubuntu. 
 
> **Paqman said:**
> They're generally very similar. They're all the same under the skin (ie: they all use the Linux kernel), and most of the other components are the same too. The differences tend to be the choice of desktop environment, package manager, and default set of apps pre-installed. Each distro maintains it's own software repositories. 
 
> **mal1958 said:**
> Many distros are geared for different tuype of uses. Also, there is the different package handeling systems too. Fedora is more of an enterprise base then a desktop base, some others can also fall into this trap. Some come with only bare bones in the app sections, while others suffer bloat from trying to stuff in as much as possible without thinking of what is needed. My personal opinion is that Ubuntu is the best of the Desktop varients and has just enough to make things work properly and swiftly. 
 
That's all good to know.  I intend to stay with ubuntu for the foreseeable future but it is good know that a change won't mean a whole chunk of wasted learning. 
 
Does anyone know of any good, concise, current lists of distributions ideally with some discussion of pros and cons?  All the results I looked at from Google were from pre-2010. 
 
I was reading the manual page on [AptGet]("https://help.ubuntu.com/community/AptGet/Howto") and the whole package manager thing makes a lot of sense.  I like the idea that it knows the relevant dependencies of a given package and can install these as well with an additional command.  I presume that these commands (apt-get install and apt-get build-dep) are basically what are run when I install something via the software centre?   
 
On a related note and as an aside, are these dependencies relative to your system setup (i.e. does it take into account your system itself and already installed applications) and decided on the fly at the point of install? 
 
> **MG&TL said:**
> 2) Yes, the interface is completely separate, however some interfaces need different libraries to support their specific needs, such as icons or compositing. 
 
> **Gone fishing said:**
> 2. Yes the Window managers are seperate from the OS but they are more than skins they are more like kits for running the GUI, they are also found on non Linux UNIX OSes such as FreeBSD. 
 
> **Paqman said:**
> Essentially yes. Linux is very modular. Windows and OS X each only ship with one unchangeable desktop environment. Linux allows you to change this, or to install several and choose which one to work in. 
 
> **mal1958 said:**
> Yes, you are correct. As for the Gnome and unity shells, they are simply different ways for Ubuntu to interact with you, the user. I prefer the Gnome desktop, and others prefer the new Unity desktop. 
 
Right, so I can mix and match to an extent by the sounds of it.  What is the official term for each part of the system, operating system (ubuntu) and windows manager or desktop environment (Unity)? It helps to know the right terms to get more focused google results.  Presumably there are limitations to this mixing and matching (the libraries mentioned by MG&TL), is there any existing list of compatible/well suited "sets"?  Can advanced users combine libraries to suit different environments if required? 
 
Looking at the "General system information" tab in Sysinfo there is a flag stating GNOME 2.32.1 (Ubuntu 2011-04-14) does this mean I am running Gnome as a desktop environment or is Unity something that runs on top of Gnome? 
 
> **MG&TL said:**
> 3) You can run any and all of the desktop environments, have a play and see what suits. 
 
> **Paqman said:**
> That's pretty subjective. If you're happy with the DE you're using, then you're happy. You are a bit short on RAM, so a light DE and lightweight apps might give better performance. 
 
> **PhilGil said:**
> 3) You might want to give the XFCE or LXDE desktop environments a try. They are targeted toward older, lower-speced machines. However, they have fewer features than the Unity desktop. 
 
> **mal1958 said:**
> This is, I believe, personal preferences. I have been told that my system should use one of the light versions of the Ubuntu. I however, use the full Ubuntu 10.04 ver with the Gnome desktop and it runs fine. 
 
So really it's a see what feels right and use that by the sounds of it.  Using the setup I currently have everything runs a lot smoother than it did on the same machine running XP so I am currently happy.  Perhaps I will stick with this for now and then try and lighter weight DE and see if I miss any features or really like/notice the extra speed. 
 
> **cmcanulty said:**
> For a different DE though just install from synaptic log out and log in to whichever one you like no partitioning needed and your files , apps are all still there 
 
This is a useful tip, it makes changing desktop environments sounds relatively straightforward, thanks.   When I try any changes I will come back to this for more details as the Synaptic Packet Manager looks a little complex for now. : ] 
 
> **MG&TL said:**
> 4) [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)  
 
> **Gone fishing said:**
> 4 Sudo means super user do and gives the ordinary user super user or root privileges. The super user has complete control over the system. As this is not usually needed in the Ubuntu sudo system the admin user asks for these privileges when he needs them. 
 
> **Paqman said:**
> Using sudo isn't using the root account, it's temporarily allowing your own account to gain root's privileges. Subtle difference. The root account on Ubuntu is not used by default. 
 
> **PhilGil said:**
> 4) When you enter a command using &#8220;sudo,&#8221; your user account is temporarily elevated to administrator status. Ubuntu is not set up by default with an administrator (root, in Linux) account. Check the link MG&TL posted to learn more. 
 
> **mal1958 said:**
> This stands for Super User. Similar to Root. This is used sometimes when you want to do something that will alter the system from the command line. You should take extreme care with this, if you don't know what or where the item is coming from I would recomend that you double check. 
 
I have just read through the link provided by MG&TL, along with your answers, and it/they explained a lot.  On a home machine do you tend to use an admin account as your own or switch accounts for any admin/insallation required?  The forced password entry when any function tries to run as a super user should keep me on my toes and I assume also helps stop any casual system intruder (i.e. getting access to an unlocked physical desktop isn't enough to cause any fundamental harm). 
 
> **MG&TL said:**
> 5) Not on the same partition, no, but yes, you can 'pick and mix' as much as you want. Typically, distributions will nicely partition themselves for you, and update the bootloader. 
 
> **Gone fishing said:**
> 5 Grub can load several different OSes including Windows but these would normally need to be on different partitions. 
 
> **Paqman said:**
> Each OS would need it's own partition, but yes Grub can boot pretty much any OS you like. 
 
> **PhilGil said:**
> 5) You can install another Distro (or another version of Ubuntu) in a new partition. As part of the process, GRUB will update so that the next time you reboot you will be offered the option to load any of the installed OSes on your computer. 
 
> **mal1958 said:**
> You can load many different versions of Linux, as well as windows using grub. 
 
Excellent stuff.  I want to try to avoid using multiple partitions as I have limited HD space but if I wanted to temporarily try a different distro/build could I partition off a small area and then when I am done with it recombine it with the main Linux partition? Or is it always going to be a separate "drive" once I have partitioned it? 
 
> **mal1958 said:**
> If you are referring to the top bar which has Apps places and System Or the Unity bar along the side, I would advise that you leave these alone. Other, more knowledgeable, folk here can help you with this. 
 
I'm talking about the launcher bar on the left, the pop-out one.  I quite like the top bar, it is very neat and reminds me of an Android phone.   
 
> **MG&TL said:**
> 6) Yes, right-click and then untick keep in launcher, or drag to the trash bin. You can then drag things from the dash to the launcher to keep them in the launcher. 
 
> **Paqman said:**
> Yes, right click on an icon to either remove or pin it to the dash. 
 
For clarity when I mentioned the dash I mean: 
 
[IMG]http://i39.tinypic.com/23kdmxi.png[/IMG]
 
And when I mention the launcher I mean: 
 
[IMG]http://i44.tinypic.com/9bgj90.png[/IMG]
 
I seem to be able to add programs easily to the launcher but can't find a way to customise the dash? 
 
> **Paqman said:**
> Do you mean multiple dashes? Not as far as I'm aware. 
 
Multiple pop out launchers, like the one on the left of the screen.   
 
> **MG&TL said:**
> 7) Not as yet, no, but look at other DEs, or something to the tune of Docky or Cairo Dock. 
 
I am going to go and search for these on Google now. 
 
> **mal1958 said:**
> I believe so, as long at the launchers are named differently. 
 
I can't find a way in the GUI to do this, are there some background configuration files that need amendment? 
 
> **MG&TL said:**
> 8 ) There are two main ones-GNOME and KDE. Gnome currently uses Shell, an interface similiar to Unity, but different in its own way. Unity is based on the GNOME libraries. KDE uses a completely separate set of libraries, and looks completely different too. There's also Xfce, LXDE, and all sorts of weird and wonderful other ones. Ubuntu can run theoretically any of them, but it has in-built support for LXDE, KDE, Xfce, and Unity, in the forms of Lubuntu (LXDE), Xubuntu (Xfce), Ubuntu (Unity), and Kubuntu (KDE)-you can also easily install Shell through the software centre. All of ubuntu's supported environments can also be installed through the software centre. 
 
A few notes and opinions-Unity is less configurable than any of the others, mostly I think because it's very new. All of the others, you can have floating launchers, auto-hiding launchers, whatever size icons you want, as many launchers as you care for...the choice is yours. Generally, the less a desktop environment gives you, the more you can configure it. 
 
> **Paqman said:**
> Unity is a version of Gnome. There also exists the standard version of Gnome called Gnome Shell. Other desktop environments exist such as KDE, XFCE and LXDE. 
 
A DE is an integrated graphical environment consisting of themes, toolkits of things like window decorations and often a default suite of apps. The best way to understand how it works is to install a different DE. 
 
> **mal1958 said:**
> Gnome and unity are the two default ones for Ubuntu, while KDE is the default for Kubuntu. You can get the Gnome desktop in the newer versions of Ubuntu by installing them. Some here will know how. 
 
Thanks for that it clarifies a lot. 
 
I'm going to need to search around for advice on installing a new desktop environment when I try any changes as it sounds simple but I suspect it won't be the first time I try it. :)
 
> **MG&TL said:**
> 9) I don't think so in Unity, but try one of the other DEs. Also, try Alt-Tab, and then the down key. That produces a similiar effect. 
 
> **Paqman said:**
> Not quite sure I follow you here. I just tend to use Alt-Tab to switch so I'm not sure what problem you're describing. 
 
Pictorial: 
So here I am browsing the Ubuntu Software Centre: 

[IMG]http://i41.tinypic.com/2la80ag.png[/IMG]
 
And I want to switch to Firefox so I click on the button in the launcher and get:

[IMG]http://i40.tinypic.com/2199sns.png[/IMG]

Now if I click the Firefox button on the launcher AGAIN I get:

[IMG]http://i41.tinypic.com/4md5v.png[/IMG]

Which is what I would prefer to show on the first click.

Like you guys I tend to use alt-tab (in Windows) so this is a habit I still have in ubuntu however the users who I will have to convince to switch from Windows are my family and they are all predominantly pointers and clickers and would definitely prefer the second view.  

> **Paqman said:**
> What sort of machine would you be trying to log into, and what privileges do you have on it? 
 
> **PhilGil said:**
> 10) Remmina supports RDP (Windows remote desktop) connections. 
 
```
? sudo apt-get install remmina
``` 
 
> **alphacrucis2 said:**
> +1 for remmina. A good RDP client.  
 
I am trying to work out if it will be possible to login into my work desktop.  This is a Windows machine running XP.  Currently I log into using Putty, a mobile one time password client and an ssh key.  Essentially I'd like to replicate the same setup but login from my shiny ubuntu machine (if only as a proof of concept).  In terms of privileges on the target machine I am a basic user (but my user profile and client machine are in a remote desktop group of some sort I believe). 
 
> **mal1958 said:**
> No apologies are needed. You can't learn if you don't ask. I just hope that I was some help here. Your best bet in learning about Ubuntu is to look through the forums here and ask questions, just like you are doing. Folks here will be more then happy to answer what they can, and maybe they can refer you to places to find out more. Welcome to Ubuntu, and hope to see more posts from you. 
 
Thanks Mike, I just know what it can be like as an experienced user faced with the same questions daily!  
 
Anyway, thanks to all of you for your advice and patience so far.  It feels like a very experienced and welcoming community here.  Good stuff. :D

---

### Post by 2F4U on 2012-03-15
> Does anyone know of any good, concise, current lists of distributions  ideally with some discussion of pros and cons?  All the results I looked  at from Google were from pre-2010. 

The most comprehensive list of Linux distributions I know is on Distrowatch

[http://distrowatch.com/](http://distrowatch.com/)

For many distributions you will also find links to reviews.

---

### Post by tbhatia4 on 2012-03-15
> **mikewhatever said:**
> Wow, dude! You are trying to bite off too much at once. Leave a little bit for tomorrow ..., and may be the day after.

lol 

he's curious at start

---

### Post by Lisiano on 2012-03-15
> **ukchris said:**
> Does anyone know of any good, concise, current lists of distributions ideally with some discussion of pros and cons?  All the results I looked at from Google were from pre-2010.
[http://distrowatch.com](http://distrowatch.com) is a good place as well as Wikipedia
[http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions](http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions)
[http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions)
> **ukchris said:**
> On a related note and as an aside, are these dependencies relative to your system setup (i.e. does it take into account your system itself and already installed applications) and decided on the fly at the point of install?
The second you tell Apt to install something, Apt "locks the system" (To prevent any modifications while it's doing it's job) and checks what you already have installed, what you want to install and what needs to be installed so you can install what you want.
Let's say there is a application called Fun, you need to install it but it's dependecies (Or requirments) are Time, Space, Knowledge, say your system already has Time and Space installed, Apt will then just download Knowledge and Fun, install Knowledge then proceed to install Fun.
> **ukchris said:**
> Right, so I can mix and match to an extent by the sounds of it.  What is the official term for each part of the system, operating system (ubuntu) and windows manager or desktop environment (Unity)? It helps to know the right terms to get more focused google results.
[LIST]
[*]Linux kernel - heart/core of any Linux install
[*]Ubuntu - OS (As a whole)
[*]Desktop environment - Unity, Gnome, KDE, LXDE, XFCE, etc. They provide the libraries so your GUI applications can actually be Graphical user interfaces.
[*]Window manager - This just manages your windows, there are default window managers per each DE but are mostly interchangeble, a popular one being Compiz. They let you move around your windows, click on them, type in them, have fun with them.
[*]Kernel modules - These are "addons" to your kernel, they provide drivers and support for different filesystems.
[*]Other software - Just that, other software.
[/LIST] I might've missed something but nobodys perfect.
> **ukchris said:**
> Presumably there are limitations to this mixing and matching (the libraries mentioned by MG&TL), is there any existing list of compatible/well suited "sets"?  Can advanced users combine libraries to suit different environments if required?
There is no limit on what DEs you can have installed, Apt will take care of the dependencies, so even if you install a KDE app (For example Kopete, an instant messenger, like Empathy or Pidgin) then Apt will automatically install everything needed to run KDE apps, while not installing the whole DE, it will download a "Basic KDE".
> **ukchris said:**
> Looking at the "General system information" tab in Sysinfo there is a flag stating GNOME 2.32.1 (Ubuntu 2011-04-14) does this mean I am running Gnome as a desktop environment or is Unity something that runs on top of Gnome?Unity is based on Gnome, you can say it runs on top of GTK which Gnome also runs on top of. GTK is the libraries that make Gnome what it is. QT for KDE. GTK for XFCE. I think it's GTK for LXDE but I don't remember.
> **ukchris said:**
> On a home machine do you tend to use an admin account as your own or switch accounts for any admin/insallation required?  The forced password entry when any function tries to run as a super user should keep me on my toes and I assume also helps stop any casual system intruder (i.e. getting access to an unlocked physical desktop isn't enough to cause any fundamental harm).
A "Admin" user on a Linux system has no more privileges than any other user, except one. An "Admin" can elevate a programs privileges up to Root, it's like NT AUTHORITY/NT SYSTEM on Windows, so even higher than Administrator. By default, sudo will timeout in 5 minutes. A "Evil" user can still cause harm though, while not having any power over the core system, he/she still has power over your files, so if you leave your PC on, don't forget to lock it (Ctrl+Alt+L or in the top right corner).
> **ukchris said:**
> Excellent stuff.  I want to try to avoid using multiple partitions as I have limited HD space but if I wanted to temporarily try a different distro/build could I partition off a small area and then when I am done with it recombine it with the main Linux partition? Or is it always going to be a separate "drive" once I have partitioned it?
You can later recombine it, but I wouldn't advise trying it untill you are more than just knee deep with Linux, more like hip deep.
> **ukchris said:**
> I'm talking about the launcher bar on the left, the pop-out one.  I quite like the top bar, it is very neat and reminds me of an Android phone.
In the rare times I boot Windows, I also have the launcher on top, just makes more sense for me nowadays.> **ukchris said:**
> I seem to be able to add programs easily to the launcher but can't find a way to customise the dash?When you open Dash, you can start typing to search for an application or click the icon on the lower part of Dash which looks like a ruler, pen and pencil, from there is a text button - "Filter Results", just press it and you can access the app categories.
> **ukchris said:**
> I'm going to need to search around for advice on installing a new desktop environment when I try any changes as it sounds simple but I suspect it won't be the first time I try it. :)Easiest way is to install ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or lubuntu-desktop. Installing one of those will also install everything that comes with a default install of Ubuntu, Kubuntu, Xubuntu and Lubuntu respectively.
> **ukchris said:**
> Like you guys I tend to use alt-tab (in Windows) so this is a habit I still have in ubuntu however the users who I will have to convince to switch from Windows are my family and they are all predominantly pointers and clickers and would definitely prefer the second view.
Not that I'm aware of, but it should be easy to teach them to "double-click" the icon.
> **ukchris said:**
> I am trying to work out if it will be possible to login into my work desktop.  This is a Windows machine running XP.  Currently I log into using Putty, a mobile one time password client and an ssh key.  Essentially I'd like to replicate the same setup but login from my shiny ubuntu machine (if only as a proof of concept).  In terms of privileges on the target machine I am a basic user (but my user profile and client machine are in a remote desktop group of some sort I believe).I'm safe to assume you are using SSH? Does it say SSH when you login using Putty? If so, then you can use SSH that is built-in to Ubuntu. The SSH key will need to be placed in ~/.ssh/ . Folders with a dot are not usually visible, you can either display hidden folders or press Ctrl+L and type in ~/.ssh when you open Nautilus (File Manager), then enter. After you do that, you need to open a Terminal (Ctrl+Alt+T) and type in the following```
ssh username@42.42.42.42
```username being your username on your WORK machine (No need to type in username@ if you have the same login on your home machine) and 42.42.42.42 being the IP you need to connect to or the DNS. After you did that, you should be loged in. Note, I don't what exactly you do or did in Putty to get a desktop so I can't tell you what you need to do now to get one in Ubuntu.
> **ukchris said:**
> Anyway, thanks to all of you for your advice and patience so far.  It feels like a very experienced and welcoming community here.  Good stuff. :D Don't get tricked. We are all very evil hackers just dying to get into your machine, steal your credit card numbers, your social security ID, your wife, your kids and your cat. _Especially_ your cat. Jokes aside, welcome to Ubuntu and hope you enjoy your time with it.

---

### Post by PhilGil on 2012-03-15
> **ukchris said:**
> 
I was reading the manual page on AptGet and the whole package manager thing makes a lot of sense. I like the idea that it knows the relevant dependencies of a given package and can install these as well with an additional command. I presume that these commands (apt-get install and apt-get build-dep) are basically what are run when I install something via the software centre?
The Software Center is a GUI that uses apt behind the scenes for installing packages. To install a package from the command line you use
"sudo apt-get install PackageName". 

> **ukchris said:**
> On a related note and as an aside, are these dependencies relative to your system setup (i.e. does it take into account your system itself and already installed applications) and decided on the fly at the point of install?
Yes. Library files are typically shared amongst all applications that are dependent on them. If you stick to installing packages from repositories built for your version/distribution you're very unlikely to have dependency problems.

> **ukchris said:**
> Right, so I can mix and match to an extent by the sounds of it. What is the official term for each part of the system, operating system (Ubuntu) and windows manager or desktop environment (Unity)? It helps to know the right terms to get more focused google results. Presumably there are limitations to this mixing and matching (the libraries mentioned by MG&TL), is there any existing list of compatible/well suited "sets"? Can advanced users combine libraries to suit different environments if required?
Linux is extremely modular. Experienced users can mix and match components at will. For a beginner, it's better to stick to a fully configured distribution like Ubuntu.

A window manager typically handles the placement of windows on your screen, the window sizing, minimizing and maximizing, draws window borders and title bars and handles drive mounting and unmounting. A desktop environment is composed of a window manager and a selection of gui tools for working with your machine (such as a configuration manager and a file manager). It often includes a selection of higher level software, as well.

> **ukchris said:**
> I have just read through the link provided by MG&TL, along with your answers, and it/they explained a lot. On a home machine do you tend to use an admin account as your own or switch accounts for any admin/insallation required? The forced password entry when any function tries to run as a super user should keep me on my toes and I assume also helps stop any casual system intruder (i.e. getting access to an unlocked physical desktop isn't enough to cause any fundamental harm).
Most of us would strongly discourage from using an admin account as your daily driver. One of the pillars of Linux security is using the lowest number of permissions you need to accomplish your task. This is why Ubuntu doesn't enable the root account by default.

---

### Post by ukchris on 2012-03-15
Thanks folks. :)

And sorry for butchering posts and the order of posts below to try and make sense of it all.  :oops:

> **2F4U said:**
> The most comprehensive list of Linux distributions I know is on Distrowatch

[http://distrowatch.com/](http://distrowatch.com/)

For many distributions you will also find links to reviews.

> **Lisiano said:**
> [http://distrowatch.com]("http://distrowatch.com/") is a good place as well as Wikipedia
[http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions](http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions)
[http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions)

Thanks for those sites, just spent some time looking through the Ubuntu variants on Distrowatch.  I don't dare look beyond Ubuntu for now else this machine won't know what happened to it. Poor old dear.  And that's not to mention my brain.  :)

I think I will definitely be trying the light weight variants on there (Xu and Lubuntu) though.  This machine is pretty marginal in terms of general specs but a relative monster in terms of the minimum requirement for Lubuntu.

> **tbhatia4 said:**
> lol 

he's curious at start

Like a cat, but not like the proverbial killed one... I hope. 

> **Lisiano said:**
> The second you tell Apt to install something,  Apt "locks the system" (To prevent any modifications while it's doing  it's job) and checks what you already have installed, what you want to  install and what needs to be installed so you can install what you want.

I like that, even more than I liked your poetic and very understandable example. :mrgreen:

> **PhilGil said:**
> The Software Center is a GUI that uses apt  behind the scenes for installing packages. To install a package from the  command line you use
 "sudo apt-get install PackageName". 
 
And is the Software Centre representative of all of the "official" ubuntu software repository? I mean, if someone mentions a particular official application or plugin or whatever, am likely to find it there or is this the purpose of the Synaptic Packet Manager?

> **PhilGil said:**
>    A window manager typically handles the placement of windows on your  screen, the window sizing, minimizing and maximizing, draws window  borders and title bars and handles drive mounting and unmounting. A  desktop environment is composed of a window manager and a selection of  gui tools for working with your machine (such as a configuration manager  and a file manager). It often includes a selection of higher level  software, as well.

 > **Lisiano said:**
> 
 
[LIST]
[*]Linux kernel - heart/core of any Linux install
[*]Ubuntu - OS (As a whole)
[*]Desktop  environment - Unity, Gnome, KDE, LXDE, XFCE, etc. They provide the  libraries so your GUI applications can actually be Graphical user  interfaces.
[*]Window manager - This just manages your windows,  there are default window managers per each DE but are mostly  interchangeble, a popular one being Compiz. They let you move around  your windows, click on them, type in them, have fun with them.
[*]Kernel modules - These are "addons" to your kernel, they provide drivers and support for different filesystems.
[*]Other software - Just that, other software.
[/LIST]
 Thanks for those definitions Phil and Lisiano, it's very helpful to  have the right terms, not least so I can ask better questions here. 
 

 I can find basic hardware details, kernel details, OS details and what I think are DE details in the System Information application.

 

 [IMG]http://i44.tinypic.com/ap6pj.png[/IMG]
 

 And I noticed a process running called Compiz in the System Monitor,  are there any other key details I need to know about my system  information that may be helpful in future troubleshooting?

 

 > **Lisiano said:**
> I might've missed something but nobodys perfect.

:)
 
> **PhilGil said:**
> Yes. Library files are typically shared amongst all applications that  are dependent on them. If you stick to installing packages from  repositories built for your version/distribution you're very unlikely to  have dependency problems.
 
I'll stick to the the relevant repository for now then. 

> **PhilGil said:**
> Linux is extremely modular. Experienced users  can mix and match components at will. For a beginner, it's better to  stick to a fully configured distribution like Ubuntu.
  
I am looking forward to being able to tailor my OS entirely to my liking, long way to go to get there though! 

> **Lisiano said:**
> There is no limit on what DEs you can have installed, Apt will take care  of the dependencies, so even if you install a KDE app (For example  Kopete, an instant messenger, like Empathy or Pidgin) then Apt will  automatically install everything needed to run KDE apps, while not  installing the whole DE, it will download a "Basic KDE".
 Unity is based on Gnome, you can say it runs on top of GTK which Gnome  also runs on top of. GTK is the libraries that make Gnome what it is. QT  for KDE. GTK for XFCE. I think it's GTK for LXDE but I don't remember.

So given that XFCE and LXDE (which are the light desktops for Xu and Lubuntu?) are based on essentially the same back end can I interchange these desktops environments without doing an OS install?  If so how? 

> **Lisiano said:**
> Easiest way is to install ubuntu-desktop, kubuntu-desktop,  xubuntu-desktop or lubuntu-desktop. Installing one of those will also  install everything that comes with a default install of Ubuntu, Kubuntu,  Xubuntu and Lubuntu respectively.
 
Is this basically what we are talking about above and if so are they the relevant package names (as such)? 

And if that's the case... how easy is that! Very nice.

> **Lisiano said:**
> A "Admin" user on a Linux system has no more privileges than any other  user, except one. An "Admin" can elevate a programs privileges up to  Root, it's like NT AUTHORITY/NT SYSTEM on Windows, so even higher than  Administrator. By default, sudo will timeout in 5 minutes. A "Evil" user  can still cause harm though, while not having any power over the core  system, he/she still has power over your files, so if you leave your PC  on, don't forget to lock it (Ctrl+Alt+L or in the top right corner).

> **PhilGil said:**
> Most of us would strongly discourage from using an admin account as your  daily driver. One of the pillars of Linux security is using the lowest  number of permissions you need to accomplish your task. This is why  Ubuntu doesn't enable the root account by default.

Eek, right as soon as I finish this post I shall go and create a regular user account!    

With regards to the timeout, does this mean if I say install a file and it asks for my password and I then install something else within five minutes I will not have to re-enter a password?  Is this timeout configurable (to be lower)?

> **Lisiano said:**
> You can later recombine it, but I wouldn't advise trying it untill you  are more than just knee deep with Linux, more like hip deep.

Advice noted. :D

I have 90ish GB in total to play with.  What would you recommend as far as an environment to test two OS at a time if I want one as the core "I am using this one regularly" OS and one as the "I am playing with this" OS?  Something like:


[LIST]
[*]1 x 66GB core OS partition with a 2GB swap &;
[*]1 x 20GB test OS partition with a 2GB swap.
[/LIST]
If so can that be achieved during a fresh install when I have already got an 86GB partition with a 5GB swap (which has never been used more than 2%)?  If I tried to install a test OS with the specs above, would the core OS partition automatically be resized?  

And on a related note, can a swap file be changed in size without a re-install?

> **Lisiano said:**
>  In the rare times I boot Windows, I also have the launcher on top, just  makes more sense for me nowadays.When you open Dash, you can start  typing to search for an application or click the icon on the lower part  of Dash which looks like a ruler, pen and pencil, from there is a text  button - "Filter Results", just press it and you can access the app  categories.

I'm getting used to it I think, it would be nice though to be able to lay up a number of apps of your own choosing from any category into a "my category", or "my tab".  

> **Lisiano said:**
> Not that I'm aware of, but it should be easy to teach them to "double-click" the icon.

I guess that's wanting one customisation too far.  But yes, you're right, I can just tell them to double click, the problem is though that this instruction needs to be combined with a second...  

"Double click if you are in another application, single click if you are already in the right application [with many windows]."

> **Lisiano said:**
> I'm safe to assume you are using SSH? Does it say SSH when you login  using Putty? If so, then you can use SSH that is built-in to Ubuntu. The  SSH key will need to be placed in ~/.ssh/ . Folders with a dot are not  usually visible, you can either display hidden folders or press Ctrl+L  and type in ~/.ssh when you open Nautilus (File Manager), then enter.  After you do that, you need to open a Terminal (Ctrl+Alt+T) and type in  the following```
ssh username@42.42.42.42
```username being your  username on your WORK machine (No need to type in username@ if you have  the same login on your home machine) and 42.42.42.42 being the IP you  need to connect to or the DNS. After you did that, you should be loged  in. Note, I don't what exactly you do or did in Putty to get a desktop  so I can't tell you what you need to do now to get one in Ubuntu.
 
Safe to assume that yes. 

Knowing that in can be done is a start.  I'll have a look through the setup on my Windows machine a little later and see how much syncs with what you wrote above.

> **Lisiano said:**
> Don't get tricked. We are all very evil hackers just dying to get into  your machine, steal your credit card numbers, your social security ID,  your wife, your kids and your cat. _Especially_ your cat. Jokes aside,  welcome to Ubuntu and hope you enjoy your time with it.

Excellent news, when can you pick up the cats then? :mrgreen:

Thanks again all.  Great and useful replies.  I've got a lot of learning to do but I feel on a little firmer ground now at least.

---

### Post by MG&amp;TL on 2012-03-15
Bit shorter than my other post, sorry. :P

About the 'spread' of windows for firefox, you can't do that specifically as far as I know, but try the Super+W key combination. You should be able to see all of your windows fanned out for you to pick.

Yes, package management is very cool, and one of the main reasons I choose Linux. Windows doesn't keep track of its  files very well, so often you get things 'clogged up'. However, with linux, almost every system file is accounted for by the package manager. Linking back to dependencies, "ubuntu-desktop" is a package that doesn't do anything in itself, but *depends on* multiple other packages., such as unity, gtk, and applications like LibreOffice and Thunderbird Mail.

Welcome to Ubuntu!

---

