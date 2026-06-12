---
title: "Just installed, now to customize! (Help would be appreciated)"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by adhuc vivo on 2008-10-15
Hi all!  I'm looking forward to getting started with Ubuntu :-)

I've been on Ubuntu for about a month, so I know the basics of the package manager etc.  However, it was my very first experience with Linux and while I knew it was cool, I didn't really know how to use it and thought that it was somewhat inferior to Windows.  My mentality was basically, *"Oh... it doesn't work?  It must be a Linux thing."*.  However, a couple of my buddies (who I revel as computer gods) convinced me to give Linux another shot (while playing some board games :P).  So I'm hoping for a fresh start learning Linux, the right way.  To give me the mentality (and because I think I screwed up my system before...), I've completely wiped my hard drive and installed Ubuntu, 8.04 LTS.  woot.

Since I really have very little knowledge in terms of what I'm doing, I'm hoping that the Ubuntu community can help me out here.  I've come up with a list of things that I'd like to be able to do with my box.  Also, for most of them I'm not looking for a straight answer, I'm hoping to learn.  

So, if you like to talk about things you know about (most people do), please do go into a long explanation of how Ubuntu works :)!  It'd also be nice if we eventually got to where I wanted to go though :p

These questions really go all over the place, and there's a lot of them.  If you can even answer just one of them, I'd love to chat about it.  So umm... here they are (in no particular order)!

If there are any tutorials that cover this kind of stuff, please link to them!  I'll then work through those and cross off whatever they answer.

1. How easy is it to compile a program from source?  I think I tried that once and it didn't exactly work (I don't fully remember what happened...).  For a lot of the more obscure programs (random games like *Tremulous*, for example) the repository is out of date, and I don't mind updating some of my programs on my own.  Where can I find a good tutorial on compiling / maintaining packages like *Tremulous* or *haXe*?

