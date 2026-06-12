---
title: "Guide: Minimal ubuntu installation for computers with no internet connection"
date: 2009-02-28
forum: Philippine Team
---

### Post by bontakunnytpandas on 2009-02-28
OBJECTIVE:

-Minimal ubuntu installation that would fit on an OLD PENTIUM III (933 MHz, 256MB RAM, 4GB HD) w/ no internet connection
-Minimal ubuntu installation using the Gnome Desktop Environment (which i guess the best Desktop Environment that balances speed over functionality)

SETTING:

Installation on an old Pentium III Computer with the following specs and hardware:
PENTIUM III - 933 MHz + Mobo w/ onboard AUDIO/VIDEO & USB Ports
256 MB RAM
4GB HARD DRIVE
CD-RW DRIVE
NO INTERNET CONNECTION AVAILABLE

ACTION PLAN:

PHASE 1: DOWNLOAD!
-Secure a 1 GB (or higher) USB Flash Drive.
-Find a place where you download at high speeds. (e.g. Internet Cafes)
-Download the alternative install cd version (.iso image) of Ubuntu. <[http://ubuntu.mirror.ac.za/ubuntu-release/8.10/ubuntu-8.10-alternate-i386.iso]("http://ubuntu.mirror.ac.za/ubuntu-release/8.10/ubuntu-8.10-alternate-i386.iso")>
-Save this on a Flash Drive for later use.
-Download the Gnome-Core Package at the Ubuntu package repository. <[http://packages.ubuntu.com/intrepid/gnome-core]("http://packages.ubuntu.com/intrepid/gnome-core")>
-Save this on a Flash Drive for later use.

PHASE 2: BURN!
-Back to your own computer.
-Insert your USB Flash Drive.
-Secure a 700MB Blank CD-R.
-Burn the .iso image of Ubuntu on a blank CD-R using your favorite CD Authoring Software.

PHASE 3: INSTALL!
-Set system bios to boot on your CD Drive.
-Boot on the Ubuntu CD that you have burned.
-Select your language. (e.g. english)
-Highlight "Insall Ubuntu", Press F4, select "Install a command line system", press enter.
-Follow installation instructions, if unsure just stick with the default choices. (Note: Default installation will trash your previous operating system)
-Set system bios to boot on your Hard Drive.
-Boot on your new Ubuntu installation.
-You'll be greeted with a command line system, just login and continue.
-Register your Ubuntu CD in APT, type "sudo apt-cdrom add", press enter.
-You'll be asked for your password, just type your password and continue.
-Insert your ubuntu CD, press enter.
-Insert your USB Flash Drive.
-Make a directory for your Flash Drive, type "sudo mkdir /media/disk", press enter.
-Mount your Flash Drive, type "mount /dev/sdb1 /media/disk", press enter.
-Change directory to your Flash Drive, type "cd /media/disk", press enter.
-Install the gnome-core package, type "dpkg -i gnome-core_x.xx.x~xubuntux_all.deb" (Note. x represents version number), press enter.
-This command should produce an error.
-Run aptitude (package manager), type "sudo aptitude", press enter.
-Ignore the error that aptitude reports.
-Press Ctrl+T, Go to Options -> Preferences, press enter.
-Under Dependency Handling, Uncheck "Install recommended packages automatically".
-Press q to close Preferences window.
-Find the gnome-core package, it should be located under the "Obsolete and Locally Created Packages -> gnome -> main".
-Aptitudes reports the gnome-core package as a broken package, to install this package properly, select the gnome-core package and hit the plus sign twice or trice just to be sure.
-Find the following packages and hit the plus sign to install them:
	anacron
	alacarte
	gdm
	gnome-mount
	gnome-media
	gnome-system-monitor
	gnome-system-tools
	gnome-themes
	gnome-utils
	ttf-dejavu-core
	ubuntu-artwork
	xorg
-Now press g to view installation summary, press g again to start installation. (Note: you will be asked for the Ubuntu CD if its not inserted.)
-Wait for the installation to finish, press enter to continue.
-Press q to quit aptitude.
-Reboot by pressing "Ctrl + Alt + Del"
-You'll be greeted by a clean desktop with no useful applications.
-Add new applications through Aptitude.
-Customize your desktop to your liking.
-:)

CONCLUSION:
This setup have produce a minimal ubuntu installation with no useful application installed by default.
Here's a summary of the Memory Resources used on my test machine (COLD BOOT):
Mem Used	80.4
Swap Used	0.0 

What's Next?
-Maybe i'll add a list of applications that i have installed on my minimal ubuntu installation in my next draft.

Comments and suggestions are always welcome!

---

### Post by bontakunnytpandas on 2009-02-28
:ks

---

### Post by killer_d76 on 2009-03-01
thanks for sharing! ;)

---

