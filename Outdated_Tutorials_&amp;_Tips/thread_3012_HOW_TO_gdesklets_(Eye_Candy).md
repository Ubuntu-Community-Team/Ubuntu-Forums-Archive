---
title: "HOW TO: gdesklets (Eye Candy)"
date: 2004-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by jdusablon on 2004-11-02
After much noob frustration of my own, I've decided to share what I've learned to get gdesklets working.

1. Add Universe to apt/Synaptic repositories. See [here](http://www.ubuntuforums.org/showthread.php?t=179) for more detail.

2. Fire up Synaptic Package Manager (or use sudo apt-get from terminal,) find and select **gdesklets** and **gdesklets-data** for installation, install.

3. Reboot. Don't know if it's necessary, but it yields better results for me.

4. From the **Applications** menu, select **Run Application...** and type ```
gdesklets
```That gets the daemon running.

5. Again from **Applications** menu, select **Run Application...** and type ```
gdesklets /usr/share/gdesklets/Displays/XXXX/ZZZZ.display
```**XXXX** represents the name of the folder containing the desklet you want to load, **ZZZZ.display** is the actual filename of the desklet module. A desklet will appear under and stuck to the mouse cursor. Find a spot on the desktop and click to place the desklet there.

6. You can move gdesklets by clicking and dragging them with the middle mouse button. You can configure any desklet by right-clicking on it.

Thanks to moderator Rancoras and this [thread](http://ubuntuforums.org/showthread.php?t=1851) for the help. Hope this is useful.

---

### Post by St-Ex on 2004-11-02
Did someone got xmms-corner working? I installed python-xmms, the display is there, but xmms is not loaded...

---

### Post by Rancoras on 2004-11-02
There's a little button in the lower left corner of the display....hard to describe where....  just to the left of the one that opens "preferences".  It loads and unloads xmms.

---

### Post by dave_blob on 2004-11-02
To make it a little eaiser, go into the folders with all the displays, right-click on a .display file and tell it to 'open with' and type in gdesklets. 
Now you can just double click on any one of the displays and it loads automatically.

---

### Post by St-Ex on 2004-11-03
> There's a little button in the lower left corner of the display....hard to describe where.... just to the left of the one that opens "preferences". It loads and unloads xmms 

Thx... 'Got it!

---

### Post by afonit on 2004-11-04
jdusablon

thank you soooooo much for this, now I have finally gotten gdesklets running for the first time.

wonderfull

thanks again for talking the time to post your solution

---

### Post by elwis on 2004-11-08
Man, I hope these will work someday. I only get attrubute-errors telling me there are no AttributeError: 'Display' object has no attribute '_Display__group'
'NoneType' object has no attribute 'group'
'NoneType' object has no attribute 'group'

I managed to get a small weather square once, but since it didn't want to display anything (retrieval failed) I could live without it. Hope it'll get better in the future

---

### Post by Rancoras on 2004-11-08
What command are you typing that results in that error?

---

### Post by elwis on 2004-11-08
[QUOTE=Rancoras]What command are you typing that results in that error?[/QUOTE]
 Well, I can't get it back, now I only get a
> 
gDesklets 0.26.2
Copyright (C) 2003, 2004 The gDesklets Team

This software is licensed under the terms of the GNU GPL.


And nothing happens :)

Anyway, no bother, since the weather desklet can't retrieve any information, it's not of much use anyway. (But it would of course be nice to impress my Ms-colleagues.. but nah, they simply don't deserve the beauty :)

---

### Post by Rancoras on 2004-11-08
And you followed the howto at the top of this thread?

---

### Post by Arbiter on 2004-11-09
This may be a dumb question, but bear with me I'm new at this...

I got gdesklets working, but I'll log out or reboot the machine and the gdesklets apps don't show up when I reboot.  How can I get the gdesklets daemon running when GNOME starts?

---

### Post by nehalem on 2004-11-10
To add to this discussion, instead of having to type each time "gdesklets path/to/display" you can just go to the properties of a display file->Open With and add gdesklets.  From now on you can just double click any .display file to create desklets.

This simplified my life a bit.

---

### Post by Rancoras on 2004-11-10
[QUOTE=Arbiter]This may be a dumb question, but bear with me I'm new at this...

I got gdesklets working, but I'll log out or reboot the machine and the gdesklets apps don't show up when I reboot.  How can I get the gdesklets daemon running when GNOME starts?[/QUOTE]

I saved my session with the displays I wanted running, and they come back every time.

---

### Post by cll2001 on 2004-11-11
Thanks for the pointers. However I do have a slight problem. How do I get gdesklets to be started at boot up without going to the RUN console?

---

### Post by shimon on 2004-11-11
[QUOTE=jdusablon]
3. Reboot. Don't know if it's necessary, but it yields better results for me.
[/QUOTE]
there is no need for this at all it doesn't help or make a difrence (unless your using winbloat) please remove this and don't make your self look  :oops:

---

### Post by HungSquirrel on 2004-11-11
[QUOTE=cll2001]Thanks for the pointers. However I do have a slight problem. How do I get gdesklets to be started at boot up without going to the RUN console?[/QUOTE]
 Logout with gdesklets running, and tell Gnome to save your session.  Should do the trick.

---

### Post by HiddenWolf on 2004-11-11
It is far easier to just search for *.display
It will give you all files listed that gdesklets can run.

---

### Post by cll2001 on 2004-11-11
[QUOTE=HungSquirrel]Logout with gdesklets running, and tell Gnome to save your session.  Should do the trick.[/QUOTE]  :shock: Sorry for being apart of the Redundancy squad. I guess I should have read a little further. :oops: 
 But a real problem has surfaced and that is even after I tell gnome to save my session . Not all of the starters come back. Firefox seems to work as does Evolution and the Home folder. But programs like theGimp or synaptic or gnome nettool don't always come back. Is there a bug in gdesklets perhaps ?

---

### Post by Rancoras on 2004-11-11
Geez!  You want that many apps starting automatically?

---

### Post by jayclark on 2004-11-13
Well before my hardrive went bad gdesklets worked fine. Now that I replaced the hardrive and reinstalled Ubuntu gdesklets don't work anymore....

---

### Post by jayclark on 2004-11-13
Ok nevermind, after a restart they finally started working.

---

### Post by chombee on 2004-11-14
I can't ever get the weather applets to work, can someone tell me how to configue them?

---

### Post by mattyh on 2004-11-14
Most of the weather ones didn't work for me either.  I finally cheated [img]http://www.ubuntuforums.org/images/smilies/icon_wink.gif[/img]  I installed the gdesklets from hoary (not recommended as I have noted some instability brought to my system via my installing hoary apps...not just gdesklets), and it worked.  I read on the gdesklet forums that the .26 version included in ubuntu has some bugs, but they have stopped working on it and just gone ahead and jumped to .30 and above.  So, long story short, once hoary comes out things will be all better ;)

---

### Post by dickosoft on 2004-11-15
Hey,

I keep getting this problem.

[I]dicko@ubuntu:~ $ sudo apt-get install gdesklets
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gdesklets: Depends: libgtop2-2 but it is not going to be installed
E: Broken packages
[/I]

Currently is installed: libgtop2-4.

I have taken the following actions:
1. installed libgtop2-2 apart from gdekslets, but then my applets like volume control and minicommander doesn't appear at the bar and in the add to panel list
2. installed gdesklets with a tar.gz. I got the same error

Does someone know how to solve my problem?

---

### Post by HiddenWolf on 2004-11-15
Hm, the gdesklets version in hoary is broken for me :-S

---

### Post by TravisNewman on 2004-11-15
[QUOTE=HiddenWolf]Hm, the gdesklets version in hoary is broken for me :-S[/QUOTE]
 A few people, myself included, have had problems with Hoary's gdesklets. If you shut down gdesklets, remove .gdesklets from your home directory, log out and back in, run gdesklets again, everything works. That worked for me and bvc at least.

---

### Post by gorth on 2004-11-26
Are there anybody out there with the same trouble as described in:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=3997](https://bugzilla.ubuntu.com/show_bug.cgi?id=3997)

---

### Post by Xian on 2004-11-30
For those having trouble running this application in Ubuntu using the available binary packages, you might consider installing the new gDesklets v0.32pre source tarball from the program homepage. It did require a few python development libs to be installed in order to finish compliling, but they were all located in the Warty repo's. I didn't have to install anything from Universe, Hoary, or another source library.

The nice thing about using a 0.3x version is that you can type "gdesklets shell" as a run application command, and this will not only start the gDesklets program, but also install and manage all the displays that are maintained for the newer versions with a very nice graphical GUI, and it will sit in the tray notification area (if enabled) when the window is closed.

---

### Post by svyeta on 2004-12-05
I'm getting rather confused with gDesklets.  I've installed it following the HOWTO, yet when i run the gdesklet command, the output becomes:

gDesklets 0.26.2
Copyright (C) 2003, 2004 The gDesklets Team

This software is licensed under the terms of the GNU GPL.

/usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning: gtk.mainloop is deprecated, use gtk.main instead
  self.warn(message, DeprecationWarning)

Yet, if I continue trying to start a .display file, it eventually works - though with quite a few errors, I might add.

Any idea how this can be fixed?

I think this has been a previous question as well though I don't think it was answered.

Cheers,
svyeta

---

### Post by Rancoras on 2004-12-05
The gdesklets in Warty is an older version.  The message you're seeing is not an error, but a warning.  It is telling you that gtk.mainloop is no longer being used, that the program should use gtk.main instead.  It really has no effect on whether gdesklets runs or not.  It will run just fine.  FWIW the latest version of gdesklets doesn't give this warning, but you'll have to wait for Hoary for that version.  To sum up, don't worry about the message.

---

### Post by karih on 2004-12-08
Thanks for the How-to, very helpful!

One minor problem I'm having though, if I use the "disk" desklet (see picture attachment) it displays wrong partition sizes.  As in the attached image I have 9.2GB /home partition but the desklet says it's only 1.15GB and the percentage isn't even correct (according to $ df).

Any ideas what might be wrong?

---

### Post by Rancoras on 2004-12-08
I think that's a bug that's fixed in the latest version.  You'll either have to compile it or wait for Hoary.  Myself, I'm just waiting.

---

### Post by mjjohansen on 2004-12-09
/me concludes compiling is probably a better idea for /me.

---

### Post by mr_bungie on 2004-12-13
I just compiled, is a bit more fast  :D

---

### Post by Quest-Master on 2004-12-20
Is there any way for CornerXMMS to play music but not have XMMS itself running?

---

### Post by safecracker on 2004-12-21
I get the following error after installing gdesklets 

(gDesklets:5969): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

can anyone help?

nevermind now I realized. The above error is actually debug code, it doesn't matter. The deamon is actually running. all is well.

---

### Post by rwabel on 2004-12-24
thanks for the howto. I'm on hoary and the installation worked fine. the daemon is running but I cannot start a Display. I wanted to use the StarterBar, but I also tried others. I always get this error message:
A sensor could not be found. This usually means that it has not been installed. But I've installed gdesklets and the data.

Traceback (most recent call last):
  File "/usr/share/gdesklets/factory/SensorFactory.py", line 60, in create_sensor
    module = __import__(name)
  File "/usr/share/gdesklets/Sensors/StarterBar/__init__.py", line 2, in ?
    from IconSet import IconSet
  File "/usr/share/gdesklets/Sensors/StarterBar/IconSet.py", line 9, in ?
    from utils import GConfWatcher
ImportError: cannot import name GConfWatcher

I hope someone can help me, thanks

---

### Post by node on 2004-12-27
Wont work for me.
I've installed gdesklets and gdesklets-data from CLI.
Now theres gDesklets under Applications-Accessoires-gDesklet.
When i fire it up, it says starting, but nothing happens.
When i use the CLI to run I get the following error.


```
root@ubuntubox:/usr/share/gdesklets/Displays/memory # gdesklets meminfo.display

(gDesklets:4828): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
gDesklets 0.26.2
Copyright (C) 2003, 2004 The gDesklets Team

This software is licensed under the terms of the GNU GPL.

root@ubuntubox:/usr/share/gdesklets/Displays/memory #
```

---

### Post by beeldings on 2004-12-27
When I tried compiling gDesklets-0.32 from the source, I received this error:

```

$ checking for glib-2.0 gdk-pixbuf-2.0 gtk+-2.0 pygtk-2.0 >= 2.4.0 Package pygtk-2.0
$ was not found in the pkg-config search path.
$ Perhaps you should add the directory containing 'pygtk-2.0.pc'
$ to the PKG_CONFIG_PATH environment variable
$ No package 'pygtk-2.0' found
$
$
$ configure: error: Library requirements (glib-2.0 gdk-pixbuf-2.0 gtk+-2.0 pygtk-2.0 >= 2.4.0) not met;
$ consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```

---

### Post by jadm5000 on 2004-12-27
[QUOTE=Rancoras]And you followed the howto at the top of this thread?[/QUOTE]
 Desklets -
*scratches head* .... im obviously TOO new here

---

### Post by AlvaroBF on 2004-12-28
Traceback (most recent call last):
  File "/usr/share/gdesklets/factory/DisplayFactory.py", line 99, in create_display
    dsp.new_child(childtype, settings, children)
  File "/usr/share/gdesklets/display/Display.py", line 219, in new_child
    import targetregistry
  File "/usr/share/gdesklets/display/targetregistry.py", line 18, in ?
    from TargetHTML          import TargetHTML
  File "/usr/share/gdesklets/display/TargetHTML.py", line 6, in ?
    import gtkhtml2
ImportError: No module named gtkhtml2

This error appears whenever I want to load any Display

Any idea?

---

### Post by UJM on 2004-12-29
[QUOTE=AlvaroBF]Traceback (most recent call last):
  File "/usr/share/gdesklets/factory/DisplayFactory.py", line 99, in create_display
    dsp.new_child(childtype, settings, children)
  File "/usr/share/gdesklets/display/Display.py", line 219, in new_child
    import targetregistry
  File "/usr/share/gdesklets/display/targetregistry.py", line 18, in ?
    from TargetHTML          import TargetHTML
  File "/usr/share/gdesklets/display/TargetHTML.py", line 6, in ?
    import gtkhtml2
ImportError: No module named gtkhtml2

This error appears whenever I want to load any Display

Any idea?

[email]alvaro.bf@gmail.com[/email] (I'm using Hoary version)[/QUOTE]
upgraded to Hoary this weekend installed latest gdesklets & gdesklets-data and got exactly the same results as AlvaroBF, I couldn't load ANY displays, tried various methods, from the shell, from run box, or by clicking on the actual display file in the gdesklets directory, also tried deleting gdesklets from my home directory then logging back on... still no joy .... formatted re-installed Warty. (for some reason Hoary ran noticably slower on my 750mhz machine than Warty.)
.

---

### Post by Swehulk on 2004-12-30
I get this massage when I try to load CornerXMMS:

"Could not load sensor 'CornerXMMS'

An error occured while loading a sensor. This most likely means that the sensor is broken or simply not installed."

"Invalid display file '/usr/share/gdesklets/Displays/CornerXMMS-0.0.5/cornerxmms-bottomright.display'

The display file contains invalid data and could not be loaded."

I downloaded it from [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)
and I have installed it using ./ in terminal

What could it be?
 :sad:

---

### Post by safecracker on 2004-12-31
[QUOTE=node]Wont work for me.
I've installed gdesklets and gdesklets-data from CLI.
Now theres gDesklets under Applications-Accessoires-gDesklet.
When i fire it up, it says starting, but nothing happens.
When i use the CLI to run I get the following error.


```
root@ubuntubox:/usr/share/gdesklets/Displays/memory # gdesklets meminfo.display

(gDesklets:4828): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
gDesklets 0.26.2
Copyright (C) 2003, 2004 The gDesklets Team

This software is licensed under the terms of the GNU GPL.

root@ubuntubox:/usr/share/gdesklets/Displays/memory #
```[/QUOTE]


please sir look 2 posts above your own, that is debug code not an error try loading a gdesklet app

---

### Post by Swehulk on 2005-01-01
Anyone have any idea on my problem? :D

---

### Post by sobralense on 2005-01-01
Just show this, running the daemon and dont running any Displays
*even putting on shell the path like desc. on top of this thread.

Traceback (most recent call last):
  File "/usr/share/gdesklets/factory/DisplayFactory.py", line 99, in create_display
    dsp.new_child(childtype, settings, children)
  File "/usr/share/gdesklets/display/Display.py", line 219, in new_child
    import targetregistry
  File "/usr/share/gdesklets/display/targetregistry.py", line 18, in ?
    from TargetHTML          import TargetHTML
  File "/usr/share/gdesklets/display/TargetHTML.py", line 6, in ?
    import gtkhtml2
ImportError: No module named gtkhtml2



updated to Hoary just about now =P
cat /etc/debian_version
3.1

gdesklets_0.32-1ubuntu1_i386.deb
gdesklets-data_0.32_all.deb

the packages installed.

Any one knows?

---

### Post by TravisNewman on 2005-01-01
Getting the same things as you guys. None of the gdesklets work for me. I assume it has something to do with the recent repackaging to make it install with python 2.4. I still have 2.3 installed... if there was some way to tell it to use 2.3 and not 2.4 these errors might go away.

---

### Post by sobralense on 2005-01-02
Ok guys, a bit of searching don't really hurts .. =D

This dude discovered a way.. =D> 

I think could be more easy to find anwsers than other with questions (I founded this when was looking for ubuntu developers ..)


[http://www.ubuntuforums.org/showthread.php?t=5829](http://www.ubuntuforums.org/showthread.php?t=5829)

( the most important for lazy)

Sonicred said:
"Gdesklets were not working before but now with python-gnome2-extras and python2.4-gnome2-extras installed all is well.

These should probably be marked as gdesklet dependencies."


*sorry about the bad English :rolleyes:

---

### Post by rwabel on 2005-01-02
that's really the solution. thank you very much for the posting.

---

### Post by Uuranor on 2005-01-02
[QUOTE=rwabel]that's really the solution. thank you very much for the posting.[/QUOTE]
 Not for me :(
I have python2.4-gnome-extras, python-gnome2-extras and python-gnome2-extras-dev but I can't connect to the gdesklets daemon.
The log tells me that gnome-python2 bindings is not correctly installed.

---

### Post by Swehulk on 2005-01-02
Could anybody plz tell a noob lie me how to install them? :D

---

### Post by sobralense on 2005-01-02
[QUOTE=Uuranor]Not for me :(
I have python2.4-gnome-extras, python-gnome2-extras and python-gnome2-extras-dev but I can't connect to the gdesklets daemon.
The log tells me that gnome-python2 bindings is not correctly installed.[/QUOTE]

That's for gtkxml bug , that was a problem with python 2.4 and/or gdesklets
I'm using the hoary unstable version of the system.

---

### Post by Uuranor on 2005-01-03
[QUOTE=sobralense]That's for gtkxml bug , that was a problem with python 2.4 and/or gdesklets
I'm using the hoary unstable version of the system.[/QUOTE]

And to you do they function? O.o
I have hoary too and all the new python packages...

---

### Post by sobralense on 2005-01-03
Well, a bit slow I think... but my machine isn't that cool... a Duron 1.3ghz with 256mb ddr.

here is: (~600k I think this link its ok, try seeit)

[http://sobralense.host.sk/screenshot.png](http://sobralense.host.sk/screenshot.png)

---

### Post by Uuranor on 2005-01-03
To me they aren't working... I can't start the daemon :(
The error on the gdesklets.log is always the same: gnome-python2 not correctly installed :(

---

### Post by sobralense on 2005-01-03
I think you may try reinstalling all the "ubuntu-desktop" packages and remove and reinstall again the python packs...
I saw now and there are few python upgrades, but my ubuntu is working, so upgrading isnt a good idea, I think.

versions are:
python-gnome2-extras: 2.9.2-0ubuntu
python2.4-gnome2-extras 2.9.2-0ubuntu

---

### Post by vaskark on 2005-01-03
[font=Trebuchet MS]i can start the daemon but can't load any desklets. i keep getting this error:
  
   > Traceback (most recent call last):
    File "/usr/share/gdesklets/factory/DisplayFactory.py", line 99, in create_display
      dsp.new_child(childtype, settings, children)
    File "/usr/share/gdesklets/display/Display.py", line 219, in new_child
      import targetregistry
    File "/usr/share/gdesklets/display/targetregistry.py", line 18, in ?
      from TargetHTML          import TargetHTML
    File "/usr/share/gdesklets/display/TargetHTML.py", line 6, in ?
      import gtkhtml2
  ImportError: No module named gtkhtml2
  
  I have libgtkhtml2 installed, but I can't find a package named gtkhtml2. Anyone have some advice? I'm using updated hoary.[/font]

---

### Post by wallijonn on 2005-01-03
I made the mistake of trying to install gdesklets. Now my desktop is blank and I can't do anything. There is no .gdesklets in my /Home directory.

So I booted my Ubuntu-LiveCD, 
started a root terminal

sudo gedit mnt/hda1/etc/inittab
changed default init level to 1

saved the file
logged out
removed LiveCD

apt-get install gnome-panel
apt-get install gnome-core

That's right **installing gdesklets and gdeslets-data blew up and deleted gnome-panel & gnome-core**. So I could no longer get Rhymthbox to play my Internet Radio stations. This must be a Hoary-only app. as it blew up my Warty. 

[COLOR=Red]**[SIZE=4]You've been warned[/SIZE]**.[/COLOR]

Now I have to redo my whole desktop (icons, themes, fonts, wallpaper, etc).

What a pain!

Just rebooting to init 1 and apt-get remove gdesklets did not fix the problem.
deleting the files listed in /var/lib/dpkg/info/gdesklets.list did not help.
deleting /etc/gconf/schemas/gdesklets did not help.
deleting /usr/share/gdesklets directories did not help.
deleting home//.gconf & .gconfd did not help. (Another reason why I had to rebuild my desktop).

With the gnome-panel reinstall came this:
!prefs-key=/apps/panel/profiles/default/applets/mixer (no schema) on login and whenever I made a change to the panel. I eventually had to delete it. I had to remove / add gnome-applets via ag-get remove and SPM.

---

### Post by HBK on 2005-01-04
Hi,
is it possible to make some gDesklets always-on-top? I have the Starter-Bar and it's really great, but I would like it to be always on top, like the second gnome bar (which I deleted :P) was. Is that possible?

Thanks,
HBK

---

### Post by rbran100 on 2005-01-04
i would love to have the same functionality however i think that the design of gDesklets currently dosn't allow for that.  I don't know what it would do in the way of overhead either.  Let me know if you figure this out.

Rich

---

### Post by sobralense on 2005-01-04
Dear vaskark, try looking up the thread... PLEASE  =P
And then.. tell if U did it work.  8-[

---

### Post by Uuranor on 2005-01-06
[QUOTE=sobralense]I think you may try reinstalling all the "ubuntu-desktop" packages and remove and reinstall again the python packs...
I saw now and there are few python upgrades, but my ubuntu is working, so upgrading isnt a good idea, I think.

versions are:
python-gnome2-extras: 2.9.2-0ubuntu
python2.4-gnome2-extras 2.9.2-0ubuntu[/QUOTE]
 I've tried in all the manners ... But nothing happened :(
The log tell me always the same thing: gnome-python2 is not installed correctly.

---

### Post by dejitarob on 2005-02-07
Not suprisingly, the gdesklets version in the universal repository is old. Most of the old displays that come with it are broken like weather, memory and hdd monitors. The [new version of gdesklets]("http://gdesklets.gnomedesktop.org/"), which is easy to install if you follow the readme, supposedly adds and fixes a lot but is not backwards compatible with the old displays, which are a majority of the gdesklets released. As far as I can tell there have been a few new displays released like SideCandy, but they aren't as attractive or useful as the old ones. Anyone aware of alternatives or any cool gdesklets that are working? It seems like every screenshot I see is using an outdated version or display that no longer works.

---

### Post by Xian on 2005-02-07
[QUOTE=dejitarob]As far as I can tell there have been a few new displays released like SideCandy, but they aren't as attractive or useful as the old ones. Anyone aware of alternatives or any cool gdesklets that are working? It seems like every screenshot I see is using an outdated version or display that no longer works.[/QUOTE]
I also decided to compile the latest version from source. All the required libs are in the warty repo for anyone who was curious. It will take a while for the desklets to catch up to the changes being implemented now, but at least there appears to be a clear standard going forward. I thought that the new RSS reader was a great addition. It looks super and is very configurable.

---

### Post by arx-lupus on 2005-02-07
Have used gdesklets on a previous Slackware install and on Hoary. The Side Candy desklets are a different approach than the old sensor/display setup. They are not the snazziest at the moment but given a little time you should see new variations.

If you are happy tinkering you could always modify the ones offered. Have a look on the gdesklets forum for pointers on that.

---

### Post by cdhotfire on 2005-02-23
anyone know how to get the weather thing going, because it says it cant get the weather. :? . Also for some reason when i open gdesklets now it pop up like 50 thigns. So gnome reboots. How to i unistall it completely?, because i went to synaptic and unistalled it there, but that didnt work.

---

### Post by lonetree on 2005-02-24
Guys,

just started using ubuntu for a while, kinda new to this, have been using some other linux distro for a while too, found ubuntu has a bright future.

By the way, I'm trying to install gDesklets, seems to be unable to install. Perhaps someone can give a step by step guide, first question, where should I install the files to?

Hope you guys out there can help.

Thanks a zillion.

Regards

Lonetree

---

### Post by Rhodan on 2005-03-27
Yeah I'd love to get gdesklets working properly.

Does it work in hoary ? I tried it in Warty and got the daemon going but could never add anything to the bar, is there a guide anywhere that I can look at ?

---

### Post by emperor on 2005-03-27
gdesklets works great in Hoary.
Just install "gdesklets" and "gdesklets-data". 
The data package includes quite a few "sensors and displays", ready to startup!

---

### Post by andlinux21 on 2005-05-25
[FONT=Comic Sans MS]Looks as if I will be trying gdesklets tomorrow I never could get it installed on my SUSE 9.1 box[/FONT]

---

### Post by sjatkins on 2008-05-23
This doesn't work for me as the daemon never comes up.  Everything times out trying to establish a connection to it and I can't find it in the process list.  A message saying the log file may help me to solve the problem is very unhelpful as the "/.gdesklet logfiles are empty except for a header line.  So what is going on with this flakey toy?

---

### Post by BatmansGehilfe on 2008-07-15
I expirience the same problem. I use Hardy in the 64-bit-version. Perhaps thats part of the problem?

I would appreciate greatly any help!

Cheers,
Daniel

---

