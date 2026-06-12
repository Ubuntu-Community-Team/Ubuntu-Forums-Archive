---
title: "Upgrade to KDE 4.2?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-28
Hi, all:

I'm running the latest stable KDE.  I REALLY need some of the functionality in KDE 4.2, most specifically, the ability to have different settings in different virtual desktops (wallpapers, plasmoids, icons, etc).

Is there a seamless way to upgrade to 4.2 beta?  Can I enable some repos or something to upgrade and have them work all the way through the stable release of 4.2?

---

### Post by Skripka on 2008-11-28
> **tarahmarie said:**
> Hi, all:

I'm running the latest stable KDE.  I REALLY need some of the functionality in KDE 4.2, most specifically, the ability to have different settings in different virtual desktops (wallpapers, plasmoids, icons, etc).

Is there a seamless way to upgrade to 4.2 beta?  Can I enable some repos or something to upgrade and have them work all the way through the stable release of 4.2?

Only packages for OpenSUSE are currently available, debs should be available sometime soon.


BUT--(big) BUT--you're asking to play with _**[B]fire**[/B]_.  Beta quality software is just that, and it is just as likely to work as it is to eat your firstborn children.  You may get the functionality you want, or you may end up with a b0rked computer with your OS and docs all killed or beyond your reach.

---

### Post by bangmalley on 2008-11-28
Add this to your sources

deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) intrepid main

and sudo apt-get install kde-nightly

log out and change the session.

Credit: [http://ubuntuforums.org/showpost.php?p=6182939&postcount=2](http://ubuntuforums.org/showpost.php?p=6182939&postcount=2)

---

### Post by tarahmarie on 2008-11-28
> **Skripka said:**
> Only packages for OpenSUSE are currently available, debs should be available sometime soon.


BUT--(big) BUT--you're asking to play with _**[B]fire**[/B]_.  Beta quality software is just that, and it is just as likely to work as it is to eat your firstborn children.  You may get the functionality you want, or you may end up with a b0rked computer with your OS and docs all killed or beyond your reach.

That's true.  Still--I NEED the separate workspaces BADLY, and no one seems to be able to tell me how to get separate workspaces with differing wallpapers, icons, and plasmoids in KDE 4.1.

---

### Post by TheUnabeefer on 2008-11-30
> **tarahmarie said:**
> That's true.  Still--I NEED the separate workspaces BADLY, and no one seems to be able to tell me how to get separate workspaces with differing wallpapers, icons, and plasmoids in KDE 4.1.

It USED to be there, but I noticed it missing since the upgrade to 4.1.3... on the little squigly doo-dad up in the top right corner, there used to be a "Zoom Out" and then "Add Activity"  They call it the ZUI (Zooming User Interface) and its purpose was to allow sort of "layers" with different plasmoids and wallpaper and all that jazz, in addition to your different desktops.

So, say you have 4 desktops, then you create an "activity", and you have another layer, which changes the plasma interface for your 4 desktops, while the applications running on the desktops stay the same.

Here's a video on YouTube that sorta shows it:  [http://www.youtube.com/watch?v=EhODrJkoidA]("http://www.youtube.com/watch?v=EhODrJkoidA")

Anyways, it was suddenly gone in 4.1.3, rendering the swirly-gig in the corner even MORE useless than I already considered it.  Maybe it will be back in 4.2, I don't know.

---

### Post by C. Wizard on 2008-11-30
> **tarahmarie said:**
> Hi, all: I'm running the latest stable KDE....
The last **_STABLE release was 8.04 with KDE 3.5.10._**
I made the mistake of installing Kubuntu 8.10 with KDE 4.xx and I can**_NOT_** recommend it to anyone who has to depend upon their computer to get serious work done, i.e., their income is dependent upon a stable working computer.
KDE 4.xx is "pretty" but it has a long, long, very long way to go before it is ready for serious daily use. 
8.10 hasn't been much better and appears to have been released too soon.  In the month since its release, the kernel has been "updated" at least 3, if not 4 times.  The CUPS files have been updated more than that.  The KDE files... once or twice. Gwenview is trashed. Kopete doesn't work corrently. Neither does KMail. Sound does not work correctly with the KDE desktop and its applications, but works OK with other applications.  Scanning still sucks, but it has never been good with Linux... and the list goes on.
Stay with K/Ubuntu 8.04 and KDE 3.5.10 for a few more months if you can.

---

### Post by binbash on 2008-11-30
> **C. Wizard said:**
> The last **_STABLE release was 8.04 with KDE 3.5.10._**
I made the mistake of installing Kubuntu 8.10 with KDE 4.xx and I can**_NOT_** recommend it to anyone who has to depend upon their computer get serious work done, i.e., their income is dependent upon a stable working computer.
KDE 4.xx is "pretty" but it has a long, long, very long way to go before it is ready for serious daily use. 
8.10 hasn't been much better and appears to have been released too soon.  In the month since its release, the kernel has been "updated" at least 3, if not 4 times.  The CUPS files have been updated more than that.  The KDE files... once or twice. Gwenview is trashed. Kopete doesn't work corrently. Neither does KMail. Sound does not work correctly with the KDE desktop and its applications, but works OK with other applications.  Scanning still sucks, but it has never been good with Linux... and the list goes on.
Stay with K/Ubuntu 8.04 and KDE 3.5.10 for a few more months if you can.

I dont see any problems at KDE 4.1.X  except 1-2 very small issues.

---

### Post by Skripka on 2008-11-30
> **binbash said:**
> I dont see any problems at KDE 4.1.X  except 1-2 very small issues.

Ditto-except for a handful of minor annoyances-it works beautifully here.

---

### Post by C. Wizard on 2008-11-30
> **binbash said:**
> I dont see any problems at KDE 4.1.X  except 1-2 very small issues.
Do you use it in a business environment? Sorry, it just can't cut it.  
They finally had it together with the combination of K/Ubuntu 8.04 and KDE 3.5.10.  I could show that to people as a valid alternative to, ugh, winblows, but not 8.10/KDE 4.
I don't understand the thinking behind an outfit that takes a known good product and then trashes it and turns the clock back a few years by releasing something that doesn't work, KDE 4.x, as well as their previous product, KDE 3.5.10.  
"Stupid is as stupid does" and it will only hurt the reputation of Linux community in the long run. That is, KDE must be just like mickeysoft since they put out buggy software and beta test it on the end user.
KDE 4.xx should NOT have been released for general use until it was as good as KDE 3.5.10.
IMHO, of course. :)

