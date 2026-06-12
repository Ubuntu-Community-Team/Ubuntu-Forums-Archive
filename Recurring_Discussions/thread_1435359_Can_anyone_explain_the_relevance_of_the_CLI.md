---
title: "Can anyone explain the relevance of the CLI?"
date: 2010-03-21
forum: Recurring Discussions
---

### Post by andy1964 on 2010-03-21
Hi
New-ish to Linux. Rather concerned at the almost-obsessive nature of people's love for the CLI.   Why?
I was a long time Windoze user and had not used the DOS or CMD function for many years. Microsoft and Apple seem to manage nicely without them (at least for the end-user).
I move to Linux and find I'm in a time warp. It seems if you want to do anything beyond creating or moving a file/folder, you need to use the CLI - and have to spend hours working out then remembering really odd commands. 
I'm not a programmer (just an end-user) so don't want to spend my time learning code. 
There seems to be a lot to talk about making Linux (esp. Ubuntu) the new choice for Jo Public - but I just keep coming up against CLI. Windoze manages without it, ad so does MAC. Am I mistaken or is Linux still a bit eliteist? 
I not stupid (I have a MSc) and can enter commands verbatim (with a modicum of understanding). When the function does not work, I'm stuck!
I know it's free and so-on - I really support FOSS. Can't we just fade out the CLI except for programmers and hard-core users? 

I await you rage!
Cheers 
Andy

---

### Post by Ozymandias_117 on 2010-03-21
Almost everything you can do in the CLI, you can do in the GUI. But when you ask for help on the forum, we don't necessarily know if you have the a program installed that will allow you to bypass the CLI for your particular problem (And some problems there just isn't any way to fix in the GUI). Because of this, it is usually quicker and simpler to tell people the terminal commands to fix their problem.

---

### Post by Ozymandias_117 on 2010-03-21
Also, from what I've seen/read If you want complete GUI, you may want to try the GNU/Linux distribution Mandriva. It is supposed to be a lot more menu based than Ubuntu. 

Quoting HermanAB > There are various Linux distributions and there should be one for every taste and need. If you want a super easy to use Linux suitable for your Grandma or grandchild, then use Puppy Linux. If you want something like Windows with wizards for everything, where you can go click crazy, use Suse or Mandriva. If you want something intermediate between Mandriva and Slackware, then use Ubuntu.

---

### Post by patchwork on 2010-03-21
There really isn't that much that NEEDS to be done from CLI for most users....but you'll see it listed during troubleshooting methods because:

1.  It's (nearly) universal.  GUIs change between distros, upgrades, desktop managers, etc.  The CLI really doesn't change within a distribution.

2.  It's faster for users who know how to use it.  (One piped command can take the place of 30 seconds of point-click, point-click, point-click)

3.  Learning even the basics of the CLI can lead to a much greater understanding of the filesystem in general.

Although you are not alone in your distaste of the command line, it's flexibility and power is unlikely to make it go the way of the dinosaur.

---

### Post by cascade9 on 2010-03-21
+1 to the above responses. 

