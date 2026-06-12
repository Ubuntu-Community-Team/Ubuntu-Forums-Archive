---
title: "New eAR OS Media Center release"
date: 2008-06-03
forum: Other OS Talk
---

### Post by earos.dk on 2008-06-03
Since it is really difficult to announce a distro to the public let's try here:


eAR OS is a complete Linux distribution based on Ubuntu 8.04, but without the lack of speed and security.


The most important features of this release:

1) Now you can navigate the eAR Media Center with a mouse, a touch pad or a touch screen! Use the mouse or your finger to scroll around.
Left-Click to select and activate an item. Middle-Click to access the build-in help menu and user guide. Right-Click to go backward in menues.

2) Windows Media Center Remotes (new version with Philips ID) are now working out-of-the-box.

3) Update of the 2.6.24 Real-Time Linux kernel and update of almost all applications to the very newest stable releases. The excellent Exaile audio player with iPod support has been added too.

4) New features in the MORE menu. You can easily extent the MORE features yourself, use the examples.

5) Firefox with support of QuickTime content and DIVX movie playback. For example, now you can watch the Apple Movie Trailers in High Definition.

6) Firewall to prevent incoming traffic. Permissions to run the firewall have been setup for you. Therefore the firewall is working out-of-the-box, just go through the wizard and specify your connection to the internet. The firewall is auto-started every time you start your PC.


We really do hope you will enjoy the speed and the new features of the eAR OS, version 1.09b.

Edit:
The link to download directly or torrent: 
[http://www.earos.dk]("http://www.earos.dk")

---

### Post by azurehi on 2008-06-04
Hello - I cannot install the latest release for the same reason I could not install HH ubuntu 8.04...without adding all_generic_ide
See:  [http://ubuntuforums.org/showthread.php?t=767154]("http://ubuntuforums.org/showthread.php?t=767154")

I tried several times to add this, but being somewhat of a newbie, I could not find the location.  In 8.04, I selecet install, F6 and then add all_generic_ide and the installation proceeds.  Any help appreciated

---

### Post by Cam_B on 2008-06-04
funny, I was looking for a media oriented distro, looks like I found it... Hope it works...

---

### Post by matiit on 2008-06-05
Ca I install ear media center on other distro? 
for egzample ubuntu,debian, slack. I don't want install ear OS but i want use ear media center... It is GPL, but i don't know where to find sources or even DEB's!

---

### Post by notwen on 2008-06-05
Clean looking GUI you have there.  Good luck w/ your project and I'll be sure to try it out if I ever make myself another HTPC.  =]

---

### Post by earos.dk on 2008-06-09
I have only experienced one PC that could not install the eAR OS distro. The reason is the new initramfs from Ubuntu, that I am using now.
Previously I used Debian, but it did not support that many GPU's which Ubuntu does. It may be solved by the Ubuntu team, the day they get the 8.04 to install similar to 7.10.

You can find all source code by apt-get source or on the Live CD.

The purpose of this distro is to make everything to be working out-of-the-box. This is certainly really impossible with a .deb package or the source code. Afterwards you have to configure a ton yourself and this is the opposite of the eAR OS.

I am working on a brand new MMI-lauout that does not look like what you have  seen before. I am integrating the eAR Media Center into the Desktop.

Imagine to have the eAR Media Center to be an operational wallpaper!

All the best,
[www.earos.dk](www.earos.dk)

---

### Post by azurehi on 2008-06-09
Thank you earos.dk:  Just last evening I was able to edit the install command line, adding all_generic_ide, and the installation proceeded very smoothly.  Your distribution is Very Nice, indeed, and everything works, just as you have said.  It loads to desktop very quickly and is very pleasing to look at.  Thank you for your work and I'll be looking forward to your next project.

---

### Post by earos.dk on 2008-06-12
few updates are available.

---

### Post by wlake on 2008-06-12
Hi,
I just installed 1.09b and am still getting used to it. One observation is that when installing it seemed to hand at the 94% point,configuring hardware. Took a long time to finally install. 

The second observation is that I have a fairly new Nvidia card Geforce GO 7400, the new glx driver has worked on all other distros, but when I installed the restricted driver in eAR OS, after a reboot I got a black screen. I rebooted into recovery mode and that disabled the Nvidia driver so I am not using it.

I am curious as to the advantages of the rt kernel?

I think I will grow to like this distro. I also installed Firefox 3.0.

Is the dock bar Avant and if so is the preferences manger present?

Lastly is this the best place to give feedback and ask questions?

Regards,
wlake

---

### Post by earos.dk on 2008-06-13
Yes, it takes a few minutes to configure the hardware during install. Here it takes approx. 3 - 4 minutes to configure the hardware. IMO this is not a problem.

The Live-CD is using the restricted driver, and after install to hard disk it is disabled. This is an issue to the ubiquity installer. When the distro is installed to hard disk you have to enable the restricted nVidia driver yourself. Sorry!

FireFox 2.0 is default, because much more plugins works with it. One plugin I will not live without is the mediaplayer connectivity plugin. The day it works with the not yet released Firefox 3.0 the eAR OS will come with FireFox 3.0. In the mean time you have to install it yourself.

eAR OS is not using the Avant dockbar anymore. It was removed in version 1.06 because of, sorry to say, the out-of-control amount of memory consumption, especially plugins are way too bad regarding this issue. Today, it is using Simdock, and now the RAM memory consumption has been reduced by minimum 250MB. Furthermore, the Simdock runs without OpenGL, AWN does not. Next time the eAR OS comes with a development version of Simdock, that IMO works really good.

Yes, a forum of its own should be available, but time.....,  :-)
Hopefully a forum will come pretty soon. I will ask one to let him get it up and running.

The distro is still improved, the more feedback the better it will be.

---

### Post by wlake on 2008-06-13
Thanks for your reply.

Enabling the Nvidia driver myself did not work for me. When I rebooted I still got a black screen with the computer frozen. Had to turn it off and back on. So I am still not using the Nvidia driver. Not a huge problem for me.

I did download the update script and it ran fine. So I have the update media center and Simdock.

Regards,
wlake

---

### Post by xd397 on 2008-06-17
Can i Get the graphics and programs on ear media for Ubuntu 8.4

---

### Post by smartboyathome on 2008-06-17
> **xd397 said:**
> Can i Get the graphics and programs on ear media for Ubuntu 8.4

I would also like to know if the eAR Media Center is available for download. It should be, as it is in a repo, but I don't know which repo. If the eAR Media Center is free under the terms of the GNU General Public License, then the source should be made available on the website to download.

---

### Post by belgofac on 2008-06-20
I have been a longtime user of Windows mce2005 and Vista MCE. (Australia) Besides that I have a pc with 3 Linux and 2 Win OS (Quintuple boot):)

