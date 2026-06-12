---
title: "Short Guide to Window Maker"
date: 2005-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by xequence on 2005-11-02
Guide to Window Maker

First, sudo apt-get install wmaker

			Overview

	Done? Good. First, Window Maker is sort of old. You might like it, or not, but no matter what, it is faster then Gnome or KDE. Log out to GDM (Or any other log in screen) and click on "Session". Choose window maker and log in. It will tell you something else is default, do you want to change window maker to default. You can choose yes or no, but it might be better to not have it by default now. You dont know if you like it or not! Ok, so it takes about a second to load. Not bad, eh? To the basics - On the top right over there are three icons. I dont think the top one does anything. The middle one will launch a terminal and the bottom one will take up the preferences. (On both, right click and choose Launch).

			How to use it

	Now, on the bottom left there is a little place where the icons of your programs go. To open up a program you just right click and choose run, then type the name of the program. It will come up. You will notice the window bar only has an X on the top right. That as you might guess will close the window. On the far left is a minimize button. You can also right click on the window bar to do some things like maximize or hide. Now, see that icon on the bottom left. Right click on it. You can use it to hide, unhide, set icon, or kill the window. (Set icon basically lets you choose the icon picture the window uses). You can right click on anywhere on the desktop to open up the menu. They are all quite self explanitory. On the bottom, you use session to restart windowmaker or do anything else like exit it. Go to appearance. You can choose a style, icons, and a background. You can use a theme which has all three of those preset. You can also save the a theme. You can use different backgrounds. If you want to use your own background, put it in /home/*USERNAME HERE*/GNUstep/Library/WindowMaker/Backgrounds and you can choose it.

			Programs to Enhance Window Maker

	Windowmaker on its own is neat, but to be really useable you might want some other programs. Xfe is a good and fast file manager that has the same look as Window Maker. (Sudo apt-get install xfe). You can run it by right clicking, choose run, and typing xfe into it. Now to customize a bit more. Add a panel. I have tried many panels and perlpanel is my favorite. (Sudo apt-get install perlpanel). Before running perlpanel you will want to move the application icons away from the bottom. Launch preferences, go to icon preferences (fourth one) and choose for them to be in the top left corner. Now make the icon size 32x32 so they dont take up so much of the screen. While you are at it, go to the far option on the right and check "Automatically save session when exiting windowmaker". This will save perlpanel there for when you next log in. Now save and close. Right click on the desktop and choose "Session > Restart Window Maker". Now, right click, choose run, and type in perlpanel. A panel on the bottom will appear. You can click "Actions" and run a program, take a screenshot, perlpanel preferences, and add to panel. Choose "Add to Panel > Launchers > Launcher". Type in the name of the program you want for name, a short description for comment, and the name in small case letters in  program. Choose the icon and click OK. You now have a launcher of your program right there. I have three - Opera, Azureus, and xfe. You can add other launchers and delete them by going to Configure.

			Conclusion

	Now you have a fully functional customized Window Maker desktop. You have a background image, a good file manager, a good panel, and it can be customized even more (but that is for you to do yourself with your own ideas). If anything freezes on you just open up a terminal and type in killall then the name of the program.

---

### Post by phanboy_iv on 2005-11-02
Woo..WindowMaker. Definitely my favorite after GNOME. Runs a lot closer to the terminal, so it's a great learning experience(fast too), and it's ultra-configurable.
Doesn't get too much press, though. Great guide.

---

### Post by xequence on 2005-11-02
[QUOTE=phanboy_iv]Woo..WindowMaker. Definitely my favorite after GNOME. Runs a lot closer to the terminal, so it's a great learning experience(fast too), and it's ultra-configurable.
Doesn't get too much press, though. Great guide.[/QUOTE]

Thank you very much =) Yea, its odd how it isnt really talked about much.

---

### Post by benplaut on 2005-11-03
dude... you are like *so* civil war era :P

---

### Post by regeya on 2005-11-30
Nice to see Window Maker getting some attention.  

Somebody's gotta point out one thing, though:  Window Maker was heavily inspired by OPENSTEP, so if you want a filemanager that's light *and* closer to WM's heart, install fsviewer.  It's rough around the edges, but it's got a nice NeXT look and lighter than GWorkspace, for sure ya betcha. :)  Or rather, it would be if the gworkspace package weren't totally b0rked.  I realize it's in 'universe' but could there be at least a *little* QA on non-main packages?

