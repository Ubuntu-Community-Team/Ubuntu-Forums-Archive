---
title: "How to: Create a complete, snappy and beautiful Ubuntu Desktop"
date: 2009-07-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Labello on 2009-07-10
[img]http://files.getdropbox.com/u/416097/tut/start.png[/img]

In this tutorial I will try to show you how to install and setup a whole ubuntu system. You might ask what is supposed to be so special about it. Special about it is that we will somehow build it "from the ground up". We will start with a very minimalistic installation and will expand the functionality step by step. It will take longer to have a running production system than the normal ubuntu installation via liveCD. But therefore it will be much more customized to fit just your needs which will result in shorter boottime, less ressource consumption and an all in all more responsive system. But we wont stop at the general package and system config. I will show you how to get an effective compiz-configuration that is aiming at workflow without blowing up your PC and an all in all good looking OS that is enyojable to work with.

This is my first tutorial in the Open Source world. I see it like paying back for the great software that I am allowed to use. I have been using Ubuntu since Feisty Fawn (7.04 I think) and I fell in love with it from the first moment on. I did reinstall Ubuntu about uncountable times. Kubuntu, Xubuntu, UbuntuStudio, Linux Mint, CrunchBang Linux and of course the standart Ubuntu. And everytime I came closer to the "Perfect Desktop". I fiddled around with many apps and configs which where aiming at improving my workflow with the whole system. And now I feel somehow ready enough to let you know what my experiments resulted in.

Before you start following this guide you should take a look at the end and browse through my instructions to get a clue what I will be coming up with and whether this fits your needs and taste. Feel free to post some proposals to make it even better. I will add them to this post. 

MOREOVER I ASK YOU TO BACK UP ALL YOUR SENSITIVE DATA! Something might go wrong especially during partitioning and you might get lost in tears afterwards.

Prerequisites:
You should know how to use a commandline and know what repositories are and how to deal with them. Moreover you should have a graphicscard that has full 3D-support and can handle compositing. Therefore a computer not older than four years will do fine in this guide. Then you should be able to connect to the internet during the setup. Best should be a wired connection to make sure that it works flawlessly out of the box.

Terminology:
**BOLD** headlines indicate 100% neccessary steps you must follow!
*ITALIC* headlines indicate steps that are useful but not neccessary.

Applies for:
Ubuntu Jaunty Jackalope 9.04 32Bit (no other machine here to test it)

