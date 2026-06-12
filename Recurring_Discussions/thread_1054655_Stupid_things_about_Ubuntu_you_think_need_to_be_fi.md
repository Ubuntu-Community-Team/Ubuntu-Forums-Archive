---
title: "Stupid things about Ubuntu you think need to be fixed"
date: 2009-01-29
forum: Recurring Discussions
---

### Post by diablo75 on 2009-01-29
So I had one heck of a time today trying to share a printer from one PC to another, both running Ubuntu.  So much so that I decided to reinstall Ubuntu.

On the PC which the Printer is actually attached, I installed it, and shared it using the options checked off in the attached screenshot.  But upon clicking OK I get another picture (see another attached screen shot).

The reason I'm posting about this:

1.  New users will see this and follow the on screen directions to find they've been misguided.  Because on a default install, there is no "Administration>Settings>Firewall".

2.  It suggests accessing and editing firewall settings?  Editing them to what end?  What ports need to be opened?  It does not say.

So... this is just one tiny little rant that I think is very valid.

---

### Post by swoll1980 on 2009-01-29
Yeah that's a little crazy. Did you file a bug report?

---

### Post by RPG Master on 2009-01-29
I can't use anyother theme besides shiki-colors with compiz without weird stuff hapening to the window borders. I kinda miss using Dust and Human...

---

### Post by Skripka on 2009-01-29
Stupid things?


How about native FRIGGIN multi-button mouse support?!!??

PS-Can anyone tell I'm p*ssed that this still has yet to happen?

---

### Post by MasterNetra on 2009-01-29
I would like to see Ubuntu rotate the taskbar image for Vertical taskbars?(Or at least have the option for Ubuntu to do that) You would think this would be a easy thing to do. (at least compare to the stuff they usually do)

---

### Post by cariboo on 2009-01-29
Most of the things you are complaining about are not Ubuntu specific, the adjust firewall message is definitely a bug, please report it using [Launchpad]("http:///bugs.launchpad.net/").
I've never seen that before, but then I use the cups web interface to setup and share printers. You can access the cups interface using firefox and [http://localhost:631](http://localhost:631).

> I can't use anyother theme besides shiki-colors with compiz without weird stuff hapening to the window borders. I kinda miss using Dust and Human...


Human is still installed by default, and you can get dust and a few more by installing the community-themes package.

> How about native FRIGGIN multi-button mouse support?!!??

Jaunty has a graphical utility called btnx that does exacty what you are waiting for.

Jim

---

### Post by swoll1980 on 2009-01-30
> **RPG Master said:**
> I can't use anyother theme besides shiki-colors with compiz without weird stuff hapening to the window borders. I kinda miss using Dust and Human...

Are you using nvidia driver 177? if so upgrade to 180xx I had the same problem this fixed it [click here]("apt:nvidia-glx-180") to install

---

### Post by Skripka on 2009-01-30
> **cariboo907 said:**
> 

Jaunty has a graphical utility called btnx that does exacty what you are waiting for.

Jim

To be blunt.  I don't believe you.

As of September 2008 all development of BTNX halted.  Because the new Xorg 7.4 broke (included with Intrepid Ibex)all the hacks that make btnx work.