---

### Post by Skripka on 2008-11-30
> **C. Wizard said:**
> 
KDE 4.xx should NOT have been released for general use until it was as good as KDE 3.5.10.
IMHO, of course. :)

Let's see here....KDE3.x series has been around for how long (cough 6 years-cough)?  NO major software when it comes out is bug free, Windows OS, MacOS-doesn't matter.  If you don't mind playing with KDE3 for the next 5-7 years until KDE4 "is ready", there you go.

A new release as good as a software in development for 6 years, as good as the old stuff, at time of release--who are you kidding?

---

### Post by C. Wizard on 2008-11-30
> **Skripka said:**
> ...A new release as good as a software in development for 6 years, as good as the old stuff, at time of release--who are you kidding?
Of course you are entitled to your opinion :) but in the case of KDE 4.x, nonsense. KDE is suppose to be a evolutionary product, that is, it gets better as it goes along. So, what do they do, dump 3.5.10 and start from scratch?!
Reminds me of the current situation at the Bangkok airports. About as smart as mud.  They are going to kill, if they haven't already, this years tourist season and the effect will linger on for years to come.
KDE 4.xx is doing the same thing to their user base. People will either switch to another desktop or maybe even be driven back to, ugh, winblows.  I've personally have had just about enough of the increasingly apparent attitude of the Ubuntu developers to hide more and more of the operating system from the end user and old Slackware is starting to look better and better with each passing day.

---

### Post by Skripka on 2008-11-30
> **C. Wizard said:**
> Of course you are entitled to your opinion :) but in the case of KDE 4.x, nonsense. KDE is suppose to be a evolutionary product, that is, it gets better as it goes along. So, what do they do, dump 3.5.10 and start from scratch?!


_***YES***_.

Blame the nature of code.

If you really need a lecture as to why keep reading.

When you want to move forward--you have to dump code and start over.  Lots of things in KDE4 could just plain not be done in KDE3--if it could have been would they have started tabula rasa?  No one in their right mind wants to start over from scratch-except for when they have no other choice.  The KDE3 codebase has been carried over for 6 years-and has probably gone as far as it could.

