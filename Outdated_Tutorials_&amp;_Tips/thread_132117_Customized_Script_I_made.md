---
title: "Customized Script I made"
date: 2006-02-17
forum: Outdated Tutorials &amp; Tips
---

### Post by tbeehler on 2006-02-17
I put together a script that would do something similar to what Automatix and Easy Breezy do, but I added a few more things to the mix.  I added winbind and a nsswitch.conf file so that people could reach LAN computers by hostname.  I have added several themes and a few wallpapers as well.  I have a complete list in the readme file.  Just thought I'd give back to a community that has helped me so much.

Since I don't have a hosted site, the file can be downloaded from here:

[http://www.savefile.com/files/4772226](http://www.savefile.com/files/4772226)

Enjoy!

---

### Post by manicka on 2006-02-18
I think it would be a good idea for you to explain in this thread exactly what this script does to a  users system. From what I can see the user has no control over what the script does (unless they alter the script themselves). 

Users need to be fully aware of what the script will do before downloading it. I know it's in the read me, but an explanation woud be nice here as well.

---

### Post by tbeehler on 2006-02-18
[QUOTE=manicka]I think it would be a good idea for you to explain in this thread exactly what this script does to a  users system. From what I can see the user has no control over what the script does (unless they alter the script themselves). 

Users need to be fully aware of what the script will do before downloading it. I know it's in the read me, but an explanation woud be nice here as well.[/QUOTE]


Good point.  Unless you edit the install file, you do not have any control over what does and does not get installed.  If you do not want something installed, simply remove it from the script.  I apologize for not saying that here.

---

### Post by Wallakoala on 2006-02-18
[QUOTE=tbeehler]Good point.  Unless you edit the install file, you do not have any control over what does and does not get installed.  If you do not want something installed, simply remove it from the script.  I apologize for not saying that here.[/QUOTE]

I'm pretty sure he means that you should say exactly what it does right here...

---

### Post by tbeehler on 2006-02-18
I have posted the script at the bottom of the page so everyone can see.  Hope this clears things up.  Let me know if you guys have any other problems or questions.

From the readme file:  These are the programs that will be installed.

Thunderbird
Winbind
SMBFS
Gftp
dvd ripper
w32codecs
Mplayer with plugins
Firefox with plugins
Wine
Java
VLC
Beep Media Player
Kopete
Ogle
Gnome Splash Screen Manager
Gdesklets
Several Thunderbird Languages
libdvdcss
and more.

Also, My script will make it so that Ctrl-Alt-Del opens up the System Monitor.  I did this for the users who are fresh off of windows.

Finally, My script will create a Backgrounds folder in your Home folder and copy all of the wallpapers to there.  I tried several things to get it to copy to the correct place and have them automatically show up in the Wallpaper Background selector, but I have failed.  :(  If anyone knows of a way, I'd love to hear it.  


Also, here's the script below:

sudo apt-get install winbind smbfs gftp dvdrip w32codecs  mplayer-386 firefox flashplayer-mozilla sun-j2re1.5 azureus wine firestarter acroread acroread-plugins mozilla-acroread kaffeine-mozilla libflash-mozplugin libflash-swfplayer mozilla opensc mozilla-plugin-vlc mozplugger swf-player vlc j2re1.4-mozilla-plugin mozilla-openoffice.org mozilla-mplayer ndisgtk wifi-radar openvpn dcgui gtk-gnutella frostwire beep-media-player beep-media-player-dev beep-media-player-jack beep-media-player-scrobbler ogle ogle-gui gdesklets gdesklets-data gcursor gnome-splashscreen-manager kopete mozilla-thunderbird mozilla-thunderbird-enigmail mozilla-thunderbird-locale-el mozilla-thunderbird-locale-ko mozilla-thunderbird-locale-nb mozilla-thunderbird-locale-pt-br mozilla-thunderbird-locale-tr mozilla-thunderbird-locale-ca mozilla-thunderbird-locale-de mozilla-thunderbird-locale-fr mozilla-thunderbird-locale-it mozilla-thunderbird-locale-nl mozilla-thunderbird-locale-pl mozilla-thunderbird-locale-uk mozilla-thunderbird-offline mozilla-thunderbird-typeaheadfind msttffonts unzip skype gnomebaker streamripper streamtuner vcdimager cdrdao subtitleripper mplayer-fonts libdvdread3 libdvdnav4 libxvidcore4 ndiswrapper-utils

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system -monitor"

sudo cp nsswitch.conf /etc --reply=yes

sudo mkdir /home/$USER/Backgrounds

sudo cp Backgrounds/*.jpg /home/$USER/Backgrounds --reply=yes


#Login Themes
sudo tar -xvf Themes/15783-tux-vs-msbutterfly.tar --directory=/usr/share/gdm/themes/ --overwrite


#Icon Themes
sudo tar -xvf Themes/Icons/Crystalcursors.tar --directory=/usr/share/icons --overwrite
sudo tar -xvf Themes/Icons/d3aicons.tar --directory=/usr/share/icons --overwrite

#Window Themes
sudo tar -xvf Themes/YattaBlues.tar --directory=/home/$USER/.themes/ --overwrite
sudo tar -xvf Themes/SmoothXP.tar --directory=/home/$USER/.themes/ --overwrite
sudo tar -xvf Themes/Smoked_Glass.tar --directory=/home/$USER/.themes/ --overwrite
sudo tar -xvf Themes/emac.tar --directory=/home/$USER/.themes/ --overwrite
sudo tar -xvf Themes/DigitalDark.tar --directory=/home/$USER/.themes/ --overwrite
sudo tar -xvf Themes/darker_theme --directory=/home/$USER/.themes/ --overwrite
sudo tar -xvf Themes/Clearlooks-Clarity.tar --directory=/home/$USER/.themes/ --overwrite
sudo tar -xvf Themes/AquaExtremeSunken.tar --directory=/home/$USER/.themes/ --overwrite
sudo tar -xvf Themes/Alphacube.tar --directory=/home/$USER/.themes/ --overwrite
sudo tar -xvf Themes/18669-Wintah.tar --directory=/home/$USER/.themes/ --overwrite
sudo tar -xvf Themes/Theme/VistaButRounded.tar --directory=/home/$USER/.themes/ --overwrite
sudo tar -xvf Themes/Theme/osx.tar --directory=/home/$USER/.themes/ --overwrite

sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh

---

### Post by benplaut on 2006-02-18
this is a bit random ATM... it's just a collection of program install commands.

give it a bit more work, or, better yet, contribute to Easy Breezy or Automatix

---

### Post by majikstreet on 2006-02-18
what's libdvdcss? what's ogle? what's winbind? explain this stuff more!

also, look around at bash guides on like say the linux documtentation project.. they tell you how to accept user input in bash scripts ;P

---

### Post by tbeehler on 2006-02-18
[QUOTE=majikstreet]what's libdvdcss? what's ogle? what's winbind? explain this stuff more!

also, look around at bash guides on like say the linux documtentation project.. they tell you how to accept user input in bash scripts ;P[/QUOTE]


I agree that it is a very crude script, but I just wanted a quick and dirty way of installing everything I needed and thought I'd share what works for me. :)  For those of you who don't know, libdvdcss is a library needed to play DVD's, Ogle is a DVD player, and winbind: (from the samba website) Is a component of the Samba suite of programs that solves the unified logon problem. Winbind uses a UNIX implementation of Microsoft RPC calls, Pluggable Authentication Modules (PAMs), and the name service switch (NSS) to allow Windows NT domain users to appear and operate as UNIX users on a UNIX machine. It allows you to see use a hostname instead of IP address.

---