[http://www.ollisalonen.com/btnx/](http://www.ollisalonen.com/btnx/)

Unless Jaunty is using an outdated Xorg-it isn't using BTNX...unless someone else has taken up development of BTNX.

 If it actually is working again, I'll be pleased--but fer cripes sake, btnx functionality should have been integrated WAY back.  WAY back.  It shouldn't be a 3rd party hack to work.

---

### Post by jimrz on 2009-01-30
> **diablo75 said:**
> So I had one heck of a time today trying to share a printer from one PC to another, both running Ubuntu.  So much so that I decided to reinstall Ubuntu.

On the PC which the Printer is actually attached, I installed it, and shared it using the options checked off in the attached screenshot.  But upon clicking OK I get another picture (see another attached screen shot).

The reason I'm posting about this:

1.  New users will see this and follow the on screen directions to find they've been misguided.  Because on a default install, there is no "Administration>Settings>Firewall".

2.  It suggests accessing and editing firewall settings?  Editing them to what end?  What ports need to be opened?  It does not say.

So... this is just one tiny little rant that I think is very valid.

what happens if you check "allow printing from the internet" and the click the "refresh" button?

---

### Post by lisati on 2009-01-30
> **Skripka said:**
> Stupid things?


How about native FRIGGIN multi-button mouse support?!!??

PS-Can anyone tell I'm p*ssed that this still has yet to happen?

My three-button mouse works well.....

(ooops I'm currently using Vista, but don't recall any problems with any of the Ubuntu installs I've done.....)

---

### Post by swoll1980 on 2009-01-30
> **Skripka said:**
> 
PS-Can anyone tell I'm p*ssed that this still has yet to happen?

Who are you pissed at?

---

### Post by Skripka on 2009-01-30
> **lisati said:**
> My three-button mouse works well.....

(ooops I'm currently using Vista, but don't recall any problems with any of the Ubuntu installs I've done.....)

I have a mouse with a total of 6 buttons, and 2 scroll wheels...it would be nice if more than only 2 buttons and one scroll wheel worked again (they did under btnx in Hardy...which btnx doesn't exist anymore-unless someone else is deeveloping the code).

---

### Post by lisati on 2009-01-30
> **Skripka said:**
> I have a mouse with a total of 6 buttons, and 2 scroll wheels...it would be nice if more than only 2 buttons and one scroll wheel worked again (they did under btnx in Hardy...which btnx doesn't exist anymore-unless someone else is deeveloping the code).

Aaah, I see. I don't have any experience with anything over and above the two-button + combined scroll-wheel/third button, so I'm unable to help here.....

---

### Post by Skripka on 2009-01-30
> **swoll1980 said:**
> Who are you pissed at?

The kind folks at Ubuntu for starters...who apparently believe there's no one uses anything more than a 2 button mouse.  Getting a multi button mouse to work shouldn't require 3rd party hacks (which break easily).

---

### Post by swoll1980 on 2009-01-30
> **Skripka said:**
> The kind folks at Ubuntu for starters...who apparently believe there's no one uses anything more than a 2 button mouse.  Getting a multi button mouse to work shouldn't require 3rd party hacks (which break easily).

Not to sound ignorant or anything, which I probably do anyways, but what do you use all those buttons for?

---

### Post by Skripka on 2009-01-30
> **swoll1980 said:**
> Not to sound ignorant or anything, which I probably do anyways, but what do you use all those buttons for?

No problem :)

This Mouse:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16826104015](http://www.newegg.com/Product/Product.aspx?Item=N82E16826104015)
(The call it 7 button+2 wheel...it is really 6...the 7th is a neat clutch on the scroll wheel)


What works:
-Left Click
-Right Click
-Scroll-wheel 1 (up/down and side scrolling

What doesn't work:
-Back button (for web browsing)
-Forward button (for web browsing)
-Search button (never worked under btnx)
-Scroll wheel 2-Click button (for present desktops effect)
-Scroll wheel 2 (for easy Alt-Tabing between apps)

Everything just goes faster--and there's no need to go hunting and clicking icons.  Especially if your multitasking between several web-browser windows, a few PDFs, and a OO.org document....and in my graduate work-I often find myself doing this

Yes I'm lazy.  But many mice now have back/forward button functionality-this is a minimum. 


Oh, well enough of my ranting.  I'm in a mood as a result of paper shuffling tonight.

---

### Post by swoll1980 on 2009-01-30
> **Skripka said:**
> No problem :)

This Mouse:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16826104015](http://www.newegg.com/Product/Product.aspx?Item=N82E16826104015)
(The call it 7 button+2 wheel...it is really 6...the 7th is a neat clutch on the scroll wheel)


What works:
-Left Click
-Right Click
-Scroll-wheel 1 (up/down and side scrolling

What doesn't work:
-Back button (for web browsing)
-Forward button (for web browsing)
-Search button (never worked under btnx)
-Scroll wheel 2-Click button (for present desktops effect)
-Scroll wheel 2 (for easy Alt-Tabing between apps)

Everything just goes faster--and there's no need to go hunting and clicking icons.  Especially if your multitasking between several web-browser windows, a few PDFs, and a OO.org document....and in my graduate work-I often find myself doing this

Yes I'm lazy.  But many mice now have back/forward button functionality-this is a minimum. 


Oh, well enough of my ranting.  I'm in a mood as a result of paper shuffling tonight.

Cool! I didn't even know they had mice that did all that stuff. I'll have to check it out next time I'm at Micro Center

---

### Post by jrusso2 on 2009-01-30
I don't see btnx in the Hardy Repos.

---

### Post by earthpigg on 2009-01-30
> Stupid things about Ubuntu you think need to be fixed 

-i still can't keep track of what is in system->pref and system->admin. there doesn't seem to be any common pattern.

-things that must be run as root not automatically being added to the menus as such. nvidia-settings, for example, is essentially a useless menu entry... and it doesn't even tell you this. it starts and you THINK you are changing settings... but then (if you are a new user, as i was) none of it actually saves, and there is no indication as to why... confusing.

-there should be an "i chose to diregard the philosophical issues about FLOSS and linux" button that installs ubuntu-restricted-extras, region-coded dvd support, etc.

-put ubuntu-tweak in the repos

-when NTFS-partitioned media that was not properly removed last time is put in, put a point-n-click way to force mount in front of you that asks you for your password and then does it.

-multi monitor support. when i unplug my laptop from the 2nd monitor, it should realize the 2nd monitor is not there next time i boot up instead of putting my gnome panel over there where i cant get to it...



that being said, i <3 ubuntu and appreciate the hard work that folks have put into it.

---

### Post by shatteredmindofbob on 2009-01-30
Are...are you asking for a list? Because...I can give you one. 

1. PulseAudio - Seriously...wtf?!? I know..not very constructive, but I'm reasonably sure a good number of the people on forum know what I'm trying to articulate. 

2. Compiz - I've heard this is being worked on, so maybe it won't be a problem come Jaunty, but really Compiz Fusion either needs to get fixed or it needs to go. It's insane how many times either I post or I see someone else post a problem on the forums and see the first reply: "Oh, that's a Compiz bug, disable it and it will work." Again - WTF?!? I've managed to make my Ubuntu experience a fair bit better by disabling it...but a fair bit worse as well since I don't have Compiz running anymore. 

and well...there are many many more, but I'll try not to hijack to thread, especially some of the things I think need to be changed would require a fundamental change in the way Linux works in general...

---

### Post by diablo75 on 2009-01-30
I have no fear of seeing the thread "hijacked".  I wouldn't mind seeing it become a melting pot for complaints.  I would regret to see anyone really shy away from watching "flaws" be voiced.  The flaw I posted about is obviously on the OS.  A few others here are as well.  Some... well... see, this is where things start to look like kids fighting in elementary school where there's a lot of finger pointing and little compromise.

If Ubuntu wants to be popular, it needs to be non-technical for most tasks.  The thing that I think Ubuntu has does best at thus far is cutting into the resistance that is the obsessive-compulsive linux user, who is strict, stubborn, loves typeing his password left and right, editing text files filled with jargon that nobody but he understands, and so on.  Ubuntu seems to try and automate this type of mentality and boil it down to a simple password entry, which is a great way to tackle otherwise difficult to understand tasks (like sharing a freaking printer or a folder with another computer; but it's still not perfect).

How many of you out there have used a Mac?  I've barely used one.  I have a friend who's used one for nearly his whole life.  He recently lost his Mac due to a hardware failure, and replaced it with a Vista laptop (letting me install Ubuntu along side it).  It is no mystery to me why he's chosen to use Windows instead of Ubuntu.  Figuring the mystery out is the point of this thread.  There is too much out there that is just plain "stupid" that just needs to be fixed before it will ever be able to compete in the real world, if it is actually intended to become the next big mainstream OS.  If it isn't, if the user base out there thinks it's destined to become and remain the "awesome" OS that it is right now and remain hidden in the shadows of mediocrity because it takes some kind of "guru" to keep it working from day to day... it makes most wonder if it's worth wasting their time with.

---

### Post by MindFlayer on 2009-01-30
> **shatteredmindofbob said:**
> 
1. Pulseaudio - seriously...wtf?!? I know..not very constructive, but i'm reasonably sure a good number of the people on forum know what i'm trying to articulate. 


+1. :-\"

---

### Post by diablo75 on 2009-01-30
Here's another.  And I post this honestly not knowing who to blame... Ubuntu, or Firefox.

When I click on a link to a *.pls file (otherwise known as a "Shoutcast MP3 playlist") It presents the attached screenshot.

Lets say I don't want it to open it with Totem.  Instead, I'd like it to play in VLC, (or XMMS for those die hard XMMS fans out there).  So I click on the drop down where "Movie Player" is currently shown, and select "Other..." because NOTHING ELSE IS THERE.

Instead of being presented with a nice listing of installed applications, I'm asked to browse my root file structure.  I, after 3 years of using this OS, still have little idea as to where I should even look to find VLC or any other app for that matter.  New users, I would bet hard cash, HATE THIS.  Sorry.

Edit:  Before anyone tells me "how to do this"  I shouldn't have to be told.  If I click "Other..." I **shouldn't** have to see the file structure.  I should be given a listing of installed apps to pick from.  Simple, clean.

---

### Post by RaZe42 on 2009-01-30
> **Skripka said:**
> No problem :)

This Mouse:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16826104015](http://www.newegg.com/Product/Product.aspx?Item=N82E16826104015)
(The call it 7 button+2 wheel...it is really 6...the 7th is a neat clutch on the scroll wheel)


What works:
-Left Click
-Right Click
-Scroll-wheel 1 (up/down and side scrolling

What doesn't work:
-Back button (for web browsing)
-Forward button (for web browsing)
-Search button (never worked under btnx)
-Scroll wheel 2-Click button (for present desktops effect)
-Scroll wheel 2 (for easy Alt-Tabing between apps)

Everything just goes faster--and there's no need to go hunting and clicking icons.  Especially if your multitasking between several web-browser windows, a few PDFs, and a OO.org document....and in my graduate work-I often find myself doing this

Yes I'm lazy.  But many mice now have back/forward button functionality-this is a minimum. 


Oh, well enough of my ranting.  I'm in a mood as a result of paper shuffling tonight.

I've got the exact same mouse, and forward/back works in Firefox out of the box, but not in Nautilus.

The search button(out of the box) opens Tracker(is that what it's called?)

If you use compiz, then the second "scroll" wheel is easy to assign to a compiz action.
Just manually edit the CCSM shortcuts:
push forward: Button13
push backward: Button15
push down: Button17

to configure the "microgear" scrolling(when frictionless goes on)
there's a small application called "revoco". There's a thread about it somewhere here on the forums:D

EDIT: I'm using intrepid

---

### Post by Skripka on 2009-01-30
> **RaZe42 said:**
> I've got the exact same mouse, and forward/back works in Firefox out of the box, but not in Nautilus.

The search button(out of the box) opens Tracker(is that what it's called?)

If you use compiz, then the second "scroll" wheel is easy to assign to a compiz action.
Just manually edit the CCSM shortcuts:
push forward: Button13
push backward: Button15
push down: Button17

to configure the "microgear" scrolling(when frictionless goes on)
there's a small application called "revoco". There's a thread about it somewhere here on the forums:D

EDIT: I'm using intrepid

[I have a thread, still unanswered in General Help]("http://ubuntuforums.org/showthread.php?t=1052573")-as to why B/F works in Firefox but nowhere else....and I'd rather use any browser other than Firefox (it is slow, and looks terrible in KDE).

I'll give revoco a try....

EDIT-Yay it works again, finally...If our Thanks! feature was implemented again-I'd give it to you...but for now Thanks!

PS_doesn't change my criticism that it shouldn't be a 3rd party hack ;)

---

### Post by daynah on 2009-01-30
Can I just second the mouse thing? I have a logitech multimedia mouse that has even more buttons (volume up/down, fast forward/back, play/pause) and it's really silly that I can't just go into a program and click on what needs to be what. Here's a way to set this up that would be simple from the user's end:

Have a screen that would have the names of basic commands:
Main click (what is usually called "left click")
Secondary click (what is usually called "Right click")
Scroll up
Scroll down
Play
Volume Up
Volume down
ect...

Then you click on it (according to however your mouse is set at that time) and a screen will pop up saying something like "Click the button on your mouse that you want to assign to this command." And then you click, and everything's done and set and magical.

But it's not. There's crazy combinations of letters and my mouse has too many buttons for the computer's tiny little brain to even be able to comprehend without compiling a kernel with some code form a project that hasn't been updated in years!

I'm usually okay about this until someone walks into my room, sees my intimidating mouse and goes "What do these buttons do?" and starts pressing them and I get the pleasure of answering...

Nothing. They do absolutely nothing.

---

### Post by Polygon on 2009-01-30
pulseaudio is fine. yes its buggy, but its better for everything in the long run that we switch to pulseaudio rather then stay with alsa.

also, the fast user switch applet. No, i do not need two things telling me my pidgin status. I would also like the old behavior of having it bring up a big window in the middle of the possible actions (shutdown, restart) rather then the tiny little list that they have now.

---

### Post by zakany on 2009-01-30
Setting resolution and refresh rate should include at least one valid pick. Using the wrong refresh rate on my cheapie LCD turns it off. Kinda hard to repair that when you can't see the screen!

If I didn't have a spare CRT sitting around, I'd have been unable to use Ubuntu. Period.

Took me an hour to fix that problem because Ubuntu wouldn't save the settings from the Nvidia control panel. I had to sudo into the Nvidia controls via terminal. There was no feedback that my settings were not being saved.

--

PS: I find this odd: "pulseaudio is fine. yes its buggy." buggy != fine

---

### Post by GrouchoMarx on 2009-01-30
This is really more of a kernel issue, but most of the problems mentioned so far are really insignificant when compared to power management and battery life. Specifically, on my platform I get 9 hours of battery life in Vista, compared to 3.5 hours in Ubuntu on an Intel computer. Also the fan runs constantly in Ubuntu, regardless of temperature, whereas it hardly ever runs in Vista. Note that Intel releases open source drivers for their chipsets, so this isn't really a closed-source driver issue. Yes it's newer hardware, and it usually takes time to sort out all the kinks, but I have never heard of or seen power consumption in Linux being anywhere near what it is in Windows.

No, it's not Ubuntu's "fault", but the GUI, theme, and icons are really insignificant problems in comparison, and if I could make one wish, it would be to fix power management in Linux.

---

### Post by Sceiron on 2009-01-30
> **masternetra said:**
> i would like to see ubuntu rotate the taskbar image for vertical taskbars?(or at least have the option for ubuntu to do that) you would think this would be a easy thing to do. (at least compare to the stuff they usually do)

+1

---

### Post by uberdonkey5 on 2009-01-30
PULSE AUDIO! +1
Why did I bother upgrading to intrepid? I have a very busy day, my upgrade wiped off skype, installed pulse audio (which stops my microphone working properly) and the repositories are not working.

Intrepid should not have been released in this condition. Makes me wonder how bad Jaunty is gonna be. When I get home tonight I'm gonna go back to hardy. What a waste of time!

---

### Post by Skripka on 2009-01-30
> **MasterNetra said:**
> I would like to see Ubuntu rotate the taskbar image for Vertical taskbars?(Or at least have the option for Ubuntu to do that) You would think this would be a easy thing to do. (at least compare to the stuff they usually do)

I've never seen a OS or distro which does a good job with vertical toolbars....perhaps my memory is failing and there was one back Pre-Win3.1

---

### Post by Mr. Picklesworth on 2009-01-30
> **diablo75 said:**
> Here's another.  And I post this honestly not knowing who to blame... Ubuntu, or Firefox.

When I click on a link to a *.pls file (otherwise known as a "Shoutcast MP3 playlist") It presents the attached screenshot.

Lets say I don't want it to open it with Totem.  Instead, I'd like it to play in VLC, (or XMMS for those die hard XMMS fans out there).  So I click on the drop down where "Movie Player" is currently shown, and select "Other..." because NOTHING ELSE IS THERE.

Instead of being presented with a nice listing of installed applications, I'm asked to browse my root file structure.  I, after 3 years of using this OS, still have little idea as to where I should even look to find VLC or any other app for that matter.  New users, I would bet hard cash, HATE THIS.  Sorry.

Edit:  Before anyone tells me "how to do this"  I shouldn't have to be told.  If I click "Other..." I **shouldn't** have to see the file structure.  I should be given a listing of installed apps to pick from.  Simple, clean.

The problem there is Firefox, because it is built entirely for the Windows ecosystem with Linux (especially GNOME) as a quiet afterthought. It tends to ignore the presence of completely adequate widgets for certain jobs, as well as existing desktop-wide settings like default handlers for file types. It's still a good browser, but it isn't user friendly as a result. That screenshot of yours is exactly why I keep saying Ubuntu should use Epiphany by default.

---

### Post by diablo75 on 2009-01-30
Here's another one (although this doesn't land so much on Ubuntu's shoulders as it does Amarok's... or does it?)

Amarok, hailed as the top dog of music management and streaming radio stations, comes LOADED with radio stations in it's playlist that won't play "out of the box".  (See screenshot).  For instance, if you open up the "Cool Stations" channel filter, which has something like 30 "Favorite" "Cool" radio stations, and double-click on one, it doesn't want to play.  How cool is that?

What's worse is the error message that is produced gives you absolutely no useful information.  Not even a hint as to how to fix the problem or even an offer to fix it all on it's own via a nifty "Download the missing codec" button, which Totem actually does do on it's own in some instances.

Bare in mind this problem persists even if you have Restricted Extras installed.  The exact same radio station will play in VLC or Totem, but not in Amarok?  New users will see this "stupid" stuff and go, "Hmmm... What good is this???"  And likely never use it again.  "Do you use Amarok?"  "No, why the hell would I?  It doesn't do anything cool."

(Don't worry, I'm going to CC this to the Amarok devs and see who they want to pass the buck off to).

---

### Post by swoll1980 on 2009-01-30
You Guys need to make sure to file bug reports on all these problems, The devs don't troll forums looking for bugs they go to lauchpad I'm sure, or the reports get e-mailed to them maybe, either wayu if you want the problems to get fixed you have to file bug reports.

---

### Post by Johnsie on 2009-01-30
The software in the repositories is often outdated. For example, Amarok 2 is out sou why do the repos only have 1.4?

I guess thats what you get for letting a company control what software you can use.

---

### Post by Skripka on 2009-01-30
> **Johnsie said:**
> The software in the repositories is often outdated. For example, Amarok 2 is out sou why do the repos only have 1.4?

I guess thats what you get for letting a company control what software you can use.

No...It is long time Ubuntu policy, that newer versions of software released after a distro release can only be gotten through backports or PPAs for that distro release--as a measure to ensure greatest stability and compatibility.

---

### Post by SpenceMakesSense on 2009-01-30
I'm not sure if its just me but whenever I set up a second x server on a second screen my first x server goes ape sh** whenever the computer is prompted to system beep. Seems like a strange error but I posted a thread with no help so I guess Ill wait to see how jaunty handles it.

---

### Post by estyles on 2009-01-30
> **diablo75 said:**
> Here's another.  And I post this honestly not knowing who to blame... Ubuntu, or Firefox.

Instead of being presented with a nice listing of installed applications, I'm asked to browse my root file structure.  I, after 3 years of using this OS, still have little idea as to where I should even look to find VLC or any other app for that matter.  New users, I would bet hard cash, HATE THIS.  Sorry.

Normally, with this kind of complaint, I'd be the first to say something like, "all you have to do is this... it's not hard, quit complaining."  However....  you're absolutely right.  A list of installed applications is readily available, and not showing that is crazy.  Also acceptable (though not perfect) would be to just type in the name of the application...  I want to use vlc, I type in vlc - it works for launchers, but firefox can't figure it out?  Silly.  Of course, it's not an Ubuntu-specific problem, but it is very annoying.  Searching through the root file system is something that Unix/Linux mostly discourage.  If it's not in /home/user/, then the average user shouldn't be expected to find it...  even for /bin and /usr/bin/.

Other complaints:

1) Pulseaudio, as stated.

2) Flash sucks on Linux, obviously an Adobe problem, not an Ubuntu one.  Still needs fixing.

3) No options during install.  For one thing, this causes Ubuntu to overwrite the MBR even if I don't want it to, much like Windows.  I'm sure the alternate install CD has options, but if I want to install Grub to /dev/sda5 instead of /dev/sda, that's a basic enough option...  Also, some options on partitioning other than a) use my whole hard drive, b) screw everything up automatically, c) I'll do it myself.  I always use c) of course, but a lot of users use b) because they want to dual boot, and AFAICT it never does things right.  Installer also gives no options for separate /home partition or anything else...  I use a /home/user/Data partition instead, but a /home partition would help a lot of users to not lose stuff when they upgrade or reinstall.

4) Intelligently grouped settings.  The Administration and Preferences menus are full of icons that bring up a dialog with like 1 single check-box... it's ridiculous.  I don't need 25 different settings menus that each have one check-box or drop-down.  How about "Display Settings", instead of Screensaver, Screen Resolution, and whichever menu it is that comes up when you right-click the desktop and choose "Change desktop background...", which has most of the actually useful settings on it?

