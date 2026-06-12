---
title: "HOWTO: Improve orange Dapper look"
date: 2006-05-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Laterix on 2006-05-31
This is my Ubuntu Orange-look theme for Ubuntu Dapper 6.06. This project started with few improvements, but now it's quite complete "desktop look". I've also written installation script for it.

[IMG]http://users.utu.fi/ljtaim/pics/orange-logo.jpg[/IMG]

Read my guide [**here**]("http://www.taimila.com/orange-look.php") and checkout [Example screenshot]("http://www.taimila.com/images/orange-look/orange-example.png"). The font in screenshot is called HandleGotD and it's not part of the Orange-look, because it's not a free font.

**UPDATES**
- Firefox Human theme
- Gnomebaker Human icon theme
- Rhythmbox notification icon
- OK button icon, Quit icon in file menu and one Synaptic icon
- Gnome configuration tool icons (Gconf)
- Firestarter
- Simple folder icons
- GDM themes
- Installation script
- Compiz theme
- Firefox Orange-look theme

I'd like to get feedback and questions to this thread. Hopefully you'll like it.

**Install script**
This is my very first bash script and there might be some bugs. I've tested this script with fresh install of Ubuntu dapper and it worked with it. It might show some "mv" errors, but those are nothing serious. It just means that there is nothing to backup before install process. Script takes backup of every file it overwrites, but there is no uninstall script at the moment. So only manual uninstall is possible at the moment.

Script doesn't install Firestarter icons, smooth-orange, GDM theme or wallpaper. Look my guide for these.

Please give me feedback about this script and tell me how to improve it! To install Orange-look with script do these steps:
```

wget http://www.taimila.com/downloads/orange-look-installer
chmod 755 orange-look-installer
sudo ./orange-look-installer

```
**[COLOR="Red"]DO NOT INSTALL SAME THINGS TWICE! This will overwrite your backup files with orange-look files. This is not fatal, but just incase you want those ugly icons back. ;)[/COLOR]**

[B][COLOR="Red"]
Most of the changes will apply to all users!
[/COLOR][/B]

Here is the script:
```

#!/bin/bash

# This script installs Ubuntu Orange-look to your Ubuntu dapper. Script
# asks on every improvement if it should be installed.
#
# For more information about Orange-look check out my website at
# http://users.utu.fi/ljtaim/dapper-improvments.php
#
# If you use this script you don't need to download anything else from the
# site. Script downloads all needed files during installation.
#
# User interface is implemented with zenity, so you need to be running X-server.
#
# WARNING ! ! !
# I don't take any responsibility of what this script does. I have tested it on
# my computer and it works, but if it breaks your ubuntu installation, then I'm
# really sorry, but that's it. So no warranty for this one. :)
#
# NOTICE: Do not run installation twice! If you do that your backups will be
#         overwritten with orange-look files.
#
# Date: 1.7.2006
# Version: 0.1
# Written by: Lauri Taimila

TEMP_DIR=~/orange-look-temp

# Install orange wallpaper and active it
function install_wallpaper
{
	wget http://zone13.digitalgrafis.com/files/intelmac_red_16001024_notxt.jpg
	mv intelmac_red_16001024_notxt.jpg /usr/share/backgrounds/orange-look.jpg
	gconftool-2 --set --type string /desktop/gnome/background/picture_filename "/usr/share/backgrounds/orange-look.jpg"
}

# Download Firestarter source code, replace icons, compile and install
function install_firestarter
{
	apt-get -y build-dep firestarter
	apt-get -y install build-essential checkinstall
	apt-get -y source firestarter
	cd firestarter-1.0.3
	./configure
	make
	checkinstall
	cd ..
	wget http://users.utu.fi/ljtaim/downloads/firestarter.png
	mv firestarter.png /usr/share/pixmaps/
}

# Installs rhythmbox icon improvements
# Takes backup of original icons.
function install_rhythmbox
{
	ln -s /usr/share/icons/Human/scalable/devices/gnome-dev-cdrom-audio.svg /usr/share/icons/Human/scalable/apps/gnome-media-player.svg
	
	wget http://users.utu.fi/ljtaim/downloads/rhythmbox_extra_icons.tar.gz
	tar zxf rhythmbox_extra_icons.tar.gz
	mv stock_shuffle.png /usr/share/icons/Human/24x24/actions/
	mv stock_music-library.png /usr/share/icons/Human/24x24/actions/
	mv stock_repeat.png /usr/share/icons/Human/24x24/actions/
	
	mv /usr/share/rhythmbox/art/rhythmbox-podcast.png /usr/share/rhythmbox/art/rhythmbox-podcast_ol_backup.png
	mv /usr/share/rhythmbox/art/rhythmbox-tray-icon.png /usr/share/rhythmbox/art/rhythmbox-tray-icon_ol_backup.png
	mv rhythmbox-tray-icon.png /usr/share/rhythmbox/art/
	mv rhythmbox-podcast.png /usr/share/rhythmbox/art/

	mv /usr/share/icons/gnome/24x24/stock/media/stock_playlist.png /usr/share/icons/gnome/24x24/stock/media/stock_playlist_ol_backup.png
	mv /usr/share/icons/gnome/24x24/stock/media/stock_smart-playlist.png /usr/share/icons/gnome/24x24/stock/media/stock_smart-playlist_ol_backup.png
	mv stock_playlist.png /usr/share/icons/gnome/24x24/stock/media/
	mv stock_smart-playlist.png /usr/share/icons/gnome/24x24/stock/media/
	
	cd /usr/share/icons/
	gtk-update-icon-cache --force Human
	gtk-update-icon-cache --force gnome
	cd $TEMP_DIR
}

# Install orange Terminal server client theme.
# Takes backup of original theme.
function install_tsclient
{
	wget http://users.utu.fi/ljtaim/downloads/tsclient_dapper_theme.tar.gz
	tar zxf tsclient_dapper_theme.tar.gz
	mv /usr/share/pixmaps/tsclient /usr/share/pixmaps/tsclient_ol_backup
	mv tsclient /usr/share/pixmaps/
}

# Install orange Gaim theme.
# Takes backup of original theme.
function install_gaim_theme
{
	wget http://users.utu.fi/ljtaim/downloads/gaim_dapper_theme.tar.gz
	tar zxf gaim_dapper_theme.tar.gz
	mv /usr/share/pixmaps/gaim /usr/share/pixmaps/gaim_ol_backup
	mv gaim /usr/share/pixmaps/
	
	wget http://users.utu.fi/ljtaim/downloads/gaim.png
	mv gaim.png /usr/share/pixmaps/
}

# Install misc icon improvements.
# Takes backup of original icons.
function install_misc_icons
{
	# Quit and OK/apply icons
	ln -s /usr/share/icons/Tango/scalable/actions/dialog-close.svg /usr/share/icons/Tango/scalable/actions/gtk-quit.png
	ln -s /usr/share/icons/Tango/scalable/actions/dialog-apply.svg /usr/share/icons/Tango/scalable/actions/gtk-ok.svg
	ln -s /usr/share/icons/Tango/scalable/actions/dialog-apply.svg /usr/share/icons/Tango/scalable/actions/gtk-yes.svg
	ln -s /usr/share/icons/Tango/scalable/actions/dialog-apply.svg /usr/share/icons/Tango/scalable/actions/stock-apply.svg
	cd /usr/share/icons/
	sudo gtk-update-icon-cache --force Tango
	cd $TEMP_DIR
	
	# Synaptic icon
	wget http://users.utu.fi/ljtaim/system-upgrade.png
	mv /usr/share/synaptic/glade/system-upgrade.png /usr/share/synaptic/glade/system-upgrade_ol_backup.png
	mv system-upgrade.png /usr/share/synaptic/glade/
	
	# Go-Home icon
	wget http://users.utu.fi/ljtaim/downloads/go-home-icons.tar.gz
	tar zxf go-home-icons.tar.gz
	mv /usr/share/icons/Human/24x24/actions/go-home.png /usr/share/icons/Human/24x24/actions/go-home_ol_backup.png
	mv /usr/share/icons/Human/22x22/actions/go-home.png /usr/share/icons/Human/22x22/actions/go-home_ol_backup.png
	mv go-home24.png /usr/share/icons/Human/24x24/actions/go-home.png
	mv go-home22.png /usr/share/icons/Human/22x22/actions/go-home.png
	mv go-home16.png /usr/share/icons/Human/16x16/actions/go-home.png
	
	# Volume icons
	wget http://users.utu.fi/ljtaim/downloads/volume-icons.tar.gz
	tar zxf volume-icons.tar.gz
	mv audio-volume-high.png /usr/share/icons/Human/22x22/status/
	mv stock_volume-1.png /usr/share/icons/Human/22x22/status/
	mv stock_volume-med.png /usr/share/icons/Human/22x22/status/
	mv audio-volume-low.png /usr/share/icons/Human/22x22/status/
    mv stock_volume-2.png /usr/share/icons/Human/22x22/status/
    mv stock_volume-min.png /usr/share/icons/Human/22x22/status/
    mv audio-volume-medium.png /usr/share/icons/Human/22x22/status/
	mv stock_volume-3.png /usr/share/icons/Human/22x22/status/
	mv stock_volume-mute.png /usr/share/icons/Human/22x22/status/
	mv audio-volume-muted.png /usr/share/icons/Human/22x22/status/
	mv stock_volume-4.png /usr/share/icons/Human/22x22/status/
	mv stock_volume.png /usr/share/icons/Human/22x22/status/
	mv stock_volume-0.png /usr/share/icons/Human/22x22/status/
	mv stock_volume-max.png /usr/share/icons/Human/22x22/status/
	
	# Ubuntu menu logo icon
	wget http://users.utu.fi/ljtaim/downloads/start-here.png
	wget http://users.utu.fi/ljtaim/downloads/start-here24.png
	mv /usr/share/icons/Human/22x22/places/start-here.png /usr/share/icons/Human/22x22/places/start-here_ol_backup.png
	mv /usr/share/icons/Human/24x24/places/start-here.png /usr/share/icons/Human/24x24/places/start-here_ol_backup.png
	mv start-here.png /usr/share/icons/Human/22x22/places/
	mv start-here24.png /usr/share/icons/Human/24x24/places/start-here.png
	
	cd /usr/share/icons/
	sudo gtk-update-icon-cache --force Human
	cd $TEMP_DIR
}

# Install Gnomebaker icons.
# DOESN'T take backup of original icons. apt-get --reinstall will do fine.
function install_gnomebaker
{
	if [ -f "/usr/share/gnomebaker/baker-cd.png" ] 
	then
		wget http://users.utu.fi/ljtaim/downloads/gnomebaker_human_icons.tar.gz
		tar zxf gnomebaker_human_icons.tar.gz
		cd gnomebaker
		mv -f baker-add-dir.png /usr/share/gnomebaker
		mv -f baker-add-files.png /usr/share/gnomebaker
		mv -f baker-audio-copy.png /usr/share/gnomebaker
		mv -f baker-blank-cdrw.png /usr/share/gnomebaker
		mv -f baker-blank-dvdrw.png /usr/share/gnomebaker
		mv -f baker-burn-cd.png /usr/share/gnomebaker
		mv -f baker-cd-iso.png /usr/share/gnomebaker
		mv -f baker-cd.png /usr/share/gnomebaker
		mv -f baker-cue-image.png /usr/share/gnomebaker
		mv -f baker-data-copy.png /usr/share/gnomebaker
		mv -f baker-dvd-iso.png /usr/share/gnomebaker
		mv -f baker-import-session.png /usr/share/gnomebaker
		mv -f baker-remove-files.png /usr/share/gnomebaker
		mv -f gnomebaker-48.png /usr/share/gnomebaker
		mv -f splash_2.png /usr/share/gnomebaker
		cd $TEMP_DIR
	else
		zenity --info --title "Orange-look" --text "It seems that Gnomebaker is not installed. Installation will skip this part."
	fi
}

# Install Gconf-editor icons.
# Takes backup of original icons.
function install_gconf
{
	wget http://users.utu.fi/ljtaim/downloads/gconf-editor-dapper-icons.tar.gz
	tar zxf gconf-editor-dapper-icons.tar.gz
	mv /usr/share/pixmaps/gconf-editor /usr/share/pixmaps/gconf-editor_ol_backup
	mv gconf-editor /usr/share/pixmaps/
}

# Replace Human folder icons with Simple-Human folder icons.
# Takes backup of original icons.
function install_simple_folder
{
	# Remove png icons so that scalable svg files are used instead
	mv /usr/share/icons/Human/16x16/places/folder.png /usr/share/icons/Human/16x16/places/folder_ol_backup.png
	mv /usr/share/icons/Human/16x16/places/user-home.png /usr/share/icons/Human/16x16/places/user-home_ol_backup.png
	mv /usr/share/icons/Human/24x24/places/folder.png /usr/share/icons/Human/24x24/places/folder_ol_backup.png
	mv /usr/share/icons/Human/24x24/places/user-home.png /usr/share/icons/Human/24x24/places/user-home_ol_backup.png
	mv /usr/share/icons/Human/48x48/places/folder.png /usr/share/icons/Human/48x48/places/folder_ol_backup.png
	mv /usr/share/icons/Human/48x48/places/user-home.png /usr/share/icons/Human/48x48/places/user-home_ol_backup.png
	
	wget http://users.utu.fi/ljtaim/downloads/simple-human-icons.tar.gz
	tar zxf simple-human-icons.tar.gz
	mv /usr/share/icons/Human/scalable/filesystems /usr/share/icons/Human/scalable/filesystems_ol_backup
	mv /usr/share/icons/Human/scalable/places /usr/share/icons/Human/scalable/places_ol_backup
	mv filesystems /usr/share/icons/Human/scalable/
	mv places /usr/share/icons/Human/scalable/
	
	cd /usr/share/icons/
	gtk-update-icon-cache --force Human
	cd $TEMP_DIR
}

# Check if user is not root
if [ $(id -u) != "0" ]; then
    zenity --info --title "Orange-look" --text "You need to be root to install orange-look.\n Use sudo to run this script."
    exit 1
fi
# Ask if user want's to proceed with installation
zenity --question --title "Orange-look" --text "This is Ubuntu orange-look installer. Press OK to begin installation."

# Installation process. Ask on every improvement and execute install functions.
# Creates a temporary directory for downloads and it's removed after installation
# automatically.
if [ "$?" = "0" ]; then

	mkdir $TEMP_DIR
	cd ~/orange-look-temp
	
	zenity --question --title "Orange-look" --text "Do you want to install gconf-editor icons?"
	if [ "$?" = "0" ]; then
		$(install_gconf)
	fi
	
	zenity --question --title "Orange-look" --text "Do you want to install Orange Gaim theme?"
	if [ "$?" = "0" ]; then
		$(install_gaim_theme)
	fi
	
	zenity --question --title "Orange-look" --text "Do you want to install Gnomebaker icons?"
	if [ "$?" = "0" ]; then
		$(install_gnomebaker)
	fi
	
	zenity --question --title "Orange-look" --text "Do you want to install Terminal Server Client theme?"
	if [ "$?" = "0" ]; then
		$(install_tsclient)
	fi
	
	zenity --question --title "Orange-look" --text "Do you want to install Rhythmbox icons?"
	if [ "$?" = "0" ]; then
		$(install_rhythmbox)
	fi
	
	zenity --question --title "Orange-look" --text "Do you want to install Simple-folder icons?"
	if [ "$?" = "0" ]; then
		$(install_simple_folder)
	fi

	zenity --question --title "Orange-look" --text "Do you want to install misc icon improvements?"
	if [ "$?" = "0" ]; then
		$(install_misc_icons)
	fi
	
	#zenity --question --title "Orange-look" --text "Do you want to install orange wallpaper?"
	#if [ "$?" = "0" ]; then
	#	$(install_wallpaper)
	#fi

	#zenity --question --title "Orange-look" --text "Do you want to install Firestarter icons?"
	#if [ "$?" = "0" ]; then
	#	$(install_firestarter)
	#fi
	
	cd ..
	rm -rf orange-look-temp
	zenity --info --title "Orange-look" --text "All done! Please restart your X to make sure that all changes will apply."
	exit 0
else
	# User clicked cancel to first question
	echo "Orange-look installation aborted."
	exit 1
fi

```