Downloaded version 1.09 in the weekend. 
 
Pro's:

Ran flawless from the live cd.  
Channel scanning and EPG running in 1 minute.

Con's:

Live and recorded tv quality is below standards. You can improve the quality by changing a setting but then the cpu gets too much load and you will get stuttering.

Gui needs a lot of improvements and one should be able to control all settings from there.

Conclusion:

eAR cannot compare to MCE2005 at this stage.  What concerns me is the fact that the developer charges $60 Aus dollars for the Pro version.  However, I do not know what the Pro version of eAR entails and there's no way of testing it without paying.  What's better in the Pro version?

Is there going to be an improvement of recording quality (probably a codec/driver issue)?

Willem Raak

---

### Post by earos.dk on 2008-06-20
Thank you for your comments. The more feedback the better it will be.

Stutting is a DVB hardware driver issue, which is out of my control. I have a perfect picture with my DVB TV cards, but no names here...

A new version 1.10 has been made, I am currently testing it.  It has been transformed to a real distro. Now, everything works out-of-the-box, regardless of the username and password you select during installation. You can create many users to run on the same machine, they will all experience everything works out-of-the-box. Version 1.09 and older versions came with a pre-configured user and that was a problem when not reading the installation guide.

Default video settings have changed too and all packages are the newest, including the newest Real-Time Linux kernel.

A repo will come, but time.... give me some :-)

The new version 1.10 will be ready for download when I have finished all tests. I do expect to finish that tomorrow.

All the best,
[www.earos.dk](www.earos.dk)

EDIT, because I forgot: Version 1.10 comes with a wizard to let you very simple specify the places of where you have stored your media files. Specify the folders with muisc, videos, photos and recorded TV to whatever you wish.

---

### Post by earos.dk on 2008-06-23
Hi again,

Today, Version 1.1 has been released. It can be downloaded via torrent, http and ftp. Please use torrent, the more users the better it works.

All issues from the until now two reviews have been addressed.

It comes with a brand new theme for a better look, optimized operation, Firefox 3 with the 22/6-2008 updated Mediaplayer Connectivity plugin, select a username and password of your own choice and everything works out-of-the-box, and finally, eAR OS is now a real distro.

Enjoy and all the best,
[www.earos.dk](www.earos.dk)

---

### Post by rbolio on 2008-06-23
Okay, so, can the eAR media center be installed in Hardy?

And if so, is there any way to set it up to run with the dell media direct key?... seems like something many people would like to try (or atleast me...)



Cheers.

---

### Post by earos.dk on 2008-06-23
A dedicated repository is not important, because it has a repository and because it is not really for newbies to setup the media center and a .deb package can not do it fully (to let all back-end applications working out-of-the-box). With the eAR OS everythig works out-of-the-box, if the hardware is supported. You need to tweak a lot yourself when using a .deb package on Hardy.

eAR OS is using the Hardy repository, so you can do everything with the eAR OS that you can with Hardy.

---

### Post by smartboyathome on 2008-06-23
People want the repo though because they dont want to install a whole new os. I would say just release the media center and basic instructions, and the community can take care of the rest (editing them, making them easier to understand, etc). What ultimately should happen is that you release the source (in a tar.gz format) which lets users modify it and redistribute it, unless the eAR Media Center is not open source.

---

### Post by earos.dk on 2008-06-23
A .tar.gz file with some "ugly" source code and some "nice" is already on the Live CD, but it is not just so easy to move it to another distribution, because it is not made for that, except when tweaking a lot. The source code is a huge hack and forke of other projects that is assembled in one.

I can actually easily generate a .dep package, but the maintenance of it is bigger than making a distro that just works.

Currently, I don't have the time for another new project.

---

### Post by allforcarrie on 2008-06-23
> **smartboyathome said:**
> People want the repo though because they dont want to install a whole new os. I would say just release the media center and basic instructions, and the community can take care of the rest (editing them, making them easier to understand, etc). What ultimately should happen is that you release the source (in a tar.gz format) which lets users modify it and redistribute it, unless the eAR Media Center is not open source.

isnt this required under GPL? i dont realy understand i guess.


after downloading, the distro would not boot on my 80 gig IDE drive. Sad because i really wanted to check this out.

---

### Post by ptipton on 2008-06-24
Looks interesting will download and try tonight. Some questions on the TV front. I use both Windows MCE and MythTV (with XBMC ( linux and xbox) and standard mythtv linux frontends), personally I find that MythTV's ability to run multiple frontends from a single backend to be a big advantage. Given this and the fact that digital TV is not yet available where I live makes me wonder whether support for mythTV backends has been considered for eAR?

---

### Post by Shane_S on 2008-06-24
I downloaded the distro yesterday via Bittorrent from your site and it would appear that i happened to get lucky and get the latest version as it's got Firefox 3 in it. Unfortunately though i did not have time to play with it other than booting up the live CD but I must say it is very nice looking from what i played with so far. And since it's based on Ubuntu Hardy It suits me perfectly. I can't wait to get home tonight so i can play with it and perform a real install. I did view some media though and the full screen play was perfectly smooth on my weak intel grafics chip on my test box. 

Keep up the great work!!!. 

Shane

---

### Post by earos.dk on 2008-06-24
# allforcarrie,

You may build your own .deb package. A tarbar is on the Live CD. Expect it will take a lot of time, because it is not yet prepared for that.

