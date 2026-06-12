---
title: "gEDA: HowTo, Tune-Up, Quirks, Tips&amp;Tricks for Ubuntu Edgy version"
date: 2006-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Adrian Nania on 2006-10-22
!!!  work in progress ](*,) !!!

The best gEDA documentation source I know: _**[http://geda.seul.org/wiki/geda:documentation](http://geda.seul.org/wiki/geda:documentation)**_

This post is for gEDA on Ubuntu Edgy and/or Feisty (partially tested on Debian Etch and Sid), i386/i686/K7 kernel. The best option for me was to install an updated gEDA version from source, mainly from CVS.
The easiest way is to use the necessary script to install one by one any required component. Look inside this Archive with script files:
_**[http://www.ubuntuforums.org/attachment.php?attachmentid=22504&d=1168224524](http://www.ubuntuforums.org/attachment.php?attachmentid=22504&d=1168224524)**_

**With this script is possible to use a brand new Ubuntu box and install automatically all the necessary dependencies and the latest gEDA components as of today, 20070107**

_**[COLOR="Blue"]This HowTo was initially created for the default version installed through synaptic. The synaptic version is too old and has way too many bugs. So, I decided to install the latest available gEDA from CVS and change this HOWTO to reflect this new version.[/COLOR]**_

If you fallowed the compiling steps as described in the attached script files, then is easy to make all the necessary changes to replace my default installation PATH with your choice.

After compiling gEDA from CVS sources, the first file we need to modify is /home/programs/gEDA/share/gEDA/system-gschemrc. Look inside the file, identify the lines we need to modify and apply the changes as described here or choose your own preferences:
```
kate /home/programs/gEDA/share/gEDA/system-gschemrc
```

To sort alphabetically the library files *.sym
```
;(sort-component-library "disabled")
(sort-component-library "enabled")
```
To disable the annoying log window pop-up
```
;(log-window "startup")
(log-window "later")
```
To select the right window size, on my case 1920x1200.
```
;(window-size 650 487)	; Good size for 800x600
;(window-size 900 650)	; Good size for 1024x768
;(window-size 950 712)	; Good size for 1152x864
;(window-size 1100 825)	; Good size for 1280x1024
;(window-size 1400 950)	; Good size for 1400x1150
;(window-size 1600 1022) ; Good size for 1600x1200
(window-size 1920 1022)	; Good size for 1920x1200
```
To print black on white:
```
(output-color "disabled")
;(output-color "enabled")
```
To keep the middle mouse button for "pan" action:
```
(middle-button "mousepan")
;(middle-button "action")
;(middle-button "stroke")
;(middle-button "repeat")
```
To activate the auto numbering for components placement:
```
(load (string-append gedadata "/scheme/auto-uref.scm"))
(add-hook! add-component-hook auto-uref)
(add-hook! copy-component-hook auto-uref)
```

The second file we need to modify is /home/programs/gEDA/share/gEDA/system-gafrc.
```
kate /home/programs/gEDA/share/gEDA/system-gafrc
```
Just identify the lines we need to modify and apply the changes.
The interesting part of adding user libraries: my choice to keep my own gEDA libraries is: /home/projects/gEDA-lib/sym
Change accordingly this path to your preferred location:
```
;(component-library-search "${GEDADATA}/sym")
(component-library-search "/home/projects/gEDA-lib/sym")
```

To get an working shortcut for attached PDF files to *.sym library files, the third file we need to modify is:
```
kate /home/programs/gEDA/bin/gschemdoc
```
We should have acroread installed, or use other PDF handler:
```
CANDIDATE_BROWSER="mozilla galeon netscape netscape-navigator opera firefox konqueror"
CANDIDATE_PDFREADER="acroread xpdf ggv gv"
```

[-o< _**[COLOR="Blue"]Now we can start using gEDA. Everything here is symbol editing, through gschem.[/COLOR]**_

To attach a PDF as &#8220;documentation&#8221; field to a *.sym library component, first edit the symbol and press (aa)
This keyboard shortcut is the equivalent command:
```
Add -> Attribute (aa)

```
The pop-up window allows us to type the desired documentation shortcut. Use the right syntax for "Name" and "Value", like:
```
Name <- documentation
Value <- file:///home/projects/PDF's/NPN/SOT-23/MMBT2222A.pdf
``` 
The "documentation" field could be a hyper link, like [http://rocky.digikey.com/WebLib/ST%20Micro/Web%20Data/MMBT2222A.pdf](http://rocky.digikey.com/WebLib/ST%20Micro/Web%20Data/MMBT2222A.pdf)
Do not check the "Visible" box, otherwise you will end up with all that story visible on your schematic.
To see/check/modify all the attributes, visible or invisible, force them to be visible with:
```
Edit -> Show/Hide Inv Text (en)
```
Check all of them and when everything looks OK change the invisible attributes to be invisible with (en)
Now, when a component is selected, the associated PDF files will be available right away with the keyboard shortcut (Ho):
```
Hierarchy -> Documentation (Ho)
```

Symbol Creation
[http://www.geda.seul.org/wiki/geda:documentation](http://www.geda.seul.org/wiki/geda:documentation)
[http://geda.seul.org/wiki/geda:master_attributes_list](http://geda.seul.org/wiki/geda:master_attributes_list)
[http://www.geda.seul.org/wiki/geda:csygas](http://www.geda.seul.org/wiki/geda:csygas)

There is no difference between the Schematic Capture interface and the actual Component Symbol interface.
To create/change a symbol is like working with a standard schematic and saving the file with the  *.sym extension.
Verify and select the desired &#8220;pinseq&#8221; for your component to be identical to the spice model pin sequence as listed inside the associated spice model file.
To achieve this, open a schematic, SELECT THE COMPONENT of interest and go down to the associated *.sym with the command (Hs):
```
Hierarchy -> Down Symbol (Hs)
```
To modify/add/verify the attributes for a pin, select the pin and use:
[/CODE]Edit -> Edit ... (ee)[/CODE]
&#8220;pinlabel&#8221; could be any character, {A, 1, B0, JohnDoe} with no space.
"pinnumber" must be a number, like {6, 3, 8, 22 ...}, corresponding to the real pcb footprint.
"pinseq" must be ordered and consecutive numbers, like {1, 2, 3, 4, ...}, from the spice file pins list.
ERROR_INVALID_PIN can happen if the &#8220;pinseq&#8221; don't start at 1 or have gaps in the numbering.
&#8220;pinseq&#8221; pin list from the spice model file must be associated with the corresponding &#8220;pinnumber&#8221;.
My personal choice: "pinseq" visible, &#8220;pinlabel&#8221; and "pinnumber" invisible.
This is the easiest and quickest way to verify if the pcb footprint pin assignment and the spice pin assignment must be corrected, because only "pinseq" is the absolute reference (stable and ordered).

#-o _**[COLOR="Red"]Very Important:[/COLOR]**_

You can play around with Snap Grid Spacing (oS) as necessary to draw graphic elements. However, the  Snap Grid Spacing looks like a buggy beast, many times the end result is just an unusable mess.  Do not move the red active end of a pin or the whole pin if the grid is not 100 mils. We can move only the inactive white end of a pin if the grid is not 100 mils.
More headaches we can get from the Edit -> Symbol Translate (et). This ferocious command must be used with 0 &#8220;zero&#8221; or multiples of 100 (mils) only, any other value will make the symbol unusable for a schematic with 100 mils grid. More, make sure the grid is set to 100 mils before using  Symbol Translate.
Looks quite useful to invoke two commands first thing right after editing a symbol:
(et) <- 1000 ;translate the symbol to 1000 mils to see any attributes around the symbol
(en) ;temporarily make the invisible attributes to become visible
Do not use the shortcut "Add -> Attribute (aa)" to add global component attributes if any other element is selected, otherwise the intended  general component attribute will be associated with that element accidentally selected. Do not use the shortcut "Add -> Attribute (aa)" to add pin attributes like pinlabel, pinnumber, pintype or pinseq if the pin is not first selected. We must first select that pin and only after that use "Add -> Attribute (aa)" or "Edit -> Edit (ee)", otherwise the pin-specific attribute will be a meaningless "floating around" global symbol attribute. Unfortunately gEDA in not verifying if a pin-specific attribute is actually attached to a pin or if a global symbol attribute is attached to a pin as a meaningless pin-specific attribute. You can get tricked and believe that the attribute you just placed on the screen is attached to what you need. If you want an entire symbol to be graphical (no elec. connections) , add a &#8220;graphical=1&#8221; attribute as global attribute to the symbol. The netlister will ignore these symbols entirely.
I suspect this are a few mandatory rules to use  Symbol creation/changes:
```
rule 01: you can modify Snap Grid Spacing (oS) to any value
rule 02: any time when a pin is placed, the active red end must be on 100mill
rule 03: to satisfy rule 2, change the grid (oS) to 100mill to place a pin
rule 04: do not touch the active red end of a pin if the grid is not 100mils
rule 05: only the white inactive end of a pin could be moved on any grid size
rule 06: activate the invisible attributes with (en)
rule 07: add any required attributes for documentation, footprint, spice model
rule 08: select an attribute and change its size with (ex)
rule 09: move around and place the attributes as desired
rule 10: change back the invisible text to normal invisible state with (en)
rule 11: verify the Snap Grid Spacing (oS) to be 100mils
rule 12: symbol Translate (et) must be used to set zero offset before saving
rule 13: mandatory, before saving, Edit -> Symbol Translate (et) 0 "zero"
rule 14: under no circumstances touch something other than save after rule 12
rule 15: save Page As (fa), choose the path and the name.sym
rule 16: to make some other changes, open again the desired symbol
```
Here is the NPN model example I am using, with all the attributes visible:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=18559&d=1162260457[/IMG]

1, 2, and 3 close to the pins are the "pinseq" attributes. Beside the "pinseq"=1,2,3 attributes, only the "refdes"=Q? and the "value"=MMBT2222A are visible by default. Select any placed attribute and use "Edit -> Edit Text (ex)" to change Value, Size, Color, and Alignment. I like for all the attributes Size=6, fits well on 100mils grid.

---

### Post by Adrian Nania on 2006-12-28
I suppose I will open another HowTo for installing electronics software under Ubuntu and keep this one for actual use of electronics tools.
Here is a beginning: a small collection of scripts to download, update and install gEDA and other electronic programs, under Ubuntu Edgy and Feisty and Debian Etch and Sid.
One must save/edit the script and replace all over my user name with his user name, my PATH choice with his own choice.
The *-compiling-prepare script takes care of all necessary dependencies for all the programs on my list. It is necessary to install both KDE and Gnome tools.

the gEDA packages must be built and installed in the following order:
# geda
# libstroke
# libgeda
# symbols
# gschem
# gnetlist
# gsymcheck
# gattrib
# utils
# docs
# examples
# pcb
# gerbv
# gnucap
# verilog
# gtkwave
# gwave
# ngspice
# datadraw
# gnetman
# gspiceui


# extra packages needed for electronic developement
# kjwaves
# gpsim-dev gpsim-doc gpsim-lcd gpsim-lcd-graphic gpsim-led gpsim-logic gputils
# ktechlab
# xgpasm
# cpik
# pikdev
# piklab
# kicad
# qucs

000-debian-etch-electronics-compiling-prepare script:
```
#!/bin/bash
# /home/backups/src/electro/gEDA/000-debian-etch-electronics-compiling-prepare
# created by Adrian Nania 20061226


clear
echo 'this is for Debian Etch 386/686/K7. For other distros the packages name could be different'
echo
echo the script MUST be executed as root. Login as root with '"su -"' followed by the password
echo the reason: any package MUST be compiled as root, otherwise you can end up with errors
echo
echo if you do not have the root enabled, open a console and type: '"sudo passwd root"'
echo you will be asked to type once your user password and to type twice the new root password
echo you can choose the same password for root as your personal password
echo
echo save this script on your HDD and change the file attributes to be '"executable"'
echo you can use konqueror for this or open a shell and type: '"chmod +x /.../FileName"'
echo also, edit the script and replace all over my user name '"adi"' with your '"name"'
echo modify my default directories with your personal preferences
echo
echo press '"Enter"' to continue or '"Ctrl-C"' to abort, enable root, and login with '"su -"' ...
read


rm -rf /home/adi/tmp /home/adi/.cvspass /home/programs/gEDA
rm -rf /home/adi/KJWaveSPICE.properties /home/programs/kjwaves
rm -rf /home/adi/Desktop/gEDA.desktop
rm -rf /home/adi/Desktop/gschem.desktop
rm -rf /home/adi/Desktop/gattrib.desktop
rm -rf /home/adi/Desktop/pcb.desktop
rm -rf /home/adi/Desktop/gerbv.desktop
rm -rf /home/adi/Desktop/gspiceui.desktop
rm -rf /home/adi/Desktop/gtkwave.desktop
rm -rf /home/adi/Desktop/gwave.desktop
rm -rf /home/adi/Desktop/kjwaves.desktop
mkdir /home/backups /home/backups/src /home/backups/src/electro /home/adi/tmp
mkdir /home/backups/src/electro/gEDA /home/programs /home/programs/gEDA
chown -R adi:adi /home/programs /home/backups/src /home/adi
cd /home/adi/tmp


# after a clean Ubuntu feisty i386 install:
cat >>sources.list <<"EOF"
deb http://ftp.us.debian.org/debian/ etch main contrib non-free
deb-src http://ftp.us.debian.org/debian/ etch main contrib non-free
deb http://security.debian.org/ etch/updates main contrib non-free
deb-src http://security.debian.org/ etch/updates main contrib non-free

EOF


cp -dpr /etc/apt/sources.list /etc/apt/sources.list.bak
cp -dpr /home/adi/tmp/sources.list /etc/apt/
clear
echo Ubuntu upgrade and package installation started.
echo if impatient, check the log file: /home/adi/tmp/update.log
apt-get update
apt-get -y dist-upgrade
apt-get install -y --force-yes gnome kde libgcj7-dev libgtk2.0-dev xaw3dg-dev subversion-tools \
        guile-1.8-dev groff gdk-imlib11-dev libgdk-pixbuf-dev build-essential automake1.9 gawk \
        libgd2-xpm-dev libxaw7-dev libedit-dev libgnome2-dev libgdchart-gd2-xpm-dev libdb3-dev \
        tclreadline colorgcc libpngwriter0-dev libgda2-dev libgdk-pixbuf-gnome-dev tclx8.4-dev \
        guile-gnome0-gnome-ui tclxml tcllib plotutils libplot-dev libplot-perl libwxgtk2.6-dev \
        libgdk-pixbuf-gnome-dev libguilegtk-1.2-dev libglade2-dev libgtkextra-dev latex-xcolor \
        autoconf libbz2-dev tetex-extra axel flex bison wine-dev tk8.4 libgtkextra-x11-2.0-dev \
	libtool libusb-dev exdbm xlibs-dev qt4-designer libqt3-mt-dev kde-devel-extras texinfo \
        sun-java5-jdk gperf octave2.9
# libgtk+2.0-directfb-dev replaced by libgtk2.0-0, libgtkextra-x11-2.0-dev not in ubuntu
apt-get clean
updatedb

apt-get remove -y automake1.4
cp -dpr /etc/apt/sources.list.bak /etc/apt/sources.list
rm -rf /etc/apt/sources.list.bak

```
000-ubuntu-edgy-electronics-compiling-prepare:
```
#!/bin/bash
# /home/backups/src/electro/gEDA/000-ubuntu-edgy-electronics-compiling-prepare
# created by Adrian Nania 20061226


clear
echo 'this is for (K)Ubuntu Edgy 386/686/K7. For other distros the packages name could be different'
echo
echo the script MUST be executed as root. Login as root with '"su -"' followed by the password
echo the reason: any package MUST be compiled as root, otherwise you can end up with errors
echo
echo if you do not have the root enabled, open a console and type: '"sudo passwd root"'
echo you will be asked to type once your user password and to type twice the new root password
echo you can choose the same password for root as your personal password
echo
echo save this script on your HDD and change the file attributes to be '"executable"'
echo you can use konqueror for this or open a shell and type: '"chmod +x /.../FileName"'
echo also, edit the script and replace all over my user name '"adi"' with your '"name"'
echo modify my default directories with your personal preferences
echo
echo press '"Enter"' to continue or '"Ctrl-C"' to abort, enable root, and login with '"su -"' ...
read


rm -rf /home/adi/tmp /home/adi/.cvspass /home/programs/gEDA
rm -rf /home/adi/KJWaveSPICE.properties /home/programs/kjwaves
rm -rf /home/adi/Desktop/gEDA.desktop
rm -rf /home/adi/Desktop/gschem.desktop
rm -rf /home/adi/Desktop/gattrib.desktop
rm -rf /home/adi/Desktop/pcb.desktop
rm -rf /home/adi/Desktop/gerbv.desktop
rm -rf /home/adi/Desktop/gspiceui.desktop
rm -rf /home/adi/Desktop/gtkwave.desktop
rm -rf /home/adi/Desktop/gwave.desktop
rm -rf /home/adi/Desktop/kjwaves.desktop
mkdir /home/backups /home/backups/src /home/backups/src/electro /home/adi/tmp
mkdir /home/backups/src/electro/gEDA /home/programs /home/programs/gEDA
chown -R adi:adi /home/programs /home/backups/src /home/adi
cd /home/adi/tmp


# after a clean Ubuntu Edgy i386 install:
cat >>sources.list <<"EOF"
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb http://www.getautomatix.com/apt edgy main
#AUTOMATIX REPOS START
deb http://archive.canonical.com/ubuntu dapper-commercial main
deb http://archive.ubuntu.com/ubuntu edgy-updates universe
deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END
EOF


cp -dpr /etc/apt/sources.list /etc/apt/sources.list.bak
cp -dpr /home/adi/tmp/sources.list /etc/apt/
clear
echo Ubuntu upgrade and package installation started.
echo if impatient, check the log file: /home/adi/tmp/update.log
apt-get update
apt-get -y dist-upgrade
apt-get install -y --force-yes gnome kde libgcj7-dev libgtk2.0-dev xaw3dg-dev subversion-tools \
        guile-1.6-dev groff gdk-imlib11-dev libgdk-pixbuf-dev build-essential automake1.9 gawk \
        libgd2-xpm-dev libxaw7-dev libedit-dev libgnome2-dev libgdchart-gd2-xpm-dev libdb3-dev \
        tclreadline colorgcc libpngwriter0-dev libgda2-dev libgdk-pixbuf-gnome-dev tclx8.4-dev \
        guile-gnome0-gnome-ui tclxml tcllib plotutils libplot-dev libplot-perl libwxgtk2.6-dev \
        libgdk-pixbuf-gnome-dev libguilegtk-1.2-dev libglade2-dev libgtkextra-dev latex-xcolor \
        libtool libbz2-dev tetex-extra wine-dev flex axel texinfo tk8.4 autoconf sun-java5-jdk \
        exdbm bison qt4-designer xlibs-dev libqt3-mt-dev kde-devel-extras xlibs-dev libusb-dev \
	gperf octave2.9
# libgtk+2.0-directfb-dev replaced by libgtk2.0-0, libgtkextra-x11-2.0-dev not in ubuntu
apt-get clean
updatedb

apt-get remove -y automake1.4
cp -dpr /etc/apt/sources.list.bak /etc/apt/sources.list
rm -rf /etc/apt/sources.list.bak

```
000-ubuntu-feisty-electronics-compiling-prepare
```
#!/bin/bash
# /home/backups/src/electro/gEDA/000-ubuntu-feisty-electronics-compiling-prepare
# created by Adrian Nania 20061226


clear
echo 'this is for (K)Ubuntu Feisty 386/686/K7. For other distros the packages name could be different'
echo
echo the script MUST be executed as root. Login as root with '"su -"' followed by the password
echo the reason: any package MUST be compiled as root, otherwise you can end up with errors
echo
echo if you do not have the root enabled, open a console and type: '"sudo passwd root"'
echo you will be asked to type once your user password and to type twice the new root password
echo you can choose the same password for root as your personal password
echo
echo save this script on your HDD and change the file attributes to be '"executable"'
echo you can use konqueror for this or open a shell and type: '"chmod +x /.../FileName"'
echo also, edit the script and replace all over my user name '"adi"' with your '"name"'
echo modify my default directories with your personal preferences
echo
echo press '"Enter"' to continue or '"Ctrl-C"' to abort, enable root, and login with '"su -"' ...
read


rm -rf /home/adi/tmp /home/adi/.cvspass /home/programs/gEDA
rm -rf /home/adi/KJWaveSPICE.properties /home/programs/kjwaves
rm -rf /home/adi/Desktop/gEDA.desktop
rm -rf /home/adi/Desktop/gschem.desktop
rm -rf /home/adi/Desktop/gattrib.desktop
rm -rf /home/adi/Desktop/pcb.desktop
rm -rf /home/adi/Desktop/gerbv.desktop
rm -rf /home/adi/Desktop/gspiceui.desktop
rm -rf /home/adi/Desktop/gtkwave.desktop
rm -rf /home/adi/Desktop/gwave.desktop
rm -rf /home/adi/Desktop/kjwaves.desktop
mkdir /home/backups /home/backups/src /home/backups/src/electro /home/adi/tmp
mkdir /home/backups/src/electro/gEDA /home/programs /home/programs/gEDA
chown -R adi:adi /home/programs /home/backups/src /home/adi
cd /home/adi/tmp


# after a clean Ubuntu feisty i386 install:
cat >>sources.list <<"EOF"
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
EOF


cp -dpr /etc/apt/sources.list /etc/apt/sources.list.bak
cp -dpr /home/adi/tmp/sources.list /etc/apt/
clear
echo Ubuntu upgrade and package installation started.
echo if impatient, check the log file: /home/adi/tmp/update.log
apt-get update
apt-get -y dist-upgrade
apt-get install -y --force-yes gnome kde libgcj7-dev libgtk2.0-dev xaw3dg-dev subversion-tools \
        guile-1.6-dev groff gdk-imlib11-dev libgdk-pixbuf-dev build-essential automake1.9 gawk \
        libgd2-xpm-dev libxaw7-dev libedit-dev libgnome2-dev libgdchart-gd2-xpm-dev libdb3-dev \
        tclreadline colorgcc libpngwriter0-dev libgda2-dev libgdk-pixbuf-gnome-dev tclx8.4-dev \
        guile-gnome0-gnome-ui tclxml tcllib plotutils libplot-dev libplot-perl libwxgtk2.6-dev \
        libgdk-pixbuf-gnome-dev libguilegtk-1.2-dev libglade2-dev libgtkextra-dev latex-xcolor \
        xlibs-dev libbz2-dev tetex-extra axel flex bison texinfo tk8.4 libgtkextra-x11-2.0-dev \
        libtool sun-java5-jdk exdbm autoconf libusb-dev kde-devel-extras qt4-designer wine-dev \
        libqt3-mt-dev gperf octave2.9
# libgtk+2.0-directfb-dev replaced by libgtk2.0-0, libgtkextra-x11-2.0-dev not in ubuntu
apt-get clean
updatedb

apt-get remove -y automake1.4
cp -dpr /etc/apt/sources.list.bak /etc/apt/sources.list
rm -rf /etc/apt/sources.list.bak

```
001-download-all
If only a specific package is required, just select the part of interest, not the whole set
```
#!/bin/bash
# /home/backups/src/electro/gEDA/001-download-all
# created by Adrian Nania 20061226


clear
rm -rf /home/adi/tmp
mkdir /home/adi/tmp
cd /home/adi/tmp


clear
# http://geda.seul.org/wiki/geda:installation
# http://geda.seul.org/wiki/geda:documentation
# http://www.geda.seul.org/developer.html
echo gEDA download started
export CVSROOT=:pserver:anoncvs@cvs.seul.org:/home/cvspsrv/cvsroot
echo To download the CVS version, the required CVS password is "guest"
cvs login
cvs co geda/gaf
cvs co geda/support
cvs co geda/buildgeda
cvs co geda/xgsch2pcb


clear
# http://pcb.sourceforge.net/
# http://sourceforge.net/cvs/?group_id=73743
# http://pcb.sourceforge.net/manual.html
echo download pcb
echo For password, just press Enter
cvs -d:pserver:anonymous@pcb.cvs.sourceforge.net:/cvsroot/pcb login
cvs -z3 -d:pserver:anonymous@pcb.cvs.sourceforge.net:/cvsroot/pcb co -P pcb


clear
# http://gerbv.sourceforge.net/
echo download gerbv
echo For password, just press Enter
cvs -d:pserver:anonymous@gerbv.cvs.sourceforge.net:/cvsroot/gerbv login
cvs -z3 -d:pserver:anonymous@gerbv.cvs.sourceforge.net:/cvsroot/gerbv co gerbv


clear
# http://www.geda.seul.org/tools/gnucap/index.html
# http://www.geda.seul.org/tools/gnucap/devel/
echo gnucap download started
axel -a http://www.geda.seul.org/tools/gnucap/devel/gnucap-0.35.tar.gz


clear
# http://www.icarus.com/eda/verilog/
# ftp://icarus.com/pub/eda/verilog/snapshots/
echo verilog download started
wget -c ftp://icarus.com/pub/eda/verilog/snapshots/verilog-20061210.tar.gz


clear
# http://home.nc.rr.com/gtkwave/
echo gtkwave download started
axel -a http://home.nc.rr.com/gtkwave/gtkwave-current.tar.gz


clear
# http://www.telltronics.org/software/gwave/
echo gwave download started
axel -a http://geda.seul.org/dist/gwave-20051222.tar.gz


clear
# http://ngspice.sourceforge.net/index.html
# http://ngspice.sourceforge.net/cvsaccess.html#
# http://ngspice.sourceforge.net/files/
echo ngspice download started
axel -a http://superb-west.dl.sourceforge.net/sourceforge/ngspice/ng-spice-rework-17.tar.gz
# axel -a http://ngspice.sourceforge.net/files/ng-spice-rework_CVS.tar.gz
# cvs -d :pserver:anonymous@cvs.ngspice.sourceforge.net:/cvsroot/ngspice login
# cvs co ngspice/ng-spice-rework


clear
echo datadraw download started
svn co https://datadraw.svn.sourceforge.net/svnroot/datadraw/trunk datadraw


clear
echo gnetman download started
wget -c http://www.viasic.com/opensource/gnetman-11Dec06.tar.gz


clear
echo gspiceui download started
wget -c http://downloads.sourceforge.net/gspiceui/gspiceui-v0.8.90.tar.gz


clear
echo kjwaves download started
axel -a http://www.comefly.us/files/kjwaves_1.1.1.zip


clear
echo gpsim download started
# from http://gpsim.sourceforge.net/gpsim_svn.html
cd /home/adi/tmp
svn co https://svn.sourceforge.net/svnroot/gpsim/trunk gpsim


clear
echo gpsim-lcd download started
# http://www.dattalo.com/gnupic/lcd.html
axel -a http://www.dattalo.com/gnupic/lcd-0.2.1.tar.gz


clear
echo xgpasm download started
axel -a http://xizard.free.fr/download/source/xgpasm-1.0.tar.gz


clear
echo cpik download started
axel -a http://pikdev.free.fr/cpik-0.1.tar.gz


clear
echo pikdev download started
axel -a http://pikdev.free.fr/pikdev-0.9.2-1.tar.gz


clear
echo swcadIII download started
axel -a http://ltspice.linear.com/software/swcadiii.exe


clear
echo piklab download started
svn co https://svn.sourceforge.net/svnroot/piklab/trunk/piklab piklab


# clear
# echo PIC30-toolchain download started
# axel -a http://downloads.sourceforge.net/piklab/binutils-pic30-2.01.tar.bz2
# axwl -a http://downloads.sourceforge.net/piklab/gcc-pic30-2.01.tar.bz2


clear
echo kicad download started
axel -a ftp://iut-tice.ujf-grenoble.fr/cao/kicad-2006-08-28.tgz


clear
echo adms download started
echo For password, just press Enter
# http://mot-adms.sourceforge.net/
# cvs -d:pserver:anonymous@mot-adms.cvs.sourceforge.net:/cvsroot/mot-adms login
# cvs -z3 -d:pserver:anonymous@mot-adms.cvs.sourceforge.net:/cvsroot/mot-adms co -P adms
wget -c http://easynews.dl.sourceforge.net/sourceforge/mot-adms/adms-2.2.4.tar.gz
# http://qucs.sourceforge.net/index.html
# http://qucs.sourceforge.net/download.html
clear
echo qucs download started
# echo For password, just press Enter
# cvs -d:pserver:anonymous@qucs.cvs.sourceforge.net:/cvsroot/qucs login
# cvs -z3 -d:pserver:anonymous@qucs.cvs.sourceforge.net:/cvsroot/qucs co qucs &&
# cvs -z3 -d:pserver:anonymous@qucs.cvs.sourceforge.net:/cvsroot/qucs co qucs-core &&
# cvs -z3 -d:pserver:anonymous@qucs.cvs.sourceforge.net:/cvsroot/qucs co qucs-doc
axel -a http://superb-west.dl.sourceforge.net/sourceforge/qucs/qucs-0.0.10.tar.gz


clear
chown -R adi:adi /home/adi/tmp
cd /

```

---

### Post by Adrian Nania on 2007-01-05
002-geda-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/002-geda-compile
# created by Adrian Nania 20061226


clear
echo 'this is for Ubuntu Edgy 386/686/K7. For other distros the packages name could be different'
echo
echo the script MUST be executed as root. Login as root with '"su -"' followed by the password
echo the reason: any package MUST be compiled as root, otherwise you can end up with errors
echo
echo if you do not have the root enabled, open a console and type: '"sudo passwd root"'
echo you will be asked to type once your user password and to type twice the new root password
echo you can choose the same password for root as your personal password
echo
echo save this script on your HDD and change the file attributes to be '"executable"'
echo you can use konqueror for this or open a shell and type: '"chmod +x /.../FileName"'
echo also, edit the script and replace all over my user name '"adi"' with your '"name"'
echo modify my default directories with your personal preferences
echo
echo first, run the '"000-ubuntu-edgy-electronics-compiling-prepare"' script to install dependencies
echo second, run the '"001-ubuntu-edgy-download-all"' script or copy the clean gEDA package here
echo you must respect the compiling order for the packages: 002*, 003*, 004*, ...
echo the gEDA suite can not be partially compiled or on top of the old existing one
echo
echo compiling geda project manager:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort, enable root, and login with '"su -"' ...
read


clear
rm -rf /home/programs/gEDA
rm -rf /home/adi/Desktop/gEDA.desktop
rm -rf /home/adi/Desktop/gschem.desktop
rm -rf /home/adi/Desktop/gattrib.desktop
mkdir /home/programs /home/programs/gEDA
cd /home/adi/tmp


clear
echo my choice for installation directory is /home/programs/gEDA
echo I will change in the the Makefile the default '$(HOME)/geda' with my choice
cd /home/adi/tmp/geda/gaf/
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
echo to fix the old editor error, /home/adi/tmp/geda/gaf/geda/src/tool.c is changed:
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
echo we need the default environment variables for gEDA:
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


clear
echo geda error fix from: http://www.seul.org/pipermail/geda-dev/2006-September/000746.html
echo geda error fix from: http://www.mail-archive.com/geda-dev@moria.seul.org/msg00731.html
echo the error info is for gschem but geda has the same bug
echo after the "'make all'" command, during geda compiling, we will change "'mkinstalldirs'"
echo in /home/adi/tmp/geda/gaf/geda/po/Makefile
echo 'mkinstalldirs = $(SHELL) $(MKINSTALLDIRS)' must be replaced with:
echo 'mkinstalldirs = ${top_srcdir}/mkinstalldirs'
cd /home/adi/tmp/geda/gaf/geda &&
./autogen.sh &&
./configure --prefix=/home/programs/gEDA &&
make all &&
sed -i 's/mkinstalldirs = \$(SHELL) \$(MKINSTALLDIRS)/mkinstalldirs = \${top_srcdir}\/mkinstalldirs/' /home/adi/tmp/geda/gaf/geda/po/Makefile &&
make install &&
clear &&
echo geda project manager compiled OK
echo


echo To start gEDA, you can use the Launcher created on your desktop:
echo
rm -rf /home/programs/gEDA/geda.start
rm -rf /home/adi/Desktop/gEDA.desktop
cat >>/home/programs/gEDA/geda.start <<"EOF"
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH
/home/programs/gEDA/bin/geda
EOF
chmod +x /home/programs/gEDA/geda.start
cat >>/home/adi/Desktop/gEDA.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/gEDA/geda.start
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=gEDA
GenericName[en_CA]=gEDA
Comment[en_CA]=
Name=gEDA
GenericName=gEDA
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```
003-libstroke-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/003-libstroke-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling libstroke:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


echo for libstroke, there is an error with tcl8.4 installed on /usr/include/tcl8.4
echo tcl files are requested from /usr/include/tcl or /usr/include, so we need extra symlinks
echo after the 'make all' command during geda compiling
cd /usr/include/
ln -s /usr/include/tcl8.4/tcl.h
ln -s /usr/include/tcl8.4/tclDecls.h
ln -s /usr/include/tcl8.4/tclPlatDecls.h
ln -s /usr/include/tcl8.4/tclDecls.h
ln -s /usr/include/tcl8.4/tclPlatDecls.h
cd /home/adi/tmp/geda/support/libstroke*
./configure --prefix=/home/programs/gEDA &&
make &&
make install &&
clear &&
echo libstroke compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
004-libgeda-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/004-libgeda-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling libgeda:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


echo libgeda error fix from: http://archives.seul.org/geda/user/Feb-2006/msg00172.html
echo there was a missing PATH variable: PKG_CONFIG_PATH=/home/adi/tmp/geda/gaf/libgeda
export PKG_CONFIG_PATH=/home/adi/tmp/geda/gaf/libgeda:${PKG_CONFIG_PATH}
cd /home/adi/tmp/geda/gaf/libgeda
export PKG_CONFIG_PATH=/home/adi/tmp/geda/gaf/libgeda:${PKG_CONFIG_PATH}
./autogen.sh &&
./configure --prefix=/home/programs/gEDA &&
make all &&
make install &&
clear &&
echo libgeda compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
005-symbols-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/005-symbols-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling symbols:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/geda/gaf/symbols
./autogen.sh &&
./configure --prefix=/home/programs/gEDA &&
make all &&
make install &&
clear &&
echo symbols compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
006-gschem-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/006-gschem-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling gschem:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


echo gschem error fix from: http://archives.seul.org/geda/dev/Dec-2006/msg00023.html
echo 'AM_GNU_GETTEXT_VERSION([%INSTALLED_GETTEXT_VERSION%])' replaced on 'configure.ac.in'
sed -i 's/AM_GNU_GETTEXT_VERSION(0.12.1)/AM_GNU_GETTEXT_VERSION([%INSTALLED_GETTEXT_VERSION%])/' /home/adi/tmp/geda/gaf/gschem/configure.ac.in
cd /home/adi/tmp/geda/gaf/gschem
./autogen.sh &&
./configure --prefix=/home/programs/gEDA --disable-nls &&
make all &&
make install &&
clear &&
echo gschem compiled OK
echo


echo To start gschem, you can use the Launcher created on your desktop:
echo
rm -rf /home/programs/gEDA/gschem.start
rm -rf /home/adi/Desktop/gschem.desktop
cat >>/home/programs/gEDA/gschem.start <<"EOF"
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH
/home/programs/gEDA/bin/gschem
EOF
chmod +x /home/programs/gEDA/gschem.start
cat >>/home/adi/Desktop/gschem.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/gEDA/gschem.start
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=gschem
GenericName[en_CA]=gschem
Comment[en_CA]=
Name=gschem
GenericName=gschem
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```
007-gnetlist-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/007-gnetlist-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling gnetlist:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/geda/gaf/gnetlist
./autogen.sh &&
./configure --prefix=/home/programs/gEDA &&
make all &&
make install &&
clear &&
echo gnetlist compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
008-gsymcheck-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/008-gsymcheck-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling gsymcheck:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/geda/gaf/gsymcheck
./autogen.sh &&
./configure --prefix=/home/programs/gEDA &&
make all &&
make install &&
clear &&
echo gsymcheck compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
009-gattrib-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/009-gattrib-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling gattrib:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/geda/gaf/gattrib
./autogen.sh &&
./configure --prefix=/home/programs/gEDA &&
make all &&
make install &&
clear &&
echo gattrib compiled OK
echo


echo To start gattrib, you can use the Launcher created on your desktop:
echo
rm -rf /home/programs/gEDA/gattrib.start
rm -rf /home/adi/Desktop/gattrib.desktop
cat >>/home/programs/gEDA/gattrib.start <<"EOF"
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH
/home/programs/gEDA/bin/gattrib
EOF
chmod +x /home/programs/gEDA/gattrib.start
cat >>/home/adi/Desktop/gattrib.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/gEDA/gattrib.start
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=gattrib
GenericName[en_CA]=gattrib
Comment[en_CA]=
Name=gattrib
GenericName=gattrib
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```
010-utils-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/010-utils-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling utils:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/geda/gaf/utils
./autogen.sh &&
./configure --prefix=/home/programs/gEDA &&
make all &&
make install &&
clear &&
echo utils compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
011-docs-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/011-docs-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling docs:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/geda/gaf/docs
./autogen.sh &&
./configure --prefix=/home/programs/gEDA &&
make all &&
make install &&
clear &&
echo docs compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
012-examples-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/012-examples-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling examples:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/geda/gaf/examples
./autogen.sh &&
./configure --prefix=/home/programs/gEDA &&
make all &&
make install &&
clear &&
echo examples compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
013-pcb-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/013-pcb-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling pcb:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/pcb
echo pcb error fix from: http://archives.seul.org/geda/user/Jul-2006/msg00350.html
echo to fix the error, --enable-maintainer-mode is added for ./configure
./configure --prefix=/home/programs/gEDA --with-exporters="ps gerber bom png" \
        --enable-maintainer-mode &&
make  &&
make install &&
clear &&
echo pcb compiled OK
echo


echo To start pcb, you can use the Launcher created on your desktop:
echo
rm -rf /home/programs/gEDA/pcb.start
rm -rf /home/adi/Desktop/pcb.desktop
cat >>/home/programs/gEDA/pcb.start <<"EOF"
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH
/home/programs/gEDA/bin/pcb
EOF
chmod +x /home/programs/gEDA/pcb.start
cat >>/home/adi/Desktop/pcb.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/gEDA/pcb.start
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=pcb
GenericName[en_CA]=pcb
Comment[en_CA]=
Name=pcb
GenericName=pcb
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```
014-gerbv-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/014-gerbv-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling gerbv:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/gerbv*
aclocal &&
autoheader &&
automake --copy --add-missing &&
autoconf &&
./configure --prefix=/home/programs/gEDA &&
make &&
make install &&
clear &&
echo gerbv compiled OK
echo


echo To start gerbv, you can use the Launcher created on your desktop:
echo
rm -rf /home/programs/gEDA/gerbv.start
rm -rf /home/adi/Desktop/gerbv.desktop
cat >>/home/programs/gEDA/gerbv.start <<"EOF"
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH
/home/programs/gEDA/bin/gerbv
EOF
chmod +x /home/programs/gEDA/gerbv.start
cat >>/home/adi/Desktop/gerbv.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/gEDA/gerbv.start
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=gerbv
GenericName[en_CA]=gerbv
Comment[en_CA]=
Name=gerbv
GenericName=gerbv
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```
015-gnucap-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/015-gnucap-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling gnucap:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/
tar -xzf gnucap*
cd gnucap*
./configure --prefix=/home/programs/gEDA &&
make &&
make install &&
clear &&
echo gnucap compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
016-verilog-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/016-verilog-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling verilog:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/
tar -xzf verilog*
cd verilog*
./configure --prefix=/home/programs/gEDA &&
make &&
make install &&
clear &&
echo verilog compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
017-gtkwave-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/017-gtkwave-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling gtkwave:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/
tar -xzf gtkwave*
cd gtkwave*
mkdir /home/programs/gEDA/share/doc/geda-doc/examples/gtkwave
cp -dpr ./examples/* /home/programs/gEDA/share/doc/geda-doc/examples/gtkwave/
cp -dpr /home/adi/tmp/gtkwave-3.0.19/.gtkwaverc /home/programs/gEDA/bin/
sed -i 's/read X/X="2"/' /home/adi/tmp/gtkwave-3.0.19/configure &&
./configure --prefix=/home/programs/gEDA &&
make &&
make install &&
clear &&
echo gtkwave compiled OK
echo


echo To start gtkwave, you can use the Launcher created on your desktop:
echo
rm -rf /home/programs/gEDA/gtkwave.start
rm -rf /home/adi/Desktop/gtkwave.desktop
cat >>/home/programs/gEDA/gtkwave.start <<"EOF"
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH
/home/programs/gEDA/bin/gtkwave /home/programs/gEDA/share/doc/geda-doc/examples/gtkwave/des.vzt
EOF
chmod +x /home/programs/gEDA/gtkwave.start
cat >>/home/adi/Desktop/gtkwave.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/gEDA/gtkwave.start
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=gtkwave
GenericName[en_CA]=gtkwave
Comment[en_CA]=
Name=gtkwave
GenericName=gtkwave
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```
018-NotDebian-gwave-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/018-NotDebian-gwave-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling gwave:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


echo '# http://biolpc22.york.ac.uk/pub/2.8.0-rc3/install-gtk-2.8.0-rc3.txt
# download gtk+ v1.3 from ftp://ftp.gtk.org/pub/gtk/v1.3, gwave doen not work with gtk+2
# the GTK 1.2 version and the 2 version can be installed at the same time
# you just have to use the correct include and library directories when compiling
# compile gtk+ v1.3 in /.../SomeDirectory and use: --with-gtk=${prefix} like:
# ./configure --with-gtk=1 --prefix=$HOME/localinst/gpsim
# ./configure --help
# gtk-config --cflags'


cd /home/adi/tmp/
'cp -dpr /home/backups/src/electro/gEDA/CVS-sources-20061226/pango-0.26.tar.gz ./
tar -xzf pango*
cd pango*
./configure --prefix=/home/adi/tmp/progs &&
make &&
make install &&
clear &&
echo pango compiled OK. Press enter to compile gtk1.2
read
cp -dpr /home/backups/src/electro/gEDA/CVS-sources-20061226/gtk+-1.3.9.tar.gz ./
tar -xzf gtk*
cd gtk*
./configure --prefix=/home/adi/tmp/progs &&
make &&
make install &&
clear &&
echo gwave compiled OK. Press enter to compile gwave
read'
# cp -dpr /home/backups/src/electro/gEDA/CVS-sources-20061226/gwave-20051222.tar.gz ./
tar -xzf gwave*
cd gwave*
./configure with --prefix=/home/programs/gEDA &&
make &&
make install &&
clear &&
echo gwave compiled OK
echo


echo To start gwave, you can use the Launcher created on your desktop:
echo
rm -rf /home/programs/gEDA/gwave.start
rm -rf /home/adi/Desktop/gwave.desktop
cat >>/home/programs/gEDA/gwave.start <<"EOF"
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH
/home/programs/gEDA/bin/gwave
EOF
chmod +x /home/programs/gEDA/gwave.start
cat >>/home/adi/Desktop/gwave.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/gEDA/gwave.start
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=gwave
GenericName[en_CA]=gwave
Comment[en_CA]=
Name=gwave
GenericName=gwave
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```
019-ngspice-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/019-ngspice-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling ngspice:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/
tar -xzf ng*
cd ng*
# cd /home/adi/tmp/ngspice/ng-spice-rework
#	--enable-maintainer-mode	this is for the CVS version
#	--enable-experimental	this one is generating errors
#	--enable-sense2		this one is generating errors
#	--enable-ekv		this one is generating errors
#	--enable-cider		this one is generating errors
#	--enable-cluster	this one is generating errors
./autogen.sh &&
./configure --prefix=/home/programs/gEDA \
	--enable-nosqrt \
	--enable-nobypass \
	--enable-capzerobypass \
	--enable-predictor \
	--enable-newtrunc \
	--enable-intnoise \
	--enable-xspice \
	--enable-numparam \
	--enable-dot-global \
	--enable-xgraph \
	--with-editline=yes &&
make &&
make install &&
clear &&
echo ngspice compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
020-datadraw-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/020-datadraw-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling datadraw:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/datadraw/datadraw3*
./configure --prefix=/home/programs/gEDA &&
make &&
make install &&
clear &&
echo datadraw compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
021-gnetman-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/021-gnetman-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling gnetman:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp
tar -xzf gnetman*
cd gnetman*
./configure --prefix=/home/programs/gEDA &&
make &&
make install &&
clear &&
echo gnetman compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
022-gspiceui-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/022-gspiceui-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling gspiceui:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/geda/gaf
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH


cd /home/adi/tmp/
tar -xzf gspiceui*
cd gspiceui*
make &&
make install INSTALLDIR=/home/programs/gEDA &&
clear &&
echo gspiceui compiled OK
echo


echo To start gspiceui, you can use the Launcher created on your desktop:
echo
rm -rf /home/programs/gEDA/gspiceui.start
rm -rf /home/adi/Desktop/gspiceui.desktop
cat >>/home/programs/gEDA/gspiceui.start <<"EOF"
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH
/home/programs/gEDA/bin/gspiceui
EOF
chmod +x /home/programs/gEDA/gspiceui.start
cat >>/home/adi/Desktop/gspiceui.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/gEDA/gspiceui.start
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=gspiceui
GenericName[en_CA]=gspiceui
Comment[en_CA]=
Name=gspiceui
GenericName=gspiceui
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```

---

### Post by Adrian Nania on 2007-01-05
023-kjwaves-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/023-kjwaves-compile
# created by Adrian Nania 20061226


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling kjwaves:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


rm -rf /home/programs/kjwaves
rm -rf /home/programs/kjwaves/kjwaves.start
rm -rf /home/adi/Desktop/kjwaves.desktop
rm -rf /home/adi/KJWaveSPICE.properties
mkdir /home/adi/tmp /home/programs /home/programs/kjwaves


cd /home/adi/tmp/
unzip kjwaves* &&
cp -dpr kjwaves /home/programs/ &&
clear &&
echo kjwaves installed OK
echo


echo To start kjwaves, you can use the Launcher created on your desktop:
echo
cat >>/home/programs/kjwaves/kjwaves.start <<"EOF"
export PATH=/home/programs/kjwaves:${PATH}
java -jar /home/programs/kjwaves/SpiceFE.jar
EOF
chmod +x /home/programs/kjwaves/kjwaves.start
cat >>/home/adi/Desktop/kjwaves.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/kjwaves/kjwaves.start
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=kjwaves
GenericName[en_CA]=kjwaves
Comment[en_CA]=
Name=kjwaves
GenericName=kjwaves
Comment=
EOF
cat >>/home/adi/KJWaveSPICE.properties <<"EOF"
#Sat Dec 23 16:55:55 PST 2006
#Sat Dec 23 16:55:55 PST 2006
rawfilepath=/home/adi/KJ-WavesRAW.OUT
SPICEEngine=ngspice
SPICEDevicesXMLFile=/home/programs/kjwaves/SpiceDevices.xml
circuitpath=/home/adi/test.CIR
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```
024-gpsim-install
```
#!/bin/bash
# /home/backups/src/electro/gEDA/024-gpsim-install
# created by Adrian Nania 20061226


echo installing gpsim:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort ...
read


apt-get update
apt-get -y dist-upgrade
apt-get install -y gpsim-dev gpsim-doc gpsim-lcd gpsim-lcd-graphic gpsim-led gpsim-logic gputils
apt-get clean


echo To start gpsim, you can use the Launcher created on your desktop:
rm -rf /home/adi/Desktop/gpsim.desktop
cat >>/home/adi/Desktop/gpsim.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=gnome-terminal -x gpsim
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=gpsim
GenericName[en_CA]=gpsim
Comment[en_CA]=
Name=gpsim
GenericName=gpsim
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```
025-ktechlab-install
```
#!/bin/bash
# /home/backups/src/electro/gEDA/025-ktechlab-install
# created by Adrian Nania 20061226


echo installing ktechlab:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort ...
read


apt-get update
apt-get -y dist-upgrade
apt-get install -y ktechlab
apt-get clean


echo To start ktechlab, you can use the Launcher created on your desktop:
rm -rf /home/adi/Desktop/ktechlab.desktop
cat >>/home/adi/Desktop/ktechlab.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=ktechlab
TryExec=
Icon=ktechlab
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=ktechlab
GenericName[en_CA]=ktechlab
Comment[en_CA]=
Name=ktechlab
GenericName=ktechlab
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /


echo 'cd /home/adi/tmp/
rm -rf ./*
cp -dpr /home/backups/src/electro/gEDA/CVS-sources-20061226/ktechlab* ./
tar -jxf ktechlab*
cd ktechlab*
# export PATH=/home/programs/gpsim/include/gpsim:${PATH}
# ./autogen.sh &&
./configure --prefix=/home/programs/pic &&
make &&
make install &&
clear &&
echo ktechlab compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /'

```
026-xgpasm-install
```
#!/bin/bash
# /home/backups/src/electro/gEDA/026-xgpasm-install
# created by Adrian Nania 20061226


echo installing xgpasm:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort ...
read


# from http://xizard.free.fr/logiciels/xgpasm/xgpasm.html
cd /home/adi/tmp
tar -xzf xgpasm*
cd xgpasm*
./configure --prefix=/home/programs/xgpasm &&
make &&
make install &&
clear &&
echo xgpasm compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /


echo To start xgpasm, you can use the Launcher created on your desktop:
rm -rf /home/adi/Desktop/xgpasm.desktop
cat >>/home/adi/Desktop/xgpasm.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/xgpasm/bin/xgpasm
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=xgpasm
GenericName[en_CA]=xgpasm
Comment[en_CA]=
Name=xgpasm
GenericName=xgpasm
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```
027-cpik-install
```
#!/bin/bash
# /home/backups/src/electro/gEDA/027-cpik-install
# created by Adrian Nania 20061226


echo installing cpik:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort ...
read


# from http://xizard.free.fr/logiciels/xgpasm/xgpasm.html
cd /home/adi/tmp
tar -xzf cpik*
cd cpik*
./cpik-install
# cp cpik /usr/bin/
# cp include/* /usr/share/cpik/include/
# cp lib/* /usr/share/cpik/lib/
# cp src/* /usr/share/cpik/src
# cp doc/* /usr/share/cpik/doc
echo cpik installed OK
echo
chown -R adi:adi /home/programs /home/adi
cd /

```
028-pikdev-install
```
#!/bin/bash
# /home/backups/src/electro/gEDA/028-pikdev-install
# created by Adrian Nania 20061226


echo installing pikdev:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort ...
read


# from http://pikdev.free.fr/
cd /home/adi/tmp
tar -xzf pikdev*
cd pikdev*
export MOC=/usr/share/qt3/bin/moc
./configure --prefix=/home/programs/pikdev \
        --with-qt-dir=/usr/share/qt3 \
        --with-qt-includes=/usr/include/qt3 \
        --with-qt-libraries=/usr/lib/qt3 --with-extra-libs=/usr/lib/kde3 \
        --enable-libsuffix= &&
make &&
make install &&
clear &&
echo pikdev compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /


echo To start pikdev, you can use the Launcher created on your desktop:
rm -rf /home/adi/Desktop/pikdev.desktop
cat >>/home/adi/Desktop/pikdev.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/pikdev/bin/pikdev
TryExec=
Icon=/home/programs/pikdev/share/icons/hicolor/32x32/apps/pikdev.png
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=pikdev
GenericName[en_CA]=pikdev
Comment[en_CA]=
Name=pikdev
GenericName=pikdev
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```
029-piklab-install
```
#!/bin/bash
# /home/backups/src/electro/gEDA/029-piklab-install
# created by Adrian Nania 20061226


echo installing piklab:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort ...
read


# http://piklab.sourceforge.net/
# http://ubuntuforums.org/showthread.php?t=123481&page=2
# http://piklab.sourceforge.net/install.php
cd /home/adi/tmp
cd piklab*
make -f Makefile.cvs
./configure --prefix=/home/programs/piklab --enable-debug=full &&
make &&
make install &&
clear &&
echo piklab compiled OK
echo
chown -R adi:adi /home/programs /home/adi
cd /


echo To start piklab, you can use the Launcher created on your desktop:
rm -rf /home/adi/Desktop/piklab.desktop
cat >>/home/adi/Desktop/piklab.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/piklab/bin/piklab
TryExec=
Icon=/home/programs/piklab/share/icons/hicolor/32x32/apps/piklab.png
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=piklab
GenericName[en_CA]=piklab
Comment[en_CA]=
Name=piklab
GenericName=piklab
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```
030-kicad-install
```
#!/bin/bash
# /home/backups/src/electro/gEDA/030-kicad-install
# created by Adrian Nania 20061226


echo installing kicad:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort ...
read


clear
#rm -rf /home/adi/tmp
mkdir /home/adi/tmp
cd /home/adi/tmp
#from http://www.lis.inpg.fr/realise_au_lis/kicad/
axel -a ftp://iut-tice.ujf-grenoble.fr/cao/kicad-2006-08-28.tgz
tar -xzf kicad*
rm -rf /home/programs/kicad
mv ./kicad /home/programs/
# from http://www.kicadlib.org/
rm -rf /home/adi/tmp/*
wget -c http://www.kicadlib.org/modules/Gajda_amplif_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Gajda_analogSW_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Vocanson_display_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/75lbc179_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/sc16is7x2_spi_tssop28_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/16c754_80_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/FT245BM_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Gajda_ttlieee_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Gajda_cmosieee_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Atmega8_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Atmega8_16PI_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Atmega64_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/attiny_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/18f2550_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/PIC18F4455_DIP40.lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/PIC18F45J10_DIP40.lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/18f4550_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/lpc2138_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Gajda_opto_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Cer_reso_lib.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/ULN280xA.lib.zip
unzip *.zip && rm *.zip
mv ./* /home/programs/kicad/library/
wget -c http://www.kicadlib.org/modules/FCP_ZIF_18.mod.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/CONN_USB_B_emp.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Vocanson_display_mod.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/TSSOIC28_mod.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/vqfp80_emp.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/TQFP32_08_emp.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/TQFP44_08_emp.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/ico_download01.png
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/PBRC_H_emp.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/D2PAK_emp.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Gajda_power_mod.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Frausti_Boschat_PCB.zip
unzip *.zip && rm *.zip
mv ./* /home/programs/kicad/modules
wget -c http://www.kicadlib.org/modules/fpc_conn_zif_smt_18.wrl.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/vqfp80_wrl.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Gajda_power_3D.zip
unzip *.zip && rm *.zip
wget -c http://www.kicadlib.org/modules/Frausti_Boschat_3D.zip
unzip *.zip && rm *.zip
mkdir /home/programs/kicad/modules/packages3d/contrib
mv ./* /home/programs/kicad/modules/packages3d/contrib


echo kicad installed OK
echo
chown -R adi:adi /home/programs /home/adi
cd /


echo To start kicad, you can use the Launcher created on your desktop:
rm -rf /home/adi/Desktop/kicad.desktop
cat >>/home/adi/Desktop/kicad.desktop <<"EOF"
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=kicad
Type=Application
Exec=/home/programs/kicad/linux/kicad
TryExec=
Icon=/home/programs/kicad/linux/kicad_icon.png
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=kicad
GenericName[en_CA]=kicad
Comment[en_CA]=
GenericName=kicad
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```
031-qucs-compile
```
#!/bin/bash
# /home/backups/src/electro/gEDA/031-qucs-compile
# created by Adrian Nania 20070105


clear
echo read iside of '"002-ubuntu-edgy-geda-compile"' script for general instructions
echo
echo compiling adms:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/
rm -rf /home/programs/adms
tar -xzf adms*
cd adms*
# autoheader && aclocal && automake && autoconf && ./configure --prefix=/home/programs/adms &&
./configure --prefix=/home/programs/adms && make && make install &&
clear &&
echo adms compiled OK
cd ..
echo press '"Enter"' to continue compiling qucs or '"Ctrl-C"' to abort
read


echo compiling qucs:
rm -rf /home/programs/qucs
tar -xzf qucs*
cd qucs*
./configure --prefix=/home/programs/qucs && make && make install &&
cd .. &&
echo qucs compiled OK


echo 'compiling qucs:
rm -rf /home/programs/qucs
cd qucs
sh autogen.sh &&
./configure --prefix=/home/programs/qucs --enable-maintainer-mode &&
make && make install &&
cd .. &&
echo qucs compiled OK
echo press '"Enter"' to continue compiling qucs-core or '"Ctrl-C"' to abort
read
cd qucs-core &&
export PATH=/home/programs/adms/bin:${PATH} &&
sh autogen.sh &&
./configure --prefix=/home/programs/qucs --enable-maintainer-mode &&
make && make install &&
cd .. &&
echo qucs-core compiled OK
echo press '"Enter"' to continue compiling qucs-doc or '"Ctrl-C"' to abort
read
cd qucs-doc &&
sh autogen.sh &&
./configure --prefix=/home/programs/qucs --enable-maintainer-mode &&
(cd technical/ && make technical) &&
(cd tutorial/ && make tutorial) &&
(cd tutorial/ && make book) &&
clear &&
echo qucs compiled OK
echo'


echo To start qucs, you can use the Launcher created on your desktop:
echo
rm -rf /home/adi/Desktop/qucs.desktop
cat >>/home/adi/Desktop/qucs.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/qucs/bin/qucs
TryExec=
Icon=/home/programs/qucs/share/qucs/bitmaps/big.qucs.xpm
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=qucs
GenericName[en_CA]=qucs
Comment[en_CA]=
Name=qucs
GenericName=qucs
Comment=
EOF
chown -R adi:adi /home/programs /home/adi
cd /

```

---

### Post by snowboard975 on 2007-03-04
Thanks a lot for this great howto. 

I'm trying to install geda but faced some errors. I'm afraid that gtkwave download script is no longer valid at this point. When running 001 script the following error appears.
```

Initializing download: http://home.nc.rr.com/gtkwave/gtkwave-current.tar.gz
HTTP/1.1 404 Not Found
./001-download-all: line 61:   907 Segmentation fault      (core dumped) axel -a http://home.nc.rr.com/gtkwave/gtkwave-current.tar.gz

```

gwave download link also seems to be invalid now. It shows the following error. 
```
gwave download started
Initializing download: http://geda.seul.org/dist/gwave-20051222.tar.gz
HTTP/1.1 404 Not Found
./001-download-all: line 67:   912 Segmentation fault      (core dumped) axel -a http://geda.seul.org/dist/gwave-20051222.tar.gz
```

I get the following error when running 024 script. I googled gpsim-lcd-graphic and it seems to be supported in Ubuntu Feisty but not in Edgy. Is there any other way to install it in Ubuntu Edgy?
```
E: Couldn't find package gpsim-lcd-graphic
```

---

### Post by Adrian Nania on 2007-03-09
This is unfortunately a mess we need to deal with as the people in charge do not have any kind of consideration for keeping name/shortcut compatibility.

To correct the download problem for gtkwave, try changing in “001-download-all” file the line:
axel -a [http://home.nc.rr.com/gtkwave/gtkwave-current.tar.gz](http://home.nc.rr.com/gtkwave/gtkwave-current.tar.gz)
with the line:
axel –a [http://home.nc.rr.com/gtkwave/gtkwave-3.0.22.tar.gz](http://home.nc.rr.com/gtkwave/gtkwave-3.0.22.tar.gz)

For gwave problem, still inside “001-download-all” file, change the line:
axel -a [http://geda.seul.org/dist/gwave-20051222.tar.gz](http://geda.seul.org/dist/gwave-20051222.tar.gz)
with this one:
axel –a [http://www.cs.unc.edu/~tell/dist/gwave-20051222.tar.gz](http://www.cs.unc.edu/~tell/dist/gwave-20051222.tar.gz)

I remember I tried to install gpsim-lcd-graphic on Edgy but I was stopped by some dependency problems. The good news: Feisty will be ready soon ...

---

### Post by dptxp on 2007-04-01
Has anyone installed on 64-bit ? The 64 bit version ?
Can anyone tell me how to do it ?

---

### Post by penvzila on 2007-06-21
I'm about to try.

---

### Post by Adrian Nania on 2007-06-30
_**[COLOR="Blue"]I will try to update the whole procedure for AMD64. This is a necessary exercise because many of the repositories are not any more available.[/COLOR]**_
If my choice of using Automatix2 is not desired, just remove the associated repositories. Automatix2 can help with wine for LT SwitcherCAD plus many extra audio/video programs.

AMD64-000-Ubuntu-Feisty-electronics-compiling-prepare
```

#!/bin/bash
# /home/programs/src/electro/gEDA/AMD64-000-Ubuntu-Feisty-electronics-compiling-prepare
# created by Adrian Nania 20070628


clear
echo 'this is for (K)Ubuntu Feisty AMD64. For other distros the packages name could be different'
echo
echo the scripts MUST be executed as root. Login as root with '"su -"' followed by the password
echo the reason: any package MUST be compiled as root, otherwise you can end up with errors
echo
echo if you do not have the root enabled, open a console and type: '"sudo passwd root"'
echo you will be asked to type once your user password and to type twice the new root password
echo you can choose the same password for root as your personal password
echo
echo save the scripts on your HDD and change the file attributes to be '"executable"'
echo you can use konqueror for this or open a shell and type: '"chmod +x /.../FileName"'
echo also, edit the script and replace all over my user name '"adi"' with your '"name"'
echo modify my default directories with your personal preferences
echo
echo press '"Enter"' to continue or '"Ctrl-C"' to abort, enable root, and login with '"su -"' ...
read


rm -rf /home/adi/tmp /home/adi/.cvspass /home/programs/gEDA
rm -rf /home/adi/KJWaveSPICE.properties /home/programs/kjwaves
# rm -rf /home/adi/Desktop/gEDA.desktop
rm -rf /home/adi/Desktop/gschem.desktop
rm -rf /home/adi/Desktop/gattrib.desktop
rm -rf /home/adi/Desktop/pcb.desktop
rm -rf /home/adi/Desktop/gerbv.desktop
rm -rf /home/adi/Desktop/gspiceui.desktop
rm -rf /home/adi/Desktop/gtkwave.desktop
rm -rf /home/adi/Desktop/gwave.desktop
rm -rf /home/adi/Desktop/kjwaves.desktop
mkdir /home/programs /home/programs/src /home/programs/src/electro /home/adi/tmp
mkdir /home/programs/src/electro/gEDA /home/programs/gEDA
chown -R adi:adi /home/programs /home/adi
cd /home/adi/tmp


# after a clean Ubuntu Feisty AMD64 install:
cat >>sources.list <<"EOF"

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe

deb http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe

deb http://www.getautomatix.com/apt feisty main


#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

#AUTOMATIX REPOS END
EOF


cp -dpr /etc/apt/sources.list /etc/apt/sources.list.bak
cp -dpr /home/adi/tmp/sources.list /etc/apt/
clear
echo Ubuntu upgrade and package installation started.
echo if impatient, check the log file: /home/adi/tmp/update.log
apt-get update
apt-get install -y --force-yes gnome kde libgcj7-dev libgtk2.0-dev xaw3dg-dev subversion-tools \
        guile-1.8-dev groff gdk-imlib11-dev libgdk-pixbuf-dev build-essential automake1.9 gawk \
        libgd2-xpm-dev libxaw7-dev libedit-dev libgnome2-dev libgdchart-gd2-xpm-dev libdb3-dev \
        tclreadline colorgcc libpngwriter0-dev libgda2-dev libgdk-pixbuf-gnome-dev tclx8.4-dev \
        exdbm gperf plotutils libplot-dev libplot-perl libwxgtk2.6-dev libqt3-mt-dev octave2.9 \
        libgdk-pixbuf-gnome-dev libguilegtk-1.2-dev libglade2-dev libgtkextra-dev latex-xcolor \
        xlibs-dev libbz2-dev tetex-extra axel flex bison texinfo tk8.4 libgtkextra-x11-2.0-dev \
        tcllib sun-java5-jdk autoconf libusb-dev kde-devel-extras qt4-designer wine-dev tclxml \
        libtool libgtkextra-x11-2.0-dev libgtk2.0-0 git-cvs transfig fig2ps tgif
apt-get -y autoremove
# apt-get install -y guile-gnome0-gnome-ui //this package is not available for Feisty AMD64 ?
apt-get -y dist-upgrade
apt-get clean
clear
echo please wait, '"updatedb"' could take quite a while...
# updatedb
apt-get remove -y automake1.4
cp -dpr /etc/apt/sources.list.bak /etc/apt/sources.list
rm -rf /etc/apt/sources.list.bak
clear
echo AMD64-000-Ubuntu-Feisty-electronics-compiling-prepare DONE
echo


# the gEDA packages must be built and installed in the following order:
# geda
# libstroke
# libgeda
# symbols
# gschem
# gnetlist
# gsymcheck
# gattrib
# utils
# docs
# examples
# the remaining programs are not installed by gEDA:
# pcb
# gerbv
# gnucap
# verilog
# gtkwave
# gwave
# ngspice
# datadraw
# gnetman
# gspiceui


# extra packages needed for electronic developement
# kjwaves
# gpsim-dev gpsim-doc gpsim-lcd gpsim-lcd-graphic gpsim-led gpsim-logic gputils
# ktechlab
# xgpasm
# cpik
# pikdev
# piklab
# kicad

```
AMD64-001-Ubuntu-Feisty-download-all
```

#!/bin/bash
# /home/programs/src/electro/gEDA/AMD64-001-Ubuntu-Feisty-download-all
# created by Adrian Nania 20061226


rm -rf /home/adi/tmp
mkdir /home/adi/tmp
cd /home/adi/tmp


clear
echo references:
echo http://www.geda.seul.org/wiki/geda:installation
echo http://www.geda.seul.org/wiki/geda:documentation
echo http://www.geda.seul.org/developer.html
echo http://geda.seul.org/wiki/geda:scm
echo
echo gEDA download started
export CVSROOT=:pserver:anonymous@git.gpleda.org/home/git/gaf.git
cvs co master
# cp -dprv /home/programs/src/electro/gEDA/master /home/adi/tmp/
rm -rf /home/programs/src/electro/gEDA/master
cp -dprv /home/adi/tmp/master /home/programs/src/electro/gEDA/


clear
echo references:
echo http://pcb.sourceforge.net/
echo http://sourceforge.net/cvs/?group_id=73743
echo http://pcb.sourceforge.net/manual.html
echo
echo pcb download started
echo For password, just press Enter
cvs -d:pserver:anonymous@pcb.cvs.sourceforge.net:/cvsroot/pcb login
cvs -z3 -d:pserver:anonymous@pcb.cvs.sourceforge.net:/cvsroot/pcb co -P pcb
# cp -dprv /home/programs/src/electro/gEDA/pcb /home/adi/tmp/
rm -rf /home/programs/src/electro/gEDA/pcb
cp -dprv /home/adi/tmp/pcb /home/programs/src/electro/gEDA/


chown -R adi:adi /home/adi /home/programs
cd /
clear
echo AMD64-001-Ubuntu-Feisty-download-all DONE
echo

```
AMD64-002-gschem-compile
```

#!/bin/bash
# /home/programs/src/electro/gEDA/AMD64-002-gschem-compile
# created by Adrian Nania 20070630
clear
echo the script MUST be executed as root. Login as root with '"su -"' followed by the password
echo the reason: any package MUST be compiled as root, otherwise you can end up with errors
echo
echo if you do not have the root enabled, open a console and type: '"sudo passwd root"'
echo you will be asked to type once your user password and to type twice the new root password
echo you can choose the same password for root as your personal password
echo
echo save this script on your HDD and change the file attributes to be '"executable"'
echo you can use konqueror for this or open a shell and type: '"chmod +x /.../FileName"'
echo also, edit the script and replace all over my user name '"adi"' with your '"name"'
echo modify my default directories with your personal preferences
echo
echo first, run the '"AMD64-000-Ubuntu-Feisty-electronics-compiling-prepare"' script to install dependencies
echo second, run the '"AMD64-001-Ubuntu-Feisty-download-all"' script or copy the clean gEDA package here
echo you must respect the compiling order for the packages: 002*, 003*, 004*, ...
echo the gEDA suite can not be partially compiled or on top of the old existing one
echo
echo compiling geda project manager:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort, enable root, and login with '"su -"' ...
read
clear
echo from: http://www.seul.org/pipermail/geda-announce/2006-August/000023.html
echo The geda '(gManager)' source tarball is not longer being distributed/maintained
echo This is laughable, all that gEDA “project centric” bragging was BS after all
echo
echo press '"Enter"' to continue
read
clear


echo my choice for installation directory is /home/programs/gEDA
echo I will change in the the Makefile the default '$(HOME)/geda' with my choice
cd /home/adi/tmp/master
sed -i 's/prefix?=\$(HOME)\/geda/prefix?=\/home\/programs\/gEDA/' Makefile
# echo to fix the old editor error, /home/adi/tmp/geda/gaf/geda/src/tool.c is changed:
# sed -i 's/-----/kate/' /home/adi/tmp/geda/gaf/geda/src/tool.c
make
echo we need the default environment variables for gEDA:
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH
make install &&
clear &&
echo gEDA compiled OK
echo


echo To start gschem, you can use the Launcher created on your desktop:
echo
rm -rf /home/programs/gEDA/gschem.start
rm -rf /home/adi/Desktop/gschem.desktop
cat >>/home/programs/gEDA/gschem.start <<"EOF"
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH
/home/programs/gEDA/bin/gschem
EOF
chmod +x /home/programs/gEDA/gschem.start
cat >>/home/adi/Desktop/gschem.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/gEDA/gschem.start
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en]=gschem
GenericName[en]=gschem
Comment[en]=
Name=gschem
GenericName=gschem
Comment=
EOF


echo To start gattrib, you can use the Launcher created on your desktop:
echo
rm -rf /home/programs/gEDA/gattrib.start
rm -rf /home/adi/Desktop/gattrib.desktop
cat >>/home/programs/gEDA/gattrib.start <<"EOF"
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH
/home/programs/gEDA/bin/gattrib
EOF
chmod +x /home/programs/gEDA/gattrib.start
cat >>/home/adi/Desktop/gattrib.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/gEDA/gattrib.start
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en]=gattrib
GenericName[en]=gattrib
Comment[en]=
Name=gattrib
GenericName=gattrib
Comment=
EOF


chown -R adi:adi /home/programs /home/adi
cd /
clear
echo AMD64-002-gschem-compile DONE
echo

```
AMD64-003-pcb-compile
```

#!/bin/bash
# /home/programs/src/electro/gEDA/AMD64-003-pcb-compile
# created by Adrian Nania 20070630


clear
echo read iside of '"AMD64-000-Ubuntu-Feisty-electronics-compiling-prepare"' script for general instructions
echo
echo references:
echo 
echo http://pcb.sourceforge.net/obtaining.html
echo http://sourceforge.net/cvs/?group_id=73743
echo
echo compiling pcb:
echo press '"Enter"' to continue or '"Ctrl-C"' to abort and read instructions ...
read


cd /home/adi/tmp/pcb
echo pcb error fix from: http://archives.seul.org/geda/user/Jul-2006/msg00350.html
echo to fix the error, --enable-maintainer-mode is added for ./configure
./configure --prefix=/home/programs/gEDA --with-exporters="ps gerber bom png" \
        --enable-maintainer-mode &&
make  &&
make install &&
clear &&
echo pcb compiled OK
echo


echo To start pcb, you can use the Launcher created on your desktop:
echo
rm -rf /home/programs/gEDA/pcb.start
rm -rf /home/adi/Desktop/pcb.desktop
cat >>/home/programs/gEDA/pcb.start <<"EOF"
export LD_LIBRARY_PATH=/home/programs/gEDA/lib:$LD_LIBRARY_PATH
export PATH=/home/programs/gEDA/bin:${PATH}
export PKG_CONFIG_PATH=/home/programs/gEDA/lib/pkgconfig:$PKG_CONFIG_PATH
/home/programs/gEDA/bin/pcb
EOF
chmod +x /home/programs/gEDA/pcb.start
cat >>/home/adi/Desktop/pcb.desktop <<"EOF"
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/home/programs/gEDA/pcb.start
TryExec=
Icon=kcmmemory
X-GNOME-DocPath=
Terminal=false
Name[en_CA]=pcb
GenericName[en_CA]=pcb
Comment[en_CA]=
Name=pcb
GenericName=pcb
Comment=
EOF


chown -R adi:adi /home/programs /home/adi
cd /
clear
echo AMD64-003-pcb-compile DONE
echo

```

---