5) Network manager - hasn't worked correctly for me (and many others) since Intrepid launched.  Wasn't incredibly useful in Hardy either.  Needs work.

I think that's most of it.  Don't get me wrong - there's no perfect OS and I don't claim that any other OS does everything better than Ubuntu, certainly not Windows (others may prefer other distros, but I haven't found one yet that's worth switching to... I think Arch has potential, but they hate GUIs so much and the community is nowhere near as friendly/helpful).  It's just some stuff that annoys me and I hope is being looked into...  Also, I know that a lot of it is upstream as well.

---

### Post by LowSky on 2009-01-30
You know guys know Canonical build a website for these type of problems
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)
but here are my suggestions

System menu is really annoying and is horrible set up, use any other gnome based distro and the same options are found else where, kinda annoying!

More system installed theme and wallpaper options, and loose the brown, it looks ugly, why not use the red/orange/yellow of the logo more often?

A built in help function would be nice, that can help answer questions about the system, kinda like in Windows, have it linked to the ubuntu wiki/documentation.

Better networking control built in

During install it would be nice to see an advanced feature for what applications are installed, so advanced users can install the apps they use/need without the extra clutter.

It would be nice to see a Q&A section on this forum with people from Canonical answeing and/or moderating about where developement of their beloved OS is going. It would be nice to know people from the company actually post here and don't completly hide behind their screen name. Maybe to explain why they chose a new feature or left something out.