I believe the "boot problem" is as usual with all distros. Press ESC when you see Grub and edit the parameters. When you are up and running then edit /boot/grub/menu.lst. Remember to backup the menu.lst file.
If you can't boot from the Live CD in safe graphic mode, then you may save your time, because it may be difficult if you are not used to boot without the X-server and tweak...

--

# ptipton,
MythTV is too complicated for new users and here in Scandinavia Analog TV is closed in 2009. Most people here are using Digital TV. Then you can record to hard disk, indeed.

It is easy to add Analog TV yourself. See my comments here to this very new review:
[http://www.linux.com/feature/138508](http://www.linux.com/feature/138508)

, but you can't record Analog TV without adding a server yourself.

--

# Shane_S,
Thank you. It gives energy to continue :-)

---

### Post by uffe on 2008-06-28
I'm relatively new to Linux, have tried Freespire  2.0.8

Yesterday - by coincident - I saw eAR OS on the net, downloaded it and tried it. It looks great so I tried to install it.
That I cant! When I reach Apr. 87% it freeze or the install program just disappears. If I skip the languish packs I can reach apr. 94%. 

I tried on the same PC that I have run Freespire on with no problem. It's an  AMD Sempron 2800+ with 1gb ram and 250gb HD. I let it take over the entire HD 
I have tried deleting partitions and formatting the HD - in all it's more than ten times I tried installing and with no luck.

Any suggestions what I do wrong ???

Uffe   
:???:

---

### Post by earos.dk on 2008-06-30
Ensure you have an internet connection up and running,

Have patience during hardware configuration. If you have a fast machine it is fast, if you have a slow machine it is slow. Have patience during hardware config!

Here it works on all machines, including brand new iMac's and with the new Intel Atom CPU's.

If you have a brand new iMac and you want to get rid of OS X Leopard then you just need to add an option to get the sound to work and fetch Leopards binary MS WiFi drivers. Then it works on iMac Alu too and you are OS X Leopard Free :guitar:

---

### Post by uffe on 2008-07-01
> Ensure you have an internet connection up and running,
No problem - that worked perfect.
> Have patience during hardware configuration. If you have a fast machine it is fast, if you have a slow machine it is slow. Have patience during hardware config!
I have a lot of patience, but when the machine freezes - no response on mouse og keyboard. No activity on HD, CD-drive or internet conection  in more than 5 minits - I think I have been patient enough.
> Here it works on all machines
That don't help me mutch!!! 
> If you have a brand new iMac
I did not ask what you would like me to by!!

eAR OS look nice and I like the way the desktop and menu's are build. **_IF_** it had worked - It had been my favourite for the PC in the living room.