---

### Post by henriquemaia on 2006-05-31
[quote=Laterix]I made a small guide for those how like to keep their dapper orange. My guide includes small improvements to Rhythmbox and new themes for Gaim and Terminal server client -programs.

Read my guide [**here**]("http://users.utu.fi/ljtaim/dapper-improvments.php").

I'd like to get feedback and questions in this thread. Hopefully you'll like it.

*Teaser image*
[URL="http://users.utu.fi/ljtaim/images/gaim_dapper.png"]
[IMG]http://users.utu.fi/ljtaim/images/dapper_gaim_thumb.png[/IMG]
[/URL][/quote]

Well... it's hard not to like it. Your website presentation is very good and professional and your orange Dapper looks amazing. Very nice work.

---

### Post by l4v4_f10w on 2006-05-31
Very nice website.

---

### Post by nalthien on 2006-05-31
The one thing that appears to really be missing is a "Human" theme for firefox (and yes, I know I can use epiphany for the look...but I don't want to use epiphany, I want to use firefox).

---

### Post by Laterix on 2006-05-31
[QUOTE=nalthien]The one thing that appears to really be missing is a "Human" theme for firefox (and yes, I know I can use epiphany for the look...but I don't want to use epiphany, I want to use firefox).[/QUOTE]
This is not true. Maybe I should add it to my website, but you can find one here
[http://www.ffnn.nl/pages/projects/ubuntu-firefox-themes/download-install.php]("http://www.ffnn.nl/pages/projects/ubuntu-firefox-themes/download-install.php")

And thanks all for you feedback.

---

### Post by ericesque on 2006-05-31
very nice work indeed.  To me, those colors scream tangerine.

---

### Post by nalthien on 2006-05-31
[QUOTE=Laterix]This is not true. Maybe I should add it to my website, but you can find one here
[http://www.ffnn.nl/pages/projects/ubuntu-firefox-themes/download-install.php]("http://www.ffnn.nl/pages/projects/ubuntu-firefox-themes/download-install.php")

And thanks all for you feedback.[/QUOTE]
Oh nice.  Thanks!

Whoever created that should post it to the official site addons.mozilla.org.  Much easier to find there than on some blog post in the wild.

---

### Post by Laterix on 2006-05-31
[QUOTE=nalthien]Oh nice.  Thanks!

Whoever created that should post it to the official site addons.mozilla.org.  Much easier to find there than on some blog post in the wild.[/QUOTE]
Actually there is a package in repository for those themes. Can't remember it's name though.

---

### Post by antipasta on 2006-05-31
I love the orange titlebar of your windows, and your font and close/minimize icons are really cool as well.

I checked your site, but it doesn't seem to mention those aspects of your theme. How can I make my dapper look like that?

---

### Post by McDuff on 2006-05-31
it is firefox-themes-ubuntu

---

### Post by John.Michael.Kane on 2006-05-31
Laterix just looked at your site, and i must say it is very well written, and easy to understand both howto's you have there.

---

### Post by meborc on 2006-05-31
really nice work... i love orange (in the mornings) :cool:

---

### Post by yostral on 2006-05-31
The package name is "firefox-themes-ubuntu" .

Edit: Oups.. too late :D

---

### Post by Laterix on 2006-05-31
Someone asked about theme I use. It's called Smooth-orange. I updated my site and you can find a link there.

---

### Post by Laterix on 2006-05-31
I added **Firefox** and **Gnomebaker** to my guide. Enjoy!

---

### Post by Whoopie on 2006-05-31
Hi Laterix,

nice howto, thanks!

Just a comment: it should be /usr/share/gnomebaker, not /usr/share/pixmaps/gnomebaker.

Best regards,
Whoopie

---

### Post by southerncross on 2006-05-31
thanks for the great job laterix... i love orange too

---

### Post by Laterix on 2006-05-31
[QUOTE=Whoopie]
Just a comment: it should be /usr/share/gnomebaker, not /usr/share/pixmaps/gnomebaker.
[/QUOTE]
Thanks, that's true. I have to change it.

---

### Post by Qoon3x on 2006-05-31
very nice guide!
And thanks for the Rhythmbox icons :)

---

### Post by Whoopie on 2006-05-31
Hi,

just found a tango theme for thunderbird:
[https://addons.mozilla.org/thunderbird/2258/](https://addons.mozilla.org/thunderbird/2258/)

Best regards,
Whoopie

---

### Post by groggyboy on 2006-05-31
whew - that is *really* orange!

you weren't kidding about it, were you!

---

### Post by Laterix on 2006-05-31
[QUOTE=Whoopie]
just found a tango theme for thunderbird:
[https://addons.mozilla.org/thunderbird/2258/](https://addons.mozilla.org/thunderbird/2258/)
[/QUOTE]
Thanks for the link, I'll guess I could add this to guide tomorrow altough I prefer Evolution myself.

---

### Post by Nonno Bassotto on 2006-05-31
Maybe you can consider adding some information here.
[http://www.ubuntuforums.org/showthread.php?t=184150](http://www.ubuntuforums.org/showthread.php?t=184150)
This thread has the aim to collect some cool themes, but up to now there are just two entries. A post with some screenshots and a link to your guide would be very nice.

---

### Post by steveneddy on 2006-05-31
What rhymes with orange?

doorhinge!

That made me 41 beans. What do I win?

---

### Post by Turgon on 2006-06-01
Very nice, this should be default!

---

### Post by Alex_Perry on 2006-06-01
What font are you using in those screenshots?

---

### Post by skippy81 on 2006-06-01
I love both your website and your dapper sugestions, you obviously have a very good eye for graphics.  

I am using the suggested wallpaper and compiz theme now, and I think my desktop looks amazing.   Many thanks.

---

### Post by Laterix on 2006-06-01
[QUOTE=Alex_Perry]What font are you using in those screenshots?[/QUOTE]
It's called HandleGotD. Unfortunately it's not free font.

---

### Post by Laterix on 2006-06-01
Thankyou everyone for you feedback! You all have been very kind. I keep on working this still. I just added a small but important improvement to my guide.

It's about howto change your Rhythmbox notification icon to better one. Look at the screenshot below and your own icon. You'll see the difference.

---

### Post by Kobalt on 2006-06-01
Hi ! 
Great site & themes. 
By the way, you should add to your site this guification for gaim : 
[http://www.gnome-look.org/content/show.php?content=40005]("http://www.gnome-look.org/content/show.php?content=40005")

Cheers on Dapper !

---

### Post by hanzomon4 on 2006-06-01
How do you install the smooth-orange theme It keeps saying the file format is invalid

---

### Post by Laterix on 2006-06-01
[QUOTE=hanzomon4]How do you install the smooth-orange theme It keeps saying the file format is invalid[/QUOTE]
It's been a long time since I installed it. I can't remember, but I guess you could extract that tarball manually and then just move the smooth-orange directory to  *~/.themes*. It's a hidden directory, because it begins with a dot. You can get hidden directories shown in nautilus simply by pressing CTRL+H.

---

### Post by zerwas on 2006-06-01
[QUOTE=Laterix]It's been a long time since I installed it. I can't remember, but I guess you could extract that tarball manually and then just move the smooth-orange directory to  *~/.themes*. It's a hidden directory, because it begins with a dot. You can get hidden directories shown in nautilus simply by pressing CTRL+H.[/QUOTE]

That's exactly the way it works!
Great work, thank you, my desktop looks very nice 8)

---

### Post by peRosine on 2006-06-01
Thanks man, I love it.

---

### Post by poyner on 2006-06-04
unfortunately the orange theme seems to produce some odd results if you're using compiz..... is anyone able to make a package for compiz?

---

### Post by Laterix on 2006-06-04
[QUOTE=poyner]unfortunately the orange theme seems to produce some odd results if you're using compiz..... is anyone able to make a package for compiz?[/QUOTE]
What do you mean? I think smooth-orange theme is made to be used with Compiz. It's not even orange with Metacity.

---

### Post by poyner on 2006-06-04
[QUOTE=Laterix]What do you mean? I think smooth-orange theme is made to be used with Compiz. It's not even orange with Metacity.[/QUOTE]hmmmm what I mean is that some applications seem to have no theme applied to them. Like synaptic for instance. the scroll bars and buttons all seem to have reverted to a standard gtk theme. Maybe the orange theme is just missing some items or something? 
See my attached thumbnails.

---

### Post by Nonno Bassotto on 2006-06-04
This is because these apps are used with root privileges, hence they use root settings, including the themes. You may want to have a look at the fourth point of this thread
[http://ubuntuforums.org/showthread.php?t=77694&highlight=howto+eyecandy](http://ubuntuforums.org/showthread.php?t=77694&highlight=howto+eyecandy)

---

### Post by nami on 2006-06-04
I am trying to use smoothorange.

I have downloaded it onto my desktop and dropped it into the "themes preferences" window and it said "invalid file format" ???

How do I use it?

---

### Post by Laterix on 2006-06-04
[QUOTE=nami]I am trying to use smoothorange.

I have downloaded it onto my desktop and dropped it into the "themes preferences" window and it said "invalid file format" ???

How do I use it?[/QUOTE]
I gave instructions eariler in this thread. Please read the thread and you'll find the answers. Shortly: copy theme folder to ~/.themes.

---

### Post by projecteternity on 2006-06-04
[QUOTE=poyner]hmmmm what I mean is that some applications seem to have no theme applied to them. Like synaptic for instance. the scroll bars and buttons all seem to have reverted to a standard gtk theme. Maybe the orange theme is just missing some items or something? 
See my attached thumbnails.[/QUOTE]

The theme is in your user's theme folder and not root's so programs launched as root can't find them. The best fix for this is linking the root .theme directory to your own with:

(assuming you are in your home directory)
```
sudo ln -s .themes /root
```

Or you could move them one by one to the system directory or root's directory if you really wanted to.

---

### Post by alfonz on 2006-06-04
I rather like the no themes settings for root. At least that way I can tell what environment I am looking for and if its the ugly not themed one then i know I should finish up and close it ;)

BTW Laterix great guide.

---

### Post by yteh on 2006-06-04
Laterix... just wanted to say thanks.

---

### Post by Choad on 2006-06-04
mmmmmmm that looks sexeh

good work matey

---

### Post by lithorus on 2006-06-04
Thanks for this. It certainly looks different from everything else out there (XP/Vista/OSX) which is why I love it.

---

### Post by Laterix on 2006-06-04
[QUOTE=lithorus]Thanks for this. It certainly looks different from everything else out there (XP/Vista/OSX) which is why I love it.[/QUOTE]
Yeah, I think it has a nice unique Ubuntu feeling on it.

I added three very small improvments to my guide today. Just a few icons. One of them is here:
[IMG]http://www.taimila.com/images/orange-look/synaptic_icon.png[/IMG]
Or this alternative one:
[IMG]http://users.utu.fi/ljtaim/system-upgrade.png[/IMG]

---

### Post by zenwhen on 2006-06-04
Good work!

---

### Post by Laterix on 2006-06-05
[QUOTE=zenwhen]Good work![/QUOTE]
Thanks, another update **Gconf orange-look icons**.
[URL="http://users.utu.fi/ljtaim/images/gconf-dapper.png"]
[IMG]http://users.utu.fi/ljtaim/images/gconf-thumb.jpg[/IMG]
[/URL]

---

### Post by openmind on 2006-06-05
Subtle, yet very effective. Great job Laterix! =D>

---

### Post by Choad on 2006-06-06
[QUOTE=Laterix]Thanks, another update **Gconf human icons**.
[URL="http://users.utu.fi/ljtaim/images/gconf-dapper.png"]
[IMG]http://users.utu.fi/ljtaim/images/gconf-thumb.jpg[/IMG]
[/URL][/QUOTE]
your window shadows in xgl are lush fat things. mine look horrid and dont line up at the bottom right... how did you hack that? did you even change anything? am i trippin?

---

### Post by Laterix on 2006-06-06
[QUOTE=Choad]your window shadows in xgl are lush fat things. mine look horrid and dont line up at the bottom right... how did you hack that? did you even change anything? am i trippin?[/QUOTE]
Actually my Compiz is broken at the moment. :( But My Compiz decoration options are:

shadow_offset_x = 1
shadow_offset_y = 1
shadow_opacity = 0.9
shadow_radius = 20

---

### Post by Choad on 2006-06-06
[QUOTE=Laterix]Actually my Compiz is broken at the moment. :( But My Compiz decoration options are:

shadow_offset_x = 1
shadow_offset_y = 1
shadow_opacity = 0.9
shadow_radius = 20[/QUOTE]
ok now i sound like a total noob.... where did you configure that? i can't find it in gconf-editor

i searched for "shadow_offset_x" and it said it couldnt be found anywhere in gconf-editor

is the shadows a seperate plugin that needs to be added to compiz?

---

### Post by Choad on 2006-06-06
[QUOTE=Laterix]Actually my Compiz is broken at the moment. :( But My Compiz decoration options are:

shadow_offset_x = 1
shadow_offset_y = 1
shadow_opacity = 0.9
shadow_radius = 20[/QUOTE]
it would seem that according to [this](http://en.opensuse.org/Compiz#Decoration) that the options are in plugins>decoration but in my plugins>decoration all i have is short_description and long_description

i tried adding thos keys you game me but they didnt alter anything so i deleted them again

---

### Post by Laterix on 2006-06-06
[QUOTE=Choad]is the shadows a seperate plugin that needs to be added to compiz?[/QUOTE]
It's decoration plugin: /apps/compiz/plugins/decorations/allscreens/options in gconf.
if there are no options you can add them by yourself.

---

### Post by Choad on 2006-06-06
[QUOTE=Laterix]It's decoration plugin: /apps/compiz/plugins/decorations/allscreens/options in gconf.
if there are no options you can add them by yourself.[/QUOTE]
how do you add a directory?

my one ends at /decorations

how can i add /allscreens/options ??? i cant find any menu functions and there is no right click menu

im off out now tho so i wont reply till tomorow. thanks for the help anyway !!!

---

### Post by mejy on 2006-06-06
Is any one working on an installation script?  If not I might give it a go.

Also a few suggestions (think of it as a wishlist, I know its unrealistic)
[LIST]
[*]Main Menu Icons
[LIST]
[*]Rhythmbox
[*]Totem
[*]Gimp
[*]gThumb
[*]AbiWord
[*]GNumeric
[*]Gnome Games in Human would be awesome
[*]GConf Editor
[*]Firefox, Thunderbird icons from here - [http://www.gnome-look.org/content/show.php?content=36589](http://www.gnome-look.org/content/show.php?content=36589) - would be cool if you can get the guys permission
[/LIST]
[*]An 'Apply' icon for synaptic - the ok dialogue one would do fine
[*]Now into the realms of fantasy... OpenOffice Icons & Gimp Icons :D (although you might be able to intergrate jimmac's ones if he releases them under an appropriate lisence [http://jimmac.musichall.cz/icons.php](http://jimmac.musichall.cz/icons.php))
[/LIST]
A few of these are floating round the net and I intend to give a few others a go over the weekend.  Anyway, really great work - keep it up!

---

### Post by Laterix on 2006-06-07
[QUOTE=mejy]Is any one working on an installation script?  If not I might give it a go.

Also a few suggestions (think of it as a wishlist, I know its unrealistic)
[/QUOTE]
I was thinking of write installation script, because it shouldn't be too hard. Just few wget, tar and copy commands. But you're more than welcome to do it, if you want to. :)

About your wishlist, I agree with it, but unfortunately I'm not an artist really. All my improvements on the guide are based on existing icons. I have modded some icons a bit, but I haven't really done any icons from the scratch.

---

### Post by Choad on 2006-06-07
[QUOTE=Choad]how do you add a directory?

my one ends at /decorations

how can i add /allscreens/options ??? i cant find any menu functions and there is no right click menu

im off out now tho so i wont reply till tomorow. thanks for the help anyway !!![/QUOTE]
anyone?

---

### Post by Laterix on 2006-06-07
[QUOTE=Choad]anyone?[/QUOTE]
I don't know, but I think you get answers easier in a Compiz thread or [compiz forums]("http://www.compiz.net").

---

### Post by Choad on 2006-06-07
[QUOTE=Laterix]I don't know, but I think you get answers easier in a Compiz thread or [compiz forums]("http://www.compiz.net").[/QUOTE]
ahahaaaaa

ok i found on that forum u linked me to if you go to [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) and add his repository then upgrade the system it will fix a bunch of problems. it also added some cool shizzle like trail effects and all kinds of jazz. highly recomend you add that repo

in fact if i were you i'd add it to your "how to make dapper look cool" tutorial because some of the plugins it gives are wicked

---

### Post by anodizer on 2006-06-11
Laterix this is really great work.
There is a small problem with gaim though. The logo.png in your icons is too big and looks awful. Maybe you use Gaim 2 or smthn and your logo is perfect, but could you make the same with other dimensions? (210x150 pixels, gaim 1.5 use this).

---

### Post by Laterix on 2006-06-11
[QUOTE=anodizer]Laterix this is really great work.
There is a small problem with gaim though. The logo.png in your icons is too big and looks awful. Maybe you use Gaim 2 or smthn and your logo is perfect, but could you make the same with other dimensions? (210x150 pixels, gaim 1.5 use this).[/QUOTE]
Yes, I have Gaim 2.0 beta and I have tested theme only with it. Why don't you install 2.0? It's a way better than 1.5 anyway. :)

---

### Post by surfer57 on 2006-06-11
kewl! I like, I like a lot!!!  awesome!!!

---

### Post by ayoli on 2006-06-12
nice tweaks and beautiful website ;)
just a comment about your guide to make ubuntu looks like OSX: you don't have to logout/login to have your new fonts working, a *sudo fc-cache -f -v /usr/share/fonts* should do the trick.
Another thing that really makes look OSX is [kxdocker]("http://www.xiaprojects.com/www/prodotti/kxdocker/main.php") bar, but it requires qt libs.
(a recent .deb of kxdocker can be found here: [http://asher256-repository.tuxfamily.org/english.php](http://asher256-repository.tuxfamily.org/english.php))

---

### Post by nocturn on 2006-06-12
Many of these improvements are great.  I especially hated the fact that Synaptic had such ugly icons while Dapper has a nice theme.

Maybe you can create a launchpad entry (bugreport) to get them included.
Mark announced earlier that there may be an artwork overhaul for Dapper after release.

---

### Post by Laterix on 2006-06-12
[QUOTE=nocturn]Many of these improvements are great.  I especially hated the fact that Synaptic had such ugly icons while Dapper has a nice theme.

Maybe you can create a launchpad entry (bugreport) to get them included.
Mark announced earlier that there may be an artwork overhaul for Dapper after release.[/QUOTE]
I really don't feel taking credit for these, because all icons I use are not my work. I just edit them little and put them into new places. Some of the improvements could be "fixed" in next Ubuntu relase, but others are application specific.

I added a new icon-package and installation instructions to my site. This time it's Firestarter's turn to fit better with Dapper look. Link to guide is in my signature and in the first post of this thread.

**Firestarter - Dapper look**
[URL="http://users.utu.fi/ljtaim/images/firestarter.png"]
[IMG]http://users.utu.fi/ljtaim/images/firestarter_thumb.png[/IMG]
[/URL]

---

### Post by Nibiruet on 2006-06-14
[QUOTE=Laterix]This is not true. Maybe I should add it to my website, but you can find one here
[http://www.ffnn.nl/pages/projects/ubuntu-firefox-themes/download-install.php]("http://www.ffnn.nl/pages/projects/ubuntu-firefox-themes/download-install.php")

And thanks all for you feedback.[/QUOTE]
Any similar themes for Thunderbird?

---

### Post by Laterix on 2006-06-15
[QUOTE=Nibiruet]Any similar themes for Thunderbird?[/QUOTE]
This link was posted to this thread earlier by Whoopie.
[https://addons.mozilla.org/thunderbird/2258/]("https://addons.mozilla.org/thunderbird/2258/")

---

### Post by imagine on 2006-06-15
Very nice.
I hope you extend your guide.

---

### Post by Laterix on 2006-06-30
I added a set of simple human folder icons. I also added these to [gnome-look]("http://www.gnome-look.org/content/show.php?content=41750").

[IMG]http://www.gnome-look.org/content/pre1/41750-1.png[/IMG]

I made these icons for those who like Human theme, but thinks that current folder artwork is too glossy. I'm not one of those though. ;)

EDIT: Actually, these new folders look pretty good on my desktop. These go better with rest of my desktop even though I'm fan of the original folder artwork.

---

### Post by joakim2 on 2006-07-01
[QUOTE=Laterix]I added a set of simple human folder icons. I also added these to [gnome-look]("http://www.gnome-look.org/content/show.php?content=41750").

[IMG]http://www.gnome-look.org/content/pre1/41750-1.png[/IMG]

I made these icons for those who like Human theme, but thinks that current folder artwork is too glossy. I'm not one of those though. ;)

EDIT: Actually, these new folders look pretty good on my desktop. These go better with rest of my desktop even though I'm fan of the original folder artwork.[/QUOTE]

I rm -rf'ed /usr/share/icons/Human/scalable/{places,filesystems} and replaced them with the folders in your pack but the icons didn't change :(

---

### Post by Laterix on 2006-07-01
[QUOTE=joakim2]I rm -rf'ed /usr/share/icons/Human/scalable/{places,filesystems} and replaced them with the folders in your pack but the icons didn't change :([/QUOTE]
You might need to refresh icon cache. Just go in your terminal to **/usr/share/icons** directory and apply this command:
```

sudo gtk-update-icon-cache -f Human

```
That should do it.

---

### Post by joakim2 on 2006-07-01
[QUOTE=Laterix]You might need to refresh icon cache. Just go in your terminal to **/usr/share/icons** directory and apply this command:
```

sudo gtk-update-icon-cache -f Human

```
That should do it.[/QUOTE]

No such luck :( I even rebooted just to be sure but it's the same old Human icons...

---

### Post by Laterix on 2006-07-01
[QUOTE=joakim2]No such luck :( I even rebooted just to be sure but it's the same old Human icons...[/QUOTE]
That's strange. I assume that you are using Human icons and not any other iconset.

Are you sure that you have files in **/usr/share/icons/Human/scalable/filesystems** and **/usr/share/icons/Human/scalable/places**, because I can't see why it wouldn't work.

Also, check that those files have read permissions for all users.

---

### Post by joakim2 on 2006-07-01
[QUOTE=Laterix]That's strange. I assume that you are using Human icons and not any other iconset.

Are you sure that you have files in **/usr/share/icons/Human/scalable/filesystems** and **/usr/share/icons/Human/scalable/places**, because I can't see why it wouldn't work.

Also, check that those files have read permissions for all users.[/QUOTE]

Yes! It's driving me nuts now! If I browser to the folders in Nautilus I see the new icons fine, but they just won't show up as the folder icons! I checked the time stamp on the icon cache file to make sure it was getting updated properly and it is, the permissions look fine or I wouldn't be able to browse to those folders in Nautilus either. I'm fairly stumped :(

---

### Post by Laterix on 2006-07-01
[QUOTE=joakim2]Yes! It's driving me nuts now! If I browser to the folders in Nautilus I see the new icons fine, but they just won't show up as the folder icons! I checked the time stamp on the icon cache file to make sure it was getting updated properly and it is, the permissions look fine or I wouldn't be able to browse to those folders in Nautilus either. I'm fairly stumped :([/QUOTE]
This is very odd. I can't think of anything right now, but you could try to download and install [this]("http://www.gnome-look.org/content/show.php?content=41807") instead. Someone made a complete icon theme of my Simple icons. Perhaps it works...

---

### Post by joakim2 on 2006-07-01
[QUOTE=Laterix]This is very odd. I can't think of anything right now, but you could try to download and install [this]("http://www.gnome-look.org/content/show.php?content=41807") instead. Someone made a complete icon theme of my Simple icons. Perhaps it works...[/QUOTE]

Yup -  that one worked. That is still so weird...

---

### Post by Laterix on 2006-07-01
**New Update**

I wrote an **install script** for my Orange-look. Please see the first post for more detail. I hope that all problems are reported to this thread. It's also nice to hear if it works. :)

---

### Post by MakubeX on 2006-07-01
[QUOTE=joakim2]Yes! It's driving me nuts now! If I browser to the folders in Nautilus I see the new icons fine, but they just won't show up as the folder icons! I checked the time stamp on the icon cache file to make sure it was getting updated properly and it is, the permissions look fine or I wouldn't be able to browse to those folders in Nautilus either. I'm fairly stumped :([/QUOTE]

hmm.. may i know what application (or specific theme/app) that shows the info on hardware on your screenshot? I'm curious because it looks clean.

Thanks.

---

### Post by joakim2 on 2006-07-01
[QUOTE=MakubeX]hmm.. may i know what application (or specific theme/app) that shows the info on hardware on your screenshot? I'm curious because it looks clean.

Thanks.[/QUOTE]

Certainly sir, it's conky:

[http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)

---

### Post by Laterix on 2006-07-01
OOPS! nevermind

---

### Post by Hairy_Palms on 2006-07-01
on your osx gconf theme the link downloads the orange gconf theme :)

---

### Post by Laterix on 2006-07-01
[QUOTE=Hairy_Palms]on your osx gconf theme the link downloads the orange gconf theme :)[/QUOTE]
Argh, you're right. I have replaced wrong package with the new version. I made dapper gconf to fit better with my simple-folders, but I have replaced osx package instead. Too bad, that I don't have that OSX package anymore...

PS. Install script has some features that are not in the guide yet. For example that orange menu logo you can see in screenshot. I'll add those later... this was just a hint to everyone.

No one has been brave enough to run my script :D

---

### Post by Janux on 2006-07-01
Great improvements, thanks!
There is just one thing, thought. In your screenshot you have a nice Music Player icon (Rhythmbox maybe?), it would be great if you post that too.

---

### Post by Hairy_Palms on 2006-07-02
rhythmbox howto is in the guide, also the file manager in the screenshot is thunar not nautilus isnt it?

---

### Post by Laterix on 2006-07-02
[QUOTE=Hairy_Palms]rhythmbox howto is in the guide, also the file manager in the screenshot is thunar not nautilus isnt it?[/QUOTE]
Yes, it's thunar and it's in dapper repoistory.

> 
There is just one thing, thought. In your screenshot you have a nice Music Player icon (Rhythmbox maybe?), it would be great if you post that too.

Actually that image is part of rhythmbox package now. I updated the tar.gz file, but did't have to time to update guide yet. My script installs that icon and few other new rhythmbox icons too. If you don't want to use script then you can wait that I update it into guide.

Script will also install that volume icon I have there, if you select to install misc icons.

---

### Post by Janux on 2006-07-02
[quote=Laterix]Actually that image is part of rhythmbox package now. I updated the tar.gz file, but did't have to time to update guide yet. My script installs that icon and few other new rhythmbox icons too. If you don't want to use script then you can wait that I update it into guide.

Script will also install that volume icon I have there, if you select to install misc icons.[/quote]
Thanks, just changed the trayicon!

---

### Post by John Jason Jordan on 2006-07-03
[QUOTE=Laterix]Yes, it's thunar and it's in dapper repository.[/QUOTE]
I just discovered thunar yesterday and immediately installed it. I love it! All except for one thing -- there seems to be no Search function. Have I just missed it somewhere? Or might it be possible to make a Search function using an Action? 

Would also like to be able to get it to see my Windows desktop over my home ethernet (via samba). It doesn't do this by default. Any suggestions?

---

### Post by Laterix on 2006-07-03
[QUOTE=John Jason Jordan]
Would also like to be able to get it to see my Windows desktop over my home ethernet (via samba). It doesn't do this by default. Any suggestions?[/QUOTE]
I think there is no search neither network protocol supports at the moment. I would really like to see FTP and SFTP support in the future.

While writting to thread again, i could introduce my next updates. I'm still working on them, but here is a preview. :) Firefox and Thunderbird themes for orange-look.

[URL="http://users.utu.fi/ljtaim/pics/pewview.png"]
[IMG]http://users.utu.fi/ljtaim/pics/pewview_thumb.png[/IMG]
[/URL]

---

### Post by domino on 2006-07-06
> 
While writting to thread again, i could introduce my next updates. I'm still working on them, but here is a preview. Firefox and Thunderbird themes for orange-look.

I love the preview! I'll just wait for the next update before running the script. Or shuold I just run the script now?

---

### Post by ericesque on 2006-07-07
excellent work laterix.  Ubuntu has needed this kind of cohesion for some time now.  Someone thinking outside the win/osx cookie cutter box.  I like the simple icons for the right side of the panel.  color makes for too much clutter over there.

---

### Post by jharris on 2006-07-07
Extremely nice theme laterix. Coming over from OS X, this theme, tied in with XGL, makes me feel more at home in ubuntu. I sincerely hope that you continue to develop/enhance the orange theme and perhaps even diversify it eventually with other colours ;)

Anyway, many thanks for making my time in ubuntu even more enjoyable.

-J

---

### Post by dspivey on 2006-07-07
thank you very much, laterix.

---

### Post by Laterix on 2006-07-07
> **domino said:**
> I love the preview! I'll just wait for the next update before running the script. Or shuold I just run the script now?
I would say that you could run script now, because I don't know how to install thunberbird or firefox themes with script. So they won't be part of it anyway.

And thank you for all your nice comments! It makes me feel that this is not vain.

I bought my own domain few days ago and I will move my site there. It's still available at the old address, but I recommend you to update your bookmark (if someone really have made one) to [www.taimila.com]("http://www.taimila.com")

---

### Post by n00bWillingToLearn on 2006-07-07
I tried the script, on a brand new unaltered user account, and most of it didn't work. I don't have the new backrounds, most icons, title bar... A few of the things worked but I am mostly still brown and sad :( I will look at the script myself (although all I know is java, it seems strait foreward enough ) and try to see what might have gone wrong. It may also be a problem with my machine as I have been having problems with X lately. Anyways, I am willing to make another user and try again, this time saving any output, or anything else you want to troubleshoot. I seem to be your only beta tester and I know how that feels see: [http://ubuntuforums.org/showthread.php?t=198809](http://ubuntuforums.org/showthread.php?t=198809)
for my own script / program ( for changing screen saver preferences in gnome-screensaver ) That nobody seems interested in enough to help test it out :(

[edit] Your install script also effects all users so my one user with my personal configuration, and my other with your osx theme ( I keep mulltiple users to try out new looks without having to worry about uninstalling / reverting anything ) are all 1/3 orange. If possible, you might want to modify your script to only change the current users configuration.

---

### Post by Laterix on 2006-07-08
> **n00bWillingToLearn said:**
> I tried the script, on a brand new unaltered user account, and most of it didn't work. I don't have the new backrounds, most icons, title bar... A few of the things worked but I am mostly still brown and sad :( 

That's too bad. :( The script doesn't acutally install wallpaper, because I don't know how to do that, but you can do missing pieces manually by following my guide.

> 
I will look at the script myself (although all I know is java, it seems strait foreward enough ) and try to see what might have gone wrong. 

I appriciate it. It's quite simple and you shouldn't have problems understading it.

> 
Your install script also effects all users so my one user with my personal configuration, and my other with your osx theme ( I keep mulltiple users to try out new looks without having to worry about uninstalling / reverting anything ) are all 1/3 orange. If possible, you might want to modify your script to only change the current users configuration.

Unfortunately this is not possible for all improvements. Some of them could be done user spesific though. Perhaps I should do that.

---

### Post by Don_DiZzLe on 2006-07-08
Im triyin to compile firestarter with the u'r new icons from the ur guide but  at the make command I get this:

libtool: link: cannot find the library `/usr/lib/libXrender.la'
make[3]: *** [firestarter] Error 1
make[3]: Leaving directory `/home/dazkrlauwste/firestarter-1.0.3/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dazkrlauwste/firestarter-1.0.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dazkrlauwste/firestarter-1.0.3'
make: *** [all-recursive-am] Error 2
dazkrlauwste@Don-DiZzLe:~/firestarter-1.0.3$

How do I fix this?

---

### Post by Laterix on 2006-07-08
> **Don_DiZzLe said:**
> Im triyin to compile firestarter with the u'r new icons from the ur guide but  at the make command I get this:

libtool: link: cannot find the library `/usr/lib/libXrender.la'
make[3]: *** [firestarter] Error 1
make[3]: Leaving directory `/home/dazkrlauwste/firestarter-1.0.3/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dazkrlauwste/firestarter-1.0.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dazkrlauwste/firestarter-1.0.3'
make: *** [all-recursive-am] Error 2
dazkrlauwste@Don-DiZzLe:~/firestarter-1.0.3$

How do I fix this?

Looks like my guide is missing some dependencis. I had already installed all developement packages, so I don't know what it actually needs, but I think you need to install at least libx11-dev packages with apt-get. Try make after that again and tell me if it works.

---

### Post by domino on 2006-07-10
> **Laterix said:**
> I would say that you could run script now, because I don't know how to install thunberbird or firefox themes with script. So they won't be part of it anyway.
[/URL]
Then may I ask where you got or a dl link for the nice looking Ff and Tb themes on your screeny?

Thanks!

---

### Post by Don_DiZzLe on 2006-07-10
What are the fonts that u use in u'r screenie?

Their very cool!!

---

### Post by Laterix on 2006-07-10
> **domino said:**
> Then may I ask where you got or a dl link for the nice looking Ff and Tb themes on your screeny?

I haven't finished those yet, so there is no download at the moment. I will add them to my guide when they are ready. It's summer and all, so I don't sit all the time on my computer. :) It might take some time...


> 
What are the fonts that u use in u'r screenie?

Font is called handleGotD and unforunately it's not free of charge. So please don't ask download links.

---

### Post by domino on 2006-07-10
AAh np mate. I thought it was already posted somewhere. Have a great summer!

---

### Post by Laterix on 2006-07-20
> **domino said:**
> Have a great summer!
I will!

Just a small update this time. I made Compiz theme for Orange-look. It doesn't differ that much from the original compiz theme, but I like it because it's simple.

Here is a [preview]("http://users.utu.fi/ljtaim/pics/orange-compiz.png").

[**Download here**]("http://www.taimila.com/downloads/Orange-look.cgwdtheme.tar.gz")

---

### Post by Kobalt on 2006-07-20
Niiice work Laterix ! :rolleyes: 
I really like the smooth & orange look you give in your improvements... You should really be somehow contributing to the official art team.

---

### Post by domino on 2006-07-20
Still waiting for that perfect Ff theme :)

---

### Post by Reducer on 2006-07-21
Thanks!  I love this theme on my XGL/compiz setup.
I couldn't seem to find the wallpaper at the link you provided.  Can you recommend another wallpaper to match your theme?

I'm looking forward to ff and tb themes as well!

Jason

---

### Post by Laterix on 2006-07-21
> **Reducer said:**
> 
I couldn't seem to find the wallpaper at the link you provided.

That's wierd. I tried it and the link works for me. Here is a [direct link to wallpaper]("http://zone13.digitalgrafis.com/files/intelmac_red_16001024_notxt.jpg").

---

### Post by Kobalt on 2006-07-21
It's a shame, I can't seem to install your brand new orange theme for compiz Laterix... I have compizthemer and cgwd installed, both updated, yet when I try to import it with Compizthemer it got an error message like : "Error calling tar." What do you think of that ?

---

### Post by Laterix on 2006-07-21
> **Kobalt said:**
> It's a shame, I can't seem to install your brand new orange theme for compiz Laterix... I have compizthemer and cgwd installed, both updated, yet when I try to import it with Compizthemer it got an error message like : "Error calling tar." What do you think of that ?
I have Compizthemer 0.12 and I exported it with that. I really don't know much about compiz themes and how they work. I just assumed that one could download my package and import it with compizthemer. So, it is possible that I have missed something there. Anyone else? I'd like to if anyone is able to install that.

---

### Post by Laterix on 2006-07-21
> **domino said:**
> Still waiting for that perfect Ff theme :)

Heh heh, Well your support made me to release it. It's not complete, but I think it has all the important icons.

Preview
[URL="http://users.utu.fi/ljtaim/pics/firefox.png"]
[IMG]http://users.utu.fi/ljtaim/pics/firefox-thumb.png[/IMG]
[/URL]

Download is in my guide.

---

### Post by Kobalt on 2006-07-21
Well in fact, it seems it's my compizthemer that has a problem : it just doesn't work... There was an update this morning, from version 0.12 to 0.13, I had to install the "cgwd" package. Since then, I just can't make any changes to my metacity theme, through Compizthemer or the System > Pref. > Themes tab... Anyone having this trouble around here ?

---

### Post by Reducer on 2006-07-21
> **Laterix said:**
> I have Compizthemer 0.12 and I exported it with that. I really don't know much about compiz themes and how they work. I just assumed that one could download my package and import it with compizthemer. So, it is possible that I have missed something there. Anyone else? I'd like to if anyone is able to install that.

I had the same problem.  To work around it, I downloaded the OSX theme from Laterix's site as well then put the .png from that tar.gz into the orange tar.gz.  It worked like a charm after that; although my maximize, close buttons may be off. :)

---

### Post by Reducer on 2006-07-21
> **Laterix said:**
> That's wierd. I tried it and the link works for me. Here is a [direct link to wallpaper]("http://zone13.digitalgrafis.com/files/intelmac_red_16001024_notxt.jpg").

Thanks!  I was looking for one called 'orange' so I missed it. I didn't even think about using the 'red' one.

---

### Post by lazyd2 on 2006-07-21
> **Kobalt said:**
> Well in fact, it seems it's my compizthemer that has a problem : it just doesn't work... There was an update this morning, from version 0.12 to 0.13, I had to install the "cgwd" package. Since then, I just can't make any changes to my metacity theme, through Compizthemer or the System > Pref. > Themes tab... Anyone having this trouble around here ?
See [here]("http://www.ubuntuforums.org/showpost.php?p=1283090&postcount=23")

---

### Post by Kobalt on 2006-07-21
Thanks a lot lazyd2, I got my compizthemer to work again ! I still can't install the orange Laterix's theme though... 
Replacing gnome-window-decroator by cgwd package improved the speed of compizthemer actually...

---

### Post by Sircoelho on 2006-07-21
Just installed the script but I can't see your theme at System->Preferences->Themes.

No errors occurred ad script installation.

---

### Post by Laterix on 2006-07-21
> **Sircoelho said:**
> Just installed the script but I can't see your theme at System->Preferences->Themes.

No errors occurred ad script installation.

Script installs only limited amount of improvements, because of my lack of knowledge of Bash scripting. You have to do some things still manually. :(

---

### Post by Sircoelho on 2006-07-21
Ok, but where I can get and install your screenshot window decoration (Theme)?

You're using official ubuntu font right?

---

### Post by Laterix on 2006-07-21
> **Sircoelho said:**
> Ok, but where I can get and install your screenshot window decoration (Theme)?
Link is in my guide, but here is [direct link]("http://www.taimila.com/downloads/Orange-look.cgwdtheme.tar.gz"). It's Compiz theme and there is probably something wrong with it. Read posts above for more information.

> 
You're using official ubuntu font right?

Font in my screenshots is HandleGotD and it's not Ubuntu font. It's also NOT free font so don't ask any download links. I don't have them.

---

### Post by n00bWillingToLearn on 2006-07-22
Sorry about my earlier post:oops:, your script installed everything fine. Some of my problems where because I just thought it installed things that it didn't, others were with my machine, for instance the title bar only seems to be orange in compiz and because I am on a PPC and Nvidea won't recompile their drivers for PPC:evil: I have not gotten XGL to work yet. It was only when I was setting up my friends x86 machine with XGL that I realized it did work in Compiz. Anyways, GREAT job. Your screenshots are probably the slickest and cleanest ones I have seen and I second the desire for you to help out with the official Ubuntu artwork team. One thing you could do that might even get things rolling would be to explicitly state that your guide is in the creative commons and your script under the GPL ( If you want them to be ). Again, great job and I look foreward to trying your new compiz theme ( the screenshot looks great:D) when I get compiz up and running.

---

### Post by harissza on 2006-07-22
Hi Laterix,

Thanks for the great theme and I really appreciate the hard work but this guide is lacking a bit. You should have really menioned at the beginning that you use your own fonts! You know we all live busy life and want to get things done quickly without reading 12 pages with mainly positive feedback.  

I have missed the point (alongsode of few others by the looks) that this "orange look" doesn't come with the fonts you have the screenshots of.

I was gonna get the rest though this morning and found that something is wrong. At the selection I didn't pick firestarter and gnomebaker because I don't have/need them but it shouldn't make difference at all. The script ran fine, no errors, restarted X. 

I got only the gnome-menu icon and volume control icon replaced on gnome-panel and the folder icons but nothing else. I really miss the window-frame ( and the fonts of course but that was explained) design. Wallpaper and GDM went fine manually, work ok. Any idea about the window frame problem?

Another question is that you prefer glossy icons according to one of your posts right? I got the the non-glossy ones this morning by the installer. Has it become default now? I would like to get the glossy ones. 

Any help much appreciated.

Adam

---

### Post by fragos on 2006-07-22
This is a stuningly beautiful piece of work.  Very taseful and complete.  It's obvious you spent a lot of time on this.  My hat's off to you.

---

### Post by Laterix on 2006-07-23
> **harissza said:**
> 
You should have really menioned at the beginning that you use your own fonts!

Yeah, you're right. I think I should have mention that or I could use some other font in screenshots.

> 
You know we all live busy life and want to get things done quickly without reading 12 pages with mainly positive feedback.

Yep, those are my favourite posts. :) Without them I wouldn't have continued to do this.

> 
I got only the gnome-menu icon and volume control icon replaced on gnome-panel and the folder icons but nothing else. I really miss the window-frame ( and the fonts of course but that was explained) design. Wallpaper and GDM went fine manually, work ok. Any idea about the window frame problem?

It is mentioned in my guide and in the first post that script doesn't change it all. It just helps you and saves some time, but you have to do things manually. I would love to have a script that makes it all, but I don't know how to do that. About window frame, are you using Compiz? If so there is a theme package on my site. If you have problems to install it, it's because of rapid developement of Compizthemer, I think. Are you saying that Rhythmbox icons didn't change?

> 
Another question is that you prefer glossy icons according to one of your posts right? I got the the non-glossy ones this morning by the installer. Has it become default now? I would like to get the glossy ones. 

Script asks "Do you want to install Simple-folder icons?". Those are the less glossy icons. If you select yes, it will use them, no and it will use default Human folder icons.

You're right, I said I like glossy more, but it took me only a day to change my mind. :) I really like those simple ones and they are now used in other themes (firefox, gconf, etc) too. So they are "official" icons of Orange-look.

If you want to use Human icons instead, here is small uninstall script just for you. This uninstalls only Simple folders.
```

#!/bin/bash

# Uninstall Simple folders.

if [ $(id -u) != "0" ]; then
    zenity --info --title "Error" --text "Use sudo to run this script."
    exit 1
fi

mv /usr/share/icons/Human/16x16/places/folder_ol_backup.png /usr/share/icons/Human/16x16/places/folder.png
mv /usr/share/icons/Human/16x16/places/user-home_ol_backup.png /usr/share/icons/Human/16x16/places/user-home.png
mv /usr/share/icons/Human/24x24/places/folder_ol_backup.png /usr/share/icons/Human/24x24/places/folder.png
mv /usr/share/icons/Human/24x24/places/user-home_ol_backup.png /usr/share/icons/Human/24x24/places/user-home.png
mv /usr/share/icons/Human/48x48/places/folder_ol_backup.png /usr/share/icons/Human/48x48/places/folder.png
mv /usr/share/icons/Human/48x48/places/user-home_ol_backup.png /usr/share/icons/Human/48x48/places/user-home.png
mv /usr/share/icons/Human/scalable/filesystems /usr/share/icons/Human/scalable/filesystems_ol
mv /usr/share/icons/Human/scalable/places /usr/share/icons/Human/scalable/places_ol
mv /usr/share/icons/Human/scalable/filesystems_ol_backup /usr/share/icons/Human/scalable/filesystems
mv /usr/share/icons/Human/scalable/places_ol_backup /usr/share/icons/Human/scalable/places

cd /usr/share/icons/
gtk-update-icon-cache --force Human

```

---

### Post by harissza on 2006-07-23
Hi Laterix,

>Yep, those are my favourite posts. :) Without them I wouldn't have continued to do this.

I'm sure they are. :)

>It is mentioned in my guide and in the first post that script doesn't >change it all. It just helps you and saves some time, but you have to do >things manually. I would love to have a script that makes it all, but I >don't know how to do that. About window frame, are you using Compiz? If so >there is a theme package on my site. If you have problems to install it, >it's because of rapid developement of Compizthemer, I think. Are you saying that Rhythmbox icons didn't change?

Ok, thanks I might have missed that... I have an onboard i915 card so no point for Compiz I suppose. I got a bit confused about the entire thing so my aplogies. 

I looked at your script a further and understood. I did what it meant to do I just misunderstood the topic and expected more. I did mainly all changes manually and all ok now. 

Thanks

Adam
Thanks

---

### Post by Kobalt on 2006-07-24
And finally, after today's update of Compizthemer (>0.18 ), your great orange theme works fine Laterix !:rolleyes: 
Thanks a lot for this contribution. I've just put the radius rate very low in the theme, I'm not so fond of its effects, but otherwise it's just great.

---

### Post by Stormbringer on 2006-07-25
Hi, Laterix

Came across your great HOWTO and pimped up my Dapper AMD64.

Although everything worked fine I noticed that your guide causes some minor glitches if 32-Bit applications are running in the 64-Bit OS (non-chrooted) .

But first let me start with two questions ...

**gtk-quit**

Your script as well as your website reads ...

```

# Quit and OK/apply icons
ln -s /usr/share/icons/Tango/scalable/actions/dialog-close.svg /usr/share/icons/Tango/scalable/actions/gtk-quit.png

```

Shouldn't the link target read gtk-quit.svg instead of gtk-quit.png?!? Would make a lot more sense as the source actually *IS* an SVG.


**stock-apply.svg**

Again, your script as well as your website reads...

```

ln -s /usr/share/icons/Tango/scalable/actions/dialog-apply.svg /usr/share/icons/Tango/scalable/actions/stock-apply.svg

```

Shouldn't the link target read stock_apply.svg?!? All of the stock_* feature an underscore instead of an dash.


BTW: I didn't make use of your script --- I made all the steps manually inside an terminal.


**32-Bit apps (i.e. VMware Server, Google Earth Installer, ...) on 64-Bit Dapper**

Although I have all ia32-libs installed VMware Server as well as the installer of Google Earth complain about an missing GTK svg_loader.so on the AMD64 platform (the contents of librsvg/librsvg-common aren't available as an ia32 compatiblity package).

The result is that, i.e., the "Quit" icon doesn't get displayed as the SVG cannot be loaded.

Apart from the symlinks inside the "scalable" directory you should add the following symlinks to make everything work out smoothly...

```

ln -s /usr/share/icons/Tango/24x24/actions/dialog-close.png /usr/share/icons/Tango/24x24/actions/gtk-quit.png
ln -s /usr/share/icons/Tango/24x24/actions/dialog-apply.png /usr/share/icons/Tango/24x24/actions/gtk-ok.png
ln -s /usr/share/icons/Tango/24x24/actions/dialog-apply.png /usr/share/icons/Tango/24x24/actions/gtk-yes.png
ln -s /usr/share/icons/Tango/24x24/actions/dialog-apply.png /usr/share/icons/Tango/24x24/actions/stock-apply.png

ln -s /usr/share/icons/Tango/22x22/actions/dialog-close.png /usr/share/icons/Tango/22x22/actions/gtk-quit.png
ln -s /usr/share/icons/Tango/22x22/actions/dialog-apply.png /usr/share/icons/Tango/22x22/actions/gtk-ok.png
ln -s /usr/share/icons/Tango/22x22/actions/dialog-apply.png /usr/share/icons/Tango/22x22/actions/gtk-yes.png
ln -s /usr/share/icons/Tango/22x22/actions/dialog-apply.png /usr/share/icons/Tango/22x22/actions/stock-apply.png

ln -s /usr/share/icons/Tango/16x16/actions/dialog-close.png /usr/share/icons/Tango/16x16/actions/gtk-quit.png
ln -s /usr/share/icons/Tango/16x16/actions/dialog-apply.png /usr/share/icons/Tango/16x16/actions/gtk-ok.png
ln -s /usr/share/icons/Tango/16x16/actions/dialog-apply.png /usr/share/icons/Tango/16x16/actions/gtk-yes.png
ln -s /usr/share/icons/Tango/16x16/actions/dialog-apply.png /usr/share/icons/Tango/16x16/actions/stock-apply.png

```

The other icons (GAIM, GnomeBaker, ...) doesn't cause any problem as they are PNGs.

Cheers,
Storm

---

### Post by skizz on 2006-07-25
Wow! It's pretty nice! I wonder if... This re-themed Gnome will be included by default in Edgy... It's kinda... VERY **FUTURISTIC** (and clean, though). The font you chose is outstanding. 

I hope we'll see a future releases of this.

Good job,
A.

---

### Post by ptipton on 2006-07-26
This is a great piece of work and looks fabtastic. With the latest versions of the Compiz software everything works fine for me with the exception that the progress bars in Synaptic come up blue instead of orange. Any ideas?

---

### Post by blackdahliamurder on 2006-07-26
Love the new theme! Although I don't use Gnome, I do plan on installing Gnome as soon as I get my wireless card up and running! Although, the only thing I'm not too crazy about is the _ [] X on the top right of the windows. I really don't know what it is, I can't put my finger on it. :\

---

### Post by pjot on 2006-07-31
Hey there!

First of all GREAT icons/theming.

However I can't seem to get rid of the menu in firefox (something you apparently managed to accomplish) so my question to you is: How? :)

---

### Post by Laterix on 2006-08-01
> **pjot said:**
> 
However I can't seem to get rid of the menu in firefox (something you apparently managed to accomplish) so my question to you is: How? :)
You need [**Compact menu extension**]("http://cdn.mozdev.org/compact") for Firefox.

---

### Post by Laterix on 2006-08-01
> **Stormbringer said:**
> 
Your script as well as your website reads ...
```

# Quit and OK/apply icons
ln -s /usr/share/icons/Tango/scalable/actions/dialog-close.svg /usr/share/icons/Tango/scalable/actions/gtk-quit.png

```

Shouldn't the link target read gtk-quit.svg instead of gtk-quit.png?!? Would make a lot more sense as the source actually *IS* an SVG.

Yes, you are right. It's my mistake and because it works, I haven't noticed it before. But yes, it shouldn't change file extension. This applys to all files.

> 
The result is that, i.e., the "Quit" icon doesn't get displayed as the SVG cannot be loaded.

OK, I didn't think this, because I don't have any problems with SVG. But good point.

> 
Apart from the symlinks inside the "scalable" directory you should add the following symlinks to make everything work out smoothly...

Thanks for your tips and corrections!

---

### Post by pjot on 2006-08-03
Hey again, thanks alot for the tip on that extension.

I've modded it a bit to (according to me) fit Ubuntu better. I've made two versions of the extension, but I cannot host it 24/7 so if you like them I was wondering if you would host them for the community? Maybe even as a part of your howto.. ;)

***#*1**
Firefox Logo

[IMG]http://img138.imageshack.us/img138/9214/fflogosr4.png[/IMG]

***#*2**
Ubuntu Logo

[IMG]http://img138.imageshack.us/img138/2927/ublogoyx6.png[/IMG]

I've attached a tar-ball with the two .xpi files (this is because you can't upload .xpi files on the forums). 

**-pjot**

---

### Post by rabside on 2006-08-03
after installing your script some icons (for example for volume icon, system monitor, windows terminal client, ecc) don't change if I change the icon theme.  what can I do to resolve?

thx a lot!

---

### Post by Laterix on 2006-08-04
> **pjot said:**
> 
I've modded it a bit to (according to me) fit Ubuntu better. I've made two versions of the extension, but I cannot host it 24/7 so if you like them I was wondering if you would host them for the community? Maybe even as a part of your howto.. ;)
**-pjot**
Hey, these look good. That default fish icon is not that great. :) I'll add this to my guide. Thanks for your contribution.

I also received a new Orange Compiz theme for latest Theme manager. Compiz Theme manager was updated and old themes doesn't work with the version 0.3x or higher. *Ranno Randmaa* "ported" my orange theme to the new theme manager. Thanks goes to him as well. Theme is available on my site.

---

### Post by Laterix on 2006-08-04
> **rabside said:**
> after installing your script some icons (for example for volume icon, system monitor, windows terminal client, ecc) don't change if I change the icon theme.  what can I do to resolve?

Gnome theme doesn't effect Terminal Server Client. That program uses it's own icons which are in /usr/share/pixmaps/tsclient. Script copied that folder to /usr/share/pixmaps/tsclient_ol_backup. So if you want to remove orange theme you have to delete current **tsclient** folder and then rename **tsclient_ol_backup** to **tsclient**.

Volume icon should change if you change Gnome icon theme. This might require you to restart X or kill gnome-panel.

What is System Monitor? :)

To sum it up. Application themes (firestarter, gnome baker, gaim) etc. Doesn't change if you change your theme. These are not depending on current theme. These applications uses their own image resource files.

---

### Post by Reducer on 2006-08-05
I'm running CGWD Themer 0.37, but I can't get the updated Orange look to install.  When I choose to import a theme, nothing shows up in the dialog box.  What simple yet crucial step am I missing?

Jason

---

### Post by Laterix on 2006-08-05
> **Reducer said:**
> I'm running CGWD Themer 0.37, but I can't get the updated Orange look to install.  When I choose to import a theme, nothing shows up in the dialog box.  What simple yet crucial step am I missing?

Jason
My guess would be that Compiz thememanager is changing so much at the moment. It's almost impossible to keep themes compatible with all versions. Updated theme is not my work and I haven't tested it myself, so I can't say much about that.

---

### Post by mrojas73 on 2006-08-05
> **Laterix said:**
> I will!

Just a small update this time. I made Compiz theme for Orange-look. It doesn't differ that much from the original compiz theme, but I like it because it's simple.

Here is a [preview]("http://users.utu.fi/ljtaim/pics/orange-compiz.png").

[**Download here**]("http://www.taimila.com/downloads/Orange-look.cgwdtheme.tar.gz")

Nice guide, however I can't install the themes with GGWD Themer 0.37

---

### Post by sujit on 2006-08-10
Hey!

A very well made script! It worked like a piece of cake for me, on my Xubuntu installation. Keep up the good work.

Cheers,
Sujit.

---

### Post by BitTorrentBuddha on 2006-08-11
I love this project, orange is one of the most unique things and the looks it gets are incredible. The only problem so far is that there isn't (to my knowledge) a version of the compiz theme compatible with CGWD. Please correct me if I'm wrong.

---

### Post by jpmorelli on 2006-08-12
Thank's a lot for your orange-theme, some options looks really nice in my desktop.
I also make one uninstaller, I'm not a programmer but I rewrote some lines to  move the backup to the original name. But I don't know how to reset the volume icon to the default setting, can you tell me how can i do it?
Thanks !

---

### Post by Laterix on 2006-08-12
> **jmorelli said:**
> Thank's a lot for your orange-theme, some options looks really nice in my desktop.
I also make one uninstaller, I'm not a programmer but I rewrote some lines to  move the backup to the original name. But I don't know how to reset the volume icon to the default setting, can you tell me how can i do it?
Thanks !
Thanks, I think you can remove those volume icons from /usr/share/icons/Human/22x22/status/ to uninstall them.

---

### Post by Laterix on 2006-08-12
Patric T. has made new Orange-look GTK theme and Orange-look GDM theme. Thanks for him! You can download those themes from gnome-look.org

GTK theme (Widgets)
[URL="http://www.gnome-look.org/content/show.php?content=44030"]
[IMG]http://www.gnome-look.org/content/m1/m44030-1.png[/IMG]
[/URL]

GDM theme (Login screen)
[URL="http://www.gnome-look.org/content/show.php?content=44066"]
[IMG]http://www.gnome-look.org/content/m1/m44066-1.png[/IMG]
[/URL]

---

### Post by mrojas73 on 2006-08-13
I have been trying for days to install the orange theme with CGWD without much luck. I just realize that the name extension of the downloaded file has to be changed to .cgwdtheme and it will be work.  you can just click on browse and go to the directory where the file is and it will be seen by cgwd.

My version of CGWD is 0.51.  I hope this helps the noobs like my self.

---

### Post by Kobalt on 2006-08-13
Thank you thank you mrojas73 ! I can enjoy that wonderful theme again ! 
PS : I blogged your trick (but my blog is in french).

---

### Post by desperado666 on 2006-08-16
[http://my.opera.com/community/customize/skins/info/?id=4741](http://my.opera.com/community/customize/skins/info/?id=4741)

Orange Dapper Look (Tango icons) now even for Opera Browser!

---

### Post by rko618 on 2006-08-18
Nice work! I however feel that I prefer the old folder icons.  How can I change them back? I know I have to restore the backups but how?

---

### Post by Laterix on 2006-08-18
> **rko618 said:**
> Nice work! I however feel that I prefer the old folder icons.  How can I change them back? I know I have to restore the backups but how?

Sorry, but I'm in New York at the moment. I will write instruction for you when I return to Finland. Writing this from Apple Store at SoHo. :)

---

### Post by Laterix on 2006-08-25
> **rko618 said:**
> Nice work! I however feel that I prefer the old folder icons.  How can I change them back? I know I have to restore the backups but how?

[Here it is]("http://www.ubuntuforums.org/showpost.php?p=1290580&postcount=123"), in case you didn't find it already.

---

### Post by m.musashi on 2006-08-26
Great theme and nice web site too. One request, however. Is there a higher resolution wallpaper for wide screen monitors? The one I have looks a bit grainy on my laptop.

Thanks.

---

### Post by oyvindaa on 2006-08-26
It's a nice theme, but personally I like an all blue theme with Human Azul icons better. Keep up the good work though :)

---

### Post by Laterix on 2006-08-26
> **oyvindaa said:**
> It's a nice theme, but personally I like an all blue theme with Human Azul icons better. Keep up the good work though :)
No no, blue is eighties ;) Anyway, I updated my Guide and added some links there. Some Compiz and GTK themes. None of them is my work though.

---

### Post by oyvindaa on 2006-08-27
> **Laterix said:**
> No no, blue is eighties ;) Anyway, I updated my Guide and added some links there. Some Compiz and GTK themes. None of them is my work though.

Maybe I'm a bit 'eighties' then ;)

---

### Post by Sircoelho on 2006-12-28
This works on Edgy?

---

### Post by Laterix on 2006-12-29
> **Sircoelho said:**
> This works on Edgy?

Most of the improvements should work just fine. Some of the icon locations seems to be changed though. I wouldn't run the script, but if you follow the guide skip the *Misc icon improvements* or check if there is any differences in Edgy.

To be honest, I haven't tested this on edgy at all.

---

