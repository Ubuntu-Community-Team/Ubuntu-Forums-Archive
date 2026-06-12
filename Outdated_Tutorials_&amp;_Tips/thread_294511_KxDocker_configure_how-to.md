---
title: "KxDocker configure how-to"
date: 2006-11-06
forum: Outdated Tutorials &amp; Tips
---

### Post by turbojugend_gr on 2006-11-06
It seems that there are various users that wish to use the MIGHTY kxdocker in their (gnome) ubuntu.

First of all install it using this very good supriyadisw how-to: [http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake](http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake)

After you are successfully done, you should end up with an ugly "windowed" kxdocker, with your plugin choices only.

**1.** To remove the window and end up with a smooth kxdocker:

[LIST]
Open configurator from the tray icon, then navigate to the window tab, and there make the following changes:

IN THE DESKTOP SQUARE:
[*]"auto send the docker to background layer" (unchecked)
[*]"auto raise the dock on events" (checked)
[*]"enable fast hiding" (unchecked)
[*]"Raise the dock whenever you touch the left corner" (unchecked)*
[*]"Raise ................................right corner" (unchecked)*
[*]"Hide the dock after" (whatever you like I use 1200ms)
[*]"Wait before raise the dock" (20ms)
[*]"Desktop shrink (whatever you want-i use the default value)

Store configuration now and close, you might need to restart kxdocker to see the changes (i can't recall).

* --> It has to do with your beryl settings, in my beryl config, I have nothing set to right corner gesture, but it is safer to leave both unchecked for start, then you can experiment. If you mess up the config KILL the process do not exit through the tray, or the messed up config will be saved.
[/LIST]

**2** Now remove all the malfunctioning plug-in you thought you needed. ;). Simply right-click and "remove this". (usual things are the pager,clock,trash,kde menu and others)

**3** You are now left with a few icons, don't worry let's populate this dock: simply drag and drop ALL (yes all) the apps you use at least once a week! Don't worry you will manage them... I 'll tell you how later.

**4** OK you should have a chaos over there... let's put some order. For example let's start with the video apps, they should all be in one spot (just scroll the mouse over one and other should appear). 
You should write down all the apps you have put there and make up your mind how many MAIN categories of computer tasks are in your mind, For simplicity let's suppose there are only 6 (personally I use 15) - PLACES/ACCESSORIES/INTERNET/IMAGE/MULTIMEDIA - now let's put all our apps in one of those categories, keep writing down, computer-home-search under PLACES, Firefox-thunderbird-xchat-Torrent Swapper-Ekiga under INTERNET and so on.
When your are done with your notes let's go on with the actual job.
Open Configurator through the tray icon. There navigate to rolling icons and choose one by one all your apps to configure. In the dialog there change the TEXT display to your liking, the rolling icon group to what it should be according to your notes (app category) and in the matches tab change TITLE match (or create one) with the TITLE that shows when you open that application. Remember to change ACTIONS to what they should be if they are malfunctioning. Also consider changing the icons for your apps with a nicer icon.

**5** NOw let's create a Trash. Remove he trash plugin if you haven't done so. Create a new rolling icon through configurator, place a full TRASH icon (no workaround still known to me for changing icons depending on the trash status) and empty file to the trash so you are happy ;). Go to actions and set the first one to "nautilus --no-desktop Trash:" and the second to "mv "%1" ~/.Trash". This way when you drag and drop a file over that icon it will be moved to your trash! Actually when you drag and drop a video over your mplayer icon it will start playing it (!) so it is a general thing. We only did a workaround for a gnome trash here.

I hope it works for you, I will be editing this tutorial, to become better as it is lengthy...

WORKAROUNDS: 
*Whenever you wish to save a config open configurator and "store configuration now". Whenever you close the kxdocker through the tray it is automatically saved.
*If you make sth you don't wish to be stored, do not close the kxdocker through the tray icon, kill it!
*Remember to close kxdocker before logging out through the tray, so you won't loose the configs you 've made during the session.

P.S.: Sorry for the length of the tutorial, but that's the main reason for no such how-to's for kxdockers, it is a complex thing to do. ;)

P.S.2.: Let me know if it worked for you, my only joy is the felling I helped somebody...;)

Here is a screenshot so you will get an idea how it should look. (image quality is poor but it should do the trick)

---

### Post by jogebau on 2006-11-06
Hi, remember me from the other thread?

Got it installed and I am configurating it now. Ive got a few issues.

1. Icons that I put there have the highres icon i assign to them, but icons of running applications have some really ugly lowres icons. if i change that and restart theyve got the lowres icon again.

anything else can wait, im tired

thanks anyway

---

### Post by turbojugend_gr on 2006-11-06
@jogebau: You have to do all the steps, what you are saying is in step 4. If you do this nicely you will end up with your icons having an arrow under them when the app is running. It has to do with the "matches" thing. I suggest you should readd through the post, you should be allright. Of course there should be apps, you use very rarely and therefore you didn't create a launcher, those would end up with their /usr/pixmaps icon on the dock, for those I just changed the icons.

