---
title: "HOWTO: Successfully run gDesklets"
date: 2005-05-05
forum: Outdated Tutorials &amp; Tips
---

### Post by derrick1985 on 2005-05-05
gDesklets is a nice little program where you can add "desklets" to your desktop that control different programs/show different stats. You can use it to replace your Gnome panels, or maybe add some guages to show your CPU/Mem usage, the choices are yours.

So, to begin, here is what your need to do:

**1. Installing gDesklets using APT** 

Installing gDesklets is fairly easy. First, you need to add the universe/multiverse repositories. You can find out how to do that at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) under [Howto add extra repositories](http://www.ubuntuguide.org/#extrarepositories) Once done, open up a terminal and type
```
sudo apt-get install gdesklets (notice all the small letters)
```

You now have gdesklets installed. For anyone who is going to try this through Synaptic, you will have two gdesklets search results: gdesklets and gdesklets-data. DO NOT INSTALL GDESKLETS DATA! the files are out of date, and won't work right with gdesklets.

**2. Setting up your desklets** 

Now the fun part, we get to set up our desklets! First, lets test and see if gDesklets is installed and working correctly. Goto your gnome panel Accessories---gDesklets. It should now open up in a window. Goto Profiles---New Profile. Call this profile default.

**3. Getting and installing desklets** 

Getting and installing desklets is probably the easiest part of this entire HOWTO. Here is what you do: Open up a browser and goto [http://gdesklets.gnomedesktop.org/categories.php](http://gdesklets.gnomedesktop.org/categories.php)

This is their Displays&Sensors page, here is where you can get your applets. Scroll around through the different categories and find a few that you like. Save them to your home directory (I'm using /home/myusername/gdesklets to store them)

Now, time to install them. LEAVE THEM IN THEIR FORMAT, do not extract them. Go back to your gDesklets window and go File---Install Package. Select the desklet that you want to install (one at a time) and it will appear in the right hand window. Double click on it and add it to your desktop. To configre your desklet, right click and select Configure, enter in your options.

Congratulations, you now have your desklets installed.

**4. Getting gDesklets to start on log in** 

Now, wouldn't it be nice if this all happened for you right on statup of your system? Well, it can. Goto your Gnome panel and select System---Preferences---Sessions. 
Goto the Startup Programs tab and select Add. Fill in with this information:

Startup Command: gdesklets
Order: 50
Ok

That's it. Enjoy.

---

### Post by derrick1985 on 2005-05-05
Here is a sample picture showing my desktop with gDesklets:

---

### Post by bored2k on 2005-05-05
[http://www.lynucs.org/?gdesklets](http://www.lynucs.org/?gdesklets) < These will make anyone want them

Flawless guide by the way.

---

### Post by Rodrigo on 2005-05-05
thanks for the How to, I didnt know where to start :p

---

### Post by N'Jal on 2005-05-05
I feel special i worked it out myself. :D I'm getting there. This is how i did it, though i DIDN'T know about the no data package bit that made my desklets look ugly in warty. Well i know that bit for future. So thank you for that.

---

### Post by risager on 2005-05-05
Beautiful. Nice howto. It was so annoying with all that broken stuff in gdesklets-data. 

Could someone please explain how you use these in your daily routines. My problem is that I want to use these because they seem so beautiful and potentially useful, but usually my current application fill the whole screen except a gnome bar at the top and the buttom of my screen (I'm on a 15 inch laptop). So if I use e.g starter-bar which looks so cool, it usually slows me down that I have to minimize or move a window to get to start another application. (The Mac OSX guys should have the same problem) Don't you use maximized windows? Is gdesklets only relevant to people with +17inch screens?

---

### Post by derrick1985 on 2005-05-05
[QUOTE=risager]Beautiful. Nice howto. It was so annoying with all that broken stuff in gdesklets-data. 

Could someone please explain how you use these in your daily routines. My problem is that I want to use these because they seem so beautiful and potentially useful, but usually my current application fill the whole screen except a gnome bar at the top and the buttom of my screen (I'm on a 15 inch laptop). So if I use e.g starter-bar which looks so cool, it usually slows me down that I have to minimize or move a window to get to start another application. (The Mac OSX guys should have the same problem) Don't you use maximized windows? Is gdesklets only relevant to people with +17inch screens?[/QUOTE]


Hmmm... What resolution do you have your screen set to? And, if your laptop is powered by, lets say an ATI Radeon mobile, or nVidia card, do you have their drivers installed?

---

### Post by risager on 2005-05-05
[QUOTE=derrick1985]Hmmm... What resolution do you have your screen set to? And, if your laptop is powered by, lets say an ATI Radeon mobile, or nVidia card, do you have their drivers installed?[/QUOTE]

I have a nVidia GeForce FX5200 with drivers installed and running 1280x800.

---

### Post by Heliode on 2005-05-05
[QUOTE=risager]I have a nVidia GeForce FX5200 with drivers installed and running 1280x800.[/QUOTE]

Well, I think you can compare it to the Dashboard feature in Apple's OSX Tiger. When you minimize your windows, you get a bunch of sensors so you can track things like the weather, ethernet up/down, processor load, etc. 

Thanks a lot for this howto! I used gDesklets a lot in Warty, and was quite pissed off when it didn't work properly in Hoary. Why is the gdesklets-data package still in there, anyway?

---

### Post by AndyAWS on 2005-05-05
Ok, it seems to have worked but the Temp Display I'm trying to run needs 'LTVBorder'.
Where do i get that? It was part of the Data file before, I believe.

---

### Post by derrick1985 on 2005-05-06
[QUOTE=risager]I have a nVidia GeForce FX5200 with drivers installed and running 1280x800.[/QUOTE]

Well, the only thing I can suggest you try and do is add to your top gnome bar, the Window Selector panel, remove the one you have on the bottom, and run your programs not maximized, but with a little bit of room left at the bottom so you can see your starter-bar.

---

### Post by pjack76 on 2005-05-06
[QUOTE=risager]
Could someone please explain how you use these in your daily routines. My problem is that I want to use these because they seem so beautiful and potentially useful, but usually my current application fill the whole screen except a gnome bar at the top and the buttom of my screen (I'm on a 15 inch laptop). So if I use e.g starter-bar which looks so cool, it usually slows me down that I have to minimize or move a window to get to start another application. (The Mac OSX guys should have the same problem) Don't you use maximized windows? Is gdesklets only relevant to people with +17inch screens?[/QUOTE]

If you have so many windows open that your Desktop isn't visible -- or if you maximize everything you use -- then gDesklets can still be useful if you use GNOME's "Show Desktop" feature. Press CTRL-ALT-D, and all of your windows will be minimized and you can see the desklets on your desktop. Press CTRL-ALT-D again, and your windows will go back to where they were.

In this manner, you can have gDesklets act like OS X's Dashboard feature.

---

### Post by thecrimsonking on 2005-05-06
How is gDesklets different or better than SuperKaramba?

Looks like they both do the same things to me.

---

### Post by p0rnflake on 2005-05-06
Excellent guide - was up and running in a minutte :D

---

### Post by N'Jal on 2005-05-07
> Could someone please explain how you use these in your daily routines. My problem is that I want to use these because they seem so beautiful and potentially useful, but usually my current application fill the whole screen except a gnome bar at the top and the buttom of my screen (I'm on a 15 inch laptop). So if I use e.g starter-bar which looks so cool, it usually slows me down that I have to minimize or move a window to get to start another application. (The Mac OSX guys should have the same problem) Don't you use maximized windows? Is gdesklets only relevant to people with +17inch screens?

I use a 14" CRT monitor with an integrated Intel graphics chip and it's fine for me. I have windows always maximised on the basis that if i am writing this i really cannot try launching another program unless i have preprogrammed anothre program to launch with a F# key

---

### Post by jonny on 2005-05-07
Fabulous.  I was completely ignorant about this app - and I've been missing out far too long.

---

### Post by derrick1985 on 2005-05-07
[QUOTE=jonny]Fabulous.  I was completely ignorant about this app - and I've been missing out far too long.[/QUOTE]

Glad you are enjoying it!

Hope you post a screenshot of your desktop.

---

### Post by AndEat on 2005-05-08
This seems simple enough, but when I try to use installed desklets for monitoring disk, cpu, network, etc. I get an error message stating this or that sensor is not available. I am assuming my hardware doesn't support these functions, but I'm going to post here for advice and reinstall the the program. 

I'm running an Inspiron 5100 that is not a total museum piece. I know I don't have cpu temp monitoring capacity from previous experience, so there is no surprise in being unable to access hardware info.

---

### Post by Xian on 2005-05-08
[QUOTE=AndEat]This seems simple enough, but when I try to use installed desklets for monitoring disk, cpu, network, etc. I get an error message stating this or that sensor is not available. I am assuming my hardware doesn't support these functions, but I'm going to post here for advice and reinstall the the program. [/QUOTE]
You might want to post links for the sensors you are having problems with so others can attempt to run them on their system. It just makes it easier to diagnose a problem if you can duplicate it elsewhere.

---

### Post by Rhodan on 2005-05-09
[QUOTE=derrick1985]
That's it. Enjoy.[/QUOTE]

Excellent howto, it's about time someone did a good job like this. Thanks very much !

---

### Post by raven on 2005-05-09
Thank you, it was very easy to follow, 
but how can I make the background of the sensors
be transparent, when I look at the pictures,
in the folders of each gdesklets it is transparent
ex: "gfx/bg.png" but I get a black background
any Help ???

---

### Post by risager on 2005-05-09
[QUOTE=raven]Thank you, it was very easy to follow, 
but how can I make the background of the sensors
be transparent, when I look at the pictures,
in the folders of each gdesklets it is transparent
ex: "gfx/bg.png" but I get a black background
any Help ???[/QUOTE]

Right-click on the gdesklets icon in the taskbar. Click Configuration. In the Xcomposite  support section see if Translucency is checked. If it is try unchecking it and restart gdesklets

---

### Post by derrick1985 on 2005-05-10
[QUOTE=raven]Thank you, it was very easy to follow, 
but how can I make the background of the sensors
be transparent, when I look at the pictures,
in the folders of each gdesklets it is transparent
ex: "gfx/bg.png" but I get a black background
any Help ???[/QUOTE]

ANd if that doesn't work:

Open up the gimp and make a new image. Select it's background as transparent. Save it and use it.

---

### Post by raven on 2005-05-10
[QUOTE=risager]Right-click on the gdesklets icon in the taskbar. Click Configuration. In the Xcomposite  support section see if Translucency is checked. If it is try unchecking it and restart gdesklets[/QUOTE]

Thanx that worked perfectly.

---

### Post by Zelut on 2005-05-10
I got gdesklets installed in my Applications menu but when I load it I only see a blank window with no options for creating a profile.  Any ideas?

I can't seem to upload a screenshot via the forum so check it out here...

[http://www.christeredwards.com/test/Screenshot.png](http://www.christeredwards.com/test/Screenshot.png)

---

### Post by derrick1985 on 2005-05-11
[QUOTE=kuyaedz]I got gdesklets installed in my Applications menu but when I load it I only see a blank window with no options for creating a profile.  Any ideas?

I can't seem to upload a screenshot via the forum so check it out here...

[http://www.christeredwards.com/test/Screenshot.png](http://www.christeredwards.com/test/Screenshot.png)[/QUOTE]

That's even a new one for me.

Have you made any modifications to the gnome-panel, EX: hacks?

---

### Post by Zelut on 2005-05-11
I'm not sure what it is I've done to the panel or to my installation but I'm actually giong to do a reinstall here soon anyway.

I've done a fresh install on my notebook & 'sudo apt-get install gdesklets' works just fine & I'm enjoying a number of candied-apps :)  I think I may have caused some conflicts in trying to manually install it before.  I'm going to just clean the system out & try over (its only a two day old install anyway, not going to lose much)

---

### Post by derrick1985 on 2005-05-11
[QUOTE=kuyaedz]I'm not sure what it is I've done to the panel or to my installation but I'm actually giong to do a reinstall here soon anyway.

I've done a fresh install on my notebook & 'sudo apt-get install gdesklets' works just fine & I'm enjoying a number of candied-apps :)  I think I may have caused some conflicts in trying to manually install it before.  I'm going to just clean the system out & try over (its only a two day old install anyway, not going to lose much)[/QUOTE]

k, glad it works on atleast one of your machines  :)

---

### Post by Zelut on 2005-05-11
[QUOTE=derrick1985]k, glad it works on atleast one of your machines  :)[/QUOTE]
 I've actually tracked down the culprit too.  When I try to install the gmail sidebar for gdesklets it kills it & afterwards it wont work.  I'm stayin' away from that from now on (now wont work on either machine).

I've been planning on reinstalling each machine anyway... usually takes about a week of tweakin' & hackin' before I figure out what works & what doesn't :)

---

### Post by Obionekanewbie on 2005-05-11
](*,) 

guys can anyone help, the how to is grande but i cant get on the first ladder run!

I have gDesklets in my Apps - Accessories menu ok but when I click it nothing happens. I get "starting gDesklets" down on my bottom taskbar but then it disappears no other windows?

Apologies in advance for my Newbieness!   ](*,)

---

### Post by darkaudit on 2005-05-11
[QUOTE=kuyaedz]I got gdesklets installed in my Applications menu but when I load it I only see a blank window with no options for creating a profile.  Any ideas?

I can't seem to upload a screenshot via the forum so check it out here...

[http://www.christeredwards.com/test/Screenshot.png](http://www.christeredwards.com/test/Screenshot.png)[/QUOTE]Have you a) installed gdesklets-data, or b) dragged-and-dropped any desklets from the gdesklets site into the shell? I think it needs some desklets to actually work with.

---

### Post by ryman on 2005-05-11
Is SC weather working for you guys. I keep getting errors on line 16 ... =(

---

### Post by ryman on 2005-05-12
I found this website provide great icons for starter bar. Its for windows but you can use it for starterbar too ... 

[http://interfacelift.com/icons-win/](http://interfacelift.com/icons-win/)

---

### Post by derrick1985 on 2005-05-12
[QUOTE=ryman]Is SC weather working for you guys. I keep getting errors on line 16 ... =([/QUOTE]

I get the same problem. I have an older weather desklet running, and it still works fine.

BUT SC doesn't.

---

### Post by bihe on 2005-05-12
perfect howto - thx

---

### Post by pdk001 on 2005-05-15
i've finally successfully installed it on my machine
thanks bunch for your tip

---

### Post by arnieboy on 2005-05-29
I have been running gdesklets as well of later after a couple of years when I was mesmerized by KDE's superkaramba.. The coolest desklet according to me is the gmail checker.

---

### Post by Majlo on 2005-05-30
[QUOTE=ryman]I found this website provide great icons for starter bar. Its for windows but you can use it for starterbar too ... 

[http://interfacelift.com/icons-win/](http://interfacelift.com/icons-win/)[/QUOTE]


Thx :-) ..Icons are very good

---

### Post by andlinux21 on 2005-06-01
[COLOR=Blue]I finally got gdesklets to work for me and my Micron Transport Xke this is pretty sweet i have the weather plugin, g-mail, and the sensors but i cant get those to work[/COLOR]

---

### Post by baraider on 2005-06-02
I install gdesklets and not gdesk-data but there is no gdesklets in my applications-accessories to click on and create a profle....

When i run it from terminal..nothing comes up

andy@kubuntu:~$ gdesklets &
[2] 8228
andy@kubuntu:~$ Starting gdesklets-daemon...
Connected to daemon in 267 microseconds.

---

### Post by frozen_fire on 2005-06-02
you are using kubuntu aka running kde and gdelsklets is for gnome 
in kde you got superkaramba that do the same job

---

### Post by baraider on 2005-06-02
[QUOTE=frozen_fire]you are using kubuntu aka running kde and gdelsklets is for gnome 
in kde you got superkaramba that do the same job[/QUOTE]
kubutu is just the name of my machine....i plan to install kde on top of the gnome....but stuck with gnome...

---

### Post by fubar2k1 on 2005-06-03
> you are using kubuntu aka running kde and gdelsklets is for gnome 
in kde you got superkaramba that do the same job

You can run them under KDE also

---

### Post by Ride Jib on 2005-06-26
Does the gDesklet website not load for anyone else?

Is there anywhere else we can download these goodies from?

---

### Post by Ride Jib on 2005-06-26
Ok, when I try to put "cornerxmms" on my desktop, it tells me "A sensor could not be found." What the heck is this? Since when does a media player require sensors?

Anyone have any insight on this?

---

### Post by graabein on 2005-06-27
How do I find the weather.com location or postal code for Trondheim, Norway for the iWeather desklet?

---

### Post by jonny on 2005-06-27
[QUOTE=graabein]How do I find the weather.com location or postal code for Trondheim, Norway for the iWeather desklet?[/QUOTE]Go to weather.com and find your town.  Look at the url and you'll see a code buried in the address somewhere.  That's the number you need.

---

### Post by Skel on 2005-06-27
[[IMG]http://img297.echo.cx/img297/4966/screenshot9oq.th.png[/IMG]](http://img297.echo.cx/my.php?image=screenshot9oq.png)

I have gdesklets running version .035 but i cant get it to be transparent all i see is this big black spts around my desklets anyone know how i can fix it.. I tried to click in confuguation didn twork and adding transparne tas backgroudn for each desklet didnt work... :/ ](*,)

I figured it out the transpancy thing in configuration i needed turned off...

---

### Post by graabein on 2005-06-28
[QUOTE=jonny]Go to weather.com and find your town.  Look at the url and you'll see a code buried in the address somewhere.  That's the number you need.[/QUOTE]
Brilliant. Thanks!

---

### Post by gammyhand on 2005-06-28
[QUOTE=Obionekanewbie]](*,) 

guys can anyone help, the how to is grande but i cant get on the first ladder run!

I have gDesklets in my Apps - Accessories menu ok but when I click it nothing happens. I get "starting gDesklets" down on my bottom taskbar but then it disappears no other windows?

Apologies in advance for my Newbieness!   ](*,)[/QUOTE]
I have exactly the same problem. Anyone know what is causing it?

---

### Post by sturner16 on 2005-06-28
Yes I get relatively the same problem.  gDesklets will run, however I cannot load any desklets at all.  Ex:  Double-clicking Starterbar in the gDesklets window will create a box in the middle of my screen with no options/buttons/etc...just a blank box.  I can't even right-click to customize or anything.  Then closing that box (yes it has max-min-close buttons) brings up a different-sized box, however it acts the same as the previous one.

Sorry if this doesn't make sense, this whole gDesklets thing isn't really making sense to me.  Running the application seems to hang my system a lot.

btw...new Ubuntu user (first time w/ Linux), and so far it has treated me very well.  A big thank you to everybody for all your help on these boards!

---

### Post by foxy123 on 2005-06-28
[QUOTE=gammyhand]I have exactly the same problem. Anyone know what is causing it?[/QUOTE]
if you have a problem with launching any programme, the best thing to do is to start it from terminal and see what are the error messages. Then you can post those messages here or googled for them.

in case of GDesklets, run gdesklets from your terminal and let us know what problem you have...

---

### Post by gammyhand on 2005-06-30
[QUOTE=foxy123]if you have a problem with launching any programme, the best thing to do is to start it from terminal and see what are the error messages. Then you can post those messages here or googled for them.

in case of GDesklets, run gdesklets from your terminal and let us know what problem you have...[/QUOTE]
Good advice. Thanks! :)

---

### Post by gammyhand on 2005-06-30
[QUOTE=gammyhand]Good advice. Thanks! :)[/QUOTE]
 OK...I have gdesklets installed fine. The problem is that whenever I try and download a desklet from their site I get an XML parsing error on the files.php page...anyone know whats causing it?

---

### Post by jnk on 2005-06-30
Nice.!!!!

Got the things I wanted up and working directly.
Just one thing, is gDesklets realy supposed to eat 40% - 50% CPU.?

EDIT: Darn attachment...... [Screenshot](http://screens.piratkopia.se/screen-gdesklets.png)

---

### Post by foxy123 on 2005-06-30
[QUOTE=jnk]Nice.!!!!

Got the things I wanted up and working directly.
Just one thing, is gDesklets realy supposed to eat 40% - 50% CPU.?

EDIT: Darn attachment...... [Screenshot](http://screens.piratkopia.se/screen-gdesklets.png)[/QUOTE]
as I noticed 0.35 is less hungry...

---

### Post by jnk on 2005-07-01
installed 0.35 and it's a BIG difference.

---

### Post by glandula on 2005-07-05
any chance of a newbie guide on how to install 0.35.1  ? i dont know how to install anything that isnt in synaptec

---

### Post by foxy123 on 2005-07-05
[QUOTE=glandula]any chance of a newbie guide on how to install 0.35.1  ? i dont know how to install anything that isnt in synaptec[/QUOTE]
is there any paticular reason for upgading 0.35?

---

### Post by glandula on 2005-07-05
yes cos i want it

---

### Post by foxy123 on 2005-07-05
well, 0.35 deb is available here [http://ubuntuforums.org/showthread.php?t=40982](http://ubuntuforums.org/showthread.php?t=40982)
you can d/l it and run:
```
sudo dpkg -i gdesklets_0.35-1~5.04ubp1_i386.deb
``` 

However, if you want 0.35.1 in particular you will have to compile it from the source or wait until it's backported.

---

### Post by Xian on 2005-07-05
[QUOTE=glandula]any chance of a newbie guide on how to install 0.35.1  ? i dont know how to install anything that isnt in synaptec[/QUOTE]
It is no more difficult that downloading the [.35.1](http://www.gdesklets.org/releases/gDesklets-0.35.1.tar.bz2) version, extracting it with a right-click on the file, and then viewing the README which is located in the newly extracted folder. All the instructions are in that file, and presented for you in step by step detail what to do on your machine. Begin with this and then post back if you have any questions. You will learn more by doing as much as you can for yourself.

---

### Post by neurosion on 2005-07-13
I haven't been able to pull up the [gdesklets website](gdesklets.gnomedesktop.org) for two days now.  Anyone have any information?

---

### Post by zarathustra on 2005-07-13
Not just gDesklets area...the entire website doesn't work...

---

### Post by arnieboy on 2005-07-14
this is the real bane of FOSS.. no accountability.. they shd atleast leave a one line message as to when its gonna come up...

---

### Post by foxy123 on 2005-07-14
it's happened before... pretty annoying when you have no info when it's up again...

---

### Post by flak9 on 2005-07-15
yea, this is driving me nuts also.  does anyone know of an alternative place to download the different deskets?

gdesklets.org says:

"Sorry, the server has been hacked and defaced.
We'll return soon!"

---

### Post by zarathustra on 2005-07-15
Looks like it's back.

---

### Post by DaRk on 2005-07-18
Hey, I just installed my Ubuntu and am slowly learning my way about the OS. I attempted to follow the install instructions for the gDesklets, but ge the following error:
      Reading package lists... Done
      Building dependency tree... Done
      E: Couldn't find package gdesklets
Since I can't get it through the apt-get thing, can someone either suggest another method or give me a detailed set of instructions to compile it myself?

---

### Post by foxy123 on 2005-07-19
[QUOTE=DaRk]Hey, I just installed my Ubuntu and am slowly learning my way about the OS. I attempted to follow the install instructions for the gDesklets, but ge the following error:
      Reading package lists... Done
      Building dependency tree... Done
      E: Couldn't find package gdesklets
Since I can't get it through the apt-get thing, can someone either suggest another method or give me a detailed set of instructions to compile it myself?[/QUOTE]
grab it here [http://www.sethkinast.com/ubuntu/hoary/backports/gdesklets_0.35.1-1~5.04ubp1_i386.deb](http://www.sethkinast.com/ubuntu/hoary/backports/gdesklets_0.35.1-1~5.04ubp1_i386.deb)
and run
```
sudo dpkg -i gdesklets_0.35.1-1~5.04ubp1_i386.deb
```

---

### Post by Strangerdave on 2005-07-28
Thanks for the "How To"  I like these things and have been searching for a way to install them :) 

-TS-

---

### Post by gcblig on 2005-08-26
Thanks so much - this is the first time i got gdesklets to run successfully!

---

### Post by pranith on 2005-09-12
me getting the following errors  ](*,) 

# gdesklets start

Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/gdesklets/utils/__init__.py", line 23, in _pretty_excepthook
    deep_trace = True)
  File "/usr/lib/gdesklets/utils/ErrorFormatter.py", line 77, in format
    if (path and vfs.exists(path)):
  File "/usr/lib/gdesklets/utils/vfs.py", line 102, in exists
    return gnomevfs.exists(gnomevfs.URI(uri))
NameError: global name 'gnomevfs' is not defined

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/gdesklets", line 4, in ?
    from main.DisplayList import DisplayList
  File "/usr/lib/gdesklets/utils/ErrorFormatter.py", line 119, in _new_imp
    module = _old_imp(name, globs, locls, fromlist)
  File "/usr/lib/gdesklets/main/DisplayList.py", line 4, in ?
    from utils import vfs
  File "/usr/lib/gdesklets/utils/ErrorFormatter.py", line 119, in _new_imp
    module = _old_imp(name, globs, locls, fromlist)
  File "/usr/lib/gdesklets/utils/vfs.py", line 120, in ?
    exists = exists_urllib2
NameError: name 'exists_urllib2' is not defined


what shud i do? :( :cry:

---

### Post by kahrytan on 2007-07-26
Does anyone know how to move the desklets? Right-Click and Move doesn't work.  I tried right-click, choose move, and click to grab it but the grab is then disabled. Mouse wheel button doesn't work either.

---

### Post by kickstart on 2007-07-27
Hey guys, im having trouble with this one.

I can install it fine but when i go applications--> accessories --> gdesklets the shell will start but i get no file edit view or any options like that i just get a blank box, when i exit it, it tells me i have to force quit (obviously crashed). 

If i start it from terminal with 'gdesklets start' it says 'starting gdesklets-daemon' and then says 'cannot establish connection to daemon: timeout!' followed by 'the log file might help you solving the problem'

interestingly, when i go into synaptic and search for gdesklets, its telling me that i have both gdesklets and gdesklets-data install, however when i try and remove just gdesklets-data i have to remove both, reinstalling makes no difference, same problem.

any help would be appreciated, im a linux noob and really want to get this working:D

thanks

---

### Post by kickstart on 2007-07-30
ive been fiddling around with still no luck, anyone else got any ideas? see my post above for my problem. thanks

---

### Post by PaulFXH on 2007-07-30
> **kahrytan said:**
> Does anyone know how to move the desklets? Right-Click and Move doesn't work.  I tried right-click, choose move, and click to grab it but the grab is then disabled. Mouse wheel button doesn't work either.

To move, DON'T click -- just move the mouse. The click is to STOP the gdesklet moving.

---

### Post by Noobish on 2007-08-05
Nice quote at the end we appreciate you yanks voting democratic.Cut and run yankee...lol

---

### Post by ginsujim on 2008-10-07
> **kickstart said:**
> Hey guys, im having trouble with this one.

I can install it fine but when i go applications--> accessories --> gdesklets the shell will start but i get no file edit view or any options like that i just get a blank box, when i exit it, it tells me i have to force quit (obviously crashed). 

If i start it from terminal with 'gdesklets start' it says 'starting gdesklets-daemon' and then says 'cannot establish connection to daemon: timeout!' followed by 'the log file might help you solving the problem'

interestingly, when i go into synaptic and search for gdesklets, its telling me that i have both gdesklets and gdesklets-data install, however when i try and remove just gdesklets-data i have to remove both, reinstalling makes no difference, same problem.

any help would be appreciated, im a linux noob and really want to get this working:D

thanks

Havin the same problem here.  Anyone have any ideas on this?

---