I would love a rolling release over the six month release schedule, and a constant testing branch like debian would be awesome. {I'm using Arch as a side OS and I'm liking it more every day... if only it had a GUI for PACMAN built in:)  )

---

### Post by shatteredmindofbob on 2009-01-30
> **diablo75 said:**
> I have no fear of seeing the thread "hijacked".  I wouldn't mind seeing it become a melting pot for complaints.  I would regret to see anyone really shy away from watching "flaws" be voiced.  The flaw I posted about is obviously on the OS.  A few others here are as well.  Some... well... see, this is where things start to look like kids fighting in elementary school where there's a lot of finger pointing and little compromise.

If Ubuntu wants to be popular, it needs to be non-technical for most tasks.  The thing that I think Ubuntu has does best at thus far is cutting into the resistance that is the obsessive-compulsive linux user, who is strict, stubborn, loves typeing his password left and right, editing text files filled with jargon that nobody but he understands, and so on.  Ubuntu seems to try and automate this type of mentality and boil it down to a simple password entry, which is a great way to tackle otherwise difficult to understand tasks (like sharing a freaking printer or a folder with another computer; but it's still not perfect).

How many of you out there have used a Mac?  I've barely used one.  I have a friend who's used one for nearly his whole life.  He recently lost his Mac due to a hardware failure, and replaced it with a Vista laptop (letting me install Ubuntu along side it).  It is no mystery to me why he's chosen to use Windows instead of Ubuntu.  Figuring the mystery out is the point of this thread.  There is too much out there that is just plain "stupid" that just needs to be fixed before it will ever be able to compete in the real world, if it is actually intended to become the next big mainstream OS.  If it isn't, if the user base out there thinks it's destined to become and remain the "awesome" OS that it is right now and remain hidden in the shadows of mediocrity because it takes some kind of "guru" to keep it working from day to day... it makes most wonder if it's worth wasting their time with.

In that case, I'll give you my big one: software installation. 

Yes, the repos are great, WHEN the software you want is in there and IF it gets updated REGULARLY and I'm not talking about having to wait six months for the next distro to get the latest version. 

On a Windows or Mac box, I can download and install the latest OpenOffice the second it's released (assuming their servers don't crash under the weight.) 