:(:(:( Uffe

---

### Post by earos.dk on 2008-07-01
Less than 15 minutes ago I installed eAR OS vers. 1.10b on a HP Pavilion zv6000, which belongs to my 11 year old girl.

I am writing from it now, but the Broadcom WIFI needs further investigation, similar to what the Broadcom of the iMac did. The Broadcom  worked in previous release, but it seems that the Ubuntu repository has disabled it. It may be blacklisted in /etc/modprobe.d/blacklist, I will find out. It is enabled in restricted drivers!

--

So far, I have not experienced any PC which could not install eAR OS.
What I can recommend is that you click the Control Center icon in the lower panel and then you UPDATE your system while you are running the Live CD. Do this BEFORE you click the install icon. Then you will get the newest installer from the Ubuntu 8.04 repository.

I know within the last week a new ubiquity installer has been released.

--

Else you may try to add acpi=force or acpi=off to the grub parameters.

Good luck.

---

### Post by uffe on 2008-07-02
> earos.dk
Thank you for trying to help. I have a lot of trouble both trying to install and the same time express my self in English ( I'm Danish and it would be much easier for me if I could find you on a danish forum !! )  Nevertheless, I've tried to follow your directions. When I'm lucky and get so far - with out it freeze - as open the controlcenter, there then is 40 updates. 
I've tried with all marked - that don't work - it freeze again. Is it just a single one I've have to mark or what???  

Uffe

---

### Post by earos.dk on 2008-07-02
Just mark Ubiquity, which is the Live CD installer.
Else it may require too much of your RAM.

Remember the Live CD is using Casper to boot into RAM.

Edit, By The Way: You can ask questions in Danish at [www.linuxin.dk](www.linuxin.dk)
I am there every day.

---

### Post by azurehi on 2008-07-02
After installing and updating the latest eAR version, including the restricted drivers, re-boot is to minimal resolution with no way to 1152x864 or higher, i.e., options not offered in "display".  I have tried with the correct monitor and video card but nothing changes...same message on re-boot.

After installation is completed I chose "restart" and removed cd  rather than choosing the other option of continuing to use live cd and then restating from live cd.  I don't know whether this would account for my problem.  thanks for any suggestions.

---

### Post by earos.dk on 2008-07-02
I am using Intel GPU's on all of my machines and 
ATI where I am forced to.

The problem is the restriced drivers or it is nVidia's problem.

Bad answer, I know, but I can't help to solve nVidia's or ATI's problems.
They should deliver better drivers for their GPU's.

Edit:
I may not understand the problem.
After install then you must remove the Live CD.
The first to do, after you reboot from the hard disk, if you are using nVidia or ATI, it is to enable its restricted driver.
After that then restart the X server or just reboot as suggested.

PS: During install the restricted driver is disabled by the Ubiquity installer and therefore you have to enable the restricted driver again, after reboot from the hard disk. Ubiquity is made in that way.

---

### Post by riromero on 2008-07-03
I'm running the live CD just now. Works perfectly on my hardware out of the box as advertised.

One simple question: How can DVD and CD cover art be included in the movie and music listings? I see that in the screenshots on the webpage. If this works correctly, I'm sold. 

- Reuben

---

### Post by earos.dk on 2008-07-03
Put the cover art into the folder where the CD has been ripped automatically.

Fetching cover arts automatically goes wrong 10% of the time. 
Therefore you should do it manually. Go to for example [http://www.cdcovers.cc/](http://www.cdcovers.cc/) and right-click to save the cover art in the folder with a ripped DVD or downloaded movie or a ripped CD.
Then you will browse through cover arts and the screen saver will show the CD cover of the playing music :guitar:

---

### Post by riromero on 2008-07-03
It doesn't work for me. If I place the jpg image from cdcovers.cc (or any jpg image) in the directory the glowing blue folder icon is replaced by a small, very dark blue square. Oh well, thanks anyway.

- Reuben

---

### Post by earos.dk on 2008-07-04
Of course it works for you, if you save a a .png or a .jpg in the folder with the music tracks.

Next time the media center is started its database will be initialized with the new images.

But anyway, it is not the best way to do it. The eAR RT-OS Enterprice Edition has a program that will fetch cover arts and ensures all images are equal in size and gives them mirror reflections. This program is not  included in the Free Edition and will not be that.

---

### Post by uffe on 2008-07-04
> Just mark Ubiquity, which is the Live CD installer.
Else it may require too much of your RAM.):P

Hej.
All my troubles must have been in the AMD processor !!

I have another PC with a Pentium4 processor and 2Gb ram.

I disconnected the HD and put an old 6,4Gb in instead. **YES** - followed your instructions and all ran smooth. 

As far as I can tell until now, all works perfect. I only have one problem: I can't find out to connect to our home network. I can connect to the internet and I can find "windows network" but underneath it says "unknown type". Oh yes, why don't "help" work anywhere ?


PS.  This is posted from inside eAR OS.


Kindly regards

---

### Post by uffe on 2008-07-04
OK. when my wife turned on her PC, suddenly I could see the network.
We have a extern HD in the network. I't cant be seen or accessed if there's not a windows pc is open on the network. That was no issue in XP. Why???

Uffe

---

### Post by tijmz on 2008-07-04
This thread was bumped with perfect timing :)

I'm going to check this out, but can anyone tell me whether the media center is extendable, i.e. are there plugins that allow you to browse Flickr, Picasa et cetera from the photo menu, YouTube and Vimeo from the video menu, and so on?

If so, this might be exactly what I've been looking for for weeks :D

---

### Post by jellisii on 2008-07-04
Hi,

I apparently had an older 1.09 (I think.  Where can I find a version number?) iso on my drive when I decided to install earos.  I'd like to upgrade to 1.10, but there seems to be no option for this short of downloading the entire .iso.  I did run the update manager as suggested on the update section of the earos.dk website.  

I am trying to assign my music folder to a smb (Currently.  I will probably configure NFS on the mac that's hosting all the data at some point) share on another machine.  I tried adding the line audio_dir = smb://machine/path/to/music, to /home/earmusic/.mms/config and restarting the media frontend, but it states "Could not find any music".  I know I have .mp3 files in the folder to which I am pointing.  Rebooting did not resolve this issue.

I like the setup, tho.  It gives a nice clean frontend for a PC attached to my TV.  Web browsing on the couch is nice. :)

---

### Post by earos.dk on 2008-07-04
AMD CPUs works, it may be nVidia that is the problem.

Flickr is in the More menu. You can add Google Picasa yourself, it is very  easy to extend this menu to whatever you wish.

Add symlinks to external drives, USB- or Network drives or whatever you like and you can access the media files inside the media center.

--

Written from eAR RT-OS running on the new 4 Watt Intel Atom CPU (it runs fast) connected to the Logitech diNovo Mini, 
what an ultra-small keyboard :)



Edit - crosing posts
1.10 has been pretty much re-factored, because some did not like a pre-selected password. That was a huge change and therefore it is not possible to upgrade without installing the live cd one more time.

---

### Post by riromero on 2008-07-05
I now have everything working thanks to the help given here. Very nice! For me this is much better than MythTV. Some simple questions...

I would prefer mplayer to kaffeine for playing DVDs and videos. In the ~/.mms/config file there are multiple references to mplayer but regardless
of the settings kaffeine is always called. It looks like kaffeine is hardcoded in the /etc/ear/kaffeineplay*.sh scripts, but I'm no expert. Is there a simple way to use mplayer without modification of the shell scripts?

Also, I would like the eAR interface to run automatically after booting. Is there an easy way to do this?

- Reuben

---

### Post by earos.dk on 2008-07-05
Replace kaffeine with mplayer to play DVD:

Open a terminal and 
```
sudo gedit /etc/ear/kappeineplayDVD.sh
```

and replace the content of the file with:


```

#!/bin/bash
#
# Parameter for mPlayer:
# Stereo:       -channels 2
# Quadro:       -channels 4
# 5.1 Surround: -channels 6


# Disable screensaver
gnome-screensaver-command -d 

# Example: With Norwegian subtitles and 5.1 surround
mplayer -fs -zoom -vo xv -af volume=-26 -pp 0 -sub no dvd:// -channels 6

```




Autostart: 
Click the Control Center icon in the buttom panel and enter Sessions.

Now you should add ```
/etc/ear/./start-eAR.sh
```

and the media center will autostart every time to boot.

---

### Post by earos.dk on 2008-07-05
I forgot :-)

Replace kaffeine with mplayer to play video files stored in the /home/your-username/eAR-Video folder:


Open a terminal and write:

```
sudo gedit /etc/ear/kaffeineplayfile.sh
```


And replace the content of the file with

```

#!/bin/sh 

# Disable screensaver
gnome-screensaver-command -d 

# Let mplayer play the movie, add surround, if you like!
mplayer -vo x11 -fs "$5"

```

It is a good idea to backup the original scripts before you edit.

Furthermore:
You must fine-tune the parameters to mplayer yourself.

For example, you may want to use surround, or stereo, or ......
, you may want to use another video driver than xv or x11
, you may want to change the default 20mSec front/rear delay, 
, you may want subtitles in your language
and ................



AND you for sure want consistency in the operation. for example we use "f" for higher volume, "l" for lower, "end" to quit, etc.

Therefore you should replace the content of the /etc/mplayer/input.conf with the following:

```

##
## MPlayer input control file
##
## You are able to redefine default keyboard/joystick/mouse/LIRC bindings, or
## add new ones here.
## See DOCS/tech/slave.txt for possible commands that can be bound.
## Also see mplayer -input cmdlist for other possible options.
## The file should be placed in the $HOME/.mplayer directory.
##

RIGHT seek +10
LEFT seek -10
DOWN seek -60
UP seek +60
PGUP seek 600
PGDWN seek -600
m mute
# switch_audio          # switch audio streams
+ audio_delay 0.100
- audio_delay -0.100
[ speed_mult 0.9091	# scale playback speed
] speed_mult 1.1
{ speed_mult 0.5
} speed_mult 2.0
BS speed_set 1.0	# reset speed to normal
q quit
ESC quit
END quit
ENTER pt_step 1 1       # skip to next file
p pause
. frame_step            # advance one frame and pause
SPACE pause
HOME pt_up_step 1
##END pt_up_step -1
> pt_step 1             # skip to next file
< pt_step -1            #         previous
INS alt_src_step 1
DEL alt_src_step -1
o osd
I osd_show_property_text "${filename}"     # display filename in osd
z sub_delay -0.1        # subtract 100 ms delay from subs
x sub_delay +0.1        # add
l volume -1
9 volume -1
/ volume -1
0 volume 1
* volume 1
f volume 1
1 contrast -1
2 contrast 1
3 brightness -1
4 brightness 1
5 hue -1
6 hue 1
7 saturation -1
8 saturation 1
( balance -0.1          # adjust audio balance in favor of left
) balance +0.1          #                                  right
d frame_drop
r sub_pos -1            # move subtitles up
t sub_pos +1            #                down
#? sub_step +1		# immediately display next subtitle
#? sub_step -1		#                     previous
#? sub_scale +0.1	# increase subtitle font size 
#? sub_scale -0.1	# decrease subtitle font size                  
s vo_fullscreen
T vo_ontop              # toggle video window ontop of other windows
w panscan -0.1          # zoom out with -panscan 0 -fs
e panscan +0.1          #      in
S screenshot            # take a png screenshot with -vf screenshot
                        # S will take a png screenshot of every frame

h tv_step_channel 1
l tv_step_channel -1
n tv_step_norm
b tv_step_chanlist

##
## GUI
##

#l gui_loadfile
#t gui_loadsubtitle
#a gui_about
#s gui_stop
#p gui_playlist
#r gui_preferences
#c gui_skinbrowser

##
## Joystick section
## WARNING: joystick support has to be explicitly enabled at
##          compiletime with --enable-joystick
##

JOY_RIGHT seek 10
JOY_LEFT seek -10
JOY_UP seek 60
JOY_DOWN seek -60
JOY_BTN0 pause
JOY_BTN1 osd
JOY_BTN2 volume 1
JOY_BTN3 volume -1

##
## Apple Remote section
##

AR_PLAY pause
AR_PLAY_HOLD quit
AR_NEXT seek 30
AR_NEXT_HOLD seek 120
AR_PREV seek -10
AR_PREV_HOLD seek -120
AR_MENU osd
AR_MENU_HOLD mute
AR_VUP volume 1
AR_VDOWN volume -1

##
## OSD Menu movement keys
##
## If you are using only the keyboard it is enough to define one command (like
## "menu up"), because then that single key will display the menu, which can
## then be navigated with the cursor keys and ENTER.
##
## LIRC users should bind each "menu" command to a button on their remote.
##
## The set_menu command directly displays the (sub)menu specified as
## its argument. Usage should be self-explanatory (although not likely
## to be needed), after reading input.conf.
##

#MOUSE_BTN0 menu up
#y menu down
#y menu ok
#y menu cancel
#y menu hide
#y set_menu general_pref

##
## DVDNAV
## Requires dvdnav://
##

KP8 dvdnav 1            # DVDNav UP
KP2 dvdnav 2            # DVDNav DOWN
KP4 dvdnav 3            # DVDNav LEFT
KP6 dvdnav 4            # DVDNav RIGHT
KP5 dvdnav 5            # DVDNav MENU
KP_ENTER dvdnav 6       # DVDNav SELECT (ok)
KP7 dvdnav 7            # DVDNav PREVIOUS menu (in the order chapter->title->root)

#? seek_chapter -1      # skip to previous dvd chapter
#? seek_chapter +1      #         next

```


Well, you asked, it is easier to use kaffeine :-)

