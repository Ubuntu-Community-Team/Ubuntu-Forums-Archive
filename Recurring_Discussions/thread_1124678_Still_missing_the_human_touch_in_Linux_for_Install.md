---
title: "Still missing the human touch in Linux for Installing software"
date: 2009-04-13
forum: Recurring Discussions
---

### Post by eljopc on 2009-04-13
Some thoughts on Linux and what I'm missing to get the job done. Well maybe not missing wanting to have/see different. 

I'm pointing to the install of "new" software, packages and drivers. There are so much different ways to install under Linux and I think there should only be one. From within Linux but also from websites as a download.

Yes I'm a Windows user, not by choice but it was there first, understandable and there was one way of doing things. Look at the install of software, we got .exe and .MSI but all self extracting packages independent and simple and no strange extra code for extracting and installing.

Now back to Linux, non self extracting software and to much different install packages that need different unpack software and code.....

Debian, Ubuntu: APT
[root]# apt-get install packagename

Fedora, Red Hat: yum
[root]# yum install packagename

Mandriva: urpm
[root]# urpmi packagename

Tar Balls
[user]$ tar -xzvf filename.tar.gz

SUSE uses RPM

This is not for human beings, this is for Linux Power users. I train a lot of people on Windows but this should be one type of install package no strange code in a window to extract or install.

Is it so hard to make one package that extracts all software into Linux. I now get why manufacturers from hardware do not easily make software for Linux. Where there is a simple way to make it for Windows and Mac, for Linux every distro needs his own.

---

### Post by tom66 on 2009-04-13
You can download a .deb and install it, or you can use Synaptic. Both are possible on default Ubuntu installs.

Edit: Variety is the spice of life. Variety means that any security problem only affects a fraction of users. Limiting potential damage.

---

### Post by swoll1980 on 2009-04-13
I happen to think that Synaptic is by far the fastest,easiest, and most secure way to find, and install software on any os period.

---

### Post by Tibuda on 2009-04-13
Human beings opens the "Add/remove" item in the "Applications" menu. No apt-get/yum/whatever in the command line.

---

### Post by SunnyRabbiera on 2009-04-13
Personally I find using repositories easier then using .exe installers.
What you are suggesting has been suggested a million times already, using one kind of installer and one kind of installer interface.
But really Yum, Apt, and URPMI are very similar to eachother in terms of commandline and installer interface.
Its not that hard to understand each one, and personally I think its better then installing .exe with its next, next, I agree, enter code, next next, finish type installation.
And yes no one forces you to use commandline, one can easily use synaptic or gedebi.

---

### Post by mikewhatever on 2009-04-13
> **eljopc said:**
> 
Is it so hard to make one package that extracts all software into Linux. I now get why manufacturers from hardware do not easily make software for Linux. Where there is a simple way to make it for Windows and Mac, for Linux every distro needs his own.

Oh really?! What about Open Office, Skype and VirtualBox, just to name a few?

---

### Post by Mehall on 2009-04-13
> **SunnyRabbiera said:**
> Personally I find using repositories easier then using .exe installers.
What you are suggesting has been suggested a million times already, using one kind of installer and one kind of installer interface.
But really Yum, Apt, and URPMI are very similar to eachother in terms of commandline and installer interface.
Its not that hard to understand each one, and personally I think its better then installing .exe with its next, next, I agree, enter code, next next, finish type installation.

This.

And a lot of distros use Synaptic anyway.

If you're using an rpm based distro and want apt, you can install apt-rpm, so you have your apt interface there.

But as people said, those people you are talking about won't do it on the command line, unless following a tutorial, and then they should follow one for their distro. And even then, most tutorials tell you what to install, and just give the CLI version as an example.

---

### Post by Therion on 2009-04-13
> **eljopc said:**
> There are so much different ways to install under Linux and I think there should only be one. 

**Linux Attitude:**  Synaptic is a choice...  Yum is a choice...  Installing from source (e.g. from a "tarball") is a choice...  Choices, choices!!!

**Closed Source Attitude:** You **WILL **do it **THIS **way, every time.  Period.

---

### Post by Methuselah on 2009-04-13
If you see many options for a particular download choose the .deb if you're running ubuntu.

Better yet, use synaptic or add/remove programs.

