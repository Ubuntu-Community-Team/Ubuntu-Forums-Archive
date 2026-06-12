---
title: "An &quot;install-all&quot; zsh script"
date: 2006-08-29
forum: Outdated Tutorials &amp; Tips
---

### Post by pau on 2006-08-29
Hi,

I wrote a small script to "automagically" install all kind of codecs you'll need to play movies/music **sadly** encoded with propietary programs, as well as googleearth, the nice enlightenment **engage**, **moblock**, a new set of **icons** I like a lot (gartoon), nessus, the **latest nightly build of wengo**, fonts, rippers, **Xara Xtreme**,  the fancy **kiba-dock**, **skype-rec** (a program to record your skype conversations in ogg or mp3 files, but it can also be used for wengo etc), the **games Cube, Tremulous, Second life**, as well as a lot of personal things (list in red, change as you want), automatix, sunjava, kino, **theora (latest)** etc etc

Of course you can just chop the code and select the things you want to install and modify it accordingly... :mrgreen: 

This is meant to be run after a clean ubuntu dapper installation.
```

#!/usr/bin/env bash

cd /tmp &&

# Get gartoon icon set

wget http://www.aei.mpg.de/~pau/gartoon.tar.gz ; mkdir $HOME/.icons; mv gartoon.tar.gz $HOME/.icons && tar xvfz $HOME/.icons/gartoon.tar.gz ;

# Become su for the rest of the script

su -s &&

# Make the icons available in the pixmaps directory to use them for apps

sudo mkdir /usr/share/pixmaps/gartoon;
sudo ln -sf $HOME/.icons/gartoon/svg/* /usr/share/pixmaps/gartoon;
sudo ln -sf $HOME/.icons/gartoon/scalable/apps/*     /usr/share/pixmaps/gartoon;
sudo ln -sf $HOME/.icons/gartoon/scalable/devices/*    /usr/share/pixmaps/gartoon;
sudo ln -sf $HOME/.icons/gartoon/scalable/emblems/*  /usr/share/pixmaps/gartoon;
sudo ln -sf $HOME/.icons/gartoon/scalable/filesystems/*  /usr/share/pixmaps/gartoon;
sudo ln -sf $HOME/.icons/gartoon/scalable/mimetypes/*  /usr/share/pixmaps/gartoon;
sudo ln -sf $HOME/.icons/gartoon/scalable/Xtras/* /usr/share/pixmaps/gartoon;

# Get nice ComixCursor theme for the cursor and install it

wget http://www.aei.mpg.de/~pau/ComixCursors-0.4.2.tar.bz2 ; sudo tar xvfj ./ComixCursors-0.4.2.tar.bz2 ; sudo mv ComixCursors-* /usr/share/icons ;

# Backup sources.list

sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_ORIGINAL ;

# Get the modified one

wget http://www.aei.mpg.de/~pau/sources.list_dapper && sudo mv -f ./sources.list_dapper /etc/apt/sources.list ;

# gpg procedure requiered for automatix

wget http://www.getautomatix.com/apt/key.gpg.asc ;
gpg --import key.gpg.asc ;
gpg --export --armor 521A9C7C | sudo apt-key add -

# gpg procedure required for engage

sudo wget soulmachine.net/public.key && sudo apt-key add public.key ;

# update, upgrade

sudo apt-get update ;
sudo apt-get -y -V upgrade ;

############################ Automatix ############################
sudo apt-get install -y -V zenity && sudo apt-get install -y -V automatix2 &&
automatix2 &&
############################ Automatix ############################

# In case we didn't do this with Automatix
sudo apt-get install -y -V sun-java5-jre sun-java5-plugin &&
sudo update-java-alternatives --set java-1.5.0-sun &&
sudo apt-get install -y -V flashplugin-nonfree &&
sudo update-flashplugin &&
wget -c http://www.users.on.net/~stubby/FrostWire-4.10.9-2.i586.deb &&
sudo dpkg -i FrostWire-4.10.9-2.i586.deb &&

############################ Engage ############################
wget http://www.aei.mpg.de/~pau/engage_osx.tar.gz ;
mkdir -p ~/.e/e/applications/allmkdir -p ~/.e/e/applications/engage ;
mv engage_osx.tar.gz ~/.e/e/applications/engage ;
cd ~/.e/e/applications/engage/ && tar xvfz engage_osx.tar.gz&&
cd /tmp&&
sudo apt-get install -y -V engage eutils 
clear ;
echo "Use e_util_eapp_edit ~/.e/e/applications/engage/gnome-terminal.eap to configure the files of engage";
sleep 4;
############################ Engage ############################

############################ kiba dock ############################
clear &&
sleep 3 &&
echo "Installation of the kiba dock; you'll need xgl though..."
sleep 3 &&
sudo apt-get -y -V install automake1.4- &&
sudo apt-get -y -V install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx-dev  librsvg2-dev checkinstall libglade2-dev &&
cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock &&
cd ./kiba-dock&&
./autogen.sh&&
make&&
make install-schemas&&
sudo checkinstall&&
cd /tmp &&
############################ kiba dock ############################

############################ Moblock ############################
clear &&
sleep 3 &&
echo "Installation of Moblock..."
sleep 3 &&
gpg --keyserver subkeys.pgp.net --recv DEDA0559 &&
gpg --export --armor DEDA0559 | sudo apt-key add - &&
sudo apt-get -y -V install moblock-nfq &&
############################ Moblock ############################

######################## Googleearth (if not done with Automatix) ########################
clear &&
sleep 3 &&
echo "Installation google earth; click _exit_ when finished"
sleep 3 &&
wget -c http://dl.google.com/earth/GE4/GoogleEarthLinux.bin &&
sudo sh GoogleEarthLinux.bin &&
sudo cp /usr/local/google-earth/googleearth.desktop /usr/share/applications/ &&
clear &&
echo "google earth installed"
sleep 3 &&
######################## Googleearth (if not done with Automatix) ########################


###################### Multimedia codecs (if not done with Automatix) ######################
sudo apt-get install -y -V gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base &&
sudo apt-get install -y -V gstreamer0.10-plugins-good gstreamer0.10-plugins-bad &&
sudo apt-get install -y -V gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly &&
sudo apt-get install -y -V gstreamer0.10-plugins-ugly-multiverse &&
sudo apt-get install -y -V w32codecs &&
###################### Multimedia codecs (if not done with Automatix) ######################

# How to install DVD playback capability
# 
# ironss: gstreamer dvd plugin is available as part of plugins-bad (or ugly?)
# and does not work reliably. However, Totem works with the xine backend to play
# back DVDs. This will keep you going until gstreamer gets dvd playback. Note
# that you do not have to install xine-ui or mplayer as suggested in 

sudo apt-get install -y -V libdvdread3 && 
sudo /usr/share/doc/libdvdread3/examples/install-css.sh &&
sudo apt-get install -y -V totem-xine &&

################################################################ Not serious thingies ################################################################
sudo apt-get install -y -V wormux pingus lbreakout2 stellarium celestia d4x azureus bittornado bittornado-gui amule skype streamtuner streamripper cowbell banshee audacity bum stellarium 
################################################################ Not serious thingies ################################################################

################################################################ Serious thingies ################################################################

sudo apt-get install -y -V zsh zsh-lovers vim-gnome lynx xine-ui libxine-extracodecs qiv dhcpcd dvdbackup mjpegtools mkisofs mplayer mp32ogg easytag inkscape nvu build-essential wine quanta kdebase kde-i18n-ca k3b libk3b2-mp3 gparted firestarter ethereal gthumb mcrypt gv gnome-gv kpdf a2ps tetex-base tetex-extra tex-common latex-beamer xfig aspell maxima wxmaxima maxima-doc labplot gnuplot grace g77 most mencal kwifimanager ksnapshot pstoedit libtheora\* libogg-dev libvorbis-dev ffmpeg2theora grip subversion gnubiff mutt gworldclock stopwatch wifi-radar xmame-x xmms xmms-skins psutils &&
################################################################ Serious thingies ################################################################

clear ; rehash &&

echo -n ""

#################################################################### Theora ####################################################################
cd /tmp&&
echo "Installation of last version theora..."
echo -n ""
sleep 3;

#theora darrera versio
lynx -dump http://downloads.xiph.org/releases/theora/ | grep "tar.gz" | gawk '{print $2}' | tail -2 | grep libtheora-1 > /tmp/theora.txt &&
wget `cat /tmp/theora.txt`&&
tar xvfz /tmp/libtheora* &&
rm /tmp/libtheora* &&
cd /tmp/libtheora* &&
./configure ;
make ;
sudo make install ;
cd examples ;
cp $HOME/bin/encoder_example $HOME/bin/encoder_example_old ;
gcc -o $HOME/bin/encoder_example encoder_example.c -logg -lvorbis -lvorbisenc -ltheora;
clear;
echo "Installation last version Theora finished... "
sleep 3;
#################################################################### Theora ####################################################################

#################################################################### skype-rec ####################################################################
echo "Installation of last version skype-rec..."

echo -n ""

sleep 3;
cvs -d:pserver:anonymous@skype-rec.cvs.sourceforge.net:/cvsroot/skype-rec co skype-rec &&
cd skype-rec&&
make&&
sudo make install&&
cd /tmp&&
clear;
echo "Installation last version skype-rec finished... "
sleep 3;
#################################################################### skype-rec ####################################################################

#################################################################### Wengo ####################################################################


echo -n ""

sleep 3;
# The binary deb doesn't work (sound problems). Have to fetch last nightlybuild
#
# wget http://wengofiles.wengo.fr/wengophone/rc/wengophone-0.958m-1.i386.deb &&
# sudo dpkg -i wengophone-0.958m-1.i386.deb &&

lynx -dump http://download.wengo.com/nightlybuilds/binary/NG/GNULinux/rc2/ | tail -1 | gawk '{print $2}' > /tmp/Wengo.txt&&
wget `cat /tmp/Wengo.txt`&&
tar xvfj wengophone*&&
rm wengophone*&&
mv wengo* $HOME/wengo&&
# wget http://www.aei.mpg.de/~pau/wengo.desktop.txt &&
# sudo mv ./wengo.desktop.txt /usr/share/applications/kde/wengophone.desktop &&
clear;
echo "Installation Openwengo finished..."
sleep 3;
#################################################################### Wengo ####################################################################

#################################################################### Xara Xtreme ####################################################################
clear;
echo "Instal.lacio de la darrera versio de Xara Xtreme..."
echo -n ""
sleep 3;

lynx -dump http://www.xaraxtreme.org/download/ | grep "Recom" | tail -1 |  gawk '{print $2}' > /tmp/xara.txt &&
wget `cat /tmp/xara.txt`&&
tar xvfj RecomX* &&
sudo mv xaral* /opt &&
sudo ln -s /opt/xara*/bin/* /usr/bin/
wget http://www.aei.mpg.de/~pau/xara.desktop.txt &&
sudo mv xara.desktop.txt /usr/share/applications/xara.desktop &&
clear &&

echo "Installation Xara Xtreme finished... ";
sleep 3;
#################################################################### Xara Xtreme ####################################################################

#################################################################### Cube ####################################################################
clear;
echo "Installation of Cube..."
echo -n ""
sleep 3;
wget http://yeknan.free.fr/blog/fichiers/games/cube_20040522-4_i386.deb && 
sudo dpkg -i cube_20040522-4_i386.deb && 
rm -f cube_20040522-4_i386.deb
#################################################################### Cube ####################################################################

#################################################################### Tremulous ####################################################################
sudo mkdir /usr/local/games/tremulous&&
cd /usr/local/games/tremulous&&
sudo wget http://easynews.dl.sourceforge.net/sourceforge/tremulous/tremulous-1.1.0-installer.x86.run&&
sudo chmod a+x tremulous-1.1.0-installer.x86.run&&
sudo sh tremulous-1.1.0-installer.x86.run&&
sudo rm tremulous-1.1.0-installer.x86.run&&
cd /tmp&&
wget http://www.aei.mpg.de/~pau/tremulous.txt&&
mv tremulous.txt /usr/share/applications/tremulous.desktop&&
#################################################################### Tremulous ####################################################################

#################################################################### Second life ####################################################################
sudo mkdir /usr/local/games/second-life&&
cd /usr/local/games/second-life&&
sudo wget -c http://secondlife.com/downloads/viewer/SecondLife_i686_1_12_1_13.tar.bz2 && sudo tar xvfjp SecondLife_i686_1_12_1_13.tar.bz2&&
sudo rm SecondLife_i686_1_12_1_13.tar.bz2&&
sudo mv SecondLife_i686_1_12_1_13/* .&&
sudo rm -r SecondLife_i686_1_12_1_13&&
sudo wget http://www.aei.mpg.de/~pau/secondlife.txt&&
sudo mv secondlife.txt /usr/share/applications/secondlife.desktop&&
cd /tmp&&
#################################################################### Second life ####################################################################

echo -n ""
echo "xmms installation and general setup..."
echo -n ""
wget -c http://easylinux.info/uploads/xmms-wma_1.0.4-2_i386.deb &&
sudo dpkg -i xmms-wma_1.0.4-2_i386.deb &&
#Associate XMMS to play MP3/M3U/WAV files
sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup &&
sudo cp /usr/share/applications/defaults.list /tmp/defaults.list_tmp &&
sudo sed -e 's/audio\/mpeg=.*/audio\/mpeg=XMMS.desktop/g' /tmp/defaults.list_tmp > /tmp/defaults.mp3 &&
sudo sed -e 's/audio\/x-mpegurl=.*/audio\/x-mpegurl=XMMS.desktop/g' /tmp/defaults.mp3 > /tmp/defaults.m3u &&
sudo sed -e 's/audio\/x-wav=.*/audio\/x-wav=XMMS.desktop/g' /tmp/defaults.m3u > /tmp/defaults.list &&
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list &&
sudo rm -f /tmp/defaults.* &&

clear &&

echo "xmms installation and setup finished... "
sleep 3;
#################################################################### xmms ####################################################################

echo -n ""

echo "Instal.lacio de kino i configuracio general..."

echo -n ""


#kino
sudo apt-get install -y -V kino &&
sudo apt-get install -y -V kinoplus &&
sudo apt-get install -y -V kino-timfx &&
sudo apt-get install -y -V kino-dvtitler &&
sudo modprobe raw1394 &&
sudo modprobe ohci1394 &&
sudo modprobe video1394 &&
sudo mknod -m 666 /dev/raw1394 c 171 0;
sudo chmod 666 /dev/raw1394 &&

#nessus
sudo apt-get install -y -V nessus &&
sudo apt-get install -y -V nessusd &&
sudo nessus-adduser &&
sudo ln -fs /etc/init.d/nessusd /etc/rc2.d/S20nessusd &&
sudo /etc/init.d/nessusd start &&

#rar
sudo apt-get install -y -V rar &
sudo ln -fs /usr/bin/rar /usr/bin/unrar &

#DVD Ripper (dvd::rip)
sudo apt-get install -y -V dvdrip vcdimager cdrdao subtitleripper &&
sudo ln -fs /usr/bin/rar /usr/bin/rar-2.80 &&
wget http://www.aei.mpg.de/~pau/dvdrip.desktop.txt &&
sudo mv ./dvdrip.desktop.txt /usr/share/applications/dvdrip.desktop &&

#extrafonts
sudo apt-get install -y -V xfonts-intl-arabic &&
sudo apt-get install -y -V xfonts-intl-asian &&
sudo apt-get install -y -V xfonts-intl-chinese &&
sudo apt-get install -y -V xfonts-intl-chinese-big &&
sudo apt-get install -y -V xfonts-intl-european && 
sudo apt-get install -y -V xfonts-intl-japanese &&
sudo apt-get install -y -V xfonts-intl-japanese-big &&
sudo apt-get install -y -V xfonts-intl-phonetic &&
sudo apt-get install -y -V gsfonts-x11 &&
sudo apt-get install -y -V msttcorefonts &&
sudo fc-cache -f -v &&

clear &&
echo "Ja esta. He instal.lat un fum de coses; ara reengeguem..."
sleep 3 &&
sudo reboot


```

To start engage after installation type on a terminal, for instance: 

```
engage -W 1280 -H 1280 -T 0 -I 1 -i 1 -e software -H 200 -s 26 -Z 1.9 --mode 1 740 -B "#00000000" -b "#4EEEEEEE" -S 8
```

---

### Post by calvinthomas on 2006-08-29
I'm not going to try it because i've got everything working already but I think its an excellent idea! Well done!

Calv

---

### Post by pau on 2006-08-30
thanks...

I wrote it because I fear my laptop is dying and I'll have to soon install ubuntu on a new machine and I'm fed up of doing this kind of things per hand everytime... [-(

---

### Post by cyanide on 2007-06-28
Can you tell me which version of engage this script installs???
And does it need a compositing manager like Beryl or Compiz or XGL???

Thanks.

---

### Post by cyanide on 2007-06-28
Can you tell me which version of engage this script installs???
And does it need a compositing manager???

Thanks.

---