---

### Post by arvvvs on 2008-07-05
As some help, you may want to look at Elisa Media Center.  It's installable as a .deb and has some great plugins, such as youtube, and f-spot.  Since its open source you might be able to use portions of it.

I'm gonna try your distro out soon.

---

### Post by tijmz on 2008-07-05
I second that. Integrating Elisa in your distribution would be a great idea and might benefit both products.

---

### Post by earos.dk on 2008-07-05
Thank you for the suggestion. I have been looking into that in more than a year, but there are some major issues:

1) Elisa is using Gstreamer plugins and they sound IMO very awful and crappy. It is not audiophile sound quality.

2) Elisa can not play DVD or DVB TV without purchasing extra plugins. However, I fixed that with a system call from Python, it worked.

3) It has too many bugs and IMO it is not yet stable.


But I like their GUI principle and it would be simple to design a new theme that looks much better.

--

I will take a look into it one more time and check how much it has been improved, but currently, I am satisfied.

--

BTW: It is okay to force users to have hardware that supports OpenGL. Else it will not work, eAR does.

---

### Post by riromero on 2008-07-05
Perfect. Thank you. 

Some comments regarding Elisa...

In my quest for the perfect media center I've tried:

MythTV - Powerful, complex backend that works well as a PVR. For music and video though, the frontend is not so great. Mythmusic is simply abysmal. There is no way my wife and kids are going to use it.

Elisa - Beautiful frontend. Unfortunately there isn't much power underneath. It doesn't support playing DVDs. It freezes with about 1/4 of my media collection. I have a digital audio receiver and spent considerable effort getting it to work with my sound card. With Elisa it's broken again and there is no way for me to simply change a shell script to fix it. I find that the Elisa configuration files are also non-intuitive; you cannot make useful modifications without knowing the magic words.

I installed eAR a few days ago and now I almost have the configuration I was looking for. Everything works! Even my wife and kids are using it now.

