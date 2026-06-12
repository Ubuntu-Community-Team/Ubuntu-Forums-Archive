---
title: "Gnome Dock"
date: 2006-11-18
forum: Outdated Tutorials &amp; Tips
---

### Post by GPH on 2006-11-18
[http://www.gnome-dock.org/trac/wiki](http://www.gnome-dock.org/trac/wiki)

From what I understand, the project is not actively developed, but what we have for the moment is great. It is prettier than kiba-dock, more functional and also more "OS X-like". It takes more time to customize, but I think it's worth it. Here's how I installed it on Edgy with AIGLX:

**1. Install these packages**
```

sudo apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev
```[B]
2. Make sure you have build-essential to be able to compile cairo.[/B]

**3. Download Cairo 1.2.6**

[http://cairographics.org/releases/cairo-1.2.6.tar.gz](http://cairographics.org/releases/cairo-1.2.6.tar.gz)

**4. Install Cairo 1.2.6**

```
./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc
``````
make
``````
sudo make install
```**5. Download cairo-dock**

[http://www.gnome-dock.org/prerelease...-0.0.1b.tar.gz](http://www.gnome-dock.org/prerelease...-0.0.1b.tar.gz) (doesn't seem to work anymore)
Try this instead: [ATTACH]19718[/ATTACH]

**6. Extract the tarball in /opt**
[B]
7. Install cairo-dock[/B]

```
make clean
``````

make
```Also, change your virtual vertical size in Beryl from 1 to 2, otherwise it will probably bug. That's a weird fix found by someone in this thread, but it works.

To open the dock, use

```
./cairo-dock --no-glitz
```To add launchers, play with cairo-dock.c and redo
```

make
```once you've saved the file.

Also, you'll probably have to change Vertical Virtual Size in Beryl from 1 to 2 to avoid a bug.

At the moment, it only accepts icons in .svg, but it's fairly easy to convert .png to .svg using InkScape. Good luck!

[[IMG]http://img526.imageshack.us/img526/9744/capturegx4.th.jpg[/IMG]]("http://img526.imageshack.us/my.php?image=capturegx4.jpg")

---

### Post by BLTicklemonster on 2006-11-19
"make sure you have all the necessary packages to compile".. what do you mean? Oh, I see xgl and compiz, never mind.

---

### Post by GPH on 2006-11-19
No, I meant the build-essential packages, but you also need AIGLX/XGL to be able to run this. BTW, does it work for someone else than me ?

---

### Post by BLTicklemonster on 2006-11-19
After playing around with beryl for a while, watching things work arbitrarily and not work with clocklike precision, I'm pretty sure that if I have to put any kind of x-""-gl or compiz priz whatever on to use something, I'll just pass. That's a neat looking dock, but it's not worth having to put all that on my computer just for that one look.

---

### Post by jlosch on 2006-11-20
GPH, do you still have the tarball?  I'm interested in playing around with gnome-dock, but it looks like the site is having problems.

---

### Post by GPH on 2006-11-20
> **jlosch said:**
> GPH, do you still have the tarball?  I'm interested in playing around with gnome-dock, but it looks like the site is having problems.

I didn't have the original tarball, so I made one from my dock folder that also includes the icons that I use. The attachment is in the how-to.

---

### Post by jlosch on 2006-11-21
> **GPH said:**
> I didn't have the original tarball, so I made one from my dock folder that also includes the icons that I use. The attachment is in the how-to.

Thanks, that worked great.  For some reason, though, I can't seem to get the icons to show up.  Only dc++.svg seems to work.  I tried changing the file names to absolute paths in cairo-dock.c then recompiling, but no luck.  Guess I'll have to play around with it some more.

---

### Post by gjtoth on 2006-11-21
Kooldock seems to do this and works just fine under Edgy.  Very easy to configure and add stuff to.

---

### Post by christhemonkey on 2006-11-21
But Kooldock and kibadock are all written for kde, using the qt toolkit.

Whereas normal ubuntu users may not want a kde app, loading lots of extra qt libraries.

Or maybe its just me preferring to use gnome apps in gnome and kde apps in kde...

---

### Post by jlosch on 2006-11-21
Ok, I think I figured it out.  When you converted the .png files to .svg, Inkscape saved them not as true svg's, but as an svg with an embedded image.  From amarok.svg:

```
  <image
     xlink:href="/home/guillaume/.icons/OSX/scalable/apps/amarok.png"
     sodipodi:absref="/home/guillaume/.icons/OSX/scalable/apps/amarok.png"
     width="48"
     height="48"
     id="image2293"
     x="0"
     y="0" />

```

So for anyone using the tarball from the post, you'll need to find different svg icons.

Otherwise, this how-to works great.  Thanks for the files GPH!

---

### Post by _SMD on 2006-12-04
hi there!

how to make gnome-dock running on startup? i tried to put it in Startup Program ... "cd /opt/cairo-dock && ./cairo-dock --no-glitz"

but it doesn't work for me. 

tq in advance.

---

### Post by GPH on 2006-12-04
Extract this archive, go to Sessions and put the extracted file in Startup Programs.

---

### Post by cs_tech on 2006-12-11
to the op, can you please share your icons? id love to have those awesome OSX icons. :D

---

### Post by Kobalt on 2006-12-11
Thanks a bunch, it works like a charm ! 
One little questions though : I would like to have just a simple glow effect as a background for my dock, I don't want to have lines... Where is this area I must edit in cairo-dock.c ?
Thanks again :rolleyes: !

---

### Post by Tuna on 2006-12-16
ok, maybe i'm just stupid, but in the OP's instructions, it says to do 

```
./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc
```

but when i paste that into Terminal it gives me an error saying the directory doesn't exist.  i'm guessing it's just my misunderstanding of what i'm supposed to do on that step?  i've installed several apps now and never seen a command like that ](*,)

---

### Post by chojin on 2006-12-18
wow what a sloppy package this is. The bash scripts are linked to your home directory and aren't relative, there's headers missing, the svg's aren't even svg's....

don't mean to complain but seriously...

---

### Post by GPH on 2006-12-18
> **chojin said:**
> wow what a sloppy package this is. The bash scripts are linked to your home directory and aren't relative, there's headers missing, the svg's aren't even svg's....

don't mean to complain but seriously...

The original package on the author's site is down and people asked for a package. It takes about five minutes to modify it to suit your needs, so instead of complaining, you should build yourself a *better* package and submit it here. It would be much more constructive.

---

### Post by floke on 2006-12-18
Finding SVG icons is a bit of a pain.
There are some fairly nifty ones here
[http://www.gnome-look.org/content/show.php?content=43601](http://www.gnome-look.org/content/show.php?content=43601)

I'm sure there are others on the gnome-look site too, but just wanted to get the first ones I could find so that I could get the dock working:mrgreen: 

If anyone knows of any others could they post them here?
Also - does anyone know if, and how, you can run menus from the dock - otherwise it seems a bit pointless, given that you'll still need to keep hold of your panels:-k 

Still - looks good though (from what I have working so far....)

---

### Post by Kobalt on 2006-12-18
Here are some Tango svg icons if you want : 
[http://ubunteros.free.fr/tango_svg.tar.gz](http://ubunteros.free.fr/tango_svg.tar.gz)

---

### Post by pormogo on 2006-12-19
I've been meaining to try this out. I was going to use kiba dock but ran into some issues getting it configured so I guess now I'll be trying this one :)

---

### Post by Roman78 on 2006-12-23
For me it worked. But i think i mis some package, because i see the dock but no images...

---

### Post by macewan on 2006-12-26
make sure there are images where it is looking

sudo gedit /opt/cairo-dock/cairo-dock.c

note where the images are located - they end with .svg

---

### Post by Bobtheknight on 2006-12-27
It works for me, but now I need to get rid of gnome-panel because when the dock autohides, I can get it back as gnome panel gets in the way.  Anyone know how to do that?

---

### Post by superbob666 on 2006-12-27
> **Bobtheknight said:**
> It works for me, but now I need to get rid of gnome-panel because when the dock autohides, I can get it back as gnome panel gets in the way.  Anyone know how to do that?

just do that on line approx line 823 and 716
//	g_uiHideHandlerId = g_timeout_add (15, move_down, (gpointer) pWidget);

run 'make' again

---

### Post by macewan on 2006-12-27
lines 713 & 821 on the latest I've used stops the hidding

---

### Post by superbob666 on 2006-12-27
any way of starting gnome-dock at startup ???


thanks

---

### Post by Bobtheknight on 2006-12-27
It works now by moving the gnome panel to the top

Two minor issues:  

1.  If I want to use terminal, 	{"terminal.svg", "Terminal", "gnome-terminal"}, <-- with this line
it starts the terminal and I'm automatically in /opt/cairo-dock/.  Is there a way to switch it so when terminal opens I'm in ~/

2.  Is there a way to open 2 things at once from dock instead of open one thing, move mouse away so it hides, then call it up again and open other thing?

Thanks.

P.S.  Oh to start it from start-up, go to page 2 and download a script that does it.  The instructions are in the same post/page.

---

### Post by Mateo on 2007-01-01
does this disappear when you aren't using it?  i have only tried the adesklets yab Dock, but it doesn't disappear, plus it doesn't stay on top so you have to minimize everything to launch a new application.

---

### Post by Angelaki on 2007-01-04
I have install cairo-dock and it is very beautiful but i have a little problem.

1) I can't move icons or press the mouse button in screen bottom. I cant press in this screen any from this faces!!! :( :( :( 

2) The auto hide option don't work in my computer. :-k :-k :-k 

I waiting for your help!!! :-k

---

### Post by pinballkid on 2007-01-04
I've been meaning to try this out for a while now. Thanks for the howto.

Is anyone else experiencing a big black bar that cuts off the bottom of the screen in gnome (but not the panel) when the dock starts? I'd really like to get rid of it as it makes the dock a bit unusable.

---

### Post by Laterix on 2007-01-04
> **Bobtheknight said:**
> 
1.  If I want to use terminal, 	{"terminal.svg", "Terminal", "gnome-terminal"}, <-- with this line
it starts the terminal and I'm automatically in /opt/cairo-dock/.  Is there a way to switch it so when terminal opens I'm in ~/

You could try to add **--working-directory=/your/path** as command parameter.

---

### Post by DJ_Peng on 2007-01-06
I've got it running, but I can't make any changes to the dock. I manually edited cairo-dock.c but it keeps running the original set of icons, not my edited set. Any ideas why?

---

### Post by robin_liu on 2007-01-07
> **pinballkid said:**
> I've been meaning to try this out for a while now. Thanks for the howto.

Is anyone else experiencing a big black bar that cuts off the bottom of the screen in gnome (but not the panel) when the dock starts? I'd really like to get rid of it as it makes the dock a bit unusable.
i have same problem
anyone can help?

---

### Post by xlobo on 2007-01-07
I'm experiencing the same black bar problem. Does anyone know how to make it disappear? I've other problem... when I close Terminall window, the Gnome-dock closes too...

---

### Post by Steveway on 2007-01-07
You need a compositing manager to get rid of the Black border.
I would suggest you Beryl, see beryl-project.org to get informations about setting up Beryl.

---

### Post by macewan on 2007-01-07
> **Steveway said:**
> You need a compositing manager to get rid of the Black border.
I would suggest you Beryl, see beryl-project.org to get informations about setting up Beryl.

or use xcompmgr

@bobtheknight, gnome-terminal --working-directory=~/

```
 static Icon g_aIcons[] =
{
        {"gnome-fs-home.svg", "Home", "nautilus /home/macewan"},
        {"clock.svg", "Clock", "/usr/bin/cairo-clock"},
        {"web-browser.svg", "Browser", "firefox"},
        {"im.svg", "IM", "gaim"},
        {"terminal.svg", "Terminal", "**gnome-terminal --working-directory=~/**"},
        {"lockscreen.svg", "Lock", "gnome-screensaver-command --lock"},
        {"stop.svg", "Kill", "xkill"},
        {"logout.svg", "Logout", "gnome-session-save --kill"},
        {"user-trash-full.svg", "Trash", "nautilus trash:///"}
};
```@DJ Peng, after you have save cairo-dock.c you need to make again. ex.

macewan@moc:/opt/cairo-dock$ **sudo vi cairo-dock.c**

{pretend I made my changes, saved it and am now back at the prompt}

macewan@moc:/opt/cairo-dock$ **sudo make**

^^^^^^^^^^^^^^^^^^^^^^^    you forgot?

---

### Post by DJ_Peng on 2007-01-07
Not so much as forgot as never knew. I can't believe they don't have a configuration rool, but then it is an early version. Thanks for pointing it out.

ETA: Damn. You did say that in the first post, didn't you.

---

### Post by cjoey19 on 2007-01-08
great guide, but how do i exit the dock? (i used the script)

---

### Post by robin_liu on 2007-01-08
> **cjoey19 said:**
> great guide, but how do i exit the dock? (i used the script)
i use kill to exit dock 
(the default dock have it)
maybe you can try it

---

### Post by cjoey19 on 2007-01-08
thanks for pointing that out, now it will be great if there are more svg icons.........any kind soul with a great nice pack???

---

### Post by DJ_Peng on 2007-01-08
I ended up making my own from png and jpg icons, but the fact that I have to kill it so harshly makes me hesitant to keep it running all the time.

---

### Post by cjoey19 on 2007-01-09
svg made from inkscape works good? i think its ok to kill it so harshly because it doesnt save any config files (since everything is hardcoded) right?

---

### Post by DJ_Peng on 2007-01-09
I do use Inkskcape to make my svgs, but I end up having to Export the image instead of Saving it sometimes because the saved files don't always work for me.

As far as killing it via the system monitor, it may be okay since it doesn't save anything, but IMO no program should make us go that route to shut it down. It reeks of bad programming and even worse UI to me. But that's just my opinion.

---

### Post by NumberOne on 2007-01-09
I have a couple of issues with this setup, and I hope someone can help.

1.  The launch bar is only showing up on my first desktop, not on the other three.  I am loading it using sessions-startup programs.  It seems that if cairo-dock is started after beryl is started it shows up on all 4 desktops.  When entering the commands in the session window I have no control in the order in which programs load, and cairo dock always seems to load befor beryl reguardless of the order in which they are entered.  After entering the programs in sessions, if I close the sessions window and reopen, the programs change order with cairo being listed first.

How can I assure that cairo-dock loads after beryl???

2.  When I use Inkscape to convert .png files to .svg files it is saving the .svg files as a link to the original .png file.  That means I have to keep a copy of the icon in both .png and .svg format.

How do I force Inkscape to save the converted icon to a regular .svg file.

Thanks,
Tony

---

### Post by noidear on 2007-01-10
Hi

the way I got cairo-dock to load after beryl has loaded is as follows.

1. Create a script file called **gnomedock-start.sh** in your cairo-dock folder. I installed cairo-dock in the **/opt** dir so it would be

**sudo gedit /opt/cairo-dock/gnomedock-start.sh**

If you have cairo-dock installed elsewhere then change the path


2. Then enter the following into the open file gnomedock-start.sh

[B]#!/bin/bash
sleep 2
cd /opt/cairo-dock
LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH ./cairo-dock --no-glitz --no-background &[/B]

3. Save and close the file

For your info the line **sleep 2** makes the script wait for 2 seconds before running and this therefore gives beryl enough time to load before cairo-dock starts to load. If you need to you can change to the 2 to 3 or more to give more time, or experiment with reducing it to 1 and see if it still works on that setting.
The other lines are the path to cairo-dock and its libraries


4. Make gnomedock-start.sh executable as follows

**sudo chmod 755 /opt/cairo-dock/gnomedock-start.sh**


5. Finally go to System > Preferences > Sessions and click on the Startup Programs tab


6. Click on the Add button and browse to the gnomedock-start.sh file in /opt/cairo-dock


7. Reboot and watch the dock appear on all sides of beryl cube

Hope this helps :)

---

### Post by jrh on 2007-01-10
anyone using gnome-dock with bery has noticed that gnome-dock gets the the desktop focus? 

For instance, when you have two windows (two gnome-terminals for instance) and switch between the two of them (with alt+tab) then gnome-dock gets the focus (instead of switching between the two terminals). This renders gnome-dock unusable for me on my machine... :-(

Any solutions anyone?

---

### Post by spockrock on 2007-01-10
ok so to all the people having raster(.png, .jpeg etc) to vector(.svg) image problems I have two possible workarounds.

Ok first method isn't a real .svg, and is linked to a .png file, but gives you a 100% accurate image.  Grab the blank.svg I have uploaded now open it in inkscape.  import your png file, a 128x128 or 256x256 doesn't really matter but something with a good resolution.  Now the image, might be huge or blown up and pixelated looking (if it looks pixelated just ignore that it wont look like that in the end), zoom out and now resize click on the image and hold down the control 'ctrl' key and click on a diagonal double arrow, and shrink the image so it fits in the box from the blank.svg file. now 'save as' save this as an .svg  BTW plx do not resize the original png.  Now copy both the original png and new svg to /opt/cairo-dock/  or where ever you have it.  This should make the image appear properly in gnome-dock.

The second method, results in a true .svg however results my vary, Also transparency might be lost, and when restoring transparency I have seen it remove white areas from the image.
Ok so this is how you should attempt this, open blank.svg with inkscape, then import the png.  pick the png image so that it is either surrounded by resize or rotate arrows, now from the path menu pick trace bitmap, this trys to redraw the bitmap as an svg.  My only suggestion is to play with the settings use preview and then finally ok when its ready.  This will create an image with a white background, if you don't like the result delete it, and select the bitmap, and try to redraw it, if you do like it, you can now delete the bitmap. Now resize the image to fit in the box.  Also you will notice that now the background is white. you can use the edit path nodes click on the white background right click, and select delete.  This should remove the background I have also noticed this also removes any white areas of the image as well.  If you guys find a fix plx do share.  Anyways this will create a proper svg thats usable without the png. You can however create a new layer under the redrawn section and redraw a the area under the image and fill with white.

enjoy....

---

### Post by MeathooK427 on 2007-01-10
I don't know if my Compiz is messed up or what. Same deal as on Kiba-dock. Around the outside of the dock, there is a huge black rectangle area, that covers the whole bottom of the screen. Agh

Anybody have a nice command to reload Compiz?

---

### Post by jbus on 2007-01-10
So, is there a specific reason that this is no longer in development? abandonware? donationrequiredware? teaseware? 

I installed it to see how it works and I like it alot to play with, but it definitely needs some polishing before it's usable along with png support, taskbar capabilities, etc... If the original devs don't care to work on it any longer, I sure hope someone else will take over.

---

### Post by spockrock on 2007-01-10
> **MeathooK427 said:**
> I don't know if my Compiz is messed up or what. Same deal as on Kiba-dock. Around the outside of the dock, there is a huge black rectangle area, that covers the whole bottom of the screen. Agh

Anybody have a nice command to reload Compiz?

I am not sure but I believe its because you dont have xgl or aiglx running but I could be wrong........

> **jbus said:**
> So, is there a specific reason that this is no longer in development? abandonware? donationrequiredware? teaseware? 

I installed it to see how it works and I like it alot to play with, but it definitely needs some polishing before it's usable along with png support, taskbar capabilities, etc... If the original devs don't care to work on it any longer, I sure hope someone else will take over.

I dunno but its great its quick, works well, isnt annoying.....oh well.....

---

### Post by MeathooK427 on 2007-01-11
> I am not sure but I believe its because you dont have xgl or aiglx running but I could be wrong........

Nah, both enabled in xconfig. It happened with the latest nVidia drivers, I don't know if that messed with my Compiz as well or what, but the animations don't work with it now either.

---

### Post by m1215 on 2007-01-12
this is a great how to. i managed to setup xcompmgr and gnome dock with a minimal amount of effort. i didnt want all the bells and whistles of compiz or beryl. also the convert png with the blank.svg in an earlier post worked great.  im running on edgy with gnome and nvidia fx5600 ultra card. 
thanks to all for the useful info.

---

### Post by spockrock on 2007-01-13
I am glad my svg trickery worked, it took me a while with a lot of tinkering how to properly get svgs working.

---

### Post by 13warrior on 2007-01-13
Thanks.. It really helped me...  :-D

---

### Post by spockrock on 2007-01-13
any one know if its possible or how to change the icon sizes, that would be great

---

### Post by eitan_a on 2007-01-14
When you turn off autohide, you can't use a good portion of the bottom of the screen since if you click it you select an icon.  I want to fix this...any ideas??

---

### Post by pinballkid on 2007-01-15
It's a real shame that this project seems to be dead. One of the nicer tickets I saw (that hasn't been updated in 5 months!) is to make gnome-dock aware of currently running applications. I'd guess this is so you can actually replace the gnome panel with gnome-dock, which I would love!

---

### Post by DJ_Peng on 2007-01-15
That's a featuire I had hoped to find in gnome-dock,and the fact that it isn't there is part of why I stopped using it. I'd love to see it continue, in fact I'd see about helping with it if I knew anything about programming.

---

### Post by eitan_a on 2007-01-15
What's annoying is that the code behind cairo-dock is *not* that hard to edit so someone with some experience in programming for the desktop environment could fix the issues we brought up in a couple hours.  This is by far the nicest and most stable dock I've tried, and the fastest too.  

I myself will attempt to hack it but it could take a couple weeks or more before I fix the issues.  So far I have kept autohide working to make the dock useable.

I believe this dock will see much wider-spread use if someone could code a UI to edit the programs in the dock, rather than having to code it (although personally I don't care).  But if you guys want this to be included in gnome in the future, it's something to think about.

---

### Post by Grayscale on 2007-01-16
Thanks so much for this, it was a great jumpstart to figuring out how to install this.  Had absolutely no problems with your guide.  As others have requested, could you please share your icons?  Some of those look very nice.  I've been downloading icon sets myself, and customizing.  This is definately the best dock out there so far.  I really hope it starts getting developed more actively as I wish it had some settings to toggle.

---

### Post by bravus on 2007-01-16
Just to let you know:
I've started refactoring the code and I'm going to extend cairo-dock (aka gnome-dock).

What's on the agenda so far:
- png icon support
- DONE: icons can be added by placing links (*.desktop-files) in ~/.cairo-dock/ (since 0.1c)
- configuration through gconf-editor (Alt-F2, gconf-editor, apps->cairo-dock), nice configuration interface later on
- debian/ubuntu packages
- app status indicator (grayed out icons when apps are not running)
- theme support (basically for the background image, the icons will be taken from *.desktop files in ~/.cairo-dock/)
- drag and drop support (add new icons, drop something on the trash basket etc.)
- plugin engine for icons other than app launchers (e.g. clock, mail indicator, gaim applet etc.)

Any ideas for further features?

I'll let you know when ubuntu-packages are available.

---

### Post by DJ_Peng on 2007-01-16
Awesome news, bravus! Thanks! The only other things I can see I'd like to see are for it to acknowledge new programs being ru (*a la* MacOS X) and the ability to close the program without killing it in the event I want to close it temporarily.

---

### Post by dlai on 2007-01-16
This is great news, was actually going to ask if you guys at gnome-dock.org needed any help in development, because it seems no one had been working for months...

So if you do need help, say so!

---

### Post by spockrock on 2007-01-16
> **bravus said:**
> Just to let you know:
I've started refactoring the code and I'm going to extend cairo-dock (aka gnome-dock).

What's on the agenda so far:
- png icon support
- icons can be added by placing links (*.desktop-files) in ~/.cairo-dock/
- configuration through gconf-editor (Alt-F2, gconf-editor, apps->cairo-dock), nice configuration interface later on
- debian/ubuntu packages
- app status indicator (grayed out icons when apps are not running)
- theme support (basically for the background image, the icons will be taken from *.desktop files in ~/.cairo-dock/)
- drag and drop support (add new icons, drop something on the trash basket etc.)
- plugin engine for icons other than app launchers (e.g. clock, mail indicator, gaim applet etc.)

Any ideas for further features?

I'll let you know when ubuntu-packages are available.

you are my hero, I was going through the code last night and found myself a bit overwhelmed, I have done c for a couple of years, but have never done anything like this.  I am glad some one who knows what they are doing picked up cairo-dock.

---

### Post by eitan_a on 2007-01-16
> **bravus said:**
> Just to let you know:
I've started refactoring the code and I'm going to extend cairo-dock (aka gnome-dock).

What's on the agenda so far:
- png icon support
- icons can be added by placing links (*.desktop-files) in ~/.cairo-dock/
- configuration through gconf-editor (Alt-F2, gconf-editor, apps->cairo-dock), nice configuration interface later on
- debian/ubuntu packages
- app status indicator (grayed out icons when apps are not running)
- theme support (basically for the background image, the icons will be taken from *.desktop files in ~/.cairo-dock/)
- drag and drop support (add new icons, drop something on the trash basket etc.)
- plugin engine for icons other than app launchers (e.g. clock, mail indicator, gaim applet etc.)

Any ideas for further features?

I'll let you know when ubuntu-packages are available.

That' great!  I believe for this dock to be mainstream (which it should) it needs a simple easy UI.  All I can add is to fix the minor bugs already present.  The ones I can remember right now are..

- Clicking a big area above the icons runs those icons.  This makes a good chunk of the screen useless if you disable autohide.

- With autohide on, you can only open 1 program at a time..aka, open 1, hide the toolbar, then unhide it and run the next.

Those are the nagging ones I can think of right now.  I still think this is the most useable dock out there, the fastest too and it's pretty functional as is right now.

---

### Post by bravus on 2007-01-16
Hi,

did some coding today and here's what came out.

It's basically the same as before with one major improvement: You don't need to change the code to add icons. Also the icons no longer need to be in the same folder as the binary.
Last but not least you can start the binary from everywhere (including automatically at startup).

Quick Howto:
1. tar xfvz cairo-dock-0.1c.tar.gz
2. make
3. ./install.sh
4. ./cairo-dock &

You need the usual dependencies to do step 2 (compile). Look for earlier messages in this thread for details.

Should work.
To add icons take a look in the ".cairo-dock" dir right under your home-dir. The install.sh script installed some *.desktop-files there. To add an icon, just copy one of them and change the contents of the file (only Name, Icon, Exec are important).
Right now you can't control the order of the icon's appearing. Sorry for that.

Feedback appreciated.

Next to come, propably by the end of the week:
- png-support
- preferences settings using gconf
- edgy i386 deb's

Have fun with it.

---

### Post by jbus on 2007-01-16
Thanks Bravus... I'm looking forward to more of your changes.

---

### Post by dlai on 2007-01-16
very good!!!

---

### Post by eitan_a on 2007-01-16
Before you delve into this too far could you address the 2 bugs I mentioned before?  I believe that will add more usability, along with .png icons (although I have converted my sweet icons to svg)

> **bravus said:**
> Hi,

did some coding today and here's what came out.

It's basically the same as before with one major improvement: You don't need to change the code to add icons. Also the icons no longer need to be in the same folder as the binary.
Last but not least you can start the binary from everywhere (including automatically at startup).

Quick Howto:
1. tar xfvz cairo-dock-0.1c.tar.gz
2. make
3. ./install.sh
4. ./cairo-dock &

You need the usual dependencies to do step 2 (compile). Look for earlier messages in this thread for details.

Should work.
To add icons take a look in the ".cairo-dock" dir right under your home-dir. The install.sh script installed some *.desktop-files there. To add an icon, just copy one of them and change the contents of the file (only Name, Icon, Exec are important).
Right now you can't control the order of the icon's appearing. Sorry for that.

Feedback appreciated.

Next to come, propably by the end of the week:
- png-support
- preferences settings using gconf
- edgy i386 deb's

Have fun with it.

---

### Post by Grayscale on 2007-01-16
Wow, Bravus, thank you so much.  This is going to be really amazing!  Having the ability to order the icons is a must for me, so I will start testing once you get that feature knocked out.  Might try to compile later on once I get the rest of my setup complete!  Can't wait for PNG support!

---

### Post by spockrock on 2007-01-17
I love you bravus

---

### Post by plafuro on 2007-01-17
I can't wait to test the changes at home !!

Thanks Bravus !!

---

### Post by mercurysquad on 2007-01-17
Hey, great work!
I would also like to help, so let's set up a subversion repo and begin hacking! :D
[http://code.google.com/p/cairo-dock/](http://code.google.com/p/cairo-dock/) < if anyone's interested, leave me a message at mercurysquad+ubuntu@googlemail.com

---

### Post by xplode_me on 2007-01-17
mercurysquad, there's already a svn repo set up at [http://www.gnome-dock.org.]("http://www.gnome-dock.org") If you feel like you could tackle some of the code contact us at the trac.

Thanks :)

Nice work, bravus! :D Love it!

---

### Post by bravus on 2007-01-17
Hi,

**I stopped working on cairo-dock after only 1 day ;-)**

**Why?**
cairo-dock was a proof-of-concept by *macslow*. the code is really very "dirty". It would probably be possible to improve it, but I won't.

**What's next?**
I've started a new dock-project today. The working title is **udock** (u for universal). In contrast to cairo-dock udock won't concentrate on imitating the Mac OS X dock. Instead it's ment to be a serious try to go for the #1 dock in the gnome-sphere that combines the best of all existing docks, namely:
- the aspect-orientation of gimmie-dock (extended by some more aspects)
- the flexibility of kxdocker
- the graphics engine of cairo-dock
- NOT the play-around nice to have physics engine kiba-dock has

**Want to get involved?**
udock will be module-based, i.e. the items displayed on the dock are setup, drawn and controlled by modules/plugins. I call them item engines. One engine can handle multiple items. The most obvious item engine is the Application Launcher item engine. Others could be a clock engine, a mail indicator engine, a gaim display engine etc.
If you think you know what to do with an editor and a C-compiler and if you want to join in please drop me a line. cairo-background would be great.
For those who don't do coding: udock will support themes from day 1. So if you'd like to be the one to create the very first and/or the very best theme for udock, please let me know!
Themes will mainly include the background graphics and the special decoration of popup-windows.

**When will it be ready?**
I hope I'll have the core ready by the end of next weekend.

---

### Post by DJ_Peng on 2007-01-17
Wow, I didn't know cairo-dock was in that bad a shape. I can't do any programming, and I've never worked with theming (other than to mod the hell out of some themes for my blog), but when you're ready for people to start testing it I hope you let us know. I look forward to giving udock a spin, even if the training wheels are still attached.

---

### Post by spockrock on 2007-01-17
> **bravus said:**
> Hi,

**I stopped working on cairo-dock after only 1 day ;-)**

**Why?**
cairo-dock was a proof-of-concept by *macslow*. the code is really very "dirty". It would probably be possible to improve it, but I won't.

**What's next?**
I've started a new dock-project today. The working title is **udock** (u for universal). In contrast to cairo-dock udock won't concentrate on imitating the Mac OS X dock. Instead it's ment to be a serious try to go for the #1 dock in the gnome-sphere that combines the best of all existing docks, namely:
- the aspect-orientation of gimmie-dock (extended by some more aspects)
- the flexibility of kxdocker
- the graphics engine of cairo-dock
- NOT the play-around nice to have physics engine kiba-dock has

**Want to get involved?**
udock will be module-based, i.e. the items displayed on the dock are setup, drawn and controlled by modules/plugins. I call them item engines. One engine can handle multiple items. The most obvious item engine is the Application Launcher item engine. Others could be a clock engine, a mail indicator engine, a gaim display engine etc.
If you think you know what to do with an editor and a C-compiler and if you want to join in please drop me a line. cairo-background would be great.
For those who don't do coding: udock will support themes from day 1. So if you'd like to be the one to create the very first and/or the very best theme for udock, please let me know!
Themes will mainly include the background graphics and the special decoration of popup-windows.

**When will it be ready?**
I hope I'll have the core ready by the end of next weekend.

umm... no I agree the code was dirty, and really I found myself altering lines of code to see the effect.  I would like to help, I have programmed, in C, Java, C++, Assembly and various hardware specific Robot languages.  I don't really have experience in software as high level as this, except for creating a program that interfaced with robotic arm and gave the user the robo vision, and allowed for minor user tweaks to the arms.  But that was done in vb .net and that really holds your hand for alot, and I did most of the work on the robots AI, so again very hardware specific stuff.

Again I don't have much experience in the design of software that you are going for, but I would love to learn.  I would like to help, but I just wanted to be upfront with the level of coding I have done.  really alot of command line apps, never any gui programs except for the robot vision program in my final year of university.  Hopefully I can be an asset and not a burden.....

---

### Post by Grayscale on 2007-01-18
Well, Bravus, you seem like you know what you're doing, and I wish you the best of luck!  Are you going to create another thread somewhere?  If you are let us know the link ;)

---

### Post by dlai on 2007-01-18
Hey bravus, I'm really happy you took this turn... have been using gimmie as well lately, and I also liked some the ideas there. I would really like to help you on this... How can I participate... drop me a message and we are good to go.

---

### Post by jbus on 2007-01-18
This is great news Bravus! Best of luck with your work on udock. Please consider functionality similar to XFCE's iconbox  when integrating a taskbar into udock. The current gnome window list takes up way too much space and is not very aesthetic, large icons and or thumbnails would be great. Even if you are not looking to duplicate the OS X dock, borrowing a couple of good ideas from it wouldn't be a bad idea.

---

### Post by pormogo on 2007-01-18
It's awesome to see a project kinda spring up like this. :) 

I would really love to start using this dock but I am having some issues getting the dependencies installed. I followed the initial steps in this thread. Well to make a long story short here is what I ended up with. 

```
root@pleasantodor:/home/darthbator/cairo# apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
librsvg2-bin is already the newest version.
librsvg2-common is already the newest version.
librsvg2-dev is already the newest version.
libglitz-glx1 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libglitz-glx1-dev: Depends: libglitz1-dev (= 0.5.6-1) but it is not going to be installed
E: Broken packages
root@pleasantodor:/home/darthbator/cairo# apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev libglitz-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
librsvg2-bin is already the newest version.
librsvg2-common is already the newest version.
librsvg2-dev is already the newest version.
libglitz-glx1 is already the newest version.
Note, selecting libglitz1-dev instead of libglitz-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libglitz1-dev: Depends: xlibmesa-gl-dev but it is not going to be installed or
                          libgl-dev
E: Broken packages
root@pleasantodor:/home/darthbator/cairo# apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev libglitz-dev xlibmesa-gl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
librsvg2-bin is already the newest version.
librsvg2-common is already the newest version.
librsvg2-dev is already the newest version.
libglitz-glx1 is already the newest version.
Note, selecting libglitz1-dev instead of libglitz-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xlibmesa-gl-dev: Depends: libgl1-mesa-dev but it is not going to be installed
E: Broken packages
root@pleasantodor:/home/darthbator/cairo# apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev libglitz-dev xlibmesa-gl-dev libgl1-mesa-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
librsvg2-bin is already the newest version.
librsvg2-common is already the newest version.
librsvg2-dev is already the newest version.
libglitz-glx1 is already the newest version.
Note, selecting libglitz1-dev instead of libglitz-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: mesa-common-dev (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
E: Broken packages
root@pleasantodor:/home/darthbator/cairo# apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev libglitz-dev xlibmesa-gl-dev libgl1-mesa-dev mesa-common-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
librsvg2-bin is already the newest version.
librsvg2-common is already the newest version.
librsvg2-dev is already the newest version.
libglitz-glx1 is already the newest version.
Note, selecting libglitz1-dev instead of libglitz-dev
mesa-common-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: mesa-common-dev (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
E: Broken packages
root@pleasantodor:/home/darthbator/cairo# apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev libglitz-dev xlibmesa-gl-dev libgl1-mesa-dev mesa-common-dev 6.5.1+cvs20060824
Reading package lists... Done
Building dependency tree       
Reading state information... Done
librsvg2-bin is already the newest version.
librsvg2-common is already the newest version.
librsvg2-dev is already the newest version.
libglitz-glx1 is already the newest version.
Note, selecting libglitz1-dev instead of libglitz-dev
mesa-common-dev is already the newest version.
E: Couldn't find package 6.5.1+cvs20060824
root@pleasantodor:/home/darthbator/cairo# apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev libglitz-dev xlibmesa-gl-dev libgl1-mesa-dev mesa-common-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
librsvg2-bin is already the newest version.
librsvg2-common is already the newest version.
librsvg2-dev is already the newest version.
libglitz-glx1 is already the newest version.
Note, selecting libglitz1-dev instead of libglitz-dev
mesa-common-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: mesa-common-dev (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
E: Broken packages
```

However when I check to see if I have mesa-common-dev I do.

[i]darthbator@pleasantodor:~$ dpkg -l mesa-common-dev
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                Version                             Description
+++-===================================-===================================-======================================================================================
ii  mesa-common-dev                     6.5.1+cvs20060824                   Developer documentation for Mesa[/i]

---

### Post by pinballkid on 2007-01-19
Well done for taking the initiative! I'll try to help out where I can. Are you planning on setting up Trac and svn somewhere? It would make the project easier to contribute to.

---

### Post by bravus on 2007-01-19
FYI:

New version of gimmie out today:
[http://www.beatniksoftware.com/blog/?p=53]("http://www.beatniksoftware.com/blog/?p=53")

gimmie is my personal favorite at the moment.

bravus.

---

### Post by idn on 2007-01-20
I think it would be cool if it really integratd into gnome, so that there isnt a need for themes. For exmaple it should use the default gnome colours and icons. 

In beryl now there is a window thumbnail plugin that displays a mini window when you hover over the window list item in the panel, it would be cool if this was also compatible with the window list in udock

Anyway, good luck with this!

---

### Post by bravus on 2007-01-21
Hi,

I know I said I wouldn't work on cairo-dock anymore.
But I couldn't help it today and...

added png-support to cairo-dock.

Have fun with it.

Bravus.

---

### Post by BOBSONATOR on 2007-01-22
Great how to.

---

### Post by phssthpok on 2007-01-22
I've been tinkering with cairo-dock.c for a week and still haven't been able to get autohide working. 

Strangely, if I middle-click and drag-move the dock somewhere else on the screen, then when the mouse leaves the dock window, the dock snaps back to its original position at the bottom of the screen and autohides. This only works if the move results in a new x location. A new y location with the same x location does nothing. Then, when the cursor is near the bottom of the screen, the dock unhides but will not rehide without another drag-move.

By placing g_print markers in the relevant places, I've learned that move_down, on_leave_notify, and gtk_window_move are being called identically when the cursor leaves the dock area for both cases: when the dock has been moved and when it hasn't. But for some reason the dock only hides in the first case.

Any thoughts?

---

### Post by bravus on 2007-01-22
added icon-caching today. takes some time on startup to cache the icons but it's way faster now and less cpu-consuming.

try higher values for CACHE_STEPS (line 66) to make it look smoother. it will take more time at startup then.

have fun with it,
Bravus

---

### Post by eitan_a on 2007-01-22
Wow, awseome work dude!!

I would love if you could work on the auto-hide behavior, since I'd rather it not auto-hide but it's too buggy.  For instance, there's a huge section of the lower half of the screen that is unusable when auto-hide is off.

---

### Post by BLTicklemonster on 2007-01-22
So what does this do that gdesklets StarterBar doesn't do?

---

### Post by davim on 2007-01-22
Nice work I've been using kiba-dock but it's too much eye candy and too less usability (but it's getting better :) ) I would like to try udock. Is it hosted in [http://www.gnome-dock.org/trac](http://www.gnome-dock.org/trac) svn??
You could post your code in beryl forums you'll find there lots of beta testers...

here's an article on OSX doc might give you some ideas :)
[http://www.asktog.com/columns/044top10docksucks.html](http://www.asktog.com/columns/044top10docksucks.html)

---

### Post by eitan_a on 2007-01-22
> **BLTicklemonster said:**
> So what does this do that gdesklets StarterBar doesn't do?

Not suck.

Sorry but i used the gdesklet's starterbar and it was extremely buggy

---

### Post by BLTicklemonster on 2007-01-22
oic I used it but have gotten into the minimalistic aspects of fluxbox lately, and have my menu set up with everything I use frequently at the top. I just right click and pick. But I do like the way this dock looks.

---

### Post by Grayscale on 2007-01-23
Bravus, the cairo-dock updates are really nice and much appreciated!  So are you planning on continuing development of cairo-dock or are you still starting your own project?

---

### Post by bravus on 2007-01-23
No, I won't go on improving it, at least no major improvements.

But there's a little team around Karl Lattimer (the guy who drives gnome-dock.org) that's going to improve it, I think.

In udock I won't integrate any heavy visual effects like cairo-dock does in the standard release. but there's going to be a visual filter plugin interface.

Bravus.

---

### Post by dxxvi on 2007-01-23
I don't know why it's so difficult to have just an OSX-like gnome dock in Ubuntu. When I look at DreamLinux 2.2 and its dock, I wish if there were an easy way (just by apt-get-ing, not compiling anything nor touching beryl) to have it in Ubuntu. DreamLinux made it perfectly. It runs in vmware which has a very basic graphic card. I hope Ubuntu developers will take a glance at DreamLinux.

---

### Post by macewan on 2007-01-23
no hiding


*From within the directory that contains your cairo dock files

wget [http://www.macewan.org/cairo-dock.c](http://www.macewan.org/cairo-dock.c)
 sudo make
 ./cairo-dock &#8211;no-glitz

---

### Post by eitan_a on 2007-01-23
> **dxxvi said:**
> I don't know why it's so difficult to have just an OSX-like gnome dock in Ubuntu. When I look at DreamLinux 2.2 and its dock, I wish if there were an easy way (just by apt-get-ing, not compiling anything nor touching beryl) to have it in Ubuntu. DreamLinux made it perfectly. It runs in vmware which has a very basic graphic card. I hope Ubuntu developers will take a glance at DreamLinux.

How can you install this dock without downloading the whole iso?

---

### Post by Grayscale on 2007-01-23
macewan, is version including the updates bravus has done with the png support and caching, or have you just modified the original cairo-dock?

---

### Post by bravus on 2007-01-24
The dock used in Dreamlinux is Engage, which is a part of Enlightenment.

Here's the link:
[http://www.enlightenment.org/Applications/Engage/]("http://www.enlightenment.org/Applications/Engage/")

Should be possible to install it standalone. Don't ask me how, google's your best friend.

Bravus.

---

### Post by bravus on 2007-01-25
To prevent other apps to react slowly when moving the mouse over cairo-dock, try starting cairo-dock with "nice ./cairo-dock".

---

### Post by proxima estacion on 2007-01-25
Hey, So how did you resolve the issue of only being able to see the DC++ icon, I got it all working, looks great but can only get the one icon up. Any pointers or assistance would be great.

thanks.

---

### Post by bravus on 2007-01-26
Sorry, I don't know what you mean.
There's currently a bug with svg-icons. The original icons have to be 48x48 in size.
Maybe that's your problem?

Btw: The disadvantage of the nice-solution is that the processes (applications) that are spawned from the dock also run in low priority mode.
I'll fix both problems this weekend.

---

### Post by xplode_me on 2007-01-26
Mailings lists have been setup. Be sure to check gnome-dock's developers page at [http://www.gnome-dock.org/trac/wiki/Develop](http://www.gnome-dock.org/trac/wiki/Develop)

---

### Post by eitan_a on 2007-01-26
I think one major improvement to the gnome dock is if windows can be minimized to it, like the taskbar, but only show the icons (maybe a preview?) and the title.

---

### Post by gidra on 2007-01-26
Managed to do this, great dock. However when I press the show desktop icon, the dock hides. Any ideas how to avoid this ? i.e. show desktop hides all windows except gnome-dock

---

### Post by c-e-l on 2007-01-27
Hi Bravus,

There are 2 lines of code around line numbers 1184 and 1185 that seeemd to have been added recently that is preventing the background from displaying.. Not sure why the lines were added and they seem to have no purpose other than stopping the background from displaying..

The lines are:

```
gboolean autohide = gconf_client_get_bool(gConfClient, "/apps/cairo-dock/autohide", NULL);
g_bDrawBackground = gconf_client_get_bool(gConfClient, "/apps/cairo-dock/drawBackground", NULL);
```

If I comment them out I can see the background again and modifying the relevent lines (288 to 306 - TANGO_COLOR_XXXX)to match the tango.h entries allows one to change the bg colors again.. There seems to be a --no-background tag for the command line for those who do not want the background..

Another problem which I think someone mentioned is the desktop files load randomly and no order file or anything of the sort is allowed or works..

PNG support is great but if you use png files and no svg files the dock does not render correctly.. you must turn on the background to see the effect I speak of.. I did notice though that if you are using a mix of png and svg files and you are lucky enough to get the first icon in the list as a svg the dock renders correctly.. There seems to be some sort of dependency with the svg files in order to render the dock correctly with the background and the corner radius'..

Besides all the other ideas suggested I think the following would be nice..

- The ability to sectionalize the dock and add a seperator ie; (icon) (icon) (icon) | (icon) (icon)
- The ability to control the zoom level on roll over. I think the current default is too much and couldn't work out how to control it..

Anyone know why the fixed options don't seem to have any effect..

```
static gint g_iWindowWidth = 0; 					// full screen-width
static gint g_iWindowHeight = 0; 					// 3 * icon-height
static gint g_iDockWidth = 0; 						// current dock-width
static gint g_iDockHeight = 0; 

```

Thanks to all who have been trying to improve upon the dock.. It seems there has been some activity at the website and the mailing list is now working.. I hope the project takes off.. :)

Regards,
cel...........

---

### Post by bravus on 2007-01-28
Hi cel,

[LIST]
[*]think i fixed the png-only problem
[*]fixed the gconf-problem (removed the lines)
[*]added a MAGNIFICATION variable. change to lower values. I recommend turning off text labels then
[/LIST]

Use the latest svn-revision.

---

### Post by c-e-l on 2007-01-28
Thanks for the quick response bravus.. Did you incorporate the changes with the ones Karl has done before your update? 

Besides posting this here I opened tickets at the trac..

When I change the Magnification setting the dock goes into an infinite loop pegging cpu to 99%.. I must Kill to stop..

I receive the following error on compile:

cairo-dock.c: In function &#8216;main&#8217;:
cairo-dock.c:1267: warning: assignment discards qualifiers from pointer target type
cairo-dock.c:1270: warning: assignment discards qualifiers from pointer target type

Code is:

```
	            icon_filename = gtk_icon_info_get_filename (icon_info);
		        }
		      } else {
		        icon_filename = gtk_icon_info_get_filename (icon_info);

```


I'm trying to get an order file done but my coding skills are very weak with C.. Very sloppy indeed..

Is anyone having a weird issue with Beryl? When I first load the desktop the dock won't unhide.. However when I unload beryl and load metacity as window manager and then reload beryl as the window manager all works fine.. Strange.. 

Maybe it is because I'm not running Ubunutu? :shock: 

cel...........

---

### Post by bravus on 2007-01-28
strange. i have intesively experimented with the magnification factor and it never reacted like that.

there's still a bug when using svg-icons with original sizes other than 48x48. I'll fix that one soon.

the errors you get are actually warnings, not errors. Karl added those lines. afaik he's planning to work them over.

also the strange beryl-error didn't occur to me before. I use beryl, too.

adding an ordering feature is less complicated as it looks. but i'd suggest you to wait until Karl and I have done a major code-refactoring. Karl's working on a basic design template for the refactored version.

Bravus.

---

### Post by c-e-l on 2007-01-28
Thanks bravus.. 

Glad to hear a code refactoring is in the making.. :)

I'm using 100% png files for the latest version.. Maybe this is why.. I will try using only svg files and see if I get the same result.. 

Has someone condensed all the feature requests and quirks from this thread?

---

### Post by xplode_me on 2007-01-29
Fixed auto-hide.

Change line 143's FALSE to TRUE if you want to enable auto-hide.

static gboolean g_bAutoHide = FALSE;

---

### Post by eitan_a on 2007-01-29
There is an autohide bug that plagues cairo 1.3.6, where if you take away autohide, there is a big area of desktop space on the bottom that is unusable to gnome and serves the purpose of saving space for the zoomed in icons when u scroll over them.  The only workaround currently was to allow autohide to allow full use of the desktop until the dock is called for.

Is this bug still present in your revisions of cairo dock?  Where can i find the source for your revisions?  Also, have you accomplished icon ordering too?

---

### Post by xplode_me on 2007-01-29
Icon ordering is still a no-go.

You can check out latest svn source running:

svn co [http://www.gnome-dock.org/svn/](http://www.gnome-dock.org/svn/) gnome-dock

The problem with the dock taking up alot of space that is reserved for when icons zoom is still present.

---

### Post by deep.tinker77 on 2007-01-29
I would like to thank the people who put this guide together (GPH and more), and others like superbob666 and macewan for helping me fix a problem that had been killing me for about 2 days. Also, SpockRock for helping me create svg's out of any png :) . And last, but not least Bravus for picking up the project and running with it to make improvements. My desktop is almost complete thanks to all of you and when it's finished, you will all recieve my thanks again :)

---

### Post by xplode_me on 2007-01-29
deep.tinker77 you can use PNG's withouth a wraper SVG now ;)

Just try latest SVN.

---

### Post by DJ_Peng on 2007-01-29
I'm positive I asked this the other day, and I know I saw my post in the topic, but it seems to have disappeared so I'll ask again. I see these rewrites and updates are for gnome-/cairo-dock, but is there any update on the udock? Or has that been canceled in favor of fixing gnome-dock?

---

### Post by bravus on 2007-01-29
udock lives.
I use cairo-dock as some kind of sandbox for my ideas for udock.

---

### Post by DJ_Peng on 2007-01-29
Coolness. I haven't gotten the newer versions of cairo-dock because I was waiting for a test version of udock to be available. Thanks for the update.

---

### Post by c-e-l on 2007-01-29
Hi Bravus,

Any eta on a preview? 

While gnome dock is a nice start it is very tempermental.. I currently use the orginal code as I cannot run the latest code stable.. Plus along with the fact I cannot control the icon order.. I also noticed that the svg's I use with the orignal code look much crisper than with the current code..

Anyways I look forward to seeing a udock preview..

cel...........

---

### Post by bravus on 2007-01-30
Hi,

udock is not at all ready to be shown here.
And I won't release it until it's really reached a certain maturity level.

Don't think of current gnome-dock/cairo-dock as a full-blown ready-to-use dock app.
It's really only a sandbox for trying out some gimmicks and features.

I personally am working on both - udock and gnome-dock 2.0 (the refactored version). While gnome-dock 2.0 will be very graphics- and effects-oriented udock is going to be pretty conservative compared to that. gnome-dock might look like like Apple's Mac OS X dock, udock more like gimmie or the gnome panel.
while udock is meant to replace the gnome-panel, gnome-dock isn't.

Since I think release 0.0.1e or so I've integrated icon precaching in cairo-dock. That might be the reason why it doesn't look so crisp. Try to increase the CACHE_STEPS value to something between 20 and 30 and compile again.

Bravus.

---

### Post by jbus on 2007-01-30
Bravus,

Does udock have a project page where we can keep up with its progress?

---

### Post by bravus on 2007-01-30
yes and no.
yes: there's a site: [http://code.google.com/p/udock/](http://code.google.com/p/udock/)
no: it's not up to date and i don't update it frequently

---

### Post by DjBeck on 2007-01-31
I can't get gnome-dock to work ... and I bet there's something I've missed.
I'm following this guide:
[http://www.macewan.org/2007/01/11/how-to-install-cairo-dock-on-ubuntu-edgy/](http://www.macewan.org/2007/01/11/how-to-install-cairo-dock-on-ubuntu-edgy/)

But when I run this command, nothing seems to happen:
```

./configure –enable-warnings –enable-glitz –disable-quartz –disable-atsui –disable-xcb –disable-win32 –disable-gtk-doc

```

I get the following output:
```

configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: –enable-warnings
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: –enable-glitz
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: –disable-quartz
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: –disable-atsui
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: –disable-xcb
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: –disable-win32
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: –disable-gtk-doc
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for –enable-warnings-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking build system type... Invalid configuration `–enable-warnings': machine `–enable' not recognized
configure: error: /bin/bash ./config.sub –enable-warnings failed

```

Since something goes wrong there, the make - command results in
```

make: *** No targets specified and no makefile found.  Stop.

```

What am I missing here? 
Thanks in advance!

---

### Post by ErnobmaS on 2007-01-31
I was getting some similar errors. My problem was that I copied and pasted the code, instead of typing it in, and where there should be two hyphens, there was only one (longer one). Make sure your dashes are right, eg ./configure --enable-warnings... Hope that helps!

---

### Post by bravus on 2007-02-01
Hi.

For edgy (Ubuntu 6.10) skip this step and do

sudo apt-get install libcairo2-dev libcairo2

instead.

Bravus.

---

### Post by xplode_me on 2007-02-01
Be warned though, that ubuntu's cairo packages are not glitz enabled ;)

Its now possible to enable / disable auto-hide with the svn version :)

---

### Post by eitan_a on 2007-02-01
> **xplode_me said:**
> Be warned though, that ubuntu's cairo packages are not glitz enabled ;)

Its now possible to enable / disable auto-hide with the svn version :)

Is the bug where the dock takes up 30% of the bottom of the window still present in the svn version?  I think when this is fixed the gnome dock will be usable without autohide.

I think its usability will increase also if taskbarred programs are shown in the dock, only as icons with their titles (like it is in MacOSX) since with that we can almost do away with the gnome panel.

---

### Post by eitan_a on 2007-02-01
I also am wondering, is there a nice way to merge the gnome panel with gnome dock...in essence having the gnome panel with the expanding icons of the gnome dock with the useability of the gnome panel.  Has someone attempted to merge these?

---

### Post by bravus on 2007-02-01
i don't recommend to use cairo-dock w/o autohide enabled.
it always takes the whole screen's width.

again: gnome-dock in the current setup is not ment to be used as an everyday mission-critical panel-replacement.

it's just a proof of concept.

i personally don't that there's going to be a very useful dock for gnome that makes use of heavy graphical effects in the next few years. why? you can see it from 2 perspectives:
a) the current graphics hardware is too slow
b) cairo as a 2d drawing lib sucks when it comes to speed

again: my personal favorite at the moment ist gimmie dock.

Bravus.

---

### Post by DjBeck on 2007-02-01
** EDIT: Oh,  I'm sorry... the answer's a little bit earlier in the thread. Just added sleep at the top.**


[COLOR="Silver"]Finally got it working. Thanks for all your help guys. 

Only one thing left ... I'm also using Beryl, and the command "./cairo-dock --no-glitz" adds the gnome-dock to all my desktops. 

When using the startup-script (gnomedock-start.sh), which I found earlier in the thread, only one of the desktops gets the dock...how to add it to all desktops on startup?[/COLOR]

---

### Post by eitan_a on 2007-02-01
I dunno...I just tried gimmie and wasn't thrilled about it at all.  I really like the graphics of the cairo dock and it's very fast when u disable the background.  I'm going to go try the engage dock but so far I'm still coming back to the cairo dock!  

> **bravus said:**
> i don't recommend to use cairo-dock w/o autohide enabled.
it always takes the whole screen's width.

again: gnome-dock in the current setup is not ment to be used as an everyday mission-critical panel-replacement.

it's just a proof of concept.

i personally don't that there's going to be a very useful dock for gnome that makes use of heavy graphical effects in the next few years. why? you can see it from 2 perspectives:
a) the current graphics hardware is too slow
b) cairo as a 2d drawing lib sucks when it comes to speed

again: my personal favorite at the moment ist gimmie dock.

Bravus.

---

### Post by dlai on 2007-02-02
Hey Bravus,
I appreciate your work on a dock like this for gnome, but as you may have seen others have started projects like yours... e.g. gimmie or avant window navigator, maybe you should consider joining forces with them!

Best Regards

---

### Post by bravus on 2007-02-02
Thanks.
gimmie is coded in python and I simply don't know python.
awn is a project I got today right today. and believe me: it's the most professional code i've seen in a dock project yet.
but I keep coding on udock (as I said 1000 times before: cairo/gnome-dock is only a proof-of-concept sanbox for some newish features).
i build udock myself from scratch and i integrate some very new concepts.
I think there's never going to be a #1 dock for gnome. the user should be able to choose from lots of alternatives.
plus: udock is coded with maximum portability in mind. it's going to be very simple to port it to virtually every plattform that has cairo-support (linux, unix, osx, windows etc.)

---

### Post by dlai on 2007-02-04
That's just plain cool! I wish you good luck!:)

---

### Post by wingchun on 2007-02-04
hi

can someone tell me what i have to learn to try to modify cairo-dock or try to create something like this prog ?

thanks

laurent

---

### Post by bravus on 2007-02-04
C, GTK+, CAIRO

For contributing to udock, replace GTK+ with Xlib.

---

### Post by wingchun on 2007-02-04
thanks Bravus.

i really know nothing about that but if one day i"m able to contribute to something, it will be my pleasure.:) 

sorry for my english. I hope it make sence.

thanks for answer

ps: is code::block a good IDE for ubuntu ?

regards

---

### Post by GULLI.ver on 2007-02-05
Hi there! \\:D/  ... this is my first post ...

Well, in fact it isn't. I started to write a post 30 minutes ago - but than everything froze up ... f**k ATI!! ... I will try a again ...

brr... so, what did I wrote ... yeah: I wanted to say thank you for this thread and for the new dock itself. It's great, it's way faster than kiba-dock and with a few adaption I am now using the dock as an every day tool. :)

I took the source from cairo-dock-0.1e.tar.gz send by bravus two weeks ago. I do not know c (my one and only love is perl ;) ), so it took me quite a while to get through the code. Now that I understand 10% of it, I have some questions ... *g*

[LIST]
[*]I needed the dock to be somewhere else - not at the bottom. First I tried to have it at the top, but I could not convice gtk_window_move () to accept any negative values for auto-hide. **Is there any trick to do so?**
[*]So the only option was moving it to the right side of the screen. I edited dozens of variables, but after all it is working. It would be great to have a command line code to set up the "dock's gravity": --dock-bottom. --dock-right, --dock-top and --dock-left, even if there may be no way of using auto-hide in it's actual form at top or left side. I have no idea how to implement a positioning-function without rewriting the script four times or having huge if-than-else-structures. Anyway: **I guess it is much easier to implement such a positioning-function when being in an early stage of the gnome-dock project.** Later with all the "sort icons", "drag-n-drop", "change command" stuff it will be way more complicated. I attached my adapted source to this post. So if there is someone who would like to join it in the project ... [-o< 
[*]I've got a problem with Beryl. The more sensibly detection if the dock should be up (lines 715 ff) is not working at all in Beryl. In fact, the dock is not sensible at all within the outmost right 3px. I had to let the dock stick out 6px in order to get it back. (line 500) When moving the mouse all the way to the right, the dock is not responding. Only pixel 4 to 6 from the right side are sensible to the dock so that it will unhide. When switching to Metacity, the dock is sticking out about 25px and even reacting when moving the mouse all the way to the right. **Can anyone verify and explain this behaviour?**
[/LIST]

I guess, that's it for now. Well, the background is still deactivated like in the original source (line 1185 ff) - because I broke it during switching X and Y axis. But I don't want to have a background at all ... ;)

Hava a great day and many greetings from germany! :) 
... sorry for my bad english ...

---

### Post by bravus on 2007-02-06
Hi,

@wingchun:
In my opinion it's not a good idea for a beginner to use an IDE. You should either use gedit or (better) get used to emacs.
And to learn C buy yourself a good C-book (sorry, I only know some good ones that were written in German). After that (in 2 months or so) these links might be useful:
[http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)
[http://www.utas.edu.au/infosys/info/documentation/C/CStdLib.html](http://www.utas.edu.au/infosys/info/documentation/C/CStdLib.html)
[http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)
[http://developer.gnome.org/doc/API/2.0/glib/index.html](http://developer.gnome.org/doc/API/2.0/glib/index.html)
[http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html)
[http://cairographics.org/documentation](http://cairographics.org/documentation)

@GULLI.ver:
Tach erstmal. Ich mach mal in Englisch weiter, sonst versteht ja außer uns keiner was...
The dock is not meant to be for production use. It's made up mostly of trial and error code and the code is not organized at all (all stuffed into one big file).
Btw: Macslow, the original initiator of cairo-dock, is a German guy, too.

---

### Post by GULLI.ver on 2007-02-06
@bravus: lustig! :) germany, nation of the eye-candy? ;)

the dock is just to handy not to be an every-day-tool. so I will keep using it if you don't mind! 8) 

I just saw, that the widget-layer plugin from beryl 0.2.0 is working finally - so having the dock at the bottom and/or having it without a working auto-hide is ok, too. *g* ... this even solves the problem, that the dock was in focus after changing the cube-sides.

does anyone know if there are more widgets based on the cairo engine?

---

### Post by wingchun on 2007-02-06
hi all

thanks again Bravus

regards

---

### Post by eitan_a on 2007-02-06
Hey guys...just want to let everyone know that I found the perfect dock (for me), and it is kxdocker.  It has everything I want in a dock, including a window list and plugins for trash and calendar.  It's as pretty as the cairo dock and is configurable.  It is much more functional as a panel replacement.

The hardest part to make it work was compiling the source and the plugins, since it's a kde app.  This took me 2 days.  After that, I needed to figure out how to configure the icons and stuff.  I still have work to do, and I think I will need to hack the config file to get the ordering of the icons to my taste (they are random right now).

Anyways, after succesfully running this bit on gnome, I'd like to help anyone else who tried kxdocker once before and gave up (like I did) since it wouldn't install/compile/run.  

The plugins worth using are trash, clock (although this takes up a good amount of cpu), calendar, and task manager.

---

### Post by iiker on 2007-02-06
got this error
configure: error: requested PNG backend could not be enabled
what to do?

---

### Post by bellemerlord on 2007-02-07
Hi

how do i include the Shutdown-menu and the Thrash into the dock? What are the settings for the .desktop Files?

THx

---

### Post by ilantz on 2007-02-11
You guys blasted me off with the enthusiastic !
I love the fixes you guys did & waiting patiently for the next ones :)   

this how-to made it quite simple to complie the source too. 
but adding the latest svn source caused a make error :

cairo-dock.c:62:32: error: gconf/gconf-client.h: No such file or directory

sudo cp /usr/include/gconf/2/gconf/*.h /usr/include/gconf/
- this solved the issue & the source compiled with 2 warnings: 

cairo-dock.c: In function &#8216;main&#8217;:
cairo-dock.c:1271: warning: assignment discards qualifiers from pointer target type
cairo-dock.c:1274: warning: assignment discards qualifiers from pointer target type

besides that all is sweet !!
n00b running on edgy + beryl.

p.s.:

> **eitan_a said:**
> Anyways, after succesfully running this bit on gnome, I'd like to help anyone else who tried kxdocker once before and gave up (like I did) since it wouldn't install/compile/run.  

i'd like that !! no-go here until now..

---

### Post by jeyaganesh on 2007-02-13
Hallo everything goes fine. but in my dock there is only DC++ icon. there are no icon picture for some launchers (like firefox, gimp - there are only file names) in /opt/cairo-dock too. Could anyone please explain me how to add/delete icons to the dock. I will appreciate it.

:-({|= :-({|= :-({|= :-({|=

---

### Post by jeyaganesh on 2007-02-13
I found extracted cairo-dock.tar.gz file download from macewan.org and the first post of this thread itself has no icon picture for most of the launchers. I feel thats why my dock has no icons.

---

### Post by black_eye on 2007-02-15
How do you turn auto hide off. I changed this line: static gboolean autoHide = FALSE; did make again but the dock still hides. What goes wrong?

---

### Post by macewan on 2007-02-19
[I][SIZE=1]> **black_eye said:**
> How do you turn auto hide off. I changed this line: static gboolean autoHide = FALSE; did make again but the dock still hides. What goes wrong?
[/SIZE][/I][SIZE=1][SIZE=2]
@black_eye, don't forget to Google a subject before asking. :)
[/SIZE][/SIZE] 
[Answer]("http://www.macewan.org/2006/12/27/howto-stop-cairo-dock-from-hiding/#comment-26734")

cd /opt/cairo-dock
 sudo gedit /opt/cairo-dock/cairo-dock.c
 lines 713 and 821 (on my version) contain the following line:
 g_uiHideHandlerId = g_timeout_add (15, move_down, (gpointer) pWidget);
 simply comment them out to stop autohide:
 // g_uiHideHandlerId = g_timeout_add (15, move_down, (gpointer) pWidget);
 sudo make
 ./cairo-dock &#8211;no-glitz

---

### Post by kragen on 2007-02-20
this dock is awesome, my only quibble is that I keep on managing to close it with Alt-f4, any way to stop that happening?

---

### Post by jfinkels on 2007-02-21
I followed the instructions on the gnome-dock Trac for building and installing, but it doesn't say anything about how to add or edit .desktop files. Can someone enlighten me as to how .desktop files work, or post an example, please? Thanks.

---

### Post by cjoey19 on 2007-02-22
guys, i got some problem compiling the lastest svn and also the cairo-dock 0.1e tarball..

here is d error message

```
joey@shadowUbuntu:~/cairo-dock-0.1e$ make
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx gconf-2.0`   `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx gconf-2.0` -lm  cairo-dock.c   -o cairo-dock
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
cairo-dock.c:43:19: error: cairo.h: No such file or directory
cairo-dock.c:44:25: error: pango/pango.h: No such file or directory
cairo-dock.c:45:28: error: gdk/gdkkeysyms.h: No such file or directory
cairo-dock.c:46:21: error: gtk/gtk.h: No such file or directory
cairo-dock.c:47:26: error: librsvg/rsvg.h: No such file or directory
cairo-dock.c:48:32: error: librsvg/rsvg-cairo.h: No such file or directory
cairo-dock.c:59:32: error: gconf/gconf-client.h: No such file or directory
cairo-dock.c:70: error: expected specifier-qualifier-list before ‘gchar’
cairo-dock.c:90: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:91: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:93: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_DimensionData’
cairo-dock.c:94: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iScreenHeight’
cairo-dock.c:95: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iCurrentWidth’
cairo-dock.c:96: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iCurrentHeight’
cairo-dock.c:97: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bClicked’
cairo-dock.c:102: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_uiRedraws’
cairo-dock.c:103: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_uiEvents’
cairo-dock.c:104: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_uiTimeoutHandlerId’
cairo-dock.c:105: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_uiHideHandlerId’
cairo-dock.c:113: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iWindowMove’
cairo-dock.c:114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iAtBottom’
cairo-dock.c:116: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iWindowPositionX’
cairo-dock.c:117: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iWindowPositionY’
cairo-dock.c:118: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iWindowWidth’
cairo-dock.c:119: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iWindowHeight’
cairo-dock.c:120: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iDockLineWidth’
cairo-dock.c:121: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iDockRadius’
cairo-dock.c:122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iDockWidth’
cairo-dock.c:123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iDockHeight’
cairo-dock.c:124: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iDockOffsetX’
cairo-dock.c:125: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iDockOffsetY’
cairo-dock.c:126: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_fGradientOffsetX’
cairo-dock.c:127: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iInfluenceGlobal’
cairo-dock.c:129: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bDrawBackground’
cairo-dock.c:130: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bUseIconBuffering’
cairo-dock.c:131: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bUseText’
cairo-dock.c:132: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bKeepAbove’
cairo-dock.c:133: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bSkipPager’
cairo-dock.c:134: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bSkipTaskbar’
cairo-dock.c:135: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bSticky’
cairo-dock.c:136: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘autoHide’
cairo-dock.c:145: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bUseBenchmark’
cairo-dock.c:148: error: expected ‘)’ before ‘fX’
cairo-dock.c:149: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘shrink_down’
cairo-dock.c:150: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘grow_up’
cairo-dock.c:151: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘clicked’
cairo-dock.c:152: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘none_clicked’
cairo-dock.c:155: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:158: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:198: error: expected ‘)’ before ‘*’ token
cairo-dock.c: In function ‘get_first_icon’:
cairo-dock.c:212: error: ‘icons’ undeclared (first use in this function)
cairo-dock.c:212: error: (Each undeclared identifier is reported only once
cairo-dock.c:212: error: for each function it appears in.)
cairo-dock.c:212: error: invalid type argument of ‘->’
cairo-dock.c: In function ‘get_last_icon’:
cairo-dock.c:216: error: ‘icons’ undeclared (first use in this function)
cairo-dock.c:216: error: invalid type argument of ‘->’
cairo-dock.c: At top level:
cairo-dock.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_current_dock_width’
cairo-dock.c:230: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_dock_offset_y’
cairo-dock.c:236: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_current_dock_offset_x’
cairo-dock.c:242: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_current_dock_offset_y’
cairo-dock.c:248: error: expected ‘)’ before ‘*’ token
cairo-dock.c:423: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘move_up’
cairo-dock.c:463: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘move_down’
cairo-dock.c:512: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_expose’
cairo-dock.c:531: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_configure’
cairo-dock.c:555: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_key_press’
cairo-dock.c:595: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_button_press’
cairo-dock.c:660: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_motion_notify’
cairo-dock.c:791: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_enter_notify’
cairo-dock.c:813: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘benchmark’
cairo-dock.c:829: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_leave_notify’
cairo-dock.c:858: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘none_clicked’
cairo-dock.c:870: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘clicked’
cairo-dock.c:900: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘grow_up’
cairo-dock.c:924: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘shrink_down’
cairo-dock.c:945: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘scale’
cairo-dock.c:959: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘scaleIntegral’
cairo-dock.c:974: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘scaledPosition’
cairo-dock.c:980: error: expected ‘)’ before ‘fMouseX’
cairo-dock.c:1052: error: expected ‘)’ before ‘*’ token
cairo-dock.c:1103: error: expected ‘)’ before ‘*’ token
cairo-dock.c:1170: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘spit_out_redraws’
cairo-dock.c: In function ‘main’:
cairo-dock.c:1183: error: ‘GConfClient’ undeclared (first use in this function)
cairo-dock.c:1183: error: ‘gConfClient’ undeclared (first use in this function)
cairo-dock.c:1184: error: ‘gboolean’ undeclared (first use in this function)
cairo-dock.c:1184: error: expected ‘;’ before ‘autohide’
cairo-dock.c:1185: error: ‘g_bDrawBackground’ undeclared (first use in this function)
cairo-dock.c:1188: error: ‘icons’ undeclared (first use in this function)
cairo-dock.c:1189: error: ‘gchar’ undeclared (first use in this function)
cairo-dock.c:1189: error: ‘home_dir_fn’ undeclared (first use in this function)
cairo-dock.c:1190: error: ‘cairo_dir’ undeclared (first use in this function)
cairo-dock.c:1199: error: ‘file_rel_fn’ undeclared (first use in this function)
cairo-dock.c:1201: error: ‘file_abs_fn’ undeclared (first use in this function)
cairo-dock.c:1202: error: ‘GKeyFile’ undeclared (first use in this function)
cairo-dock.c:1202: error: ‘keyfile’ undeclared (first use in this function)
cairo-dock.c:1203: error: ‘G_KEY_FILE_NONE’ undeclared (first use in this function)
cairo-dock.c:1204: error: expected expression before ‘Icon’
cairo-dock.c:1204: warning: initialization makes pointer from integer without a cast
cairo-dock.c:1205: error: ‘icon_filename’ undeclared (first use in this function)
cairo-dock.c:1209: error: ‘Icon’ has no member named ‘acFileName’
cairo-dock.c:1211: error: ‘Icon’ has no member named ‘acName’
cairo-dock.c:1212: error: ‘Icon’ has no member named ‘acCommand’
cairo-dock.c:1219: error: ‘GtkWidget’ undeclared (first use in this function)
cairo-dock.c:1219: error: ‘pWindow’ undeclared (first use in this function)
cairo-dock.c:1220: error: ‘GdkScreen’ undeclared (first use in this function)
cairo-dock.c:1220: error: ‘gdkscreen’ undeclared (first use in this function)
cairo-dock.c:1222: error: ‘GError’ undeclared (first use in this function)
cairo-dock.c:1222: error: ‘pError’ undeclared (first use in this function)
cairo-dock.c:1223: error: ‘guint’ undeclared (first use in this function)
cairo-dock.c:1223: error: expected ‘;’ before ‘uiHandlerId’
cairo-dock.c:1224: error: expected ‘;’ before ‘uiBenchmarkId’
cairo-dock.c:1225: error: ‘cairo_t’ undeclared (first use in this function)
cairo-dock.c:1225: error: ‘pCairoContext’ undeclared (first use in this function)
cairo-dock.c:1226: error: ‘gint’ undeclared (first use in this function)
cairo-dock.c:1226: error: expected ‘;’ before ‘i’
cairo-dock.c:1231: error: ‘i’ undeclared (first use in this function)
cairo-dock.c:1234: error: ‘g_bUseBenchmark’ undeclared (first use in this function)
cairo-dock.c:1234: error: ‘TRUE’ undeclared (first use in this function)
cairo-dock.c:1251: error: ‘g_bUseText’ undeclared (first use in this function)
cairo-dock.c:1251: error: ‘FALSE’ undeclared (first use in this function)
cairo-dock.c:1253: error: ‘g_bUseIconBuffering’ undeclared (first use in this function)
cairo-dock.c:1255: error: ‘g_bKeepAbove’ undeclared (first use in this function)
cairo-dock.c:1257: error: ‘g_bSkipPager’ undeclared (first use in this function)
cairo-dock.c:1259: error: ‘g_bSkipTaskbar’ undeclared (first use in this function)
cairo-dock.c:1261: error: ‘g_bSticky’ undeclared (first use in this function)
cairo-dock.c:1266: error: expected ‘;’ before ‘help’
cairo-dock.c:1267: error: ‘help’ undeclared (first use in this function)
cairo-dock.c:1278: error: ‘GList’ undeclared (first use in this function)
cairo-dock.c:1278: error: ‘ic’ undeclared (first use in this function)
cairo-dock.c:1282: error: ‘Icon’ has no member named ‘acFileName’
cairo-dock.c:1283: error: ‘Icon’ has no member named ‘pHandle’
cairo-dock.c:1283: error: ‘Icon’ has no member named ‘acFileName’
cairo-dock.c:1284: error: ‘Icon’ has no member named ‘pHandle’
cairo-dock.c:1284: error: ‘g_DimensionData’ undeclared (first use in this function)
cairo-dock.c:1285: error: ‘Icon’ has no member named ‘fWidth’
cairo-dock.c:1285: error: ‘gdouble’ undeclared (first use in this function)
cairo-dock.c:1285: error: expected ‘;’ before ‘g_DimensionData’
cairo-dock.c:1286: error: ‘Icon’ has no member named ‘fHeight’
cairo-dock.c:1286: error: expected ‘;’ before ‘g_DimensionData’
cairo-dock.c:1287: error: ‘Icon’ has no member named ‘bClicked’
cairo-dock.c:1288: error: ‘Icon’ has no member named ‘fPeriod’
cairo-dock.c:1291: error: ‘Icon’ has no member named ‘acFileName’
cairo-dock.c:1292: error: ‘Icon’ has no member named ‘bClicked’
cairo-dock.c:1293: error: ‘Icon’ has no member named ‘fPeriod’
cairo-dock.c:1298: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
cairo-dock.c:1300: error: ‘g_iCurrentWidth’ undeclared (first use in this function)
cairo-dock.c:1302: error: ‘g_iWindowWidth’ undeclared (first use in this function)
cairo-dock.c:1303: error: ‘g_iWindowHeight’ undeclared (first use in this function)
cairo-dock.c:1303: error: ‘Icon’ has no member named ‘fHeight’
cairo-dock.c:1370: error: ‘g_iCurrentHeight’ undeclared (first use in this function)
cairo-dock.c:1371: error: ‘g_iScreenHeight’ undeclared (first use in this function)
cairo-dock.c:1372: error: ‘g_iWindowPositionX’ undeclared (first use in this function)
cairo-dock.c:1373: error: ‘g_iWindowPositionY’ undeclared (first use in this function)
cairo-dock.c:1378: error: ‘GDK_BUTTON_PRESS_MASK’ undeclared (first use in this function)
cairo-dock.c:1379: error: ‘GDK_POINTER_MOTION_MASK’ undeclared (first use in this function)
cairo-dock.c:1380: error: ‘GDK_POINTER_MOTION_HINT_MASK’ undeclared (first use in this function)
cairo-dock.c:1391: error: ‘gtk_main_quit’ undeclared (first use in this function)
cairo-dock.c:1395: error: ‘on_expose’ undeclared (first use in this function)
cairo-dock.c:1399: error: ‘on_configure’ undeclared (first use in this function)
cairo-dock.c:1403: error: ‘on_key_press’ undeclared (first use in this function)
cairo-dock.c:1407: error: ‘on_button_press’ undeclared (first use in this function)
cairo-dock.c:1411: error: ‘on_motion_notify’ undeclared (first use in this function)
cairo-dock.c:1415: error: ‘on_enter_notify’ undeclared (first use in this function)
cairo-dock.c:1419: error: ‘on_leave_notify’ undeclared (first use in this function)
cairo-dock.c:1476: error: expected ‘;’ before ‘fEnd’
cairo-dock.c:1480: error: ‘fEnd’ undeclared (first use in this function)
cairo-dock.c:1480: error: ‘Icon’ has no member named ‘fWidth’
cairo-dock.c:1483: error: ‘iInfluenceGlobal’ undeclared (first use in this function)
cairo-dock.c:1492: error: ‘uiHandlerId’ undeclared (first use in this function)
cairo-dock.c:1492: error: ‘spit_out_redraws’ undeclared (first use in this function)
cairo-dock.c:1493: error: ‘uiBenchmarkId’ undeclared (first use in this function)
cairo-dock.c:1493: error: ‘benchmark’ undeclared (first use in this function)
cairo-dock.c:1493: error: ‘gpointer’ undeclared (first use in this function)
cairo-dock.c:1493: error: expected ‘)’ before ‘pWindow’
cairo-dock.c:1507: error: ‘Icon’ has no member named ‘pHandle’
cairo-dock.c:1508: error: ‘Icon’ has no member named ‘pIconBuffer’
cairo-dock.c: At top level:
cairo-dock.c:1516: error: expected ‘)’ before ‘*’ token
cairo-dock.c:1594: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [cairo-dock] Error 1
joey@shadowUbuntu:~/cairo-dock-0.1e$ 

```

any ideas? i used to be able to compile the dock before i reinstalled ubuntu on my desktop..

---

### Post by bravus on 2007-02-22
Hi,

look for desktop-files in /usr/share/applications and just copy them to the .cairo-dock subfolder of your home-folder (e.g. /home/jfinkels/.cairo-dock).

> **jfinkels said:**
> I followed the instructions on the gnome-dock Trac for building and installing, but it doesn't say anything about how to add or edit .desktop files. Can someone enlighten me as to how .desktop files work, or post an example, please? Thanks.

---

### Post by bravus on 2007-02-22
Hi,

are you sure you installed the lib[xyz]-dev packages of gtk, cairo and rsvg?

If so please post the output of the following commad:
pkg-config --libs --cflags cairo gtk+-2.0 librsvg-2.0

> **cjoey19 said:**
> 
cairo-dock.c:43:19: error: cairo.h: No such file or directory
cairo-dock.c:44:25: error: pango/pango.h: No such file or directory
cairo-dock.c:45:28: error: gdk/gdkkeysyms.h: No such file or directory
cairo-dock.c:46:21: error: gtk/gtk.h: No such file or directory
cairo-dock.c:47:26: error: librsvg/rsvg.h: No such file or directory
cairo-dock.c:48:32: error: librsvg/rsvg-cairo.h: No such file or directory
cairo-dock.c:59:32: error: gconf/gconf-client.h: No such file or directory


---

### Post by ilantz on 2007-02-22
Hi Bravus !!

good to see you still checking up in here :)
any news regarding gnome-dock/udock ??

best regards

---

### Post by jfinkels on 2007-02-22
> **bravus said:**
> Hi,

look for desktop-files in /usr/share/applications and just copy them to the .cairo-dock subfolder of your home-folder (e.g. /home/jfinkels/.cairo-dock).

Thank you very much!

---

### Post by Canes on 2007-02-23
> **kragen said:**
> this dock is awesome, my only quibble is that I keep on managing to close it with Alt-f4, any way to stop that happening?

Try this : [http://www.sandaru1.com/2007/02/21/another-eye-candy-gadjet-to-my-linux-box-installing-cairo-dock-in-ubuntu-edgy-610/](http://www.sandaru1.com/2007/02/21/another-eye-candy-gadjet-to-my-linux-box-installing-cairo-dock-in-ubuntu-edgy-610/)

---

### Post by Jens Johansson on 2007-02-23
Hi guys, Ok I got the dock to work, new icons / launchers and every thing worked great, until I wanted to add it to the startup.
I used the scrips on page 5 but when when it starts after reboot I get the original dock again with only the dc++ icon visible.
The original cairo-dock.c script doesn't even exists but The dock is loading the info from the original file... 

So, I am very confused at the moment

---

### Post by cjoey19 on 2007-02-23
the output to pkg-config --libs --cflags cairo gtk+-2.0 librsvg-2.0

```

joey@shadowUbuntu:~$ pkg-config --libs --cflags cairo gtk+-2.0 librsvg-2.0
-I/usr/local/include/cairo -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/librsvg-2  -L/usr/local/lib -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lrsvg-2 -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
joey@shadowUbuntu:~$
```


edit: problem solved! thanks guys, i found out i didnt install libgconf2.

---

### Post by johnceo on 2007-02-23
> **Canes said:**
> Try this : [http://www.sandaru1.com/2007/02/21/another-eye-candy-gadjet-to-my-linux-box-installing-cairo-dock-in-ubuntu-edgy-610/](http://www.sandaru1.com/2007/02/21/another-eye-candy-gadjet-to-my-linux-box-installing-cairo-dock-in-ubuntu-edgy-610/)

This link worked fine for me for resloving both DC++ icon problem and startup issues.

---

### Post by olavjunior on 2007-02-24
Can I get the dock to show open windows? Like object-dock in windows?

Any better docks coming around? I find it difficult to change quality of the svg-files. Would be better if they just were png I think.

Well eoungh fiklin' today - this **** takes time! ;)

---

### Post by bravus on 2007-02-24
**_Yet another cairo-dock installation howto_**

NOTE: this version of cairo-dock is known to be very very buggy. So don't use it in production!!!

requirements for this to work:
- you need to run a x86 version of ubuntu (not amd64!!!)
- you need to have xgl running
- you need to have beryl or compiz or xcompmgr running

```
wget http://udock.googlecode.com/files/cairodock_0.0.1e-1_i386.deb
sudo dpkg -i cairodock_0.0.1e-1_i386.deb
mkdir ~/.cairo-dock
cd /usr/share/applications
cp firefox.desktop ~/.cairo-dock/
```
repeat the last line for all apps you'd like to see in the dock (replace firefox by e.g. xmms) [1]

start by typing cairo-dock

[1] important: this only works for .desktop-files that use PNG or SVG images as icons. You can check that with this command:
grep Icon <yourfile>.desktop
To include custom apps create your own .desktop-files in ~/.cairo-dock. They need to have a [Desktop Entry] section with key-value-pairs for Name, Exec and Icon

**_FAQ:_**
Q: *How can I influence the Icons' order*
A: *Not at all*

Q: *What command-line args are valid?*
A: *--no-background and --benchmark, the others are buggy in this version*

Q: *How can I start it at startup?*
A: *System->Settings->Sessions->[3rd tab]->Add*

Q: *When will cairo-dock be ready for production use?*
A: *Never. cairo-dock is a proof-of-concept demo and not ment to be used in production.*

Q: *What are good alternatives?*
A: *awn, gimmie, kiba-dock (see google)*

Q: *Is anything similar to cairo-dock in the pipe?*
A: *gnome-dock is the follow-up projet. see [http://www.gnome-dock.org](http://www.gnome-dock.org)*

Q: *How do I uninstall it?*
A: *sudo dpkg --purge cairodock*

---

### Post by olavjunior on 2007-02-24
Useful! Thanks. 

But what's the program that shows open windows?

---

### Post by bravus on 2007-02-24
There's beryl-plugin that makes gnome-panel show a live preview when hovering over the task items.

Also kiba-dock's latest revision has a live preview feature.

And finally awn shows open windows, but no live preview.
Don't ask for urls or howtos. Google is your best friend.

> **olavjunior said:**
> Useful! Thanks. 

But what's the program that shows open windows?

---

### Post by eitan_a on 2007-02-26
I'd say kxdocker is the most similar to gnome dock (cairo dock was written as a proof of concept to kxdocker to make it run on gnome, but kxocker runs on gnome now so..).  It shows opened windows and has the ability to show window previews but it doesn't work in the current version.  I think it'd help the community out if people could work on kxdocker instead of gnome dock, but no one listens to me..

---

### Post by kragen on 2007-02-26
I'm not a KDE fan, and for me, kxdocker epiphanises all that I dislike about KDE, I also hate having the KDE libraries on my computer. Dont get me wrong - kxdocker looks like a great app, that the average KDE user would be more than happy with, but I want a gnome app, made with the gnome philosophy in mind, and definitely with no dependency on KDE libraries.

Besides, as bravus has stated, this is merely a proof of concept test, for me it's simply a stop-gap while I wait for someone to write a proper gnome dock :D

EDIT: Oh yeah, forgot to say: thanks loads for the link, I dont have time to try it now, but it looks very promising. I will be sure to give it a try tomorrow :)

---

### Post by bravus on 2007-02-27
@Canes: I agree. And udock is making good progress ;-)

@Jens: I understand your concerns. You're right: Time and Efforts shouldn't be spent on multiple projects but concentrated on one particual. That's exactly the idea of udock: Udock is supposed to be most flexible regarding the platform. Everything platform dependend is packed in libraries and loaded at runtime. That means you'll be able to call udock --platform=gtk and you'll get the gtk version with gtk-preferences menu and integration in gconf etc. if you prefer qt, you just type udock --platform=qt and you'll get qt functions. In windows environments the platform would be win32 and the windows registry would be used for preferences storage.
Also the plugins (applauncher, clock, taskbar etc.) will be useable on multiple platforms.
I think the multi-platform approach is better than the "use qt-apps in gnome" approach.
All that is possible because the core (drawing) of udock is cairo and cairo is availble on many platforms.
Got the idea?

---

### Post by olavjunior on 2007-03-01
The dock is great! I love it :) (Much better then object dock wich I'm used to)

But I wan't to add Matlab to my dock. The problem is that Matlab has to be run trough the terminal. So what's the code for that?

---

### Post by spockrock on 2007-03-01
> **olavjunior said:**
> The dock is great! I love it :) (Much better then object dock wich I'm used to)

But I wan't to add Matlab to my dock. The problem is that Matlab has to be run trough the terminal. So what's the code for that?

matlab -desktop

and it will work.... :)

---

### Post by jonah1980 on 2007-03-01
why hasn't this got packaged up in a deb properly for everyone by now, it's just what feisty needs to take ubuntu forward

---

### Post by davim on 2007-03-02
Has anyone heard of AWN (avant-window-manager)? it's still in early development state but it's very stable, has cool features and looks very promising.

For more information see -> [http://awn.wetpaint.com/](http://awn.wetpaint.com/)

---

### Post by jonah1980 on 2007-03-03
tried it but it sat in a really weird place on the screen and cos didnt have beryl on at moment i couldnt move it and didnt work right. gonna stick with gdesklets for now. shame no system tray integrated into these dockers though, gnome dock looks like it will be the coolest if ever gets finished

also how do i uninstall avant window navigator now i've got it installed?

---

### Post by Quickdood on 2007-03-06
I am thinking of trying gnome dock.  I was wondering do active programs minimize to the dock?

---

### Post by eitan_a on 2007-03-06
no they don't

---

### Post by Quickdood on 2007-03-06
Maybe I can use avant windows manager and gnome dock together. This would be kind of cool because avant is for only active applications and apps minimize to it, and gnome is a good launcher.

---

### Post by flargen on 2007-03-06
> **Quickdood said:**
> Maybe I can use avant windows manager and gnome dock together. This would be kind of cool because avant is for only active applications and apps minimize to it, and gnome is a good launcher.

That is untrue. Avant window navigator CAN launch apps - try dragging a menu item to the dock.

---

### Post by jonah1980 on 2007-03-06
i wouldnt use avant-window-navigator as i can't uninstall or get rid of it now i've installed it!

---

### Post by tlacuache on 2007-03-08
I've been using Avant Window Navigator for a few days now and I'm really liking it a lot. Finally I have  my launchers and my taskbar icons all on the same dock!

As was mentioned, though, it does require a composite manager (beryl), and I'm not running beryl on my laptop, so I can't enjoy it there.

I didn't have any problems at all installing awn, personally. I just followed this howto:

[http://ubuntuforums.org/showthread.php?t=351186&highlight=avant+window+navigator](http://ubuntuforums.org/showthread.php?t=351186&highlight=avant+window+navigator)

I did it using the SVN method because I think the posted .tgz didn't include the launcher capabilities, at least when I grabbed it.

-SG

---

### Post by steve101101 on 2007-03-13
I got through the install without any troubles. however when i launch the dock the only icon i can see is the dc++ one. also the terminal also has these errors

steve@Ubuntu:/opt/cairo-dock$ ./cairo-dock --no-glitz
        
** (process:5082): WARNING **: Unknown error forking main binary / abnormal early exit ...

** (process:5066): WARNING **: Unknown error forking main binary / abnormal early exit ...

i can click on the appropriate places where the icons should be to launch the programs. 

please help.

---

### Post by philipho on 2007-03-14
Hi,

In the original post it said i am supposed to Extract the tarball in /opt, however, i am getting access denied errors. May i know what can i do to overcome that?

---

### Post by steve101101 on 2007-03-14
extract the folder on the desktop to then use the following command

```
sudo mv /home/username/Desktop/cairo-dock /opt/cairo-dock
```

cairo-dock is the name of the extracted folder and username is your name

---

### Post by philipho on 2007-03-14
> **steve101101 said:**
> extract the folder on the desktop to then use the following command

```
sudo mv /home/username/Desktop/cairo-dock /opt/cairo-dock
```

cairo-dock is the name of the extracted folder and username is your name

Thank you..

---

### Post by steve101101 on 2007-03-14
I got through the install without any troubles. however when i launch the dock the only icon i can see is the dc++ one. 

please help

---

### Post by rewrittenfromscratch on 2007-03-15
Okay. I'm a new Ubuntu user, so forgive me if this is an easy problem, but I can't seem to install gnome-dock.

I keep getting the same results every time.

[PHP]ken@lappy486:/opt/cairo-dock$ make clean
rm -f *.o *~ cairo-dock
ken@lappy486:/opt/cairo-dock$ make
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
cairo-dock.c:52:25: error: cairo-glitz.h: No such file or directory
cairo-dock.c: In function ‘dock_cairo_create’:
cairo-dock.c:189: warning: assignment makes pointer from integer without a cast
make: *** [cairo-dock] Error 1
[/PHP]

---

### Post by steve101101 on 2007-03-15
> **GPH said:**
> Extract this archive, go to Sessions and put the extracted file in Startup Programs.

Can you be more specific on how to do this thanks.

---

### Post by steve101101 on 2007-03-15
never mind i got it.

---

### Post by steve101101 on 2007-03-15
does anyone know how to change the default programs that are in the gnome dock and add new ones???

i cannot seem to right click it.

---

### Post by joyolee on 2007-03-18
@steve101101  


u can delete or create your own *.desktop file in  ~/.cairo-dock

---

### Post by anssi on 2007-03-26
> **bravus said:**
> **_Yet another cairo-dock installation howto_**

NOTE: this version of cairo-dock is known to be very very buggy. So don't use it in production!!!

requirements for this to work:
- you need to run a x86 version of ubuntu (not amd64!!!)
- you need to have xgl running
- you need to have beryl or compiz or xcompmgr running

```
wget http://udock.googlecode.com/files/cairodock_0.0.1e-1_i386.deb
sudo dpkg -i cairodock_0.0.1e-1_i386.deb
mkdir ~/.cairo-dock
cd /usr/share/applications
cp firefox.desktop ~/.cairo-dock/
```
repeat the last line for all apps you'd like to see in the dock (replace firefox by e.g. xmms) [1]

start by typing cairo-dock

[1] important: this only works for .desktop-files that use PNG or SVG images as icons. You can check that with this command:
grep Icon <yourfile>.desktop
To include custom apps create your own .desktop-files in ~/.cairo-dock. They need to have a [Desktop Entry] section with key-value-pairs for Name, Exec and Icon

**_FAQ:_**
Q: *How can I influence the Icons' order*
A: *Not at all*

Q: *What command-line args are valid?*
A: *--no-background and --benchmark, the others are buggy in this version*

Q: *How can I start it at startup?*
A: *System->Settings->Sessions->[3rd tab]->Add*

Q: *When will cairo-dock be ready for production use?*
A: *Never. cairo-dock is a proof-of-concept demo and not ment to be used in production.*

Q: *What are good alternatives?*
A: *awn, gimmie, kiba-dock (see google)*

Q: *Is anything similar to cairo-dock in the pipe?*
A: *gnome-dock is the follow-up projet. see [http://www.gnome-dock.org](http://www.gnome-dock.org)*

Q: *How do I uninstall it?*
A: *sudo dpkg --purge cairodock*

How I get autohide for this?

---

### Post by iopo on 2007-03-30
Hi everybody,

I installed everything following the FAQ and it works perfectly. Anyway, I find the customization process quite lengthy so I decided to uninstall it. Unfortunatly I got:

andrea@andrea-laptop:~$ sudo dpkg --purge cairodock
dpkg - warning: ignoring request to remove cairodock which isn't installed.

Any idea?

Thanks

---

### Post by lotacus on 2007-04-03
The configuration process for cairo-dock isn't lengthy at all in my opinion, however I think I am running an old version of it. I find some bugs already.

1. the screen area about 1/10 of the screen at the bottom is unusable for the mouse. try to right click and you can't. If a window is moved down near there, you can't get it back.

Also, it seems that when running it as a login script, it will start with the black border (because beryl hasn't fully loaded) then it disappears after beryl loads. However, it reapears on the left virtual desktop of the cube. wierd huh?

Another is the icons. At least for one. A default computer icon which resembles a mac monitor/computer is displayed lower then the rest.

I'm trying to find a way to run kiba-dock, but it's trouble-some. can't seem to get it to go.

Anways, to remove cairo-dock, you just remove the /opt/ directory, if that's where you installed it to. sudo rm -R /opt. You can also remove the extracted files from the tar.gz.

---

### Post by signalat on 2007-04-05
added a configuration window to the gnome dock, which is shown up by right click the gnome dock.
what the configuration window can do:
* modify existing launcher item property
* remove launcher item
* add new launcher item
* move icon positions (move the icon left/right with the "->" "<-" button)

to get it work, create a configuration file "icons.conf" under "$HOME/.cairo-dock"
the format of icons.conf is:
[Files]
Name=rhythmbox.desktop;kmess.desktop;firefox.desktop;

add at least one ".desktop" file to the icons.conf so that the dock could be shown on the screen. and then, add as many icons as you like using the configuration window.

Quick Howto:
1. tar xfvz cairo-dock-0.1g.tar.gz
2. make
3. ./install.sh
4. ./cairo-dock &

this version is based on bravus's cairo-dock-0.1f code.

source files:

---

### Post by signalat on 2007-04-05
added background color to the dock.

---

### Post by got_nix on 2007-04-07
hm... i need the dependent package for your cairo package. make fails i'm sure its because of dependencies too.

---

### Post by signalat on 2007-04-07
> **got_nix said:**
> hm... i need the dependent package for your cairo package. make fails i'm sure its because of dependencies too.

you need install cairo package first. the .deb file is too big to be attached here. so do the following:
1. Install these packages
Code:

sudo apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev


2. Make sure you have build-essential to be able to compile cairo.

3. Download Cairo 1.2.6

[http://cairographics.org/releases/cairo-1.2.6.tar.gz](http://cairographics.org/releases/cairo-1.2.6.tar.gz)

4. Install Cairo 1.2.6

Code:

./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc

Code:

make

Code:

sudo make install

5. unarchive cairo-dock-0.1h.tar.gz and compile.

---

### Post by nameless_reverie on 2007-04-07
I'm having trouble installing cairo dock.
Everything has worked out until the very end when i try to "make". 
I keep on getting this error: 

jose@jose-laptop:/opt/cairo-dock$ make
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
cairo-dock.c:52:25: error: cairo-glitz.h: No such file or directory
cairo-dock.c: In function ‘dock_cairo_create’:
cairo-dock.c:184: warning: assignment makes pointer from integer without a cast
make: *** [cairo-dock] Error 1
jose@jose-laptop:/opt/cairo-dock$ make clean && make all
rm -f *.o *~ cairo-dock
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
cairo-dock.c:52:25: error: cairo-glitz.h: No such file or directory
cairo-dock.c: In function ‘dock_cairo_create’:
cairo-dock.c:184: warning: assignment makes pointer from integer without a cast
make: *** [cairo-dock] Error 1


can anyone help me? i'm still a little new to ubuntu. 

please respond asap.
thanks!!!

---

### Post by signalat on 2007-04-07
> **nameless_reverie said:**
> I'm having trouble installing cairo dock.
Everything has worked out until the very end when i try to "make". 
I keep on getting this error: 

jose@jose-laptop:/opt/cairo-dock$ make
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
cairo-dock.c:52:25: error: cairo-glitz.h: No such file or directory
cairo-dock.c: In function ‘dock_cairo_create’:
cairo-dock.c:184: warning: assignment makes pointer from integer without a cast
make: *** [cairo-dock] Error 1
jose@jose-laptop:/opt/cairo-dock$ make clean && make all
rm -f *.o *~ cairo-dock
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
cairo-dock.c:52:25: error: cairo-glitz.h: No such file or directory
cairo-dock.c: In function ‘dock_cairo_create’:
cairo-dock.c:184: warning: assignment makes pointer from integer without a cast
make: *** [cairo-dock] Error 1


can anyone help me? i'm still a little new to ubuntu. 

please respond asap.
thanks!!!

you need install cairo package first.

---

### Post by nameless_reverie on 2007-04-07
i did install the cairo package.
as a matter of fact, i installed it three times already and i keep on getting the same error:

jose@jose-laptop:/opt/cairo-dock$ sudo make
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
cairo-dock.c:52:25: error: cairo-glitz.h: No such file or g directory
cairo-dock.c: In function ‘dock_cairo_create’:
cairo-dock.c:184: warning: assignment makes pointer from integer without a cast
make: *** [cairo-dock] Error 1


i don't know what to do!

but i am getting the cairo dock from: [http://www.gnome-dock.org/prerelease/cairo-dock-0.0.1b.tar.gz](http://www.gnome-dock.org/prerelease/cairo-dock-0.0.1b.tar.gz)

instead of the one provided because when i try to extract it to /opt , it keeps on saying:
"EXRACTION NOT PERFORMED: You don't have the right permissions to extract archives in the folder "/opt" ", and i'm the root user anyway. 
i dont know if that's the problem, but PLEASEEE someone help me!
i've been wasting so many HOURS trying to figure out how to install this one softwar.

THANKS!

---

### Post by nameless_reverie on 2007-04-08
ok. well it finally installed and then it disappeared.

then i decided to just install that cairo-dock-0.1h, yet this error came up:

jose@jose-laptop:/opt/cairo-dock-0.1h$ sudo make
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx gconf-2.0`   `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx gconf-2.0` -lm  cairo-dock.c   -o cairo-dock
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
cairo-dock.c:43:19: error: cairo.h: No such file or directory
cairo-dock.c:44:25: error: pango/pango.h: No such file or directory
cairo-dock.c:45:28: error: gdk/gdkkeysyms.h: No such file or directory
cairo-dock.c:46:21: error: gtk/gtk.h: No such file or directory
cairo-dock.c:47:26: error: librsvg/rsvg.h: No such file or directory
cairo-dock.c:48:32: error: librsvg/rsvg-cairo.h: No such file or directory
cairo-dock.c:58:32: error: gconf/gconf-client.h: No such file or directory
cairo-dock.c:73: error: expected specifier-qualifier-list before ‘gchar’
cairo-dock.c:96: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:97: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:99: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_DimensionData’
cairo-dock.c:100: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iScreenHeight’
cairo-dock.c:101: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iCurrentWidth’
cairo-dock.c:102: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iCurrentHeight’
cairo-dock.c:103: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bClicked’
cairo-dock.c:108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_uiRedraws’
cairo-dock.c:109: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_uiEvents’
cairo-dock.c:110: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_uiTimeoutHandlerId’
cairo-dock.c:111: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_uiHideHandlerId’
cairo-dock.c:119: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iWindowMove’
cairo-dock.c:120: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iAtBottom’
cairo-dock.c:122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iWindowPositionX’
cairo-dock.c:123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iWindowPositionY’
cairo-dock.c:124: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iWindowWidth’
cairo-dock.c:125: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iWindowHeight’
cairo-dock.c:126: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iDockLineWidth’
cairo-dock.c:127: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iDockRadius’
cairo-dock.c:128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iDockWidth’
cairo-dock.c:129: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iDockHeight’
cairo-dock.c:130: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iDockOffsetX’
cairo-dock.c:131: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iDockOffsetY’
cairo-dock.c:132: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_fGradientOffsetX’
cairo-dock.c:133: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iInfluenceGlobal’
cairo-dock.c:135: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bDrawBackground’
cairo-dock.c:136: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bUseIconBuffering’
cairo-dock.c:137: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bUseText’
cairo-dock.c:138: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bKeepAbove’
cairo-dock.c:139: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bSkipPager’
cairo-dock.c:140: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bSkipTaskbar’
cairo-dock.c:141: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bSticky’
cairo-dock.c:142: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘autoHide’
cairo-dock.c:151: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bUseBenchmark’
cairo-dock.c:154: error: expected ‘)’ before ‘fX’
cairo-dock.c:155: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘shrink_down’
cairo-dock.c:156: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘grow_up’
cairo-dock.c:157: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘clicked’
cairo-dock.c:158: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘none_clicked’
cairo-dock.c:160: error: expected declaration specifiers or ‘...’ before ‘gint’
cairo-dock.c:161: error: expected ‘)’ before ‘bmovetoleft’
cairo-dock.c:169: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:172: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:210: error: expected ‘)’ before ‘*’ token
cairo-dock.c: In function ‘get_first_icon’:
cairo-dock.c:222: error: ‘icons’ undeclared (first use in this function)
cairo-dock.c:222: error: (Each undeclared identifier is reported only once
cairo-dock.c:222: error: for each function it appears in.)
cairo-dock.c:222: error: invalid type argument of ‘->’
cairo-dock.c: In function ‘get_last_icon’:
cairo-dock.c:226: error: ‘icons’ undeclared (first use in this function)
cairo-dock.c:226: error: invalid type argument of ‘->’
cairo-dock.c: At top level:
cairo-dock.c:229: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_current_dock_width’
cairo-dock.c:238: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_current_dock_height’
cairo-dock.c:247: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_dock_offset_y’
cairo-dock.c:252: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_current_dock_offset_x’
cairo-dock.c:257: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_current_dock_offset_y’
cairo-dock.c:262: error: expected ‘)’ before ‘*’ token
cairo-dock.c:442: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘move_up’
cairo-dock.c:481: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘move_down’
cairo-dock.c:529: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_expose’
cairo-dock.c:546: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_configure’
cairo-dock.c:567: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_key_press’
cairo-dock.c:604: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_button_press’
cairo-dock.c:691: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_motion_notify’
cairo-dock.c:819: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_enter_notify’
cairo-dock.c:838: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘benchmark’
cairo-dock.c:853: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_leave_notify’
cairo-dock.c:879: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘none_clicked’
cairo-dock.c:890: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘clicked’
cairo-dock.c:919: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘grow_up’
cairo-dock.c:942: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘shrink_down’
cairo-dock.c:962: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘scale’
cairo-dock.c:975: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘scaleIntegral’
cairo-dock.c:989: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘scaledPosition’
cairo-dock.c:994: error: expected ‘)’ before ‘fMouseX’
cairo-dock.c:1065: error: expected ‘)’ before ‘*’ token
cairo-dock.c:1114: error: expected ‘)’ before ‘*’ token
cairo-dock.c:1179: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘spit_out_redraws’
cairo-dock.c:1190: error: expected declaration specifiers or ‘...’ before ‘gint’
cairo-dock.c: In function ‘configure_dialog’:
cairo-dock.c:1193: error: ‘GtkWidget’ undeclared (first use in this function)
cairo-dock.c:1193: error: ‘dialog’ undeclared (first use in this function)
cairo-dock.c:1193: error: ‘label_name’ undeclared (first use in this function)
cairo-dock.c:1193: error: ‘label_type’ undeclared (first use in this function)
cairo-dock.c:1193: error: ‘label_exec’ undeclared (first use in this function)
cairo-dock.c:1193: error: ‘label_comments’ undeclared (first use in this function)
cairo-dock.c:1193: error: ‘label_icon’ undeclared (first use in this function)
cairo-dock.c:1194: error: ‘edit_name’ undeclared (first use in this function)
cairo-dock.c:1194: error: ‘edit_exec’ undeclared (first use in this function)
cairo-dock.c:1194: error: ‘edit_comments’ undeclared (first use in this function)
cairo-dock.c:1194: error: ‘edit_icon’ undeclared (first use in this function)
cairo-dock.c:1195: error: ‘btn_icon’ undeclared (first use in this function)
cairo-dock.c:1195: error: ‘table’ undeclared (first use in this function)
cairo-dock.c:1200: error: ‘GTK_DIALOG_MODAL’ undeclared (first use in this function)
cairo-dock.c:1200: error: ‘GTK_DIALOG_DESTROY_WITH_PARENT’ undeclared (first use in this function)
cairo-dock.c:1210: error: ‘GTK_RESPONSE_APPLY’ undeclared (first use in this function)
cairo-dock.c:1211: error: ‘GTK_STOCK_CLOSE’ undeclared (first use in this function)
cairo-dock.c:1212: error: ‘GTK_RESPONSE_CLOSE’ undeclared (first use in this function)
cairo-dock.c:1215: error: ‘FALSE’ undeclared (first use in this function)
cairo-dock.c:1216: error: invalid type argument of ‘->’
cairo-dock.c:1226: error: ‘GTK_EXPAND’ undeclared (first use in this function)
cairo-dock.c:1226: error: ‘GTK_FILL’ undeclared (first use in this function)
cairo-dock.c:1241: error: ‘GList’ undeclared (first use in this function)
cairo-dock.c:1241: error: ‘glist’ undeclared (first use in this function)
cairo-dock.c:1245: error: ‘combo’ undeclared (first use in this function)
cairo-dock.c:1246: error: invalid type argument of ‘->’
cairo-dock.c:1250: error: ‘Icon’ has no member named ‘acType’
cairo-dock.c:1251: error: invalid type argument of ‘->’
cairo-dock.c:1275: error: ‘Icon’ has no member named ‘acName’
cairo-dock.c:1276: error: ‘Icon’ has no member named ‘acCommand’
cairo-dock.c:1277: error: ‘Icon’ has no member named ‘acComment’
cairo-dock.c:1278: error: ‘Icon’ has no member named ‘acFileName’
cairo-dock.c:1282: error: ‘gint’ undeclared (first use in this function)
cairo-dock.c:1282: error: expected ‘;’ before ‘result’
cairo-dock.c:1283: error: ‘GKeyFile’ undeclared (first use in this function)
cairo-dock.c:1283: error: ‘keyfile’ undeclared (first use in this function)
cairo-dock.c:1286: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:1286: error: ‘str_name’ undeclared (first use in this function)
cairo-dock.c:1287: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:1287: error: ‘str_exec’ undeclared (first use in this function)
cairo-dock.c:1288: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:1288: error: ‘str_comment’ undeclared (first use in this function)
cairo-dock.c:1289: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:1289: error: ‘str_icon’ undeclared (first use in this function)
cairo-dock.c:1290: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:1290: error: ‘str_type’ undeclared (first use in this function)
cairo-dock.c:1290: error: invalid type argument of ‘->’
cairo-dock.c:1292: error: ‘gchar’ undeclared (first use in this function)
cairo-dock.c:1292: error: ‘keydata’ undeclared (first use in this function)
cairo-dock.c:1295: error: ‘result’ undeclared (first use in this function)
cairo-dock.c:1298: error: ‘TRUE’ undeclared (first use in this function)
cairo-dock.c:1298: error: ‘idx’ undeclared (first use in this function)
cairo-dock.c:1305: error: ‘Icon’ has no member named ‘acFileName’
cairo-dock.c:1306: error: ‘Icon’ has no member named ‘acType’
cairo-dock.c:1307: error: ‘Icon’ has no member named ‘acName’
cairo-dock.c:1308: error: ‘Icon’ has no member named ‘acCommand’
cairo-dock.c:1309: error: ‘Icon’ has no member named ‘acComment’
cairo-dock.c:1320: error: ‘home_dir_fn’ undeclared (first use in this function)
cairo-dock.c:1321: error: ‘desktopfile’ undeclared (first use in this function)
cairo-dock.c:1321: error: ‘Icon’ has no member named ‘acDesktopFileName’
cairo-dock.c:1329: error: expected expression before ‘Icon’
cairo-dock.c:1329: warning: initialization makes pointer from integer without a cast
cairo-dock.c:1332: error: ‘icon_filename’ undeclared (first use in this function)
cairo-dock.c:1336: error: ‘Icon’ has no member named ‘acFileName’
cairo-dock.c:1337: error: ‘Icon’ has no member named ‘acType’
cairo-dock.c:1338: error: ‘Icon’ has no member named ‘acType’
cairo-dock.c:1339: error: ‘Icon’ has no member named ‘acName’
cairo-dock.c:1340: error: ‘Icon’ has no member named ‘acCommand’
cairo-dock.c:1341: error: ‘Icon’ has no member named ‘acComment’
cairo-dock.c:1344: error: ‘icons’ undeclared (first use in this function)
cairo-dock.c:1347: error: ‘Icon’ has no member named ‘acName’
cairo-dock.c:1348: error: ‘Icon’ has no member named ‘acType’
cairo-dock.c:1349: error: ‘Icon’ has no member named ‘acCommand’
cairo-dock.c:1350: error: ‘Icon’ has no member named ‘acComment’
cairo-dock.c:1351: error: ‘Icon’ has no member named ‘acFileName’
cairo-dock.c:1354: error: ‘newfile’ undeclared (first use in this function)
cairo-dock.c:1356: error: ‘Icon’ has no member named ‘acDesktopFileName’
cairo-dock.c:1372: error: ‘gconstpointer’ undeclared (first use in this function)
cairo-dock.c:1373: error: ‘Icon’ has no member named ‘acDesktopFileName’
cairo-dock.c: At top level:
cairo-dock.c:1384: error: expected ‘)’ before ‘bmovetoleft’
cairo-dock.c: In function ‘saveconfig’:
cairo-dock.c:1408: error: ‘gchar’ undeclared (first use in this function)
cairo-dock.c:1408: error: ‘home_dir_fn’ undeclared (first use in this function)
cairo-dock.c:1409: error: ‘fconf’ undeclared (first use in this function)
cairo-dock.c:1417: error: ‘GList’ undeclared (first use in this function)
cairo-dock.c:1417: error: ‘ic_tmp’ undeclared (first use in this function)
cairo-dock.c:1418: error: ‘icons’ undeclared (first use in this function)
cairo-dock.c: In function ‘fill_icon_data’:
cairo-dock.c:1429: error: ‘Icon’ has no member named ‘acFileName’
cairo-dock.c:1431: error: ‘Icon’ has no member named ‘pHandle’
cairo-dock.c:1431: error: ‘Icon’ has no member named ‘acFileName’
cairo-dock.c:1432: error: ‘Icon’ has no member named ‘pHandle’
cairo-dock.c:1432: error: ‘g_DimensionData’ undeclared (first use in this function)
cairo-dock.c:1433: error: ‘Icon’ has no member named ‘fWidth’
cairo-dock.c:1433: error: ‘gdouble’ undeclared (first use in this function)
cairo-dock.c:1433: error: expected ‘;’ before ‘g_DimensionData’
cairo-dock.c:1434: error: ‘Icon’ has no member named ‘fHeight’
cairo-dock.c:1434: error: expected ‘;’ before ‘g_DimensionData’
cairo-dock.c:1435: error: ‘Icon’ has no member named ‘bClicked’
cairo-dock.c:1435: error: ‘FALSE’ undeclared (first use in this function)
cairo-dock.c:1436: error: ‘Icon’ has no member named ‘fPeriod’
cairo-dock.c:1438: error: ‘Icon’ has no member named ‘acFileName’
cairo-dock.c:1440: error: ‘Icon’ has no member named ‘bClicked’
cairo-dock.c:1441: error: ‘Icon’ has no member named ‘fPeriod’
cairo-dock.c: In function ‘main’:
cairo-dock.c:1448: error: ‘GConfClient’ undeclared (first use in this function)
cairo-dock.c:1448: error: ‘gConfClient’ undeclared (first use in this function)
cairo-dock.c:1449: error: ‘gboolean’ undeclared (first use in this function)
cairo-dock.c:1449: error: expected ‘;’ before ‘autohide’
cairo-dock.c:1451: error: ‘g_bDrawBackground’ undeclared (first use in this function)
cairo-dock.c:1451: error: ‘TRUE’ undeclared (first use in this function)
cairo-dock.c:1454: error: ‘icons’ undeclared (first use in this function)
cairo-dock.c:1455: error: ‘gchar’ undeclared (first use in this function)
cairo-dock.c:1455: error: ‘home_dir_fn’ undeclared (first use in this function)
cairo-dock.c:1456: error: ‘cairo_dir’ undeclared (first use in this function)
cairo-dock.c:1458: error: ‘fconf’ undeclared (first use in this function)
cairo-dock.c:1460: error: ‘GKeyFile’ undeclared (first use in this function)
cairo-dock.c:1460: error: ‘keyfile_conf’ undeclared (first use in this function)
cairo-dock.c:1461: error: ‘G_KEY_FILE_NONE’ undeclared (first use in this function)
cairo-dock.c:1463: error: ‘strflist’ undeclared (first use in this function)
cairo-dock.c:1464: error: ‘gsize’ undeclared (first use in this function)
cairo-dock.c:1464: error: expected ‘;’ before ‘size’
cairo-dock.c:1465: error: ‘gint’ undeclared (first use in this function)
cairo-dock.c:1465: error: expected ‘;’ before ‘j’
cairo-dock.c:1467: error: ‘size’ undeclared (first use in this function)
cairo-dock.c:1469: error: ‘j’ undeclared (first use in this function)
cairo-dock.c:1470: error: ‘file_rel_fn’ undeclared (first use in this function)
cairo-dock.c:1471: error: ‘file_abs_fn’ undeclared (first use in this function)
cairo-dock.c:1473: error: ‘keyfile’ undeclared (first use in this function)
cairo-dock.c:1475: error: expected expression before ‘Icon’
cairo-dock.c:1475: warning: initialization makes pointer from integer without a cast
cairo-dock.c:1477: error: ‘Icon’ has no member named ‘acDesktopFileName’
cairo-dock.c:1479: error: ‘icon_filename’ undeclared (first use in this function)
cairo-dock.c:1484: error: ‘Icon’ has no member named ‘acFileName’
cairo-dock.c:1485: error: ‘Icon’ has no member named ‘acType’
cairo-dock.c:1486: error: ‘Icon’ has no member named ‘acName’
cairo-dock.c:1487: error: ‘Icon’ has no member named ‘acCommand’
cairo-dock.c:1488: error: ‘Icon’ has no member named ‘acComment’
cairo-dock.c:1496: error: ‘GtkWidget’ undeclared (first use in this function)
cairo-dock.c:1496: error: ‘pWindow’ undeclared (first use in this function)
cairo-dock.c:1497: error: ‘GdkScreen’ undeclared (first use in this function)
cairo-dock.c:1497: error: ‘gdkscreen’ undeclared (first use in this function)
cairo-dock.c:1499: error: ‘GError’ undeclared (first use in this function)
cairo-dock.c:1499: error: ‘pError’ undeclared (first use in this function)
cairo-dock.c:1500: error: ‘guint’ undeclared (first use in this function)
cairo-dock.c:1500: error: expected ‘;’ before ‘uiHandlerId’
cairo-dock.c:1501: error: expected ‘;’ before ‘uiBenchmarkId’
cairo-dock.c:1502: error: ‘cairo_t’ undeclared (first use in this function)
cairo-dock.c:1502: error: ‘pCairoContext’ undeclared (first use in this function)
cairo-dock.c:1503: error: expected ‘;’ before ‘i’
cairo-dock.c:1508: error: ‘i’ undeclared (first use in this function)
cairo-dock.c:1511: error: ‘g_bUseBenchmark’ undeclared (first use in this function)
cairo-dock.c:1528: error: ‘g_bUseText’ undeclared (first use in this function)
cairo-dock.c:1528: error: ‘FALSE’ undeclared (first use in this function)
cairo-dock.c:1530: error: ‘g_bUseIconBuffering’ undeclared (first use in this function)
cairo-dock.c:1532: error: ‘g_bKeepAbove’ undeclared (first use in this function)
cairo-dock.c:1534: error: ‘g_bSkipPager’ undeclared (first use in this function)
cairo-dock.c:1536: error: ‘g_bSkipTaskbar’ undeclared (first use in this function)
cairo-dock.c:1538: error: ‘g_bSticky’ undeclared (first use in this function)
cairo-dock.c:1543: error: expected ‘;’ before ‘help’
cairo-dock.c:1544: error: ‘help’ undeclared (first use in this function)
cairo-dock.c:1555: error: ‘GList’ undeclared (first use in this function)
cairo-dock.c:1555: error: ‘ic’ undeclared (first use in this function)
cairo-dock.c:1563: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
cairo-dock.c:1565: error: ‘g_iCurrentWidth’ undeclared (first use in this function)
cairo-dock.c:1567: error: ‘g_iWindowWidth’ undeclared (first use in this function)
cairo-dock.c:1568: error: ‘g_iWindowHeight’ undeclared (first use in this function)
cairo-dock.c:1568: error: ‘Icon’ has no member named ‘fHeight’
cairo-dock.c:1630: error: ‘g_iCurrentHeight’ undeclared (first use in this function)
cairo-dock.c:1631: error: ‘g_iScreenHeight’ undeclared (first use in this function)
cairo-dock.c:1632: error: ‘g_iWindowPositionX’ undeclared (first use in this function)
cairo-dock.c:1633: error: ‘g_iWindowPositionY’ undeclared (first use in this function)
cairo-dock.c:1638: error: ‘GDK_BUTTON_PRESS_MASK’ undeclared (first use in this function)
cairo-dock.c:1639: error: ‘GDK_POINTER_MOTION_MASK’ undeclared (first use in this function)
cairo-dock.c:1640: error: ‘GDK_POINTER_MOTION_HINT_MASK’ undeclared (first use in this function)
cairo-dock.c:1651: error: ‘gtk_main_quit’ undeclared (first use in this function)
cairo-dock.c:1655: error: ‘on_expose’ undeclared (first use in this function)
cairo-dock.c:1659: error: ‘on_configure’ undeclared (first use in this function)
cairo-dock.c:1663: error: ‘on_key_press’ undeclared (first use in this function)
cairo-dock.c:1667: error: ‘on_button_press’ undeclared (first use in this function)
cairo-dock.c:1671: error: ‘on_motion_notify’ undeclared (first use in this function)
cairo-dock.c:1675: error: ‘on_enter_notify’ undeclared (first use in this function)
cairo-dock.c:1679: error: ‘on_leave_notify’ undeclared (first use in this function)
cairo-dock.c:1738: error: ‘gdouble’ undeclared (first use in this function)
cairo-dock.c:1738: error: expected ‘;’ before ‘fEnd’
cairo-dock.c:1742: error: ‘fEnd’ undeclared (first use in this function)
cairo-dock.c:1742: error: ‘Icon’ has no member named ‘fWidth’
cairo-dock.c:1745: error: ‘iInfluenceGlobal’ undeclared (first use in this function)
cairo-dock.c:1754: error: ‘uiHandlerId’ undeclared (first use in this function)
cairo-dock.c:1754: error: ‘spit_out_redraws’ undeclared (first use in this function)
cairo-dock.c:1755: error: ‘uiBenchmarkId’ undeclared (first use in this function)
cairo-dock.c:1755: error: ‘benchmark’ undeclared (first use in this function)
cairo-dock.c:1755: error: ‘gpointer’ undeclared (first use in this function)
cairo-dock.c:1755: error: expected ‘)’ before ‘pWindow’
cairo-dock.c:1769: error: ‘Icon’ has no member named ‘pHandle’
cairo-dock.c:1770: error: ‘Icon’ has no member named ‘pIconBuffer’
cairo-dock.c: At top level:
cairo-dock.c:1778: error: expected ‘)’ before ‘*’ token
cairo-dock.c:1856: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c: In function ‘refresh_icon_cache’:
cairo-dock.c:1869: error: ‘GtkWidget’ undeclared (first use in this function)
cairo-dock.c:1869: error: ‘pWindow’ undeclared (first use in this function)
cairo-dock.c:1870: error: ‘cairo_t’ undeclared (first use in this function)
cairo-dock.c:1870: error: ‘pCairoContext’ undeclared (first use in this function)
cairo-dock.c:1873: error: ‘GList’ undeclared (first use in this function)
cairo-dock.c:1873: error: ‘windowlist’ undeclared (first use in this function)
cairo-dock.c:1874: error: expected expression before ‘)’ token
cairo-dock.c:1876: error: ‘g_bUseText’ undeclared (first use in this function)
cairo-dock.c:1878: error: ‘g_bUseIconBuffering’ undeclared (first use in this function)
cairo-dock.c: In function ‘calc_icon_positions’:
cairo-dock.c:1887: error: ‘GList’ undeclared (first use in this function)
cairo-dock.c:1887: error: ‘ic’ undeclared (first use in this function)
cairo-dock.c:1888: error: ‘gdouble’ undeclared (first use in this function)
cairo-dock.c:1888: error: expected ‘;’ before ‘fEnd’
cairo-dock.c:1889: error: ‘icons’ undeclared (first use in this function)
cairo-dock.c:1891: error: ‘fEnd’ undeclared (first use in this function)
cairo-dock.c:1891: error: ‘Icon’ has no member named ‘fWidth’
cairo-dock.c:1894: error: ‘iInfluenceGlobal’ undeclared (first use in this function)
cairo-dock.c:1894: error: ‘g_iWindowWidth’ undeclared (first use in this function)
make: *** [cairo-dock] Error 1


any ideas on what i did wrong signalat?

please respond asap.

---

### Post by signalat on 2007-04-08
i've seen the error before if i use an IDE to compile it. well, i think that's because i didn't configure my IDE. anyway, i just go to the terminal and compile it. it works for me.
anyway, it will attach the binary file here and you could try if you wanna. you could put the binary file anyway you wanna. remember to run the install.sh file first to create the working directory and make sure you create icons.conf file with at least one entry so that the program could get run. 

> **nameless_reverie said:**
> ok. well it finally installed and then it disappeared.

then i decided to just install that cairo-dock-0.1h, yet this error came up:

jose@jose-laptop:/opt/cairo-dock-0.1h$ sudo make
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx gconf-2.0`   `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx gconf-2.0` -lm  cairo-dock.c   -o cairo-dock
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
cairo-dock.c:43:19: error: cairo.h: No such file or directory
cairo-dock.c:44:25: error: pango/pango.h: No such file or directory
cairo-dock.c:45:28: error: gdk/gdkkeysyms.h: No such file or directory
cairo-dock.c:46:21: error: gtk/gtk.h: No such file or directory
cairo-dock.c:47:26: error: librsvg/rsvg.h: No such file or directory


please respond asap.

---

### Post by nameless_reverie on 2007-04-08
ok. i finally installed Cairo-Dock...

BUTTTTTT, everytime i launch it, and i move my mouse close to it, it suddenly disappears (it sinks down)!!! then when i try to launch it from an icon in the panel, it doesnt work either. also, i tried putting it on start-up, but that doesnt work either!!!
ANDD, i DID that thing that prevents auto hide:
// g_uiHideHandlerId = g_timeout_add (15, move_down, (gpointer) pWidget);

I'M JUST SOOO FRUSTRATED WITH THIS THING, EVERYTIME I THINK I'M CLOSE TO SUCCESS, IT MESSES UP. arghhh!

any suggestions/help guys?

---

### Post by signalat on 2007-04-08
> **nameless_reverie said:**
> ok. i finally installed Cairo-Dock...

BUTTTTTT, everytime i launch it, and i move my mouse close to it, it suddenly disappears (it sinks down)!!! then when i try to launch it from an icon in the panel, it doesnt work either. also, i tried putting it on start-up, but that doesnt work either!!!
ANDD, i DID that thing that prevents auto hide:
// g_uiHideHandlerId = g_timeout_add (15, move_down, (gpointer) pWidget);

I'M JUST SOOO FRUSTRATED WITH THIS THING, EVERYTIME I THINK I'M CLOSE TO SUCCESS, IT MESSES UP. arghhh!

any suggestions/help guys?

1. it sinks down because it is coded to behave autohide.
2. failed to launch from an icon in the panel, you probably put parameters like "%" in the command, delete all the parameter, it will be fine. 
2. how do u put it on start-up?  do you give the correct path?

---

### Post by kwaanens on 2007-04-09
> **bravus said:**
> [http://code.google.com/p/udock/](http://code.google.com/p/udock/)

Came across this when googling for "udock" (in order to locate this thread) and found "uDock™" here: [http://www.myronl.com/U2CI/U2CI_QSG_DFTc_09_05.pdf](http://www.myronl.com/U2CI/U2CI_QSG_DFTc_09_05.pdf)
Maybe you should get another name, so you avoid legal issues.

Sorry if this was mentioned before.

Really anxious to see more of your efforts!

- Ketil

---

### Post by kwaanens on 2007-04-09
> **tlacuache said:**
> I've been using Avant Window Navigator for a few days now and I'm really liking it a lot. Finally I have  my launchers and my taskbar icons all on the same dock!

As was mentioned, though, it does require a composite manager (beryl), and I'm not running beryl on my laptop, so I can't enjoy it there.

I didn't have any problems at all installing awn, personally. I just followed this howto:

[http://ubuntuforums.org/showthread.php?t=351186&highlight=avant+window+navigator](http://ubuntuforums.org/showthread.php?t=351186&highlight=avant+window+navigator)

I did it using the SVN method because I think the posted .tgz didn't include the launcher capabilities, at least when I grabbed it.

-SG

I'm also loving Awn. Finally, I'm rid of kooldock! On [http://awn.wetpaint.com/page/Ubuntu](http://awn.wetpaint.com/page/Ubuntu) there are lines to go into sources.list, and behold! it's updated through Synaptic or Aptitude.

- Ketil

---

### Post by Bart Ellebaut on 2007-04-13
I've got a problem.
I just downloaded the cairostuff, but when I put in the code:" ./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc"
I get : ./config: no such file or directory.

What am I doing wrong?

thx

---

### Post by Ethos on 2007-04-16
Hello everyone ive been working on getting this to work for a little bit tonight and i have it working almost flawlessly...The only thing left is that I have no icons...Im able to launch programs and when i run accross the dock it says the name like its supposed to, but i have no icons...I downloaded some svg icons and threw them in there but no success...any ideas?

---

### Post by julie_lebou on 2007-04-17
Have no idea what this : 6. Extract the tarball in /opt means! I need the details! :-)

---

### Post by chakkaradeep on 2007-04-17
I get the same error,

```

cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx gconf-2.0`   `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx gconf-2.0` -lm  cairo-dock.c   -o cairo-dock
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
Package gconf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-2.0' found
cairo-dock.c:43:19: error: cairo.h: No such file or directory
cairo-dock.c:44:25: error: pango/pango.h: No such file or directory
cairo-dock.c:45:28: error: gdk/gdkkeysyms.h: No such file or directory
cairo-dock.c:46:21: error: gtk/gtk.h: No such file or directory
cairo-dock.c:47:26: error: librsvg/rsvg.h: No such file or directory
cairo-dock.c:48:32: error: librsvg/rsvg-cairo.h: No such file or directory
cairo-dock.c:58:32: error: gconf/gconf-client.h: No such file or directory
cairo-dock.c:73: error: expected specifier-qualifier-list before ‘gchar’
cairo-dock.c:96: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:97: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cairo-dock.c:99: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_DimensionData’
cairo-dock.c:100: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iScreenHeight’
cairo-dock.c:101: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iCurrentWidth’
cairo-dock.c:102: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_iCurrentHeight’
cairo-dock.c:103: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘g_bClicked’
.............
..................
............................... it still goes on like this


```

I have installed nearly all packages with *gconf* in the repos . I am using feisty and I didnt not use any IDE to compile.

Thanks

---

### Post by chakkaradeep on 2007-04-18
Ok, got thru the error, it was due to not installing *libgconf2-dev* package. Compilation passed, but now,

```

chaks@NEO:~/cairo-dock-0.1h$ sudo ./install.sh 
cp: cannot stat `*.desktop': No such file or directory
cp: cannot stat `*.svg': No such file or directory
chaks@NEO:~/cairo-dock-0.1h$ ls
cairo-dock  cairo-dock.c  install.sh  Makefile  tango-colors.h
chaks@NEO:~/cairo-dock-0.1h$ ./cairo-dock 
Segmentation fault (core dumped)

```

Any idea ?

---

### Post by signalat on 2007-04-21
> **chakkaradeep said:**
> Ok, got thru the error, it was due to not installing *libgconf2-dev* package. Compilation passed, but now,

```

chaks@NEO:~/cairo-dock-0.1h$ sudo ./install.sh 
cp: cannot stat `*.desktop': No such file or directory
cp: cannot stat `*.svg': No such file or directory
chaks@NEO:~/cairo-dock-0.1h$ ls
cairo-dock  cairo-dock.c  install.sh  Makefile  tango-colors.h
chaks@NEO:~/cairo-dock-0.1h$ ./cairo-dock 
Segmentation fault (core dumped)

```

Any idea ?

you need icons.conf  and at least one .desktop file under $HOME/.cairo-dock to start the program. create the icons.conf and one .desktop file as blow, then you can added as many as you like through the configuration window.

------------- icons.conf  --------------------------
[Files]
Name=rhythmbox.desktop;

----------------- rhythmbox.desktop  -------------
[Desktop Entry]
Name=Music
Exec=rhythmbox
Type=Application
Comment=Play and organize your music collection
Icon=xmms.png

---

### Post by DerangedDingo on 2007-04-28
I dunno why. But I decided to make a small icon set.... err.. a few icons, it's not really a set, and combine them with the ones that worked in the cairo-dock package. If any newbs just installed it and want a few icons and a working dock quickly this could help very nicely.

Unfortunately, due to my own ineptitude while making a few of the icons I was doing so from a folder in my desktop and moving that folder causes the icons to not work... So I'm not sure if, even with the folder inside, and moved to your desktop, the icons would work, because of the different usernames.

Here ya go. It includes a cairo-dock.c file with a few icons cut out and one or two added in, a buncha icons, and the folder that needs to be moved to the desktop that contains all the originals.

---

### Post by black_ice on 2007-04-30
i followed this how to but when i want to setup cairo-dock an error alawys appear 

[PHP] root@adam-laptop:/opt/cairo-dock# ./cairo-dock --no-glitz

(cairo-dock:30465): Gtk-WARNING **: cannot open display:  
root@adam-laptop:/opt/cairo-dock# ./cairo-dock --no-glitz

(cairo-dock:31080): Gtk-WARNING **: cannot open display: [/PHP]

!!!!!!!!!!!!!!!!!!!!!!!! 

i have added this script gnomedock-start.sh to my start programs but the apple bar appears and i cannot see i icons and it loads with program that i have never installed before  ? and there is no icons for but when i make my mouse move on icons the icons appear and the name of the icon appears with no icon ? what i can do ?

---

### Post by Vaelrith on 2007-05-06
I can't do step 3 because the cairo graphics website seems to be down.  If anyone has this package could they send it to me? 

Many thanks

---

### Post by jonah1980 on 2007-05-07
hey guys i'm using the gnome dock for gdesklets called starterbar. it's cool but doesnt autohide and has no tray etc...

the great thing is not needing beryl/compiz etc, gdesklets is awesome for widgets and docks and stuff but there's not much dev going on. i wonder if anyone know of anything for gdesklets that beats starterbar or anything being worked on?

---

### Post by dannymichel on 2007-05-09
I don't have permission to extrat it to /opt

---

### Post by b3n87 on 2007-05-10
just put sudo at the start of the command

---

### Post by dannymichel on 2007-05-10
> **GPH said:**
> [http://www.gnome-dock.org/prerelease...-0.0.1b.tar.gz](http://www.gnome-dock.org/prerelease...-0.0.1b.tar.gz) (doesn't seem to work anymore)
Try this instead: [ATTACH]19718[/ATTACH]

**6. Extract the tarball in /opt**
[B]
7. Install cairo-dock[/B]

```
make clean
``````

make
```Also, change your virtual vertical size in Beryl from 1 to 2, otherwise it will probably bug. That's a weird fix found by someone in this thread, but it works.

To open the dock, useWhere is the extract command?

---

### Post by olavjunior on 2007-05-10
I had Cairo-dock under edgy, and loved it and got used to it!

But I'm having bigger trouble getting it to work under feisty, so I'm hoping for some help here..
I finally figured out how to install cairo 1.2.6. But when I try to type sudo make in terminal, I get a looong list of errors (the end of the errors is attached)

I hace cairo-clock running if that means anything at all...

EDIT: 

I was missing out on some of these :

[I]1. Install these packages
Code:

sudo apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev[/I]

Now I've got cairo up and running againg :) Don't know why I didn't get these pagages to begin with...? Followed the wrong turtorial perhaps..

---

### Post by dannymichel on 2007-05-10
> **dannymichel said:**
> Where is the extract command?
Anyone think they can help me with my issue?

---

### Post by balance07 on 2007-05-10
has anyone gotten this working nicely with dual-screens? when i run it, it plops down right between my 2 monitors. i'd rather have it centered on monitor 1. i've played around with the c file, but settings don't seem to change what i want. thanks in advance.

---

### Post by the_hero on 2007-05-11
> **dannymichel said:**
> Anyone think they can help me with my issue?

Simply, right click on the archive and choose "Extract here"

---

### Post by dannymichel on 2007-05-11
I don't have permission to extract it in /opt

---

### Post by kwaanens on 2007-05-11
sudo chown yourusername.yourusername /opt

---

### Post by balance07 on 2007-05-11
> **dannymichel said:**
> I don't have permission to extract it in /opt

extract it to your desktop, then hit Alt+F2, type "gksudo nautilus", press enter, type your password, press enter, navigate to /home/<username>/Desktop and cut/paste the cairo or whatever folder to /opt

---

### Post by jvc26 on 2007-05-11
I have the bizarre issue of none of the .svg icons show up, only one of them at a time. In nautilus they don't show up with a preview image, except for one of them. They were converted .pngs with inkscape, which worked fine, and can view them as .svgs in inkscape... Any ideas?
Il

---

### Post by jfca283 on 2007-05-12
hi 
i wonder how can i make the dock always above?
minimize the zoom when i move over a launcher?
if i press the show desktop applet, the dock minimizes, any idea about this?
i don't know which version i've installed, so i uploaded my conf files if it helps
thanks

---

### Post by galileo99 on 2007-05-13
thanks for the help, now it work, but one little problem: how can i prevent it form auto-hiding?

---

### Post by Rospo Zoppo on 2007-05-27
> **galileo99 said:**
> thanks for the help, now it work, but one little problem: how can i prevent it form auto-hiding?

You can have the solution in the beginning of the discussion..

---

### Post by cyrylski on 2007-06-07
Besides graphical resemblance and basic functionality there absolutely NOTHING in common between thisahere and MacOS dock panel, as one suggested. 

I appreciate authors effort cuz it looks really nice but please notice that obtaining it to work is far too complicated to compare it to Mac OS. There it just IS, here I had to spend 1,5 hour to install it, then tune it and, then realize that ooops but its user-unfriendly - there's no config window and the background arround the panel icons is pitch black (no transparency) and it disapears in Beryl. 
Maybe I spent to little time on learning how to make it work but still, it's not 

But I'm just a lame in Ubuntu for the time being and I jumped from Windows, expecting that everything will run smoothly. So I'll just wish the author good luck in further development :)

---

### Post by sel on 2007-06-08
Bravus seems to have gone that way -------> [over here]("http://code.google.com/p/udock/").

---

### Post by kwaanens on 2007-06-08
> **cyrylski said:**
> Besides graphical resemblance and basic functionality there absolutely NOTHING in common between thisahere and MacOS dock panel, as one suggested. 

I appreciate authors effort cuz it looks really nice but please notice that obtaining it to work is far too complicated to compare it to Mac OS. There it just IS, here I had to spend 1,5 hour to install it, then tune it and, then realize that ooops but its user-unfriendly - there's no config window and the background arround the panel icons is pitch black (no transparency) and it disapears in Beryl. 
Maybe I spent to little time on learning how to make it work but still, it's not 

But I'm just a lame in Ubuntu for the time being and I jumped from Windows, expecting that everything will run smoothly. So I'll just wish the author good luck in further development :)

My, oh my, what level of annoyance...

Gnome-dock is extremely early in development. Maybe you should check out [http://www.kiba-dock.org/](http://www.kiba-dock.org/) or [http://awn.wetpaint.com/](http://awn.wetpaint.com/) instead. Install the debs, takes you 1 minute. Configuring isn't that hard either.

- Ketil

---

### Post by dannymichel on 2007-06-09
I get ```
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
```
and please see screen-shot

---

### Post by justagamer on 2007-06-10
I got all the way to the make clean install on the cairo-dock and it just keeps saying there's nothing to make clean i extracted it to the opt folder and it just wont work.

---

### Post by spockrock on 2007-06-11
> **dannymichel said:**
> I get ```
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
```
and please see screen-shot

that is actually has nothing to do with the dock, but with your the file .fonts.conf in your home folder

---

### Post by maxfact on 2007-06-11
i have a problem but my english is not good 
i have installed gnome-dock but have this problem:
icon.svg not exist 

see for believe

[[IMG]http://img521.imageshack.us/img521/117/schermatacairodockdg7.th.png[/IMG]](http://img521.imageshack.us/my.php?image=schermatacairodockdg7.png)

---

### Post by Exxentrix on 2007-06-11
works till i get to step 4
when it says:
bash: ./configure: No such file or directory

---

### Post by spockrock on 2007-06-11
> **maxfact said:**
> i have a problem but my english is not good 
i have installed gnome-dock but have this problem:
icon.svg not exist 

see for believe

[[IMG]http://img521.imageshack.us/img521/117/schermatacairodockdg7.th.png[/IMG]](http://img521.imageshack.us/my.php?image=schermatacairodockdg7.png)

are you using an .svg icon, it can only handle .svg right now.

---

### Post by bl3s5in on 2007-06-12
Neither svg or png icons work. If they did the app might actually be use able.

---

### Post by dannymichel on 2007-06-12
> **dannymichel said:**
> I get ```
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
```
and please see screen-shot
Can anyone help me with my issue?
Why aren't my icons showing?
This thing also crashes my system.

---

### Post by maxfact on 2007-06-12
> **spockrock said:**
> are you using an .svg icon, it can only handle .svg right now.

yes now is all right 
i have do handle.svg 
ok
ok
i am italian exscuse me for my english ):P

---

### Post by DerangedDingo on 2007-06-13
.svgs to the rescue.

I saw these and remembered my trouble with .svgs and Gnome Dock
check out the links... They're for icon themes at Gnome-Look.org that are purely comprised of .svg icons made in Inkscape. Just dig through, find an icon for an app you like and sub the sucker in into your cairo-dock folder


i haven't read all the other posts though, I don't know if anyone else found a really good solution.. other than making svg links to pngs in the early pages.

[http://gnome-look.org/content/show.php/GnomeProject+icon+?content=60258](http://gnome-look.org/content/show.php/GnomeProject+icon+?content=60258)
[http://gnome-look.org/content/show.php/Glass+Icons+Theme?content=32146](http://gnome-look.org/content/show.php/Glass+Icons+Theme?content=32146)

---

### Post by maxfact on 2007-06-17
Now this is my gnome-dock
[[IMG]http://img167.imageshack.us/img167/8693/schermatacairodock1un0.th.png[/IMG]](http://img167.image[shack.us/my.php?image=schermatacairodock1un0.png)

Thanks yuo so much all yuo
grazie di cuore a tutti voi :guitar:

---

### Post by maxfact on 2007-06-19
i have a little problem 
i would like a gnome dock ever up on desktop
i work in this file```
cairo-dock.c
```
but i dont understand whit my handle

this my file modify but not function why?where my error
```
3456789 123456789 123456789 123456789 123456789 123456789 123456789 123456789 
**      10        20        30        40        50        60        70        80
**
** program:
**    cairo-dock
**
** author(s):
**    Mirco "MacSlow" Mueller <macslow@bangang.de>
**    Behdad Esfahbod <behdad@behdad.org>
**    David Reveman <davidr@novell.com>
**    Karl Lattimer <karl@qdh.org.uk> 
**
** Copyright (C) Mirco Mueller, June 2006.
**
** notes:
**    A stress-test for cairo, librsvg, and glitz.  This program is released
**    under the terms of the GNU General Public License. If you don't know what
**    that means take a look at:
**
**        http://www.gnu.org/licenses/licenses.html#GPL
**
** notes from original author:
**
**    I just know that some folks will bug me regarding this, so... yes there's
**    nearly everything hard-coded, it is not nice, it is not very usable for
**    easily (without any hard work) making a full dock-like application out of
**    this, please don't email me asking to me to do so... for everybody else
**    feel free to make use of it beyond this being a small but heavy stress
**    test. I've written this on an Ubuntu-6.06 box running Xgl/compiz. The
**    icons used are from the tango-project...
**
**        http://tango-project.org/
**
**    Over the last couple of days Behdad and David helped me (MacSlow) out a
**    great deal by sending me additional tweaked and optimized versions. I've
**    now merged all that with my recent additions.
**
*******************************************************************************/

#include <math.h>
#include <string.h>
#include <cairo.h>
#include <pango/pango.h>
#include <gdk/gdkkeysyms.h>
#include <gtk/gtk.h>
#include <librsvg/rsvg.h>
#include <librsvg/rsvg-cairo.h>
#ifdef HAVE_GLITZ
#include <gdk/gdkx.h>
#include <glitz-glx.h>
#include <cairo-glitz.h>
#endif

#include "tango-colors.h"

#define WIN_HEIGHT 150
#define INFLUENCE 150.0
#define GAP 1.0

typedef struct _Icon {
	gchar acFileName[64];
	gchar acName[32];
	gchar acCommand[90];
	gdouble fX;
	gdouble fY;
	gdouble fWidth;
	gdouble fHeight;
	gdouble fScale;
	gdouble fImageScale;
	cairo_surface_t* pIconBuffer;
	cairo_surface_t* pTextBuffer;
	gdouble fTextXOffset;
	gdouble fTextYOffset;
	RsvgHandle* pHandle;
	gboolean bClicked;
	gdouble fPeriod;
} Icon;

static Icon g_aIcons[] =
{
	{"gnome-fs-home.svg", "Home", "nautilus /home/max"},
	{"gnome-terminal.svg", "Terminal", "gnome-terminal --working-directory=/home/max"},
	{"firefox.svg", "Firefox", "firefox"},
	{"sound-juicer.svg", "K3b", "k3b"},
	{"xchat.svg", "Xchat", "xchat"},
	{"gnome-multimedia.svg", "Totem", "totem"},
	{"ooo_writer.svg", "Writer", "ooffice -writer"},
	{"ooo_math.svg", "Calc", "ooffice -calc"},
	{"evolution.svg", "Evolution", "evolution-2.10"},
	{"gnome-mixer.svg", "Rhythmbox", "rhythmbox"},
	{"gnome-gimp.svg", "GIMP", "gimp"},
	{"dc++.svg", "DC++", "/opt/linuxdcpp/ldcpp"},
	{"gnome-fs-trash-empty.svg", "Cestino", "nautilus trash:///"},
	{"gnome-system.svg", "Configuration", "gconf-editor"},

};

#define SVGS ((int)(sizeof (g_aIcons) / sizeof (g_aIcons[0])))

static RsvgDimensionData g_DimensionData;
static gint g_iScreenHeight = 0;
static gint g_iCurrentWidth = 0;
static gint g_iCurrentHeight = WIN_HEIGHT;
static gboolean g_bClicked = FALSE;
static gint g_iClickedIcon = -1;
static float g_fClickedIconX = 0.0;
static float g_fMouseX = 0.0;
static float g_fMouseY = 0.0;
static guint g_uiRedraws = 0;
static guint g_uiEvents = 0;
static guint g_uiTimeoutHandlerId = 0;
static guint g_uiHideHandlerId = 0;
static float g_fInfluence = 0.0;
static float g_fMagnitude = 0.0;

#define UP 1
#define DOWN 0
#define STATIC 2

static gint g_iWindowMove = STATIC;
static gint g_iAtBottom = FALSE;

static gint g_iWindowPositionX = 0; /* dock-windows current y-position */
static gint g_iWindowPositionY = 0; /* dock-windows current y-position */
static gint g_iWindowWidth = 0; /* full screen-width */
static gint g_iWindowHeight = 0; /* 3 * icon-height */
static gint g_iDockLineWidth = 2; /* thickness of dock-bg outline */
static gint g_iDockRadius = 15; /* radius of dock-bg corners */
static gint g_iDockWidth = 0; /* current dock-width */
static gint g_iDockHeight = 0; /* current dock-height */
static gint g_iDockOffsetX = 0; /* x-position for unscaled dock */
static gint g_iDockOffsetY = 0; /* y-position for unscaled dock */
static gdouble g_fGradientOffsetX = 4.0f; /* controls gradient-animation */
static gint iInfluenceGlobal;

static gboolean g_bDrawBackground = FALSE;
static gboolean g_bUseIconBuffering = TRUE;
static gboolean g_bUseText = TRUE;
static gboolean g_bKeepAbove = TRUE;
static gboolean g_bSkipPager = TRUE;
static gboolean g_bSkipTaskbar = TRUE;
static gboolean g_bSticky = TRUE;

#ifdef HAVE_GLITZ
static gboolean g_bUseGlitz = TRUE;
static glitz_drawable_format_t *gDrawFormat = NULL;
static glitz_drawable_t* g_pGlitzDrawable = NULL;
static glitz_format_t* g_pGlitzFormat = NULL;
#endif

static gboolean g_bUseBenchmark = FALSE;
static int g_iAutoMoveDir = 1;

static void recalc_positions (Icon* pIcon, int iIcons, gdouble fX, gdouble fGap, gdouble fInfluence, gdouble fMagnitude);
static gboolean shrink_down (gpointer data);
static gboolean grow_up (gpointer data);
static gboolean clicked (gpointer data);
static gboolean none_clicked ();

static cairo_t *
dock_cairo_create (GdkWindow* pWindow)
{
#ifdef HAVE_GLITZ
	if (g_pGlitzDrawable)
	{
		glitz_surface_t* pGlitzSurface;
		cairo_surface_t* pCairoSurface;
		cairo_t* pCairoContext;

		pGlitzSurface = glitz_surface_create (g_pGlitzDrawable,
						      g_pGlitzFormat,
						      g_iCurrentWidth,
						      g_iCurrentHeight,
						      0,
						      NULL);

		if (gDrawFormat->doublebuffer)
			glitz_surface_attach (pGlitzSurface,
					      g_pGlitzDrawable,
					      GLITZ_DRAWABLE_BUFFER_BACK_COLOR);
		else
			glitz_surface_attach (pGlitzSurface,
					      g_pGlitzDrawable,
					      GLITZ_DRAWABLE_BUFFER_FRONT_COLOR);

		pCairoSurface = cairo_glitz_surface_create (pGlitzSurface);
		pCairoContext = cairo_create (pCairoSurface);

		cairo_surface_destroy (pCairoSurface);
		glitz_surface_destroy (pGlitzSurface);

		return pCairoContext;
	}
#endif

	return gdk_cairo_create (pWindow);
}

static void
on_alpha_screen_changed (GtkWidget* pWidget,
			 GdkScreen* pOldScreen,
			 GtkWidget* pLabel)
{                       
	GdkScreen* pScreen = gtk_widget_get_screen (pWidget);
	GdkColormap* pColormap = gdk_screen_get_rgba_colormap (pScreen);
      
	if (!pColormap)
		pColormap = gdk_screen_get_rgb_colormap (pScreen);

	gtk_widget_set_colormap (pWidget, pColormap);
}

static gint
get_current_dock_width ()
{
	gint iWidth = 0;

	iWidth = g_aIcons[SVGS-1].fX + g_aIcons[SVGS-1].fWidth * g_aIcons[SVGS-1].fScale - g_aIcons[0].fX + 2 * g_iDockRadius + g_iDockLineWidth;

	return iWidth;
}

static gint
get_dock_offset_y ()
{
	return g_iWindowHeight - g_aIcons[0].fHeight - g_iDockLineWidth;
}

static gint
get_current_dock_offset_x ()
{
	return g_aIcons[0].fX;
}

static gint
get_current_dock_offset_y ()
{
	return g_iWindowHeight - g_aIcons[0].fHeight - g_iDockLineWidth;
}

static void
render (cairo_t* pCairoContext,
	gint iWidth,
	gint iHeight)
{
	int icon;
	cairo_pattern_t* pPattern = NULL;

	/* set rendering-"fidelity" and clear canvas */
	cairo_set_tolerance (pCairoContext, 0.1);
	cairo_set_source_rgba (pCairoContext, 0.0, 0.0, 0.0, 0.0);
	cairo_set_operator (pCairoContext, CAIRO_OPERATOR_SOURCE);
	cairo_paint (pCairoContext);

	/* draw background */
	if (g_bDrawBackground)
	{
		cairo_save (pCairoContext);
		pPattern = cairo_pattern_create_linear (0.0f,
												0.0f,
												100.0f,
												(gdouble) iHeight);
		if (cairo_pattern_status (pPattern) == CAIRO_STATUS_SUCCESS)
		{
			gdouble fGradientAlpha = 0.4f;
			cairo_matrix_t matrix;
			gint iRadius = g_iDockRadius;
			gint iLineWidth = g_iDockLineWidth;
			gint iDockWidth = get_current_dock_width ();
			gint iDockOffsetX = get_current_dock_offset_x ();
			gint iDockOffsetY = get_dock_offset_y ();
			gdouble fStep;

			cairo_pattern_set_extend (pPattern, CAIRO_EXTEND_REPEAT);
			cairo_matrix_init_translate (&matrix, g_fGradientOffsetX, 10.0f);
			cairo_pattern_set_matrix (pPattern, &matrix);
			for (fStep = 0.0f; fStep < 1.0f; fStep += 0.1f)
			{
				cairo_pattern_add_color_stop_rgba (pPattern,
												   fStep,
												   TANGO_COLOR_ALUMINIUM1_LIGHT,
												   fGradientAlpha);
				cairo_pattern_add_color_stop_rgba (pPattern,
												   fStep + 0.025f,
												   TANGO_COLOR_ALUMINIUM1_MID,
												   fGradientAlpha);
				cairo_pattern_add_color_stop_rgba (pPattern,
												   fStep + 0.05f,
												   TANGO_COLOR_ALUMINIUM1_LIGHT,
												   fGradientAlpha);
				cairo_pattern_add_color_stop_rgba (pPattern,
												   fStep + 0.075f,
												   TANGO_COLOR_ALUMINIUM1_MID,
												   fGradientAlpha);
			}
			cairo_pattern_add_color_stop_rgba (pPattern,
											   1.0f,
											   TANGO_COLOR_ALUMINIUM1_LIGHT,
											   fGradientAlpha);

			cairo_move_to (pCairoContext, iDockOffsetX, iDockOffsetY - iLineWidth/2);
			
			cairo_rel_line_to (pCairoContext, iDockWidth -2 * iRadius - iLineWidth, 0);
			/* Top Right */
			cairo_rel_curve_to (pCairoContext,
								0, 0,
								iRadius, 0,
								iRadius, iRadius);
			cairo_rel_line_to (pCairoContext,
							   0, iHeight - iDockOffsetY - iRadius);/// - 2 * iRadius);
			/* Bottom Right */
			/*cairo_rel_curve_to (pCairoContext,
								0, 0,
								0, iRadius,
								-iRadius, iRadius);*/

			cairo_rel_line_to (pCairoContext,
							   -iDockWidth + iLineWidth, 0);
			/* Bottom Left */
			/*cairo_rel_curve_to (pCairoContext,
								0, 0,
								-iRadius, 0,
								-iRadius, -iRadius);
			cairo_rel_line_to (pCairoContext, -iRadius, -iRadius);*/


			cairo_rel_line_to (pCairoContext,
							   0, -iHeight + iDockOffsetY + iRadius);
			/* Top Left */
			cairo_rel_curve_to (pCairoContext,
								0, 0,
								0, -iRadius,
								iRadius, -iRadius);

			cairo_set_source (pCairoContext, pPattern);
			cairo_fill_preserve (pCairoContext);
			cairo_set_line_width (pCairoContext, iLineWidth);
			cairo_set_source_rgba (pCairoContext,
								   TANGO_BLACK,
								   0.3f);
			cairo_stroke (pCairoContext);
			cairo_pattern_destroy (pPattern);
		}
		cairo_restore (pCairoContext);
	}

	cairo_set_operator (pCairoContext, CAIRO_OPERATOR_OVER);

	for (icon = 0; icon < SVGS; icon++)
	{
		cairo_save (pCairoContext);
		cairo_translate (pCairoContext, g_aIcons[icon].fX, g_aIcons[icon].fY);


		/* draw the icon */
		cairo_save (pCairoContext);
		if (g_aIcons[icon].pIconBuffer)
		{
			cairo_scale (pCairoContext, g_aIcons[icon].fScale / 2.0, g_aIcons[icon].fScale / 2.0);
			cairo_set_source_surface (pCairoContext, g_aIcons[icon].pIconBuffer, 0.0, 0.0);
			cairo_paint (pCairoContext);
		}
		else
		{
			cairo_scale (pCairoContext, g_aIcons[icon].fScale, g_aIcons[icon].fScale);
			rsvg_handle_render_cairo (g_aIcons[icon].pHandle, pCairoContext);
		}
		cairo_restore (pCairoContext);

		/* draw the label-text */
		if (g_aIcons[icon].pTextBuffer && g_aIcons[icon].fScale > 1.0)
		{
			cairo_set_source_surface (pCairoContext, g_aIcons[icon].pTextBuffer,
						  -g_aIcons[icon].fTextXOffset + g_aIcons[icon].fWidth * g_aIcons[icon].fScale * 0.5,
						  -g_aIcons[icon].fTextYOffset + 0.0);
			cairo_paint_with_alpha (pCairoContext, (g_aIcons[icon].fScale *3) - 5.0 );
		}
		// Made this tighter [KL]
		cairo_restore (pCairoContext);
	}

#ifdef HAVE_GLITZ
	if (gDrawFormat && gDrawFormat->doublebuffer)
		glitz_drawable_swap_buffers (g_pGlitzDrawable);
#endif

	g_uiRedraws++;
}

static gboolean
move_up (gpointer pWidget)
{
	guint distance;
	guint max_dist;
	guint start;
	gint move;
	
	recalc_positions (g_aIcons, SVGS, g_fMouseX, GAP, g_fInfluence, g_fMagnitude);
	gtk_widget_queue_draw ((GtkWidget*) pWidget);

	if (g_uiHideHandlerId == 0) {
		g_iWindowMove = STATIC;
		return FALSE;
	}
	if (g_iWindowPositionY > g_iScreenHeight - WIN_HEIGHT)
	{
		g_iAtBottom = FALSE;

		max_dist = g_iScreenHeight - WIN_HEIGHT;
		start = g_aIcons[0].fHeight + 14;
		distance = g_iWindowPositionY - max_dist;
		move = (distance/6)+1;

		//g_print ("dist: %d, max: %d\n", distance, g_iWindowPositionY);

		
		g_iWindowPositionY -= move;
		gtk_window_move (GTK_WINDOW (pWidget),
						 g_iWindowPositionX,
						 g_iWindowPositionY);
		return TRUE;
	} else {
		if (g_uiHideHandlerId != 0)
		{
			g_source_remove (g_uiHideHandlerId);
			g_uiHideHandlerId = 0;
		}
		g_iWindowMove = STATIC;
		return FALSE;
	}
}

static gboolean
move_down (gpointer pWidget)
{
	guint distance;
	guint max_dist;
	guint start;
	gint move;
	
	recalc_positions (g_aIcons, SVGS, g_fMouseX, GAP, g_fInfluence, g_fMagnitude);
	gtk_widget_queue_draw ((GtkWidget*) pWidget);

	if (g_uiHideHandlerId == 0) {
		g_iWindowMove = STATIC;
		return FALSE;
	}

	if (g_iWindowPositionY < g_iScreenHeight - (WIN_HEIGHT - g_aIcons[0].fHeight - 14))
	{
		max_dist = g_iScreenHeight - WIN_HEIGHT;
		start = g_aIcons[0].fHeight + 14;
		distance = g_iWindowPositionY - max_dist;
		move = (distance/7)+1;

		//g_print ("dist: %d, max: %d\n", move, start);

		g_iWindowPositionY += move;

		if (g_iWindowPositionY > g_iScreenHeight - (WIN_HEIGHT - g_aIcons[0].fHeight - 14))
			g_iWindowPositionY = g_iScreenHeight - (WIN_HEIGHT - g_aIcons[0].fHeight - 14);

		gtk_window_move (GTK_WINDOW (pWidget),
						 g_iWindowPositionX,
						 g_iWindowPositionY);
		return TRUE;
	} else {
		// Should jump off screen -3px when we hit the end
		g_iAtBottom = TRUE;

		gtk_window_move (GTK_WINDOW (pWidget),
						 g_iWindowPositionX,
						 g_iScreenHeight - 3);

		if (g_uiHideHandlerId != 0)
		{
			g_source_remove (g_uiHideHandlerId);
			g_uiHideHandlerId = 0;
		}
		g_iWindowMove = STATIC;
		return FALSE;
	}
}

static gboolean
on_expose (GtkWidget*		pWidget,
	   GdkEventExpose*	pExpose)
{
	gint iWidth;
	gint iHeight;
	cairo_t* pCairoContext = NULL;

	pCairoContext = dock_cairo_create (pWidget->window);
	if (!pCairoContext)
		return FALSE;

	gtk_window_get_size (GTK_WINDOW (pWidget), &iWidth, &iHeight);
	render (pCairoContext, iWidth, iHeight);
	cairo_destroy (pCairoContext);

	return FALSE;
}

static gboolean
on_configure (GtkWidget* pWidget,
	      GdkEventConfigure* pEvent,
	      gpointer userData)
{
	gint iNewWidth = pEvent->width;
	gint iNewHeight = pEvent->height;

	if (iNewWidth != g_iCurrentWidth || iNewHeight != g_iCurrentHeight)
	{
		g_iCurrentWidth = iNewWidth;
		g_iCurrentHeight = iNewHeight;

#ifdef HAVE_GLITZ
		if (g_pGlitzDrawable)
			glitz_drawable_update_size (g_pGlitzDrawable,
						    g_iCurrentWidth,
						    g_iCurrentHeight);
#endif
	}

	return FALSE;
}

static gboolean
on_key_press (GtkWidget*	pWidget,
	      GdkEventKey*	pKey,
	      gpointer		userData)
{
	gint iX = 0;
	gint iY = 0;

	if (pKey->type == GDK_KEY_PRESS)
	{
		switch (pKey->keyval)
		{
			case GDK_Escape :
			case GDK_q :
				gtk_main_quit ();
			break;

			case GDK_Down :
				gtk_window_get_position (GTK_WINDOW (pWidget), &iX, &iY);
				if (iY < g_iScreenHeight - 1)
				{
					iY += 2;
					gtk_window_move (GTK_WINDOW (pWidget), iX, iY);
				}
			break;

			case GDK_Up :
				gtk_window_get_position (GTK_WINDOW (pWidget), &iX, &iY);
				if (iY > g_iScreenHeight - WIN_HEIGHT)
				{
					iY -= 2;
					gtk_window_move (GTK_WINDOW (pWidget), iX, iY);
				}
			break;
		}
	}

	return FALSE;
}

static gboolean
on_button_press (GtkWidget* pWidget,
		 GdkEventButton* pButton,
		 GdkWindowEdge edge)
{
	Icon *pIcon = g_aIcons;

	if (pButton->type == GDK_BUTTON_PRESS)
	{
		switch (pButton->button)
		{
			int icon;

			case 1:
			if (!g_bClicked)
			{
				g_iClickedIcon = -1;
				
				for (icon = 0; icon < SVGS; icon++)
					if (pIcon[icon].fX <= g_fMouseX &&
					    g_fMouseX <= pIcon[icon].fX + pIcon[icon].fWidth * pIcon[icon].fScale)
					{
						g_iClickedIcon = icon;

						g_bClicked = TRUE;
					}

				if (g_bClicked)
				{
					icon = g_iClickedIcon;

					g_fClickedIconX = pIcon[icon].fX
					                + pIcon[icon].fWidth * pIcon[icon].fScale / 2;

					g_uiTimeoutHandlerId = g_timeout_add (30, clicked, (gpointer) pWidget);
					pIcon[icon].bClicked = TRUE;
				}
			}
			break;

			case 2:
			gtk_window_begin_move_drag (GTK_WINDOW (gtk_widget_get_toplevel (pWidget)),
						    pButton->button,
						    pButton->x_root,
						    pButton->y_root,
						    pButton->time);
			break;

			case 3:
			gtk_window_begin_resize_drag (GTK_WINDOW (gtk_widget_get_toplevel (pWidget)),
						      edge,
						      pButton->button,
						      pButton->x_root,
						      pButton->y_root,
						      pButton->time);
			break;
		}
	}

	return FALSE;
}

static gboolean
on_motion_notify (GtkWidget* pWidget,
		  GdkEventMotion* pMotion,
		  gpointer data)
{
	gint iMouseX;
	gint iMouseY;
	gdouble fLastMouseX;

	if (g_bClicked)
		return FALSE;

	gdk_window_get_pointer (pWidget->window, &iMouseX, &iMouseY, NULL);

	fLastMouseX = g_fMouseX;
	g_fMouseX = (gdouble) iMouseX;
	g_fMouseY = (gdouble) iMouseY;

	if (fLastMouseX < g_fMouseX)
		g_fGradientOffsetX = (g_fGradientOffsetX > 0.0f) ?
							 (g_fGradientOffsetX -= 1.0f) :
							 15.0f;
	else if (fLastMouseX > g_fMouseX)
		g_fGradientOffsetX = (g_fGradientOffsetX < 15.0f) ?
							 (g_fGradientOffsetX += 1.0f) :
							 0.0f;

	/* Karl Lattimer - modified
	 * 
	 * There are some hackish bits in here, i'm very tired at present but i think i've cracked it
	 * What I've done here is make it grow when entered and shrink when leaving, this includes
	 * leaving via the sides and entering via the sides.
	 */
	int icon;
	gdouble fStart = iInfluenceGlobal;
	gdouble fEnd = fStart - GAP;
	gdouble fTop = 0;
	gint dir;

	for (icon = 0; icon < SVGS; icon++)
		fEnd += GAP + g_aIcons[icon].fWidth;
	
	if (g_fMagnitude < 0.01)
		g_fMagnitude = 0;
	else if (g_fMagnitude > 1.0)
		g_fMagnitude = 1.0;

	fTop = get_current_dock_offset_y();
	fTop -= fTop * g_fMagnitude;
	fTop -= g_iDockLineWidth;


	// Should get the position of the window and more sensibly detect
	// if dir should be UP when only 3px are showing at the bottom
	// of the screen.
	if (g_fMouseY > (get_current_dock_offset_y() - 9))
		dir = UP;	
	else if (g_fMouseY <= (fTop - 5))
		dir = DOWN;

	if (g_iAtBottom && (g_fMouseY > 1)) {
		dir = UP;
	}
	if ((g_iWindowMove == DOWN) && (dir == UP)) {
		//g_print ("Changing direction DOWN to UP\n");
		if (g_uiHideHandlerId != 0)
		{
			g_source_remove (g_uiHideHandlerId);
			g_uiHideHandlerId = 0;
		}
		
	} else if ((g_iWindowMove == UP) && (dir == DOWN)) {
		//g_print ("Changing direction UP to DOWN\n");
		if (g_uiHideHandlerId != 0)
		{
			g_source_remove (g_uiHideHandlerId);
			g_uiHideHandlerId = 0;
		}
		g_iWindowMove = dir;
	}

	g_iWindowMove = dir;

	if (g_uiHideHandlerId == 0) {
		if (dir == UP) {
			g_uiHideHandlerId = g_timeout_add (15, move_up, (gpointer) pWidget);	
		} else if (dir == DOWN) {
			g_uiHideHandlerId = g_timeout_add (15, move_down, (gpointer) pWidget);
			if (g_uiTimeoutHandlerId != 0)
			{
				g_source_remove (g_uiTimeoutHandlerId);
				g_uiTimeoutHandlerId = 0;
			}
			g_uiTimeoutHandlerId = g_timeout_add (20, shrink_down, (gpointer) pWidget);
		}
	}
	//g_print ("X: %f, Y: %f\n", g_fMouseX, g_fMouseY);

	if ((g_fMouseX > fStart) && (g_fMouseX < fEnd) && (g_fMouseY > fTop)) {
		if ((g_fMagnitude == 0) && (g_uiTimeoutHandlerId == 0)) {
			g_uiTimeoutHandlerId = g_timeout_add (16, grow_up, (gpointer) pWidget);
			if ((g_uiHideHandlerId != 0) && (g_iWindowMove == DOWN)) 
			{
				g_source_remove (g_uiHideHandlerId);
				g_uiHideHandlerId = 0;
			} 
			if (g_uiHideHandlerId == 0) {
				g_uiHideHandlerId = g_timeout_add (15, move_up, (gpointer) pWidget);
			}
		} else if ((g_uiTimeoutHandlerId != 0) && (g_fMagnitude == 1.0)) {
			g_source_remove (g_uiTimeoutHandlerId);
			g_uiTimeoutHandlerId = 0;
			g_fMagnitude = 1.0;
		} else if (g_fMagnitude == 1.0) {
			recalc_positions (g_aIcons, SVGS, g_fMouseX, GAP, g_fInfluence, g_fMagnitude);
			gtk_widget_queue_draw (pWidget);
		}
	} else { 
		if ((g_fMagnitude == 1.0) && (g_uiTimeoutHandlerId == 0)) {
			g_uiTimeoutHandlerId = g_timeout_add (16, shrink_down, (gpointer) pWidget);
		} else if ((g_uiTimeoutHandlerId != 0) && (g_fMagnitude == 0)) {
			g_source_remove (g_uiTimeoutHandlerId);
			g_uiTimeoutHandlerId = 0;
			g_fMagnitude = 0;
		}
	}

	g_uiEvents++;

	return FALSE;
}

static gboolean
on_enter_notify (GtkWidget* pWidget,
		 GdkEventCrossing* pEvent,
		 gpointer data)
{
	if (g_bUseBenchmark)
		g_iAutoMoveDir = 0;

	g_bClicked = FALSE;
	g_fInfluence = INFLUENCE;

	/*if (g_uiHideHandlerId != 0)
	{
		g_source_remove (g_uiHideHandlerId);
		g_uiHideHandlerId = 0;
	}*/

	//g_uiHideHandlerId = g_timeout_add (100, move_up, (gpointer) pWidget);

	return FALSE;
}

static gboolean
benchmark (gpointer data)
{
	g_fMouseX += g_iAutoMoveDir;

	if ((g_iAutoMoveDir > 0 && g_fMouseX >= g_iCurrentWidth) ||
	    (g_iAutoMoveDir < 0 && g_fMouseX <= 0))
		g_iAutoMoveDir = -g_iAutoMoveDir;

	recalc_positions (g_aIcons, SVGS, g_fMouseX, GAP, g_fInfluence, g_fMagnitude);

	gtk_widget_queue_draw ((GtkWidget*) data);

	return TRUE;
}

static gboolean
on_leave_notify (GtkWidget* pWidget,
		 GdkEventCrossing* pEvent,
		 gpointer data)
{
	if (g_uiTimeoutHandlerId != 0)
	{
		g_source_remove (g_uiTimeoutHandlerId);
		g_uiTimeoutHandlerId = 0;
	}
	if (g_uiTimeoutHandlerId != 0)
		return FALSE;

	if (g_bUseBenchmark)
		g_iAutoMoveDir = 1;
	
	g_uiTimeoutHandlerId = g_timeout_add (17, shrink_down, (gpointer) pWidget);

	
	if (g_uiHideHandlerId != 0)
	{
		g_source_remove (g_uiHideHandlerId);
		g_uiHideHandlerId = 0;			
	} 

	g_uiHideHandlerId = g_timeout_add (15, move_down, (gpointer) pWidget);
	return FALSE;
}

static gboolean
none_clicked (void)
{
	int i;

	for (i = 0; i < SVGS; i++)
		if (g_aIcons[i].bClicked)
			return FALSE;

	return TRUE;
}

static gboolean
clicked (gpointer data)
{
	if (g_fInfluence / INFLUENCE > 0.01)
		g_fInfluence *= 0.8;
	else
		g_fInfluence = 0.0;

	g_fMouseX = g_fMouseX * 0.63 + g_fClickedIconX * 0.37;

	recalc_positions (g_aIcons, SVGS, g_fMouseX, GAP, g_fInfluence, g_fMagnitude);

	gtk_widget_queue_draw ((GtkWidget*) data);

	if (g_fInfluence < 0.01 && none_clicked ())
	{
		g_uiTimeoutHandlerId = 0;

		if (g_bUseBenchmark)
		{
			g_iAutoMoveDir = 1;
			g_fInfluence = INFLUENCE;
		}

		return FALSE;
	}
	else
		return TRUE;
}

static gboolean
grow_up (gpointer data)
{
	if (g_fMagnitude < 0.01)
		g_fMagnitude = 0.01;
	
	if (g_fMagnitude < 0.99)
		g_fMagnitude /= 0.5;
	
	if (g_fMagnitude > 1.0)
		g_fMagnitude = 1.0;
				
	recalc_positions (g_aIcons, SVGS, g_fMouseX, GAP, g_fInfluence, g_fMagnitude);
	gtk_widget_queue_draw ((GtkWidget*) data);

	if (g_fMagnitude > 0.99 && none_clicked ())
	{
		g_uiTimeoutHandlerId = 0;
		return FALSE;
	}
	else
		return TRUE;
}

static gboolean
shrink_down (gpointer data)
{
	if (g_fMagnitude > 0.01)
		g_fMagnitude *= 0.618;
	else
		g_fMagnitude = 0.0;
		
	recalc_positions (g_aIcons, SVGS, g_fMouseX, GAP, g_fInfluence, g_fMagnitude);
	gtk_widget_queue_draw ((GtkWidget*) data);

	if (g_fMagnitude < 0.01 && none_clicked ())
	{
		g_fMagnitude = 0;
		g_uiTimeoutHandlerId = 0;
		return FALSE;
	}
	else
		return TRUE;
}

static gdouble
scale (gdouble delta, gdouble fInfluence, gdouble fMagnitude)
{
	gdouble rate = fInfluence / M_PI_2;

	if (delta <= -fInfluence)
		return 1.0;
	if (delta >= +fInfluence)
		return 1.0;

		return 1.0 + fMagnitude * cosf (delta / rate);
}

static gdouble
scaleIntegral (gdouble delta, gdouble fInfluence, gdouble fMagnitude)
{
	gdouble rate = fInfluence / M_PI_2;
	gdouble expansion = fMagnitude * rate;

	if (delta <= -fInfluence)
		return delta - expansion;

	if (delta >= +fInfluence)
		return delta + expansion;

		return delta + expansion * sin (delta / rate);
}

static gdouble
scaledPosition (gdouble fX, gdouble fMouseX, gdouble fInfluence, gdouble fMagnitude)
{
	return fMouseX + scaleIntegral (fX - fMouseX, fInfluence, fMagnitude);
}

static void
recalc_positions (Icon* pIcon, int iIcons,
		  gdouble fMouseX, gdouble fGap, gdouble fInfluence, gdouble fMagnitude)
{
	int icon;
	gdouble fStart = iInfluenceGlobal;
	gdouble fEnd = fStart - fGap;
	gdouble fLastX = fStart;
	gdouble fAdjustment = 0.0;

	for (icon = 0; icon < iIcons; icon++)
		fEnd += fGap + pIcon[icon].fWidth;

	for (icon = 0; icon < iIcons; icon++)
	{
		gdouble fWidth;
		gdouble fHeight;
		gdouble fScale;
		gdouble fStartX;
		gdouble fX;
		gdouble fScaledX;

		fWidth = pIcon[icon].fWidth;
		fHeight = pIcon[icon].fHeight;

		fStartX = fLastX;
		fLastX += fWidth + fGap;

		//fX = MIN (MAX (fStartX, fMouseX), fStartX + fWidth * 0.5);
		fX = fStartX + fWidth * 0.5;
		fScaledX = scaledPosition (fX, fMouseX, fInfluence, fMagnitude);

		fScale = scale (fX - fMouseX, fInfluence, fMagnitude);

		fWidth *= fScale;
		fHeight *= fScale;

		pIcon[icon].fX = fScaledX - (fX - fStartX) * fScale;

		if (pIcon[icon].bClicked)
		{
			pIcon[icon].fY = 50.0 + 2.0 * pIcon[icon].fHeight - pIcon[icon].fScale * pIcon[icon].fHeight - 40.0f * fabs (sin (pIcon[icon].fPeriod));
			pIcon[icon].fPeriod += 3*M_PI/50.0f;

			if (pIcon[icon].fPeriod >= 2 * M_PI)
			{
				GError* pError = NULL;

				pIcon[icon].fPeriod = 0.0f;
				pIcon[icon].bClicked = FALSE;
				g_spawn_command_line_async (pIcon[icon].acCommand, &pError);
			}
		}
		else
			pIcon[icon].fY = 50.0 + 2.0 * pIcon[icon].fHeight - fHeight;

		pIcon[icon].fScale = fScale;
	}

	if (iIcons > 0)
	{
		if (fMouseX < fStart)
			fAdjustment = fStart - pIcon[0].fX;
		else if (fMouseX > fEnd)
			fAdjustment = fEnd - (pIcon[iIcons - 1].fWidth * pIcon[iIcons - 1].fScale) - pIcon[iIcons - 1].fX;
	}

	for (icon = 0; icon < iIcons; icon++)
		pIcon[icon].fX += fAdjustment;
}

static void
fill_icon_buffer (cairo_t* pSourceContext,
		  Icon* pIcon,
		  int iIcons,
		  gdouble fMaxScale)
{
	int icon;

	for (icon = 0; icon < iIcons; icon++)
	{
		cairo_surface_t* pNewSurface;
		cairo_t* pCairoContext;

		pNewSurface = cairo_surface_create_similar (cairo_get_target (pSourceContext),
							    CAIRO_CONTENT_COLOR_ALPHA,
							    ceil (pIcon[icon].fWidth * fMaxScale),
							    ceil (pIcon[icon].fHeight * fMaxScale));
		pCairoContext = cairo_create (pNewSurface);

		/* draw stuff */
		cairo_scale (pCairoContext, fMaxScale, fMaxScale);
		rsvg_handle_render_cairo (pIcon[icon].pHandle, pCairoContext);

		cairo_destroy (pCairoContext);
		pIcon[icon].pIconBuffer = pNewSurface;
	}
}

static void
fill_text_buffer (cairo_t* pSourceContext,
		  Icon* pIcon,
		  int iIcons,
		  gdouble fMaxScale)
{
	// KL fixed the text, made it look decent
	int icon;
	PangoFontDescription *pDesc;
	PangoLayout *pLayout;

	pLayout = pango_cairo_create_layout (pSourceContext);

	pDesc = pango_font_description_new ();
	pango_font_description_set_absolute_size (pDesc, 15 * PANGO_SCALE);
	pango_font_description_set_family_static (pDesc, "sans");
	pango_font_description_set_weight(pDesc, PANGO_WEIGHT_SEMIBOLD);
	pango_layout_set_font_description (pLayout, pDesc);
	pango_font_description_free (pDesc);

	for (icon = 0; icon < iIcons; icon++)
	{
		cairo_surface_t* pNewSurface;
		cairo_t* pCairoContext;
		gint i;
		PangoRectangle ink, log;

		pango_layout_set_text (pLayout, pIcon[icon].acName, -1);
		pango_layout_get_pixel_extents (pLayout, &ink, &log);

		pNewSurface = cairo_surface_create_similar (cairo_get_target (pSourceContext),
							    CAIRO_CONTENT_COLOR_ALPHA,
							    ink.width + 2, ink.height + 2);
		pCairoContext = cairo_create (pNewSurface);
		cairo_translate (pCairoContext, -ink.x, -ink.y);

		cairo_push_group (pCairoContext);
		cairo_set_source_rgb (pCairoContext, 0.2, 0.2, 0.2);
		for (i = 0; i < 4; i++)
		{
			cairo_move_to (pCairoContext, i&2, 2*(i&1));
			pango_cairo_show_layout (pCairoContext, pLayout);
		}
		cairo_pop_group_to_source (pCairoContext);
		cairo_paint_with_alpha (pCairoContext, .7);

		cairo_set_source_rgb (pCairoContext, 1., 1., 1.);
		cairo_move_to (pCairoContext, 1., 1.);
		pango_cairo_show_layout (pCairoContext, pLayout);

		cairo_destroy (pCairoContext);

		/* set_device_offset is buggy, doesn't work for positive
		 * offsets.  so we use explicit offsets... so unfortunate.
		cairo_surface_set_device_offset (pNewSurface, 
						 log.width / 2. - ink.x,
						 log.height     - ink.y);
		 */
		pIcon[icon].fTextXOffset = log.width / 2. - ink.x;
		pIcon[icon].fTextYOffset = log.height     - ink.y;
		pIcon[icon].pTextBuffer = pNewSurface;
	}

	g_object_unref (pLayout);
}

static gboolean
spit_out_redraws (gpointer data)
{
	g_print ("%d fps, %d events\n", g_uiRedraws, g_uiEvents);
	g_uiRedraws = 0;
	g_uiEvents = 0;

	return TRUE;
}

int
main (int argc, char** argv)
{
	GtkWidget* pWindow = NULL;
	GdkScreen *gdkscreen = NULL;
	int icon = 0;
	GError* pError = NULL;
	guint uiHandlerId = 0;
	guint uiBenchmarkId = 0;
	cairo_t* pCairoContext = NULL;
	gint i;
 
 	gtk_init (&argc, &argv);
 
	for (i = 0; i < argc; i++)
	{
		if (strcmp (argv[i], "--benchmark") == 0)
			g_bUseBenchmark = TRUE;
		else if (strcmp (argv[i], "--glitz") == 0)
		{
#ifdef HAVE_GLITZ
			g_bUseGlitz = TRUE;
#else
			fprintf (stderr, "Not compiled with glitz\n");
			return 1;
#endif
		}
		else if (strcmp (argv[i], "--no-glitz") == 0)
		{
#ifdef HAVE_GLITZ
			g_bUseGlitz = FALSE;
#endif
		}
		else if (strcmp (argv[i], "--no-text") == 0)
			g_bUseText = FALSE;
		else if (strcmp (argv[i], "--no-buffering") == 0)
			g_bUseIconBuffering = FALSE;
		else if (strcmp (argv[i], "--no-keep-above") == 0)
			g_bKeepAbove = FALSE;
		else if (strcmp (argv[i], "--no-skip-pager") == 0)
			g_bSkipPager = FALSE;
		else if (strcmp (argv[i], "--no-skip-taskbar") == 0)
			g_bSkipTaskbar = FALSE;
		else if (strcmp (argv[i], "--no-sticky") == 0)
			g_bSticky = FALSE;
		else if (strcmp (argv[i], "--no-background") == 0)
			g_bDrawBackground = FALSE;
		else if (argv[i][0] == '-')
		{
			gboolean help = (strcmp (argv[i], "--help") == 0);
			fprintf (help ? stdout : stderr,
				 "Usage: %s [--benchmark] [--no-glitz] [--no-text] [--no-buffering] [--no-keep-above] [--no-skip-pager] [--no-skip-taskbar] [--no-sticky] [--no-background] [--help]\n",
				 argv[0]);
			return help ? 0 : 1;
		}
	}


	rsvg_init ();

	for (icon = 0; icon < SVGS; icon++)
	{
		g_aIcons[icon].pHandle = rsvg_handle_new_from_file (g_aIcons[icon].acFileName, &pError);
		rsvg_handle_get_dimensions (g_aIcons[icon].pHandle, &g_DimensionData);
		g_aIcons[icon].fWidth = (gdouble) g_DimensionData.width;
		g_aIcons[icon].fHeight = (gdouble) g_DimensionData.height;
		g_aIcons[icon].bClicked = FALSE;
		g_aIcons[icon].fPeriod = 0.0f;
	}

	pWindow = gtk_window_new (GTK_WINDOW_TOPLEVEL);
	gdkscreen = gtk_window_get_screen (GTK_WINDOW (pWindow));
	g_iCurrentWidth = gdk_screen_get_width (gdkscreen);

	g_iWindowWidth = gdk_screen_get_width (gdkscreen);
	g_iWindowHeight = 3 * g_aIcons[0].fHeight;

#ifdef HAVE_GLITZ
	if (g_bUseGlitz)
	{
	    glitz_drawable_format_t templ, *format;
	    unsigned long	    mask = 0;
	    XVisualInfo		    *vinfo = NULL;
	    int			    screen = 0;
	    GdkVisual		    *visual;
	    GdkColormap		    *colormap;
	    GdkDisplay		    *gdkdisplay;
	    Display		    *xdisplay;

	    templ.doublebuffer = 1;
	    mask |= GLITZ_FORMAT_DOUBLEBUFFER_MASK;

	    gdkdisplay = gtk_widget_get_display (pWindow);
	    xdisplay   = gdk_x11_display_get_xdisplay (gdkdisplay);

	    i = 0;
	    do {
		format = glitz_glx_find_window_format (xdisplay, screen,
						       mask, &templ, i++);
		if (format)
		{
		    vinfo = glitz_glx_get_visual_info_from_format (xdisplay,
								   screen,
								   format);
		    if (vinfo->depth == 32)
		    {
			gDrawFormat = format;
			break;
		    }
		    else
		    {
			if (!gDrawFormat)
			    gDrawFormat = format;
		    }
		}
	    } while (format);

		if (!gDrawFormat)
		{
			fprintf (stderr, "no double buffered GLX visual\n");
			return 1;
		}

		vinfo = glitz_glx_get_visual_info_from_format (xdisplay,
							       screen,
							       gDrawFormat);

		visual = gdkx_visual_get (vinfo->visualid);
		colormap = gdk_colormap_new (visual, TRUE);

		gtk_widget_set_colormap (pWindow, colormap);
		gtk_widget_set_double_buffered (pWindow, FALSE);
	}
	else
#endif
	on_alpha_screen_changed (pWindow, NULL, NULL);

	gtk_widget_set_app_paintable (pWindow, TRUE);
	gtk_window_set_decorated (GTK_WINDOW (pWindow), FALSE);
	gtk_window_set_resizable (GTK_WINDOW (pWindow), FALSE);
	gtk_window_set_title (GTK_WINDOW (pWindow), "cairo-dock");
	gtk_widget_set_size_request (pWindow, g_iCurrentWidth, g_iCurrentHeight);
	g_iScreenHeight = gdk_screen_get_height (gdkscreen);
	g_iWindowPositionX = 0;
	g_iWindowPositionY = g_iScreenHeight - WIN_HEIGHT;
	gtk_window_move (GTK_WINDOW (pWindow), g_iWindowPositionX, g_iWindowPositionY);
	gtk_widget_add_events (pWindow,
			       GDK_BUTTON_PRESS_MASK |
			       GDK_POINTER_MOTION_MASK |
			       GDK_POINTER_MOTION_HINT_MASK);

	gtk_widget_show (pWindow);
	if (g_bSticky)
		gtk_window_stick (GTK_WINDOW (pWindow));
	gtk_window_set_keep_above (GTK_WINDOW (pWindow), g_bKeepAbove);
	gtk_window_set_skip_pager_hint (GTK_WINDOW (pWindow), g_bSkipPager);
	gtk_window_set_skip_taskbar_hint (GTK_WINDOW (pWindow), g_bSkipTaskbar);

	g_signal_connect (G_OBJECT (pWindow),
			  "destroy",
			  G_CALLBACK (gtk_main_quit),
			  NULL);
	g_signal_connect (G_OBJECT (pWindow),
			  "expose-event",
			  G_CALLBACK (on_expose),
			  NULL);
	g_signal_connect (G_OBJECT (pWindow),
			  "configure-event",
			  G_CALLBACK (on_configure),
			  NULL);
	g_signal_connect (G_OBJECT (pWindow),
			  "key-press-event",
			  G_CALLBACK (on_key_press),
			  NULL);
	g_signal_connect (G_OBJECT (pWindow),
			  "button-press-event",
			  G_CALLBACK (on_button_press),
			  NULL);
	g_signal_connect (G_OBJECT (pWindow),
			  "motion-notify-event",
			  G_CALLBACK (on_motion_notify),
			  NULL);
	g_signal_connect (G_OBJECT (pWindow),
			  "enter-notify-event",
			  G_CALLBACK (on_enter_notify),
			  NULL);
	g_signal_connect (G_OBJECT (pWindow),
			  "leave-notify-event",
			  G_CALLBACK (on_leave_notify),
			  NULL);

	pCairoContext = dock_cairo_create (pWindow->window);
	if (g_bUseText)
		fill_text_buffer (pCairoContext, g_aIcons, SVGS, 2.0);
	if (g_bUseIconBuffering)
		fill_icon_buffer (pCairoContext, g_aIcons, SVGS, 2.0);
	cairo_destroy (pCairoContext);

#ifdef HAVE_GLITZ
	if (g_bUseGlitz)
	{
		glitz_format_t templ;
		GdkDisplay	   *gdkdisplay;
		Display	   *xdisplay;
		Window	   xid;

		gdkdisplay = gdk_display_get_default ();
		xdisplay   = gdk_x11_display_get_xdisplay (gdkdisplay);

		xid = gdk_x11_drawable_get_xid (GDK_DRAWABLE (pWindow->window));

		g_pGlitzDrawable = glitz_glx_create_drawable_for_window (xdisplay,
									 0,
									 gDrawFormat,
									 xid,
									 g_iCurrentWidth,
									 g_iCurrentHeight);
		if (!g_pGlitzDrawable)
		{
			fprintf (stderr, "failed to create drawable\n");
			return 1;
		}

		templ.color        = gDrawFormat->color;
		templ.color.fourcc = GLITZ_FOURCC_RGB;

		g_pGlitzFormat = glitz_find_format (g_pGlitzDrawable,
						    GLITZ_FORMAT_RED_SIZE_MASK   |
						    GLITZ_FORMAT_GREEN_SIZE_MASK |
						    GLITZ_FORMAT_BLUE_SIZE_MASK  |
						    GLITZ_FORMAT_ALPHA_SIZE_MASK |
						    GLITZ_FORMAT_FOURCC_MASK,
						    &templ,
						    0);
		if (!g_pGlitzFormat)
		{
			fprintf (stderr, "couldn't find surface format\n");
			return 1;
		}
	}
#endif

	g_fInfluence = INFLUENCE;
	g_fMagnitude = 0.0;
	
	gdouble fEnd;

	for (icon = 0; icon < SVGS; icon++)
		fEnd += GAP + g_aIcons[icon].fWidth;
	
	iInfluenceGlobal = ( g_iWindowWidth - (int)fEnd)/2;

	recalc_positions (g_aIcons, SVGS, g_fMouseX, GAP, g_fInfluence, g_fMagnitude);

	if (g_bUseBenchmark)
	{
		g_fMagnitude = 1.0;
		recalc_positions (g_aIcons, SVGS, g_fMouseX, GAP, g_fInfluence, g_fMagnitude);

 		uiHandlerId = g_timeout_add (1000, spit_out_redraws, NULL);
		uiBenchmarkId = g_idle_add (benchmark, (gpointer) pWindow);
	}


	gtk_main ();

	if (uiHandlerId)
		g_source_remove (uiHandlerId);
	if (uiBenchmarkId)
		g_source_remove (uiBenchmarkId);

	for (icon = 0; icon < SVGS; icon++)
	{
		rsvg_handle_free (g_aIcons[icon].pHandle);
		cairo_surface_destroy (g_aIcons[icon].pIconBuffer);
	}

	rsvg_term ();

	return 0;
}
```

---

### Post by maxfact on 2007-06-22
now risolto my problem
gnome-dock is ever up 
i have stopped autohide

very very felicity: :D:D:D

---

### Post by Vendetta_NZ on 2007-07-11
I have a problem with this. When I cd to /opt/cairo-dock/ in terminal, then run the ./cairo-dock --no-glitz command the dock opens. But when I close the terminal window, it goes again?

---

### Post by Del Piero on 2007-07-14
I am stuck at the last step of installation:

> omar@Megatron:/opt/cairo-dock$ make clean
rm -f *.o *~ cairo-dock
rm: cannot remove `cairo-dock.c~': Permission denied
rm: cannot remove `cairo-dock': Permission denied
make: *** [clean] Error 1
omar@Megatron:/opt/cairo-dock$ sudo make clean
rm -f *.o *~ cairo-dock
omar@Megatron:/opt/cairo-dock$ make
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
/usr/bin/ld: cannot open output file cairo-dock: Permission denied
collect2: ld returned 1 exit status
make: *** [cairo-dock] Error 1
omar@Megatron:/opt/cairo-dock$ sudo make
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [cairo-dock] Error 1
omar@Megatron:/opt/cairo-dock$ sudo make
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [cairo-dock] Error 1
omar@Megatron:/opt/cairo-dock$ ./cairo-dock --no-glitz
bash: ./cairo-dock: No such file or directory
omar@Megatron:/opt/cairo-dock$ make
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
/usr/bin/ld: cannot open output file cairo-dock: Permission denied
collect2: ld returned 1 exit status
make: *** [cairo-dock] Error 1
omar@Megatron:/opt/cairo-dock$ sudo make
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [cairo-dock] Error 1
omar@Megatron:/opt/cairo-dock$ sudo make install
make: *** No rule to make target `install'.  Stop.
omar@Megatron:/opt/cairo-dock$ 

---

### Post by Del Piero on 2007-07-14
please i need help here!

---

### Post by Smilez:) on 2007-07-27
Go mine working nice thought, thanks for the howto. 
running Fiesty Fawn and beryl 0.2.1


here's a screenshot

---

### Post by Depressed Man on 2007-07-27
Interesting.. but does this dock show a thumbnail of the window when minimized? It's one of the reasons I've been sticking with kiba dock (well the fact that I'm stuck when it comes to compiling Kiba dock just so I can have the option that lets me have my windows go completly under the dock is a negative).

---

### Post by nashienet on 2007-08-04
Hi,

I am a complete newbie to Linux so please forgive me for asking a very obvious question.

I've downloaded Cairo and saved it in 'Documents' as a tar.gz file... the next installation instruction: 

4. Install Cairo 1.2.6

./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc

If I enter that into the Terminal window it doesn't seem to like ./configure

Is there a step before that which is so obvious to people who have used Linux before that I have missed out?  What is configure actually doing? Is that meant to be installing the tar file or merely assuming you have already installed it and now you wish to configure bits of it?

Are there any other instructions or guides around about how to setup Gnome Dock? I am using Ubuntu 7.04.

---

### Post by fabounet on 2007-08-08
Hello world !
if you liked gnome-dock, maybe you can be interested by this topic on ubuntu-fr.org :
[the thread]("http://forum.ubuntu-fr.org/viewtopic.php?id=131714&p=1") and 
[the doc]("http://doc.ubuntu-fr.org/gnome_dock")
ok it's in french, but I think you can guess easily what's happening there ;-)

---

### Post by pw378 on 2007-08-19
You can download a huge collection of .svg clipart from Open Clip Art Library to use with the dock.   

[http://openclipart.org/media/downloads](http://openclipart.org/media/downloads)

---

### Post by Yes on 2007-08-28
Ok, I installed it fine, and I can run the dock, but whenever I move my mouse close to the bottom of the screen, the dock disappears, and so I can't click any of the icons.  Also, how do I add any icons?

Thanks.

Edit: Also, when I try running the command from the terminal, is there any way to leave the dock up and close the terminal?  I tried running /opt/cairo-dock/./cairo-dock --no-glitz from the alt+F2 dialog, but it the dock is vertical, instead of horizontal when I do that.

---

### Post by fabounet on 2007-08-28
set up the dock on the edge of the screen so that you don't go out of it unexpectedly.
Use arrows to move it, or just edit the conf file.
The attitude of the dock is also a parameter you can change in the conf panel, it's not depending on the way you launch it, so you can use alt+f2 safely.
If you close the terminal that has launched a program, of course it will kill this one (maybe the "bg" command can help, but not sure).
But of course the best way is to launch the dock on start, use the script named "launch-cairo-dock-after-beryl.sh" for that.

---

### Post by Yes on 2007-08-28
It is on the bottom edge of the screen.  What file is the conf file?

I use one command from the terminal, and the dock is horizontal.  I use the exact same command from alt+f2, and the dock is vertical.

Anyone know what my problem is?

Thanks.

---

### Post by patambrosio on 2007-08-30
i think i did something bad to my setup at home.

i did

sudo apt-get **autoremove **librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev

and after that i can't see no GUI anymore, only the terminal. how can i bring it back?

i already tried installing those packages again, and even nautilus-*, but still doesn't work.

please help. :(

---

### Post by fabounet on 2007-08-31
maybe you can try apt-get install gnome ? or some meta-package like ubuntu-desktop.

---

### Post by maxtran on 2007-09-05
Can anybody tell me how to disable the auto hide in gnome dock?
 Thank You

---

### Post by fabounet on 2007-09-08
right click -> configure -> Auto-Hide : uncheck the box.

---

### Post by LLR650 on 2007-09-10
Alright guys i've been trying to get this to work for awhile now with no luck. When i try to run the cairo i get these messages and more.....


(cairo-dock:27123): librsvg-CRITICAL **: rsvg_handle_get_dimensions: assertion `handle' failed

(cairo-dock:27123): GLib-WARNING **: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Failed to open file 'gnome-terminal.svg': No such file or directory

(cairo-dock:27123): librsvg-CRITICAL **: rsvg_handle_get_dimensions: assertion `handle' failed

---

### Post by maxtran on 2007-09-10
Why we have to type "./cairo-dock --no-glitz" to start the dock? Why not only "./cairo-dock"? What --no-glitz for?
 So is there anyway to start the dock by only type "./cairo-dock"?
 Thank you

---

### Post by sophtpaw on 2007-09-15
> **GPH said:**
> No, I meant the build-essential packages, but you also need AIGLX/XGL to be able to run this. BTW, does it work for someone else than me ?

could have said xgl was a prerequisite... 

it said build essential so i thought... cool... sorted...
i follow the whole how-to only to find out at the end i need xgl... pffffff.... let make the prerequisites clear from the beginning...

I don't have 3D accelaration on this computer, so all that for naught... sill wondering if there is not a way of crating a nice gnome dock without xgl. or compiz or beryl... on an ordinary 2D desktop..

thank you

--
sophtpaw

---

### Post by Fejker on 2007-09-18
I have a *n00b-ish* problem. When I execute the first command I get the following...

```
fejker@fejker-laptop:~$ sudo apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
librsvg2-common is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  librsvg2-dev: Depends: libgtk2.0-dev (>= 2.8.17-1) but it is not going to be installed
E: Broken packages

```

If I try adding libgtk2.0-dev I get the following...
```
fejker@fejker-laptop:~$ sudo apt-get install librsvg2-bin librsvg2-common librsvg2-dev libglitz-glx1 libglitz-glx1-dev libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
librsvg2-common is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.12) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
E: Broken packages

```

... and so on and so on ... the list grows beyond comprehension. :(

Can someone please help me? I really want to try this since I'm not too happy with the AWN bar (too buggy).

---

### Post by fabounet on 2007-09-19
sophtpaw : you can run the dock with transparency thanks to xcompmgr if you can't run Beryl.

Fejker : first you should repar your broken packages with Synaptic.
which version of Ubuntu do you use ? Feisty is recommended (though you can run the dock on any Ubuntu version, but then you have to install GTK and so on by yourself

@maxtran : --no-glitz is meaningless for the moment cause anyway the dock starts without glitz.
Use --glitz to activate glitz at run-time.
Tape cairo-dock --help to see the available options.

@LLR650 : which version of cairo-dock are you running ? currently, it's the 1.3.3.

---

### Post by Fejker on 2007-09-19
fabounet: I'm running Ubuntu Feisty.

```
fejker@fejker-laptop:~$ uname -a
Linux fejker-laptop 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux
```

I clicked on "Fix Broken Packages" in Synaptic and nothing happened. I desperately tried:

```
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

I still get the same error.

---

### Post by drawrof on 2007-09-22
i'm having a problem with the .desktop files; they work good for standard commands. but with wine, whenever there's a space to get in the execution, such as wine ..../Program Files/.... i cannot get it to be parsed after the space.

i've tried escaping it, linking it.

any workarounds?

---

### Post by yopnono on 2007-09-22
Try AWN instead.
[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum)

---

### Post by Fejker on 2007-09-22
I didn't like AWN that much, that's why I tried installing Gnome Dock and Kiba-Dock.
I like Kiba-Dock so far, but want to try Gnome dock, because it looks clean.

---

### Post by yopnono on 2007-09-22
> **Fejker said:**
> I didn't like AWN that much, that's why I tried installing Gnome Dock and Kiba-Dock.
I like Kiba-Dock so far, but want to try Gnome dock, because it looks clean.

kika I don't its bloated awn clean. May I ask why you don't like the awn?
I think it's clean.

---

### Post by Fejker on 2007-09-22
AWN kept crashing, the launcher for Evolution with the kdocker command ceased to work every time I tried to reopen it. Kiba-dock is far from perfect and also crashes from time to time, but I still prefer it over AWN.

---

### Post by yopnono on 2007-09-22
ok, sorry to hear.

---

### Post by Fejker on 2007-09-22
OK, I finally got over the dependency issue (sorted it out with clearing all the cache from apt-get, then ran aptitude and updated + installed some of the packages manually).
Now I configured and compiled cairo-dock and when I run it shows up with only the DC++ icon showing (I don't even have DC++ installed) and when I move my mouse over the bar it slides down and there's no way of getting it back.

I'm running Beryl on Feisty. Tried it with Compiz too and it's the same. The strange thing is that the bar works if I turn the composite manager off, but has an annoying black rectangle around it (as described in a post at the beginning of this thread).

I also tried setting the vertical virtual Size to the value of 2 in Beryl settings with no luck.

---

### Post by cdburgess75 on 2007-09-23
I followed the tutorial to a T. (tongue twister)  the dock came up on the bottom but I could not get to it....It would keep running away from mi mice.

:guitar:

---

### Post by fabounet on 2007-09-23
Hello.
Did you try with another theme ?
what do you mean by "slide" ? when you enter into the dock, it starts hiding ? maybe you can try to remove auto-hide. Also you can try to move it from the screen border, or to change it's position (vertical, up, etc).
There is no reason it doesn't work fr you :-)

---

### Post by JBAlaska on 2007-10-01
I read this whole thread looking for help for another user. I just thought I'd mention that the original Cairo-Dock has come a long way.

As of version 1.3.4;
No more having to compile, just install the .deb
Full english config screens (prior versions were in french)
Very stable on my Feisty Box
Built in update funtion (with 2 updates in the last 3 weeks)
No longer takes up the whole width of screen real estate

I'm currently running Cairo-Dock on top and the latest Awn on bottom and they both are great!

Get Cairo-Dock 1.3.4 [Here](http://developer.berlios.de/project/showfiles.php?group_id=8724)

---

### Post by tturrisi on 2007-10-01
as of today it's version:
  1.3.5	2007-10-01 00:00
    cairo-dock_1.3.5-beta_i686-32bits.deb	1243654 	0 	i386	.deb
    cairo-dock-plug-ins_1.3.5-beta_i686-32bits.deb	481004 	0 	i386	.deb
    cairo-dock-sources-20071001.tar.bz2	10098198 	0 	i386	.bz2
    md5sum.txt

---

### Post by rabbitnightmare on 2007-10-01
I followed the instructions to the T...
without make anything it will start with a black bar at the bottom and one icon so I reinstalled it...
I did make clean it did this:
rm -f *.o *~ cairo-dock
then I did make:
cc `pkg-config --cflags cairo gtk+-2.0 librsvg-2.0 glitz-glx` -DHAVE_GLITZ  `pkg-config --libs   cairo gtk+-2.0 librsvg-2.0 glitz-glx` -lm  cairo-dock.c   -o cairo-dock
cairo-dock.c:52:25: error: cairo-glitz.h: No such file or directory
cairo-dock.c: In function ‘dock_cairo_create’:
cairo-dock.c:189: warning: assignment makes pointer from integer without a cast
and it wont let me run it anymore what did I do wrong?:confused:

---

### Post by izzojova on 2007-10-02
Can someone explain how to install this application.  Ive gone through the step at the beginning but its says i dont have permission to enter the folder.  I was reading the most recent post and they are saying things have change from the original.  Its kind of hard to follow the constant changes.  Im a newbie have Feisty Fawn with compiz fusion emerald and downloaded the 1,34 version.  Again a series of simple steps on how to install would be greatful.

---

### Post by tturrisi on 2007-10-02
> **izzojova said:**
> Can someone explain how to install this application.  Ive gone through the step at the beginning but its says i dont have permission to enter the folder.  I was reading the most recent post and they are saying things have change from the original.  Its kind of hard to follow the constant changes.  Im a newbie have Feisty Fawn with compiz fusion emerald and downloaded the 1,34 version.  Again a series of simple steps on how to install would be greatful.

Download the .debs here:
[http://developer.berlios.de/projects/cairo-dock/](http://developer.berlios.de/projects/cairo-dock/)

Install w/ gdebi package installer.

Open a terminal and type:
cairo-dock

---

### Post by RavanH on 2007-10-02
Anybody know if this works on Gutsy AMD64?

---

### Post by NumberOne on 2007-10-03
I just installed the latest version 1.3.5, and all the config menus are in French.  Where can I get the English version, or is there a way to convert the exixting install to English??

Thanks,
T.

---

### Post by JBAlaska on 2007-10-04
Change the language here:
[IMG]http://img230.imageshack.us/img230/7218/cairodockenglishxx1.png[/IMG]

---

### Post by spockrock on 2007-10-05
wow I am trying gnome dock, its improved drastically, I wish however we could edit the task list lets you change the icons.

---

### Post by RavanH on 2007-10-05
Tried this on Gutsy AMD 64, but get VERY weird results... :(

---

### Post by hagarid on 2007-10-05
none of this worked for me the commands came back with  "Could not get" or " Unable to lock the administration directory" or best of all need administrator rights Since I am new at this I can't fix it or even figure out what is going on or how to fix it. thanks

---

### Post by ppmt on 2007-10-07
Hi,

Just thought I would say that there is a wiki in english for Cairo-Dock if you are interrested.

[http://help.ubuntu.com/community/CairoDock](http://help.ubuntu.com/community/CairoDock)

---

### Post by merlwiz79 on 2007-10-13
I have made a .deb of cairo 1.4.10(works in Gutsy and Feisty):
[http://rapidshare.com/files/62394424/cairo_1.4.10-2_all.deb.html](http://rapidshare.com/files/62394424/cairo_1.4.10-2_all.deb.html)
You can get the rest of the .debs here:
[https://developer.berlios.de/projects/cairo-dock/](https://developer.berlios.de/projects/cairo-dock/)
I have also made a Dock theme for Linux Mint.

---

### Post by RavanH on 2007-10-14
> **merlwiz79 said:**
> I have made a .deb of cairo 1.4.10(works in Gutsy and Feisty):
[http://rapidshare.com/files/62394424/cairo_1.4.10-2_all.deb.html](http://rapidshare.com/files/62394424/cairo_1.4.10-2_all.deb.html)
You can get the rest of the .debs here:
[https://developer.berlios.de/projects/cairo-dock/](https://developer.berlios.de/projects/cairo-dock/)
I have also made a Dock theme for Linux Mint.

OK, I have installed your cairo deb and also installed version cairo-dock_1.2.11_all.deb along with the plugins deb but I get the following error when entering cairo-dock in terminal:
```
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory
```
Any thoughts or suggestions? Compiling newer versions from source doesn't work for some reason and breaks off with errors too :(

---

### Post by RavanH on 2007-10-16
> **ppmt said:**
> Hi,

Just thought I would say that there is a wiki in english for Cairo-Dock if you are interrested.

[http://help.ubuntu.com/community/CairoDock](http://help.ubuntu.com/community/CairoDock)

What I did was follow the instructions there to the letter (installing all packages needed and using the latest cairo-dock-sources-20071001.tar.bz2) but that resulted in the following error:
```
$ autoreconf -isvf && ./configure --prefix=/usr && make
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal --force
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf --force
configure.ac:10: error: possibly undefined macro: AC_PROG_LIBTOOL
If this token and others are legitimate, please use m4_pattern_allow.
See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1
```
Anybody know what's wrong here?

--ravan

---

### Post by agarralo on 2007-10-17
hey i finished al the steps .. to use de  dock .. until  i got to the install step when i extrart  the tar file i must do ti on the /opt   right..?

so i did .

but  at the time to open de dock i imputed  this ./cairo-dock --no-glitz
 but  nothing  hapened . well it told me that it was not  a folder 
well i dont really know wath the problem is . but

 the cairo 1.2.6 and cairo-dock are installed 

some help please .!!

pd soorry  for my english

---

### Post by agarralo on 2007-10-17
hey i finished al the steps .. to use de dock .. until i got to the install step when i extrart the tar file i must do ti on the /opt right..?

so i did .

but at the time to open de dock i imputed this ./cairo-dock --no-glitz
but nothing hapened . well it told me that it was not a folder
well i dont really know wath the problem is . but

the cairo 1.2.6 and cairo-dock are installed

some help please .!!

pd soorry for my english

---

### Post by jobbesat on 2007-10-19
Did you try to give simply the command
cairo-dock
or
cairo-dock --no-glitz

---

### Post by AndyLovesLinux on 2007-10-23
do i need beryl installed to use the dock?!?

---

### Post by timmyw29 on 2007-10-24
Well I've got Cairo-Dock installed now, running quite nicely too, I might add. The only thing I want to change about it now is the fact that it cuts the edges off launcher/application names... I always want to see the entire label.

Any ideas? Did I miss a setting somewhere?

---

### Post by mikeym on 2007-11-10
Hi,

I've just spent the day trying to familiarise myself with the code for cairo dock as I want to make a few patches and additions to my version. I'm not a great programmer in C++ and I'm essentially new to programming for linux but I'm sure if I stick at it I'll get there in the end. 

What I was wondering was if someone who is familiar with how cairo works could advise me on how to go about implementing the first change I wanted to add which was to hide cairo dock when a fullscreen application is on top of it. 

I can find out if a full screen app is open but I can't tell were it is also I can't work out how the drawing process for cairo is carried out or how the flow of control works around the program.

---

### Post by RavanH on 2007-11-11
> **mikeym said:**
> Hi,

I've just spent the day trying to familiarise myself with the code for cairo dock as I want to make a few patches and additions to my version. I'm not a great programmer in C++ and I'm essentially new to programming for linux but I'm sure if I stick at it I'll get there in the end. 

What I was wondering was if someone who is familiar with how cairo works could advise me on how to go about implementing the first change I wanted to add which was to hide cairo dock when a fullscreen application is on top of it. 

I can find out if a full screen app is open but I can't tell were it is also I can't work out how the drawing process for cairo is carried out or how the flow of control works around the program.

Did you contact Fabrice, the project admin on [http://developer.berlios.de/projects/cairo-dock](http://developer.berlios.de/projects/cairo-dock) already?

---

### Post by scaine on 2007-11-12
Is anyone running this in 32bit Gutsy?

From [this thread]("http://ubuntuforums.org/showthread.php?p=3756045&posted=1#post3756045"), I get the following issue when I run the Cairo-dock command (with or without --no-glitz).

cd_rhythmbox_pre_init ()
rhythmbox_dbus_init ()
Connexion au bus ... réussie
Segmentation fault (core dumped)

I downloaded the deb files from here - [http://developer.berlios.de/projects/cairo-dock/]("http://developer.berlios.de/projects/cairo-dock/") with the current version being 1.4.0.

Any ideas would be greatly appreciated.

---

### Post by JBAlaska on 2007-11-12
I just posted this in another thread;
> I had the same problem when I put the latest (v 1.40) cairo-dock on my new (used) laptop.

I ended up digging through the French forum and from what I could make of their ruddy gibberish J/K, It seems to be a problem with a cd control applet conflict.

I was able to fix it by uninstalling 1.40 and using version 1.35 with 1.35 plugins, then I used the update feature in cairo-dock to get the newest version.

Worked fine this way, Here's the older version d/l page;
Code:

[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)



**btw: the deb's are much easer to install for most folks.**

---

### Post by jfal on 2007-11-12
> **JBAlaska said:**
> I just posted this in another thread;


**btw: the deb's are much easer to install for most folks.**


I tried installing the latest version, but kept getting a seg. fault.  I followed the above instructions and got it working perfectly.  Thanks.

---

### Post by skiwithpete on 2007-12-01
I'm using the dock, but having problems with loads of simple stuff.

Like how do I add a separator?  Let alone a custom one, that has a smaller width...

I can't figure out the menus either. Like configure all, appearance, behavior.  Objectdock for windows, and Rocketdock, both make this whole configuration thing much simpler.

Anyways, I love it, and I will keep using it, I'm just looking forward to the improvements.  

I need to learn to code.

P

---

### Post by mainnetwork on 2008-01-24
Im new to this, and ive had no trouble except extracting to /opt.
How do i do it? Im no root user so ill need a bit of help on this :(

---

### Post by RavanH on 2008-01-24
> **mainnetwork said:**
> Im new to this, and ive had no trouble except extracting to /opt.
How do i do it? Im no root user so ill need a bit of help on this :(

Go to the actively developed successor of Gnome Dock called Cairo Dock on [http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724) download the latest version 1.4.6.3 (two deb files - both the dock and plugins) and just install them. Easy! :)

If - by any chance - you are using an AMD64 install read my how-to _[Cairo Dock on AMD64]("http://ubuntuforums.org/showthread.php?p=3771459")_.

---

### Post by mainnetwork on 2008-01-24
> **RavanH said:**
> Go to the actively developed successor of Gnome Dock called Cairo Dock on [http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724) download the latest version 1.4.6.3 (two deb files - both the dock and plugins) and just install them. Easy! :)

If - by any chance - you are using an AMD64 install read my how-to _[Cairo Dock on AMD64]("http://ubuntuforums.org/showthread.php?p=3771459")_.

Thanks mate, if i knew how to thank you i would. ;)

---

### Post by anonymous_user on 2008-02-08
How do I move icons across separators and how do I change a launcher's icon?

---

### Post by raoulteeuwen on 2008-02-25
Hi all. I'm no expert on Linux. Got Compiz running tonight and tried Cairo (the new one). Clicked on both the deb-files, bot installed, but than what? I don't see the dock appearing. And nothing in /opt : it seems the files get extracted in Usr/Share/Cairo-dock ... Do i need to go into that map as root and execute some make command? (sorry for asking, have already been searching for a long time, couldn't find the answer).

---

### Post by RavanH on 2008-02-26
> **raoulteeuwen said:**
> Hi all. I'm no expert on Linux. Got Compiz running tonight and tried Cairo (the new one). Clicked on both the deb-files, bot installed, but than what? I don't see the dock appearing. And nothing in /opt : it seems the files get extracted in Usr/Share/Cairo-dock ... Do i need to go into that map as root and execute some make command? (sorry for asking, have already been searching for a long time, couldn't find the answer).

What happens if you pen a terminal window and give the command ```
cairo-dock
``` 

If you get an error, the dock is not installed (properly) but if all is well, you should get the first time theme dialog... 

After setting up cairo-dock like you want it to look, you can either save your session (if you are used to do that) or add it (the command cairo-dock) to your session startup list to make it start upon each login :)

---

### Post by raoulteeuwen on 2008-02-26
Thanks: i opened a terminal, typed cairo-dock and the dock opened.

A question though: i wanted to close the terminal, but then the dock disappeared. Do i need to minimize the terminal session?

And during a couple of minutes of me playing around with the (great looking) dock, the terminal window filled with lots of error-looking messages: is this normal? (i thought of copying those here, but the look as if they might contain private info (maybe url's to my inbox etc). But parts i think are save:

"gtk_widget_size_allocate(): attempt to allocate widget with width -2 and height 71" (immediately after starting the dock the 1st time)

and (after restaring the dock after me typing CTRL-C):

"NewStream: The full URL is [http://www.worldtimeserver.com/clocks/wtsclockgg2.swf?color=FF0000&wtsid=NL](http://www.worldtimeserver.com/clocks/wtsclockgg2.swf?color=FF0000&wtsid=NL)
Closed 55files.
Starting process: /usr/bin/gtk-gnash -v -x 58721326 -j 140 -k 140 -u [http://www.worldtimeserver.com/clocks/wtsclockgg2.swf?color=FF0000&wtsid=NL](http://www.worldtimeserver.com/clocks/wtsclockgg2.swf?color=FF0000&wtsid=NL) -U [http://97.gmodules.com/ig/ifr?url=http://www.worldtimeserver.com/clocks/wtsclockgg1.xml&nocache=0&up_wtssize=140&upt_wtssize=enum&up_wtsid1=NL&upt_wtsid1=enum&up_wtsid1label=Amsterdam&up_wtsid1color=FF0000&upt_wtsid1color=enum&up_wtsid1type=2&upt_wtsid1type=enum&up_wtsid2=US-NY&upt_wtsid2=enum&up_wtsid2label=New+York&up_wtsid2color=FFCC33&upt_wtsid2color=enum&up_wtsid2type=2&upt_wtsid2type=enum&lang=nl&country=nl&.lang=nl&.country=nl&synd=ig&mid=97&ifpctok=-14173116144241559&parent=http://www.google.nl&extern_js=/extern_js/f/CgJlbhICdXMrMAo4ACwrMBA4ACwrMBI4ACwrMBM4ACwrMBU4ACw/uTrgrCgC9OA.js](http://97.gmodules.com/ig/ifr?url=http://www.worldtimeserver.com/clocks/wtsclockgg1.xml&nocache=0&up_wtssize=140&upt_wtssize=enum&up_wtsid1=NL&upt_wtsid1=enum&up_wtsid1label=Amsterdam&up_wtsid1color=FF0000&upt_wtsid1color=enum&up_wtsid1type=2&upt_wtsid1type=enum&up_wtsid2=US-NY&upt_wtsid2=enum&up_wtsid2label=New+York&up_wtsid2color=FFCC33&upt_wtsid2color=enum&up_wtsid2type=2&upt_wtsid2type=enum&lang=nl&country=nl&.lang=nl&.country=nl&synd=ig&mid=97&ifpctok=-14173116144241559&parent=http://www.google.nl&extern_js=/extern_js/f/CgJlbhICdXMrMAo4ACwrMBA4ACwrMBI4ACwrMBM4ACwrMBU4ACw/uTrgrCgC9OA.js) -P base=http://www.worldtimeserver.com/clocks/ -P flashvars=__module_id__=97&up_.lang=nl&up_.country=nl&up_wtssize=140&up_wtsid1=NL&up_wtsid1label=Amsterdam&up_wtsid1color=FF0000&up_wtsid1type=2&up_wtsid2=US-NY&up_wtsid2label=New%20York&up_wtsid2color=FFCC33&up_wtsid2type=2&up_synd=ig -P height=140 -P id=flashid1 -P src=http://www.worldtimeserver.com/clocks/wtsclockgg2.swf?color=FF0000&wtsid=NL -P type=application/x-shockwave-flash -P width=140 -P wmode=opaque - 
Forked sucessfully, child process PID is 7151"

---

### Post by Flynn555 on 2008-02-28
having trouble installing cairo...

/cairo-type1-subset.o
cairo-type1-subset.c: In function 'cairo_type1_font_subset_decrypt_eexec_segment':
cairo-type1-subset.c:368: error: implicit declaration of function 'isspace'
make[3]: *** [cairo-type1-subset.lo] Error 1
make[3]: Leaving directory `/home/chad/cairo-1.2.6/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/chad/cairo-1.2.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/chad/cairo-1.2.6'
make: *** [all] Error 2

this occurs when i do 'make'

---

### Post by Flynn555 on 2008-02-28
ok nevermind i got it working...
gorgeous dock! love it! so much better than awn (imo)

i do have a few questions though...

1. whenever i run cairo dock in terminal "cairo-dock" i cant close the terminal without cairo closing as well.  is there a script or something im suposed to be using instead of typing the cairo-dock command in term??

2. if i select cairo dock to appear on the left hand side of the screen...it doesn't stay centered.  unless im hovering over it the dock sticks to the top of the screen.

any thoughts on what could be causing these two probs???

oh and does anyone know how i can add a recycle bin to the dock?

[I]
edit: solved the first problem(just added the command to the startup command list so terminal is never opened)[/I]

---

### Post by raoulteeuwen on 2008-02-29
Great you solved nr 1: just for others: see [https://help.ubuntu.com/community/AddingProgramToSessionStartup](https://help.ubuntu.com/community/AddingProgramToSessionStartup) how to auto startup programs during ubuntu boot

---

### Post by Neo4 on 2008-03-03
I have some problems in my cairo dock! 
1-If I try to remove the shortcuts icon cairo-dock will close!
2- If I open the calender under the clock I can't close it and the same for the terminal

anyone can help?

Thanks

---

### Post by RavanH on 2008-03-04
> **Neo4 said:**
> I have some problems in my cairo dock! 
1-If I try to remove the shortcuts icon cairo-dock will close!
There are two different methodes of removing an applet/module: 1. by right clicking the icon and selecting the 'remove this module' option (you probably tried this one and it failed?); 2. right-click anywhere on the dock and select 'Cairo Dock > Configure' and open the System tab (or the Applets tab if it shows) and uncheck under Applets the module you do not want anymore...
I had the same problem with the systray icon. It turned out that methode number 2 worked on the previous version but on the latest both options failed. After changing some config options of that applet and using it a few times, I finally could remove the icon... Strange, èh? 

> **Neo4 said:**
> 2- If I open the calender under the clock I can't close it and the same for the terminal
What do you mean? Can you explain more?

---

### Post by Neo4 on 2008-03-04
> **RavanH said:**
> There are two different methodes of removing an applet/module: 1. by right clicking the icon and selecting the 'remove this module' option (you probably tried this one and it failed?); 2. right-click anywhere on the dock and select 'Cairo Dock > Configure' and open the System tab (or the Applets tab if it shows) and uncheck under Applets the module you do not want anymore...
I had the same problem with the systray icon. It turned out that methode number 2 worked on the previous version but on the latest both options failed. After changing some config options of that applet and using it a few times, I finally could remove the icon... Strange, èh? 


What do you mean? Can you explain more?

none of the options work, that's what i've already tried and result on cairo-dock to close!

the second question i've already find the anwser is by clicking on the middle mouse button.

Anyway I don't like this bar, i prefer AWN.
the open windows if minimized with transparency, the lancher that opens a app like firefox don't stay on the launcher creates a new icon on the open apps.. I just don't like it!

---

### Post by boob11 on 2008-03-09
Thanks

---

### Post by puccaso on 2008-03-09
can someone make a deb of this and post it please..

im using an eee pc with 2g harddrive, idonthave space to compile.


thanks

---

### Post by pingpongboss on 2008-03-12
> **puccaso said:**
> can someone make a deb of this and post it please..

im using an eee pc with 2g harddrive, idonthave space to compile.


thanks

As far as I know, the official DEBs that you are looking for are here: [http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)

---

### Post by vicky98284 on 2008-03-18
i tried installing cairo-dock the way described above. but when i run make or make install command it saying -no make file found,no rule to make target..i was cd into opt/cairo-dock as mentioned. this is the text displayed in terminal. plz help 



tarun@tarun-laptop:/opt/cairo-dock$ make install
make: *** No rule to make target `install'.  Stop.
tarun@tarun-laptop:/opt/cairo-dock$

---

### Post by mitchellthegreat on 2008-03-18
I've never used this thing befor, nor have I heard of it, but what I would do if I were having any problems, redownload the .deb file, uninstall the package, then reinstall using the new .deb and see what happens. Whenever I have problems, that's what I do and they're usually fixed.

---

### Post by RavanH on 2008-03-18
> **vicky98284 said:**
> i tried installing cairo-dock the way described above. but when i run make or make install command it saying -no make file found,no rule to make target..i was cd into opt/cairo-dock as mentioned. this is the text displayed in terminal. plz help 

tarun@tarun-laptop:/opt/cairo-dock$ make install
make: *** No rule to make target `install'.  Stop.
tarun@tarun-laptop:/opt/cairo-dock$
Why would you be doing any 'make & make install' ? Are you not using Ubuntu/debian based Linux? If you have Ubuntu/Debian flavour, just run the two deb files and both the dock and the plugins will install themselves. 

Start the dock with command cairo-dock and see if it works...

---

### Post by kk0sse54 on 2008-03-22
I downloaded all the packages and i downloaded  Cairo 1.2.6 but when i try to install it and type in  the code it says:
jars@jars-desktop:~$ ./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc
bash: ./configure: No such file or directory

kinda new to all this and i liked the look of the cairo dock so can anyone help?

---

### Post by RavanH on 2008-03-23
> **C!oud said:**
> I downloaded all the packages and i downloaded  Cairo 1.2.6 but when i try to install it and type in  the code it says:
jars@jars-desktop:~$ ./configure --enable-warnings --enable-glitz --disable-quartz --disable-atsui --disable-xcb --disable-win32 --disable-gtk-doc
bash: ./configure: No such file or directory

kinda new to all this and i liked the look of the cairo dock so can anyone help?

Install Cairo libraries using Synaptic (or apt-get command line), download the latest cairo dock precompiled .DEB files (two of them) and dubble click them to install... 

Should not be too complicated :)

Or are you on 64bit? If so, see my How-to in my signature...

---

### Post by RavanH on 2008-03-23
Try just installing these:
[http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.5.3.2_i686-32bits.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.5.3.2_i686-32bits.deb)
and
[http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.3.2_i686-32bits.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.3.2_i686-32bits.deb)

IF dependencies are not solved automatically, then try to do them manually...

---

### Post by kk0sse54 on 2008-03-23
thanks for the help but i got it to work. don't really know what i did but it works fine for me and i love it.

---

### Post by MichaelSM on 2008-03-27
I was delighted with cairo-dock until something went wrong. I didn't notice much at the time(screen resolution?) but now I start cairo-dock and it all looks good as in white box top left of screen, followed by cairo-dock starting at the bottom as in white bar, then it disappears.

If I start it in Terminal I get this:

michael@michael-desktop:~$ cairo-dock

cairo_dock_get_window_geometry () -> 1;24 317x629 / 0,24
cairo_dock_get_window_geometry () -> 1;24 1278x869 / 0,24
cairo_dock_get_window_geometry () -> 1;24 737x433 / 0,32
cairo-dock: symbol lookup error: cairo-dock: undefined symbol: g_once_init_enter_impl

Gotta be easy. The thing worked like a wet dream for months.

Any advice appreciated.

Thank you,

Mike.

PS. Running xcompmgr as compositor. Nvidia 5500 etc. 

The brilliant dock just lost itself somewhere.

---

### Post by RavanH on 2008-03-27
> **MichaelSM said:**
> I was delighted with cairo-dock until something went wrong. I didn't notice much at the time(screen resolution?) but now I start cairo-dock and it all looks good as in white box top left of screen, followed by cairo-dock starting at the bottom as in white bar, then it disappears.

If I start it in Terminal I get this:

michael@michael-desktop:~$ cairo-dock

cairo_dock_get_window_geometry () -> 1;24 317x629 / 0,24
cairo_dock_get_window_geometry () -> 1;24 1278x869 / 0,24
cairo_dock_get_window_geometry () -> 1;24 737x433 / 0,32
cairo-dock: symbol lookup error: cairo-dock: undefined symbol: g_once_init_enter_impl

Gotta be easy. The thing worked like a wet dream for months.

Any advice appreciated.

Thank you,

Mike.

PS. Running xcompmgr as compositor. Nvidia 5500 etc. 

The brilliant dock just lost itself somewhere.

I have xcompmgr as compositor too, and Cairo Dock is running fine with it, both on Gnome and XFce... What version of cairo-dock do you have installed? What if you (re-)install the latest deb files? 

If you do not care about losing you last cairo-dock configuration (or if you saved it through the Theme Manager back when the dock was working) you might try to clear out all files in the .cairo-dock folder (except for the .cairo-dock/themes subfolder if you saved your setup) in you home directory. 

Does all that not do it for you? Try the cairo-dock developers help forum: [http://developer.berlios.de/forum/forum.php?forum_id=26288](http://developer.berlios.de/forum/forum.php?forum_id=26288)

Good luck :)

---

### Post by MichaelSM on 2008-03-27
RavanH.

Problem was with latest cairo-dock web upgrade. So I ran 'sudo apt-get remove cairo-dock*' then re-installed the earlier version which for me is cairo-dock 1.4.6.3.

All good again. It's the best dock of them all, and I tried every other mongrel when I  had no cairo-dock. Waste of time, all of them!

Cheers,

Mike

---

### Post by sc00ter on 2008-03-30
Hi, I've encountered exactly the same issue. I'm running Feisty 7.04.

I've reverted to version 1.5.2.1 which for now, works OK.

---

### Post by MichaelSM on 2008-03-31
Good reply, scOOter.

Upgrades are weird, as in why do nitwits like me upgrade something which works almost perfectly in its earlier version?

I don't mind at all the little flicker here or there, so long as the dock easily and intuitively does what suits ME.

As in a default line-up of basic launchers which can be altered if one doesn't like them.

A nice separator between launchers and working functions.

No need to sort out usage of the bottom 20mm of available screen, and a default transparency which is fine.

The ability for it to run perfectly with xcompmgr without Beryl or Compiz playing silly games.

End of rant.

Cheers,
MIke.

---

### Post by RavanH on 2008-03-31
> **MichaelSM said:**
> RavanH.

Problem was with latest cairo-dock web upgrade. So I ran 'sudo apt-get remove cairo-dock*' then re-installed the earlier version which for me is cairo-dock 1.4.6.3.

All good again. It's the best dock of them all, and I tried every other mongrel when I  had no cairo-dock. Waste of time, all of them!

Cheers,

Mike

> **sc00ter said:**
> Hi, I've encountered exactly the same issue. I'm running Feisty 7.04.

I've reverted to version 1.5.2.1 which for now, works OK.

Thanks, guys, for sharing your solution :) 

Would you mind taking the time to report the fact that the latest dock is failing you on the CD developers forum over at [http://developer.berlios.de/projects/cairo-dock](http://developer.berlios.de/projects/cairo-dock) ? TIA :)

---

### Post by RDL89 on 2008-05-10
> **RavanH said:**
> Try just installing these:
[http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.5.3.2_i686-32bits.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.5.3.2_i686-32bits.deb)
and
[http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.3.2_i686-32bits.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.3.2_i686-32bits.deb)

IF dependencies are not solved automatically, then try to do them manually...

Thanks, I finally got it to work following that suggestion.

---

### Post by KazukiFlame on 2008-05-14
for this cairo-dock, how do u set it to keep under windows like the screenlets? sometimes its annoying when it blocks the view of windows, but i don't want to set it to autohide.

---

### Post by RavanH on 2008-05-14
> **KazukiFlame said:**
> for this cairo-dock, how do u set it to keep under windows like the screenlets? sometimes its annoying when it blocks the view of windows, but i don't want to set it to autohide.

It is your window manager treating cairo-dock as a panel/dock so it will always be above other windows. To prevent this, try the start-up options **cairo-dock --toolbar-hint** or **cairo-dock --normal-hint** and see if any works for you...

---

### Post by KazukiFlame on 2008-05-15
worked like a charm, thanks

---

### Post by ash4ever on 2008-05-16
Hi guys,

I'm still considered a newbie, but do i have to have beryl instlled in order to make this app work?

---

### Post by RavanH on 2008-05-16
> **ash4ever said:**
> Hi guys,

I'm still considered a newbie, but do i have to have beryl instlled in order to make this app work?

If you mean by 'this app' the successor of Gnome Dock called [Cairo Dock]("http://developer.berlios.de/project/showfiles.php?group_id=8724"), then the answer is No. But you DO need some kind of compositor running for transparency to make the dock look like it is supposed to. Without transparency, the dock will work but will always have a black background (and not show either the desktop or any window underneath it) ...

There are several options available and it also depends on your Desktop Environment:
[LIST]
[*]If you are using **XFCE** (Xubuntu) you can use the internal compositor by activating it via Settings > Configuration Manager > Window Manager Tweaks. Click the tab Compositor and activate at least the first option 'Enable Compositing' for transparency to become available.

[*]When using **KDE** (Kubuntu) there seem to be similar options under System Settings -> Desktop -> Window Behavior -> Transparency.

[*]When on **GNOME** (Ubuntu) you will have to install a compositor but you can use xcompmgr if you do not like the extra system load like Beryl or (better) CompizFusion will bring. Do in terminal ```
sudo apt-get install xcompmgr
``` and add a new start-up option in your Sessions list named (for example) Shading and Transparency with the command **xcompmgr -c -f -n** so it will load on every login.
[/LIST]
Hope this helps :)

---