---

### Post by jogebau on 2006-11-07
Hi, again, how do I add a seperator (like these double lines)?

---

### Post by jogebau on 2006-11-07
Dont worry, worked it out myself:

Just add any Icon to the bar, reset its class to GSeparator, leave its Iconname empty and delete any actions.

CU

---

### Post by mdwuznik on 2006-11-07
Do you guys mind posting your full config for the use of other people ?
Configuring kxdocker form scratch is fairly exhausting, so maybe we could benefit from your configs and only tune them a bit to suit our needs fully ?

Cheers
Michal

---

### Post by turbojugend_gr on 2006-11-07
@mdwuznik: M8 what you say is like a two-bladed knife, it can do your job quicker, but it may hurt you as well... I would but then you wouldn't have the experience to configure it according to your needs, therefore you would spam posts asking for help, it shouldn't take more than 1 hour, and you wouldn't have learned how to organize your thought too.

Although if you feel I am talking crap, you can google up a conf, I 've seen some of 'em (actually I think the official kxdocker site has a pilot one), but never seen a how-to. That's why I made this and didn't post my config for others. The fun is in creating your system your way, as a linux user that's what I love. I am sorry if you feel I am mentoring you, that's not my point.

Long story short, I believe that this docker is superb,  because it gives you so much freedom, it's like it passes you to another pc world, the one linux users like, the one that thought is not imprisoned in stanzas, you will feel so if you create it your self too...

P.S: Yes I know it is "very-very" similar to the OSX docker, that's the think, this one is not preconfigured, oh and the most important part, it's for linux... ;)

---

### Post by foofightrs777 on 2006-11-08
I'm trying this under Edgy.  When I make I get the error:

```

 Entering directory `/home/craig/Desktop/kxdocker-1.1.4a/src'
/bin/bash ../libtool --silent --mode=link --tag=CXX g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common    -o libKXMouse.la -rpath /usr/lib/kxdocker -avoid-version -module -L/usr/share/qt3/lib -L/usr/lib    xeplugin_mouse.lo -lXtst libkxdocker.la 
/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make[2]: *** [libKXMouse.la] Error 1
make[2]: Leaving directory `/home/craig/Desktop/kxdocker-1.1.4a/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/craig/Desktop/kxdocker-1.1.4a'
make: *** [all] Error 2

```


Any ideas on what's wrong?  Is this dapper only?

---

### Post by turbojugend_gr on 2006-11-09
Nope it ain't dapper only, I use edgy, have you installed all the deps as Supriyadisw sais?

---

### Post by foofightrs777 on 2006-11-09
Yes, I was able to install the main package so I am able to open the "basic" kxDocker with window borders.  

I have been unable however to compile the newest "useful" packages  (kxdocker-resources-version.x.x.tar.bz2, kxdocker-configurator-version.x.x.tar.bz2, kxdocker-dcop-version.x.x.tar.bz2, kxdocker-i18n-version.x.x.tar.bz2 kxdocker-trayiconlogger-version.x.x.tar.bz2).  I need these packages if I am to continue to your tutorial.  I'm running into problems during the make.
When I try to make the configurator I get an error similar to this one for several pages:

```
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:259: error: invalid use of undefined type 'struct XSConfigurations'

```


Also, on the linked tutorial page there are typos in the dependencies.  build-essential was spelled incorrectly.  There's another package as well its listed as '*-driver'.  The proper package name is now '*-drivers'.

---

### Post by turbojugend_gr on 2006-11-09
I never used the site, I saw it after I managed to compile, so I din't notice if there are any typos, it just did exactly what I did so instead of posting a how-to I linked.

As for the the tarballs you are trying to compile you need to use the prefixes, and the optional libs, do you?

If not use them, supriyadisw does too, oh and btw it would be better if you asked for questions there, or search the comments, they have many issues covered.

Regards, TJ

---

### Post by jogebau on 2006-11-11
Hi, its me again... did everything like you told me to... been using it for a few days, now ive got a prob:

Sometimes when i start kxdocker it ends itself againjust after loading itself.

Is that a common bug or is it abnormal behaviour?

---

### Post by jogebau on 2006-11-11
Seems like I solved that myself. Inoticed ist was always crashing when it started automatically with the session, so now I start it through a script with a 5 second delay. 

probably has to be started after beryl...

---

### Post by turbojugend_gr on 2006-11-11
Yes it is a known bug.

---

### Post by aniskasa on 2006-11-15
I did the commands:

sudo apt-get install kxdocker kxdocker-data
sudo apt-get install build-essensial xlibs-dev libqt3-mt-dev libqt3-compat-header kdelibs4-dev kdebase-dev

(minus the typos on the latter)

