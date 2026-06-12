---
title: "Simple Kubuntu Optimization that always just WORKS!"
date: 2006-07-27
forum: Outdated Tutorials &amp; Tips
---

### Post by lunarcloud on 2006-07-27
This is a K.I.S.S. shell script that automatically optimizes a fresh Kubuntu Dapper Drake installation.

I'm making this for our company to use on new pre-built systems for customers. Customers should have their systems running streamline.

Just extract the file (right click and choose "extract here"),
open up "konsole",
change to the directory that you extracted (cd /pathtothefolder/ANYkeyOptimizer),
and type "sh install.sh"

[download]("http://freewebs.com/zempharian/ANYkeyOptimizer.tar.gz")

[http://www.kde-apps.org/content/download.php?content=43320](http://www.kde-apps.org/content/download.php?content=43320)

---

### Post by GoldBuggie on 2006-07-28
Which optimizations are you doing?

---

### Post by guillaumeh on 2006-07-28
And its 7,9 MBytes big ...?

---

### Post by T700 on 2006-07-28
A near 8M "script" to provide unspecified optimizations and it is provide by a new member with his/her first post?  If I'm wrong, I'll apologize, but I'd be VERY careful with this!

Paul

---

### Post by taketheveil on 2006-07-28
i'm inspecting this right now to see if its malicious...

folks, please beware!!!  the only practical way for someone to get malware on your computer when you're running ubuntu is through social engineering, and this sure sounds like it!

=;

edit: This guy "zarquad" has only one post here, and the link to kde-apps is broken, most likely because it was reported as malware and they decided to not host it.  STAY AWAY PEOPLE!!

---

### Post by taketheveil on 2006-07-28
Here's the script he gives out in the tarball:
```

##/bin/bash 

echo " "
echo " "
echo "ANYkey Industries Optimizer Dapper Drake Edition"
echo " "
echo " "
echo "Do not run this with sudo! Passwords will be asked for when needed."
echo " "
echo " "
echo "Please pay attention during the installation process for non-gpl'ed packages"
echo " "
echo " "

echo  "Continue?"
read Option   # read from keyboard    

 case "$Option" in
 yes)
 echo "Okay..." ;;
 no)
 exit ;;
 *)
 exit ;; 
 esac 

echo "Creating Organizational Folders in the Home Folder..."

mkdir $HOME/Pictures 
mkdir $HOME/Downloads 
mkdir $HOME/Movies
mkdir $HOME/Writing

echo " "
echo "Adding Repositories..."
sources="/etc/sources.list"

sudo cp gimp-splash.png $sources 2> /dev/null

wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg

echo " "
echo "Password needed to download repository keys..."

sudo apt-key add kubuntu-packages-jriddell-key.gpg

echo " "
echo "updating with new repositories..."

sudo apt-get update

echo " "
echo "installing basic function programs..."

sudo apt-get install kolourpaint kcontrol-kdmtheme kde-kdm-themes kcontrol-autostart alsa-oss alsa-utils amarok-engines amarok-xine gimp firefox mozilla-thunderbird camorama digikam digikamimageplugins cabextract p7zip unzip zip 

echo " "
echo "Installing programs not in repositories..."

sudo dpkg -i sharpmusique_1.0-1_i386.deb gaim-2.0.0beta3_2.0.0beta3-1_i386.deb crystal_1.0.1-1_i386.deb

echo " "
echo "Installing DVD playing capabilities..."

sudo apt-get install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 xineui libxine-extracodecs 

echo " "
echo "Removing Default Multimedia Player..."

sudo apt-get remove kaffienne

echo " "
echo "Installing Improved Multimedia Players..."

sudo apt-get install libmad0 mplayer kmplayer mozilla-mplayer mplayer-skins vlc vlc-plugin-alsa xmms xmms-mp4 xmms-scrobbler streamtuner streamripper

echo " "
echo "Installing Flash Player..."

sudo apt-get install flashplugin-nonfree

echo " "
echo "Installing Java..."

sudo apt-get install j2re1.4-mozilla-plugin

echo " "
echo "Installing Artwork..."

sudo apt-get install xscreensaver-data-extra xscreensaver-gl xscreensaver-gl-extras kde-icons-nouvext kde-icons-nuvola kde-wallpapers-lineartwork

cp Wallpaper.png ~/Pictures/
sudo cp -r gnu-linux /usr/share/apps/kdm/themes/
sudo cp -r Tux-Splash /usr/share/apps/ksplash/Themes/


gimpsplash="/usr/share/gimp/2.0/images/gimp-splash.png"
ooosplash="/usr/lib/openoffice/program/intro.bmp"
kmymoney="/usr/share/apps/kmymoney2/pics/startlogo.png"
quanta="/usr/share/apps/quanta/toolbar/quantalogo.png"
gxine="/usr/share/gxine/pixmaps/splash.png"
amarok="/usr/share/apps/amarok/images/splash_screen.jpg"
scribus="/usr/share/scribus/icons/Splash.png"
scribusng="/usr/share/scribus-ng/icons/Splash.png"
gaim="/usr/share/pixmaps/gaim/logo.png"


cp gimp-splash.png $gimpsplash 2> /dev/null
cp ooo-splash.bmp $ooosplash 2> /dev/null
cp kmymoney-splash.png $kmymoney 2> /dev/null
cp quanta-splash.png $quanta 2> /dev/null
cp gxine-splash.png $gxine 2> /dev/null
cp amarok-splash.png $amarok 2> /dev/null
cp scribus-splash.png $scribus 2> /dev/null
cp scribus-splash.png $scribusng 2> /dev/null
cp gaim-splash.png $gaim 2> /dev/null

echo " "
echo "Fully updating system (this may take a while)..."

sudo apt-get upgrade

sh graphics.sh

echo " "
echo "Installing Windows Codecs and Fonts."
echo "If you live in the United States and do not own a current copy of Windows," 
echo "be warned that installing these will be illegal. Continue?"

read Option   # read from keyboard    

 case "$Option" in
 yes)
 echo "Okay..." ;;
 no)
 
echo  " "
echo  " "
echo "Finished Optimization"
exit ;;
 *)
 exit ;; 
 esac 

sudo apt-get install win32codecs msttcorefonts 


echo  " "
echo  " "
echo "Finished Optimization"

```

I have to run so i don't know just yet...

---

### Post by exif on 2006-07-28
Looks to me more like a content patch more than an "optimization". At least from the posted source. I somehow don't see that source using up 8 megs though....

---

### Post by picpak on 2006-07-29
It probably includes .deb files too (from looking at that script).

---

### Post by sirlancelot on 2006-07-29
This is more of an installer script, not an optimization script

Very misleading.

---