Remember, no single entity controls all the different gnu-linux distributions so they use different installers for the same reason Windows and MacOS use different installers; they were developed independenty.

Just as you'd get the .exe for windows, get the .deb for ubuntu.

---

### Post by SunnyRabbiera on 2009-04-13
> **mikewhatever said:**
> Oh really?! What about Open Office, Skype and VirtualBox, just to name a few?

Indeed, and as time has passed some packages work universally almost, a .deb has become a .deb and a .rpm has become a .rpm as the distros over time have almost nullified the need for multiple types of .deb and .rpm installer.
The only reason you might see it around for certain apps is sometimes there is a speciffic fix needed for that version of linux...
But its gotten better.

---

### Post by C-{pR0F on 2009-04-13
> **SunnyRabbiera said:**
> Its not that hard to understand each one, and personally I think its better then installing .exe with its next, next, I agree, enter code, next next, finish type installation.

Totally agree with that

---

### Post by HermanAB on 2009-04-13
If you are **still** missing the human touch, send a message to [email]momshome@aeronetworks.ca[/email] or visit [http://momshome.aeronetworks.ca](http://momshome.aeronetworks.ca) and a **real** mom will answer you.  It is a service for people who don't have a mom to talk to - just starting up and experimental still.

There is a very brave, honest to goodness, real mom behind that!

---

### Post by eljopc on 2009-04-13
> **mikewhatever said:**
> Oh really?! What about Open Office, Skype and VirtualBox, just to name a few?

Thanks mike...

What I see here is Linux users defending Linux but thats not the issue here. I think Linus is great but not workable for the big world. 

I can take a Linux laptop to the first man on the street and he will first say that it looks nice. But now he wants to install a driver for his printer/scanner/webcam ... that is not in Linux but he has to download from the manufacturers site, he will never get it installed without a book with directions. 

How do we ever bring this to the big public if we won't listen to the non Linux users?

---

### Post by Tibuda on 2009-04-13
And there's nothing stopping a software company to create its own binary installer, just like Windows software.

---

### Post by SunnyRabbiera on 2009-04-13
> **eljopc said:**
> Thanks mike...

What I see here is Linux users defending Linux but thats not the issue here. I think Linus is great but not workable for the big world. 

I can take a Linux laptop to the first man on the street and he will first say that it looks nice. But now he wants to install a driver for his printer/scanner/webcam ... that is not in Linux but he has to download from the manufacturers site, he will never get it installed without a book with directions. 

How do we ever bring this to the big public if we won't listen to the non Linux users?

The real blame goes to those who make the webcams/scanners/printers/etc not linux.
Linux is not owned by a fortune 500 company like Apple or Microsoft, because its community based not company based.
Linux communities can only do so much, linux itself is more then ready for everyday use in my opinion as for the most part it is better then XP/Vista and OSX in terms of versatility and stability.
Actually truth be told Linux seems more hardware ready then Windows, most of the hardware I buy might have microsoft in mind but it doesnt stop it from working.
Like my keyboard and mouse, has the windows logo all over it as its a logitech...
But I plugged it in, and right away my mouse and keyboard work fine in linux.
In windows you are lucky if it picks up stuff without the installer CD, I have a joystick that needs drivers in windows that I need a CD for...
Linux picked it up right away.
But yes there are many devices that dont openly support linux, we dont have a crap load of money li8ke MS or Apple so its expected.

> **danielrmt said:**
> And there's nothing stopping a software company to create its own binary installer, just like Windows software.

Indeed, Linux has the same capacity as windows does, perhaps even moreso as the kernel is so diverse.
Its greed and ignorance that stops our progress.

---

### Post by hyperdude111 on 2009-04-13
.deb works a charm if you want a website with huge quantities of .deb's try "getdeb"

---

### Post by Tibuda on 2009-04-13
> **eljopc said:**
> How do we ever bring this to the big public if we won't listen to the non Linux users?
[http://ubuntuforums.org/showthread.php?t=58017](http://ubuntuforums.org/showthread.php?t=58017)

---

### Post by swoll1980 on 2009-04-13
> **eljopc said:**
> he will never get it installed without a book with directions. 

How do we ever bring this to the big public if we won't listen to the non Linux users?

What you don't understand is if free software really has to sacrifice it's principals to get get the "big public" on board, then the "big public" will have to sit this one out. Your problem is you think "Linux" is one big OS when in fact every Linux based distro is it's own independent OS.

---

### Post by Therion on 2009-04-13
> **danielrmt said:**
> 

[http://ubuntuforums.org/showthread.php?t=58017](http://ubuntuforums.org/showthread.php?t=58017)


The head of the nail... You just hit it. 

Squarely.

---

### Post by Icehuck on 2009-04-13
> **Therion said:**
> The head of the nail... You just hit it. 

Squarely.

Bingo

---

### Post by chris4585 on 2009-04-13
Sometimes I **REALLY** don't think people realize how easy it is... For example if you go to a website and download a .deb file and if you click on a .deb file, a window will pop up, click install, type in password, INSTALLED.

What is so hard about that?  Not hard at all, its easier IMO, because you don't have to click next a thousand times.

---

### Post by mikewhatever on 2009-04-13
> **eljopc said:**
> Thanks mike...

What I see here is Linux users defending Linux but thats not the issue here. I think Linus is great but not workable for the big world. 

I can take a Linux laptop to the first man on the street and he will first say that it looks nice. But now he wants to install a driver for his printer/scanner/webcam ... that is not in Linux but he has to download from the manufacturers site, he will never get it installed without a book with directions. 

How do we ever bring this to the big public if we won't listen to the non Linux users?

You may find this article interesting. [http://itmanagement.earthweb.com/osrc/article.php/3814316/Linux-Desktop-Hardware-Myths-Explored.htm](http://itmanagement.earthweb.com/osrc/article.php/3814316/Linux-Desktop-Hardware-Myths-Explored.htm)

---

### Post by Therion on 2009-04-13
> **chris4585 said:**
> ... go to a website and download a .deb file and if you click on a .deb file, a window will pop up, click install, type in password, INSTALLED.
Which works fine for Ubuntu but not so well in, say, Fedora.  Or OpenSuse.  

Which is more or less OP's original complaint.  OP wants many distros and one "universal" install method.

---

### Post by sekinto on 2009-04-13
I don't see what the problem is. The simpleton user doesn't know if they are using DEBs or RPMs, it is completely transparent in Ubuntu. When a user installs something using Add/Remove or Synaptic they don't have to worry about formats, to them they are just downloading **programs**, not DEBs.

And you can have self-extracting packages in Linux like you have with Windows if that is what you are looking for, you could even give the file the extension .exe if you wanted to (although most people use something like .bin).

I guess my point is that it doesn't effect average users and advanced users will be happy to have a choice.


And I tend to prefer package management more than getting programs directly from the creator. It is simpler, faster, lighter and much more organised.

---

### Post by HermanAB on 2009-04-13
"Which works fine for Ubuntu but not so well in, say, Fedora. Or OpenSuse."

If you double click a RPM in Red Hat, Fedora, Suse, Mandriva or PCLOS, it will pop up a dialogue window, ask for a password and install it.  It can't be made any easier, unless you want to have drive-by downloads in Firefox.

---

### Post by Therion on 2009-04-13
> **HermanAB said:**
> [quote=Therion]"Which works fine for Ubuntu but not so well in, say, Fedora. Or OpenSuse."

If you double click a RPM in Red Hat, Fedora, Suse, Mandriva or PCLOS, it will pop up a dialogue window, ask for a password and install it.  It can't be made any easier, unless you want to have drive-by downloads in Firefox.[/QUOTE]
Understood, and what's more I'm in complete agreement with you.  Personally I have no issue with each and every distro having their own unique method of package-management.  Linux is about CHOICE and I thought I made that abundantly clear in my first post.  The OP, on the other hand, does take issue with this and I was simply attempting to *clarify* the point, not *support* it.

That point being that while each package-management system is, *inside its own distro*, easy enough you can still not one-click install a (dot) deb in Fedora any easier than you can one-click install a (dot) rpm file in Ubuntu; and THAT, as far I understand the OP's first post, *is* the issue (for them).  What the OP wants is, in short, a Universal Install Format that works across all distros.  That idea is, IMO, counter to the Linux Way of Doing Things.

---

### Post by juancarlospaco on 2009-04-13
You can make a .exe or .sh with all software inside, i have been made alot of them...

Not kidding, 
install PeaZIP, make a Self-Extracting and put all .deb inside the .exe and a gksudo dpkg -i *.deb command.
*PeaZIP's Self-Extracting are designed for Wine and all GPL'ed.*

you are done.

---

### Post by BGFG on 2009-04-13
Hi guys, just signed in. has anyone mentioned package-kit ? It basically ONE frontend with a backend that interprets all(or all the major) different installation arcitectures. So problem solved.

@ OP, you should look into the history and reasoning behind the DEBIAN and RED HAT architectures.

---

### Post by swoll1980 on 2009-04-14
> **BGFG said:**
> Hi guys, just signed in. has anyone mentioned package-kit ? It basically ONE frontend with a backend that interprets all(or all the major) different installation arcitectures. So problem solved.

@ OP, you should look into the history and reasoning behind the DEBIAN and RED HAT architectures.

I still doubt that all the distros will adopt this. Am I wrong?

---

### Post by pbpersson on 2009-04-14
> **eljopc said:**
>  I now get why manufacturers from hardware do not easily make software for Linux. Where there is a simple way to make it for Windows and Mac, for Linux every distro needs his own.

From what I have heard, this is totally false.  The drivers are down inside the kernel and all Linux distros start with the same kernel - the foundation - from Linus and then build on top of it.

---

### Post by BGFG on 2009-04-14
@Swoll1980, Fedora usually leads the way in these kind of things, and they are already using it. I think once it has been ironed out totally, it may be adopted in Ubuntu. Hope to see it in Karmic :)

PS. going to stop posting to this thread now and unnecessaraily bumping it. but check it out Swoll, looks exciting..

---

### Post by dspari1 on 2009-04-14
> **eljopc said:**
> Some thoughts on Linux and what I'm missing to get the job done. Well maybe not missing wanting to have/see different. 

I'm pointing to the install of "new" software, packages and drivers. There are so much different ways to install under Linux and I think there should only be one. From within Linux but also from websites as a download.

Yes I'm a Windows user, not by choice but it was there first, understandable and there was one way of doing things. Look at the install of software, we got .exe and .MSI but all self extracting packages independent and simple and no strange extra code for extracting and installing.

Now back to Linux, non self extracting software and to much different install packages that need different unpack software and code.....

Debian, Ubuntu: APT
[root]# apt-get install packagename

Fedora, Red Hat: yum
[root]# yum install packagename

Mandriva: urpm
[root]# urpmi packagename

Tar Balls
[user]$ tar -xzvf filename.tar.gz

SUSE uses RPM

This is not for human beings, this is for Linux Power users. I train a lot of people on Windows but this should be one type of install package no strange code in a window to extract or install.

Is it so hard to make one package that extracts all software into Linux. I now get why manufacturers from hardware do not easily make software for Linux. Where there is a simple way to make it for Windows and Mac, for Linux every distro needs his own.


Practically every single software for Ubuntu can be either be gotten through synoptics(now (k)packagekit as of 9.4) or through a .deb file. You do not ever have to touch a command line if you don't want to.

The reason why many instructions in help files give command lines as instructions is because it is easier to just give you a command line to copy and paste than to tell you how to navigate through a graphical user interface to do the same thing.

---

### Post by SunnyRabbiera on 2009-04-14
> **dspari1 said:**
> Practically every single software for Ubuntu can be either be gotten through synoptics(now (k)packageit as of 9.4) or through a .deb file. You do not ever have to touch a command line if you don't want to.

The reason why many instructions in help files give command lines as instructions is because it is easier to just give you a command line to copy and paste than to tell you how to navigate through a graphical user interface to do the same thing.

I thought only Kubuntu was using Packagekit...

---

### Post by hanzomon4 on 2009-04-14
> **eljopc said:**
> Some thoughts on Linux and what I'm missing to get the job done. Well maybe not missing wanting to have/see different. 

I'm pointing to the install of "new" software, packages and drivers. There are so much different ways to install under Linux and I think there should only be one. From within Linux but also from websites as a download.

Yes I'm a Windows user, not by choice but it was there first, understandable and there was one way of doing things. Look at the install of software, we got .exe and .MSI but all self extracting packages independent and simple and no strange extra code for extracting and installing.

Now back to Linux, non self extracting software and to much different install packages that need different unpack software and code.....

Debian, Ubuntu: APT
[root]# apt-get install packagename

Fedora, Red Hat: yum
[root]# yum install packagename

Mandriva: urpm
[root]# urpmi packagename

Tar Balls
[user]$ tar -xzvf filename.tar.gz

SUSE uses RPM

This is not for human beings, this is for Linux Power users. I train a lot of people on Windows but this should be one type of install package no strange code in a window to extract or install.

Is it so hard to make one package that extracts all software into Linux. I now get why manufacturers from hardware do not easily make software for Linux. Where there is a simple way to make it for Windows and Mac, for Linux every distro needs his own.

Um... unless you're running all of these different distros at the same time, why do you care that fedora is yum install and Ubuntu is apt-get install?

As far as everything else.. rubbish
Ubuntu has Debs... you can go to a website like getdebs, download, double click, and click install, next>next>next>next>next> not required. Also you can launch add/remove and get the "app store" experience that everyone is now moving to. Odd that Linux has been doing this for years but now that Apple does it's a great thing, a little polish goes a long way.

The only time you have problems is when a piece of software you want is not packaged or not in the repos. Usually this is beta software or updated versions of apps that do exist in the repos. The PPAs have helped ease this problem. But really does the average user go around looking for betaware or the latest greatest banshee?

---

### Post by dspari1 on 2009-04-14
> **SunnyRabbiera said:**
> I thought only Kubuntu was using Packagekit...


That's strange. I though Kubuntu switched to it because Ubuntu did. (I didn't try Ubuntu vanilla).

If that's the case, I don't see why Kubuntu is going this route.

---

### Post by MikeTheC on 2009-04-14
@ OP:

I'm not sure I really understand what your difficulty is. How much easier do you want it? Anybody who wants to write software for Linux and is serious about it has (and this is as much for the protection of the individual as it is the community) to ensure their code is peer-reviewed.

If a user, once having had explained to them the basic concept of repo-based software acquisition, still can't cope with it, then that person shouldn't be using Linux. Intelligence, common sense, personal responsibility... they have to start somewhere.

---

### Post by Therion on 2009-04-14
I've just installed PackageKit out of curiosity. 

In doing so I now have two Add/Remove menus (the new one is under System/Administration) two Software Sources (both under System/Administration) and a couple new menu items (Software Log Viewer and Service Pack Creator) under Applications/System Tools.

As for the Wow-Factor... I must be missing something because it looks a lot like Synaptic only with crappier menu icons.  I'm not sure what this is supposed to do that my existing Add/Remove and Synaptic can't do already??

---

### Post by SomeGuyDude on 2009-04-14
Here's the thing.

The "human method" involves you going to find the software, downloading it to your computer, installing it, and then having that package just sitting around wherever you downloaded it. It's a lot of steps.

The "power user" method involves knowing a simple command, and as soon as you want the piece of software you needn't go find anything or have a "download folder" that you monitor. If I want opera I just type "[whatever command] opera". Simple simple.

No offense, but if "apt-get install [software]" is too difficult for someone, maybe they need something a little less complicated, like a coloring book. I could teach a ten year old this stuff in a  half hour, no problems.

The thing is, if you want take a giant list of the trade-offs that the "difficult method" offers you, you'll quickly find that the Linux method has made it far easier.

I'll give you a great example: ever downloaded a package from getdeb that didn't have its dependencies handled? Boy that's annoying. You gotta hunt down what it needs and next thing you know you're in dependency hell, hunting down package after package to download. Meanwhile you punch a command into the terminal and boom. Done.

Now, admittedly, some distros are working on having installation links that use their terminal commands (SUSE's one-click-install, for example), but seriously. The command line is NOT THAT DANG HARD. It's actually pretty farking simple. It takes maybe, what, five minutes to go "oh, so pacman -S [package] installs, huh? Neat."

---

### Post by Sef on 2009-04-14
This subject has been brought up numerous times.

---

### Post by Tibuda on 2009-04-14
> **SomeGuyDude said:**
> I'll give you a great example: ever downloaded a package from getdeb that didn't have its dependencies handled? Boy that's annoying. You gotta hunt down what it needs and next thing you know you're in dependency hell, hunting down package after package to download. Meanwhile you punch a command into the terminal and boom. Done.
I only had such experience when installing from the source code (./configure && make && sudo make install).

---

### Post by juancarlospaco on 2009-04-14
CNR.com have a Linux Only App Store *(Ubuntu included, and Paid software)*

---