Then compiled the configurator (In kxdocker-configurator-1.0.2 -dir I did ./configure, make, sudo make install) and started kxdocker.

Now there appeared one icon, a tux apple on a gray background. The right-click pop-up only has a possibility to configure that icon, but there is no general configuration option.

What should I do to get the configurator work?

---

### Post by turbojugend_gr on 2006-11-16
There should be an icon in your **system tray** that shows a tux-apple, if it doesn't you haven't installed the plugin right. Anyway you right-click that icon and select configurator

---

### Post by turbojugend_gr on 2006-11-16
@Aniskasa: Are you sure you have installed the kxdocker-trayiconlogger-version.x.x.tar.bz2 package properly ? If not retry. It's supposed to be the one that should give you the tray icon.

---

### Post by aniskasa on 2006-11-17
> **turbojugend_gr said:**
> @Aniskasa: Are you sure you have installed the kxdocker-trayiconlogger-version.x.x.tar.bz2 package properly ? If not retry. It's supposed to be the one that should give you the tray icon.

No, I'm not sure... :) Thanks.

edit: Is it possible to change the mouse over text style? It looks quite pixelated...

---

### Post by turbojugend_gr on 2006-11-17
If I get it right you did it right?

Back to your last question now, it is possible: go to theme tab in configurator and in overtext theme path choose the one you like. There you can also change the the Font used for the mouseovertext.

---

### Post by aniskasa on 2006-11-17
Yes, I got it installed properly and I'm now configuring it. Got the text changed, too.

One other thing: is there a system tray -plugin, or some other way to get the system tray to the docker?

---

### Post by turbojugend_gr on 2006-11-17
I believe not, and even if it where I would strongly suggest you not to use it, cause if kxdocker crash you can't manage your system at all. Actually MacOS X dock doesn't have a tray either.

---

### Post by aniskasa on 2006-11-17
Good point. It's just that some programs tend to put themselves to the system tray, like Skype. Would be nice to be able to command that prog too from the kxdocker.

---

### Post by gejr on 2006-11-22
I get a million of errors running it. And I think I followed the guide to its fullest, with no errors or warnings at all(which surprised me:). Let me show you what errors I get:

[THESE]("http://www.geirola.net/error.txt") are the errors i get:


Any suggestions will be highly appreciated :) The docker starts, and I can access the configuration menu through the tray icon, but the whole thing seems to crash after 20 seconds or so.

The answer to my problem was solved by reading this thread: 

[http://www.ubuntuforums.org/showthread.php?t=232128]("http://www.ubuntuforums.org/showthread.php?t=232128")

---

### Post by turbojugend_gr on 2006-11-22
IF understand right, you ae now happily using it right? If yes then I hope this how-to will help you to use it to the fullest.

P.S.: From what I 've seen you had too many plugin there, which are not to be used under gnome. This goes to most users, keep the plugins number low, the lower the better. You can install 'em after you have a working dock, and a backup of it's config ;).

---

### Post by kpolice on 2006-11-23
THX for the how-to, I am running kxdocker with GNOME now :D

---

### Post by gejr on 2006-11-23
Yes, I managed to install it, but I didn't like it too much. I think kiba-dock was easier to configure and easier to set up. + It didn't bug as much in my system. But I guess that's a matter of preference:)

This is my kiba-dock:

[ATTACH]19868[/ATTACH]

---

### Post by turbojugend_gr on 2006-11-23
Whatever suits you m8, I can't wait for kiba to introduce an "on drop command launcher" and a task manager, then I 'll definatelly switch too ,as kiba has awesome physics and is easily configarble.

The thing is that it would take more than a year, my guess, to match the superior kxdocker, not task manager, no docking, no plugins no nothing, it is only an ion docker, instead of having icons on your desktops you hold 'em on kiba and you get to play with them (god that's amuzing, I spend about 2 weeks playing with it-plain addiction),but nothinhg more, so for now there's chaotic difference betweeen the two apps, the one is a perfect panel replacement (kxdocker) and the other is only an "icon holder" (kiba).

---

### Post by userundefine on 2007-01-01
I'm having problems getting this to be stable in any way.  I start with step 1, and can remove the 'window' around the dock, save the configuration file and restart and that works.  But after that, I can't get anything to stay the way I've changed it.  After I remove items from the dock, I can't add my own to it via drag & drop.  Then, when I restart the dock, all the icons I deleted are back.  What's more, when I start it from CLI I get nothing but an outspit of errors.