We Ubuntu users seem to be a bit luckier than on other distros thanks to Getdeb.net, but why do I always get this pop-up window that essentially says "I wouldn't do that if I were you...". Plus, as great as the maintainers are, even they can't keep up. A "new" version of Tomboy notes was posted recently but if you go to the project site, there's an even newer version. 

I tried compiling from source, but after the fourth time it told me I had to install yet ANOTHER development package, I gave up. 

I realize this has more to do with project maintainers than Ubuntu itself but man, that's gotta be one of my biggest irritations. Especially since the project maintainers usually have Windows binaries up right away.

---

### Post by s3kt0r on 2009-01-30
> **GrouchoMarx said:**
> This is really more of a kernel issue, but most of the problems mentioned so far are really insignificant when compared to power management and battery life. Specifically, on my platform I get 9 hours of battery life in Vista, compared to 3.5 hours in Ubuntu on an Intel computer. Also the fan runs constantly in Ubuntu, regardless of temperature, whereas it hardly ever runs in Vista. Note that Intel releases open source drivers for their chipsets, so this isn't really a closed-source driver issue. Yes it's newer hardware, and it usually takes time to sort out all the kinks, but I have never heard of or seen power consumption in Linux being anywhere near what it is in Windows.

No, it's not Ubuntu's "fault", but the GUI, theme, and icons are really insignificant problems in comparison, and if I could make one wish, it would be to fix power management in Linux.