KDE4 already wins over its predecessor-as on my setup I could NEVER get Compiz to work right-never.  It works out of the box with KDE4 via Kwin....hours of fiddling-and All I would end up with is a dead xorg-and finally I gave up on Compiz.

For better or worse, the KDE devs took the "release early and often" approach, with KDE4.  Unfortunately, like Windows Vista-users got used to the 6-7 year old predecessor and its stability-and when the new came, people screamed in terror expecting the impossible.  I'll be the first to say the _***preposterous***_ KDE4 "Remix" on Hardy Heron was a terrible joke on end-users (I say that as the features present were largely buggy).  KDE4.1.3 though is light-years ahead of the 4.0 series.



It is impossible to port over several millions of lines of code from KDE3 to KDE4 in a timely manner, especially when the two are so fundamentally different.  Double especially when your project is FOSS, and you don't have a paid full time development team.  New (old) features are getting added back in-as things are shown to work on a wide-spread scale.  It will get there-but you cannot reasonabley expect 6 years or work on one thing to magically get transferred over to a totally different thing---the good news is the main work left is to figure out how to implement features into the new code (as opposed from gaving to invent the features from scratch).


Name ONE software OS that was PERFECT on *.0.0 release.  I dare you.  No Windows OS qualifies, no Mac OS qualifies.

---

### Post by C. Wizard on 2008-11-30
> **Skripka said:**
> _***YES***_.  It is impossible to port over several millions of lines of code from KDE3 to KDE4 in a timely manner, especially when the two are so fundamentally different.  Double especially when your project is FOSS, and you don't have a paid full time development team.  New (old) features are getting added back in-as things are shown to work on a wide-spread scale.  It will get there-but you cannot reasonabley expect 6 years or work on one thing to magically get transferred over to a totally different thing---the good news is the main work left is to figure out how to implement features into the new code (as opposed from gaving to invent the features from scratch).

OK. I'll buy that to a point, BUT, they had to know all of this, so WHY did they, the Kubuntu team, for all practical purposes, forced it upon the end user with the release of Kubuntu 8.10?!  And don't tell me we weren't "forced." If you want to be able to install the latest versions of your favorite applications "tweaked" to run on K/Ubuntu from the Ubuntu repositories, you have to "upgrade" to the latest version.

---

### Post by Skripka on 2008-11-30
> **C. Wizard said:**
> OK. I'll buy that to a point, BUT, they had to know all of this, so WHY did they, the Kubuntu team, for all practical purposes, forced it upon the end user with the release of Kubuntu 8.10?!  And don't tell me we weren't "forced." If you want to be able to install the latest versions of your favorite applications "tweaked" to run on K/Ubuntu from the Ubuntu repositories, you have to "upgrade" to the latest version.

Probably because they have to draw an "enough" line somewhere.  No matter what release they choose-it would be an arbitrary decision.

Trying to move forward and maintain backwards compatability with the old software is what NEARLY killed Apple Macintosh.  When Apple was about to go under-they were trying to write an software and OSes that would support 15+ years of hardware/software....Mac OSX was born when Jobs came back and declared only the last 3-5 years of hardware would be supported with each successive OS release.  OSX took off from there.

Windows is in an identical problem-except worse.  Win XP will work on 7+ year old hardware, and many folks do still use such hardware.  But to move the OS forward, they have to draw a line at hardware support............the problem being with 70% or so marketshare and MOST people using and wanting to use XP--no matter where they draw the line people will and are screaming.....and as Windows is expensive as is new hardware-they are justifiably angry at being declared obsolete.



There will always be folks who say something isn't "ready"...but the sooner you ween people off the old, the better it is for development.  It frees KDE from having its time 1/2 working on KDE4 and 1/2 on on KDE3--it considerably frees up devs everywhere-as they don't have to keep worrying about keeping KDE3 working (this goes for Ubuntu, as well as other devs).

---

### Post by tarahmarie on 2008-11-30
I'm glad I started this debate, but if the OP might interject--I still have a few technical questions.  

(1) If I enable the Project Neon repos, will the full release of 4.2 be in them at the end of January?

(2) Will any major 8.10 update conflict with my install of 4.2?

(3) Will the full release of 4.2 happen before or after Jaunty?

(4) When 4.2 comes out officially, can I simply remove the project neon sources from my source list and rely on the official repos?

(5) When 4.2 comes out officially, will it remove my 4.1 install? (Cuz I want it to)

