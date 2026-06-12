---
title: "Ubuntu dummy: tutorial for Windows user switching to Linux?"
date: 2022-06-16
forum: New to Ubuntu
---

### Post by abdul1337 on 2022-06-16
Hi,

I am self taught programmer from non-cs background. Currently, installed Ubuntu but trying to get my head around few things:
[LIST]
[*]How to remember those long commands posted on internet? 
[*]Best resource (ideally to read not watch) for learning linux for FIRST time user? I am trying to get my head around filesystem of linux.
[*]Wish there was interactive tutorial like codecademy style for linux that is actually free? 
[*]What is universe repository and why is sudo apt-get update always required? 
[*]Is there way to disable password authentication every time I use sudo? 
[/LIST]
So far I am liking linux over windows due to simplicity mainly, however that leaves windows for only MS Office (VBA programming) and Games. Is that the only utility windows will give me over linux?

In my goal to venture higher in data engineer/analyst/science career (currently working as a hybrid data engineer-analyst), I can't help but to learn a Linux distro, so picked Ubuntu. Plus I heard it helps with more employ-ability in data domain, don't know the validity but that's what i know.

---

### Post by tea for one on 2022-06-16
> **abdul1337 said:**
> How to remember those long commands posted on internet?
Open a terminal and type [COLOR="#0000FF"]history[/COLOR].
You will see a list of previously used commands.
Find the number of the command you wish to execute.
For example, you wish to repeat command no.58
Then type ```
!58
```

---

### Post by Holger_Gehrke on 2022-06-16
> **abdul1337 said:**
> 

[LIST]
[*]How to remember those long commands posted on internet? 
[/LIST]

Once you understand the logical structure of shell commands (program to call, options, parameters) the commands become easier to remember. The shell actually is a programming language, so understanding the way it works is important for working with it efficiently. Reading the manual pages for the various commands - before you execute something you copy-and-pasted from somewhere on the net - will hopefully stop you from doing something regrettable. Simply type 'man ' followed by the name of the command you want to know more about, for example 'man ls'. And yes, there's a man page for the manual reader ('man man').
> **abdul1337 said:**
> 


[LIST]
[*]Best resource (ideally to read not watch) for learning linux for FIRST time user? I am trying to get my head around filesystem of linux. 
[/LIST]