```
kxdocker_conf_default.xml  kxdocker_conf.xml
zach@nomadsland:~$ sudo cp /usr/share/apps/kxdocker/kxdocker_conf_default.xml /usr/share/apps/kxdocker/kxdocker_conf.xml 
zach@nomadsland:~$ X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3e00827
kxdocker: WARNING: saving xml configuration...

user@ubuntu-desktop:~$ kxdocker &
[1] 13652
user@ubuntu-desktop:~$ KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: loading xml...
kxdocker: WARNING: saving xml configuration to backup configuration...
kxdocker: WARNING: loading external xml configurations: addons_50_configurator.xml
kxdocker: WARNING: loading external xml configurations: addons_50_thememanager.xml
kxdocker: WARNING: loading external xml configurations: addons_70_bluetooth.xml
kxdocker: WARNING: loading external xml configurations: addons_90_trayiconlogger.xml
kxdocker: WARNING: loading external xml configurations: sensor_gaclock.xml
kxdocker: WARNING: loading external xml configurations: sensor_gamarok.xml
kxdocker: WARNING: loading external xml configurations: sensor_gapager.xml
kxdocker: WARNING: loading external xml configurations: sensor_gbattery.xml
kxdocker: WARNING: loading external xml configurations: sensor_gdate.xml
kxdocker: WARNING: loading external xml configurations: sensor_gmail.xml
kxdocker: WARNING: loading external xml configurations: sensor_gnetio.xml
kxdocker: WARNING: loading external xml configurations: sensor_gpipe.xml
kxdocker: WARNING: loading external xml configurations: sensor_gthrottle.xml
kxdocker: WARNING: loading external xml configurations: sensor_gtrash.xml
kxdocker: WARNING: loading external xml configurations: sensor_ipcontrack.xml
kxdocker: WARNING: loading plugins...
kxdocker: WARNING: xeplugin_register(xMatrix)
kxdocker: WARNING: xeplugin_register(xConfigurator)
kxdocker: WARNING: xeplugin_register(xGDocker)
kxdocker: WARNING: xeplugin_register(xCommand)
kxdocker: WARNING: xeplugin_register(xARP)
kxdocker: WARNING: xeplugin_register(xTaskManager)
kxdocker: WARNING: xeplugin_register(xMounts)
kxdocker: WARNING: xeplugin_register(xAnimator)
kxdocker: WARNING: xeplugin_register(xMouse)
kxdocker: WARNING: xeplugin_register(DCOP)
kxdocker: WARNING: xeplugin_register(xThemeManager)
kxdocker: WARNING: xeplugin_register(xBluetooth)
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3e001fb
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
kxdocker: WARNING: xeplugin_register(GNetIO)
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
kxdocker: WARNING: Plugins loaded:
kxdocker: WARNING: [0] xMatrix
kxdocker: WARNING: [1] xConfigurator
kxdocker: WARNING: [2] xGDocker
kxdocker: WARNING: [3] xCommand
kxdocker: WARNING: [4] xARP
kxdocker: WARNING: [5] xTaskManager
kxdocker: WARNING: [6] xMounts
kxdocker: WARNING: [7] xAnimator
kxdocker: WARNING: [8] xMouse
kxdocker: WARNING: [9] DCOP
kxdocker: WARNING: [10] xThemeManager
kxdocker: WARNING: [11] xBluetooth
kxdocker: WARNING: [12] xTray
kxdocker: WARNING: [13] GPipe
kxdocker: WARNING: [14] GAClock
kxdocker: WARNING: [15] GAmarok
kxdocker: WARNING: [16] GAPager
kxdocker: WARNING: [17] GBattery
kxdocker: WARNING: [18] GDate
kxdocker: WARNING: [19] GMail
kxdocker: WARNING: [20] GNetIO
kxdocker: WARNING: [21] GThrottle
kxdocker: WARNING: [22] GTrash
kxdocker: WARNING: [23] GIPContrack
kxdocker: WARNING: [24] xPillow
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
/usr/lib/kxdocker/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGSeparator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGSeparator.so: cannot open shared object file: No such file or directory
QImage::smoothScale: Image is a null image
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libxTask.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libxTask.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibxTask.so: cannot open shared object file: No such file or directory
QImage::smoothScale: Image is a null image
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
QImage::smoothScale: Image is a null image
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
QImage::smoothScale: Image is a null image
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
QImage::smoothScale: Image is a null image
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
QImage::smoothScale: Image is a null image
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/libGMount.so: cannot open shared object file: No such file or directory
/usr/lib/kxdocker/liblibGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libGMount.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibGMount.so: cannot open shared object file: No such file or directory
Device is not available: No such device
kxdocker: WARNING: Going to background...
dcop: removing anonymous-13652
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3e0063e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3e00724

```
I've tried different kxdocker_conf.xml files, and they do nothing different for me.  Any ideas?

---

### Post by habtish on 2007-01-04
> **turbojugend_gr said:**
> It seems that there are various users that wish to use the MIGHTY kxdocker in their (gnome) ubuntu.

First of all install it using this very good supriyadisw how-to: [http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake](http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake)

After you are successfully done, you should end up with an ugly "windowed" kxdocker, with your plugin choices only.

**1.** To remove the window and end up with a smooth kxdocker:
[LIST]
[*]Open configurator from the tray icon, then navigate to the window tab, and there make the following changes:

