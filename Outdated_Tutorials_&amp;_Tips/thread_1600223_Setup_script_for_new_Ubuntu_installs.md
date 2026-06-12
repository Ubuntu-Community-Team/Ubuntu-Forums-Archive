---
title: "Setup script for new Ubuntu installs"
date: 2010-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by KenBW2 on 2010-10-18
I developed a (somewhat simple) bash script which sets up my computer after I install Ubuntu, and thought I'd share it with the community in the hope that it might assist others in adapting it to their own needs.

[SIZE="4"][COLOR="Red"]What it does[/COLOR][/SIZE]

[LIST][*]Enables universe, multiverse etc repositories[*]Enables other repositories, both PPAs and other apt[*]Installs a specified list of packages from said repositories[*]Installs wine applications[*]Sets preferences for many applications and the systems itself through Gconf[*]Enables DVD playback[*]Copies profile folders, configuration files such as GTK bookmarks and default directories from a pen drive (Lucid script only as it's not too reliable yet)
[/LIST]

Please let me know if
[LIST=1]
[*]It helped you (I like to know someone out there is benefiting from my work)
[*]You have suggestions on how to improve it
[*]Have significant modifications you feel the community would benefit from
[/LIST]

If it proves to be popular I'll put a bit more commenting into the script to detail exactly what's happening and how to amend it

[SIZE="4"][COLOR="Red"]Maverick version (more stable, but some functionality involving copying files lacking)[/COLOR][/SIZE]

```

echo "
    Setup script for new Ubuntu installs
    Copyright (C) 2010  Kenneth Bradkey-White <kenbw2@gmail.com>

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
"
echo
echo "v0.1. Designed for Ubuntu 10.10";
echo

choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 1 ] ; then
   echo "OK"
fi
done

echo "####### Starting script #######";

echo "####### Enabling other repositories #######";
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list;
sudo wget http://www.medibuntu.org/sources.list.d/lucid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo add-apt-repository ppa:chromium-daily
sudo add-apt-repository ppa:rabbitvcs/ppa
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5;
sudo sh -c "echo 'deb http://deb.opera.com/opera-beta/ stable non-free' >> /etc/apt/sources.list";
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -;
echo "####### Enabled repositories #######";

echo "####### Updating and upgrading #######";
choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 1 ] ; then
   echo "OK"
fi
done

sudo apt-get update;
sudo apt-get upgrade -y;

echo "####### Installing and removing apps from repositories #######";

choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 1 ] ; then
   echo "OK"
fi
done

sudo apt-get install -y compizconfig-settings-manager opera pidgin wine cheese ubuntu-restricted-extras gparted inkscape vlc chromium-browser openssh-server deluge-torrent skype gnome-power-manager update-notifier php5 rabbitvcs-nautilus rabbitvcs-gedit glipper tilda panflute-applet;
sudo apt-get remove -y empathy evolution

echo "####### Install complete #######";

echo "####### Downloading files #######";
choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 1 ] ; then
   echo "OK"
fi
done

mkdir ~/Temp;
cd ~/Temp;
wget http://www.spotify.com/download/Spotify%20Installer.exe;
echo "####### Installing packages #######";
choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 1 ] ; then
   echo "OK"
fi
done

sudo dpkg -iR ./;
sudo apt-get -f install;

echo "####### Setting preferences #######";
choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
gconftool-2 --type bool --set /apps/nautilus/preferences/show_advanced_permissions true;
gconftool-2 --type string --set /apps/nautilus/preferences/click_policy "single";
gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount_open false;
gconftool-2 --type string --set /apps/nautilus/preferences/media_autorun_x_content_open_folder "[]";
gconftool-2 --type bool --set /apps/gnome-power-manager/actions/event_when_closed_battery false;
gconftool-2 --type bool --set /apps/gnome-screensaver/lock_enabled false;

gconftool-2 --type string --set /desktop/gnome/remote_access/authentication_methods "vnc";
gconftool-2 --type bool --set /desktop/gnome/remote_access/enabled true;
gconftool-2 --type bool --set /desktop/gnome/remote_access/prompt_enabled false;

gconftool-2 --type string --set /apps/rhythmbox/player/transition_time "5";
gconftool-2 --type bool --set /apps/rhythmbox/player/use_xfade_backend true;
gconftool-2 --type bool --set /apps/rhythmbox/player/transition_album_check true;
gconftool-2 --type bool --set /apps/rhythmbox/plugins/artdisplay/active true;
gconftool-2 --type bool --set /apps/rhythmbox/plugins/lyrics/active true;
gconftool-2 --type string --set /apps/rhythmbox/plugins/lyrics/engines "[astraweb.com,lyrc.com.ar,leoslyrics.com,lyricwiki.org,winampcn.com]";

gconftool-2 --type bool --set /apps/update-notifier/auto_launch false;

gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/auto_indent/auto_indent true;
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/line_numbers/display_line_numbers true;
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/save/auto_save true;

gconftool-2 --type string --set /desktop/gnome/applications/browser/exec "opera";
gconftool-2 --type int --set /desktop/gnome/peripherals/keyboard/delay 200;
gconftool-2 --type bool --set /desktop/gnome/interface/buttons_have_icons true;
gconftool-2 --type bool --set /desktop/gnome/interface/menus_have_icons true;
done
echo "####### Preference setting complete #######";

echo "####### Creating folder system #######";
choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 1 ] ; then
   echo "OK"
fi
done


echo "####### Installing Spotify #######";

wine ~/Temp/Spotify\ Installer.exe;
cd ~/;

rm -rf ~/Temp;

echo "####### Setting files complete #######";

echo "####### Other configurations #######";
choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 1 ] ; then
   echo "OK"
fi
done

sudo apt-get install libdvdread4;
sudo /usr/share/doc/libdvdread4/install-css.sh;


echo "####### Setup complete. Restarting... #######";
choice=4
echo "Press 2 to restart, or 3 to restart later"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 2 ] ; then
   echo "OK"
fi
if [ $choice -eq 3 ] ; then
   exit;
fi
done

sudo reboot;

```

[SIZE="4"][COLOR="Red"]Lucid version (includes more functionality, some unreliability in copying of files)[/COLOR][/SIZE]

```

# Known Issues
# Gnome/KDE/Other choice skips
#
#
echo "
    Setup script for new Ubuntu installs
    Copyright (C) 2010  Kenneth Bradkey-White <kenbw2@gmail.com>

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
"
echo

echo "v0.5. Designed for Ubuntu 10.04";

choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 1 ] ; then
   echo "OK"
fi
done

echo "####### Starting script #######";

echo "####### Enabling other repositories #######";
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list;
sudo wget http://www.medibuntu.org/sources.list.d/lucid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo add-apt-repository ppa:chromium-daily
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5;
sudo sh -c "echo 'deb http://deb.opera.com/opera-beta/ stable non-free' >> /etc/apt/sources.list";
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -;
echo "####### Enabled repositories #######";

echo "####### Updating and upgrading #######";
choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 1 ] ; then
   echo "OK"
fi
done

sudo apt-get update;
sudo apt-get upgrade -y;

echo "####### Installing apps from repositories #######";




choice=5
echo "Choose Desktop Environment"
echo "2 = GNOME; 3 = KDE; 4 = Other"
while [ $choice -eq 5 ]; do
read choice
if [ $choice -eq 2 ] ; then
   echo "OK"
sudo apt-get install -y compizconfig-settings-manager opera pidgin wine cheese ubuntu-restricted-extras gparted inkscape vlc chromium-browser openssh-server deluge-torrent music-applet notification-daemon skype gnome-power-manager update-notifier php;
fi
if [ $choice -eq 3 ] ; then
   echo "OK"
sudo apt-get install -y opera wine kubuntu-restricted-extras gparted inkscape vlc chromium-browser openssh-server skype php5;
fi
if [ $choice -eq 4 ] ; then
   echo "OK"
sudo apt-get install -y compizconfig-settings-manager pidgin wine cheese ubuntu-restricted-extras gparted inkscape vlc chromium-browser openssh-server deluge-torrent music-applet notification-daemon skype gnome-power-manager update-notifier;
fi
done
echo "####### Install complete #######";

echo "####### Downloading files #######";
choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 1 ] ; then
   echo "OK"
fi
done

mkdir Temp;
cd Temp;
wget http://www.spotify.com/download/Spotify%20Installer.exe;
echo "####### Installing packages #######";
choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 1 ] ; then
   echo "OK"
fi
done

sudo dpkg -iR ./;
sudo apt-get -f install;

echo "####### Setting preferences #######";
choice=5
echo "Choose Desktop Environment"
echo "2 = GNOME; 3 = KDE; 4 = Other"
while [ $choice -eq 5 ]; do
read choice
if [ $choice -eq 2 ] ; then
   echo "OK"
gconftool-2 --type bool --set /apps/nautilus/preferences/show_advanced_permissions true;
gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount_open false;
gconftool-2 --type string --set /apps/nautilus/preferences/media_autorun_x_content_open_folder "[]";
gconftool-2 --type bool --set /apps/gnome-power-manager/actions/event_when_closed_battery false;
gconftool-2 --type bool --set /apps/gnome-screensaver/lock_enabled false;

gconftool-2 --type string --set /apps/rhythmbox/player/transition_time "5";
gconftool-2 --type bool --set /apps/rhythmbox/player/use_xfade_backend true;
gconftool-2 --type bool --set /apps/rhythmbox/player/transition_album_check true;
gconftool-2 --type bool --set /apps/rhythmbox/plugins/artdisplay/active true;
gconftool-2 --type bool --set /apps/rhythmbox/plugins/lyrics/active true;
gconftool-2 --type string --set /apps/rhythmbox/plugins/lyrics/engines "[astraweb.com,lyrc.com.ar,leoslyrics.com,lyricwiki.org,winampcn.com]";

gconftool-2 --type bool --set /apps/update-notifier/auto_launch false;

gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/auto_indent/auto_indent true;
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/line_numbers/display_line_numbers true;
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/save/auto_save true;

gconftool-2 --type string --set /desktop/gnome/applications/browser/exec "opera";
gconftool-2 --type int --set /desktop/gnome/peripherals/keyboard/delay 200;
gconftool-2 --type bool --set /desktop/gnome/interface/buttons_have_icons true;
gconftool-2 --type bool --set /desktop/gnome/interface/menus_have_icons true;
fi
if [ $choice -eq 3 ] ; then
   echo "KDE option setting to be completed"
fi
done
echo "####### Preference setting complete #######";

echo "####### Creating folder system #######";
choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 1 ] ; then
   echo "OK"
fi
done


rm -rf ~/Desktop ~/Documents ~/Downloads ~/Music ~/Pictures ~/Public ~/Templates ~/Videos ~/Examples;
mkdir -p ~/Multimedia/Music "~/Multimedia/Music/Grouped/Ken's CD 3" ~/Multimedia/Audio ~/Multimedia/Pictures ~/Multimedia/Videos;
mkdir -p ~/System/Desktop ~/System/Templates ~/System/Installers;
mkdir -p ~/Transfers/Inbox/Deposit ~/Transfers/Sync/Dropbox;
mkdir -p ~/Websites;
echo "####### Folder system complete #######";

echo "####### Copying settings files #######";
choice=4
choice=4
echo "Choose Desktop Environment"
echo "2 = GNOME; 3 = KDE; 4 = Other;"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 2 ] ; then
   echo "OK"
mkdir -p Temp;
rmdir ~/.opera;
cp -r ToCopy/.opera ~/;
rmdir ~/.gconf/apps/compiz/plugins;
cp -r ToCopy/plugins ~/.gconf/apps/compiz/;
rmdir ~/.purple;
cp -r ToCopy/.purple ~/;
rm ~/.gtk-bookmarks;
cp ToCopy/.gtk-bookmarks ~/.gtk-bookmarks ./;
rm ~/.config/user-dirs.dirs;
cp ToCopy/user-dirs.dirs ~/.config;
cp -r ToCopy/autostart ~/.config;
mkdir -p ~/.gnome2/gedit/plugins;
cp ToCopy/gedit2_regex_replace_plugin.tar.gz ~/.gnome2/gedit/plugins;
fi

if [ $choice -eq 3 ] ; then
mkdir -p Temp;
rmdir ~/.opera;
cp -r ToCopy/.opera ~/;
rm .config/user-dirs.dirs;
cp ToCopy/user-dirs.dirs ~/.config;
cp -r Temp/Examples ~/System;
cp -r ToCopy/autostart ~/.config;
fi
done




echo "####### Installing Spotify #######";

wine Spotify%20Installer.exe;
cd ~/;

rm -rf Temp;
mkdir -p Temp;

echo "####### Setting files complete #######";

echo "####### Other configurations #######";
choice=4
echo "Press 1 to proceed"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 1 ] ; then
   echo "OK"
fi
done

sudo apt-get install libdvdread4;
sudo /usr/share/doc/libdvdread4/install-css.sh;
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled


echo "####### Setup complete. Restarting... #######";
choice=4
echo "Press 2 to restart, or 3 to restart later"
while [ $choice -eq 4 ]; do
read choice
if [ $choice -eq 2 ] ; then
   echo "OK"
fi
if [ $choice -eq 3 ] ; then
   exit;
fi
done

sudo reboot;

```

---

### Post by cariboo on 2010-10-26
A bump for the move

---

### Post by Zookalicious on 2010-11-05
Damn cool! I'm currently in the process of setting up something similar for myself (I seem to be doing lots of fresh installs these days....) and considering my knowledge of bash scripts is at the elementary stages, this is definitely great for working off of! Thanks a lot for the great script :)

---

### Post by cry8wolf9 on 2010-11-12
great script tnks! i will be adding/ modding it to suit my need quick question do you know a know a way to install reccommend installs and also have it save a copy of everythign it does? kind of like how dmesg > dmesg.txt will make a txt file in your home dir


Edit:
also in your Enabling other repositories section you may want to switch 
```

sudo wget http://www.medibuntu.org/sources.list.d/lucid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```
with this
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

```

---