NINE hours of battery life on vista???? What battery do you own? 9-cell?12-cell?3200-cell?

...

My laptop came with Vista installed, kept it for 3 months, then decided to go back to linux, and tried ubuntu for the first time (been user of other distros, like slack and redhat).

On Vista I had precisely 2 and a half hours of battery. On ubuntu, I get 3h, 3h15 depending on many stuff's state (wifi, lcd brightness, gaming, sound)...

So...Could you tell us about the battery model u're using??

EDIT: Like someone else said, don't bother complaining about things not working. Just ask others if you don't know how to solve it yourselves. It'll get solved sooner or later. If you don't like the way things are going, go back to Windows, maybe Linux is not for you. It's free, and people still get pissed @ devs, who do this for FREE.

thanks linux devs for all the hard work.

---

### Post by GrouchoMarx on 2009-01-30
> **s3kt0r said:**
> NINE hours of battery life on vista???? What battery do you own? 9-cell?12-cell?3200-cell?

...

My laptop came with Vista installed, kept it for 3 months, then decided to go back to linux, and tried ubuntu for the first time (been user of other distros, like slack and redhat).

On Vista I had precisely 2 and a half hours of battery. On ubuntu, I get 3h, 3h15 depending on many stuff's state (wifi, lcd brightness, gaming, sound)...

So...Could you tell us about the battery model u're using??

EDIT: Like someone else said, don't bother complaining about things not working. Just ask others if you don't know how to solve it yourselves. It'll get solved sooner or later. If you don't like the way things are going, go back to Windows, maybe Linux is not for you. It's free, and people still get pissed @ devs, who do this for FREE.

thanks linux devs for all the hard work.

LOL, 3200-cell! That's a nice round number :). I have a Lenovo x200 with a 9-cell battery. In Vista, under light browsing, the batteries last just over 9 hours. In Ubuntu, under similar conditions, just over 3. I would have to take the batteries out to get a battery spec number. But needless to say, 1/3 battery life in Linux is pretty miserable drop-off.