IN THE DESKTOP SQUARE:
[*]"auto send the docker to background layer" (unchecked)
[*]"auto raise the dock on events" (checked)
[*]"enable fast hiding" (unchecked)
[*]"Raise the dock whenever you touch the left corner" (unchecked)*
[*]"Raise ................................right corner" (unchecked)*
[*]"Hide the dock after" (whatever you like I use 1200ms)
[*]"Wait before raise the dock" (20ms)
[*]"Desktop shrink (whatever you want-i use the default value)

Store configuration now and close, you might need to restart kxdocker to see the changes (i can't recall).

* --> It has to do with your beryl settings, in my beryl config, I have nothing set to right corner gesture, but it is safer to leave both unchecked for start, then you can experiment. If you mess up the config KILL the process do not exit through the tray, or the messed up config will be saved.[/LIST]
**2** Now remove all the malfunctioning plug-in you thought you needed. ;). Simply right-click and "remove this". (usual things are the pager,clock,trash,kde menu and others)

**3** You are now left with a few icons, don't worry let's populate this dock: simply drag and drop ALL (yes all) the apps you use at least once a week! Don't worry you will manage them... I 'll tell you how later.


Am afraid I am getting stuck here. I followed the steps on the linked page to compile from source. Also compiled things like trash,configurator,trayiconlogger,resources...
and I came here and started following this howto.. Now when you say to "drag and drop" icons.. do we drag and drop them in the dock?? Because nothing is happening for me when I drag and drop applications into the dock. the only remaining Icon I have on it is the trash and it actually deleted an Icon when I tried to drop it in the docker and ended up dropping it in the trash...

Building this thing from source sorta took some time and I feel like a fool having come this far and getting stuck at such a step.. please elaborate/help

---

### Post by habtish on 2007-01-04
also forgot to put this up on my post, when I am trying to drag icons into the dock, this is what is happening in the terminal
```
Grabbing the mouse failed with "AlreadyGrabbed"

```

---

### Post by lcaley on 2007-01-05
I'm having trouble compiling/installing any of the extra packages. I have the main program installed. I have a tux apple with a gray background, but when I mouse over it, it gets a big black bar, about 1/4 of my screen behind it. I assume because I haven't installed any extra packages yet. This is a sample of the error that I get when I compile:

xeplugin_trayiconlogger.cpp:42: error: 'XEObject' was not declared in this scope
xeplugin_trayiconlogger.cpp:44: error: 'XEObject' is not a class or namespace
xeplugin_trayiconlogger.cpp: In destructor 'virtual XEPlugin_TrayIconLogger::~XE
Plugin_TrayIconLogger()':
xeplugin_trayiconlogger.cpp:57: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp: In member function 'void XEPlugin_TrayIconLogger::x
Setup()':
xeplugin_trayiconlogger.cpp:86: error: 'xWarningMsg' was not declared in this sc
ope
xeplugin_trayiconlogger.cpp:89: error: 'XEConfiguration' was not declared in thi
s scope
xeplugin_trayiconlogger.cpp:89: error: 'Configurator' was not declared in this s
cope
xeplugin_trayiconlogger.cpp:89: error: expected primary-expression before ')' to
ken
xeplugin_trayiconlogger.cpp:89: error: expected `;' before 'XEObject'
xeplugin_trayiconlogger.cpp:130: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:165: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:165: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:169: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:172: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:174: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:177: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:180: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:182: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp: In member function 'void XEPlugin_TrayIconLogger::f
etchDefaultParameters()':
xeplugin_trayiconlogger.cpp:314: error: invalid use of undefined type 'struct XS
Configurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurat
ions'
xeplugin_trayiconlogger.cpp:317: error: invalid use of undefined type 'struct XS
Configurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurat
ions'
xeplugin_trayiconlogger.cpp:319: error: invalid use of undefined type 'struct XS
Configurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurat
ions'
xeplugin_trayiconlogger.cpp:322: error: invalid use of undefined type 'struct XS
Configurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurat
ions'
xeplugin_trayiconlogger.cpp:330: error: 'QDomDocument' was not declared in this
scope
xeplugin_trayiconlogger.cpp:330: error: expected `;' before 'doc'
xeplugin_trayiconlogger.cpp:332: error: 'QDomElement' was not declared in this s
cope
xeplugin_trayiconlogger.cpp:332: error: expected `;' before 'fakeRoot'
/usr/share/qt3/include/qlabel.h:152: error: 'QSimpleRichText* QLabel::doc' is pr
ivate
xeplugin_trayiconlogger.cpp:334: error: within this context
xeplugin_trayiconlogger.cpp:334: error: request for member 'appendChild' in '((X
EPlugin_TrayIconLogger*)this)->XEPlugin_TrayIconLogger::<anonymous>.KSystemTray:
:<anonymous>.QLabel::doc', which is of non-class type 'QSimpleRichText*'
xeplugin_trayiconlogger.cpp:334: error: 'fakeRoot' was not declared in this scop
e
xeplugin_trayiconlogger.cpp:336: error: expected `;' before 'CreatingCfg'
xeplugin_trayiconlogger.cpp:345: error: 'CreatingCfg' was not declared in this s
cope
xeplugin_trayiconlogger.cpp:348: error: 'CreatingCfg' was not declared in this s
cope
xeplugin_trayiconlogger.cpp:349: error: invalid use of undefined type 'struct XS
Configurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurat                 ions'
xeplugin_trayiconlogger.cpp: In member function 'void XEPlugin_TrayIconLogger::x                 SetupParameter(QString, QString)':
xeplugin_trayiconlogger.cpp:368: error: invalid use of undefined type 'struct XS                 Configurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurat                 ions'
xeplugin_trayiconlogger.cpp:370: error: invalid use of undefined type 'struct XS                 Configurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurat                 ions'
xeplugin_trayiconlogger.cpp:373: error: invalid use of undefined type 'struct XS                 Configurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurat                 ions'
make[2]: *** [xeplugin_trayiconlogger.lo] Error 1
make[2]: Leaving directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0/                 src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0'
make: *** [all] Error 2
lcaley@lcaley-laptop:~/kxdocker/kxdocker-trayiconlogger-1.0.0$ make
Makefile:854: warning: overriding commands for target `clean-bcheck'
Makefile:817: warning: ignoring old commands for target `clean-bcheck'
Makefile:859: warning: overriding commands for target `bcheck-am'
Makefile:822: warning: ignoring old commands for target `bcheck-am'
make  all-recursive
make[1]: Entering directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0'
Makefile:854: warning: overriding commands for target `clean-bcheck'
Makefile:817: warning: ignoring old commands for target `clean-bcheck'
Makefile:859: warning: overriding commands for target `bcheck-am'
Makefile:822: warning: ignoring old commands for target `bcheck-am'
Making all in doc
make[2]: Entering directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0/doc'
Making all in .
make[3]: Entering directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0/doc'
Making all in en
make[3]: Entering directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0/doc/en'
make[2]: Leaving directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0/doc'
Making all in po
make[2]: Entering directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0/po'
Making all in src
make[2]: Entering directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0/src'
if /bin/bash ../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.  -I/usr/include  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common  -MT xeplugin_trayiconlogger.lo -MD -MP -MF ".deps/xeplugin_trayiconlogger.Tpo" -c -o xeplugin_trayiconlogger.lo xeplugin_trayiconlogger.cpp; \
        then mv -f ".deps/xeplugin_trayiconlogger.Tpo" ".deps/xeplugin_trayiconlogger.Plo"; else rm -f ".deps/xeplugin_trayiconlogger.Tpo"; exit 1; fi
xeplugin_trayiconlogger.cpp: In constructor 'XEPlugin_TrayIconLogger::XEPlugin_TrayIconLogger(QWidget*, const char*)':
xeplugin_trayiconlogger.cpp:42: error: 'XEObject' was not declared in this scope
xeplugin_trayiconlogger.cpp:44: error: 'XEObject' is not a class or namespace
xeplugin_trayiconlogger.cpp: In destructor 'virtual XEPlugin_TrayIconLogger::~XEPlugin_TrayIconLogger()':
xeplugin_trayiconlogger.cpp:57: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp: In member function 'void XEPlugin_TrayIconLogger::xSetup()':
xeplugin_trayiconlogger.cpp:86: error: 'xWarningMsg' was not declared in this scope
xeplugin_trayiconlogger.cpp:89: error: 'XEConfiguration' was not declared in this scope
xeplugin_trayiconlogger.cpp:89: error: 'Configurator' was not declared in this scope
xeplugin_trayiconlogger.cpp:89: error: expected primary-expression before ')' token
xeplugin_trayiconlogger.cpp:89: error: expected `;' before 'XEObject'
xeplugin_trayiconlogger.cpp:130: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:165: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:165: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:169: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:172: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:174: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:177: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:180: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp:182: error: 'XEObject' has not been declared
xeplugin_trayiconlogger.cpp: In member function 'void XEPlugin_TrayIconLogger::fetchDefaultParameters()':
xeplugin_trayiconlogger.cpp:314: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurations'
xeplugin_trayiconlogger.cpp:317: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurations'
xeplugin_trayiconlogger.cpp:319: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurations'
xeplugin_trayiconlogger.cpp:322: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurations'
xeplugin_trayiconlogger.cpp:330: error: 'QDomDocument' was not declared in this scope
xeplugin_trayiconlogger.cpp:330: error: expected `;' before 'doc'
xeplugin_trayiconlogger.cpp:332: error: 'QDomElement' was not declared in this scope
xeplugin_trayiconlogger.cpp:332: error: expected `;' before 'fakeRoot'
/usr/share/qt3/include/qlabel.h:152: error: 'QSimpleRichText* QLabel::doc' is private
xeplugin_trayiconlogger.cpp:334: error: within this context
xeplugin_trayiconlogger.cpp:334: error: request for member 'appendChild' in '((XEPlugin_TrayIconLogger*)this)->XEPlugin_TrayIconLogger::<anonymous>.KSystemTray::<anonymous>.QLabel::doc', which is of non-class type 'QSimpleRichText*'
xeplugin_trayiconlogger.cpp:334: error: 'fakeRoot' was not declared in this scope
xeplugin_trayiconlogger.cpp:336: error: expected `;' before 'CreatingCfg'
xeplugin_trayiconlogger.cpp:345: error: 'CreatingCfg' was not declared in this scope
xeplugin_trayiconlogger.cpp:348: error: 'CreatingCfg' was not declared in this scope
xeplugin_trayiconlogger.cpp:349: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurations'
xeplugin_trayiconlogger.cpp: In member function 'void XEPlugin_TrayIconLogger::xSetupParameter(QString, QString)':
xeplugin_trayiconlogger.cpp:368: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurations'
xeplugin_trayiconlogger.cpp:370: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurations'
xeplugin_trayiconlogger.cpp:373: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_trayiconlogger.h:50: error: forward declaration of 'struct XSConfigurations'
make[2]: *** [xeplugin_trayiconlogger.lo] Error 1
make[2]: Leaving directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lcaley/kxdocker/kxdocker-trayiconlogger-1.0.0'
make: *** [all] Error 2

