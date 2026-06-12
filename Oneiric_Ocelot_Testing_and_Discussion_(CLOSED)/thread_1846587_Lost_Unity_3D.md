---
title: "Lost Unity 3D"
date: 2011-09-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-09-19
I did an update about 2 days ago and lost Unity 3D. I only get the background and the Nautalis screen. Ubuntu 2D and GNOME shell work great - so it is not my graphics card?

Anyone have any tips on why this happened and how I can get Unity 3D back??

thanks

---

### Post by sonicb00m on 2011-09-19
Not that this suggestion is much help but I had the same problem and just downloaded and reinstalled from the daily iso.

---

### Post by mc4man on 2011-09-19
login to unity session, open ccsm & make sure the unity plugin is enabled

---

### Post by ventrical on 2011-09-19
> **mc4man said:**
> login to unity session, open ccsm & make sure the unity plugin is enabled


  Ok . .that was the fix on that install. Thanks for the suggested work-a-round! I  have to mention that it wasn't easy because  compiz kept rejecting the (Unity Plugin) until I enabled desktop cube and rotate and a few others. I should know better by now .. but I guess i don't ! :)

---

### Post by ventrical on 2011-09-19
Actually it is more buggy now. I dropped down into 3.0.010 and that helped a bit but compiz seems to get more erractic with each update.

---

### Post by ventrical on 2011-09-19
Definitely a nvidia Accelerator Current Version/3.0.0-11 conflict.  I have now changed the Nvidia driver to the (current version) binary driver and I do have screen control on a fresh install - but something really went haywire with the last update on an earlier install of Oneiric and also with xxx11, from a fresh install and current update.

 Si I will apply that  (assumed fix) to my other install and get back here.

---

### Post by ventrical on 2011-09-19
Looks like a combo of things. I think perhaps  I messed up compiz a bit - but I got it working on this  earlier install.

---

