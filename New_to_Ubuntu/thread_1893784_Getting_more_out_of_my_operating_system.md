---
title: "Getting more out of my operating system?"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by 1st2fall on 2011-12-11
I have been told that I needed to learn to use linux in order to further my potential as a physicist, well, not exactly like that...but that learning how to be flexible with linux would help me get internships and so on. 

I just installed Ubuntu 11.10 and it feels like I've just got a Mac with a tenth of the battery life. I know Ubuntu has advantages other than being free, I just don't know what they are yet. I am having difficulty installing and compiling latex and I can't even start to install and run things like ROOT...besides the applications I'll need that are strictly for linux, what kind of things should I be doing to maximize my experience?

A few side questions:
I just went for the homepage download of 11.10 without really investigating much. I have a feeling kubuntu is KDE+ubuntu, but I'm not really sure what that means yet. Just starting with the prefix list given for threads, how can I learn what these are in a concise manner (i.e. without spending a lot of timwading through Google)?

Thanks for your time,
I'd really like to get to know Ubuntu for what it is, but at the moment I just don't know how to do that.

---

### Post by mastablasta on 2011-12-11
> **1st2fall said:**
> I have been told that I needed to learn to use linux in order to further my potential as a physicist, well, not exactly like that...but that learning how to be flexible with linux would help me get internships and so on. 

I just installed Ubuntu 11.10 and it feels like I've just got a Mac with a tenth of the battery life. I know Ubuntu has advantages other than being free, I just don't know what they are yet. I am having difficulty installing and compiling latex and I can't even start to install and run things like ROOT...besides the applications I'll need that are strictly for linux, what kind of things should I be doing to maximize my experience?


Use sudo to gain root privileges.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

also check first if the programme is available in software center.

> 
A few side questions:
I just went for the homepage download of 11.10 without really investigating much. I have a feeling kubuntu is KDE+ubuntu, but I'm not really sure what that means yet. Just starting with the prefix list given for threads, how can I learn what these are in a concise manner (i.e. without spending a lot of timwading through Google)?


exactly - Kubuntu is KDE on Ubuntu core. uses same repositories and is supported by Cannonical. similary Xubuntu is XFCE on Ubuntu and Lubuntu is LXDE on ubuntu. these are just different desktop environments you can choose from. some are known to be lighter on system resources (XFCE, LXDE) others just do things in a different way with different libraries.

> 
Thanks for your time,
I'd really like to get to know Ubuntu for what it is, but at the moment I just don't know how to do that.

read *Ubuntu manual*, free e-book *Ubuntu pocket guide* and free e-book *The linux command line*.

other than that just ask your quesitons.

---

### Post by mcduck on 2011-12-11
The first thing is to stop to try downloading stuff from the web and compiling it yourself, and instead use the package management. It will download and install applications automatically for you, and also manages updates for the applciations as well as the operating system itself. And I'm absolutely sure you'll find all the common things like LaTex there. :)

Just take a look at the Ubuntu Software Center, and search for whatever apps you might need.

What comes to root, Ubuntu's security model is built in a way that the root account is locked and instead admin users have the ability to temporarily gain root privileges to handle admin tasks, through the use of sudo&gksudo commands. You'll find a good explanation and instructions here: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

It's hard to say anything about the battery life issue without knowing more about your computer, but the first thing to check would be your graphics cardd rivers, if you happen to have a recently new nVidia or AMD graphics card. Check the "Hardware Drivers" tool in Settings, if it offers any drivers for you, you definitely should install them.

...and yes, you are right, Kubuntu is the same Ubuntu system, but comes with KDE as it's desktop environment (by default) instead of the Gnome that's sued by default in Ubuntu. Same applies for other options like Xubuntu (XFCE4 as desktop) and Lubuntu (LFCE as desktop). Which one you get effects the graphical desktop environment you'll have and the applicatiosn istalled by default, but since it's still one and the same OS all the desktops and programs can be installed regardless of which Ubuntu variant you use to install the system. And which one you should get is pretty much just a question of personal preference.

I hope this helps at least a bit. And welcome to Ubuntu, of course. There might be a bit of a learning curve, but that's just to be expected when learning a new operating system. It's definitely worth the trouble, though, once you get a bit more comfortable with Ubuntu I'm sure you'll find going back to OSX or Widnows quite hard... ;)