---

### Post by turbojugend_gr on 2007-01-06
It seems you left over some plugins.... can you name all the plugins you installed?

---

### Post by chrisg0619 on 2007-01-07
> **habtish said:**
> also forgot to put this up on my post, when I am trying to drag icons into the dock, this is what is happening in the terminal
```
Grabbing the mouse failed with "AlreadyGrabbed"

```
I'm having the same problem!

---

### Post by thewump on 2007-01-08
> **userundefine said:**
> I'm having problems getting this to be stable in any way.  I start with step 1, and can remove the 'window' around the dock, save the configuration file and restart and that works.  But after that, I can't get anything to stay the way I've changed it.  After I remove items from the dock, I can't add my own to it via drag & drop.  Then, when I restart the dock, all the icons I deleted are back.  What's more, when I start it from CLI I get nothing but an outspit of errors.


I'm having the same issue with re-appearing icons.  Any that I find in the config where I can set them to "disabled" are fine, but things like the power status, and trash can just won't go away.

Anyone?  

Keith

---

### Post by ajmorris on 2007-01-13
i have a problem that when i drag stuff to the dock nothing appears to happen. If then go to configure and select the icons tab and add icon, the stuff i dragged to it appears there. The only problem then is that they try to run from /home/user/%u so they don't work. Also when i mouseover on the dock a black box appears arround it.

Any ideas?

---

### Post by ajmorris on 2007-01-13
> **gejr said:**
> Yes, I managed to install it, but I didn't like it too much. I think kiba-dock was easier to configure and easier to set up. + It didn't bug as much in my system. But I guess that's a matter of preference:)

This is my kiba-dock:

[ATTACH]19868[/ATTACH]

for this i get:  kiba-dock
GTK Accessibility Module initialized
Segmentation fault (core dumped)


