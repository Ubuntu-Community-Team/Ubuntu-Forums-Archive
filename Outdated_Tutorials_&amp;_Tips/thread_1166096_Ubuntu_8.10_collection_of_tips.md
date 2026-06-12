---
title: "Ubuntu 8.10 collection of tips"
date: 2009-05-21
forum: Outdated Tutorials &amp; Tips
---

### Post by bkbilly on 2009-05-21
**[COLOR="Green"]How to install Ubuntu Manually[/COLOR]**
To install manually Ubuntu you will need to create a new partition and select it to be “swap”. It will be about 256MB
Then create an other which will be “ext3” and in the mount point put “/”. this partition will be about 2GB

[COLOR="Green"]**Auto mount NTFS partition**[/COLOR]
```
sudo mkdir /media/windows
sudo gedit /etc/fstab
```
put this line in the end of the text (here is an example):
> /dev/sda1		/media/windows		ntfs-3g 	defaults,locale=en_US.UTF-8 		0 0
[COLOR="Purple"]In the first bullet you can put any name you want in the place of “Windows” but it has to be the same with the one in the las bullet
The letter of the partition can be found in the program “Partition Editor”[/COLOR]

**[COLOR="Green"]Fix time change on ubuntu-windows switch[/COLOR]**
```
sudo gedit /etc/default/rcS
```
> change the UTC from yes to no

**[COLOR="Green"]Install a 32bit deb package to a 64bit PC[/COLOR]**
```
sudo dpkg --force-architecture -i the_package.deb
```
		or
```
sudo dpkg --force-all -i the_package.deb
```

**[COLOR="Green"]Support RAR files[/COLOR]**
```
sudo apt-get install unrar
```

**[COLOR="Green"]Create RAR files and split them[/COLOR]**
```
sudo apt-get install rar
```
find the file you want and do the following: “Right click &#8594; Create Archive &#8594; select a name &#8594; select .rar &#8594; open the Other Options &#8594; tick the Split in volumes of and select the size”

**[COLOR="Green"]Communicate with Windows on LAN (install Samba)[/COLOR]**
```
sudo apt-get install samba
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
sudo /etc/init.d/samba restart
sudo smbpasswd -L -a bkbilly
```
when it asks for username press enter
```
sudo smbpasswd -L -e bkbilly
sudo gedit /etc/samba/smb.conf
```
Put this line to the [global] section
> usershare owner only = False
```
sudo /etc/init.d/samba restart
```

**[COLOR="Green"]Make linux look like MacOS[/COLOR]**
[COLOR="Red"]install visual effects[/COLOR]
Go to System &#8594; Preferences &#8594; Appearance &#8594; theme and click Install
Open “Ubuntu Themes” from my directory and install everything inside
Select a theme and then press “Customize” find the tabs “Controls, Window Border, Icons and Pointer” and select what you like
[COLOR="Red"]change window buttons place[/COLOR]
Press Alt+F2 and type “gconf-editor” and navigate to “apps &#8594; metacity &#8594; general”
On the right double click “button_layout” and replace with “close,maximize,minimize:menu”
To reverse it write “menu:minimize,maximize,close”
[COLOR="Red"]install Avant Window Navigator[/COLOR]
```
sudo apt-get install avant-window-navigator
```
Once you open AWN from “Applications &#8594; Accessories &#8594; Avant window Navigator” right click on dock and press “Dock Preferences”
Go to “Themes” and press “Add”
find the “AWN Dock Theme” and install that and press Apply

**[COLOR="Green"]Create keyboard shortcuts for programs[/COLOR]**
[COLOR="Red"]Ctr+Alt+Delete[/COLOR]
Go to “Keyboard Shortcuts” and find “Logout” and delete this shortcut
Press Alt+F2 and type “gconf-editor” and navigate to “apps &#8594; metacity”
Select "Global_keybindings" and search for a "run_command_X" value where X is between 1 and 12 and it is not used (i have used run_command_1)
Add this value: > <Control><Alt>Delete
Now select "Keybindings_commands" on left tree. Goto "command_X" where X is the same number selected in run_command_X option
Add this value: > gnome-system-monitor (For me is command_1)