---

### Post by Syock on 2008-11-30
>>tarahmarie
I can only answer (5), which is, if it has made its way as default in Jaunty, chances are that your 4.1 will be upgraded as you make your distro upgrade, or change your apt repo to jaunty's.

---

### Post by SunnyRabbiera on 2008-11-30
> **Skripka said:**
> 
Name ONE software OS that was PERFECT on *.0.0 release.  I dare you.  No Windows OS qualifies, no Mac OS qualifies.

Actually Firefox was pretty good when it was version 0.0.9, it actually ran better then later versions when it finally hit the 1.0 phase.

---

### Post by cptr13 on 2008-11-30
In reference to one of the responses to this thread.  I am a one-man recruiting firm and I use kde 4.1 almost exclusively.  In fairness, I have a nasty tendency to distro-hop, so I've gotten very good at backing up and restoring my critical data.  But as for KDE 4.1....it absolutely does everything I need it to do in a business, office environment.  I used Gnome for about a year before making the switch, thankfully I never got into kde3x so I don't have the "I just can't convert" issues so many longer term KDE folks seem to have.  I LOVE KDE4 so far, and it seems to only be getting better.

---

### Post by Skripka on 2008-11-30
> **SunnyRabbiera said:**
> Actually Firefox was pretty good when it was version 0.0.9, it actually ran better then later versions when it finally hit the 1.0 phase.

Browsers are nearly the only place where I could think of exceptions to my statement...OTOH, a browser is far less complicated than an OS, both in volume of code as well as potential compatability problems.

---

### Post by C. Wizard on 2008-12-06
> **Skripka said:**
> ...Windows is in an identical problem-except worse.  Win XP will work on 7+ year old hardware, and many folks do still use such hardware.  But to move the OS forward, they have to draw a line at hardware support............the problem being with 70% or so marketshare and MOST people using and wanting to use XP--no matter where they draw the line people will and are screaming.....and as Windows is expensive as is new hardware-they are justifiably angry at being declared obsolete.

There will always be folks who say something isn't "ready"...but the sooner you ween people off the old, the better it is for development.  It frees KDE from having its time 1/2 working on KDE4 and 1/2 on on KDE3--it considerably frees up devs everywhere-as they don't have to keep worrying about keeping KDE3 working (this goes for Ubuntu, as well as other devs).
Sorry. Don't buy it. Why should the public, be they winblows, MAC, or Linux users be forced to dump working hardware.  I'm not talking about a 486 processor, but, e.g., relatively new scanners or printers that work just fine and don't need to be replace. 

Of course, if you are the manufacturer of those printers, scanners, etc., you are reluctant to provide new drivers, or in some cases you refuse to provide new drivers, because you want to force people to buy new equipment they really don't need. The cost of replacing equipment simply because the operating system won't support it has to be, in the aggregate, in the billions of Dollars.

Sometimes I wonder if mickeysoft isn't in collusion with the chip makers and the hardware makers for just that reason. Intel announces a new chip and mickeysoft says,
"Great! We'll bloat up winblows even more and bring your new CPU it to its knees." The win-modems are a good example of the kind of nonsense that mickeysoft has been up to with the manufacturers trying to lock everyone into their products and secure their monopoly.

If something is truly new and improved and increases my productivity, or makes my life a little easier or more enjoyable, I'll buy it, no problem, but when a new product, or in this case, an operating system or desktop doesn't bring anything new to the table, and Vista does not, there is no reason to change.  BTW, from what I've read, regardless of what mickeysoft would like us to believe, there is very little about Vista that is new. It is just another rehash of NT with a few more "Gee Whiz! Will you look at that" visual bells and whistles.

And, speaking of not all change being good, I've been using Kubuntu 8.10 amd_64, for 5 weeks now and seriously regret making the change. 8.10 is Not stable and KDE 4.xx is not ready for the prom. Maybe it is KDE, I don't know, that is causing the problems, but it has been crashing, i.e., freezing up, so much I sometimes think I'm running Windows 98, 2nd edition. Hell, XP is more stable than 8.10. 
I NEVER, EVER, thought I would say that about Linux. I NEVER, EVER had such problems with Kubuntu 7.04, 7.10, 8.04, and all the versions of Slackware I've used in the past.
At this point I could backup and do a clean install of 8.04, but if I have to go to that much trouble I think I would rather try Slam64, an unoffical 64 bit port of Slackware.

