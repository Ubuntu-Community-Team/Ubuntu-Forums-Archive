---
title: "Ubuntu-Desktop-Minimal (Karmic Update)"
date: 2009-12-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Chesamo on 2009-12-09
[[SIZE="6"]This thread has been supplanted by a different one. Please direct your comments there.[/SIZE]](http://ubuntuforums.org/showthread.php?t=1670396)
[http://ubuntuforums.org/showthread.php?t=1670396](http://ubuntuforums.org/showthread.php?t=1670396)

[SIZE="1"]**Scroll down to my next post with a code block; the guide below is obsolete and I am only keeping it here for archive reasons.**
Nevermind, deleted it. It's not even vaguely useful. But still, go to my last post with a code block.[/SIZE]

---

### Post by AlexanderDGreat on 2010-03-16
Amazing! I like you, you are very "AWARE" of newbies like me. I followed your guide up to the end. The only problem is, when you don't have a fast Internet connection, it'll take days to install, is this correct? Thank you for a great tutorial. Let me add to the tutorials I've found:

Ubuntu Forums:
[http://ubuntuforums.org/showthread.php?t=1155961]("http://ubuntuforums.org/showthread.php?t=1155961")

Denny Halim.com
[http://wiki.dennyhalim.com/ubuntu-minimal-desktop]("http://wiki.dennyhalim.com/ubuntu-minimal-desktop")

---

### Post by idczar on 2010-03-18
wow this is awesome can't wait to try out on my macbook!

thank you so much!

---

### Post by JoK3R on 2010-03-18
Hi,

Loving the script, installed it last night and everything works great.

Quick question thou, How can I disable Gnome autostarting? 

Can you have the option in the script to enable or disable Gnome autostart in your next release :)

Thanks!

---

### Post by Chesamo on 2010-03-19
[SIZE="5"]**Also obsoleted, keep going.**[/SIZE]

---

### Post by AlexanderDGreat on 2010-03-20
Can you do something like this if Lucid Lynx releases? Greatly appreciated your time and effort. :)

---

### Post by Chesamo on 2010-03-21
Yes, I plan to update this once Lynx is released. I'm working on one based on the beta but it's... well... beta.

---

### Post by AlexanderDGreat on 2010-03-21
> Yes, I plan to update this once Lynx is released. I'm working on one based on the beta but it's... well... beta. - Thank you very much! :)

---

### Post by AlexanderDGreat on 2010-03-25
Hi! I've done this now in 3 pc's all Intel Atom, and they're working great! I just have to edit the xorg.conf for a 1280x1024 resolution on an Intel video card. Anyway, I've a question.

Can I do minimal-install-Karmic now in my laptop? The reason I'm asking is, I want to do this now in my HP laptop, but I'm thinking that my efforts will be wasted because Lucid Lynx is coming anyway. Also, can I do this and just upgrade from Lucid Lynx without missing anything?

PS I've terrible experience of Upgrading everytime Ubuntu releases a new version. What do you usually do? Thanks.

---

### Post by Chesamo on 2010-03-25
I normally do a fresh install of Ubuntu when a new release comes out since I mount my /home directory as a separate parition. I don't know how well the upgrade for this system will be... I assume it works better than the normal upgrade because there are fewer dependencies to handle. I'll test it once Lucid comes out and get back to you, allright?

---

### Post by AlexanderDGreat on 2010-03-26
> I assume it works better than the normal upgrade because there are fewer dependencies to handle. I'll test it once Lucid comes out and get back to you, allright? - Thanks dude!

---

### Post by Chesamo on 2010-04-30
Okay! What an exciting day. I've updated the script (you can find the latest version on the [Launchpad](https://launchpad.net/ubuntu-desktop-minimal)) and tested out the upgrade. There are a few errors during the upgrade, but I didn't have to do anything to resolve them. Some of the language used is a little uncomfortable. The upgrade from 9.10 went smoothly.

All in all, 10.04g "Zeptobuntu" has a clean bill of health and is ready for release!

I will be updating the guide on my website once the Ubuntu repositories stop pinging out from overuse.

(code removed do to obsolescence)

---

### Post by Chesamo on 2010-05-01
Update: I have updated the installation guide.

***EDIT: See my signature for the link ("Minimal Desktop for Ubuntu"). Click the "Guide" link at the top of the page.***

There seems to be a JavaScript problem that won't make the last few images hide. I haven't been able to figure out what it is.

And can an admin rename this thread? It's no longer just Karmic.

---

### Post by Chesamo on 2010-06-06
Zeptobuntu Update 1 has been released. View the changelog for details.

[SIZE="5"]**Also obsoleted, keep going.**[/SIZE]

---

### Post by Chesamo on 2010-10-22
"Attobuntu" 10.10 for Maverick has been released. It is fully compatible with 10.04, so you should use this script in place of Zeptobuntu.

[http://minimal-desktop.blogspot.com/2010/10/mdu-1010-attobuntu.html](http://minimal-desktop.blogspot.com/2010/10/mdu-1010-attobuntu.html)

[SIZE="5"]**Keep going.**[/SIZE]

---

### Post by Chesamo on 2010-12-06
This update has been out for some time.

10.10.1, "Attobuntu Update 1".

[http://minimal-desktop.blogspot.com/2010/11/attobuntu-update-1.html](http://minimal-desktop.blogspot.com/2010/11/attobuntu-update-1.html)

```
#!/bin/bash
## Minimal Desktop for Ubuntu 10.10.1 "Attobuntu Update 1" by the Minimal Desktop Team
## Version 11.18-2010.10.10.1
## This script is licensed under GPL 3 (http://www.gnu.org/licenses/gpl-3.0.txt)
## http://ubuntu-minimal-desktop.blogspot.com/

if [ $UID -ne 0 ]; then
sudo $0
else

echo -e "Welcome to the Minimal Desktop for Ubuntu install script.\nI will now ask you some questions, to determine what software I should install.\nItems marked with an asterisk (*) are the default options.\nPress ENTER to continue."
read dummy

echo -e "Which desktop environment would you like to install? If you do not know what\nthis means just hit Enter.\n1. GNOME*\n2. KDE\n3. Fluxbox"
read de

if [ "$de" = '2' ]; then

echo -e "Which browser would you like to install?\n1. Rekonq*\n2. Firefox\n3. Chromium\n4. Opera"
read browser

echo -e "Which Instant Messaging client would you like to install?\n1. Kopete*\n2. Konversation\n3. None"
read im

echo -e "Which productivity suite would you like to install?\n1. K Office Suite*\n2. OpenOffice.org\n3. None"
read office

echo -e "Which e-mail client would you like to install?\n1. KMail*\n2. Thunderbird\n3. None"
read email

echo -e "Which media player would you like to install?\n1. Kaffeine*\n2. Amarok\n3. KPlayer\n4. VLC Media Player\n5. None"
read player

echo -e "Do you want to install restricted software, including Flash player\nand Java? [y*|n]"
read restrict
if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
true
elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
echo "Do you want to enable DVD playback support? [y*|n]"
read dvd
if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
true
elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
echo -e "WARNING: This format is restricted in some countries. Are you sure you wish\nto continue? [y*|n]"
read dvd
fi
fi

echo -e "Do you want to install printing support? [y*|n]"
read printing

echo -e "Installation will now begin. Please do not interrupt installation by powering\noff the machine, pressing Ctrl+C, or otherwise killing this process. Press ENTER\nto continue."
read dummy

echo -e "The following software was installed:\nX.org\nKDE\nLinux Sound base system\nk3b" > README

echo "* Preparing the installation..."

if [ "$browser" = '4' ]; then
echo "deb http://deb.opera.com/opera/ stable non-free" >> /etc/apt/sources.list
wget -o /dev/null -O - http://deb.opera.com/archive.key | apt-key add -
echo -e "sleep 5m\nwget -O - http://deb.opera.com/archive.key | apt-key add -\nexit 0" > /etc/rc.local
fi

sed -i -e '/deb cdrom:/d' /etc/apt/sources.list
sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
cp /etc/apt/sources.list /etc/apt/sources.list.backup > /dev/null
uniq /etc/apt/sources.list > temp && mv temp /etc/apt/sources.list
apt-key adv --keyserver keyserver.ubuntu.com --recv 3E5C1192
aptitude update > /dev/null

echo "* Updating the system..."
aptitude -y safe-upgrade > /dev/null

echo "* Installing X.org and the Linux Sound base system..."
aptitude -y install alsa-utils xinit > /dev/null

echo "* Installing KDE and other essentials..."
sudo aptitude -y install kdm kdebase > /dev/null

echo "* Installing some important software..."
sudo aptitude -y install k3b kpackagekit kdeartwork kterm jockey-kde okular > /dev/null
sudo aptitude -yR install kdeutils > /dev/null

if [ "$browser" = '2' ]; then
echo "* Installing Firefox..." && echo "Firefox" >> README
aptitude -y install firefox > /dev/null
elif [ "$browser" = '3' ]; then
echo "* Installing Chromium..." && echo "Chromium" >> README
aptitude -y install chromium-browser > /dev/null
elif [ "$browser" = '4' ]; then
echo "* Installing Opera..." && echo "Opera" >> README
aptitude -y install opera > /dev/null
elif [ -z "$browser" ] || [ "$browser" = '1' ]; then
aptitude -y install rekonq > /dev/null
fi


if [ "$im" = '2' ]; then
echo "* Installing Konversation..." && echo "Konversation" >> README
aptitude -y install konversation > /dev/null
elif [ "$im" = '3' ]; then
true
elif [ -z "$im" ] || [ "$im" = '1' ]; then
echo "* Installing Kopete..." && echo "Kopete" >> README
aptitude -y install kopete > /dev/null
fi


if [ "$office" = '2' ]; then
echo "* Installing OpenOffice.org..." && echo -e "OpenOffice.org Suite:\n Writer\n Calc\n Impress\n Draw\n Base" >> README
aptitude -y install openoffice.org-writer openoffice.org-impress openoffice.org-calc openoffice.org-kde openoffice.org-style-oxygen > /dev/null
elif [ "$office" = '3' ]; then
true
elif [ -z "$office" ] || [ "$office" = '1' ]; then
echo "* Installing K Office Suite..." && echo -e "K Office suite:\n KWord\n KSpread\n KPresenter" >> README
aptitude -y install kword kspread kpresenter > /dev/null
fi

if [ "$email" = '2' ]; then
echo "* Installing Thunderbird..." && echo "Thunderbird" >> README
aptitude -y install thunderbird > /dev/null
elif [ "$email" = '3' ]; then
true
elif [ -z "$email" ] || [ "$email" = '1' ]; then
echo "* Installing KMail..." && echo "KMail" >> README
aptitude -y install kmail > /dev/null
fi

if [ "$player" = '2' ]; then
echo "* Installing Amarok..." && echo "Amarok" >> README
aptitude -y install amarok > /dev/null
elif [ "$player" = '3' ]; then
echo "* Installing KPlayer..." && echo "KPlayer" >> README
aptitude -y install kplayer > /dev/null
elif [ "$player" = '4' ]; then
echo "* Installing VLC Media Player..." && echo "VLC Media Player" >> README
aptitude -y install vlc > /dev/null
elif [ "$player" = '5' ]; then
true
elif [ -z "$player" ] || [ "$player" = '1' ]; then
echo "* Installing Kaffeine..." && echo "Kaffeine" >> README
aptitude -y install kaffeine > /dev/null
fi

if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
true
elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
echo "* Installing restricted extras..." && echo "Kubuntu restricted extras" >> README
aptitude -y install kubuntu-restricted-extras libdvdread4 > /dev/null
if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
true
elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
echo " DVD playback support" >> README
ARCH="$(uname -m |grep 64)"
if [ -z "$ARCH" ]; then
wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
else
wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
fi
dpkg -i libdvdcss2.deb > /dev/null
rm libdvdcss2.deb
fi
fi

if [ "$printing" = 'n' ] || [ "$printing" = 'N' ]; then
true
elif [ -z "$printing" ] || [ "$printing" = 'y' ] || [ "$printing" = 'Y' ]; then
echo "* Instlling the printing subsystem..." && echo "CUPS subsystem" >> README
aptitude -y install cups system-config-printer-kde > /dev/null
fi

echo "* Performing some clean-up..."
aptitude -yf install > /dev/null
aptitude clean > /dev/null

elif [ "$de" = '3' ]; then

echo -e "Minimal Desktop for Fluxbuntu is recommended for experienced Linux users only.\nAre you sure you wish to continue? [y*|n]"
read cont

if [ "$cont" = 'n' ] || [ "$cont" = 'N' ]; then
$0
fi

echo -e "The following software will be installed:\nWeb browser: Arora; IM Client: Ayttm; Text Editor: Nedit\nMedia Player: VLC; Flash and Java support: No\nWould you like to enable DVD playback? [y*|n]"
read dvd

if [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
echo -e "WARNING: This format is restricted in some countries. Are you sure you wish\nto continue? [y*|n]"
read dvd
fi

echo -e "Installation will now begin. Please do not interrupt installation by powering\noff the machine, pressing Ctrl+C, or otherwise killing this process. Press ENTER\nto continue."
read dummy

echo -e "The following software was installed:\nX.org\nFluxbox\nLinux Sound base system\nNedit" > README

echo "* Preparing the installation..."

sed -i -e '/deb cdrom:/d' /etc/apt/sources.list
sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
apt-key adv --keyserver keyserver.ubuntu.com --recv 3E5C1192
aptitude update > /dev/null

echo "* Updating the system..."
aptitude -y safe-upgrade > /dev/null

echo "* Installing X.org and the Linux Sound base system..."
aptitude -y install alsa-utils xinit > /dev/null

echo "* Installing Fluxbox and other essentials..."
aptitude -y install xdm fluxbox eterm > /dev/null

echo "* nstalling Nedit..."
aptitude -y install nedit > /dev/null

echo "* Installing Arora..." && echo "Arora" >> README
aptitude -y install arora > /dev/null

echo "* Installing Ayttm..." && echo "Ayttm" >> README
aptitude -y install ayttm > /dev/null

echo "* Installing VLC Media Player..." && echo "VLC Media Player" >> README
aptitude -y install vlc > /dev/null

if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
true
elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
echo " DVD playback support" >> README
ARCH="$(uname -m |grep 64)"
if [ -z "$ARCH" ]; then
wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
else
wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
fi
dpkg -i libdvdcss2.deb > /dev/null
rm libdvdcss2.deb
fi

echo "* Performing some clean-up..."
aptitude -yf install > /dev/null
aptitude clean > /dev/null

elif [ -z "$de" ] || [ "$de" = '1' ]; then

echo -e "Which browser would you like to install?\n1. Firefox*\n2. Epiphany\n3. Chromium\n4. Opera"
read browser

echo -e "Which Instant Messaging client would you like to install?\n1. Pidgin*\n2. Empathy IM\n3. None"
read im

echo -e "Which productivity suite would you like to install?\n1. GNOME Office Suite*\n2. OpenOffice.org\n3. None"
read office

echo -e "Which e-mail client would you like to install?\n1. Evolution*\n2. Thunderbird\n3. None"
read email

echo -e "Which media player would you like to install?\n1. Rhythmbox*\n2. Totem\n3. Banshee\n4. VLC Media Player\n5. None"
read player

echo -e "Which network connection tool would you like to install?\n1. GNOME Network Manager*\n2. Wicd\n3. None"
read wireless

echo -e "Do you want to install restricted software, including Flash player\nand Java? [y*|n]"
read restrict
if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
true
elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
echo "Do you want to enable DVD playback support? [y*|n]"
read dvd
if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
true
elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
echo -e "WARNING: This format is restricted in some countries. Are you sure you wish\nto continue? [y*|n]"
read dvd
fi
fi

echo -e "Do you want to install printing support? [y*|n]"
read printing

echo "Would you like to install some extra Ubuntu artwork and themes? [y*|n]"
read theme

echo -e "Installation will now begin. Please do not interrupt installation by powering\noff the machine, pressing Ctrl+C, or otherwise killing this process. Press ENTER\nto continue."
read dummy

echo -e "The following software was installed:\nX.org\nGNOME\nLinux Sound base system\nBrasero" > README

echo "* Preparing the installation..."

if [ "$browser" = '4' ]; then
echo "deb http://deb.opera.com/opera/ stable non-free" >> /etc/apt/sources.list
wget -o /dev/null -O - http://deb.opera.com/archive.key | apt-key add -
echo -e "sleep 5m\nwget -O - http://deb.opera.com/archive.key | apt-key add -\nexit 0" > /etc/rc.local
fi

sed -i -e '/deb cdrom:/d' /etc/apt/sources.list
sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
apt-key adv --keyserver keyserver.ubuntu.com --recv 3E5C1192
aptitude update > /dev/null

echo "* Updating the system..."
aptitude -y safe-upgrade > /dev/null

echo "* Installing X.org and the Linux Sound base system..."
aptitude -y install alsa-utils xinit > /dev/null

echo "* Installing GNOME and other essentials..."
aptitude -y install gdm gnome-core gnome-themes-selected gnome-themes-ubuntu light-themes indicator-applet-session > /dev/null

if [ "$wireless" = '2' ]; then
echo "Wicd" >> README
aptitude -y install wicd > /dev/null
elif [ "$wireless" = '3' ]; then
true
elif [ -z "$wireless" ] || [ "$wireless" = '1' ]; then
echo "GNOME Network Manager" >> README
aptitude -y install network-manager-gnome > /dev/null
fi

echo "* Installing some important software..."
aptitude -y install brasero file-roller gcalctool gdebi gnome-screensaver gnome-utils jockey-gtk update-manager evince > /dev/null

if [ "$browser" = '2' ]; then
echo "* Installing Epiphany..." && echo "Epiphany" >> README
aptitude -y install epiphany-browser > /dev/null
elif [ "$browser" = '3' ]; then
echo "* Installing Chromium..." && echo "Chromium" >> README
aptitude -y install chromium-browser > /dev/null
elif [ "$browser" = '4' ]; then
echo "* Installing Opera..." && echo "Opera" >> README
aptitude -y install opera > /dev/null
elif [ "$browser" = '5' ]; then
true
elif [ -z "$browser" ] || [ "$browser" = '1' ]; then
echo "* Installing Firefox..." && echo "Firefox" >> README
aptitude -y install firefox > /dev/null
fi


if [ "$im" = '2' ]; then
echo "* Installing Empathy IM..." && echo "Empathy IM" >> README
aptitude -y install empathy > /dev/null
elif [ "$im" = '3' ]; then
true
elif [ -z "$im" ] || [ "$im" = '1' ]; then
echo "* Installing Pidgin..." && echo "Pidgin" >> README
aptitude -y install pidgin > /dev/null
fi


if [ "$office" = '2' ]; then
echo "* Installing OpenOffice.org..." && echo -e "OpenOffice.org Suite:\n Writer\n Calc\n Impress\n Draw\n Base" >> README
aptitude -y install openoffice.org-writer openoffice.org-impress openoffice.org-calc openoffice.org-gtk openoffice.org-style-tango > /dev/null
elif [ "$office" = '3' ]; then
true
elif [ -z "$office" ] || [ "$office" = '1' ]; then
echo "* Installing GNOME Office Suite..." && echo -e "GNOME Office suite:\n Abiword\n Gnumeric" >> README
aptitude -y install abiword gnumeric > /dev/null
fi


if [ "$email" = '2' ]; then
echo "* Installing Thunderbird..." && echo "Thunderbird" >> README
aptitude -y install thunderbird > /dev/null
elif [ "$email" = '3' ]; then
true
elif [ -z "$email" ] || [ "$email" = '1' ]; then
echo "* Installing Evolution..." && echo "Evolution" >> README
aptitude -y install evolution > /dev/null
fi

if [ "$player" = '2' ]; then
echo "* Installing Totem..." && echo "Totem" >> README
aptitude -y install totem-gstreamer > /dev/null
elif [ "$player" = '3' ]; then
echo "* Installing Banshee..." && echo "Banshee" >> README
aptitude -y install banshee > /dev/null
elif [ "$player" = '4' ]; then
echo "* Installing VLC Media Player..." && echo "VLC Media Player" >> README
aptitude -y install vlc > /dev/null
elif [ "$player" = '5' ]; then
true
elif [ -z "$player" ] || [ "$player" = '1' ]; then
echo "* Installing Rhythmbox..." && echo "Rhythmbox" >> README
aptitude -y install rhythmbox > /dev/null
fi

if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
true
elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
echo "* Installing restricted extras..." && echo "Ubuntu restricted extras" >> README
aptitude -y install ubuntu-restricted-extras > /dev/null
if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
true
elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
echo " DVD playback support" >> README
ARCH="$(uname -m |grep 64)"
if [ -z "$ARCH" ]; then
wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
else
wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
fi
dpkg -i libdvdcss2.deb > /dev/null
rm libdvdcss2.deb
fi
fi

if [ "$printing" = 'n' ] || [ "$printing" = 'N' ]; then
true
elif [ -z "$printing" ] || [ "$printing" = 'y' ] || [ "$printing" = 'Y' ]; then
echo "* Instlling the printing subsystem..." && echo "CUPS subsystem" >> README
aptitude -y install cups system-config-printer-gnome > /dev/null
fi

if [ "$theme" = 'n' ] || [ "$theme" = 'N' ]; then
true
elif [ -z "$theme" ] || [ "$theme" = 'y' ] || [ "$theme" = 'Y' ]; then
echo "* Instlling extra themes..." && echo "Extra GNOME themes" >> README
aptitude -y install gnome-themes gnome-themes-extras gnome-theme-gilouche ubuntu-artwork > /dev/null
fi

echo "* Performing some clean-up..."
aptitude -y -f install > /dev/null
aptitude clean > /dev/null

fi

chmod a+rw README

echo -e "\nIf there are any problems with this script, please send an email to:\nminimal-desktop-drivers@lists.launchpad.net\n\nIf you believe this script contains bugs, please report them in our Launchpad page:\nhttps://edge.launchpad.net/minimal-desktop-for-ubuntu\n\nThanks for using this script!" >> README

echo -e "Congratulations! Minimal Desktop for Ubuntu has been installed. Please read\nthe README generated by this script, located in your home folder. It contains\nsome very important information.\n\nA reboot is required to use your new system.\nWould you like to reboot now? [y*|n]"
read reboot

if [ "$reboot" = 'n' ] || [ "$reboot" = 'N' ]; then
true
elif [ -z "$reboot"] || [ "$reboot" = 'y' ] || [ "$reboot" = 'Y' ]; then
reboot
fi

fi

exit 0
```

---

### Post by senor_smile on 2010-12-07
> **Chesamo said:**
> This update has been out for some time.

10.10.1, "Attobuntu Update 1".

[http://minimal-desktop.blogspot.com/2010/11/attobuntu-update-1.html](http://minimal-desktop.blogspot.com/2010/11/attobuntu-update-1.html)

```
#!/bin/bash
## Minimal Desktop for Ubuntu 10.10.1 "Attobuntu Update 1" by the Minimal Desktop Team
## Version 11.18-2010.10.10.1
## This script is licensed under GPL 3 (http://www.gnu.org/licenses/gpl-3.0.txt)
## http://ubuntu-minimal-desktop.blogspot.com/

if [ $UID -ne 0 ]; then
sudo $0
else

echo -e "Welcome to the Minimal Desktop for Ubuntu install script.\nI will now ask you some questions, to determine what software I should install.\nItems marked with an asterisk (*) are the default options.\nPress ENTER to continue."
read dummy

echo -e "Which desktop environment would you like to install? If you do not know what\nthis means just hit Enter.\n1. GNOME*\n2. KDE\n3. Fluxbox"
read de

if [ "$de" = '2' ]; then

echo -e "Which browser would you like to install?\n1. Rekonq*\n2. Firefox\n3. Chromium\n4. Opera"
read browser

echo -e "Which Instant Messaging client would you like to install?\n1. Kopete*\n2. Konversation\n3. None"
read im

echo -e "Which productivity suite would you like to install?\n1. K Office Suite*\n2. OpenOffice.org\n3. None"
read office

echo -e "Which e-mail client would you like to install?\n1. KMail*\n2. Thunderbird\n3. None"
read email

echo -e "Which media player would you like to install?\n1. Kaffeine*\n2. Amarok\n3. KPlayer\n4. VLC Media Player\n5. None"
read player

echo -e "Do you want to install restricted software, including Flash player\nand Java? [y*|n]"
read restrict
if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
true
elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
echo "Do you want to enable DVD playback support? [y*|n]"
read dvd
if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
true
elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
echo -e "WARNING: This format is restricted in some countries. Are you sure you wish\nto continue? [y*|n]"
read dvd
fi
fi

echo -e "Do you want to install printing support? [y*|n]"
read printing

echo -e "Installation will now begin. Please do not interrupt installation by powering\noff the machine, pressing Ctrl+C, or otherwise killing this process. Press ENTER\nto continue."
read dummy

echo -e "The following software was installed:\nX.org\nKDE\nLinux Sound base system\nk3b" > README

echo "* Preparing the installation..."

if [ "$browser" = '4' ]; then
echo "deb http://deb.opera.com/opera/ stable non-free" >> /etc/apt/sources.list
wget -o /dev/null -O - http://deb.opera.com/archive.key | apt-key add -
echo -e "sleep 5m\nwget -O - http://deb.opera.com/archive.key | apt-key add -\nexit 0" > /etc/rc.local
fi

sed -i -e '/deb cdrom:/d' /etc/apt/sources.list
sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
cp /etc/apt/sources.list /etc/apt/sources.list.backup > /dev/null
uniq /etc/apt/sources.list > temp && mv temp /etc/apt/sources.list
apt-key adv --keyserver keyserver.ubuntu.com --recv 3E5C1192
aptitude update > /dev/null

echo "* Updating the system..."
aptitude -y safe-upgrade > /dev/null

echo "* Installing X.org and the Linux Sound base system..."
aptitude -y install alsa-utils xinit > /dev/null

echo "* Installing KDE and other essentials..."
sudo aptitude -y install kdm kdebase > /dev/null

echo "* Installing some important software..."
sudo aptitude -y install k3b kpackagekit kdeartwork kterm jockey-kde okular > /dev/null
sudo aptitude -yR install kdeutils > /dev/null

if [ "$browser" = '2' ]; then
echo "* Installing Firefox..." && echo "Firefox" >> README
aptitude -y install firefox > /dev/null
elif [ "$browser" = '3' ]; then
echo "* Installing Chromium..." && echo "Chromium" >> README
aptitude -y install chromium-browser > /dev/null
elif [ "$browser" = '4' ]; then
echo "* Installing Opera..." && echo "Opera" >> README
aptitude -y install opera > /dev/null
elif [ -z "$browser" ] || [ "$browser" = '1' ]; then
aptitude -y install rekonq > /dev/null
fi


if [ "$im" = '2' ]; then
echo "* Installing Konversation..." && echo "Konversation" >> README
aptitude -y install konversation > /dev/null
elif [ "$im" = '3' ]; then
true
elif [ -z "$im" ] || [ "$im" = '1' ]; then
echo "* Installing Kopete..." && echo "Kopete" >> README
aptitude -y install kopete > /dev/null
fi


if [ "$office" = '2' ]; then
echo "* Installing OpenOffice.org..." && echo -e "OpenOffice.org Suite:\n Writer\n Calc\n Impress\n Draw\n Base" >> README
aptitude -y install openoffice.org-writer openoffice.org-impress openoffice.org-calc openoffice.org-kde openoffice.org-style-oxygen > /dev/null
elif [ "$office" = '3' ]; then
true
elif [ -z "$office" ] || [ "$office" = '1' ]; then
echo "* Installing K Office Suite..." && echo -e "K Office suite:\n KWord\n KSpread\n KPresenter" >> README
aptitude -y install kword kspread kpresenter > /dev/null
fi

if [ "$email" = '2' ]; then
echo "* Installing Thunderbird..." && echo "Thunderbird" >> README
aptitude -y install thunderbird > /dev/null
elif [ "$email" = '3' ]; then
true
elif [ -z "$email" ] || [ "$email" = '1' ]; then
echo "* Installing KMail..." && echo "KMail" >> README
aptitude -y install kmail > /dev/null
fi

if [ "$player" = '2' ]; then
echo "* Installing Amarok..." && echo "Amarok" >> README
aptitude -y install amarok > /dev/null
elif [ "$player" = '3' ]; then
echo "* Installing KPlayer..." && echo "KPlayer" >> README
aptitude -y install kplayer > /dev/null
elif [ "$player" = '4' ]; then
echo "* Installing VLC Media Player..." && echo "VLC Media Player" >> README
aptitude -y install vlc > /dev/null
elif [ "$player" = '5' ]; then
true
elif [ -z "$player" ] || [ "$player" = '1' ]; then
echo "* Installing Kaffeine..." && echo "Kaffeine" >> README
aptitude -y install kaffeine > /dev/null
fi

if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
true
elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
echo "* Installing restricted extras..." && echo "Kubuntu restricted extras" >> README
aptitude -y install kubuntu-restricted-extras libdvdread4 > /dev/null
if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
true
elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
echo " DVD playback support" >> README
ARCH="$(uname -m |grep 64)"
if [ -z "$ARCH" ]; then
wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
else
wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
fi
dpkg -i libdvdcss2.deb > /dev/null
rm libdvdcss2.deb
fi
fi

if [ "$printing" = 'n' ] || [ "$printing" = 'N' ]; then
true
elif [ -z "$printing" ] || [ "$printing" = 'y' ] || [ "$printing" = 'Y' ]; then
echo "* Instlling the printing subsystem..." && echo "CUPS subsystem" >> README
aptitude -y install cups system-config-printer-kde > /dev/null
fi

echo "* Performing some clean-up..."
aptitude -yf install > /dev/null
aptitude clean > /dev/null

elif [ "$de" = '3' ]; then

echo -e "Minimal Desktop for Fluxbuntu is recommended for experienced Linux users only.\nAre you sure you wish to continue? [y*|n]"
read cont

if [ "$cont" = 'n' ] || [ "$cont" = 'N' ]; then
$0
fi

echo -e "The following software will be installed:\nWeb browser: Arora; IM Client: Ayttm; Text Editor: Nedit\nMedia Player: VLC; Flash and Java support: No\nWould you like to enable DVD playback? [y*|n]"
read dvd

if [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
echo -e "WARNING: This format is restricted in some countries. Are you sure you wish\nto continue? [y*|n]"
read dvd
fi

echo -e "Installation will now begin. Please do not interrupt installation by powering\noff the machine, pressing Ctrl+C, or otherwise killing this process. Press ENTER\nto continue."
read dummy

echo -e "The following software was installed:\nX.org\nFluxbox\nLinux Sound base system\nNedit" > README

echo "* Preparing the installation..."

sed -i -e '/deb cdrom:/d' /etc/apt/sources.list
sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
apt-key adv --keyserver keyserver.ubuntu.com --recv 3E5C1192
aptitude update > /dev/null

echo "* Updating the system..."
aptitude -y safe-upgrade > /dev/null

echo "* Installing X.org and the Linux Sound base system..."
aptitude -y install alsa-utils xinit > /dev/null

echo "* Installing Fluxbox and other essentials..."
aptitude -y install xdm fluxbox eterm > /dev/null

echo "* nstalling Nedit..."
aptitude -y install nedit > /dev/null

echo "* Installing Arora..." && echo "Arora" >> README
aptitude -y install arora > /dev/null

echo "* Installing Ayttm..." && echo "Ayttm" >> README
aptitude -y install ayttm > /dev/null

echo "* Installing VLC Media Player..." && echo "VLC Media Player" >> README
aptitude -y install vlc > /dev/null

if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
true
elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
echo " DVD playback support" >> README
ARCH="$(uname -m |grep 64)"
if [ -z "$ARCH" ]; then
wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
else
wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
fi
dpkg -i libdvdcss2.deb > /dev/null
rm libdvdcss2.deb
fi

echo "* Performing some clean-up..."
aptitude -yf install > /dev/null
aptitude clean > /dev/null

elif [ -z "$de" ] || [ "$de" = '1' ]; then

echo -e "Which browser would you like to install?\n1. Firefox*\n2. Epiphany\n3. Chromium\n4. Opera"
read browser

echo -e "Which Instant Messaging client would you like to install?\n1. Pidgin*\n2. Empathy IM\n3. None"
read im

echo -e "Which productivity suite would you like to install?\n1. GNOME Office Suite*\n2. OpenOffice.org\n3. None"
read office

echo -e "Which e-mail client would you like to install?\n1. Evolution*\n2. Thunderbird\n3. None"
read email

echo -e "Which media player would you like to install?\n1. Rhythmbox*\n2. Totem\n3. Banshee\n4. VLC Media Player\n5. None"
read player

echo -e "Which network connection tool would you like to install?\n1. GNOME Network Manager*\n2. Wicd\n3. None"
read wireless

echo -e "Do you want to install restricted software, including Flash player\nand Java? [y*|n]"
read restrict
if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
true
elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
echo "Do you want to enable DVD playback support? [y*|n]"
read dvd
if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
true
elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
echo -e "WARNING: This format is restricted in some countries. Are you sure you wish\nto continue? [y*|n]"
read dvd
fi
fi

echo -e "Do you want to install printing support? [y*|n]"
read printing

echo "Would you like to install some extra Ubuntu artwork and themes? [y*|n]"
read theme

echo -e "Installation will now begin. Please do not interrupt installation by powering\noff the machine, pressing Ctrl+C, or otherwise killing this process. Press ENTER\nto continue."
read dummy

echo -e "The following software was installed:\nX.org\nGNOME\nLinux Sound base system\nBrasero" > README

echo "* Preparing the installation..."

if [ "$browser" = '4' ]; then
echo "deb http://deb.opera.com/opera/ stable non-free" >> /etc/apt/sources.list
wget -o /dev/null -O - http://deb.opera.com/archive.key | apt-key add -
echo -e "sleep 5m\nwget -O - http://deb.opera.com/archive.key | apt-key add -\nexit 0" > /etc/rc.local
fi

sed -i -e '/deb cdrom:/d' /etc/apt/sources.list
sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
apt-key adv --keyserver keyserver.ubuntu.com --recv 3E5C1192
aptitude update > /dev/null

echo "* Updating the system..."
aptitude -y safe-upgrade > /dev/null

echo "* Installing X.org and the Linux Sound base system..."
aptitude -y install alsa-utils xinit > /dev/null

echo "* Installing GNOME and other essentials..."
aptitude -y install gdm gnome-core gnome-themes-selected gnome-themes-ubuntu light-themes indicator-applet-session > /dev/null

if [ "$wireless" = '2' ]; then
echo "Wicd" >> README
aptitude -y install wicd > /dev/null
elif [ "$wireless" = '3' ]; then
true
elif [ -z "$wireless" ] || [ "$wireless" = '1' ]; then
echo "GNOME Network Manager" >> README
aptitude -y install network-manager-gnome > /dev/null
fi

echo "* Installing some important software..."
aptitude -y install brasero file-roller gcalctool gdebi gnome-screensaver gnome-utils jockey-gtk update-manager evince > /dev/null

if [ "$browser" = '2' ]; then
echo "* Installing Epiphany..." && echo "Epiphany" >> README
aptitude -y install epiphany-browser > /dev/null
elif [ "$browser" = '3' ]; then
echo "* Installing Chromium..." && echo "Chromium" >> README
aptitude -y install chromium-browser > /dev/null
elif [ "$browser" = '4' ]; then
echo "* Installing Opera..." && echo "Opera" >> README
aptitude -y install opera > /dev/null
elif [ "$browser" = '5' ]; then
true
elif [ -z "$browser" ] || [ "$browser" = '1' ]; then
echo "* Installing Firefox..." && echo "Firefox" >> README
aptitude -y install firefox > /dev/null
fi


if [ "$im" = '2' ]; then
echo "* Installing Empathy IM..." && echo "Empathy IM" >> README
aptitude -y install empathy > /dev/null
elif [ "$im" = '3' ]; then
true
elif [ -z "$im" ] || [ "$im" = '1' ]; then
echo "* Installing Pidgin..." && echo "Pidgin" >> README
aptitude -y install pidgin > /dev/null
fi


if [ "$office" = '2' ]; then
echo "* Installing OpenOffice.org..." && echo -e "OpenOffice.org Suite:\n Writer\n Calc\n Impress\n Draw\n Base" >> README
aptitude -y install openoffice.org-writer openoffice.org-impress openoffice.org-calc openoffice.org-gtk openoffice.org-style-tango > /dev/null
elif [ "$office" = '3' ]; then
true
elif [ -z "$office" ] || [ "$office" = '1' ]; then
echo "* Installing GNOME Office Suite..." && echo -e "GNOME Office suite:\n Abiword\n Gnumeric" >> README
aptitude -y install abiword gnumeric > /dev/null
fi


if [ "$email" = '2' ]; then
echo "* Installing Thunderbird..." && echo "Thunderbird" >> README
aptitude -y install thunderbird > /dev/null
elif [ "$email" = '3' ]; then
true
elif [ -z "$email" ] || [ "$email" = '1' ]; then
echo "* Installing Evolution..." && echo "Evolution" >> README
aptitude -y install evolution > /dev/null
fi

if [ "$player" = '2' ]; then
echo "* Installing Totem..." && echo "Totem" >> README
aptitude -y install totem-gstreamer > /dev/null
elif [ "$player" = '3' ]; then
echo "* Installing Banshee..." && echo "Banshee" >> README
aptitude -y install banshee > /dev/null
elif [ "$player" = '4' ]; then
echo "* Installing VLC Media Player..." && echo "VLC Media Player" >> README
aptitude -y install vlc > /dev/null
elif [ "$player" = '5' ]; then
true
elif [ -z "$player" ] || [ "$player" = '1' ]; then
echo "* Installing Rhythmbox..." && echo "Rhythmbox" >> README
aptitude -y install rhythmbox > /dev/null
fi

if [ "$restrict" = 'n' ] || [ "$restrict" = 'N' ]; then
true
elif [ -z "$restrict" ] || [ "$restrict" = 'y' ] || [ "$restrict" = 'Y' ]; then
echo "* Installing restricted extras..." && echo "Ubuntu restricted extras" >> README
aptitude -y install ubuntu-restricted-extras > /dev/null
if [ "$dvd" = 'n' ] || [ "$dvd" = 'N' ]; then
true
elif [ -z "$dvd" ] || [ "$dvd" = 'y' ] || [ "$dvd" = 'Y' ]; then
echo " DVD playback support" >> README
ARCH="$(uname -m |grep 64)"
if [ -z "$ARCH" ]; then
wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
else
wget -o /dev/null -O libdvdcss2.deb http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
fi
dpkg -i libdvdcss2.deb > /dev/null
rm libdvdcss2.deb
fi
fi

if [ "$printing" = 'n' ] || [ "$printing" = 'N' ]; then
true
elif [ -z "$printing" ] || [ "$printing" = 'y' ] || [ "$printing" = 'Y' ]; then
echo "* Instlling the printing subsystem..." && echo "CUPS subsystem" >> README
aptitude -y install cups system-config-printer-gnome > /dev/null
fi

if [ "$theme" = 'n' ] || [ "$theme" = 'N' ]; then
true
elif [ -z "$theme" ] || [ "$theme" = 'y' ] || [ "$theme" = 'Y' ]; then
echo "* Instlling extra themes..." && echo "Extra GNOME themes" >> README
aptitude -y install gnome-themes gnome-themes-extras gnome-theme-gilouche ubuntu-artwork > /dev/null
fi

echo "* Performing some clean-up..."
aptitude -y -f install > /dev/null
aptitude clean > /dev/null

fi

chmod a+rw README

echo -e "\nIf there are any problems with this script, please send an email to:\nminimal-desktop-drivers@lists.launchpad.net\n\nIf you believe this script contains bugs, please report them in our Launchpad page:\nhttps://edge.launchpad.net/minimal-desktop-for-ubuntu\n\nThanks for using this script!" >> README

echo -e "Congratulations! Minimal Desktop for Ubuntu has been installed. Please read\nthe README generated by this script, located in your home folder. It contains\nsome very important information.\n\nA reboot is required to use your new system.\nWould you like to reboot now? [y*|n]"
read reboot

if [ "$reboot" = 'n' ] || [ "$reboot" = 'N' ]; then
true
elif [ -z "$reboot"] || [ "$reboot" = 'y' ] || [ "$reboot" = 'Y' ]; then
reboot
fi

fi

exit 0
```

Thanks!  I just discovered this script after having maintained my own version that wasn't nearly as efficient or complete.  I can't wait to try this own out on my next minimal desktop or server install that needs a gui.

---

### Post by Chesamo on 2011-02-02
[[SIZE="6"]This thread has been supplanted by a different one. Please direct your comments there.[/SIZE]](http://ubuntuforums.org/showthread.php?t=1670396)
[http://ubuntuforums.org/showthread.php?t=1670396](http://ubuntuforums.org/showthread.php?t=1670396)

---