---

### Post by BC59 on 2011-12-11
> **1st2fall said:**
> I just installed Ubuntu 11.10 and it feels like I've just got a Mac with a tenth of the battery life. 

The other questions being answered, I suggest you to install the application Jupiter, to control the life of your battery.

In this site is explained perfectly how to do it. You just need to open a terminal with CTRL+ALT+T and paste and run the commands of the website.

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

---

### Post by 1st2fall on 2011-12-11
I know how to use sudo to temporarily elevate to root privileges :)
...I was referring to this: [http://root.cern.ch/drupal/](http://root.cern.ch/drupal/)

@BC59 Thank you! This application is very helpful :)

@mcduck I'm not sure that the serious physics systems I want to run come in that pre-boxed form. While they do arise when you wade through the Ubuntu documentation wiki, how to install them is not really explained (or so I remember). I did find some LaTeX applications, but for some reason I can't get it to compile properly via terminal, if I have a more specific question I'll ask the appropriate people though ^^.
Where should I go to investigate the KDE/Gnome/Other differences? I believe I have Gnome and while I don't have any issues, I would like to investigate.

@mastablasta I will look into those resources some time later today if I can and will be sure to ask if I have a more direct question about something later. Thanks!

---

### Post by mastablasta on 2011-12-12
ah you will need to donwload source and compile it. 
 
but first check if it is available in software center. you might need to enable additional repositories to see it.
 
a good place to investigae is distrowatch that provides links to reviews as well as information on installed packages:
 