Next, I will add an IR remote and my ideal Media Center will be complete.

- Reuben

---

### Post by tijmz on 2008-07-06
> **earos.dk said:**
> 1) Elisa is using Gstreamer plugins and they sound IMO very awful and crappy. It is not audiophile sound quality.

2) Elisa can not play DVD or DVB TV without purchasing extra plugins. However, I fixed that with a system call from Python, it worked.

3) It has too many bugs and IMO it is not yet stable.

[...]

I will take a look into it one more time and check how much it has been improved, but currently, I am satisfied.
It's still based on Gstreamer and it still lacks DVD playback. The latter is supposed to be fixed in the upcoming version (0.5), [along with other stuff](https://launchpad.net/elisa/+milestone/0.5.1). I don't know when 0.5 will be released, but since there are win32 0.5.1 alpha builds available from the Elisa site I figure it won't be long.

Until then, I share many of your reservations about it (although I've never had any stability problems). With the embedded YouTube/Flickr browsing and the (claimed) modular architecture I think they're on the right track, though.

But let's not derail this thread about Ear OS to a discussion about Elisa by itself. I gather from your post that Ear OS does not use Gstreamer. Does this mean it will be difficult to keep the Ear OS distro intact and install Elisa at the same time? Sorry if it's a stupid question, I'm just not that knowledgeable about these sort of things.

---

### Post by arvvvs on 2008-07-06
I just installed eAR OS and so far so good.  Speedy, cool looking.  
My only complaints so far are that there is no graphical deb installer, and some functions such as synapatic are missing.  I believe that they were removed for extra security but I miss them.  Also because of synaptic I can't install compiz and configure it.  
But I do like the folder icons the earlier version of eAR.  It made it look much more orignal, and not copied off mac icons.

[http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)  Some more good software you can incorporate is Facebook Chat integrated into Pidgin.

---

### Post by riromero on 2008-07-06
All the basic stuff is there, it's just not listed in the menus. If you right click on the top menu and choose "Edit Menus", you can unhide Synaptic, any of the standard Ubuntu administration tools, applications, whatever.

- Reuben

---

### Post by arvvvs on 2008-07-06
Thanks.
But my other problem is whenever I'm in the media center and click on music it says Could not find any file.  "Please specify directory in teh config file."  Where is this config file and how do I use it.

Wait I ran the wizard.sh, and now it works.  It should be setup in teh installation, or at first logon.

Another thing: Try to include some form of widgets.  Widgets help alot, although there are few really good ones.  Google just released theres but its buggy and glitchy, KDE 4 is gonna have a good one though.

---

### Post by earos.dk on 2008-07-06
Compiz, its setting manager, Synaptic, etc.: Everything is there.
Just click the Control Center icon in the buttom panel.

(or you can unhide the usual icons in the Gnome top panel menu).

Compiz is not turned on by default, because I don't want to spend extra resources on that when running the media center, but you can enable it yourself. If you do, then you should let the Gnome top panel autohide (right-click the panel). Else you can see it in the media center, but you can't access it without switching to another work space.


Pidgin is there too.


The only thing you need to install yourself, because of Live CD disk space issues, is OpenOffice and Skype, and then the icons in the buttom will work:

```
sudo apt-get -y install openoffice.org skype
```


You can also install Elisa from Synaptic. It will run, but without DVB TV and DVD playback.

---

### Post by tjharring on 2008-07-08
I just tried to install eaR OS. When it gets to the point of asking what language, I select English, and the system never moves. The indicator keeps spinning drive lights flash but the install never proceeds. Is there something I'm missing?

---

### Post by arvvvs on 2008-07-08
Well heres a suggestion you can use from Elise.  iPod Control.  It might help if EAR had iPod control, or MP3 player control

---

### Post by earos.dk on 2008-07-08
> I just tried to install eaR OS. When it gets to the point of asking what language, I select English, and the system never moves. The indicator keeps spinning drive lights flash but the install never proceeds. Is there something I'm missing?

Strange, Which kind of hard disk are you using, IDE or SATA?

Here it installs on a ton of very different machines, but I have not tried all hw in the world.

In case of any install problems please use the update manager to update the Live CD while it runs live in RAM.
Update ONLY the **Ubiquity** installer and not everything else that the update manager suggest.
After install to hard disk you should run the update manager and update everything.

---

### Post by tjharring on 2008-07-09
> **earos.dk said:**
> Strange, Which kind of hard disk are you using, IDE or SATA?

Here it installs on a ton of very different machines, but I have not tried all hw in the world.

In case of any install problems please use the update manager to update the Live CD while it runs live in RAM.
Update ONLY the **Ubiquity** installer and not everything else that the update manager suggest.
After install to hard disk you should run the update manager and update everything.

I am using 2 60g IDE drives, master, slave. The system is a Dell Optiplex, P3, 512mb ram. I have installed 2 other distros, Suse 10.2, Kubuntu on this system. I will not be able to try this again until the weekend. I will try to update the live cd before running install this time.

I will let you know how I make out. Thank you for the response and the suggestion.

---

### Post by riromero on 2008-07-12
I've been playing with my IR remote (Streamzap IR) for several hours now. I notice that the ~/.lircrc configuration uses irxevent to send the key codes. If I try to send them to eAR directly it doesn't work. So I'm guessing that, unlike MythTV, lirc support isn't compiled into eAR and the key-press events can only be sent through the window manager. It would be cleaner (and easier to configure) if lirc were compiled in and the controls for eAR, kaffeine, mplayer, etc. could each be configured seperately. Any chance of this?

- Reuben

---

### Post by riromero on 2008-07-13
I believe there is a bug in the eAR distribution. The DVD autoplay didn't work so I poked around. Using gconf-editor I see that autoplay_dvd_command is set to home/earmusic/.ear/./kaffeineplayDVD.sh which doesn't exist.

I believe this should be /etc/ear/kaffeineplayDVD.sh.

- Reuben

---

### Post by earos.dk on 2008-07-20
#riromero,

You are correct. This minor "bug" will be corrected/deleted in a future distribution release, the user may be forced to set up the auto-playback himself. 
Previous it worked when the user was forced to use earmusic to be the username.

Regarding lirc this is a matter of taste and policy. Today, it works with almost all applications that does not support lirc.

---

### Post by CbrPad on 2008-07-26
I loved the look of this and it worked great on the live cd (latest version 1.10) so I gave it a whiz installing.

I've got 3 partitions - swap, /, /home

I wiped all existing config files from my /home and just left data before installing.

Everything seemed to go ok and on rebooting the bootsplash and gdm login screens were fine, but when I logged in all I found was a basic gnome setup, a plain brown background with no wallpaper, default panels top and bottom, etc.  

I could go into appearances where there was one theme present but it wasn't actually applied. I had to click 'Customise' and apply the window borders, icons, etc, manually.  

The dock isn't launched, it's present in the menus, but contains only Firefox and one other launcher by default.   

The EAR media centre doesn't appear to have been installed at all.

I've added my usual 4 workplaces and a workspace switcher, but cannot switch between them at all, despite being able to move apps by clicking on the menu options and telling them to move to another workspace.  Once there I can no longer access them.

Any ideas as to why I've gotten these issues?  I've installed it twice, first time with default settings (but adding my own username and manually changing the partitions), the second I updated Ubiquity then installed choosing the same options.

Thanks in advance !

---

### Post by earos.dk on 2008-07-26
You never booted the partition with the eAR OS.

If you have another hard disk, then make a clean install without other distributions.

--

Tomorrow, I am going to Rhodos in Greece to dive. When I return I will prepare a new release with updates from the past two months.

---

### Post by Clint_E on 2008-07-27
I can't get my MCE Philips SRM 5100 remote to work with ear OS??
/dev/lirc isn't created, have the same problem with mythbuntu 8.04...  is there some thing I have missed - I thought the philips mce remotes should work out of the box?


BR

Clint_E

---

### Post by CbrPad on 2008-07-27
> **earos.dk said:**
> You never booted the partition with the eAR OS.

If you have another hard disk, then make a clean install without other distributions.

--

Tomorrow, I am going to Rhodos in Greece to dive. When I return I will prepare a new release with updates from the past two months.


Hi, I have three partitions...

sda1 - swap
sda2 - /
sda3 - /home


I removed all config data (for Hardy which I had been using) from sda3, hidden files, the lot - basically everything except personal data.  

I then installed eAr choosing sda3 as /home once more and sda2 as /, making sure that sda2 was formatted in the process.  

I've tried this several times now with the same result and there are no other distros installed.  I've installed many distros this way and have never had this problem before, it simply seems to be failing to properly configure itself somehow ?

Looking forward to the next release !

---

### Post by CbrPad on 2008-07-30
Btw, I've just picked up an Advent / Msi Wind and installed on that using the default options and there were no issues with configuration of the UI.  It doesn't seem to pick up bluetooth or webcam tho but I'm not worried about those and I can't say about wifi as I don't have that.

---

### Post by yragrelluf on 2008-07-31
I love eAROS so far, but the media center wont launch. I think gtkorphan messed it up. This is what my terminal says-

xxxx@xxxx-laptop:~$ /etc/ear/./start-eAR.sh
eAR: no process killed
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/xxxx/.DCOPserver_xxxx-laptop__0
and start dcopserver again.
---------------------------------

KDE Daemon (kded) already running.
kbuildsycoca running...
Reusing existing ksycoca
xxxx@xxxx-laptop:~$ eAR: error while loading shared libraries: libccgnu2-1.6.so.0: cannot open shared object file: No such file or directory

any suggestions without reinstalling and then not using gtkorphan, because I dont want to add and remove apps and music and pics again?

---

### Post by calibre97 on 2008-08-03
Fired up the live CD last night and I like it. Now I'm ready to try installing, but I'm a little confused. I have an existing setup as follows:
Primary partition (from when this was an XP laptop):
/sda1 is 30GB /BLAH for data
Begin extended partition:
/sda5 is a 10GB blank, ext3 formatting partition, for another distro such as eAR OS]
/sda6 is 13GB /home for Kubuntu
/sda7 is 13GB / for Kubuntu
/sda8 is 2.5GB swap
/sda9 is 80GB /BLAH2 for my XP and other VMs