when i try to run it. :(

---

### Post by s04bf1c2 on 2007-01-15
Hello, thanks for your guide it has proved very helpful. 

However i have 2 questions, turbojuend  says that for certain apps there process name is different and therefore with task manager they're icon shall be different. ie firefox vs firefox-bin. I've added all my icons to the /usr/share/apps/kxdocker/themes/icons dir (even) firefox-bin but to no avail, firefox still always uses its standard logo rather than my preferred one.

Also turbojuend supplies a picture of his dock where open applications do not create another icon in the task manager, the arrow shows its open below its (single) icon.

Can anyone point me in the right direction?

---

### Post by turbojugend_gr on 2007-01-15
First of all pardon me for my absense, but I am taking my uni exams at this period.

now **@ all of you having issues when you drag icons that do not appear**, try draggin the app you won and dropping it on an existing icon on the dock, then open the configurator and change that apps group to sth else (as always the groups are representented with 1 slot on the dock with rolling icons one "after" the other, scroll over on to see the next). Restart kxdocker (quit from the systray then start it over) and the new icon group should appear.

**@s04bf1c2** 1. right click on the icon representing firefox let's say, and then choose configure. On the dialog that appears near the bottom there is the icon used, click on it and select any icon you wish from your hard drive, that should stick there if you close kxdocker gracefully (quit using the choice on the system tray menu, when you click the "linux" apple on the tray).
2. You have to let kxodcker know which app is running when you click on any icon, the usual case is that kxodkcer won't recognize the app, a clever way to do that would be... open the app that is not recongnized (and thus is shown again on the left of the dock) right click there and choose "keep in dock", then simply remove the existing icon/launcher for that app, and configure the new icon to be in the rolling icons group you wish it to , restart kxdocker and all should be fine. A better but more complex way would be to use the matches tab (on the configure icon/launcher dialog) there you should put the name that is shown on the window bar when it runs, or maybe even it's dcop and class, you can also copy and paste those from the generated icon on the very left of the kxodcker (the one I told you to keep in dock previously) configure/dialog/matches for every app that behaves this way.

Plz post here whether that worked for youse or not, I will find sometime to read them the following days.

Best Regards, TJ.

P.S.: I will update the guide as soon as I finish my uni exams, so keep in touch. Also I encourage you to avoid any scripts on the web for automatic installation of kxdocker, since that won't let you choose what plugins you may use, and therefore you won't be able to understand how kxdocker works later on.

P.S.2: Those having issues with omni-present plugins, plz let me know what are the full list of the plugins you installed, and also if you used a srcipt for the installation. Finally you should know that the plugins should be deleted from the alias screen if they continue to appear despite you telling them not to. A nice way to that would be by not including those plugins to installation, try deleteing their folders, or even better re-install kxdocker ommiting the bad behaved plugins, (remember to **keep your current config file**) and it shouldn't be that much of hussle.

---

### Post by s04bf1c2 on 2007-01-16
Thanks a million. Kxdocker now runs the way i wish :D

---

### Post by jperrine088 on 2007-01-16
yeah im having the same problem with the giant black box when you scroll over kxdocker. I had it working perfectly fine in Suse, but i decided to make the switch over to a debain based distro. I installed all the kde development files necessary, and compiled kxdocker without any problems. I just cant seem to get to the bottom of this problem..

---

### Post by pingvin on 2007-02-14
At last, someone with exactly the same problem as me!
I had it working just fine with Dapper, but now I've upgraded to Edgy I also get the horrible black box you describe :confused: Same problem with KDE also.
If anyone has any ideas please let me know.
Many thanks

Mike

---

### Post by eitan_a on 2007-02-15
kxdocker is awesome.  I'd like to get thumbnail grabbing working correctly (to get live previews of windows in the taskbar) but it's always a black box, only once did I see the window correctly.  Does this have something to do with it being gnome, and not kde?  I'd like some help going through the taskmanager code and fix this nagging issue.  Thanks a bunch!

---

### Post by pingvin on 2007-02-16
It's probably of no consolation but we did resolve the black box issue (it was a huge black box across the whole of the bottom of the screen whenever kxdocker did anything) and the answer is yes it can run in Gnome but in needs a composite window manager (ie. Beryl). In Dapper I had thumbnail previews working fine, though they weren't live updates, ie. it would take a thumbnail of each window when it was maximised, started, etc but not constantly update it. Apparently the actual Mac Dock shows the film minimised when you shrink the movie player to the tray, which sounds very cool.

Good luck with that, in conclusion I don't think it's a Gnome thing.

Mike

---

### Post by kobewan on 2007-02-17
I don't think that it's a Compiz thing. The new version of KXDocker has support for a composite window manager (and it does work in Beryl), but the sie says that it should also support fake transparency for regular window managers. I assume that if we can figure out the right combination of settings and plug-ins to use, we can get rid of that black box.

Of course, I don't have any solid proof of this, but right after I run 'kxdocker' in Terminal, it prints this:

KXDocker Will use Composite Extensions!

I'm going to try tweaking it some more and getting rid of that black box.

---

### Post by eitan_a on 2007-02-18
That's great man, good luck.  Also, if you can, can you try to decrease the icon size in the task manager?

---

### Post by pingvin on 2007-02-20
Okay here is one solution, but it's a complete cop-out: go back to Dapper's 0.39 version from the repos. It's even harder to configure, but atleast it doesn't even try to do real transparency, so no horrible black box.
Fraid I had no luck atall with 1.1.4

Mike

---

### Post by petersjm on 2007-04-17
Great howto. Got it working on Edgy with Beryl. I've got two questions, though.

1. If auto-hide is on, it sinks below the screen (as normal), but when I touch the screen edge, it does not rise again so I have to killall and restart it. Any clues?

2. Is there a plugin, or a way to get the K-Menu on KXDocker? The original post says about removing all the broken plugins like trash etc, and also mentions "KDE Menu", but my docker didn't have one - did I miss a plugin?

Thanks for you help guys :-)

---

### Post by turbojugend_gr on 2007-04-17
Hi there, thank you fpr your praise. Now for the hiding part, I click on the apple-penguin icon, kxdocker has on the sys trray, a simple left click is enought to hide it or reveal it if hidden. I do not use autohide, I prefer clicking there to manage this. It is supposed to work with autohide too.

Now as for the second question, yes most propably you missed the plugin. Download it and install it as you did with all the rest plugins.

---