---

### Post by C. Wizard on 2008-12-06
> **cptr13 said:**
> In reference to one of the responses to this thread.  I am a one-man recruiting firm and I use kde 4.1 almost exclusively.  In fairness, I have a nasty tendency to distro-hop, so I've gotten very good at backing up and restoring my critical data.  But as for KDE 4.1....it absolutely does everything I need it to do in a business, office environment.  I used Gnome for about a year before making the switch, thankfully I never got into kde3x so I don't have the "I just can't convert" issues so many longer term KDE folks seem to have.  I LOVE KDE4 so far, and it seems to only be getting better.
If it works for you fine, but you must not be using Kopete, KMail, Gwenview, digiKam, Kaffeine, MPlayer, VLC, gxine, or KlamAV, none of which work as advertised and there are many applications, especially KDE applicatons, that I have yet to use.

Most of my business "paperwork" involves writing letters (word processing), retrieving photos, printing, scanning documents into .pdf files, and transmitting the same via e-mail.

The scanning is done in XP running inside a VirtualBox as XSane does a horrible job of scanning. Well, I don't know if it is XSane or Sane, the backend. Probably Sane.  

I can't retrieve photos with digiKam, that is broken, so I use a combination of Dolphin and Gwewnview or The Gimp.  

Gwenview itself is broken and many of the features that made it so popular (and it was a great viewer) no longer work. Ditto Kmail, Kopete, Kaffeine, MPlayer, gxine, and KlamAV. VLC doesn't work period.

Surprisingly, the HP printer drivers work better than they ever have, which is a nice, but not much of a consolation.

KMail is so slow, both sending and receiving I've just about given up and switched to Thunderbird.  Too bad, as KMail and Kopete were my two favorite applications, followed by VLC and Gwenview. The spell checker in KMail is absolutely worthless. It can't even identify the plural form of a simple word. Any word for that matter. For example, take the word, "word." Add an "s" to the end and the spell checker see it as an error.  Ditto anything ending in "ing," "ly," etc., etc., etc. 

I would expect this kind half-baked nonsense from microsoft, but not from a Linux distribution. 

Time to move on. ):P

---

### Post by Skripka on 2008-12-06
> **C. Wizard said:**
> If it works for you fine, but you must not be using Kopete, KMail, Gwenview, digiKam, Kaffeine, MPlayer, VLC, gxine, or KlamAV, none of which work as advertised and there are many applications, especially KDE applicatons, that I have yet to use.


Dunno what is the deal with your machine-but the only thing that is buggy is VLC on my machine (and that is only when Amarok is minimized in the tray)--otherwise it runs fine.  YMMV of course.

---

### Post by C. Wizard on 2008-12-06
> **Skripka said:**
> Dunno what is the deal with your machine-but the only thing that is buggy is VLC on my machine (and that is only when Amarok is minimized in the tray)--otherwise it runs fine.  YMMV of course.
[-X
Can you tell me with a straight face, without crossing your fingers behind your back :) , there is nothing wrong with Gwenview?

---

### Post by Skripka on 2008-12-06
> **C. Wizard said:**
> [-X
Can you tell me with a straight face, without crossing your fingers behind your back :) , there is nothing wrong with Gwenview?

Is there something wrong with Gwenview that I should be noticing?  :confused: 

It runs fine here, It does what I expect it to when I expect it to.  Of course I only use Gwenview as an organizational tool, no image/photo editing-GIMP fills in that task (I know the "plugins" pulldown is completely vacant in Gwenview)

////////////hands out on keyboard and toes out from under desk, in full view///////////////

---

### Post by C. Wizard on 2008-12-07
> **Skripka said:**
>  (I know the "plugins" pulldown is completely vacant in Gwenview)
And you don't thing that is a serious problem?!
Without that I have to use two other programs, make that three counting Gwenview, to get done what I use to be able to do in Gwenview.

To so ardently defend something so seriously flawed as KDE 4.xx (and the fact it was forced on Kubuntu users) you must be a KDE developer or somehow associated with KDE. Correct?

---

### Post by Skripka on 2008-12-07
> **C. Wizard said:**
> And you don't thing that is a serious problem?!
Without that I have to use two other programs, make that three counting Gwenview, to get done what I use to be able to do in Gwenview.