So what I want to do is install eAR media center to /sda5 and add a line to GRUB so I can boot to Kubuntu still or to eAR media center. The install instructions appear to favor installing this to a whole drive. Anyone have any thoughts/experience with installing this to a partition that's part of an existing installation? I was going to try making a new VM for this but figured that'd be way off the optimum path so I'll try putting it into /sda5. I know the guys are in Greece now so I'll grab a new Live CD when it's available when they return.

UPDATE: Clicked Install icon on desktop from Live CD. At partition step, it offered to claim a chunk of /sda9 (which is 80GB). My question is, how big a partition does this thing need? The chunk it wants to take is 35GB, leaving me with 45GB. I'm guessing I won't be able to pop this into little ol' 10GB /sda5. Any guidance as to the size of the partition for this? I can of course share the swap partition, and I figure I'll put everything into /sda5 (/, /home/, /usr, etc).

---

### Post by earos.dk on 2008-08-04
yragrelluf,

Please read the README-FREE.TXT file or

1) Press ALT F2
2) Run the following command: /etc/ear/./ear-recover.sh


That will fix the database and you don't need to install your media files one more time.

---

### Post by calibre97 on 2008-08-05
Well, I said ta heck with it and ran the installer. Took up only about 2.5 GB. I plan on having any media files on a different disk so space shouldn't be an issue. 

I put in my own login name and password, though, contrary to the instructions and it seems to be working so far. My Broadcom wireless was detected by the install just fine and although DHCP worked at first, I had to change to fixed IP after rebooting after a mega update (125MB over 127 items!). I'm downloading openoffice right now and will work on enabling the multimedia items (installing css, getting gnome-audio package, that kind of thing) next. So far it's pretty darn nice I gotta say.

The main thing now is getting my sources list right. That always seems to be the issue. You can't get anything if you don't know about it and not everything seems to be presented with an easy "Select if you want it" checkbox. But I'm not worried because these forums are simply the best...and I normally run Kubuntu! Whatever they're running for that forum just gets in the way AND I don't think as many people participate.