### Post by mc4man on 2011-09-19
Myself use cube/rotate rather than wall (unity requies either wall or cube be set.
On any fresh install rather than mess with ccsm I start with this command, after compiz resets then go in and set up # of ws's, scroll on desktop, adjust the text overlay on the scale spread,  ect. (I remove quite a # of plugins that aren't useful here
```
gconftool-2 -s --type=list --list-type=string /apps/compiz-1/general/screen0/options/active_plugins  "[core,composite,opengl,decor,png,text,vpswitch,resize,place,cube,gnomecompat,move,regex,rotate,scale,scaleaddon,animation,expo,unityshell]"
```

There is an erronous conflict between cube> flip left & unity > edge reveal left, though recently unity seems to take it a bit personally at times and the launcher can suddenly stop revealing on left edge.
(can be fixed by disabling the reveal & flip, then re-enabling both

Till the 2nd part of the minimize bug has a fix released - xserver was fix released today, unity will be next upgrade, it important to make sure the in unity plugin > switcher > that "show minimized windows in switcher" option remains disabled

---

### Post by ventrical on 2011-09-19
> **mc4man said:**
> Myself use cube/rotate rather than wall (unity requies either wall or cube be set.
On any fresh install rather than mess with ccsm I start with this command, after compiz resets then go in and set up # of ws's, scroll on desktop, adjust the text overlay on the scale spread,  ect. (I remove quite a # of plugins that aren't useful here
```
gconftool-2 -s --type=list --list-type=string /apps/compiz-1/general/screen0/options/active_plugins  "[core,composite,opengl,decor,png,text,vpswitch,resize,place,cube,gnomecompat,move,regex,rotate,scale,scaleaddon,animation,expo,unityshell]"
```There is an erronous conflict between cube> flip left & unity > edge reveal left, though recently unity seems to take it a bit personally at times and the launcher can suddenly stop revealing on left edge.
(can be fixed by disabling the reveal & flip, then re-enabling both

Till the 2nd part of the minimize bug has a fix released - xserver was fix released today, unity will be next upgrade, it important to make sure the in unity plugin > switcher > that "show minimized windows in switcher" option remains disabled

   I was having lots of fun with alpha 3 and compiz/unity.

Thanks for your advice. I m going to try that on this new install for my Acer Extensa 4420.

Installing .......:)

---

### Post by jbicha on 2011-09-19
Alternatively, you can just run

```
unity --reset
```

when you have problems like this. That will reset all of your Compiz settings to the defaults. While CCSM is fun, I don't recommend it as there are way too many ways in there to break your Unity.

---

### Post by ventrical on 2011-09-20
> **jbicha said:**
> Alternatively, you can just run

```
unity --reset
```when you have problems like this. That will reset all of your Compiz settings to the defaults. While CCSM is fun, I don't recommend it as there are way too many ways in there to break your Unity.

```
dale@ubuntu:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...yes
[LOG]: Moving Internal Files
[LOG]: Copying subdirectory from /home/dale/.compiz/session to /home/dale/.compiz-1/session
[LOG]: Copied file /home/dale/.compiz/session/1039aaec913df78195131651278156748000000077510033 to /home/dale/.compiz-1/session/1039aaec913df78195131651278156748000000077510033
[LOG]: Successfully moved internal files
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x800

Initializing unityshell options...done
Starting unity-window-decorator
DEBUG 2011-09-20 06:07:11 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1280 h=800
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing cube options...done
Initializing debugspew options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing mag options...done
Initializing neg options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing screenshot options...done
Initializing shift options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing thumbnail options...done
Initializing water options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing zoom options...done
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "run_command_terminal_key"
Setting Update "run_command_terminal_key"
WARN  2011-09-20 06:08:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-09-20 06:08:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-09-20 06:08:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2011-09-20 06:08:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2011-09-20 06:08:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-09-20 06:08:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-09-20 06:08:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-09-20 06:08:11 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2011-09-20 06:08:12 unity.iconloader IconLoader.cpp:508 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2011-09-20 06:08:12 unity.iconloader IconLoader.cpp:508 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
WARN  2011-09-20 06:08:12 unity.iconloader IconLoader.cpp:508 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/group-songs.svg: Error opening file: No such file or directory
WARN  2011-09-20 06:08:12 unity.iconloader IconLoader.cpp:508 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/group-albums.svg: Error opening file: No such file or directory
```

which gives...

---

### Post by ventrical on 2011-09-20
> **mc4man said:**
> Myself use cube/rotate rather than wall (unity requies either wall or cube be set.
On any fresh install rather than mess with ccsm I start with this command, after compiz resets then go in and set up # of ws's, scroll on desktop, adjust the text overlay on the scale spread,  ect. (I remove quite a # of plugins that aren't useful here
```
gconftool-2 -s --type=list --list-type=string /apps/compiz-1/general/screen0/options/active_plugins  "[core,composite,opengl,decor,png,text,vpswitch,resize,place,cube,gnomecompat,move,regex,rotate,scale,scaleaddon,animation,expo,unityshell]"
```There is an erronous conflict between cube> flip left & unity > edge reveal left, though recently unity seems to take it a bit personally at times and the launcher can suddenly stop revealing on left edge.
(can be fixed by disabling the reveal & flip, then re-enabling both

Till the 2nd part of the minimize bug has a fix released - xserver was fix released today, unity will be next upgrade, it important to make sure the in unity plugin > switcher > that "show minimized windows in switcher" option remains disabled

I tried this and it forced over to the metacity/nautalis screen? I put the above code in first - then installed ccsm. I am now working out of Unity 2D.

---

### Post by ventrical on 2011-09-20
ok.. after logging out -after reseting unity- I now have Unity 3D back.... but it was never this hard to work as was with alpha which I had almost no problem with.\\One note I would just like to make is that I was using the compiz ppas - for the prerelease for Oneiric. Perhaps I should use these ?

---

### Post by ventrical on 2011-09-20
Got cube !!

:)

Thanks . Lot of good pointers here.  Lots of teething pains too :)

---

### Post by ventrical on 2011-09-20
> **mc4man said:**
> Myself use cube/rotate rather than wall (unity requies either wall or cube be set.
On any fresh install rather than mess with ccsm I start with this command, after compiz resets then go in and set up # of ws's, scroll on desktop, adjust the text overlay on the scale spread,  ect. (I remove quite a # of plugins that aren't useful here
```
gconftool-2 -s --type=list --list-type=string /apps/compiz-1/general/screen0/options/active_plugins  "[core,composite,opengl,decor,png,text,vpswitch,resize,place,cube,gnomecompat,move,regex,rotate,scale,scaleaddon,animation,expo,unityshell]"
```There is an erronous conflict between cube> flip left & unity > edge reveal left, though recently unity seems to take it a bit personally at times and the launcher can suddenly stop revealing on left edge.
(can be fixed by disabling the reveal & flip, then re-enabling both

Till the 2nd part of the minimize bug has a fix released - xserver was fix released today, unity will be next upgrade, it important to make sure the in unity plugin > switcher > that "show minimized windows in switcher" option remains disabled

Oddly enough I could not get compiz to work  on two other installs on a different PC unless I entered the above suggested code.

---

### Post by mc4man on 2011-09-20
> **ventrical said:**
> Oddly enough I could not get compiz to work  on two other installs on a different PC unless I entered the above suggested code.
That was just an example of a *way* to set up (or reset) the compiz plugins used on a unity(3d) install.
Which ones I happen to think are useful/needed may be different than what you or someone else wants.

Because Ubuntu still is not providing easy (safe) access to the unityshell options I'm all for people going into ccsm and seeing what works and what doesn't.
If they happen to mess things up well hopefully they learned something for the next time in ccsm (& usually the unity --reset will restore to default

If you get your plugin setup as you like (as far as enabled/disabled)
then you can use the get command to print the current string - save it to a text file and if need be can use THAT string in the above set command in lieu of the one I posted (though I find it good for a rotate/cube setup

```
gconftool-2 --get /apps/compiz-1/general/screen0/options/active_plugins


```

---

### Post by ventrical on 2011-09-20
As I see it , it appears that what happened with Natty is still happening with Oneiric! However, I had used the pre-release compiz ppas and they worked great back  2 weeks ago. Now all of a sudden compiz is getting touchy again (IMO)  and for newbies, it's really hard to train them. I have a few clients/friends that I am trying to sell on the idea of Edubuntu 11.04, which works exceptionally well. I am just comming from a stability perspective , looking forward to the next LTS and wondering what drastic changes will take place and even if compiz is part of all that.

  So it would be good to see compiz and Unity 3D have some cohesion across the board when Ocelot Stable is released.. especially for the sake of new users. There has to be some stability ironed out in the next few weeks, otherwise newer end_users are going to struggle with a lot of verbose work-a-rounds. I'm not complaining - I 'm just trying to make a point overall.

---

### Post by ventrical on 2011-09-20
> **mc4man said:**
> That was just an example of a *way* to set up (or reset) the compiz plugins used on a unity(3d) install.
Which ones I happen to think are useful/needed may be different than what you or someone else wants.

Because Ubuntu still is not providing easy (safe) access to the unityshell options I'm all for people going into ccsm and seeing what works and what doesn't.
If they happen to mess things up well hopefully they learned something for the next time in ccsm (& usually the unity --reset will restore to default

If you get your plugin setup as you like (as far as enabled/disabled)
then you can use the get command to print the current string - save it to a text file and if need be can use THAT string in the above set command in lieu of the one I posted (though I find it good for a rotate/cube setup

```
gconftool-2 --get /apps/compiz-1/general/screen0/options/active_plugins


```


Thanks again! :)

---

### Post by jbicha on 2011-09-20
> **ventrical said:**
> 
  So it would be good to see compiz and Unity 3D have some cohesion across the board when Ocelot Stable is released.. especially for the sake of new users. There has to be some stability ironed out in the next few weeks, otherwise newer end_users are going to struggle with a lot of verbose work-a-rounds. I'm not complaining - I 'm just trying to make a point overall.

Compiz shouldn't be changing near as much next cycle as it did this round. And compiz is working better for me now that it did just a few weeks ago.

unity --reset shouldn't be needed for those who upgrade from 11.04 stable to 11.10 stable, unless they've been tweaking things in CCSM. A simpler Unity tweak tool (or an extended gnome-tweak-tool) would be a big help.

---

### Post by ventrical on 2011-09-20
> **jbicha said:**
> Compiz shouldn't be changing near as much next cycle as it did this round. And compiz is working better for me now that it did just a few weeks ago.

unity --reset shouldn't be needed for those who upgrade from 11.04 stable to 11.10 stable, unless they've been tweaking things in CCSM. A simpler Unity tweak tool (or an extended gnome-tweak-tool) would be a big help.

My point exactly...I would hope then that compiz and/or unity would be more intuitive when trying to resolve macro conflicts - like ie; offer a new macro rather than to try and resolve conflicting macros.. etc.. but perhaps that's expecting too much and I am pressumming that that some sleek fixes may be around the corner soon.

---

### Post by ventrical on 2011-09-21
I  have a new situation where  both Unitys hang when I try:
unity --reset

I tried to copy and paste that info , but no luck.

It will start with a lot of verbose script pertaining to the reset , but then will hang in terminal. The first time I tried it  it followed through with the process in terminal until I got the terminal prompt back. Now it just hangs so I have to kill the process and I am right back at square one.


Acer Extensa 4420, 3GBDDR  AMD64AthelonX2, 120GBSATA

---

### Post by ventrical on 2011-09-21
I went into compiz experiemntal, made the icons smaller and made some adjustments there and now screen and system does not hang or lock (for now !!)

Unfreeze Unity 3D Desktop-

[B]1. Open Compiz settings manager.
2. Open Ubuntu Unity Plugin
3. Right click <experimental>tab.
4. Set <Launcher Icon Size> to 40
[/B]

---