[size=+1]**1. Download the Jaunty Jackalope Alternate ISO**[/size]
Go [here](http://releases.ubuntu.com/jaunty/) and fetch the ubuntu-9.04-alternate-i386.iso via torrent or direct download. Whichever you prefer. Burn the ISO on CD and boot from it.

[size=+1]**2. Install the basic CLI-System**[/size]
After having chosen your language you should press F4 and choose to install a "Command Line System". This system will provide you with some CLI tools to do pretty a lot of stuff. Upgrading and installing packages and networking(wired) are the most important things we will need for now. Now choose "Install Ubuntu".

[http://files.getdropbox.com/u/416097/tut/1.png](http://files.getdropbox.com/u/416097/tut/1.png)

If you have already used the alternate installation you can savely go to the partitioning chapter. If not we do a step by step installation supported with screenshots (when needed) in the following paragraphs.

Now you are asked to choose your language and location and detect your keyboard-layout. this should be rather easy and is intuitively done by following the instructions on the screen.

Now you are asked to type the hostname. choose a representative hostname and proceed.

[size=+1]**2.1.Partitioning**[/size]
Be careful with this step. It is destructive! Which means that if you do something wrong important data might be erased and you should really have backed it up before starting this guide.
Let's divide up the disk. I will show you my way of doing it, but you are free to choose whatever you want that fits your needs. Choose the "Manual" partitioning method and afterwars you see the following screen:

[http://files.getdropbox.com/u/416097/tut/2.png](http://files.getdropbox.com/u/416097/tut/2.png)

(I must note that the screens of this guide where done with virtualbox and there I don't have that much diskspace. But 40GB should be enough to handle my setup)
If there is no free space delete all partitions that you want to use for this installation. If there already is a swap partition you can leave this of course.
Now select the free space and create a new partition. Enter the size of this partition. This will be our root-partition and therefore all programms will be stored here. 20GB should be a good choice. I would not choose less because if you want to burn DVDs or encode videoclips you might be running out of temporary disk space which would be bad. Our final result won't consume more than 6GB.

[http://files.getdropbox.com/u/416097/tut/3.png](http://files.getdropbox.com/u/416097/tut/3.png)

The "noatime" mountoption should be applied. It should make the filesystem a bit faster. It also could be applied after the installation but this would be a greater effort.
The next two steps should be done with Primary and Beginning. Now we come to the settings. Since we are on Jaunty it might be a good choice to use Ext4 but if you encountered any problems with it or havent use jaunty till now, please choose Ext3. Your setup should look exactly as follows:

[http://files.getdropbox.com/u/416097/tut/4.png](http://files.getdropbox.com/u/416097/tut/4.png)

Now we proceed with the home-partition. You might ask yourself why one would want to use a seperate home-partition. It is rather easy. Linux does not only store your private data like pics and music in the /home-folder. Also many configuration files for your applications like bookmarks and pidgin-accounts. So if you want to reinstall the whole system these config files won't get lost. Also you don't have got to backup your private data before any major system changes.
Create the /home-partition in a size that allows you to create a swap-partition (if you don't already have one) with twice the size of your RAM with the following settings: (Note this partition should be a logical one)

[http://files.getdropbox.com/u/416097/tut/5.png](http://files.getdropbox.com/u/416097/tut/5.png)

Now create a swap partition with the left over disk space and finish partitioning.

[http://files.getdropbox.com/u/416097/tut/6.png](http://files.getdropbox.com/u/416097/tut/6.png)

It should take now some time to install the packages. Afterwards you will be asked to type your full name and account-name and password. This will be the first user of your system that you can use to login after your first reboot. It is pretty similar to the Live-CD. And you can choose whether you want to encrypt your home-directory but this was rather buggy with jaunty and for a save conguration you should not enable encryption. Now the setup will try to fetch some updates from a mirror and install more packages. Congrats! Just one more hit on Return to confirm setting the clock to UTC and then you are finished with the setup!

[size=+1]**3. Update and add packages**[/size]
After having completed the installation and having rebooted you will be confronted with an simple CLI:

[http://files.getdropbox.com/u/416097/tut/7.png](http://files.getdropbox.com/u/416097/tut/7.png)

Please log in with your user created during setup. Now we will first update all installed packages by invoking the following:

```

sudo apt-get update
sudo apt-get upgrade

```

So let's get started and install some really fundamental things:

```

sudo apt-get install xorg gdm gnome-session gnome-terminal gnome-menus gnome-panel nautilus metacity gedit

```

This step might take a bit since there are about 120MB to be downloaded and many dependencies to be installed. But this is okay and truly neccessary. Now we can do a reboot to get some GUI via:

```

sudo shutdown -r now

```

The login screen should appear and let you log in. After log in you should see a rather ugly gnome-desktop without that much functionality. But we are about to change that fact:

[http://files.getdropbox.com/u/416097/tut/8.png](http://files.getdropbox.com/u/416097/tut/8.png)

[size=+1]*4. Setup your needed configurations*[/size]
Now you should be configuring things like your graphics-card or wifi if it is not supported out of the box! Therefore you should use your individual methods which can not be covered in this guide. My ATI FireGL 5200 works fine with the opensource drivers.

[size=+1]**5. Add repositories and update again**[/size]

Now we will be expanding our package sources to obtain some never packages and some additional ones. Type into the terminal:

```

sudo gedit /etc/apt/sources.list

```

And copy there the following lines at the beginning of the file:
IMPORTANT: Especially the repository that contains the newer xorg-packages should be handled carefully. It might break your config and render your PC unbootable. If you know that your xorg config is always very fragile and hard to setup correctly you should not add this repo. But if your graphicscard is detected out of the box then this packages might bring some additional performance.
```

deb http://getswiftfox.com/builds/debian/ unstable non-free #linux optimized Firefox-Build
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ jaunty main #bleeding edge x.org-stuff
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ jaunty main
deb http://ppa.launchpad.net/transmissionbt-nightly/ppa/ubuntu/ jaunty main #bleeding edge transmission
deb-src http://ppa.launchpad.net/transmissionbt-nightly/ppa/ubuntu/ jaunty main
deb http://ppa.launchpad.net/fta/ppa/ubuntu/ jaunty main #repo for thunderbird 3 builds
deb-src http://ppa.launchpad.net/fta/ppa/ubuntu/ jaunty main
deb http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main #gnome-do repo
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main
deb http://packages.medibuntu.org/ jaunty free non-free #medibuntu for more codecs and skype
deb http://ppa.launchpad.net/compiz/ppa/ubuntu jaunty main #never compizbuilds
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main

```
TwiceOver was so kind to fiddle around with the repos and here you can get the signatures. THANKS TWICEOVER!
> **TwiceOver said:**
> 
Here are the keys for the PPAs listed in the OP (add them using the below command and change the 'xxxxx' to the key you want to add:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com xxxxxxxx

xorg-edgers: 8844C542
transmission-nightly: 22202A6B
fta: 0C713DA6
do-core: 77558DD0
compiz: 42C24D89
Pidgin PPA: A1F196A8
Medibuntu: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

It is time for another update:
```

sudo apt-get update
sudo apt-get upgrade

```

Now let's install more packages:
```

sudo apt-get install evince pidgin pidgin-libnotify notify-osd thunderbird-3.0 compiz compizconfig-settings-manager simple-ccsm gnome-do vlc vlc-plugin-pulse brasero pulseaudio padevchooser paprefs pavucontrol flashplugin-nonfree-extrasound rhythmbox transmission bum prelink preload readahead cups openoffice.org gthumb file-roller gdebi

```
Again this will install a huge bunch of stuff and will take some time to complete.

A browser is still missing. Therefore you should first check which architecture you are running on and then choose the appropriate package. You can check it out on the following page:
[http://getswiftfox.com/deb.htm](http://getswiftfox.com/deb.htm)

Now you can use the commandline and apt-get to install the right package.

If you are using a laptop or netbook you might need wifi. To get this use the packages TwiceOver proposed:
> **TwiceOver said:**
> 
Here's some things I also needed.
network-manager <--This is the network and wireless manager
restricted-manager  <--This is the restricted drivers manager

Install these packages by invoking the following:
```
sudo apt-get install network-manager restriced-manager
```
I have got to thank TwiceOver again for his efforts.

[size=+1]*Not really needed but good applications*[/size]
Here are some proposals that I have installed on my machine but it will certainly differ from your needs depending on what you are using your PC for.
```
sudo apt-get install gimp blender inkscape scribus agave kino skype-static-oss nautilus-image-converter
```

Since we are on Jaunty and there are real problems between skype and pulseaudio you should use the OSS-version that will work only when it is the only programm using the soundcard. The nautilus-image-converter package adds two entries in the nautilus contextmanu that come really handy when you want to batchprocess some images to rotate or scale them. Pretty handy stuff.

If you want to convert video-cips I would recommend the following application:
[http://gtk-apps.org/content/show.php/Hyper+Video+Converter?content=88970](http://gtk-apps.org/content/show.php/Hyper+Video+Converter?content=88970)
There you should follow the instructions for "debian & friends" to install it properly.

As you can see I try to use few programms but ones that can do a lot. Like VLC-Player oder the OpenOffice-Suite. This keeps it simple and you don't have got to get familiar with that many apps.

[size=+1]*6. Tweak the system performance*[/size]
First we will tweak the boot-process a bit and the overall performance. To do this invoke the following:
```
sudo bum
```
This will bring up the bootupmanager. Bum is a very handy tool to easily handle the system startup. But it also can make your system inoperable. So be carefull and follow my instructions carefully and exactly. This step will kick out some services that are not needed for ubuntu to work as a normal desktop system. The following screen shows the services that are needed to make the system run flawlessly:

[http://files.getdropbox.com/u/416097/tut/9.png](http://files.getdropbox.com/u/416097/tut/9.png)

All other services can be deactivated without causing you to much trouble. But anyway you are free to leave services that you really need activated. You can also switch them back on via bum anytime you want.

But still there are some more applications that can be left out from starting. But this time after login. To modify them go to "System" -> "Preferences" -> "Startup Applications". As far as I experienced most of them are not really needed and can be switched off except the following two:
-GNOME Keyring Daemon
-GNOME Settings Daemon
Disabling the rest will shave the time after login until your machine is really ready.

Everyone who is running a dualcore CPU or a HT CPU might fancy the next paragraph. The bootprocess can be also done cuncurrently which means that both processors are used simultaneously to run through the init-scripts which will result in a faster boot. This can be achieved easily by doing the following:
```
sudo gedit /etc/default/rcS
```
and now add the following line at the end of the file:
```
CONCURRENCY=shell
```

The next hint can be taken from the following forum post starting with step 3 since we already installed prelink:
[http://ubuntuforums.org/showthread.php?t=1971](http://ubuntuforums.org/showthread.php?t=1971)

Now it might be time for a quick reboot. You should use this boot to profile the boot sequence by doing the following:
1. Wait until Grub shows up and interrupt the countdown now select the entry that boots the latest kernel end hit "e"
2. select the second line and hit "e" again
3. now add the word "profile" at the end of this line as shown in the next screenshot:
[http://files.getdropbox.com/u/416097/tut/10.png](http://files.getdropbox.com/u/416097/tut/10.png)
4. hit return to go back to the last menu
5. press "b" to boot
This boot will take a bit longer than normal but the next ones will be faster than before.

Prelinking and profiling should be done after every major system update. Profiling especially after a kernel update. For now we are finished with the speedups. I think these were the major ones and the ones that have the biggest effect.

[size=+1]**7. Configure the system**[/size]
_1. PulseAudio_
Go to "System" -> "Preferences" -> "Sound" and switch all "Sound Playback" and "Sound Capture" to "PulseAudio Sound Server". For Default Mixer Tracks you should choose the wanted channel is you have any Mediakeys on your Keyboard. Now click on the speaker icon in the gnome-panel to eventually setup some 5.1 sound or switch on micboost and so on.
Close the window and invoke in terminal:
```
pavucontrol
```
This is the most advanced way of managing sound volume and should be prefered over the gnome volume applet.

_2. Again System Startup_
Since we installed some apps and changed some settings after our last boot clean up you should recheck the two locations to be shure no unneccessary apps or daemons are started.

[size=+1]**8. Eyecandy**[/size]
Now it is time to give the system the final touch to make it a pleasure to work with it. I spend hours looking for a good icontheme and a fitting GTK+Metacity theme that look modern and are complete. I came up with the following ones:
_1. Icons_
Mashup is definately one of the best, most complete and neatest icon-sets out there so I chose this one. Here is the Download-Link:
[http://cid-cf78487abe44ffc6.skydrive.live.com/self.aspx/espressivo/Mashup-FIVE-update.tar.bz2](http://cid-cf78487abe44ffc6.skydrive.live.com/self.aspx/espressivo/Mashup-FIVE-update.tar.bz2)
Save the file, go to "System" -> "Preferences" -> "Appearance" and drag the archive from the filemanager into that window. And now build the five different flavours:
```

cd ~/.icons/Mashup
./mashupfive.sh build

```
Now go back to "Appearance" and choose one of the five iconsets.

_2. GTK + Metacity_
First we need to install some engines to make my chosen theme work via:
```

sudo apt-get install gtk2-engines-murrine gtk2-engines

```
And now save the following file for the system-Look:
[http://gnome-look.org/content/download.php?content=107301&id=1&tan=57662189&PHPSESSID=8a4f2bed556a791ee1c437acd479ed14](http://gnome-look.org/content/download.php?content=107301&id=1&tan=57662189&PHPSESSID=8a4f2bed556a791ee1c437acd479ed14)

Install this theme like the icon theme before via drag and drop. If the theme is not applied you must click on "Customize" and select "Natty" at "Controls" and "Window Border"

_3. Compiz_
Since you should be using a pretty new machine you could afford it to invest a tiny little bit of your CPU cycles for some more sophisticated eyecandy and switch to compiz. This can be done by reverting to the "Appearance"-Window and choose the "Visual Effects"-Tab and choose the option at the bottom called "Custom". Now navigate to "System" -> "Preferences" -> "CompizConfig Settings Manager". I created a custom profile that you can import via "Preferences" and by hitting "Import". Save the following file so that you can import it:
[http://files.getdropbox.com/u/416097/tut/compiz_config.profile](http://files.getdropbox.com/u/416097/tut/compiz_config.profile)
I tried to used as few plugins as possible and as many as needed. Some important keybindings are: 
-Alt + Tab 
-Ctrl + Tab 
-Move the mouse to the upper left screen edge, hold down Ctrl and press your first mousebutton

_4. Gnome-Do_
Well. This chapter is the last one. You might try to cruzify me or not but here we will try to replace the gnome-panels with another dock entirely! Therefore we will need Gnome-Do. So open it up and open the preferences dialogue with a rightklick in the small arrow and setup the "Appearance"-Tab like this:
[http://files.getdropbox.com/u/416097/tut/11.png](http://files.getdropbox.com/u/416097/tut/11.png)
On the plugins tab you should enable the following plugins:
-Archive
-CPU Monitor Docklet
-Files and Folders
-Firefox
-Gnome Session Management
-Gnome Terminal
-Google Maps
-Google Search
-Locate Files
-Pidgin
-Rhythmbox
-Switcher Docklet
-Thunderbird
-Volume Control Docklet
-Weather Docklet
-WindowManager

Don't hesitate to try out all the others but these ones I do consider to be the most useful. Go back to the "Appearance" tab and activate all the docklets except the battery docklet which is just useful on a laptop. But if you have one - go and get it! We are nearly finished. Now you might ask yourself how to work with gnome-do. it is very intuitive once you got the concept. hit the button on the very left and start typing an application name like: "swi" and the proposal will show swiftfox. Just hit return and it will open up.
Now also open up thunderbird 3 by typing "shre" and hitting return. This also works with the names of entries in the "Preferences" and "Administration" menus of the gnome menus. When you move the pointer above the swiftfox and thunderbird icons you might see that they look REALLY trashy. we should fix this issue by first choosing appropriate icons. These icons are delivered by mashup but since both programms are not standart the icons are just not used: 
-type "home" into gnome-do and you should be able to open your home folder via gnome-do
-navigate into ~/.icons/Mashup-1/apps
-choose a icon for thunderbird and the invoke:
```

sudo cp /home/seb/.icons/Mashup-1/apps/*filename*.png /usr/share/pixmaps/thunderbird-3.0.png
sudo cp /home/seb/.icons/Mashup-1/apps/firefox-icon.png /usr/share/pixmaps/swiftfox.png

```

_5. Clean Up_
Before cleaning up make shure that you told Gnome-Do to start after login in do's preferences window and check it in the "Startup Applications".
Since we don't need the gnome-panels anymore we can delete the one at the bottom and also delete all the applets in the top panel. 
Now there are two ways of handling the last panel. Either you remove the gnome-panel entirely via: 
```

sudo apt-get remove gnome-panel

```
Or you just make the launcher unexecutable by doing the following:
-invoke:
```

sudo nautilus /usr/bin

```
-look for the gnome-panel executable
-rightklick on the file, choose "Properties" and uncheck the box in the "Permissions" tab to render it unexecutable
-close the filemanager with root permissions
Or you can just make it nearly unnoticeable:
-go into the preferences of the last remaining panel and set its color to full transparency.
-Now type "gconf-editor" into gnome-do and hit return. 
-use the tree to navigate to: /apps/panel/toplevels/*** <-- should be just one panel
-put the settings like in the following screen:
[http://files.getdropbox.com/u/416097/tut/12.png](http://files.getdropbox.com/u/416097/tut/12.png)

[size=+1]**9. Conclusion**[/size]
Now this is it! We are done. First I have got to thank you for reading my guide and I would like to read some helpful comments on my first guide ever. Since this is a very up to date tutorial I will try to keep it like that with regular updates and improvements. So please feel free to give me some hints how to make the system even better. Thanks again!

Labello

---

### Post by jpeddicord on 2009-07-11
Love the use of screenshots, provides a nice bit of context. Approved, and thank you for your contribution to Tutorials & Tips!

---

### Post by renbla on 2009-07-13
What a good tutorial :guitar: Keep it going man :lolflag:

---

### Post by j7%&lt;RmUg on 2009-07-13
Very nice guide, sped up my old computer like nothing else.

---

### Post by TwiceOver on 2009-07-13
Hrm...  I've been wanting to redo my netbook.  Maybe it is time to go this route.

So you replaced your toolbars with Gnome-Do?  I didn't know Gnome-Do could also be a dock?

---

### Post by Labello on 2009-07-13
> **TwiceOver said:**
> So you replaced your toolbars with Gnome-Do?  I didn't know Gnome-Do could also be a dock?

Yeah thats on of the surprising things about it(quoted from The IT-Crowd)

All the others: Thanks for the good responses! Is there anyone out there who treid to follow this guide entirely?

> Very nice guide, sped up my old computer like nothing else.

For real? Really? Is the difference really that huge? Well. I would be glad if it was.

---

### Post by Labello on 2009-07-14
Note:

Edited my first post in the section "5. Clean up" to show up some more methods how to get rid of the gnome-panels.

---

### Post by TwiceOver on 2009-07-14
I'm actually going to try this out here in a few minutes on my netbook.

One thing I know for sure is that I need the "Restricted Hardware Drivers" app in order to get my wireless working.  Is that included in one of your install lines or is that a separate package?

I tried using Gnome-Do/Docky but there is just something non intuitive about the dock that irks me.  Not sure exactly what.  Also no gnome menus, admin menu, prefs menu, session management... How do you get around that?

I'll let you know how it goes.

---

### Post by Labello on 2009-07-14
I am not shure about the restricted driver app.

When you are using a netbook i would not recommend to use gnome-do as a dock since you need your network-manager pretty often and also the nm-applet. so for this hardware you should stick to gnome-panels. but all the rest should work fine. but a netbook might cause you some problems since the alternate-setup is always looking for a CD-drive and the appropriate drivers. if there is none it will abort the installation process. i am not shure whether it works with an external CD-drive.

greets labello

---

### Post by TwiceOver on 2009-07-14
> **Labello said:**
> I am not shure about the restricted driver app.

When you are using a netbook i would not recommend to use gnome-do as a dock since you need your network-manager pretty often and also the nm-applet. so for this hardware you should stick to gnome-panels. but all the rest should work fine. but a netbook might cause you some problems since the alternate-setup is always looking for a CD-drive and the appropriate drivers. if there is none it will abort the installation process. i am not shure whether it works with an external CD-drive.

greets labello

There's plenty of room for a dock... Just not a dock AND a panel.  I think this is what was bothering me with Docky, it is missing a large portion of the functionality.  I guess if I get used to gnome-do and typing what I want to do I might get more used to it.

EDIT:

Here's some things I also needed.
network-manager <--This is the network and wireless manager
restricted-manager  <--This is the restricted drivers manager

Here are the keys for the PPAs listed in the OP (add them using the below command and change the 'xxxxx' to the key you want to add:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com xxxxxxxx

xorg-edgers: 8844C542
transmission-nightly: 22202A6B
fta: 0C713DA6
do-core: 77558DD0
compiz: 42C24D89
Pidgin PPA: A1F196A8
Medibuntu: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---

### Post by Labello on 2009-07-16
Hi dear readers,

with the help of TwiceOver i was able to add some stuff concerning repos and special packages for laptops. Edited into the upper post.

---

### Post by MahBumble on 2009-07-19
Thanks for the great tutorial, really easy to follow, and a great finish!

I've come across a couple of problems, and have some questions. I started following your guide from step 6 onwards, as I only recently installed Jaunty (which may be why I'm having trouble). Firstly, the command 'bum' isn't recognised, nor is 'bootupmanager'. Any other way to access these options?

Also, my Gnome-Do 'Docky' doesn't have the same preferences under the 'appearance' tab as in your screenshot (see attachment), hence I'm unable to customise docky to the same level. 

Finally, how do I insert a battery icon and workspaces icon into docky? 

Thanks,
MB

---

### Post by Labello on 2009-07-19
> **MahBumble said:**
> Thanks for the great tutorial, really easy to follow, and a great finish!

Firstly: Thank you! Glad to hear.

> **MahBumble said:**
> I've come across a couple of problems, and have some questions. I started following your guide from step 6 onwards, as I only recently installed Jaunty (which may be why I'm having trouble). Firstly, the command 'bum' isn't recognised, nor is 'bootupmanager'. Any other way to access these options?

Also, my Gnome-Do 'Docky' doesn't have the same preferences under the 'appearance' tab as in your screenshot (see attachment), hence I'm unable to customise docky to the same level.

These problems are due to the fact, that I use an extra repository for gnome-do with a later version. To correct your problem you should follow the entire step 5 which will also install the bootupmanager and some other speedups.

> **MahBumble said:**
> Finally, how do I insert a battery icon and workspaces icon into docky?
I asume that you already have done Step 5 of my guide then you will have a list entry in the plugins tab for docklets where you can activate the ones you need.

Feel free to ask any further questions ;)

labello

---

### Post by ntginson on 2009-09-02
This is a great howto. thanks for sharing it with the rest of the community. 
I do have a question, is this possible to accomplish on an existing Ubuntu desktop? I really like my desktop to look like this one but having to reinstall from scratch is a rather long process.

Also, being a new convert, I would like to know more about the minimum hardware requirements for a snappy, beautiful desktop like this one. I have a pentium 4 desktop pc with onboard video and sound, an HP dv1000 laptop and a blue netbook, all running ubuntu jaunty. I really hope I can do the snappy beautiful desktop on all 3 systems


Thank you

---

### Post by emoguitarist06 on 2009-09-08
This is an amazing Tutorial! I especially love the "CONCURRENCY=shell" and "bum" and MashUp5 is just beautiful!!

---

### Post by Labello on 2009-09-08
> **ntginson said:**
> This is a great howto. thanks for sharing it with the rest of the community. 
I do have a question, is this possible to accomplish on an existing Ubuntu desktop? I really like my desktop to look like this one but having to reinstall from scratch is a rather long process.

It might be possible to accomplish this to an existing desktop, but you might be spending a huge amount of time in removing unneeded tools and packages. So it might be easier to reinstall the system. Moreover you can make shure, that you only install the stuff that is needed.

> **ntginson said:**
> Also, being a new convert, I would like to know more about the minimum hardware requirements for a snappy, beautiful desktop like this one. I have a pentium 4 desktop pc with onboard video and sound, an HP dv1000 laptop and a blue netbook, all running ubuntu jaunty. I really hope I can do the snappy beautiful desktop on all 3 systems
Thank you

I can't really estimate this. I have got a pentium 4 ht with 3.4ghz and 2.5gb of ram. but 1gb should be fairly enough to do most of the stuff. Blender and Gimp might be exceptions.

> **emoguitarist06 said:**
> This is an amazing Tutorial! I especially love the "CONCURRENCY=shell" and "bum" and MashUp5 is just beautiful!!

I am really glad that at least some people like my setup.

---

### Post by ratdog on 2009-09-08
Hello, I think I might like this setup, but I don't know if I can do without the panel for selecting apps.  I am hoping to use my laptop for some music production with the music apps that come with ubuntustudio.  I am new to that software and don't know what all the apps are called.  Is there still a way with your setup to browse the long list of music programs?  Thanks for the tutorial.

---

### Post by Labello on 2009-09-09
My advice is to stick to a normal UbuntuStudio Setup until you know exactly what apps you need and then retry this guide with some personal modifications regarding package installation (jack, sequencer and so on)

---

### Post by edmondt on 2009-09-09
AWESOME Guide!!! Thanks for spending the time to write it... I too feel that using linux is way more productive than Windows or OSX, speaking from personal experience.

Run this in terminal to disable gnome-panel

```

sudo su
mv /usr/bin/gnome-panel /usr/bin/gnome-panelBACK
echo "" > /usr/bin/gnome-panel
chmod a+x /usr/bin/gnome-panel

```

To Re-enable:

```

sudo su
mv /usr/bin/gnome-panelBACK /usr/bin/gnome-panel

```

---

### Post by Eskobar on 2009-09-22
Awesome post bro, i'm new to linux and had been using Linux MInt for about 3 months now.... I wanted a "stripped" version and this tutorial got me where I needed to be.  Thanks a million for your hard work and posting it up!!:guitar:

---

### Post by rockerhard on 2009-09-23
[CENTER][FONT=Impact][SIZE=5][COLOR=Sienna]**:KSI love you!!**[/COLOR][/SIZE][/FONT]:KS
[/CENTER]
[B][SIZE=4][FONT=Garamond][SIZE=3]
[/SIZE][/FONT][/SIZE][/B][SIZE=4][FONT=Garamond][SIZE=3][FONT=Georgia]Well in a "ubuntu" kinda way. 'Ya know?[/FONT][/SIZE][/FONT][/SIZE][B][SIZE=4][FONT=Garamond][SIZE=3]

[/SIZE][/FONT][/SIZE][/B][SIZE=4][FONT=Garamond][SIZE=3][FONT=Georgia]Wow, the first three words in my first post :)[/FONT][/SIZE][/FONT][/SIZE]
[B][SIZE=4][FONT=Garamond][SIZE=3]
[/SIZE][/FONT][/SIZE][/B][SIZE=4][FONT=Garamond][SIZE=3][FONT=Georgia]An outstanding tutorial to say the least. Verbal excellence combined with screenshot examples even dummies like me can figure this out. This took time obviously and I just wanted to thank you for sharing your knowledge. This is exactly what I was looking for, as I am sure many others as well. [/FONT][/SIZE][/FONT][/SIZE][B][SIZE=4]
[/SIZE][/B]

---

### Post by Pauly BC on 2009-09-29
Please help! I installed Ubuntu from the regular disc rather than the alternate ISO and I have been carrying out the steps with great luck and a very quick boot. Unfortunately somehow in Step 7 audio, my operational sound system turned into static. I uninstalled pulse but it did not work! My sound device is a built-in realtek 883 on the mobo. I downloaded the driver from Asus but I don't know how to activate it.

---

### Post by Labello on 2009-09-29
First of all you should not uninstall Pulse Audio since it will be the sound server in the future.

But I am sorry to say that I can not help you out with your sound driver problem, IF it actually IS one. Maybe you should start a new thread in the proper subsection here in the forums.

---

### Post by n1ete on 2009-10-25
Greeeaat Work!!
I request an update for Karmic! ;)

thanks

---

### Post by darkwa on 2009-12-13
Great tutorial dude.
Thank you, very very much, your instructions are very clear and easy to follow

---

### Post by dief-eh? on 2009-12-25
Hello & Happy Xmas! 

I was looking forward to trying out your recommendations on a new-old govt. surplus desktop I picked up at auction. But I'm presently stumped just before Step 4, where the instructions seem to presume that the "rather ugly desktop" will have "Applications   Places   System" available, on the panel. Mine doesn't though, which makes it difficult to move forward to Step 4!

Many thanks for any ideas to try.

---

### Post by dief-eh? on 2009-12-28
Howdy fellow commandline-install buckaroos!
[update] on my own question from Friday, Xmas day: decided to start over and re-install today, and got a formerly-ugly-but-no-longer gnome-desktop with the usual <Applications...Places...System> headings on the top panel. Woohoo!

NO idea what I might have done differently the first time through, but I'll take what I can get; and maybe this will help someone else.

Chow 4 niao. And happy holidays.

---

### Post by swrightsls on 2010-01-01
I'm setting up an old Sony laptop for my daughter, which has a Pentium M 1.86Ghz, 1Gb, a new 7200rpm 160Gb sata drive, and nVidia 6400 graphics. It was quite snappy under XP, so I expected at least as good with Ubuntu 9.10, but have so far been disappointed. I've tried a few tweaks which didn't seem to help much, and then came across this guide.

My questions are: can I expect decent performance from this hardware setup using your guide, or should I give up on Gnome and try something lighter like XFCe?

Am I ok to use 9.10 instead of 9.04? Can I get a minimal install from the standard CD?

Thanks!

---

### Post by TheTank on 2010-01-01
> **swrightsls said:**
> I'm setting up an old Sony laptop for my daughter, which has a Pentium M 1.86Ghz, 1Gb, a new 7200rpm 160Gb sata drive, and nVidia 6400 graphics. It was quite snappy under XP, so I expected at least as good with Ubuntu 9.10, but have so far been disappointed. I've tried a few tweaks which didn't seem to help much, and then came across this guide.

My questions are: can I expect decent performance from this hardware setup using your guide, or should I give up on Gnome and try something lighter like XFCe?

Am I ok to use 9.10 instead of 9.04? Can I get a minimal install from the standard CD?

Thanks!
IMHO 9.04 is more performant then 9.10.
Maybe try it before moving to XFCe.

---

### Post by swrightsls on 2010-01-01
Ok, I started over with 9.04 as per the guide, and it is definitely snappier, but... a few things still not working:

-nvidia protected drivers will not load, they did load fine in a stock 9.10 install
-swiftfox won't start - 'starting swiftfox' appears on the taskbar, then nothing. I installed the prescott version, as this is a Pentium M 1.86Ghz. Using Epiphany for now...
-I'll continue on with the Gnome-do stuff so I can get a battery meter working... :-)

One more thing I'd suggest at the start is to copy the guide onto a USB key to save a lot of typing on a fresh install... just open as a text file and cut/paste the relevant command lines.

---

### Post by TheTank on 2010-01-02
> **swrightsls said:**
> Ok, I started over with 9.04 as per the guide, and it is definitely snappier, but... a few things still not working:

-nvidia protected drivers will not load, they did load fine in a stock 9.10 install
install envyng-core and envyng-gtk/qt
then install the nivida drivers with envy (I can only get it to run off of the command line for some reason)

> 
-swiftfox won't start - 'starting swiftfox' appears on the taskbar, then nothing. I installed the prescott version, as this is a Pentium M 1.86Ghz. Using Epiphany for now...

I use swiftweasel and it works fine (though I have to use 3.5.5 because there is no finished package for amd 64 atm)

> 
-I'll continue on with the Gnome-do stuff so I can get a battery meter working... :-)

Conky?

---

### Post by swrightsls on 2010-01-02
> **TheTank said:**
> install envyng-core and envyng-gtk/qt
then install the nivida drivers with envy (I can only get it to run off of the command line for some reason)

I use swiftweasel and it works fine (though I have to use 3.5.5 because there is no finished package for amd 64 atm)

Conky?

I was missing the kernel headers; once I installed them everything worked fine using the standard nvidia driver install.

Turns out the Centrino uses i686, not Prescott - Swiftfox is fine now.

I'm missing many of the plugins in do, and the all of the docklets... I found a post saying 0.82 of do requires a source build to get the docklets. I guess this guide was based on an earlier build of gnome-do?

I didn't have a battery meter in gnome panels either, so I'll try Conky.

So far I am quite impressed with the performance of this machine now - an amazing transformation!

---

### Post by Labello on 2010-01-02
> **swrightsls said:**
> I'm setting up an old Sony laptop for my daughter, which has a Pentium M 1.86Ghz, 1Gb, a new 7200rpm 160Gb sata drive, and nVidia 6400 graphics. It was quite snappy under XP, so I expected at least as good with Ubuntu 9.10, but have so far been disappointed. I've tried a few tweaks which didn't seem to help much, and then came across this guide.

My questions are: can I expect decent performance from this hardware setup using your guide, or should I give up on Gnome and try something lighter like XFCe?

Am I ok to use 9.10 instead of 9.04? Can I get a minimal install from the standard CD?

Thanks!

You should definately give it a try. a friend of mine tried it with karmic and it runs quite fine afaik.

i can not report on this from personal experience since i moved to kubuntu =)

but good luck and thanks for reading!

---

### Post by swrightsls on 2010-01-03
> **Labello said:**
> You should definately give it a try. a friend of mine tried it with karmic and it runs quite fine afaik.

i can not report on this from personal experience since i moved to kubuntu =)

but good luck and thanks for reading!

I'll stick with 9.04 for now, as the other laptop I need to set up uses Radeon graphics and the 9.10 driver doesn't work anyway. I'm using the 9.04 driver on 9.10 with it, but will reload using your guide once I find a setup I'm comfortable with.

Curious why you moved to Kubuntu? Is a guide for that setup coming soon? ;-)

---

### Post by Labello on 2010-01-04
> **swrightsls said:**
> Curious why you moved to Kubuntu? Is a guide for that setup coming soon? ;-)

First of all I wanted to give KDE a REAL change since i have been trying it just for one hour or so after each release since 4.0.

so starting with 4.3.* i considered it to be mature enough.

further i could not really see any good inventions in Ubuntu except video-drivers and boot process. but these too things apply also to KDE. and most importantly i hate the new gdm. dunno why.

another reason is that i really like kdenlive and amarok. and since i like it when everything fits i just switched to QT4 completely

and last but not least it's the astonishing freedom of choice we enjoy in the FOSS-world =) try to tell an apple or ms guy that you recently switched your desktop-environment :D

concerning a Kubuntu-Guide i am not familiar enough with KDE and especially Karmic. So there is still very much to learn for me until i know exactly which packages are needed and how to keep them as few as possible.

---

### Post by dief-eh? on 2010-01-04
Hi there,

Here's hoping everybody had a good new years.

I´m still having minor issues with this install: enable networking panel icon shows a red mute x (wired networking does not seem an option); I keep getting a ¨cant find package skype¨ from terminal (synaptic lists only skype-MID) 

Neither of which is a show-stopper, exactly, but makes me a bit wary of going through with the recommended elimination of the panels.

Any replies greatly appreciated.

---

### Post by BFG on 2010-01-05
Nice tutorial!

I had a problem with one step.

> **Labello said:**
> 
```
sudo gedit /etc/default/rcS
```
and now add the following line at the end of the file:
```
CONCURRENCY=shell
```


After this, cups doesn't run at startup.  Any ideas?  priority is default at S50
Does it need saned to load first?

/etc/rc2.d
lrwxrwxrwx 1 root root  14 2009-10-31 13:26 S50cups -> ../init.d/cups
lrwxrwxrwx 1 root root  20 2009-10-31 13:26 S50pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  15 2009-10-31 13:26 S50rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  15 2009-10-31 13:26 S50saned -> ../init.d/saned

---

### Post by Labello on 2010-01-05
hi,

to be honest i don't think that those two things are related to each other.

try to run "sudo bum" and check whether you unchecked cups. i have been using cups and cuncurrency together now on several setups. never had any issues.

---

### Post by malangbaba on 2010-01-08
Can u get a wireless manager to work in the gnome-do?
Thoughts on the standalone Docky?
I am half way through this... :) just got a running desktop

---

### Post by Labello on 2010-01-08
> **malangbaba said:**
> Can u get a wireless manager to work in the gnome-do?
Thoughts on the standalone Docky?
I am half way through this... :) just got a running desktop

hi,

i never had to cope with wireless since i used these steps so setup my desktop which is connected via ethernet. maybe someone else can help and i will insert this into the guide.

---

### Post by malangbaba on 2010-01-08
Ah. thanks. I'll look into figuring it out.

A few things (packages) I have yet figured out:
- I cant working is to access my other partitions.  It automatically tells me "Unable to mount XX filesystem: Authentication is required"  Suggestions to what package I may be missing?
- The search for files function?

---

### Post by Labello on 2010-01-09
> **malangbaba said:**
> Ah. thanks. I'll look into figuring it out.

A few things (packages) I have yet figured out:
- I cant working is to access my other partitions.  It automatically tells me "Unable to mount XX filesystem: Authentication is required"  Suggestions to what package I may be missing?

I think while editing your partition-table during setup you might have gotten something wrong. you should manually add the partitions into fstab and then invoke:

```
sudo mount -a
```

---

### Post by mvalenti on 2010-01-10
Nvidia  drivers not activating, :( and compiz not installing either.. Having low graphics mode messages everytime ubuntu starts. Any suggestions?


-Mark

---

### Post by Labello on 2010-01-10
Well you should do some research on your graphics card model. as i already mentioned in the tutorial, i can not provide any information on the rather complex aspect of getting 3D to work. sorry...

---

### Post by swrightsls on 2010-01-10
> **mvalenti said:**
> Nvidia  drivers not activating, :( and compiz not installing either.. Having low graphics mode messages everytime ubuntu starts. Any suggestions?


-Mark

I had the same issue. The solution was to install missing kernel headers, tip taken from this thread:

[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)
```

sudo apt-get install build-essential pkg-config linux-headers-$(uname -r)

```
Once the driver is active, Compiz should work fine. I've done this on two different nVidia machines and it's worked fine. An old P4/512Mb with nVidia 5200 works surprisingly well, although I looking for a similar tweaked install for KDE now...

---

### Post by Labello on 2010-01-10
> **swrightsls said:**
> An old P4/512Mb with nVidia 5200 works surprisingly well, although I looking for a similar tweaked install for KDE now...

I was thinking about making a similar guide for kubuntu, but kubuntu lucid won't need that much tweaking since kubuntu just rocks out of the box!

but still i did a minimal install of karmic and then just invoked:

```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xorg kdm kdebase kdebase-workspace firefox amarok vlc flashplugin-nonfree ark okular gwenview dolphin

```

i might have forgotten some packages but that should be it =)

---

### Post by llawwehttam on 2010-01-10
You might want to update your post for karmic a bit.

Also ubuntuzilla is very good for keeping firefox up to date.

---

### Post by Labello on 2010-01-11
> **llawwehttam said:**
> You might want to update your post for karmic a bit.

Also ubuntuzilla is very good for keeping firefox up to date.


Yeah I could but as I already mentioned I am currently using KDE with Karmic and not Gnome. So either I write a completely new guide, or I would have got to switch back to Gnome which would definately s*u*c*k =)

---

### Post by hero1900 on 2010-01-11
thx very helpful
keep it going

---

### Post by iBurger on 2010-01-26
All though I think it might be a bit out of order, reading through the discussion above, but I sometimes wonder why ubuntu feels less snappy than windows xp. I have been using ubuntu now since 8.04 as my primary os, and I love it. However, it just doesn't feel as responsive as Windows at times. Like, starting up Swiftfox, takes a few seconds, its not instant as Firefox on XP.

However, I do notice that many applications launch faster after I have launched them before. (I'm using Prelink by the way.) Does anyone has any insights as to why that is? Why ubuntu feels sometimes slower than xp? I think that this could be a potential issue for me, long term, if this doesn't improve.

(have a one year old laptop, with an Intel(R) Core(TM)2 Duo CPU T5450 and 3 gig ram onboard)

---

### Post by TheTank on 2010-01-27
@iBurger:
FF snappy on XP? Sorry, not on my work machine (with similar specs).
Just tried it and it takes 4 sec.

Though I also wonder why ff start time could be a 'potential issue, long term'. A crashing FF I could understand but a slow starting? No so.

---

### Post by iBurger on 2010-02-17
Actually, I was wrong, you were right. Grass is always greener problem. I recently installed XP again and Firefox indeed starts up slower.

---

### Post by AlexanderDGreat on 2010-02-17
Thanks for this tutorial I learned a lot mate. Although, I didn't like the Natty because when I go to the Synaptics, it looks awful the windows border there. The icons, I loved mash, but there are dark icons. Enjoyed reading from the top down, hey by the way, is gnome-do similar to cairo-dock? I was lost in the gnome-do part, how do you install that?

PS I didn't start from scratch, I already have a working 9.10 when I read this one.

PPS Thanks for the pictures. It made me feel I was on the right path.

---

### Post by nevaeh.aaric on 2010-02-18
Thanks for the guide and for updating us.

---

### Post by dot2kode on 2010-02-18
Very nice guide! I just read through it and I'm going to try it out on my netbook today (Asus 1005HA eeePC.  I will report back once I do...Thanks for putting this together and sharing! =D>

---

### Post by dot2kode on 2010-02-18
> **Labello said:**
> hi,

i never had to cope with wireless since i used these steps so setup my desktop which is connected via ethernet. maybe someone else can help and i will insert this into the guide.

This is for the Asus though however it can help if you do have bad performance with wifi under **Karmic**  My wifi worked but it was really, really slow: 
[http://sprayfly.com/2009/11/17/improve-wireless-performance-in-ubuntu-karmic-on-asus-eeepc-1005ha/]("http://sprayfly.com/2009/11/17/improve-wireless-performance-in-ubuntu-karmic-on-asus-eeepc-1005ha/")

```
sudo apt-get update && sudo apt-get install linux-backports-modules-wireless-karmic-generic
```

That page will walk any one through who is interested.

---

### Post by jarrah-95 on 2010-02-21
i just finished the guide and im loving it everything's awesome exept for two things. i dont know how to add all my new programs (the ones that i want on top of your recomendations) to the dock and also can i use the ubuntu software store update manager and synaptic with this
thank you it has sped up my laptop 50 times, this is way better than a normal ubuntu setup.

---

### Post by jarrah-95 on 2010-02-25
after doing this the system worked perfictaly, untill a coupple of days ago when it started randomly loging me out. does anyone know why or how to stop it. 
thanks for the awsome (super fast) os though

---

### Post by seanbw on 2010-02-26
This link apperas to be broken:
[http://cid-cf78487abe44ffc6.skydrive...update.tar.bz2](http://cid-cf78487abe44ffc6.skydrive...update.tar.bz2)
both FF and chrome cant access it.

Unfortunately I have a GMA 965 video chip blacklisted by compiz so I can't carry out all the steps. Thanks for the tutorial though.

---

### Post by warfacegod on 2010-05-12
My apologies if this has been asked here before.

> Doing a minimal install without at least having
Code:

APT::Install-Recommends "0"
APT::Install-Suggests "0"

in /etc/apt/apt.conf isn't exactly worth it, in my opinion

From a somewhat similar thread to this one. Is this necessary or desirable in a Minimal install?

---

### Post by dewsworld on 2010-06-07
Really an awesome tutorial.... Thanks for the stuff :)

---

### Post by sharon11 on 2010-11-15
Nice piece of reading here....i get good information about this....i visit all links posted in article....All are really informative....also tell me about duct cleaning in maryland....I am looking fro a professional cleaner....

---

### Post by Chazz44able on 2010-12-03
I'd recommend using Cairo Dock instead of Gnome do.

---

### Post by Kir_B on 2010-12-08
> **Labello said:**
> Yeah I could but as I already mentioned I am currently using KDE with Karmic and not Gnome. So either I write a completely new guide, or I would have got to switch back to Gnome which would definately s*u*c*k =)

First off, a few quick questions: 

1. How snappy is the KDE desktop?

2. Have you tried it out on older hardware (say 3 or 4 years old)?

3. Has this tutorial been successfully applied to a Lucid install, and if so, what can and cannot be done?

4. Are you planning to do a new tutorial for Lucid, as I think some of the tweaks you've done are quite intriguing and I'd love to try them out on the new box (AMD x6 1055t) we've ordered. (Should be here in the next couple weeks and will **_not_** have any Micro$oft products installed.)

I like what I've seen so far. Now I'm going to go back and dissect the life out of it.

Great work.

Kirby

---

