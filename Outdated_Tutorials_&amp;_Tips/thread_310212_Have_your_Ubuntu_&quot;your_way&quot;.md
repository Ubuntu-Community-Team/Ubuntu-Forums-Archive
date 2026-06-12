---
title: "Have your Ubuntu &quot;your way&quot;"
date: 2006-11-30
forum: Outdated Tutorials &amp; Tips
---

### Post by TheeMahn2003 on 2006-11-30
I am a programmer of the [reconstructor team]("http://reconstructor.aperantis.com/") I have built a version of Feisty Fawn (dvd Edgy Eft upgraded) can be used with any version of Ubuntu I have also set up a website and host the current release that has every thing listed here plus more listed on my [website]("http://ubuntusoftware.info/"):

[LIST]
[*]Integrated codecs (the good the bad & the ugly)
[*]Flash player 9 beta
[*]Java
[*]Adobe Acrobat reader
[*]Mplayer, VLC, Songbird & Amarok players
[*]Mencoder, K9Copy, DeVeDE, DVD Shrink - dvd copying software.
[*]Google Earth
[*]Integrated Nvidia drivers (will work with other cards)
[*]Beryl (icon on desktop of live DVD / CD to initiate works with Intel cards currently, Nvidia is coming!!!)
[*]Automatix 2 & Automatix Bleeder (in case you want additional software)
[*]Gaim beta 5 & plugins
[*]GFTP - FTP Client
[*]KVIrc - IRC Client
[*]Additional Themes and a new look for the installer (Christmas)
[*]XSnow - got to love Christmas
[*]Samba
[*]NFS
[*]EasyTag - MP3 Tag Editor
[*]GDesklets
[*]Inkscape - 3D modeling software
[*]Screem - HTML Editor
[*]Gambas - Programing environment
[*]QEMU & Kqemu Accelerator - Emulation
[*]Screem - HTML Editor
[*]Avidemux - Avi (divx /xvid) editor
[*]GDesklets - Eyecandy & info
[*]NTFS read / write support
[*]Lamp - web server (Apache2, mysql, PHP5)
[*]phpmyadmin
[*]Azureus - P2P software
[*]MS core Font's and extra fonts
[*]Wine - Windows emulation
[*]Alien - Allows installation of foriegn packages (RPM, suse etc)
[*]Gobby Team programing software
[*]Ksnapshot - Screen capture software
[*]Google Picasa - Graphic editing software
[*]Frostwire Pro - P2P software
[*]Kolourpaint - Paint shop pro on roids
[*]Qcad - Autocad wannabe
[*]Archive Suite - virtually any archive can be handled.
[*]Ajunta IDE - Programing environment
[*]Bluefish - HTML Editor
[*]Glade - Interface designer
[*]Gtranslator
[/LIST]

Reconstructor is NLite is to windows.  The customizations are virtually endless additional features are added / removed by rmod (similar to a bash script).  I create modules daily however will not post them to [reconstructors website]("http://reconstructor.aperantis.com/") until fully tested thank god for dvd-rw's.

**Getting Started**

1. Obtain [reconstructor software]("http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=select&id=5")

2. Grab any [additional modules]("http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=select&id=4") you may want added. Put them in /usr/share/reconstructor/modules

3. Applications >> System Tools >> Reconstructor >> click next

4. Check all three boxes first time only.

5. Click browse button and select your [ubuntu.iso]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download")

6. Click next & wait... Takes a long time progress can be viewed in the terminal.

**_Ubuntu your way_**
Via Tab

_Boot Screen_
From this tabbed screen you can adjust many things such as the color of the text on the boot screen as well as splash screen.

_Gnome_
Login:
GDM login, Splash screen and initial background color can be changed I suggest a browse through [gnomelook.org]("http://www.gnome-look.org") to customize the appearance.

Desktop:
Desktop wallpaper can be changed here as well as fonts.

Theme:
You can change the overall theme & icons of your Live CD / DVD such as the chrome theme screenshots below.

_APT_
Here you can enable all repos so by default the DVD / CD & when installed will have them enabled as well as add custom repos.

_Optimization_
Here you can stop services from running off disk as well as installed such as you may have no need for wireless etc.  Tweaking if you will.

_Live CD_
Here you can enter a default username / password etc.

_Modules_
This is the real meat & potatoes of the software...  This section allows adding / removing software from the Live DVD / CD.  This will only get better as time progresses & more modules become available (currently 52).