I don't know about the best one, but a good one which keeps getting recommended is 'The Linux Command Line' by William Shotts. It's available in print from No Starch Press and as a free PDF from [http://linuxcommand.org](http://linuxcommand.org) - this site also has quite a few other related things.
> **abdul1337 said:**
> 


[LIST]
[*]What is universe repository and why is sudo apt-get update always required? 
[/LIST]

The repositories are split into various areas (main, universe, multiverse, restricted) mostly along lines of licensing and who does support for these packages. 'universe' contains free software which is not directly supported by Canonical.
'apt' keeps lists of all the packages available from the various repositories configured as sources for packages. 'apt update' or 'apt-get update' updates these lists. You should always update the package lists before trying to upgrade your packages (apt upgrade / apt-get upgrade / apt full-upgrade / apt-get dist-upgrade), otherwise apt will not know about new packages which have become available since your last update.
> **abdul1337 said:**
> 


[LIST]
[*]Is there way to disable password authentication every time I use sudo? 
[/LIST]

Yes, but removing safety measures for the sake of convenience is generally frowned upon. Read the manual pages for 'sudo' and the file /etc/sudoers and 'visudo' ('man sudo', 'man 5 sudoers', 'man visudo'). Afterwards you'll know how to do it and you'll understand why it's considered a really bad idea. And you don't have to type your password every time you use sudo. There's a ticket system in sudo; once you've entered your password your user account gets a ticket valid for a limited time (15 minutes by default); as long as that ticket is valid you aren't asked for your password again. That ticket gets "revalidated" every time you run another command with 'sudo' and you can also revalidate it by running 'sudo -v' without a command.

Holger

---

### Post by him610 on 2022-06-16
> How to remember those long commands posted on internet?
You do know how to copy and paste, right?

---

### Post by poorguy on 2022-06-16
> **abdul1337 said:**
> 

[LIST]
[*]How to remember those long commands posted on internet? 
[/LIST]


Copy and paste commands into a file you create using Libreoffice-word.

> **abdul1337 said:**
> 


[LIST]
[*]Best resource (ideally to read not watch) for learning linux for FIRST time user? I am trying to get my head around filesystem of linux. 
[/LIST]


[https://linuxjourney.com/](https://linuxjourney.com/)

---

### Post by ActionParsnip on 2022-06-16
How to remember the long commands?

How do you know how to form long sentences in English language? You don't. You know individual words and phrases and constructs and can string them together to make phrases and so on. The same thing works with long Linux based commands.

---

### Post by ActionParsnip on 2022-06-16
```

sudo apt install x

```
is always needed because your user is just that, a user. It has been given permission to run commands as root using the sudo command. Your user doesnot have enough access to write to the system outside of it's $HOME folder and this keeps the OS secure. When you use sudo you will enter a grace period and so you don't need to enter your password every time. You can end the grace period using
```

sudo -k

```

---

### Post by abdul1337 on 2022-06-16
Thanks for:

 - The interactive website, really liked it. @poorguy
- Yeah can do that @him610
- Ok I need to think of it as a programming language, gotchya. And thanks for concise explanation on repos & knowing the why behind apt-update @ Holger-Gehrke
- Thanks for the tip. Will speed up the memorization process. @ tea for one 

And cheers to everyone else. I can start the linux journey now :)

---

### Post by oldfred on 2022-06-16
I still do not remember most commands, only a few I regularly use. Some I build into script xxx.sh files to run with bash.
But I like Zim as a tool to store info. It also has clickable links, so if I save a web site I can just click on it.
man zim
> [FONT=monospace][COLOR=#000000]zim - A Desktop Wiki Editor[/COLOR]
[/FONT]
I was originally just saving to text files, but then imported those  into zim. I now have over 30 pages of zim notes which are searchable on each page or across all of them. If you did a Google search of oldfred on Ubuntu forum's you probably would find all my notes.

For years I used MS Access & vba at work, but now retired.
I now use python and sqlite. Bit of a learning curve, but worthwhile.

---

### Post by grahammechanical on 2022-06-16
Ubuntu used to be known as "Ubuntu for humans." The intention of the developers is to make Linux as easy to use as possible for the ordinary user. I think that they have done a fine job. It is why we do not need to remember long commands.

The Software Updater utility runs the update/upgrade commands for us. Ubuntu Software offers applications and will install them for us. System Settings will make changes to the desktop environment and the User Interface for us. 

A lot of things can be done using Graphic User Interface utilities. Whereas years ago the changes had to be made by long commands. It allows the user to get on with the work that they want to do with their machine. And I like it.

When I first started visiting this forum every answer to every problem was a series of incomprehensible commands. I am glad that Ubuntu is no longer that complicated. In my opinion anyone choosing Linux and especially Ubuntu is not a dummy but smart.

Regards

---

### Post by The Cog on 2022-06-16
As for long commands, don't try to remember them all - your head will explode. Remember the interesting ones - the ones that you think you will find useful later. But more important, look at long ones and just try to understand how the long ones are put together from smaller pieces. Get a feel for how short commands chain together by piping, to do something really useful. 

The first one I think I learned to use was grep. Something like using cat to send the contents of a file to grep which can search for words and much more. Things like grep, sed and awk can take a huge number of arguments - you'll never learn them all. But knowing roughly what they do, and when that kind of thing might be useful, and how to look up all the exact arguments is good. I admit I started using awk for the first time only recently, and I could kick myself for not putting that effort in years ago.

It's a bit like starting to do DIY house maintenance. You start with some basic tools like a hammer and a screwdriver, and learn other tools over time, as and when the need for that tool arises. But it's all about picking up and learning tools as the need arises. Reading these forums and other sources will show you other tools that might come in useful one day, but just knowing things exist is progress.

Grep uses regular expressions as the description of the text it's searching for. If you're going to do data science, you will probably use regular expressions a lot. Worth learning the basics fairly early on.

That's my opinion, anyway. Enjoy learning.

---

### Post by TheFu on 2022-06-16
> **abdul1337 said:**
> I am self taught programmer from non-cs background. Currently, installed Ubuntu but trying to get my head around few things:

There are programmers, then there are developers.  The language matters too.  Talking to a C programmer is very different than talking to a Php or Javascript programmer. Very different.

> **abdul1337 said:**
> How to remember those long commands posted on internet? 
man pages. they are on your system and have the exact parameters for the exact version of each command on you system.  You can use man or xman to see them.  I use little scripts, aliases and vimwiki to keep notes.  There are far too many to write them all down.

Be very careful copy/pasting commands off websites.  Always put every command into an editor first. Never paste directly into a terminal.  In one of my Linux classes, I setup a website with hidden commands that did all sorts of nasty things, told all the students to just copy/paste it to see what it did.  The first 5 were surprised and told the others NOT to do it.  I showed the class on my system. I had the script setup a reverse shell into their system from a server I controlled and had it restart every time they rebooted.  The next class was interesting, since I didn't tell them about the reboot not wiping the reverse shell.  Be careful out there. You are your own worst enemy.

> **abdul1337 said:**
> Best resource (ideally to read not watch) for learning linux for FIRST time user? I am trying to get my head around filesystem of linux.
There are 20 different file systems, not 1.  That's different from other OSes. Each file system has different reasons to exist, usually related to workload, data integrity, or enterprise management features.   [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

> **abdul1337 said:**
> Wish there was interactive tutorial like codecademy style for linux that is actually free?  there are many.  But Linux skills are like learning to be a world-class sprinter when you don't know how to crawl first.  It takes years of practice to be a world-class sprinter, but most people, with effort, can be walking in a few months, running in a few years, and sprinting ... there are few sprinters.

> **abdul1337 said:**
> What is universe repository and why is sudo apt-get update always required? 
It isn't.  There are different repos. Each has different packages. We can add our own repos too, called PPAs.  **apt update**  (no need for apt-get much anymore) tells APT to update all the signatures in their package databases.  These signatures are part of the cryptographic layers to ensure that we get the packages from the people we think they are from, not some man-in-the-middle.  That's were setup.exe has a huge failure but APT had solved in the 1990s.  Most Linux distros, including those that don't use APT, have similar assurances and signatures.
Running  **sudo apt update** daily before you install something is sufficient, so you don't always need to run it.  On my stable systems, I run it weekly, before patching the entire system.  You can read more about APT packaging system at debian.org.

> **abdul1337 said:**
> Is there way to disable password authentication every time I use sudo? 
Yes. But it is a terrible idea and a number of reasons.  You don't want to be hacked do you?
Until you can figure this out for yourself, it is probably too dangerous.  BTW, the default timeout is 15 minutes, so if you use sudo every 14 minutes, that should prevent you being asked to enter the password again.  New users often abuse sudo.  It should seldom be needed on a working, stable, Linux system.  I haven't used it at all the last 2 days on this system (looked at my command history).

> **abdul1337 said:**
> So far I am liking linux over windows due to simplicity mainly, however that leaves windows for only MS Office (VBA programming) and Games. Is that the only utility windows will give me over linux?
There are things to like about most OSes.   VBA is Windows-only.  There are 1M utilities for Windows and for Linux. How can anyone claim either is better or worse?   Is a Car better than blue?

> **abdul1337 said:**
> 
In my goal to venture higher in data engineer/analyst/science career (currently working as a hybrid data engineer-analyst), I can't help but to learn a Linux distro, so picked Ubuntu. Plus I heard it helps with more employ-ability in data domain, don't know the validity but that's what i know.
For data stuff, learn R and Python.  The Linux distro doesn't matter.  Don't get too stuck with "Ubuntu" ... it is just 1 flavor and all Linuxen are related and extremely similar.
Unix knowledge generally pays more than MSFT.  There are some things that I'd never, ever, consider doing on MS-Windows and there are a few things that are very difficult on any other platform.  I was deploying Nuance voice response servers at a client. We had 20K employees calling in and they wanted sufficient VRML to support 400 concurrent users.  Nuance only ran on MS-Windows.  Ever used Siri on an iPhone?  That's Nuance.  This project was long an iPhone or Android existed.  Where I worked, we had over 150K servers. 20K were Windows and the rest were Unix and Linux spread around the world.  Oddly, we needed many more Windows admins due to very poor automation for Windows management.

With Unix, managing systems that are mostly similar can be 1, 5, 100, 1000, 50000 systems and a single admin.  I'm small-time now, but have about 20 systems to manage.  I can run 1 command that impacts all 20 of those systems in a specific way.  That can be in series or parallel, if I like. My choice.  Or I can run X in parallel as the command is run across all the systems in the group.

[https://blog.jdpfu.com/2017/09/12/linux-command-line-or-shell-resources](https://blog.jdpfu.com/2017/09/12/linux-command-line-or-shell-resources) has a list of resources.
There are Linux Skill Challenge websites all over too. [https://linuxupskillchallenge.com/](https://linuxupskillchallenge.com/)

And don't forget to find a LUG in your city.  Lots of LUGs meet online due to COVID.  There you can lurk and learn, just introduce yourself and you'll be welcome.  Most Universities will have a LUG that is open to anyone. My metro area has 7 LUGs spread around the city. We all know each other and work together on stuff.  Last week, was SELF - SouthEast Linux Fest a Linux conference in Charlotte, NC.  The videos have started to show up on their youtube channel.  Videos from prior years are there too. These conferences are less about exactly what to type, but more about "why".  The "why" is the important part and helps our minds create links at different levels to different commands.

Just know that there were lots of really smart people before you and that there is a reason for the way things are that is probably extremely elegant and efficient.  Because, there will be many times when you'll come across something and be certain the programmer was an idiot. Trust me.  I thought that too and it turned out they were brilliant.  

There are a few programmers I'm still positive that are idiots - those that create changes just to change something and break how it worked the last 20+ yrs for reasons that 0.0005% of users experience.  So, rather than make a tool for that time group, they want to screw with the entire world, change stuff, for worse outcomes.  We see that from time to time with Canonical and with Gnome and with systemd.  I don't mind new, until it is forced as the default and proven **not** to be ready for wide use. Plenty of examples exist.

---

### Post by web-user on 2022-06-25
[B]Note from a Forum Admin:  This is terrible advice and will destroy your system's security.  For your own sake, please DO NOT do this.
[/B]
To make [superuser]("https://teracontent.com/how-to-protect-linux-server-from-bots-and-hackers/") access passwordless, use this:
visudo
Find  line with %sudo groups and replace it with this:
%sudo   ALL=(ALL:ALL) NOPASSWD:ALL[FONT=microsoft sans serif]

Save and exit. Relogin and it's done.[/FONT]

---

### Post by web-user on 2022-06-25
> **The Cog said:**
> Something like using cat to send the contents of a file to grep which can search for words and much more

Isn't it a [UUOC]("https://en.wikipedia.org/wiki/Cat_(Unix)#Useless_use_of_cat")? You can do just grep PATTERN FILE.
Anyway, you wrote a great advice!

---

### Post by ActionParsnip on 2022-06-25
Yes... And remove a lot system security from your system.... Great advice /slowclap

---

### Post by QIII on 2022-06-25
@web-user:

That my be the worst advice I have seen on the Ubuntu Forums.  Please do not suggest such things again.  New users might unwittingly follow such advice and completely destroy all the security elements built in.

---

### Post by mIk3_08 on 2022-06-26
> **abdul1337 said:**
> How to remember those long commands posted on internet?
Remember? What a word. You don't have to remember commands/codes. Understanding it makes you to analyze more wider/broader scope to think than to remember in the field of computing.
If you are a programmer, remember a codes won't help you to become an elite/guro but understanding and mastering on what you are doing as a programmer makes you the ability to conquer the digital world of computing. So don't just remember it. "Understanding" it is the right word of choice. Regards and cheers.

---