Anywho, yeah, before I was using these heavier desktops these days I was a Window Maker cheerleader, and before that AfterStep, and before *that* I used FVWM.  Some folks might call me a latecomer to the Linux game but hey, just 'coz my Linux use fell off dramatically after heavy use from late '96 to late '98 doesn't mean I'm a total n00b...does it?

At one point I had what I considered to be the perfect desktop:  Window Maker, with GNOME Midnight Commander (gmc) as my filemanager.  Laugh if you will, but those Apple zealots seem to love having a dock and a desktop filemanager! ;)  Back then there was an awesome GTK theme engine that even moved the scrollbar to the left, where it's supposed to be!  For that matter there were enough NeXT fanboys at that time that you could even get a NeXT-themed Tk, but I digress.  For the GNOME menu I used a Perl script that was floating around.  It was a terribly simple thing, but WM makes it simple to script dynamic submenus.  The script was lost to time, though it's no loss as GNOME and KDE have both changed their method of storing menus at least once since then.

So anyway, yeah, I used WM for several years, and for many years I both loved it for its flexibility and looked forward to the day when GNUstep was more popular.  I'm still looking forward to that, but if WM could be made more stable, support drag-and-drop, and if the Big Two desktops still played nice outside their native habitats, I'd be more willing to use WM.  More willing?  Heck, I'm using it right now.  What I keep hoping for is a more generic desktop standard, and on the day it works and allows me to just pick an app without worrying about having to match windowmanager, filemanager, mail client, etc. I'll more than likely go back to clunky old Window Maker.

---

### Post by ardchoille on 2005-12-17
Window Maker doesn't have a system tray (notification area) and all of the dockapps that I have used which offer this funstionality can show up to 4 icons, but when you open a fifth app that has a systray icon, that fifth icon is never shown.. so, you can only see the first four systray icons and the rest are never shown. I hope someone adds a decent systray to Window Maker, or makes a dockapp that will allow more than four systray icons at once. That is the one thing I didn't like about Window Maker.

---

### Post by Niall Flinn on 2005-12-18
Fantastic! I didn't know WM was available for Debian/Ubuntu! I've been using it at work for a couple of years, and while it seems a bit sparse to begin with, it's very fast and uncluttered, and I really like being able to shade windows and also not have stupid toolbars eating up my precious screen space :)

Thanks,

Niall

---

### Post by hackyou on 2005-12-18
I love WM! Do you have a list of your favorite dockapps?

...a little bit OT... can someone tell me how-to add MWM in the session list of GDM?

Cheers
Marco

---