Once you are satisfied with all the options etc. you have set hit apply and it will build it for you (once again a long time).  Once completed you can click next and it will create the iso as well as burn it if you so desire.

That's it enjoy Ubuntu "Your Way".

I have added a FAQ that may further assist you located [here]("http://ubuntusoftware.info/faq.html").

---

### Post by wolfchri on 2006-12-04
"Have you Ubunu "your way""

--> is there maybe a "t" missing in "Ubunu" ? :mrgreen:

---

### Post by wolfchri on 2006-12-04
I have a question regarding reconsturctor "modules":

Are they installed in a way that the software they add to the system can be adminstrated via apt/synaptic?

For instance, will the w32codecs installed by the module be updated when I do a "apt-get update && apt-get dist-upgrade" ? Is there the w32codecs .deb package? Or not?

---

### Post by DC@DR on 2006-12-04
This is pretty neat and handy stuff. Will check it out soon, thanks :-)

---

### Post by TheeMahn2003 on 2006-12-04
> **wolfchri said:**
> I have a question regarding reconsturctor "modules":

Are they installed in a way that the software they add to the system can be adminstrated via apt/synaptic?

For instance, will the w32codecs installed by the module be updated when I do a "apt-get update && apt-get dist-upgrade" ? Is there the w32codecs .deb package? Or not?

I'm unsure if there is a .deb of the codecs but if there is yes apon installation would be upgraded.

---

### Post by pietro_spina on 2006-12-05
> **TheeMahn2003 said:**
> 
I am a programmer of the [reconstructor team]("http://reconstructor.aperantis.com/")


what? you mean I can have my cake and *share* it to? thanks.

-p

---

### Post by TheeMahn2003 on 2006-12-05
> **pietro_spina said:**
> what? you mean I can have my cake and *share* it to? thanks.

-p

You sure can ;)  Uploading it as I type 2nd time failed first time no resume :( once uploaded I will provide a link to download it.  We have another host as well both high speed connections :)  Special Thanks goes out to the hosts Coldbird and hopspitfire, I will give them credit in the initial post once they are uploaded & serving.

---

### Post by TheeMahn2003 on 2006-12-06
hopspitfire now has it on his FTP please extract it to an .iso and provide download details...

---

### Post by TheeMahn2003 on 2006-12-20
A long time since a post just as an update I have released a downloadable version of the initial post with so much more you can view added additional software from my website [here]("http://ubuntusoftware.info").

---

### Post by aysiu on 2006-12-20
> **TheeMahn2003 said:**
> Apologies for the misspelled title, should read Have your Ubuntu your way and no way to edit it ;)  Hopefully a moderator will read this... Read and fixed.

---

### Post by TheeMahn2003 on 2006-12-20
> **aysiu said:**
> Read and fixed.

Thanks a ton, you are the man :)

---

### Post by TheeMahn2003 on 2006-12-22
> **aysiu said:**
> Read and fixed.

Hate to bug you again but it should read: Have your Ubuntu "your way".  I hosed it up twice :)

---

### Post by master_kernel on 2006-12-24
I have added a [Google Earth module]("http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=fileinfo&id=106") to this project for you people who dream to fly.

I have used this program and it is undoubtedly the best customization program for Ubuntu. It could use a few extra features (like the ones in [MySlax Creator]("http://myslax.bonsonno.org/") for Windoze ;), or the ones in [UCK]("http://uck.sourceforge.net/") ](*,) ), but it is still great! I have customized 2 Feisty Fawn CD's and am still going. Thank you for your hard work!

---

### Post by TheeMahn2003 on 2006-12-24
> **master_kernel said:**
> I have added a [Google Earth module]("http://reconstructor.aperantis.com/index.php?option=com_remository&Itemid=33&func=fileinfo&id=106") to this project for you people who dream to fly.

I have used this program and it is undoubtedly the best customization program for Ubuntu. It could use a few extra features (like the ones in [MySlax Creator]("http://myslax.bonsonno.org/") for Windoze ;), or the ones in [UCK]("http://uck.sourceforge.net/") ](*,) ), but it is still great! I have customized 2 Feisty Fawn CD's and am still going. Thank you for your hard work!

Thanks for your effort obviously someone has compiled a debian version of Google Earth read your source...  Great work welcome aboard the reconstructor team.  Do you mind if I host it through my [website]("http://ubuntusoftware.info") still working on writing pages for the rmods I have made will take a long time last I checked I have written 52 of them (not all are posted yet).  :)  I have a google earth module I have written please note it does not work:

```
#!/bin/sh 
#
# Reconstructor Module - Google Earth
#	Copyright (c) 2006  Reconstructor Team <http://reconstructor.aperantis.com>
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

RMOD_ENGINE=1.0
RMOD_CATEGORY='Software'
RMOD_SUBCATEGORY='Productivity'
RMOD_NAME='Google Earth'
RMOD_AUTHOR='TheeMahn'
RMOD_VERSION=0.2
RMOD_DESCRIPTION='Installs Google Earth'
RMOD_RUN_IN_CHROOT=True
RMOD_UPDATE_URL='http://reconstructor.aperantis.com/update/modules/'
echo Running $RMOD_NAME...
apt-get update
#retrieve tools
apt-get install -y wget

#see if Google has been downloaded if not grab it and install
if test -f GoogleEarthLinux.bin
then
chmod +x G*.bin
./GoogleEarthLinux.bin
else
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
chmod +x G*.bin
./GoogleEarthLinux.bin
fi

#cleanup
apt-get clean
apt-get autoclean
rm GoogleEarthLinux.bin
echo $RMOD_NAME Finished...

```

The reason the module I posted not yours does not work is Google earth requires X11 to run the actual installer.  Your rmod gets around this by using pre-compiled debian based software.  Congrats and welcome aboard to the team.

---

### Post by TheeMahn2003 on 2006-12-30
I am in process of setting up a "real" [website]("http://ubuntusoftware.info/sum.html") that will be dedicated to making "Your own Ubuntu" give me at least 48 hours however to start to set it in motion.  I will show the content [here]("http://ubuntusoftware.info/test.html") a forum exclusive (not linked internally yet).  I will have howtos, software not obtainable through the repos, detailed descriptions, screenshots and additional resources based apon the application.  

Software installable by a click of the mouse provided gdebi or that of similar. Terminal based installation - code provided for those in the repos, and for those so inclined to write their own rmods source code pasted to the page.

I also have introduced as of recent additional resources based on the module viewed that will give the meat and potatoes as I have called it.  The sample page can be viewed please do not view it as set in stone a new look is to come thanks again javier my template man ;), same as Ubuntu Christmas was not set in stone I seen screenshots of it on thecodingstudios.com & had a screenshot of my homepage saying please wait as this page is being built, before I even wrote a webpage about it...  Amazing how fast the Internet works.

Any input good / bad please post as I do want to make a website that caters to all, any suggestions, comments please feel free to post.

---

### Post by asfaq on 2007-05-12
Hi there,

in the modules window, how do you install and uninstall programs? I dont get the method.. plz help!!

---

### Post by LodeRunner on 2007-06-19
The "custom apt-get" line doesn't seem to work.  I've tried simply listing the packages I want to install (separated by space) and I've tried a full "apt-get install blah blahdy blah" and either way I am left with a liveCD that lacks all of the packages.  Some of the packages I'm trying to add are from the default repositories, while some are from the repositories I've added under the APT tab--neither are included when I boot up the final ISO.  And yes, I do click "Apply" before clicking "Next" (or is it "Finish"?)

Any idea how to fix this?  Would be a really neat program if it actually worked.

---

### Post by asfaq on 2007-06-19
first look at the sources.lst file in your working directory and see if its blank. I think it is because of this reason that u are not able to include any of your custom apps.. Also.. when u click on 'accept' another terminal window will open up showing the status of the downloaded modules.. monitor that window.. you should get clues from there.. all the best!

---

### Post by dominiquec on 2007-09-12
Trying out Reconstructor and I'm stuck at a point where the Reconstructor terminal won't run. Here are the resulting messages. Any suggestions?

I am using Ubuntu 7.04 and Reconstructor 2.6. I am trying to build from Ubuntu 7.04 ISO.

Mounting /proc filesystem...
Copying apt.conf configuration...
cp: cannot stat `/etc/apt/apt.conf': No such file or directory
Copying wgetrc configuration...
Launching Gnome-Terminal for advanced customization...

(gnome-terminal:12226): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Restoring wgetrc configuration...
Removing apt.conf configuration...
Removing DNS info...
Umounting /proc...

---

### Post by chrome307 on 2007-09-13
How do you un-install this application ??

I have tried via Synaptic but I still have a Reconstructor and Custom-CD Live folder on my HOME folder which have 'locks' on them.

Thanks

---

### Post by ShuaM75 on 2007-09-24
This stuff is great! I'm drinking it in as we type! Ha! Ha!
Thanks and keep up the great work for us nOOb's.

---