Anyway, I'm up and running, albeit with this mainly as just another distro rather than a Media Center box.

---

### Post by Glyndwr on 2008-08-14
I have this installed and for the most part I am pretty impressed.    The only problem I am having is I have no sound for mp3's or internet radio stations.  Sound works fine for DVDs and video files and when I come out of ear OS I have sound with mp2s using kaffiene and exaile.

Anyone know what program this uses for playing mp3s?  I had assumed it was kaffiene but maybe I'm wrong.

That's my only problem everything else works - I just wish there was some documentation or some forums dedicated to this product where you could go to look for answers.

---

### Post by earos.dk on 2008-08-15
Certainly, the sound from Internet radio, FLAC and MP3 playback works.
And I have never heard about this problem before.

Please check the volume of the media center (use "f" for higher sound and use "l" for lower sound). I believe that's the problem, because the media center ships with low volume near to zero to avoid someone would blow out the loudspeaker drivers.


Turn up the sound volume inside the media center with "f".

---

### Post by Lem on 2008-08-21
Looks a promising release, but sadly the install cd just drops me out at a grub prompt. No grub menu at all.
I've tested the cd against the md5 sum and it's all good.

Any ideas?

---

### Post by Lem on 2008-08-22
Downloaded it again. Found a 1.09 release on torrent. Tried a different pc.

The same result every time. ??

---

### Post by earos.dk on 2008-08-23
A new release is coming pretty soon. It supports more hardware.

The installer will run on Intel Atom CPU too, the current version does not.

---

### Post by Lem on 2008-08-24
It was the grub bootloader. Stuck an IDE CD drive in and it worked ok.

earOS is interesting, but not for me. The media centre application lacks a little polish compared to some offerings out there, but the idea of a ready-to-run media distribution is highly commendable.
I feel you might do well to maybe base your media centre on something like xbmc, rather than re-inventing the wheel so to speak.
You could easily re-skin xbmc and a mythtv frontend plugin with an integrated backend would be a better tv solution than kaffiene based player.

I'm also intrigued by the use of the rt kernel. Is there real benefit from doing this? I'd never thought of using it before.

For what I want, the best solution still appears to be the 'roll-your-own' setup with a grpahically tweaked ubuntu install with xbmc/boxee and mythtv.

However, I will keep an eye on earOS. I like the idea.

PS. I love your amplifiers!

---

### Post by inhaladibilul on 2008-08-27
earos.dk when should we expect the new version, the one you mentioned earlier ?

Thank you.

---

### Post by robert shearer on 2008-09-03
eAR-OS is just what I was looking for and installed fine.
The realtime kernel makes such a difference, no more coasters!!.

Three small problems,,

1) A process called 'atieventsd' keeps writing to disk every 5 seconds or so.This happens when the computer is idle, stops when a major disk read/write happens then starts again.
 "Killall atieventsd" stops it with seemingly no other side effects but it returns on every reboot and must be killed each time.

2) the 'sysklogd' system logging daemon keeps failing and has to be reinstalled on each boot.

3) A lot of zombie processes appear and it seems that each time an app is started from the sim-dock it causes the sim-dock to restart and zombies the old one.  Currently I have 5 zombied sim-docks showing in the processes tab of the system-monitor. They're not consuming any memory so I am not too worried, and they go away on reboot but it would be good to know what is causing this??.


Update,   Seems that the ATI driver is enabled as default and if you have a non supported older card or NVidia card then the atieventsd daemon is forever looking for well, events!. Solved by uninstalling the ATI driver using Envyng.


Found another oddity, the firewall isn't enabled at each boot.Must be something in the configuration as even uninstalling firestarter and re-installing ufw won't create a firewall that is persistent.

Also noticed that the install hangs or fails if a net connection is not available. Make sure that the firewall is started from the live cd and your modem/broadband connection is active and then start the install.
Seems that some additional language and locale packages have to be downloaded for the install to complete.

---

### Post by miketowninc on 2008-09-05
Is there still no way to install it via apt-get? I really dont want to waste a cd if I dont end up liking the OS!!

---

### Post by uffe on 2008-10-12
You could use a RW disk or a USB-pen, on the other hand - disks is'nt that expensive :)

---

### Post by uffe on 2008-10-12
This was posted August 23rd, 2008> **earos.dk said:**
> A new release is coming pretty soon. It supports more hardware.

The installer will run on Intel Atom CPU too, the current version does not.

How would it be fair to define "soon". Is it weeks or several months?

Has **earos.dk** lost interest in his own project? Nothing happens on his homepage [http://www.earos.dk/]("http://www.earos.dk/") - it would be nice with a little update/roadmap under "News" or will it be "just another discontinued dist" ??  I hope not, I'm looking forward to see a 64 bit version - is my hopes too high ?? ( I would hate to have to use Myth -don't like it! and the other alternatives don't work well enough)

A in all other ways happy user
Uffe

---

### Post by robert shearer on 2008-10-17
[
> Has **earos.dk** lost interest in his own project? Nothing happens on his homepage [http://www.earos.dk/]("http://www.earos.dk/") - it would be nice with a little update/roadmap under "News" or will it be "just another discontinued dist" ?? 

Looks like it. Maybe the only support is on the 'enterprice' edition??.

Query, do check the "software sources" listing. System=>Admin=>Software sources

Some strange listings here??? 

I have stopped using this distro until I can find some answers or an alternative support page.

Anyone know of one?

---

### Post by Morbis on 2008-10-31
Hello from Russia!
Sorry for my English. 
Cool product, but how to enable support cyrillic fonts? Without this can't give full pleasure from use eAR OS!
Thank you!

---

### Post by uffe on 2008-10-31
> **Morbis said:**
> Hello from Russia!
Sorry for my English. 
Cool product, but how to enable support cyrillic fonts? Without this can't give full pleasure from use eAR OS!
Thank you!

If you run it from a liveCD you have to choose languish at the start. If you all ready installed it must be in "Controlcenter" - "Languish support"

---