[COLOR="Red"]**Thanks to jbrown96!  Answer found in [this post](http://ubuntuforums.org/showpost.php?p=5973189&postcount=2)**[/COLOR]


1b. How do I uninstall a program I compiled from source?  e.g., to update it.

[COLOR="Red"]**Thanks to jbrown96!  Answer found in [this post](http://ubuntuforums.org/showpost.php?p=5973189&postcount=2)**[/COLOR]


1c. Open Office 3.0 recently came out.  Will an upgrade from 2.4 eventually make its way to the respository, or should I compile that?

[COLOR="Red"]**Thanks to mc4100!  Answer found in [this post](http://ubuntuforums.org/showpost.php?p=5973938&postcount=22)**[/COLOR]


2. The default theme for Firefox is one integrated with Ubunutu.  That's really cool, but I like the "real" Firefox default better.  i.e., the one that you'll find on pretty much any Windows machine running Firefox.  How can I get this?

[COLOR="Red"]**Thanks to SunnyRabbiera!  Answer found in [this post](http://ubuntuforums.org/showpost.php?p=5973586&postcount=12)**[/COLOR]


3. I've found that it's possible to remove things / move things out of the section of the upper toolbar where the time is displayed.  However, I haven't been able to figure out how to move stuff **to there**.  The little divider acts as a wall when I'm trying to slide things in.

4. How can I install new screen savers, and where's a good place to look for them?

5. When I boot up the computer, it displays a dialog box asking for my username.  When I enter that, it asks for my password.  Is there any way I can use a graphical "point and click" interface for selecting my user?  Kind of like how Windows XP does it (and Fedora, for that matter).

[COLOR="Red"]**Thanks to jbrown96!  Answer found in [this post](http://ubuntuforums.org/showpost.php?p=5973189&postcount=2)**[/COLOR]


6. This one is of little importance.  Kind of like an Easter Egg.  In the top left corner of my GNOME desktop, there's a Ubuntu logo.  How can I change this to say, a penguin?

[COLOR="Red"]**Thanks to Bölvaður!  Answer found in [this post](http://ubuntuforums.org/showpost.php?p=5975942&postcount=28)**[/COLOR]


7. Another real minimal, doesn't matter question.  I've added the "Fish" applet to a GNOME panel.  I've also named it after one of my friends who always has something witty to say.  How can I modify the output so that I can add things she actually would say to the list of items to pull from?

8. Whenever I first start my computer, and it tries to connect to the internet, it looks for a wireless connection.  I don't have a wireless card... how can I change it so that it will default (or even just fall back) to a wired connection?

I really really appreciate all the help.  Let me restate that if you can explain the how's and why's of your answer, please do!  This is a really great forum and you guys are awesome!

Thanks again,
-Eric

---

### Post by jbrown96 on 2008-10-15
Welcome to Ubuntu
>  1. How easy is it to compile a program from source? I think I tried that once and it didn't exactly work (I don't fully remember what happened...). For a lot of the more obscure programs (random games like Tremulous, for example) the repository is out of date, and I don't mind updating some of my programs on my own. Where can I find a good tutorial on compiling / maintaining packages like Tremulous or haXe?

1b. How do I uninstall a program I compiled from source? e.g., to update it. 
To install from source, the same basic steps apply. To install anything you need to install some programs just once, ```
 sudo apt-get install build-essential checkinstall
``` to compile: 1. cd into the directory 2. tar xvf ./file.tar.gz 3. ./configure 4. make 5. sudo make checkinstall Checkinstall is great because you can give the program a custom name, and in the future, remove it like any other: sudo apt-get remove [program]

>  1c. Open Office 3.0 recently came out. Will an upgrade from 2.4 eventually make its way to the respository, or should I compile that?  Ooo usually has .deb packages, which are much easier to install. Just download and open the file, and it will install. 

>  3. I've found that it's possible to remove things / move things out of the section of the upper toolbar where the time is displayed. However, I haven't been able to figure out how to move stuff to there. The little divider acts as a wall when I'm trying to slide things in.  It's actually like the Windows area where the time is. Only certain things can go in there. It's more of a notification window. 

>  4. How can I install new screen savers, and where's a good place to look for them?  Try Synaptic System-->Admin-->Synaptic

>  5. When I boot up the computer, it displays a dialog box asking for my username. When I enter that, it asks for my password. Is there any way I can use a graphical "point and click" interface for selecting my user? Kind of like how Windows XP does it (and Fedora, for that matter).  System-->Admin-->Login Window. Go to local. Try Happy Gnome or Human List. 

Hopefully this gets you started

---

### Post by lametike on 2008-10-15
i can ans ur qns, 1b.
first,go applications -->add/remove appications(like the windows add or remove) and if you know the file name,type it in.if not,browse thought it to find.

---

### Post by SunnyRabbiera on 2008-10-15
This guide mainly applys to recent versions of Ubuntu (Versions 7.10 through 8.10) as I am unsure if Open office 3 will work in older versions of Ubuntu.
Anyhow I will keep this simple:
Step 1: Download open office 3 for debian
2: Extract the zip file
3: In the debs folder move everything you have into the desktop integration folder by selecting as many of the debian insallers you can at a time but there are a whole crap load of them so this might take a while.
4: For normal Ubuntu users install the package nautilus-open-terminal, for Kubuntu and xubuntu users skip this
5: For normal Ubuntu users, restart your computer, for Kubuntu and xubuntu users skip this.
6: Remove as much of open office 2 as you can
7: go into that desktop integration directory and open up a terminal, now how to open your terminal in Ubuntu is by right clicking in the folder and selecting Open terminal.
Kubuntu and xubuntu users should have the open terminal command in the main menu of both Thunar and Dolphin/Konqueror
8: put in the command: sudo dpkg -i *.deb
9: after dpkg is done you may wish to try to install the package openoffice.org3.0-debian-menus_3.0-9354_all located in your desktop integration folder.
10: done

But keep in mind open office 3 doesnt offer too much over open office 2 other then .docx support and a few other minor features... its not like its a security update or anything.

---

### Post by jbrown96 on 2008-10-15
> **lametike said:**
> i can ans ur qns, 1b.
first,go applications -->add/remove appications(like the windows add or remove) and if you know the file name,type it in.if not,browse thought it to find.
This will not uninstall programs that were compiled. There are only two ways: keep track of every file that is installed and then delete them or use checkinstall.

---

### Post by Hendrixski on 2008-10-15
> **adhuc vivo said:**
> 
I'm hoping that the Ubuntu community can help me out here.  I've come up with a list of things that I'd like to be able to do with my box.  Also, for most of them I'm not looking for a straight answer, I'm hoping to learn.  


You've come to the right place. We're one of the nicest communities on the web.

> **adhuc vivo said:**
> 
1. How easy is it to compile a program from source?

Just compiling is straightforward, you learn a few commands, or you get an IDE like Eclipse to compile it for you. But I wouldn't recommend it unless you're learning how to program, in which case, I HIGHLY recommend it. But if you just want to install programs, use synaptic (or apt-get)

> **adhuc vivo said:**
> 

5. When I boot up the computer, it displays a dialog box asking for my username.  When I enter that, it asks for my password.  Is there any way I can use a graphical "point and click" interface for selecting my user?  Kind of like how Windows XP does it (and Fedora, for that matter).


Yes. you can also set it to just automatically boot up to your preferred account.

---

### Post by adhuc vivo on 2008-10-15
[quote=jbrown96]
 Ooo usually has .deb packages, which are much easier to install. Just download and open the file, and it will install.
[/quote]

Will this be brought to the Ubuntu package manager / will it update with my software updates (since this is a big jump)?  If so, I don't see much point in mucking with it.

[quote=jbrown96]
It's actually like the Windows area where the time is. Only certain things can go in there. It's more of a notification window. 
[/quote]

Hmm... there's got to be another way.  Especially since we have the source code in front of us, it should be doable.  Does anybody know how?

~~~

1, 1b, and 5 have been resolved.  I'm very happy with my new login screen, I'm logging out just so I can see it again :lolflag:

Thanks guys, I hope somebody can help me out with the rest!

---

### Post by SunnyRabbiera on 2008-10-15
> **adhuc vivo said:**
> Will this be brought to the Ubuntu package manager / will it update with my software updates (since this is a big jump)?  If so, I don't see much point in mucking with it.


I would not worry about it, people use software outside of the repositories all the time.
Just remember that if you install open office 3 manually its up to you to maintain it like you would do on windows.

---

### Post by adhuc vivo on 2008-10-15
Okay, thanks!

---

### Post by kukibird1 on 2008-10-15
2. The default theme for Firefox is one integrated with Ubunutu.  That's really cool, but I like the "real" Firefox default better.  i.e., the one that you'll find on pretty much any Windows machine running Firefox.  How can I get this?


Go to Tools > Add-ons > Extensions disable Ubuntu Firefox Modifications.

---

### Post by adhuc vivo on 2008-10-15
That's what I thought would do it, but alas... no.  I think that the actual theme files aren't included in Ubuntu.

But that brings up an interesting question.  What exactly do those Firefox Mods do?

---

### Post by SunnyRabbiera on 2008-10-15
as for your other things:
> 2. The default theme for Firefox is one integrated with Ubunutu. That's really cool, but I like the "real" Firefox default better. i.e., the one that you'll find on pretty much any Windows machine running Firefox. How can I get this?

You mean the strata theme, this theme has not been made on linux as the mozilla team elected to make sure firefox looks good nativly in linux as opposed to just slapping on the same exact theme.
There were rumors that the strata theme would come to linux sooner or later but so far nothing.
but you can go to the mailla add ons site and search for other themes that might suit your tastes.
But to be honest there is no true theme for firefox 3 as its intended to be flexible for the OS its in.

> 3. I've found that it's possible to remove things / move things out of the section of the upper toolbar where the time is displayed. However, I haven't been able to figure out how to move stuff to there. The little divider acts as a wall when I'm trying to slide things in.
Well you may wish to unlock certain panel applications by right clicking and deselecting "lock to panel"

---

### Post by kukibird1 on 2008-10-15
> **adhuc vivo said:**
> That's what I thought would do it, but alas... no.  I think that the actual theme files aren't included in Ubuntu.

But that brings up an interesting question.  What exactly do those Firefox Mods do?


[http://ubuntuforums.org/showthread.php?t=826536]("http://ubuntuforums.org/showthread.php?t=826536")

[http://linuxhack3r.com/2008/04/05/apturl-in-ubuntu/]("http://linuxhack3r.com/2008/04/05/apturl-in-ubuntu/")

---

### Post by adhuc vivo on 2008-10-15
> 
You mean the strata theme, this theme has not been made on linux as the mozilla team elected to make sure firefox looks good nativly in linux as opposed to just slapping on the same exact theme.


Thanks for that tidbit.  A quick search for "strata" in the themes revealed these user generated ones:

[https://addons.mozilla.org/en-US/firefox/addon/8105](https://addons.mozilla.org/en-US/firefox/addon/8105)
[https://addons.mozilla.org/en-US/firefox/addon/7390](https://addons.mozilla.org/en-US/firefox/addon/7390)

> 
Well you may wish to unlock certain panel applications by right clicking and deselecting "lock to panel"


What I'm referring to here is the peculiar behavior that results after I unlock the buttons and start moving them around.  I'm more than welcome to move anything **out of** that upper right hand panel (to the right of the dot bar).  However, when I'm trying to put something **into** that panel, it simply won't go in.  I cannot right click and press "Add to panel" either.

---

### Post by trikster_x on 2008-10-15
> 3. I've found that it's possible to remove things / move things out of the section of the upper toolbar where the time is displayed. However, I haven't been able to figure out how to move stuff to there. The little divider acts as a wall when I'm trying to slide things in.


All you need to do is right click on the seperator bar and deselect lock to panel.  Then when you want to put something in that section of the panel, it will automatically move over.  You may have to unlock everything on the panel to place things exactly where you want them. And instead of drag and dropping, right click and select move after an item is unlocked.  Then you can see exactly where it will go.  Once you are done with that Lock all your panel items again so they don't move on restart(just a small problem I have noticed with my panel).  Here's a screenshot of my desktop to give you an idea of what it could look like.  Experiment with compiz and emerald and the screenlets and have fun.

Edit: You may even need to move the seperator yourself after you unlock it.

---

### Post by trikster_x on 2008-10-15
> 8. Whenever I first start my computer, and it tries to connect to the internet, it looks for a wireless connection. I don't have a wireless card... how can I change it so that it will default (or even just fall back) to a wired connection?

Right click on the network connection icon and deselect enable wireless.

---

### Post by bluebook on 2008-10-15
I'm also a newbie and wanting to customize Ubuntu ... I hope you don't mind if I ask another question on your thread ...

How do you download different "themes" for the desktop/environment?

thanks!

:KS

---

### Post by trikster_x on 2008-10-15
> 7. Another real minimal, doesn't matter question. I've added the "Fish" applet to a GNOME panel. I've also named it after one of my friends who always has something witty to say. How can I modify the output so that I can add things she actually would say to the list of items to pull from?


Which fish screenlet?  If I can add it to my program, I may be able to help with this.

---

### Post by adhuc vivo on 2008-10-15
> **trikster_x said:**
> All you need to do is right click on the seperator bar and deselect lock to panel.  Then when you want to put something in that section of the panel, it will automatically move over.  

Hmm... the network icon looks to be "stuck" to the separating bar.  I was hoping to remove my username between them.

> **trikster_x said:**
> Right click on the network connection icon and deselect enable wireless.

I have to uncheck "Enable Networking".  Which disables my ethernet too.

> **bluebook said:**
> I'm also a newbie and wanting to customize Ubuntu ... I hope you don't mind if I ask another question on your thread ...


That's why I'm putting the answers up front while I find them :)

> **trikster_x said:**
> Which fish screenlet?  If I can add it to my program, I may be able to help with this.

For the GNOME desktop, right click and press "Add to panel".  I'm referring to "Fish" under that menu.

---

### Post by trikster_x on 2008-10-15
Unfortunately, that is what that little seperator is for.  If you really don't want it there, just remove it from your panel.  The network connect icon, update icon and various other program daemons will not show up because the seperator is actually the notification area.  You can manually add the connection icon, but the update and any other icons will not show up.  I just left mine in because once I started playing with my panels, I found ways to utilize the bottom panel, and still be able to easily switch between windows.

---

### Post by trikster_x on 2008-10-15
That's odd that you have to deselect networking, because I just disabled my wireless and it left my networking checked.  Maybe a glitch in you install?

---

### Post by mc4100 on 2008-10-15
To answer 1c, Openoffice.org 3 will indeed be made available in a repository for easy updating. It will be in the backports (which can be 
activated in System -> Administration -> Software Sources. Check the box for "Unsupported Updates" in the updates tab). Probably should be uploaded in about a month.

---

### Post by trikster_x on 2008-10-15
Okay. I found the file where all those nifty fortunes are kept, unfortunately, all of my attempts to modify it caused there to be no output.  I attempted to make a small python program, but that didn't work either.  Looks like adding your own phrases is something that may be pretty involved.  Sorry.

---

### Post by adhuc vivo on 2008-10-16
> **mc4100 said:**
> To answer 1c, Openoffice.org 3 will indeed be made available in a repository for easy updating. It will be in the backports (which can be 
activated in System -> Administration -> Software Sources. Check the box for "Unsupported Updates" in the updates tab). Probably should be uploaded in about a month.

Thanks, that's done.

> **trikster_x said:**
> Okay. I found the file where all those nifty fortunes are kept, unfortunately, all of my attempts to modify it caused there to be no output.  I attempted to make a small python program, but that didn't work either.  Looks like adding your own phrases is something that may be pretty involved.  Sorry.

Thanks for trying, I wouldn't have gotten that far :)

---

### Post by aktiwers on 2008-10-16
> 
3. I've found that it's possible to remove things / move things out of the section of the upper toolbar where the time is displayed. However, I haven't been able to figure out how to move stuff **to there**.  The little divider acts as a wall when I'm trying to slide things in.

Are you talking about the system tray? Because then the program need to have the feature "minimize to tray".

If you are talking about the panel only, just drag/drop items ind there or click "add to panel". You can drag (unlucked) items around with middleclick on your mouse or by rightclick => move.

---

### Post by adhuc vivo on 2008-10-16
Yes, I believe I am talking about the system tray.  That would make sense.

My objective here would be to move the thing that says my name (the user switcher?) from right next to the tray into the tray.  Any way that this is possible?

---

### Post by rick08 on 2008-10-16
Go to [http://www.gnome-look.org/](http://www.gnome-look.org/) to change anything appearance wise, such as, cursors, themes, wallpapers, cairo themes, screensavers, etc.

---

### Post by Bölvaður on 2008-10-16
> **adhuc vivo said:**
> 
6. This one is of little importance.  Kind of like an Easter Egg.  In the top left corner of my GNOME desktop, there's a Ubuntu logo.  How can I change this to say, a penguin?

8. Whenever I first start my computer, and it tries to connect to the internet, it looks for a wireless connection.  I don't have a wireless card... how can I change it so that it will default (or even just fall back) to a wired connection
6.
/usr/share/icons/Human/24x24/places/distributor-logo.png
remember to take backup of this file and replace it under super user.

8. disable wireless

---

### Post by adhuc vivo on 2008-10-16
8. Sounds good, but how do I do that?

---

### Post by adhuc vivo on 2008-10-17
24 hour bump :)

---

### Post by WWSmith36 on 2008-10-17
> Yes, I believe I am talking about the system tray. That would make sense.

My objective here would be to move the thing that says my name (the user switcher?) from right next to the tray into the tray. Any way that this is possible?

If you are trying get to something to minimize to systray rather than taskbar, try a little program called kdocker.

```
# sudo apt-get install kdocker
```

Then you can used it by kdocker <program-name>, for example to run evolution mail and have it minimize to the tray.

```
# kdocker evolution --component=mail
```

Hope this help

---

### Post by adhuc vivo on 2008-10-17
Hey cool thanks!

Is there a way I can do something like [this](http://img236.imageshack.us/img236/2974/screenshoteh5.png)?  (*hopes you can tell by the picture*)

---

### Post by aktiwers on 2008-10-17
What do you waant to do?

---