**[COLOR="Green"]Roll-Up windows[/COLOR]**
Press Alt+F2 and type “gconf-editor” and navigate to “apps &#8594; metacity &#8594; general”
On the right double click “action_middle_click_titlebar” and replace with > toggle_shade
The default is “lower”

**[COLOR="Green"]MSN Messenger (emesene)[/COLOR]**
The plugins that you need are LibNotify, Logger, Personal Message, Screenshot, Sound, StatusHistory, Tiny URL, Youtube
[COLOR="Red"]Install Plugins[/COLOR]
download from here: http://www.emesene.org/trac/wiki/Plugins and copy the plugins you want to: > ~/.config/emesene1.0/pluginsEmesene/
[COLOR="Red"]Install fonts:[/COLOR]
```
sudo nautilus /usr/share/fonts/type1/gsfonts
```
and copy the fonts you want there
[COLOR="Red"]start it minimized[/COLOR]
> emesene -m
[COLOR="Red"]backup settings[/COLOR]
copy the directory > ~/.config/emesene1.0

**[COLOR="Green"]Dual Monitor (TwinView)[/COLOR]**
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```
find the Section “Device” and replace it with this:
> Section "Device" 
	Identifier	"TwinView" 
	Driver		"nvidia" 
	Option		"TwinView" 
	Option		"NoLogo"		"True" 
	Option		"TwinViewOrientation"	"RightOf"  
	Option		"UseEdidFreqs"		"True" 
	Option		"MetaModes"		"1360x768,1360x768; 1360x768,NULL; NULL,1360x768" 
EndSection

To change MetaMode press “Ctrl+Alt++”

**[COLOR="Green"]Manage Desktop effects[/COLOR]**
```
sudo apt-get install compizconfig-settings-manager
```
To see it go to system &#8594; preferences &#8594; “Advanced Desktop Effects Settings”

**[COLOR="Green"]Terminal tips[/COLOR]**
To install multiple programs together type sudo apt-get install program1 program2 program3
If you don't want to type sudo for having root access just type sudo bash. To have normal access type exit
To have graphical root access to folders type sudo nautilus /path/path
Go to a directory that it has space ie: “ubuntu linux” type: cd /the/directory/you/want/ubuntu\ linux
To see the list of the files in a directory type: ls /directory
To navigate up one directory level type cd ..
To navigate to the previous directory type cd -
Delete a file: rm /directrory/file.pdf Delete directory: rm -R /directory
Copy files from terminal and change name: sudo cp /directory/file.pdf /directory2/file2.pdf replace “cp” with “mv” to move files
See running processes: ps -A
Kill a process: sudo kill ##### or sudo killall #####
Kill a running program: xkill
Eject CD-Rom: eject -T

**[COLOR="Green"]Auto Shutdown[/COLOR]**
```
sudo shutdown -h now
sudo shutdown -h 5
sudo shutdown -h 23:07
```

**[COLOR="Green"]Wake On LAN[/COLOR]**
Go to bios and enable the “Wake On Lan”
```
sudo apt-get install wakeonlan
```
wakeonlan 00:13:D4:CE:41:80
You replace this “00:13:D4:CE:41:80” with the MAC Address of the computer you want to wake up

**[COLOR="Green"]Change NTFS Permissions[/COLOR]**
```
sudo apt-get install ntfs-config
```
Go to “Applications—>System Tools—>NTFS Configuration Tool” and put the permitions you want

**[COLOR="Green"]System info[/COLOR]**
```
sudo apt-get install sysinfo
```
you can find it from Applications &#8594; System Tools &#8594; Sysinfo

**[COLOR="Green"]System Details on your Desktop (Conky)[/COLOR]**
```
sudo apt-get install conky hddtemp lm-sensors python-feedparser
sudo chmod u+s /usr/sbin/hddtemp
sudo gedit /etc/default/hddtemp
```
replace everything inside with the following:
> RUN_DAEMON="true" 
DISKS_1="/dev/hdc" 
DISKS_2="/dev/sda" 
DISKS_NOPROBE="" 
INTERFACE="127.0.0.1" 
PORT="7634" 
SYSLOG="10"  
OPTIONS=""

copy the files in the folder “Conky” to the home folder. There are some hidden files that they should also be copied.
Open the “.conkyrc” file and find “yourEMAIL” and the “yourPassword” and replace them with your gmail account info.
to start it press Alt+F2 and type “conky”

**[COLOR="Green"]Install VMWare Workstation[/COLOR]**
go to http://www.vmware.com/download/ws/ and download the latest version
```
sudo apt-get install build-essential
cd ...../VMware-Workstation-6.5.2-156735
sudo ./VMware-Workstation-6.5.2-156735.x86_64.bundle
```
if you have keygen then write this:
```
chmod +x keygen
./keygen
```
make the sound work
```
**Haven't tried it**
sudo -i
aptitude install alsa-oss
chmod +s /usr/lib/libaoss.so.*
mv /usr/bin/vmware /usr/bin/vmware.orig
echo '#!/bin/bash' > /usr/bin/vmware
echo 'LD_PRELOAD=libaoss.so exec /usr/bin/vmware.orig "$@"' >> /usr/bin/vmware
chmod +x /usr/bin/vmware
exit
```

**[COLOR="Green"]Record my desktop[/COLOR]**
```
sudo apt-get install gtk-recordmydesktop
```
you find it from Applications &#8594; Sound & Video &#8594; gtk-recordMyDesktop

**[COLOR="Green"]Set as Wallpaper with right click[/COLOR]**
copy the script “Set as Wallpaper” from my folder to “~/.gnome2/nautilus-scripts”

**[COLOR="Green"]Installing WINE[/COLOR]**
Download from http://wine.budgetdedicated.com/archive/index.html the latest version and install it
```
wine iexplore http://www.winehq.org
sudo nautilus /usr/share/wine/fonts
```
replace the fonts: tahoma.ttf and tahomabd.ttf with the ones of windows
To run a program open console and then press:
```
wine start program.exe
```
To save files from wine install them in “My Documents” or “Desktop”

**[COLOR="Green"]Create your own custom Ubuntu[/COLOR]**
```
echo "deb http://www.remastersys.klikit-linux.com/repository remastersys/" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install remastersys
sudo remastersys
```
This command will take a while:
```
sudo remastersys dist
```
When it is over it will be created this file: “/home/remastersys/customdist.iso” that you will burn it on a CD
To remove the files that have been created, type “sudo remastersys clean”

**[COLOR="Green"]Backup and Restore Ubuntu[/COLOR]**
```
sudo apt-get install sbackup
```
To Backup your system go to “System &#8594; Administration &#8594; Simple Backup Config”
To Restore your system go to  “System &#8594; Administration &#8594; Simple Backup Restore”

**[COLOR="Green"]Convert a Video[/COLOR]**
```
sudo apt-get install ffmpeg
ffmpeg -i input.avi -ar 22050 -r 25 -ab 32k -t 15.4 -s 320x240 output.avi
```
Options:
-i	&#8594; the video you want to convert
-r	&#8594; framerate
-s	&#8594; resolution of the video
-t	&#8594; how much time you want to convert
-sameq &#8594; same quality
-ab	&#8594; audio bitrate
-ar	&#8594;  audio frequency
for more info click [here]("http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html#SEC17")

**[COLOR="Green"]Put a Watermark on a Video[/COLOR]**
```
sudo apt-get install ffmpeg
ffmpeg -i input.avi -vhook "/usr/lib/vhook/drawtext.so -f /the/path/of/your/font/comic.ttf -x 5 -y 5 -t YourText -s 30" -sameq output.avi
```
Options:
-s <size>			&#8594; font size
-x <pos> -y <pos>	&#8594; position of the watermark
-t <text>			&#8594; the text you want to display
-o				&#8594; outline glyphs
-c <#RRGGBB>		&#8594; color of the text

**[COLOR="Green"]Autorun Programs[/COLOR]**
System &#8594; Preferences &#8594; Sessions
Press the button Add
You type the program to the Command
If you want you can put a name and a Comment
To find the Command of a program do the following:
Right click on Applications &#8594; Edit Menus &#8594; Find the program &#8594; Right click on program &#8594; Properties

**[COLOR="Green"]How to auto login to your account[/COLOR]**
System &#8594; Administration &#8594; Login Window &#8594;
Security &#8594; Enable Automatic Login (Checked) &#8594; select the User you want to login

**[COLOR="Green"]How to allow root user to login[/COLOR]**
System &#8594; Administration &#8594; Login Window &#8594;
Security &#8594; Allow local system administrator login (Checked)

**[COLOR="Green"]Convert bin/cue files to ISO[/COLOR]**
```
sudo apt-get install bchunk
bchunk file.bin file.cue file
```

**[COLOR="Green"]Read Greek files in ISO-8859-7[/COLOR]**
```
iconv -f WINDOWS-1253 -t UTF-8 file.txt > newfile.txt
```
		or
```
iconv -f ISO_8859-7 -t UTF-8 file.txt > newfile.txt
```
to see the type of your file type:
```
file the_file.txt
```

**[COLOR="Green"]Countdown timer applet for GNOME panel[/COLOR]**
```
sudo apt-get install timer-applet
```
to run it right click on GNOME panel &#8594; Add to Panel &#8594; select Timer

**[COLOR="Green"]Disable F-Lock and program keys from the keyboard[/COLOR]** _(doesn't work on ubuntu 8.10)_
```
sudo apt-get install keytouch
```
to run it go to “System &#8594; Preferences &#8594; KeyTouch”

**[COLOR="Green"]Openoffice 2.4[/COLOR]**
[COLOR="Red"]Install Greek dictionary[/COLOR]
Download the language you want from here
```
sudo nautilus /usr/lib/openoffice/share/dict/ooo and copy all the files inside the tar file
sudo gedit /usr/lib/openoffice/share/dict/ooo/dictionary.lst
```
Write in this file > DICT el GR el_GR. Replace it with the ones of your language
[COLOR="Red"]Backup settings[/COLOR]
go to ~/openoffice.org2 and copy the folder user folder where you want to save it.

**[COLOR="Green"]OpenOffice 3 beta (64bit)[/COLOR]**
[COLOR="Red"]Install Application[/COLOR]
```
firefox "http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxx86-64deb&lang=en-US&version=3.0.0"
tar xzf ~/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz
sudo dpkg -i ~/OOO300_m9_native_packed-1_en-US.9358/DEBS/*.deb
sudo apt-get install ia32-libs
sudo apt-get install sun-java6-jre ia32-sun-java6-bin
```
copy the contents of the “Terminal Commands” to > /usr/bin
start the program with this command: ```
/opt/openoffice.org3/program/soffice or soffice3
```
[COLOR="Red"]install dictionary[/COLOR]
open OpenOffice and go to “Tools &#8594; Extension Manager”, press Add and then find your dictionary
[COLOR="Red"]backup settings[/COLOR]
go to ~/.openoffice.org and copy the folder user folder where you want to save it.
[COLOR="Red"]How to open it[/COLOR]
if you put this on the Main Menu then you can put the %U like this: > ooffice3 -writer %U
ooffice3 -writer		Word Processor
ooffice3 -calc		Spreadsheet
ooffice3 -impress	Presentation
etc....

**[COLOR="Green"]Install latest, not stable, version of Ubuntu[/COLOR]**
```
update-manager -d
```

**[COLOR="Green"]How to fix the, switch keyboard layout[/COLOR]**
```
sudo gedit /etc/X11/xorg.conf
```
find Section “InputDevice” and replace it with this:
> Section "InputDevice" 
	Identifier    "Generic Keyboard" 
	Driver        "keyboard" 
	Option        "CoreKeyboard" 
	Option        "XkbRules"    "xorg" 
	Option        "XkbModel"    "pc105" 
	Option        "XkbLayout"    "us,gr" 
	Option		"XkbVariant"	"," 
	Option		"XkbOptions"	"grp:alt_shift_toggle,grp_led:scroll" 
EndSection

**[COLOR="Green"]Fix login small font size[/COLOR]**
Choose from the “Login Window Preferences” under the “Local” menu the Human theme which is the default
```
sudo gedit /usr/share/gdm/themes/Human/Human.xml
```
and find the “<normal color=......../>” and change the font size
```
sudo gedit /usr/share/gdm/themes/Human/gtk-2.0/gtkrc 
```
and find the “font_name = .......” and change the font size

**[COLOR="Green"]Install GDM Theme[/COLOR]**
Download from here the theme you want and copy the folder you downloaded to “/usr/share/gdm/themes/”

**[COLOR="Green"]Ubuntu-system-panel[/COLOR]**
```
sudo apt-get install subversion
svn checkout http://ubuntu-system-panel.googlecode.com/svn/trunk/ ubuntu-system-panel
cd ubuntu-system-panel
./usp_update install fresh
```
for 64 bit you will need one more step
```
sudo cp /usr/lib/python2.4/site-packages/usp/plugins/_keybind64.so _keybinder.so
```

**[COLOR="Green"]Write CD/DVD[/COLOR]**
you have two options
1. Go to “Places &#8594; CD/DVD Creator” and drag your files in the window and press the button “Write to Disc”
2. Go to “Applications &#8594; Sound & Video &#8594; Brasero Disc Burning”

**[COLOR="Green"]Remove partitions from desktop[/COLOR]**
Press Alt+F2 and type “gconf-editor” and navigate to “apps &#8594; nautilus &#8594; desktop”
From the right deselect the “volumes_visible”

**[COLOR="Green"]Audio Player (MP3)[/COLOR]**
```
sudo apt-get install amarok
```
a nice OSD Preview is:
> %title (%length)
%artist {- %year}
[COLOR="Red"]backup settings[/COLOR]
copy the directory ~/.kde/share/apps/amarok

**[COLOR="Green"]Create Panoramic photograph[/COLOR]**
```
sudo apt-get install hugin
```
you can find it from “Applications &#8594; Graphics &#8594; Hugin panorama creator”

**[COLOR="Green"]Greek-English Dictionary (Magenta)[/COLOR]**
go to this page: http://www.magenta.gr/gr/lexicon_gold_linux/ and download the deb file

**[COLOR="Green"]Typing tutor over terminal[/COLOR]**
```
sudo apt-get install gtypist
```
to run it type gtypist
to run it in silent mode type: gtypist -s
to run it with custom error percentage type (0 – 100): gtypist -e 15

**[COLOR="Green"]Audio Editor[/COLOR]**
```
sudo apt-get install audacity
```
after you install it, run it and go to “Edit &#8594; Preferences &#8594; go to tab Audio 1/0 and change the playback and recording to ALSA: default”
you can also install a more difficult program that is much better: ```
sudo apt-get install ardour
```

**[COLOR="Green"]Programming Compiler[/COLOR]**
```
sudo apt-get install geany
sudo apt-get install fp-compiler
```
this program is for lots of programming languages

**[COLOR="Green"]Programming like Visual Basic 6[/COLOR]**
It is called Gambas and can be downloaded from [here]("http://gambas.sourceforge.net/")

**[COLOR="Green"]Install Abyss Web Server x1[/COLOR]**
```
wget http://www.aprelium.com/data/abwsx1.tgz
tar xvfz abwsx1.tgz
rm abwsx1.tgz
cd abyssws
./abyssws
```
Press CTRL+C to stop Abyss Web Server
```
sudo ./autostart-setup install
```
It will automatically start on startup but to run it yourself execute ```
sudo /etc/init.d/abyssws start
```
To open the page of Abyss Web Server go to > http://127.0.0.1:9999

**[COLOR="Green"]FTP Server[/COLOR]**
You will need the gproftpd that you will find it from here: http://debian.cs.binghamton.edu/debian/pool/main/g/gadmin-proftpd/
To run it type on terminal: ```
sudo gadmin-proftpd
```

**[COLOR="Green"]Install telnet Server[/COLOR]**
```
sudo apt-get install telnetd
sudo /etc/init.d/openbsd-inetd restart
```
If you want to connect ubuntu with an other pc with telnet type: telnet 192.168.0.1
If you have windows and you want to connect to a telnet server you will have to use: putty or teraterm or something else

**[COLOR="Green"]Install SSH Server[/COLOR]**
[COLOR="Red"]What to do on linux[/COLOR]
```
apt-get install openssh-server openssh-client
```
If you want to connect ubuntu with an other pc with telnet type: ```
ssh user@your-server-ip-address
```
[COLOR="Red"]What to do on windows[/COLOR]
Download the PuTTY from here: http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html
Run it and put in the “Host Name (or IP address)” the ip of your linux pc and press Open
[COLOR="Red"]How to support Greek[/COLOR]
Open PuTTY and go to “Window &#8594; Translation”
In the list of encodings, select “UTF-8”
[COLOR="Red"]How to run GUI applications[/COLOR]
Download the “Xming” from here: http://sourceforge.net/projects/xming
Install it and run it. (it will run in the background)
Go to PuTTY and put the settings you want. You must also go to “Connection &#8594; SSH &#8594; X11”
there you must tick the “Enable X11 forwarding” and place in the text of “X display location” the “localhost:0”

**[COLOR="Green"]Create Proxy server[/COLOR]**
```
sudo apt-get install squid
sudo cp /etc/squid/squid.conf /etc/squid/squid.conf.backup
sudo gedit /etc/squid/squid.conf
```
change the http_access deny all to http_access allow all
```
sudo /etc/init.d/squid restart 
```
change the port:
```
sudo gedit /etc/squid/squid.conf
```
find the http_port and change the number. The default is 3128

**[COLOR="Green"]Batch rename files[/COLOR]**
```
sudo apt-get install krename
```
to run it go to “Applications &#8594; Accessories &#8594; Krename”

**[COLOR="Green"]How to drag and drop files to a location like windows[/COLOR]**
ubuntu has replaced the right click drag and drop with the middle click

**[COLOR="Green"]Install Kubuntu on Ubuntu[/COLOR]**
```
sudo apt-get install kubuntu-desktop
```
you can change the session you want from the login screen

**[COLOR="Green"]Install Gnome-Do[/COLOR]**
```
sudo apt-get install gnome-do
```

**[COLOR="Green"]Font Viewer[/COLOR]**
```
sudo apt-get install gnome-specimen
```

**[COLOR="Green"]Remove shadow from gnome panel if you use Compiz[/COLOR]**
go to “System &#8594; Preferences &#8594; CompizConfig Settings Manager”
then go to “Window Decoration”
find the “Shadow windows” and replace the “any” to “!title=Expanded Edge Panel” without the quotes and it's ready

**[COLOR="Green"]Find the color you want[/COLOR]**
```
sudo apt-get install gcolor2
```

**[COLOR="Green"]Mount image file to see it as a directory[/COLOR]**
Go to http://www.getdeb.net/app/AcetoneISO and download the deb file that is suitable for your system.

**[COLOR="Green"]Partition Editor[/COLOR]**
```
sudo apt-get install gparted
```

**[COLOR="Green"]Install a package with a link that you can send it[/COLOR]**
> apt:packagename
you put this link on your web browser and it installs the package you want.
You must replace packagename with your own package, e.g. apt:amarok

**[COLOR="Green"]Capture Tool to take screenshots[/COLOR]**
```
echo "deb http://ppa.launchpad.net/gscrot/ubuntu intrepid main" | sudo tee -a /etc/apt/sources.list
echo "deb-src http://ppa.launchpad.net/gscrot/ubuntu intrepid main" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install gscrot
```

**[COLOR="Green"]Desktop terminal[/COLOR]**
```
sudo apt-get install devilspie
mkdir ~/.devilspie
gedit ~/.devilspie/DesktopConsole.ds
```
paste the following
> (if(matches (window_name) "DesktopConsole") (begin(set_workspace 2)
(below)(undecorate)(skip_pager)(skip_tasklist)(wintype "utility")))
open terminal and go to “Edit &#8594; Profiles &#8594; New” 
in the Profile name put “terminal” and press “Create”
select the profile “terminal” and press “Edit”
in “General” tab untick the “Show menubar by default in new terminals”
in “Title and Commands” tab replace the title with “DesktopConsole”
in the “Background” tab select the “Transparent background” and go the bar to “None”
in the “Scrolling” tab find the “Scrollbar is:” and select the “Disabled” from the drop down menu
go to “System &#8594; Preferences &#8594; Sessions” and press “Add” and put in the Command the “devilspie”
Press again Add and pun in the Command the ```
gnome-terminal --geometry=80x15+300+50 --window-with-profile=terminal
```

**[COLOR="Green"]Play MP3 files through terminal[/COLOR]**
```
sudo apt-get install vlc
```
go to the directory of the mp3 files
```
vlc -I ncurses filename.mp3
```
		or
```
vlc -I ncurses *.mp3
```
you can find the help menu by pressing “m”

**[COLOR="Green"]Install Microsoft fonts on ubuntu[/COLOR]**
```
sudo apt-get install msttcorefonts
```

**[COLOR="Green"]Rename USB drive[/COLOR]**
You can rename by GUI with gparted or with terminal by the following instructions:
Mount external usb drive
```
sudo apt-get install mtools ntfsprogs e2fsprogs jfsutils reiserfsprogs xfsprogs
echo mtools_skip_check=1 >> ~/.mtoolsrc
```
[COLOR="Red"]change FAT16/FAT32 label[/COLOR]
```
sudo mlabel -i <device> ::<label>
```
[COLOR="Red"]change NTFS label[/COLOR]
```
sudo ntfslabel <device> <label>
```
[COLOR="Red"]change ext2/ext3 label[/COLOR]
```
sudo e2label <device> <label>
```
[COLOR="Red"]change JFS label[/COLOR]
```
sudo jfs_tune -L <label> <device>
```
[COLOR="Red"]change ReiserFS (v3) label[/COLOR]
```
sudo reiserfstune -l <label> <device>
```
[COLOR="Red"]change XFS label[/COLOR]
```
xfs_admin -l <label> <device>
```
<device> =your device /dev/sdxy, ex: /dev/sdd1
<label> =your desired (new) label, ex: my_external

**[COLOR="Green"]Run a command as root without terminal[/COLOR]**
create the launcher you want and write in the Command without the < >:
```
gksudo <your application or command>
```

**[COLOR="Green"]Create custom commands on terminal[/COLOR]**
sudo nautilus /usr/bin
copy the file ooffice, or something else, somewhere and open it with gedit
replace the text with the command you want and save it
then go to the file and change it's name with the command you wish.
Move it back to /usr/bin and it's ready to use!!!

**[COLOR="Green"]Desktop Terminal with show/hide function[/COLOR]**
```
sudo apt-get install tilda
```
or
```
sudo apt-get install guake		(not for x64)
```

**[COLOR="Green"]Terminal with grid[/COLOR]**
```
sudo apt-get install terminator
```

**[COLOR="Green"]Change File-Type icons[/COLOR]**
Go to ~/.icons and open the folder of the theme you want to change
find the mimetypes folder and open it
find an Icon you want, and paste it in there
Go to your file you want to change its icon and “Right-Click &#8594; Properties &#8594; Basic tab”
find the “Type:” and find the text in the parenthesis
the text looks like this: “application/msword”
Copy the text to the icon you copied previously and paste it there.
on the icon name change the “/” to “-”

**[COLOR="Green"]IP calculator[/COLOR]**
```
sudo apt-get install gip
```

**[COLOR="Green"]Enable DVD Playback (.VOB)[/COLOR]**
```
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
```
Insert a DVD into your drive and open it with Totem

**[COLOR="Green"]Create Document (Install templates)[/COLOR]**
Copy the contents of the Templates folder to ~/Templates.
If this folder doesn't exist, then do the following:
```
mkdir ~/Templates
gedit ~/.config/user-dirs.dirs
```
find the XDG_TEMPLATES_DIR="$HOME/" and change it to XDG_TEMPLATES_DIR="$HOME/Templates"
Copy the contents of the Templates folder to ~/Templates or download from internet

**[COLOR="Green"]Nautilus Scripts[/COLOR]**
1.Copy from my folder the “nautilus-scripts” to “~/.gnome2”
2.or download from internet and paste them in the “~/.gnome2/nautilus-scripts”

**[COLOR="Green"]Desktop Widgets (Screenlets)[/COLOR]**
```
sudo apt-get install screenlets
```
To run it go to “Applications &#8594; Accessories &#8594; Screenlets”

**[COLOR="Green"]Sync a folder with an other (like windows briefcase)[/COLOR]**
you have 2 options:
1.```
sudo apt-get install grsync
```
2.copy the “Sync Iriver” script from my folder to “~/.gnome2/nautilus-scripts” and edit it

**[COLOR="Green"]Device manager[/COLOR]**
There are two programs for device manager that can be found here: “Applications &#8594; System Tools”
```
1.sudo apt-get install kde-hal-device-manager
```
```
2.sudo apt-get install gnome-device-manager
```

**[COLOR="Green"]Install Amarok 2 on Ubuntu (not stable)[/COLOR]**
```
echo "deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main" | sudo tee -a /etc/apt/sources.list 
```
I enabled the prereleased and unsupported updates in the “software sources” and then I was able to update kdelibs and subsequently amarok to v2
```
sudo apt-get update
sudo apt-get install amarok-kde4
```

**[COLOR="Green"]Mail server (Send messages to an other ubuntu user)[/COLOR]**
```
sudo apt-get install mailx
```
[COLOR="Red"]Read messages:[/COLOR]
```
mailx
```
press the number of massage
[COLOR="Red"]Send message to user:[/COLOR]
```
mailx <user>
```
write a subject
write your message
press Ctrl+D

**[COLOR="Green"]Network Monitor[/COLOR]**
```
sudo apt-get install iptraf
```
to run it type:
```
sudo iptraf
```

[FONT="Comic Sans MS"][SIZE="6"]
[COLOR="Blue"]**My folder can be downloaded from [here]("http://rapidshare.com/files/235564583/ubuntu-my-folder.tar.gz")**[/COLOR][/SIZE][/FONT]
The same info are in my folder in an odt file.
I couldn't upload the file here, so I uploaded it to rapidshare.
Can anybody try to upload it for me? thanks!

---

### Post by SteveDee on 2009-05-29
Thank you bkbilly, there is some useful stuff here.

My tip is to put all personal tips into a wiki. Using Wikidpad, all text goes into a single database file, and its very quick and easy to add, edit and find stuff. It can also be exported to HTML.

With my poor memory I could not survive without it!

---

### Post by sancho panza on 2009-06-19
Thanks!

---