As I said in the previous post, it obviously takes time for these kinks to get ironed out, and power management is not really Ubuntu's domain, but since the thread is about what you think NEEDS to be fixed, well, then I think my number one need would be better power management in Linux. Personally I don't see what good it does to ban casual discussions about the shortcomings of Ubuntu or Linux. No-one is insulting the devs.

---

### Post by aceinthenight on 2009-01-30
> **MasterNetra said:**
> I would like to see Ubuntu rotate the taskbar image for Vertical taskbars?(Or at least have the option for Ubuntu to do that) You would think this would be a easy thing to do. (at least compare to the stuff they usually do)

The image as in the actual taskabar look, or the ubuntu icon?

---

### Post by bruce89 on 2009-01-30
> Stupid things about Ubuntu you think need to be fixed

People who moan about stupid things in Ubuntu they think need to be fixed. That and people insulting developers (such as the PulseAudio ones).

---

### Post by Giant Speck on 2009-01-30
> **Skripka said:**
> Stupid things?


How about native FRIGGIN multi-button mouse support?!!??

PS-Can anyone tell I'm p*ssed that this still has yet to happen?

I hate to drag this post all the way back up, but I recently purchased a Logitech mouse for my laptop that works great with Ubuntu.  It has three mouse buttons.  The middle button works as a scrollwhell, a button, and if you push it from side to side, a side-scroller.  And even the side-scroller features work in Ubuntu.  When I get home I'll try to find the name and model of the mouse for you.

---

### Post by Mr. Picklesworth on 2009-01-30
Indeed, my VX Revolution's numerous buttons work just fine. The side scrolling, in fact, works way better than in Windows because of how events propagate between widgets and the fact that the GTK scroll container widget handles all the mouse button events itself (instead of relying on the child widget conveying that information explicitly). It's fairly magical.
I was happy to learn that even Wine sees my additional mouse buttons now. This was not the case before 8.04.