To so ardently defend something so seriously flawed as KDE 4.xx (and the fact it was forced on Kubuntu users) you must be a KDE developer or somehow associated with KDE. Correct?

Nope, wrong on that last count.  Just a fairly pleased end-user.

"Serious problem", not so much.  I'm used to using Gwenview in an Adobe Bridge type capacity--and with the GIMP 2.6, GIMP is finally usable enough to use as a photo/image editor...besides GIMP currently has more, and will probably continue to have more plugins written for it than Gwenview or Krita (for any time in the visible future).


It depends on your work flow.  The only tools native to linux that are at all comparable in interface usability to Photoshop-are GIMP (now, as of 2.6.2 or so; before that GIMP was atrocious in interface), and $100+ commercial programs; I doubt Gwenview or Krita will have an interface as elegant in organization or as useable as Photoshop at anytime in the near future....the way Gwenview is organized (as of now), leads me to think it's developers conceive of it as a fundamentally organizational tool-with some very light editing possibilities possible.  Use a hammer for nailing, and a saw for cutting I say ;)

---

### Post by C. Wizard on 2008-12-15
> **Skripka said:**
> Nope, wrong on that last count.  Just a fairly pleased end-user.

"Serious problem", not so much.  I'm used to using Gwenview in an Adobe Bridge type capacity--and with the GIMP 2.6, GIMP is finally usable enough to use as a photo/image editor...besides GIMP currently has more, and will probably continue to have more plugins written for it than Gwenview or Krita (for any time in the visible future).

It depends on your work flow.  The only tools native to linux that are at all comparable in interface usability to Photoshop-are GIMP (now, as of 2.6.2 or so; before that GIMP was atrocious in interface), and $100+ commercial programs; I doubt Gwenview or Krita will have an interface as elegant in organization or as useable as Photoshop at anytime in the near future....the way Gwenview is organized (as of now), leads me to think it's developers conceive of it as a fundamentally organizational tool-with some very light editing possibilities possible.  Use a hammer for nailing, and a saw for cutting I say ;)
I agree about The GIMP. I use it quite abit, and 2.6.x is a great improvement over previous versions, however, it doesn't work well as a photo viewer (unless I missed that feature somewhere along the line), that is, if you want to browse through a series of photos.  For that I've been using Gwenview and when an editor is needed I can export the photo into The GIMP with a few mouse clicks.  That works out as a great combination.

It would be nice if the ACDSee Photo Manager worked in WINE, but it is not to be, at least not yet. The kind people over at CodeWeavers tried to run it in CrossOver, but reported back it just wasn't, so far, possible. ACDSee Photo Manager is about $49.00US and, besides being a great photo viewer, and a good video player, it has most of the common editing features built-in.  I think they are on version "Photo Manager 2009 (actually version 11) and starting with version 9 they added a feature that will average out the highlights and shadows in one click without burning out either extreme. You can vary the results by clicking on lighter or darker objects in the photo. I find that one feature nothing short of amazing. I've tried to do that in The GIMP and have come close, but no cigar. :)

digiKam and its companion viewer showFoto are a pretty good combination. Many of its editing features work in KDE 4.xx.

Right now I'm typing this in Slackware 12 running in VirtualBox on the KDE 4.13 desktop in Kubuntu 8.10, amd_64.  Slackware 12 is 32 bit and runs KDE 3.5.7. It is running faster in VirtualBox than the 64 bit host. Plus I like KDE 3.5.xx better than 4.xx (so far).  I've gotten to the point I've been running it full screen when browsing the 'Net.
Oh, well, maybe KDE 4.2 will be worth waiting for, eh? 
:)
Still giving serious thought to moving to Slamd64 and think I will give it a try when the latest release comes out sometime in the next few weeks.

---

### Post by darthlaidher on 2009-02-18
i dunno what the deal is with my machine but kde 4.1 blows on my machine 

most of  the time i have to reboot twice before the desktop appears correctly and then its just all around slow on my machine.
but vista is super fast.

i wish it would be better :( but i guess i'll just use kde 4 for a backup whenever vista decides to take a dump.

---

### Post by tarahmarie on 2009-02-18
4.2 is a lot better.  I still have hangups over Kontact crashing, but other than that, I'm having a lovely time with it.  The settings were transferred seamlessly to 4.1, and all I'm doing right now is fiddling with the plasmoids.

---