[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)
[http://distrowatch.com/table.php?distribution=kubuntu](http://distrowatch.com/table.php?distribution=kubuntu)
[http://distrowatch.com/table.php?distribution=xubuntu](http://distrowatch.com/table.php?distribution=xubuntu)
[http://distrowatch.com/table.php?distribution=lubuntu](http://distrowatch.com/table.php?distribution=lubuntu)
 
Then of course their websites (you can google them) for example: [http://www.kubuntu.org/](http://www.kubuntu.org/)
and then take the tour....

---

### Post by daemondign on 2011-12-12
Looks like you're already getting a lot of answers from some really knowledgeable people... 
I'm eating up these links. :popcorn:
From the opposite end of the spectrum, one newby to another; if you're having trouble understanding  "*what's all the rave about linux?*" Read up on the history and developement of Linux, it'll give you insight into the ideals of this whole community. 
 When I got Ubuntu (*cough, earlier this week), the first thing I did was go to Google and type "learn linux." The results ranged far beyond my grasp, to downright goofy. But there is a lot of good reads, and some cool programs that really help me as I push my brain to understand Linux. You registered on the Ununtu Forums. Try browsing through podcast they're informative and entertaining.. if you have ADD like me, you may have to crack open a terminal and mess up some bash commands or open Firefox and browse through some forums; no worries, they make excellent background music.
My point being, if you wanna know what all the fuss is about, jump in and get dirty!!!!

---

### Post by MartijnNL on 2011-12-12
I'm not certain it's the right software, but it looks like there's a version of ROOT available on Ubuntu 10.04, which is a long term support version and will be supported until April 2013 (so just as long as the current Ubuntu 11.10).

So if you would install Ubuntu 10.04 you can install it using Software Center.

Have a look at this list: [http://packages.ubuntu.com/lucid/allpackages?format=txt.gz](http://packages.ubuntu.com/lucid/allpackages?format=txt.gz)

Scroll down until 'root....'

Oh, btw: for Natty there's also: [http://askubuntu.com/questions/39363/how-do-i-install-root-cern](http://askubuntu.com/questions/39363/how-do-i-install-root-cern)

---

### Post by Testingte on 2011-12-14
You can install several different DE's via software center. And more with some investigation!

GNOME Shell, Gnome 3's Fallback, KDE, LXDE, XFCE, Enlightenment, Openbox, Fluxbox, and (though it is not recommended as of yet..) MATE.

---

### Post by CoffeeRain on 2011-12-14
I would say that learning bash would help you get more out of Linux. I find that even when I do everyday stuff, I can do it way more efficiently using the command line than using the GUI.

---

### Post by grahammechanical on 2011-12-14
@1st2fall

Please explain how any of the above will help you or anyone become a physicist? I have been using Ubuntu for almost 5 years. How close am I to being a physicist? Could you tell me?

Now, I would not be surprised to find that computers used in physics run Unix or Linux programs. No. That would not surprise me at all. Are you saying that to learn to be a physicist you also have to learn to code Unix or Linux programs?

Surely, at the start you only need to learn how to use the programs being run on the computers. I do not doubt that physicists use some very specialized programs and that these programs are tailor made for the task. I just do not think that these professors code their own programs.

Ubuntu is a very fine Linux operating system. I use it. I like it but I cannot see how learning to use the Ubuntu operating system will help you become a physicist. Any more than taking a course on how to use Microsoft Outlook would help you. It would be useful if that program was in use where you study or do research but that course will not help you to become a physicist.

I would suggest that you need to learn the Linux command line commands. That kind of stuff. And the Linux file system. And I guess that you may need to know how to compile Linux programs. You can use Ubuntu to train yourself. You also need to know about the computer systems that you will be using as a research student of physics.

Regards.

---

### Post by Paqman on 2011-12-14
As well as Ubuntu you might want to check out Scientific Linux, at the very least so that you're familiarised with an RPM-based distro. No idea how widely it's actually used, if at all, but lots of big companies use RHEL.

I agree with grahammechanical: learn some command line basics, the  file system (including the concept of permissions), and package management, but it's mainly about getting to grips with the applications you're likely to encounter.

---

### Post by BBQdave on 2011-12-14
> **CoffeeRain said:**
> I would say that learning bash would help you get more out of Linux. I find that even when I do everyday stuff, I can do it way more efficiently using the command line than using the GUI.

+1

I believe this would be of the most value in your world; to qualify this answer, *I am not a scientist*, just a GNU/Linux user that has observed the scientific communities use of GNU/Linux :)

And as you gain more comfort with GNU/Linux, and explore more desktop environments (DE), I would suggest Xubuntu.  Xubuntu is a more configurable DE; plus Synaptic Package Manager, and I think you will be pleased with a friendly yet powerful **DE** :D

---

### Post by Mark Phelps on 2011-12-14
> I have been told that I needed to learn to use linux in order to further my potential as a physicist, well, not exactly like that...but that learning how to be flexible with linux would help me get internships and so on.

If you want an internship as a Linux programmer, then yes, this would definitely help.

Plus, unfortunately, having been involved in internship programs myself (I'm a Graduate Computer Scientist by education), I can attest that some of them are little more than grunt work -- getting college students for low rates (in some cases, free).  If that's the case, then knowing any Linux stuff will probably help -- if you want to spend your time doing menial computer tasks.

The Scientists I worked with (at Bell Labs, NASA, and others) were more interested in how to USE computers to do their projects, not how to program.  For the latter, they always had IT folks -- or interns.

So, will it help you get an intern position? Most probably.

Will it help you become a physicist? Probably not.

---

### Post by alphacrucis2 on 2011-12-14
> **1st2fall said:**
> I know how to use sudo to temporarily elevate to root privileges :)
...I was referring to this: [http://root.cern.ch/drupal/](http://root.cern.ch/drupal/)

@BC59 Thank you! This application is very helpful :)

@mcduck I'm not sure that the serious physics systems I want to run come in that pre-boxed form. While they do arise when you wade through the Ubuntu documentation wiki, how to install them is not really explained (or so I remember). I did find some LaTeX applications, but for some reason I can't get it to compile properly via terminal, if I have a more specific question I'll ask the appropriate people though ^^.
Where should I go to investigate the KDE/Gnome/Other differences? I believe I have Gnome and while I don't have any issues, I would like to investigate.

@mastablasta I will look into those resources some time later today if I can and will be sure to ask if I have a more direct question about something later. Thanks!


One thing. CERN have their own linux distro called 'scientific linux' (which is based on redhat enterprise linux). Even if you don't use the SL distro you may find their forums useful as there will be lots of physics people using it.

A couple of links:

[http://www.scientificlinux.org/](http://www.scientificlinux.org/)
[http://scientificlinuxforum.org/](http://scientificlinuxforum.org/)

---