Would be nice if we had a keyboard shortcut setting for Back, and if the Keyboard Shortcuts configuration tool would handle more mouse button events. (Although I am sure there's an adequate reason why it currently only captures the Search button).

The issue Skripka has is probably specific to certain applications. The trouble is they can't really have hardcoded Button6=Back, since different mice are different.

---

### Post by diablo75 on 2009-01-30
Flipping a couple previous posts around....

> **bruce89 said:**
> People who moan about stupid things in Ubuntu they think need to be fixed. That and people insulting developers (such as the PulseAudio ones).

> **GrouchoMarx said:**
>  Personally I don't see what good it does to ban casual discussions about the shortcomings of Ubuntu or Linux. No-one is insulting the devs.

I can't help but agree with Groucho.  The thread isn't intended to be disrespectful to developers (though others have mentioned that developers apparently never actually visit the forums... so what they don't know won't hurt them, but it also won't help them make improvements, either).  

I've dedicated 3 years to learning and loving Ubuntu because I know it has the potential to knock out commercial mainstream competitors, if only it weren't for stubborn lock-step old boys who hinder its accent towards public wide acceptance.  Linus Torvalds just finished ditching KDE, which he used to **preach** about while **bashing** GNOME, and most people don't feel like blaming him for feeling so negative.  Why should anybody else shy away from voicing their opinion about an obvious shortcoming.  I mean, the post I started this thread with contains a screen shot of a windows that says something you can only describe as being utterly ignorant.  As a user, you just can't help but look at something like that and say, "Wow, who wrote this?!  What on earth were they thinking?  Did they have a plane to catch or something?"

The quote above, "People who moan about stupid things in Ubuntu they think need to be fixed."  How do you propose we fix Linux Torvalds?  Or fix every other user like him who fled from KDE because it took a wrong turn somewhere and got sent out the door too early?  Should we tell Linus about Launchpad?  Ask him to file a bug report?  (I'd love to see the look on his face the day he gets *that* suggestion in an email).

So I guess I should just expand my idea of what a "bug" actually is for Launchpads sake.  From a bug being a hiccup in a program that either causes it to crash or break, or a hardware glitch that prevents something from working right, out to casual criticism about "Horrible interface design meets Average Joe User."  I can just see it now:  "Hey Launchpad! Did you know there isn't actually such a thing as System>Administration>Firewall?  Or that on a default install of Ubuntu, Firestarter isn't even included?  Or that the average PC user hasn't memorized all 1024 reserved port numbers, their purposes or which ones to open in the event they're asked to start up this imaginary System>Administration>Firewall program?"  Fine, I can do that.

---

### Post by bruce89 on 2009-01-30
> **diablo75 said:**
> I can't help but agree with Groucho.  The thread isn't intended to be disrespectful to developers (though others have mentioned that developers apparently never actually visit the forums... so what they don't know won't hurt them, but it also won't help them make improvements, either).  


I was in a bad mood for some reason. I also wasn't referring to this thread, but behaviour in bug trackers.

> **diablo75 said:**
> I've dedicated 3 years to learning and loving Ubuntu because I know it has the potential to knock out commercial mainstream competitors, if only it weren't for stubborn lock-step old boys who hinder its accent towards public wide acceptance.

I like the way you call me an "stubborn lock-step old boys". Being 19, this seems odd.

> **diablo75 said:**
> The quote above, "People who moan about stupid things in Ubuntu they think need to be fixed."  How do you propose we fix Linux Torvalds?  Or fix every other user like him who fled from KDE because it took a wrong turn somewhere and got sent out the door too early?  Should we tell Linus about Launchpad?  Ask him to file a bug report?  (I'd love to see the look on his face the day he gets *that* suggestion in an email).

Well, filing bugs and submitting patches are the only constructive ways to go forwards. Randomly mouthing off doesn't really work. Linus submitted patches to Metacity a few years ago (they were rejected I think).

> **diablo75 said:**
> So I guess I should just expand my idea of what a "bug" actually is for Launchpads sake.

There already is something that fills that gap, [Ubuntu Brainstorm]("http://brainstorm.ubuntu.com/"). However, I find it is full of bad or undoable ideas, but at least it's something.

---

### Post by Cracauer on 2009-01-30
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/311758](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/311758)

---

### Post by shatteredmindofbob on 2009-01-31
> **bruce89 said:**
> People who moan about stupid things in Ubuntu they think need to be fixed. That and people insulting developers (such as the PulseAudio ones).

I'm not insulting the PulseAudio developers, I'm insulting whoever thought it was a great idea to take a platform that was nowhere near ready for prime-time and make it the new standard.

---

### Post by diablo75 on 2009-01-31
> **diablo75 said:**
> Here's another.  And I post this honestly not knowing who to blame... Ubuntu, or Firefox.

When I click on a link to a *.pls file (otherwise known as a "Shoutcast MP3 playlist") It presents the attached screenshot.

Lets say I don't want it to open it with Totem.  Instead, I'd like it to play in VLC, (or XMMS for those die hard XMMS fans out there).  So I click on the drop down where "Movie Player" is currently shown, and select "Other..." because NOTHING ELSE IS THERE.

Instead of being presented with a nice listing of installed applications, I'm asked to browse my root file structure.  I, after 3 years of using this OS, still have little idea as to where I should even look to find VLC or any other app for that matter.  New users, I would bet hard cash, HATE THIS.  Sorry.

Edit:  Before anyone tells me "how to do this"  I shouldn't have to be told.  If I click "Other..." I **shouldn't** have to see the file structure.  I should be given a listing of installed apps to pick from.  Simple, clean.
It's nice to know that when I posted this, people agreed that it was a valid problem that deserved a bug report.

What's not nice is when you go to submit a bug report, and find that someone already submited one for the exact same problem FOUR F---ING YEARS AGO!!!

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/18995](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/18995)

It lists it's Importance under "Unknown".  REALLY????

---

### Post by 23meg on 2009-01-31
> **shatteredmindofbob said:**
> I'm insulting whoever thought it was a great idea to take a platform that was nowhere near ready for prime-time and make it the new standard.

Your addressee is known for his [level-headed]("http://0pointer.de/blog/projects/jeffrey-stedfast.html") [rebuttals]("http://0pointer.de/blog/projects/pascal-terjan.html").

---

### Post by RichardLinx on 2009-02-02
No support for multiple Audio/Video formats out of the box. I know this is because of legal issues with codecs and that they are easily installable but It's still 'annoying' for new users I'm sure. 

Not all problems can be fixed via GUI. People migrating from Windows or Mac OSX don't want to fix there computer problems by typing things they don't understand into a CLI.

"Ugly" GUI: To be fair I don't mind the default Ubuntu theme, but It's been complained about by so many people you would think they would have 'fixed' it by now. How hard can It be to incorporate some extra themes with the default install? There are plenty out there. I'm sure the Ubuntu look has turned away many potential users.

Just thought I'd add some extra criticism.

---

### Post by swoll1980 on 2009-02-10
> **diablo75 said:**
> 

So I guess I should just expand my idea of what a "bug" actually is for Launchpads sake.  From a bug being a hiccup in a program that either causes it to crash or break, or a hardware glitch that prevents something from working right, out to casual criticism about "Horrible interface design meets Average Joe User."  I can just see it now:  "Hey Launchpad! Did you know there isn't actually such a thing as System>Administration>Firewall?

I think you should. I filed bug reports because my printer, and modem are not supported even though both manufacturers provide open source drivers(intel and lexmark). Although lexmark only provides a developers tool kit. I assumed these were the kinds of things we could file bug reports on.

---

### Post by swoll1980 on 2009-02-10
> **RichardLinx said:**
> No support for multiple Audio/Video formats out of the box. I know this is because of legal issues with codecs and that they are easily installable but It's still 'annoying' for new users I'm sure. 


This is a silly complaint It can't be fixed unless you by a comp with Ubuntu preinstalled. This applies to windows, and osx as well.
Try doing a fresh install of windows or osx, and tell me how many audio/video formats are supported out of the box. Ubuntu would have to sacrifice it's philosophies to fix this, and I don't believe they would, or should do this. I would add that the codec installer they added to Ubuntu is great, and made it way easier to install them than the other OSes I mentioned earlier.

---

### Post by bruce89 on 2009-02-13
> **swoll1980 said:**
> This is a silly complaint It can't be fixed unless you by a comp with Ubuntu preinstalled. This applies to windows, and osx as well.
Try doing a fresh install of windows or osx, and tell me how many audio/video formats are supported out of the box. Ubuntu would have to sacrifice it's philosophies to fix this, and I don't believe they would, or should do this. I would add that the codec installer they added to Ubuntu is great, and made it way easier to install them than the other OSes I mentioned earlier.

I can't take Windows/OS X seriously, they don't have Theora, Vorbis or Dirac support out of the box.

---