### Post by Iesos on 2006-01-20
Hi, I'm having loads of problem with windowmaker. If someone who knows it pretty good could take a look here I would realy appriciate it:
[http://www.ubuntuforums.org/showthread.php?t=119590](http://www.ubuntuforums.org/showthread.php?t=119590)

---

### Post by briancurtin on 2006-01-21
im trying to get FSViewer going because im trying to make this as much like openstep was when i used it, but im having this problem when i run it from a terminal:
fsviewer warning: ICONDIR not found: /usr/GNUstep/Apps/FSViewer.app

i installed it via synaptic when searching one day, and i installed the icon file which i thought would make this work. there is no /usr/GNUstep directory, so how do i go about getting that stuff?

---

### Post by hornett on 2006-01-21
I like Window Maker, but having the menu vertically at the side upsets me. Is there any way to put it horizontally (and ideally stop app windows overlapping it, MacOS style) ?

Cheers!

---

### Post by xequence on 2006-02-13
[QUOTE=hornett]I like Window Maker, but having the menu vertically at the side upsets me. Is there any way to put it horizontally (and ideally stop app windows overlapping it, MacOS style) ?

Cheers![/QUOTE]

Sorry for the really late response, but I think you can drag it or something... I dont remember how, but I do know you can make it horizontal, I did it :P

---

### Post by pluriverse on 2007-02-07
> **hackyou said:**
> I love WM! Do you have a list of your favorite dockapps?

Marco

Ciao (Hi) Marco!

i use only WindowMaker with:

wmressel (select resolution of each monitor)
wmmixer 
wmcdplay
wmclockmon (date & time)
wmbutton (9 button to call up to 27 apps in 1 dock) [now i use 3 concurrent of these]
wmmount (show free space and un/mount every partition)
wmdiskmon (show graphically up to 3 partition use)
wmmemload (show % of ram and % or swap used)
wmhdplop (show graphically disk read/write for each drive and total instant Mb/sec transfer)
wmtop (show the 3 most active task)
wmcube (show graphically instant cpu load) [with beryllium 3d object]

[IMG]http://www.geocities.com/pluriverse_it/wmcube_beryllium.jpg[/IMG]

i use my own theme: "everyday"

in freshmeat you can find: beryllium (for wmcube), everyday (theme), solyaris (theme) and highlights (gtk theme)

[http://freshmeat.net/projects/beryllium/](http://freshmeat.net/projects/beryllium/)
[http://freshmeat.net/projects/everyday2006/](http://freshmeat.net/projects/everyday2006/)
[http://freshmeat.net/projects/solyaris/](http://freshmeat.net/projects/solyaris/)
[http://freshmeat.net/projects/highlights/](http://freshmeat.net/projects/highlights/)

with WindowMaker i also optionally use thin tools like:
dillo, xfe, dfm, perlpanel, xpad, wmagnify, scrot, aterm, leafpad

Michele  :KS

---

### Post by GeneW on 2007-02-23
I wish that WindowMaker was a little more supported, the development work seems to have stopped almost completely, they release an update once a year at best.  And the website is often broken, the mailing list archives never work, there's no bug tracking, etc.  I guess that the folks involved are off doing bigger an better things but you'd think that someone would take over.

Update: I just installed it and it is still my favorite window manager but it still has a few annoyances, most of which folks have mentioned here already.  Docker seems to do a good system tray application and xfe is a passable file manager.

---

### Post by Chaotic Thought on 2007-08-18
I might be the only one doing this, but you can actually run Window Maker fairly well with GNOME. I've reduce the GNOME panel in size and included only the parts that I use (such as the system tray). I find this very convenient in WM, because WM lets you hide the panel inside its appicon if you need extra screen space.

I put some screenshots in this thread
[http://ubuntuforums.org/showthread.php?t=515076&page=42&p=3192379](http://ubuntuforums.org/showthread.php?t=515076&page=42&p=3192379)

You can also do the same with nautilus--click hide (or kill) and the desktop icons temporarily disappear into the appicon.

Unfortunately, the stock **wmaker** does not include some of the interesting features (for these features you'll need to compile from source):
1. Single-click activation of appicons and miniwindows
2. Drag-and-drop support to let you drop files on appicons (still incomplete)
3. User menus (associate a custom floating menu with an application)

---

### Post by Tux Aubrey on 2007-08-19
I know that [dyne:bolic]("http://www.dynebolic.org/") (version 2.1) came with WM as its default...um..WM (with fluxbox as an alternative).  I think it has since switched to Xfce 4.4.  I really liked the dyne implementation and the wmakerconfig tool that came with it.  Everything is very accessible, customizable and fast. 

Does anyone know of any other distros that still come with WM.?

---

### Post by Chaotic Thought on 2007-08-19
SystemRescueCD uses the default Window Maker setup. However, that's a "rescue CD" so it may not be what you normally think of as a distribution. I normally use it to image hard disks and fix system problems (with Windows and Linux machines)

---

### Post by kellemes on 2007-10-11
> **GeneW said:**
> I wish that WindowMaker was a little more supported, the development work seems to have stopped almost completely, they release an update once a year at best.  And the website is often broken, the mailing list archives never work, there's no bug tracking, etc.  I guess that the folks involved are off doing bigger an better things but you'd think that someone would take over.


My thoughts exactly.. it's too bad, I love the feel and look of it, always did.
I need a wm that's supported and developing, Window Maker seems to be given up on.

---

### Post by Scimu on 2007-11-01
Ooo cool... Im downloading it as I write this. Going to try it out.. Seems good! Thanks a lot

---

### Post by jviscosi on 2007-11-01
> **kellemes said:**
> My thoughts exactly.. it's too bad, I love the feel and look of it, always did.
I need a wm that's supported and developing, Window Maker seems to be given up on.

I feel the same way.  I used WM for a good while this year and liked it quite a bit, but there were a few newer apps (XFCE ones if I remember correctly) that didn't behave nicely there.  It also got confused by Seamonkey mail and browser being the same app.  I eventually went back to Fluxbox, but I kept WM and still boot into it occasionally.  I love the tear-off menus; I have the window list sitting in the bottom left hand corner and frankly like that better than any taskbar I've ever used.

---

### Post by yizuman on 2008-03-08
This is neat, thanks for the info!

---

### Post by geneven on 2008-06-03
Other places WindowMaker works great:

Suse has a good Windowmaker setup.

Sidux, my current favorite distro, works well with WindowMaker.

Puppy Linux.

I'm currently trying it in Opengeu or some similarly named distro that is a spinoff of Ubuntu but seems primarily focused on Enlightenment.

Linux Mint.

Now, these distros don't necessarily MENTION that they work with Windowmaker, but if you go into Synaptic or apt-get or whatever and install wmaker and anything else that starts with wm or mentions windowmaker in the comments, you have a good windowmaker setup.

Come on, developers, start a new wave of windowmaker development! It is a good environment!

One application I like using it with is wmdrawer, which pops out a bunch of applications so you don't run out of slots!

I don't know why it hasn't been developed much; it's like Plane Geometry, it reached a certain state of completeness and then just stopped. I would like fluxbox or one of the other boxes, which are actually quite similar to Windowmaker, but it just seems easier. Fluxbox has a "slit," which is like the dock, but it doesn't seem to allow you to drop real applications (such as firefox) onto it.

I don't like to drop applications onto the desktop, as you can in Windows and many other environments, because they mess up the appearance of your desktop and create an air of disorderliness. And if there is anything I hate, it's riotous icons :)

Windowmaker still seems incredibly fast and easy. What more can you ask for?

---

### Post by i18n on 2009-04-09
I think it would be a good idea to have an Ubuntu distribution with WindowMaker as wm. 

There is a project called étoilé ([http://etoileos.com/](http://etoileos.com/)) with the aim to revive the WindowMaker and GNUStep, but very slow and tricky. I let it run at FreeBSD for a while, finally I went back to WindowMaker.

So, esp. for an old computer it would be the killer desktop.

---

### Post by hakimoto on 2010-12-28
Hello everyone,

I am an absolute advocate of WindowMaker but I have to say that the experience on 10.04 LTS is a bit disappointing. Maybe someone here can shed some light.

Of course WindowMaker works fine and I have wmmemmon, wmnd, wmdiskmon, wmbattery and wmclock working fine. But the VAST majority of dockapps either goes into "windowed" mode like wmcube (aaargh!) or doesn't run at all. I've installed all wmapps I could find from the repository and came up with this list:

* -1 EAGAIN (Resource temporarily unavailable)
** windowed, not windowless
*** ok

*wmacpi
*wmail
**wmavgload
***wmbattery
*wmbinclock
*wmblob
*wmbubble
*wmbutton
*wmcalclock
*wmcb
**wmcdplay
***wmclock
*wmclockmon
*wmcpu
*wmcpuload
**wmcube
*wmdate
***wmdiskmon
*wmfire
*wmfishtime
*wmforkplop
*wmfsm
*wmget
*wmhdplop
*wmibam
*wmifinfo
*wmifs
*wmitime
**wmload
*wmmand
*wmmatrix
*wmmemload
***wmmemmon
*wmmon
*wmmoonclock
***wmnd
*wmnetload
*wmpinboard
**wmscope
*wmsmpmon
*wmspaceweather
*wmsun
*wmsysmon
*wmtop
*wmtz
*wmweather+

Basically anything that doesn't have three asterisks is useless. Those with two asterisks will only run in their own window, not docked. Those with one asterisk will not run at all, strace will show:

-1 EAGAIN (Resource temporarily unavailable)

This is really annoying. Compiling from scratch will yield the same, across several different kernels. Currently I am running:

hhamdani@marzanna:~$ uname -ar
Linux marzanna 2.6.32-23-generic-pae #37-Ubuntu SMP Fri Jun 11 09:26:55 UTC 2010 i686 GNU/Linux

Does anyone have any of the above running, especially wmcube?

Thanks for any help!

---

### Post by Megaptera on 2010-12-28
As this thread started in 2005 with Ubuntu 5.10 Breezy I'm sure someone can update you as the current LTS is 10.04 Lucid ....!

---

### Post by hakimoto on 2010-12-28
That's precisely the problem. All of these wmapps are not running on 10.04 LTS.

I managed to download a .deb for a 0.98 version of wmcube which runs fine, but the latest will only do windowed mode (0.99.pre1-3).

What really interests me is this EAGAIN problem that most of the wmapps seem to have.

---

### Post by Megaptera on 2010-12-28
Are you sure it's still being developed? This looks like the latest entry on their website "posted on 2008-06-30 09:04:16 by kairi" [http://windowmaker.org/](http://windowmaker.org/)

---