BTW, there are a lot of people who use the command line a lot in windows. Not that many 'average users' but a lot of power users do. (and even when you dont use the command line, start-> run "command' can be a lot faster to get to some GUI tools than navigating through the GUI to get them).

---

### Post by 2hot6ft2 on 2010-03-21
+2
Even windows didn't give you a way to get to everything by gui. Point in fact there's no way in windows that I ever found to get to msconfig short of going to start > run > then typing in msconfig and hitting enter. Or editing the windows registry with regedit. That "used" to be the case with ipconfig.

---

### Post by Paddy Landau on 2010-03-21
I would chime in with that. Although I, too, prefer GUI to CLI, nevertheless I often use the CLI simply because it saves time.

However, you're right that there is an element of time-warp, because Linux doesn't have the money behind it that Windows or Mac do; and also because, being FOSS, there is fragmentation (people choose different distributions for personal tastes). Ubuntu is a good choice, but there are others.

In short, there are pros and cons to the Linux approach compared to Windows or Mac.

Still, if you prefer GUI, then when you ask for help, ask if there's a GUI alternative. People will give it if they know of it.

---

### Post by tekkidd on 2010-03-21
well you have to look at what the CLI is. the CLI is the backend of ubuntu it is the core of the heart of the system, if you remove the cli its the equivalent of deleting the windows32 folder in windows. though you may think that the cli is useless it is indeed much needed. doing things in the cli rather than on the desktop adds stability to whatever you are doing. so if i want to transfer a file from a flash drive to the hard disk or update my system and im afraid it might crash the desktop, i do it in the cli because their the system is much more stable. the cli is also vital to diagnosing program errors, so for say if i launch a program and it immediatly crashes then i will go into the terminal and tell it to launch the program so i can see what all goes wrong (and i have fixed programs this way). so getting rid of the cli will involve the complete restructuring of linux itself and all the apps that run on top of it.

---

### Post by quadproc on 2010-03-21
> **patchwork said:**
> There really isn't that much that NEEDS to be done from CLI for most users....but you'll see it listed during troubleshooting methods because:

1.  It's (nearly) universal.  GUIs change between distros, upgrades, desktop managers, etc.  The CLI really doesn't change within a distribution.

2.  It's faster for users who know how to use it.  (One piped command can take the place of 30 seconds of point-click, point-click, point-click)

3.  Learning even the basics of the CLI can lead to a much greater understanding of the filesystem in general.

An excellent and concise reply; kudos to patchwork.

I personally prefer to use the graphic interface for most things but the power, flexibility, and versatility of the CLI are unmatched by the graphic offerings.

Being able to operate in the CLI environment can be a figurative lifesaver.  For example, a while back I was trying to run Ubuntu 8.10 and had two graphics cards in the system.  The version of X windows in that release was unable to decide what to do with two graphics cards so it just gave up and quit executing, leaving me with nothing but CLI.  I was able to browse through logs and figure out the problem, and then I was able to invoke vi (yes, vi!) to insert a workaround into the xorg.conf file so that I could run the system as intended.  Without the CLI I would probably have had to do a fresh install and would have lost all my data.

The CLI certainly has its place.

quadproc

---

### Post by Trandre on 2010-03-21
This post helped me alot on the question:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

And this post:
[http://ubuntuforums.org/showthread.php?t=1434417&highlight=trandre](http://ubuntuforums.org/showthread.php?t=1434417&highlight=trandre)

Trandre

---

### Post by lisati on 2010-03-21
+1 for the previous responses. 
My $0.02: The behind-the-scenes stuff required to run a basic CLI (drivers etc) is less technically demanding than for a GUI.

What happens when your graphics drivers get messed up? If you're lucky, you might be able to use a lower or "incorrect" resolution while you're troubleshooting. However, if you can't use a graphics mode, then what? Since most machines come with generic "text mode" capabilities you'll have something to fall back on.

---

### Post by jflaker on 2010-03-21
I may add...We can likely walk you through a GUI approach to fixing an issue or getting things to the way you like...I must trust that my explanation of what and were and how to click on something was followed concisely, and that my explanation was thorough enough, otherwise you may come back and say we broke your system when in fact you may not have followed the instructions concisely or my instructions were completely not understandable....

TO THAT, if I tell you to type 
```
sudo apt-get install SomeApplication
```

unless you didn't type it correctly, which happens, there is no doubt that you did the command as I typed it for you...especially if i say...open terminal and PASTE this command. 

The CLI is and probably will be alive for some time.  Also, scripting relies on such commands.....

---

### Post by Tom.Gee on 2010-03-21
> **andy1964 said:**
> Hi
New-ish to Linux. Rather concerned at the almost-obsessive nature of people's love for the CLI.   
I await you rage!


No rage here, Andy, but I'll point out that I've been exclusively a Windows user, starting with version 3.1 in the 1990s.  I am using Ubuntu, and Linux in general, for only a week thusfar.  However, less than a hour ago, in the Windows world, in a reply to a gentleman who is providing tech support to me for a broken Windows app, I responded thus: 

[QUOTE=Myself, in an eMail response to tech-support at IDMCOMP earlier today]In fact, I find the ICON problem only in my installation of UltraEdit portable, and I've found it both times, in UE portable 15 and the latest UE 16.  UltraCompare is just fine, and my other Portable Apps are fine.  

>>But the image of Windows 2000 Professional we have in VMWare isn't recognizing the flash drive

You can fool portable apps. easily.  Install it on to the root level of a second virtual harddrive, or just filecopy the entire contents of an installed Portable Apps flash drive over to any empty directory, and SUBST that directory as a root drive letter.  

EXAMPLE: 
Let's assume E: is your Portable Apps flash drive in the real (XP Vista 7) world. 

XCOPY E:\*.* "C:\Shared\PortableAppsFlashdriveContents" /S /E /C /I /H /R /K /Y

In the virtual world be sure you have access to the directory where the contents of the Flash Drive were stored, and issue a SUBST: 

SUBST E: "C:\Shared\PortableAppsFlashdriveContents"

The SUBSTed E: drive in the virtual world should then work the same as the Portable Apps E: Flashdrive did in the real world.  
[/QUOTE]

No Andy-Bashing intended, but the CLI is not exclusive to Linux users.  I cannot imagine the Windows user who doesn't need to be at the command line, if not daily, at least a few times each week.  

The computers we use today have evolved from machines where there was no CLI, to machines that were software reprogrammable and a CLI was the indespensible method to tell a machine what to do and how to do it, to today's most popular machines, where the gesture of a pointer triggers an event that is 99.99% the same as typing in a specific command at a command line.  A click to a hotlink to Ubuntu forums in the Windows GUI basically tells the command interpreter to "LOAD IEXPLORE.EXE and execute the parameter 'http://ubuntuforums.org/showthread.php?p=9004129#post9004129'".  The GUI is really much closer to the surface of the CLI than people realize, thus its ongoing relevance. 

Tom

---

### Post by Zill on 2010-03-21
andy1964:  The CLI provides a very simple and reliable method of quickly providing unambiguous instructions.  As a simple example, if I want to move file "testfile" in my Desktop directory to my home directory I can use the following CLI command:

```
mv ~/Desktop/testfile ~/
```

If I wanted to advise how to do this using a GUI file manager, I would have to write out long and tedious instructions detailing every menu and mouse click involved.  When you consider that this could be done using many versions of numerous different GUI file managers, including Nautilus, Konqueror, Dolphin, Thunar, PCMan etc, the instructions become impossibly complex.

GUI's have their uses, certainly.  But so does the CLI :-)

---

### Post by Girya on 2010-03-21
here's an example why i use the cli. my home folder gets really disorganized after a while, I'm a pig. 

When it gets really bad I'll organize it by creating some new directories and moving files into them then deleting disk hogs like audacity data directories.  I know how to do this in nautilus but it takes several steps: search, select, create folders, move folders to trash, empty trash.

from the command line I just type a one line script and its done. ie:

```
mkdir text_files && mv *.txt text_files; rm -rf *data
```

---

### Post by RedRat on 2010-03-21
> **Girya said:**
> here's an example why i use the cli. my home folder gets really disorganized after a while, I'm a pig. 

When it gets really bad I'll organize it by creating some new directories and moving files into them then deleting disk hogs like audacity data directories.  I know how to do this in nautilus but it takes several steps: search, select, create folders, move folders to trash, empty trash.

from the command line I just type a one line script and its done. ie:

```
mkdir text_files && mv *.txt text_files; rm -rf *data
```

But you can do all that in a GUI, Nautilus if you like or Thunar. Deleting files is as easy as hitting the Delete key. 

Frankly, I too have come from Windows and I started in DOS many eons ago. Yes, there is something kinda neat about the CLI and I do use it in Ubuntu every once and awhile. I have found that there are instances where it is necessary, e.g., if the Windows manager fails for some reason. It is a good idea to be conversant with the CLI, but I will agree that some in the Ubuntu world live and die by the CLI, for them it is a religion. Take it with grain of salt.

---

### Post by andy1964 on 2010-03-21
Thanks RedRat - that's exactly what I was getting at.
Thanks to all the other who replied - I never expected such a response.
I now get it about the CLI - hopefully I won't need it much.
Thanks
Andy

---

### Post by Post Monkeh on 2010-03-21
like said above, most things can be done through the gui, but for someone explaining how to do something on a forum, it's usually much easier to just post the command you need to type into a terminal.

---

### Post by sisco311 on 2010-03-21
> **andy1964 said:**
> Hi
New-ish to Linux. Rather concerned at the almost-obsessive nature of people's love for the CLI.   Why?

Why?

> **andy1964 said:**
> 
I was a long time Windoze user and had not used the DOS or CMD function for many years. Microsoft and Apple seem to manage nicely without them (at least for the end-user).

Please explain, why do you think you have to use the *whatever you mean about DOS or CMD functions*.  

> **andy1964 said:**
> 
I move to Linux and find I'm in a time warp. 


Most of the CLI applications are up to date & under active development. 

> **andy1964 said:**
> 
It seems if you want to do anything beyond creating or moving a file/folder, you need to use the CLI - and have to spend hours working out then remembering really odd commands. 


[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)


> **andy1964 said:**
> 
I'm not a programmer (just an end-user) so don't want to spend my time learning code. 

Running a command has nothing to do with coding.

> **andy1964 said:**
> 
There seems to be a lot to talk about making Linux (esp. Ubuntu) the new choice for Jo Public - but I just keep coming up against CLI. Windoze manages without it, ad so does MAC. Am I mistaken or is Linux still a bit eliteist? 


Whit all the respect, this makes no sense for me. Please elaborate. 

> **andy1964 said:**
> 
I not stupid (I have a MSc) and can enter commands verbatim (with a modicum of understanding). When the function does not work, I'm stuck!
I know it's free and so-on - I really support FOSS. Can't we just fade out the CLI except for programmers and hard-core users? 


Once again, I bag your pardon... what's wrong with the CLI? They/You/We can improve the GUI(s) without eliminating the CLI. 

> **andy1964 said:**
> 
I await you rage!

don't, we are nice people. :) 

> **andy1964 said:**
> 
Cheers 
Andy

Cheers

---

