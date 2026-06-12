---
title: "SCRIPT: Take back the Firefox &amp; Thunderbird logo"
date: 2006-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Sam on 2006-06-18
:arrow: [SIZE="3"][COLOR="Red"]**This script is for Dapper only !!!**
To use it with **Hoary** or **Breezy** please follow [this thread](http://ubuntuforums.org/showthread.php?t=34354) ![/COLOR][/SIZE]


:arrow: [SIZE="3"][COLOR="Red"]**Note for Edgy users:**
Some folks say that it works in Edgy, too (I have not tested it). However you need to use[/COLOR][/SIZE]
```
$ sudo bash restore_mozilla_icons
```
[SIZE="3"][COLOR="Red"]instead of[/COLOR][/SIZE]
```
$ sudo restore_mozilla_icons
```
[SIZE="3"][COLOR="Red"]to get it work.[/COLOR][/SIZE]



This script is intended to replace the blue globe with the original Firefox icon. It also replaces the Thunderbird icon. Works with both Gnome and KDE.

[IMG]http://img263.echo.cx/img263/2825/windowbar6xq.png[/IMG]

You have the choice to replace the Firefox program icon, the Firefox document icon, the Thunderbird program icon and/or the Thunderbird profile manager icon.

Here we go:
[list][*]Create a new script:
(KDE users: replace 'gedit' with 'kate')
```
$ sudo gedit /usr/local/bin/restore_mozilla_icons
```
[*]Paste the following lines:
```
#! /bin/sh

#
# Restore the original Firefox and/or Thunderbird icons.
#

#
# TODO: Create and implement SVG icons
#

FIREFOX_LIB="/usr/lib/firefox/"
FIREFOX_BIN="/usr/bin/mozilla-firefox"
THUNDERBIRD_BIN="/usr/bin/mozilla-thunderbird"

ICON_PACK_URL="http://ubuntu.globalvision.ch/mozilla_icons_dapper.tar.bz2"
ICON_PACK_FILENAME="mozilla_icons_dapper.tar.bz2"
TMP_DIR="/tmp/moz-icons"$$"/"


#Ctrl-C trapping
trap ctrlc INT
ctrlc()
{
	echo -e "\nAborted by user."
	rm -rf $TMP_DIR
	exit 2
}

#Input read function
readyn()
{
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
		echo 1
		return
	fi
	echo 0
}


#Check if run as root
if [ "$UID" -ne 0 ] ; then
	echo "You must be root to do that!"
	exit 1
fi


#Ask which icons to replace
replace_ff="0"
replace_ff_doc="0"
replace_tb="0"
replace_tb_pm="0"

if [ -x "$FIREFOX_BIN" ] ; then
	#Firefox
	echo -n "Replace the Mozilla Firefox program icon (y/n)? [y] "
	if [ `readyn` -ne 0 ] ; then
		replace_ff="1"
	fi

	#Firefox document
	echo -n "Replace the Mozilla Firefox document icon (y/n)? [y] "
	if [ `readyn` -ne 0 ] ; then
		replace_ff_doc="1"
	fi
fi

if [ -x "$THUNDERBIRD_BIN" ] ; then
	#Thunderbird
	echo -n "Replace the Mozilla Thunderbird program icon (y/n)? [y] "
	if [ `readyn` -ne 0 ] ; then
		replace_tb="1"
	fi

	#Thunderbird profile manager
	echo -n "Replace the Mozilla Thunderbird profile manager icon (y/n)? [y] "
	if [ `readyn` -ne 0 ] ; then
		replace_tb_pm="1"
	fi
fi

if [ "$replace_ff" -eq "0" ] && [ "$replace_ff_doc" -eq "0" ] && [ "$replace_tb" -eq "0" ] && [ "$replace_tb_pm" -eq "0" ] ; then
	echo "Nothing to do here."
	exit 0
fi


#Ask for divert the original packaged files to alternate locations
divert="0"

echo -e "\nDo you want to divert the original packaged files to alternate locations"
echo -n "(make the changes permanent) (y/n)? [y] "
if [ `readyn` -ne 0 ] ; then
	divert="1"
fi


#Downloading
echo -en "\nDownloading and replacing icons. Please wait..."

mkdir $TMP_DIR
wget $ICON_PACK_URL -O $TMP_DIR$ICON_PACK_FILENAME >/dev/null 2>&1
if [ ! -f $TMP_DIR$ICON_PACK_FILENAME ] ; then
	echo -e "\nCannot download icons. Please check your internet connection."
	rm -rf $TMP_DIR
	exit 1
fi
tar xjf $TMP_DIR$ICON_PACK_FILENAME -C $TMP_DIR


#Replace Firefox icon
if [ "$replace_ff" -gt "0" ] ; then
	if [ ! -f $TMP_DIR"mozilla-firefox.png" ] || [ ! -f $TMP_DIR"mozilla-firefox.xpm" ] ; then
		echo "Cannot continue (unavailable Firefox icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp -f /usr/share/pixmaps/firefox.png /usr/share/pixmaps/firefox.old.png
	cp -f /usr/share/pixmaps/mozilla-firefox.xpm /usr/share/pixmaps/mozilla-firefox.old.xpm
	cp -f $FIREFOX_LIB"icons/default.xpm" $FIREFOX_LIB"icons/default.old.xpm"
	cp -f $FIREFOX_LIB"chrome/icons/default/default.xpm" $FIREFOX_LIB"chrome/icons/default/default.old.xpm"

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/firefox.png >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm >/dev/null
		dpkg-divert --rename /usr/share/firefox/icons/default.xpm >/dev/null
		dpkg-divert --rename /usr/share/firefox/chrome/icons/default/default.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-firefox.png" /usr/share/pixmaps/firefox.png
	cp $TMP_DIR"mozilla-firefox.xpm" /usr/share/pixmaps/mozilla-firefox.xpm
	cp $TMP_DIR"mozilla-firefox.xpm" $FIREFOX_LIB"icons/default.xpm"
	cp $TMP_DIR"mozilla-firefox.xpm" $FIREFOX_LIB"chrome/icons/default/default.xpm"
	echo -n "."
fi


#Replace Firefox document icon
if [ "$replace_ff_doc" -gt "0" ] ; then
	if [ ! -f $TMP_DIR"mozilla-firefox-doc.png" ] ; then
		echo "Cannot continue (unavailable Firefox document icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp -f $FIREFOX_LIB"icons/document.png" $FIREFOX_LIB"icons/document.old.png"

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/firefox/icons/document.png >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-firefox-doc.png" $FIREFOX_LIB"icons/document.png"
	echo -n "."
fi


#Replace Thunderbird icon
if [ "$replace_tb" -gt "0" ] ; then
	#TODO: if [ ! -f $TMP_DIR"mozilla-thunderbird.png" ] || [ ! -f $TMP_DIR"mozilla-thunderbird.svg" ] || [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
	if [ ! -f $TMP_DIR"mozilla-thunderbird.png" ] || [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
		echo "Cannot continue (unavailable Thunderbird icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp -f /usr/share/pixmaps/mozilla-thunderbird.png /usr/share/pixmaps/mozilla-thunderbird.old.png
	#TODO: cp -f /usr/share/pixmaps/mozilla-thunderbird.svg /usr/share/pixmaps/mozilla-thunderbird.old.svg
	cp -f /usr/share/pixmaps/mozilla-thunderbird.xpm /usr/share/pixmaps/mozilla-thunderbird.old.xpm
	cp -f /usr/share/pixmaps/mozilla-thunderbird-menu.png /usr/share/pixmaps/mozilla-thunderbird-menu.old.png
	#TODO: cp -f /usr/share/pixmaps/mozilla-thunderbird-menu.svg /usr/share/pixmaps/mozilla-thunderbird-menu.old.svg
	cp -f /usr/share/pixmaps/mozilla-thunderbird-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-menu.old.xpm
	cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.old.xpm
	cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.old.xpm
	cp -f /usr/lib/mozilla-thunderbird/icons/default.xpm /usr/lib/mozilla-thunderbird/icons/default.old.xpm
	cp -f /usr/lib/mozilla-thunderbird/icons/mozicon16.xpm /usr/lib/mozilla-thunderbird/icons/mozicon16.old.xpm
	cp -f /usr/lib/mozilla-thunderbird/icons/mozicon50.xpm /usr/lib/mozilla-thunderbird/icons/mozicon50.old.xpm

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.png >/dev/null
		#TODO: dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.svg >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.xpm >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.png >/dev/null
		#TODO: dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.svg >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/icons/default.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/icons/mozicon16.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/icons/mozicon50.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-thunderbird.png" /usr/share/pixmaps/mozilla-thunderbird.png
	#TODO: cp $TMP_DIR"mozilla-thunderbird.svg" /usr/share/pixmaps/mozilla-thunderbird.svg
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird.xpm
	cp $TMP_DIR"mozilla-thunderbird.png" /usr/share/pixmaps/mozilla-thunderbird-menu.png
	#TODO: cp $TMP_DIR"mozilla-thunderbird.svg" /usr/share/pixmaps/mozilla-thunderbird-menu.svg
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-menu.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/icons/default.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/icons/mozicon16.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/icons/mozicon50.xpm
	echo -n "."
fi


#Replace Thunderbird profile manager icon
if [ "$replace_tb_pm" -gt "0" ] ; then
	#TODO: if [ ! -f $TMP_DIR"mozilla-thunderbird-pm.png" ] || [ ! -f $TMP_DIR"mozilla-thunderbird-pm.svg" ] || [ ! -f $TMP_DIR"mozilla-thunderbird-pm.xpm" ] ; then
	if [ ! -f $TMP_DIR"mozilla-thunderbird-pm.png" ] || [ ! -f $TMP_DIR"mozilla-thunderbird-pm.xpm" ] ; then
		echo "Cannot continue (unavailable Thunderbird icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp -f /usr/share/pixmaps/mozilla-thunderbird-pm.png /usr/share/pixmaps/mozilla-thunderbird-pm.old.png
	#TODO: cp -f /usr/share/pixmaps/mozilla-thunderbird-pm.svg /usr/share/pixmaps/mozilla-thunderbird-pm.old.svg
	cp -f /usr/share/pixmaps/mozilla-thunderbird-pm.xpm /usr/share/pixmaps/mozilla-thunderbird-pm.old.xpm
	cp -f /usr/share/pixmaps/mozilla-thunderbird-pm-menu.png /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.png
	#TODO: cp -f /usr/share/pixmaps/mozilla-thunderbird-pm-menu.svg /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.svg
	cp -f /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.xpm

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm.png >/dev/null
		#TODO: dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm.svg >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm.xpm >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.png >/dev/null
		#TODO: dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.svg >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-thunderbird-pm.png" /usr/share/pixmaps/mozilla-thunderbird-pm.png
	#TODO: cp $TMP_DIR"mozilla-thunderbird-pm.svg" /usr/share/pixmaps/mozilla-thunderbird-pm.svg
	cp $TMP_DIR"mozilla-thunderbird-pm.xpm" /usr/share/pixmaps/mozilla-thunderbird-pm.xpm
	cp $TMP_DIR"mozilla-thunderbird-pm.png" /usr/share/pixmaps/mozilla-thunderbird-pm-menu.png
	#TODO: cp $TMP_DIR"mozilla-thunderbird-pm.svg" /usr/share/pixmaps/mozilla-thunderbird-pm-menu.svg
	cp $TMP_DIR"mozilla-thunderbird-pm.xpm" /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm
	echo -n "."
fi


echo " done !"


#Reload gnome-panel (Gnome) or kicker (KDE)
echo -en "\nShall I reload the panel to apply the changes (y/n)? [y] "
if [ `readyn` -ne 0 ] ; then
	killall gnome-panel >/dev/null 2>&1
	killall kicker >/dev/null 2>&1
fi


rm -rf $TMP_DIR
exit 0
```

[*]Save the file and close the text editor.
[*]Allow execution:
```
$ sudo chmod +x /usr/local/bin/restore_mozilla_icons
```
[*]Run the script:
```
$ sudo restore_mozilla_icons
```
[*]Your icons are back ![/list]


[SIZE="2"]**Known bugs**:[/SIZE]
[list][*]If you create a launcher on the desktop (or copy the one in the menu to the desktop), the icon may be bigger than the others ([example](http://img136.imageshack.us/img136/6389/screenshotiy4.png)). If so, right click on the desktop icon, choose "Stretch icon" and resize it to the appropriate size.[/list]


[SIZE="2"]**Upgrade note**:[/SIZE]
[list][*]You may get the following message if you upgraded the script and did the package divert again:```
dpkg-divert: rename involves overwriting `/usr/share/firefox/icons/default.xpm.distrib' with different file `/usr/share/firefox/icons/default.xpm', not allowed
dpkg-divert: rename involves overwriting `/usr/share/firefox/icons/document.png.distrib' with different file `/usr/share/firefox/icons/document.png', not allowed
```
In this case, you need to delete the two .distrib files to get it work:
```
$ sudo rm /usr/share/firefox/icons/default.xpm.distrib
$ sudo rm /usr/share/firefox/icons/document.png.distrib
```
Then run the script again.[/list]

---

### Post by ciscosurfer on 2006-06-22
Excellent script!  Kudos!  =D>

---

### Post by d0d0 on 2006-06-22
Nice one dude !

---

### Post by Anduu on 2006-06-22
wOOt!

Thanx :mrgreen:

---

### Post by bionnaki on 2006-06-23
worked.
thanks

---

### Post by Laterix on 2006-06-23
Greate script! Very well written and nice to have options. Thank you for this.

---

### Post by rsgooch on 2006-06-23
This script ROCKS!

---

### Post by lwr on 2006-06-23
Very nice indeed. Is it possible to also change the picture in the bottom of the frame on Thunderbird, and the Help>About pictures too?
Thanks

---

### Post by Sam on 2006-06-23
Thank everybody for your feedback ! :o

[QUOTE=lwr]Very nice indeed. Is it possible to also change the picture in the bottom of the frame on Thunderbird, and the Help>About pictures too?
Thanks[/QUOTE]
I think you need to compile Thunderbird from scratch to do that... But I'm not sure.

---

### Post by Chris03 on 2006-06-23
How to replace the Help > About for Firefox, could be changed to work with Thunderbird:

1) Get Linux build from Mozilla.com and save to Desktop

2) Right click on the .tar.gz and select Extract

4) sudo dpkg-divert --rename /usr/share/firefox/chrome/browser.jar >/dev/null

3) sudo cp ~/Desktop/firefox/chrome/browser.jar /usr/share/firefox/chrome/browser.jar

Looks much better :D

---

### Post by Chrissss on 2006-06-24
Thank your VERY much :)

---

### Post by mtpadilla on 2006-06-27
Hello. Nice script....thanks a bunch!

---

### Post by dicecca112 on 2006-06-27
does this break clicking on links in Evolution and Gaim?

---

### Post by Sam on 2006-06-27
[QUOTE=dicecca112]does this break clicking on links in Evolution and Gaim?[/QUOTE]
No, it just replaces the images used as icons.

---

### Post by Brokenrgv on 2006-06-28
this is an awesome script thanks heaps :)

---

### Post by ozarkman on 2006-06-28
thanks works great in kubuntu this is the main reason I switched to ubuntu/kubuntu all the great community support.

---

### Post by domino on 2006-06-28
Another "it works!" comment from me =D> . Thanks!

---

### Post by Zybernaut on 2006-06-29
Way cool script, and a very well written post.

[IMG]http://www.soot-n-smoke.com/tsayles/uploaded_images/MozillaIcons-729213.png[/IMG]

---

### Post by geektron on 2006-06-30
Great script! Thanks a ton!

---

### Post by saxsux on 2006-06-30
Sorry if this is a bit stupid, but I'm completely new (I haven't even started using Ubuntu yet).
Why do Firefox and Mozilla not use the "proper" icons in the first place?

---

### Post by Sam on 2006-06-30
[QUOTE=saxsux]Sorry if this is a bit stupid, but I'm completely new (I haven't even started using Ubuntu yet).
Why do Firefox and Mozilla not use the "proper" icons in the first place?[/QUOTE]
[http://www.ubuntuforums.org/showpost.php?p=930038&postcount=6](http://www.ubuntuforums.org/showpost.php?p=930038&postcount=6)

---

### Post by petersjm on 2006-07-05
Woohoo! Thanks, I was looking for a way to get my Firefox icons back!

---

### Post by Shannon on 2006-07-06
I was bothered by Firefox having that generic icon as well, but I can't seem to get this script to work. Is there something other than gedit you have to use for Kubuntu? Should I not be using the terminal? When I put it into the terminal, it says gedit: command not found. When I try the first line in Run Command it just does nothing.

It's my first week using Kubuntu, so I'm still learning.

---

### Post by bionnaki on 2006-07-06
if you're using kubuntu, use kate instead of gedit. gedit is the editor for gnome. kate is the editor for kde.

---

### Post by Shannon on 2006-07-06
Thanks, it worked great!

I have used kate, but I didn't put it together what gedit was. Now I'll be aware. Thanks for the help!

---

### Post by tep200377 on 2006-07-06
Nice script ;) I love it !!

I had forgott all about 

$ sudo apt-get install mozilla-thunderbird    , untill i read this post ;)

---

### Post by treris on 2006-07-06
Excellent script, worked like a charm, I had all of this setup under breezy as well, but couldn't remember how i'd done it, now I won't have to 
SWEET!

---

### Post by static chaser on 2006-07-07
Glad to have my old icons back, thanks

---

### Post by giacomolg on 2006-07-14
My eyes thank you a loT!:D

---

### Post by SDREnate on 2006-07-14
Like everyone else said, great script! Works perfectly for me.

---

### Post by blastus on 2006-07-14
Sweet and simple! I have no clue how the script works but it just worked :)

---

### Post by vtel57 on 2006-07-16
Sam,

This linux newbie got that to work on the very first try. Thanks so much!

~Eric

---

### Post by gotmonkey on 2006-07-17
Thanks for the script. I had been missing the firefox icons. 

excellent work!

---

### Post by xeta on 2006-07-17
Such a simple script, but a definite must have for every installation.

---

### Post by Sam on 2006-07-17
Wow thank you all !!! I didn't expect so much positive comments !

;) ;) ;)

---

### Post by Dunnix on 2006-07-29
Woot! nice to have that logo back  thanks man

---

### Post by Scythe!? on 2006-07-30
Thank you! I have always preferred the original Mozilla icons to the Linux ones!

---

### Post by twofour on 2006-07-30
Thanks!! This is great.  \\:D/

---

### Post by Christopher on 2006-07-31
Worked like a charm !!  Thank you very much ;)

---

### Post by eidex on 2006-07-31
thanks for the script!

---

### Post by Uncle Spellbinder on 2006-07-31
Thanks! Great script. Though the Blue Globe for Firefox wasn't that big a deal for me, It's nice to have the good ol' logo back. The big point for me was the Thunderbird logo. *Very* happy to have that back!

Thanks again!

---

### Post by barrack on 2006-07-31
Thanks so much for this script.

I'm installing Ubuntu on a shared computer at work. Having continuity with program icons is key for them to get familiarized quicker.

---

### Post by goonies on 2006-07-31
> **blastus said:**
> Sweet and simple! I have no clue how the script works but it just worked :)


i agree with how i have no idea how it worked but it did... away with the ugly plain boring icons and in with the stylish ones =) those old icons were driving me coocoo, thanks for the excellent script

---

### Post by Faytz on 2006-07-31
Sweet.I hate the ubuntu pre-installed icons.They are fugly

---

### Post by frenky on 2006-08-01
This is a nice one :)
Thanks a bunch!

---

### Post by mgsfan on 2006-08-02
hmm ran it but it did'nt change the firefox icon..unlses it was'nt suppose to change the fox icon and instead on the original...it did change the thunderzilla one though.

---

### Post by Patskumaster on 2006-08-02
Excellent Script!=D>

---

### Post by Sam on 2006-08-02
> **mgsfan said:**
> hmm ran it but it did'nt change the firefox icon..unlses it was'nt suppose to change the fox icon and instead on the original...it did change the thunderzilla one though.

I don't understand. You asked the script to change the Firefox icon and it failed ?

---

### Post by MartinM on 2006-08-02
Thanks a lot Sam, brilliant script and exactly the reason why I joined the Ubuntu-community; people like you helping and teaching people like me...=D>=D>=D>

---

### Post by rune on 2006-08-02
The divert is not working correctly on my computer. I've tried removing firefox, all prior diverts, installing firefox again, running the script, downgrading and then upgrading firefox.

Somehow the icons in the chrome directory does not get divertet, and are overwritten when firefox is updated.

I'm not quite sure what is wrong, but it also seems impossible to remove the old diverts without first removing firefox, then removing diverts and reinstalling firefox.

Do other people have to run the script everytime firefox is updated???

---

### Post by kostkon on 2006-08-02
Excellent script, thanks!

---

### Post by rune on 2006-08-02
The script has one error. The diverts are not working correctly, so the icons are overwritten at every reinstall/update.

Short version: change
FIREFOX_LIB="/usr/lib/firefox/"
to
FIREFOX_LIB="/usr/share/firefox/"

in the very beginning of the script and the icons are retained over updates.

Long version:

The FIREFOX_LIB variable is wrong. Firefox_xxx.deb contains these picturefiles:
rune@dapper:/var/log$ dpkg -c /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb |grep "png\|xpm" -rw-r--r-- root/root     22346 2006-07-31 17:48:03 ./usr/share/firefox/chrome/icons/default/default.xpm
-rw-r--r-- root/root       680 2004-11-30 22:55:08 ./usr/share/firefox/searchplugins/amazondotcom.png
-rw-r--r-- root/root       356 2004-11-30 22:55:08 ./usr/share/firefox/searchplugins/creativecommons.png
-rw-r--r-- root/root      1150 2005-08-23 20:15:54 ./usr/share/firefox/searchplugins/answers.png
-rw-r--r-- root/root     16520 2006-07-31 17:54:46 ./usr/share/firefox/icons/mozicon128.png
-rw-r--r-- root/root     22346 2006-07-31 17:55:54 ./usr/share/firefox/icons/mozicon50.xpm
-rw-r--r-- root/root      2825 2006-07-31 17:55:54 ./usr/share/firefox/icons/mozicon16.xpm
-rw-r--r-- root/root      3154 2006-07-31 17:54:46 ./usr/share/firefox/icons/document.png
-rw-r--r-- root/root     22346 2006-07-31 17:55:54 ./usr/share/firefox/icons/default.xpm
-rw-r--r-- root/root      6433 2006-07-31 17:48:29 ./usr/share/pixmaps/firefox.png
-rw-r--r-- root/root     22346 2006-07-31 17:48:03 ./usr/share/pixmaps/mozilla-firefox.xpm
lrwxrwxrwx root/root         0 2006-07-31 17:55:55 ./usr/share/pixmaps/mozilla-firefox.png -> firefox.png

and the script diverts files placed in FIREFOX_LIB == /usr/**lib**/firefox, but dpkg installs files in /usr/**share**/firefox...
So the files are overwritten at every update.

---

### Post by Metroid48 on 2006-08-02
I just tried this, worked fine.

Great script!

---

### Post by Mathias-K on 2006-08-02
Beautiful solution.

You should really be talking to the Automatix guys, if you're not already working on getting this in. I'd save a lot of people a lot of trouble and time.

---

### Post by Sam on 2006-08-02
> **rune said:**
> The script has one error. The diverts are not working correctly, so the icons are overwritten at every reinstall/update.

Short version: change
FIREFOX_LIB="/usr/lib/firefox/"
to
FIREFOX_LIB="/usr/share/firefox/"

in the very beginning of the script and the icons are retained over updates.

Long version:

The FIREFOX_LIB variable is wrong. Firefox_xxx.deb contains these picturefiles:
rune@dapper:/var/log$ dpkg -c /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb |grep "png\|xpm" -rw-r--r-- root/root     22346 2006-07-31 17:48:03 ./usr/share/firefox/chrome/icons/default/default.xpm
-rw-r--r-- root/root       680 2004-11-30 22:55:08 ./usr/share/firefox/searchplugins/amazondotcom.png
-rw-r--r-- root/root       356 2004-11-30 22:55:08 ./usr/share/firefox/searchplugins/creativecommons.png
-rw-r--r-- root/root      1150 2005-08-23 20:15:54 ./usr/share/firefox/searchplugins/answers.png
-rw-r--r-- root/root     16520 2006-07-31 17:54:46 ./usr/share/firefox/icons/mozicon128.png
-rw-r--r-- root/root     22346 2006-07-31 17:55:54 ./usr/share/firefox/icons/mozicon50.xpm
-rw-r--r-- root/root      2825 2006-07-31 17:55:54 ./usr/share/firefox/icons/mozicon16.xpm
-rw-r--r-- root/root      3154 2006-07-31 17:54:46 ./usr/share/firefox/icons/document.png
-rw-r--r-- root/root     22346 2006-07-31 17:55:54 ./usr/share/firefox/icons/default.xpm
-rw-r--r-- root/root      6433 2006-07-31 17:48:29 ./usr/share/pixmaps/firefox.png
-rw-r--r-- root/root     22346 2006-07-31 17:48:03 ./usr/share/pixmaps/mozilla-firefox.xpm
lrwxrwxrwx root/root         0 2006-07-31 17:55:55 ./usr/share/pixmaps/mozilla-firefox.png -> firefox.png

and the script diverts files placed in FIREFOX_LIB == /usr/**lib**/firefox, but dpkg installs files in /usr/**share**/firefox...
So the files are overwritten at every update.

Good catch. Thank you for for noticing.

I've changed the script. I only changed the lines 129, 130 and 155, now they use "/usr/share/firefox/" instead of $FIREFOX_LIB (changing $FIREFOX_LIB value will broke the script elsewhere). I think it's enough. However, if you run the new script, you need to delete the next two files, in order to do the new divert.[list][*]/usr/share/firefox/icons/default.xpm.distrib
[*]/usr/share/firefox/icons/document.png.distrib[/list]

---

### Post by jinxed on 2006-08-03
Awesome! Great work! I finally have my icons back.

---

### Post by spiral777 on 2006-08-10
> spiral@Black-Ice:~$ sudo restore_mozilla_icons
Replace the Mozilla Firefox program icon (y/n)? [y] y
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
Replace the Mozilla Firefox document icon (y/n)? [y] y
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
Nothing to do here.
spiral@Black-Ice:~$

This is what I get. Any ideas?

---

### Post by Sam on 2006-08-10
> **spiral777 said:**
> This is what I get. Any ideas?

Sounds really strange... It seems that the script was not well executed by the shell. I don't know how to solve it. Maybe check that there is no missing lines in the script.

---

### Post by eriqk on 2006-08-12
Worked like a charm here. Thanks!

Groet, Erik

---

### Post by Mathias-K on 2006-08-13
Any chance of getting this into Automatix?

---

### Post by koma77 on 2006-08-13
Thanks a lot for the script. Worked great!

I really hate that blue globe icon, it's not very pretty...

---

### Post by vuitton on 2006-08-13
thank you very much, Sam. Great script !

---

### Post by Sam on 2006-08-13
> **Mathias-K said:**
> Any chance of getting this into Automatix?

I just sent a PM to the maker of Automatix... I'm waiting for his answer.

---

### Post by uncreative on 2006-08-13
best script ever...thanks!

---

### Post by Mathias-K on 2006-08-14
> **Sam said:**
> I just sent a PM to the maker of Automatix... I'm waiting for his answer.

Thanks a lot! :)

---

### Post by DevlinP on 2006-08-14
Thanks lots. :D

---

### Post by spiral777 on 2006-08-17
Ok, I just installed Thunderbird and tried it again.

> spiral@Black-Ice:~$ sudo restore_mozilla_icons
Replace the Mozilla Firefox program icon (y/n)? [y] y
[: 67: ==: unexpected operator
[: 67: ==: unexpected operator
[: 67: ==: unexpected operator
[: 67: ==: unexpected operator
Replace the Mozilla Firefox document icon (y/n)? [y] y
[: 67: ==: unexpected operator
[: 67: ==: unexpected operator
[: 67: ==: unexpected operator
[: 67: ==: unexpected operator
Replace the Mozilla Thunderbird program icon (y/n)? [y] y
[: 81: ==: unexpected operator
[: 81: ==: unexpected operator
[: 81: ==: unexpected operator
[: 81: ==: unexpected operator
Replace the Mozilla Thunderbird profile manager icon (y/n)? [y] y
[: 81: ==: unexpected operator
[: 81: ==: unexpected operator
[: 81: ==: unexpected operator
[: 81: ==: unexpected operator
Nothing to do here.


Can anyone post how to do this manually?

---

### Post by Sokraates on 2006-08-17
Easy. Simply execute the commands within the script manually. I will only take a bit longer this way. :D

First download the icon-pack from [http://ubuntu.globalvision.ch/mozilla_icons_dapper.tar.bz2](http://ubuntu.globalvision.ch/mozilla_icons_dapper.tar.bz2)
After creating the folder in /tmp, move the icon-pack over there.

Here are some the general commands you need to execute first:
Create a folder in /tmp
```
 mkdir /tmp/moz-icons 
```
Extract the icon-pack
```
 tar xjf /tmp/moz-icons/mozilla_icons_dapper.tar.bz2 –C /tmp/moz-icons 
```


Now for Firefox:
Backup the old icons
```
 sudo cp -f /usr/share/pixmaps/firefox.png /usr/share/pixmaps/firefox.old.png 
```
```
 sudo cp -f /usr/share/pixmaps/mozilla-firefox.xpm /usr/share/pixmaps/mozilla-firefox.old.xpm 
```
```
 sudo cp -f /usr/lib/firefox/icons/default.xpm /USR/LIB/FIREFOX/icons/default.old.xpm 
```
```
 sudo cp -f /usr/lib/firefox /chrome/icons/default/default.xpm /usr/lib/firefox /chrome/icons/default/default.old.xpm 
```
```
 sudo cp -f /usr/lib/firefox/icons/document.png /usr/lib/firefox/icons/document.old.png 
```

Divert the icons:
```
 sudo dpkg-divert --rename /usr/share/pixmaps/firefox.png >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/share/firefox/icons/default.xpm >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/share/firefox/chrome/icons/default/default.xpm >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/share/firefox/icons/document.png >/dev/null 
```

Replace the icons
```
 sudo cp /tmp/moz-icons/mozilla-firefox.png /usr/share/pixmaps/firefox.png 
```
```
 sudo cp /tmp/moz-icons/mozilla-firefox.xpm /usr/share/pixmaps/mozilla-firefox.xpm 
```
```
 sudo cp /tmp/moz-icons/mozilla-firefox.xpm /usr/lib/firefox/icons/default.xpm 
```
```
 sudo cp /tmp/moz-icons/mozilla-firefox.xpm /usr/lib/firefox/chrome/icons/default/default.xpm 
```
```
 sudo cp /tmp/moz-icons/mozilla-firefox-doc.png/ /usr/lib/firefox/icons/document.png 
```


And finally for Thunderbird:
Backup the old icons
```
 sudo cp -f /usr/share/pixmaps/mozilla-thunderbird.svg /usr/share/pixmaps/mozilla-thunderbird.old.svg 
```
```
 sudo cp -f /usr/share/pixmaps/mozilla-thunderbird.xpm /usr/share/pixmaps/mozilla-thunderbird.old.xpm 
```
```
 sudo cp -f /usr/share/pixmaps/mozilla-thunderbird-menu.png /usr/share/pixmaps/mozilla-thunderbird-menu.old.png 
```
```
 sudo cp -f /usr/share/pixmaps/mozilla-thunderbird-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-menu.old.xpm 
```
```
 sudo cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.old.xpm 
```
```
 sudo cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.old.xpm 
```
```
 sudo cp -f /usr/lib/mozilla-thunderbird/icons/default.xpm /usr/lib/mozilla-thunderbird/icons/default.old.xpm 
```
```
 sudo cp -f /usr/lib/mozilla-thunderbird/icons/mozicon16.xpm /usr/lib/mozilla-thunderbird/icons/mozicon16.old.xpm 
```
```
 sudo cp -f /usr/lib/mozilla-thunderbird/icons/mozicon50.xpm /usr/lib/mozilla-thunderbird/icons/mozicon50.old.xpm 
```
```
 sudo cp -f /usr/share/pixmaps/mozilla-thunderbird-pm.png /usr/share/pixmaps/mozilla-thunderbird-pm.old.png 
```
```
 sudo cp -f /usr/share/pixmaps/mozilla-thunderbird-pm.xpm /usr/share/pixmaps/mozilla-thunderbird-pm.old.xpm 
```
```
 sudo cp -f /usr/share/pixmaps/mozilla-thunderbird-pm-menu.png /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.png 
```
```
 sudo cp -f /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.xpm 
```

Divert the icons
```
 sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.png >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.xpm >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.png >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.xpm >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/lib/mozilla-thunderbird/icons/default.xpm >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/lib/mozilla-thunderbird/icons/mozicon16.xpm >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/lib/mozilla-thunderbird/icons/mozicon50.xpm >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm.png >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm.xpm >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.png >/dev/null 
```
```
 sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm >/dev/null 
```

Replace the icons
```
 sudo cp /tmp/moz-icons/mozilla-thunderbird.png /usr/share/pixmaps/mozilla-thunderbird.png 
```
```
 sudo cp /tmp/moz-icons/mozilla-thunderbird.xpm /usr/share/pixmaps/mozilla-thunderbird.xpm 
```
```
 sudo cp /tmp/moz-icons/mozilla-thunderbird.png /usr/share/pixmaps/mozilla-thunderbird-menu.png 
```
```
 sudo cp /tmp/moz-icons/mozilla-thunderbird.xpm /usr/share/pixmaps/mozilla-thunderbird-menu.xpm 
```
```
 sudo cp /tmp/moz-icons/mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm 
```
```
 sudo cp /tmp/moz-icons/mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm 
```
```
 sudo cp /tmp/moz-icons/mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/icons/default.xpm 
```
```
 sudo cp /tmp/moz-icons/mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/icons/mozicon16.xpm 
```
```
 sudo cp /tmp/moz-icons/mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/icons/mozicon50.xpm 
```
```
 sudo cp /tmp/moz-icons/mozilla-thunderbird-pm.png /usr/share/pixmaps/mozilla-thunderbird-pm.png 
```
```
 sudo cp /tmp/moz-icons/mozilla-thunderbird-pm.xpm /usr/share/pixmaps/mozilla-thunderbird-pm.xpm 
```
```
 sudo cp /tmp/moz-icons/mozilla-thunderbird-pm.png /usr/share/pixmaps/mozilla-thunderbird-pm-menu.png 
```
```
 sudo cp /tmp/moz-icons/mozilla-thunderbird-pm.xpm /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm 
```


Reload the gnome-panel to apply the changes
```
 sudo killall gnome-panel 
```

Remove the folder in /tmp together with the icon-pack
```
 sudo rm -rf /tmp/moz-icons 
```

---

### Post by jamadagni on 2006-08-19
Dude, I am a Kubuntu user with no GNOME apps running. What do I do with this section?:

#Reload gnome-panel

Can you tell me what to do to reload the KDE-panel (I presume this is for refreshing the icon on the menu)? Thanks.

---

### Post by jamadagni on 2006-08-19
Hey and I added [this bug in malone]("https://launchpad.net/distros/ubuntu/+source/firefox/+bug/56887").

---

### Post by Sam on 2006-08-19
> **jamadagni said:**
> Dude, I am a Kubuntu user with no GNOME apps running. What do I do with this section?:

#Reload gnome-panel

Can you tell me what to do to reload the KDE-panel (I presume this is for refreshing the icon on the menu)? Thanks.

The KDE equivalent is
```
$ killall kicker
```
or you can simply logout then login again.

---

### Post by EdThaSlayer on 2006-08-19
You just eye candied my desktop!
The blue globe didnt look as good as the nice awesome firefox sign i have now!

---

### Post by skip910 on 2006-08-19
I'm sorry for bringing up such an old topic, but it just seems as though my Firefox icon is HUGE compared to the other icons on the Desktop.

Here is a screenshot:
[IMG]http://img136.imageshack.us/my.php?image=screenshotiy4.png[/IMG]

If the image doesn't show up, here is the URL: [http://img136.imageshack.us/my.php?image=screenshotiy4.png]("http://img136.imageshack.us/my.php?image=screenshotiy4.png")

Is this for everyone? Is there something I can do to shrink it?

I know this may not seem like a big deal to you, but... it annoys me.... alot.

---

### Post by Sam on 2006-08-19
> **skip910 said:**
> I'm sorry for bringing up such an old topic, but it just seems as though my Firefox icon is HUGE compared to the other icons on the Desktop.

Here is a screenshot:
[IMG]http://img136.imageshack.us/my.php?image=screenshotiy4.png[/IMG]

If the image doesn't show up, here is the URL: [http://img136.imageshack.us/my.php?image=screenshotiy4.png]("http://img136.imageshack.us/my.php?image=screenshotiy4.png")

Is this for everyone? Is there something I can do to shrink it?

I know this may not seem like a big deal to you, but... it annoys me.... alot.

Right click on the icon, choose "Strech icon" and resize it to the appropriate size.

---

### Post by skip910 on 2006-08-19
Haha, such an easy answer to my problem.

Thanks a bunch!

---

### Post by Sam on 2006-08-20
> **skip910 said:**
> Haha, such an easy answer to my problem.

Thanks a bunch!

You're welcome ! ;)

---

### Post by Stew2 on 2006-08-20
Awesome script! :D Thanks!

Regards,
Stew2

---

### Post by Sam on 2006-08-21
> **Mathias-K said:**
> Any chance of getting this into Automatix?

Ok, the script will be included in a next version of Automatix. ([thread](http://www.getautomatix.com/forum/index.php?showtopic=65))

---

### Post by faceoftheearth on 2006-08-21
Cool script. It worked great but for a small issue. I had Firefox and Thunderbird in the gdesklet launcher that is like the OSX dock and after running this script gdesklets will no longer start. If I click on the icon in the menu it pops up a window titled "gDesklets shell" which never has any contents and eventually becomes nonresponsive. If I attempt to start gdesklets from the terminal it hangs on the first step which is "starting gDesklets daemon." Anything that might resolve this? I'm relatively new to Linux so I'm not sure where the config files are so that I could somehow just delete the current settings for the gDesklets launcher. 

Thanks for the script!

---

### Post by Sam on 2006-08-21
> **faceoftheearth said:**
> Cool script. It worked great but for a small issue. I had Firefox and Thunderbird in the gdesklet launcher that is like the OSX dock and after running this script gdesklets will no longer start. If I click on the icon in the menu it pops up a window titled "gDesklets shell" which never has any contents and eventually becomes nonresponsive. If I attempt to start gdesklets from the terminal it hangs on the first step which is "starting gDesklets daemon." Anything that might resolve this? I'm relatively new to Linux so I'm not sure where the config files are so that I could somehow just delete the current settings for the gDesklets launcher. 

Thanks for the script!

Usually all your personnal settings are stored in your home folder in dot files/directories (files starting with a dot are hidden). In a terminal list the hidden files with **ls -a** or with nautilus hit Ctrl-H. gDesklets settings are stored in ~/.gdesklets. You can safely remove this directory (ensure that gDesklets is not running) to wipe out the config. However you'll need to set up your desklets again after that. I hope it'll fix that annoyance.

---

### Post by faceoftheearth on 2006-08-21
Thanks for the great info! I'm used to going into Program Files to edit such settings. That ctrl-H thing is going to come in real handy.

---

### Post by Iskra on 2006-08-21
Much better. Thanks a lot!

---

### Post by Mathias-K on 2006-08-21
> **Sam said:**
> Ok, the script will be included in a next version of Automatix. ([thread](http://www.getautomatix.com/forum/index.php?showtopic=65))

Beautiful work. Thanks a ton!

---

### Post by The Pinny Parlour on 2006-08-26
Worked a treat.  Many thanks for your fine work  :D

---

### Post by tonester on 2006-08-27
Excellent work!

---

### Post by CaveRat on 2006-08-27
disregard my mistake

---

### Post by Sam on 2006-08-27
> **CaveRat said:**
> I found another way to do this without scripts or the terminal. Not sure what will happen if Tbird or Firefox updates, but here it is any way. I surfed to the TBird home page, right clicked on the Tbird logo, then saved it to Home. Next I opened Alacarte Menu editor, scrolled down to Tbird Mail, and right clicked for properties. Next I clicked on the Icon Button, browsed to Home, clicked open, then clicked on the logo and Ok. I did the same to the Icon on the panel. 
 I thought it was odd I had to do the same thing when I installed Firefox2, considering the correct icon is in the program package. However you get it done, the real logos are definitely eye candy compared to the linux icons.

Your solution changes only the icon of the menu item or launcher. This will not use that new icon in the windows list or in the application title.

---

### Post by CaveRat on 2006-08-27
> **Sam said:**
> Your solution changes only the icon of the menu item or launcher. This will not use that new icon in the windows list or in the application title.

Ok, I'm too new at this to understand what you are saying. Changing the icons in the Applications menu and on the panel is not correct even though I can see the proper icons? Please explain.

---

### Post by CaveRat on 2006-08-27
> **Sam said:**
> Your solution changes only the icon of the menu item or launcher. This will not use that new icon in the windows list or in the application title.

OH, wait. When I open the Tbird program, the icon up in the upper left corner is still the brown envelope. Is this what you are saying?

---

### Post by Sam on 2006-08-27
> **CaveRat said:**
> OH, wait. When I open the Tbird program, the icon up in the upper left corner is still the brown envelope. Is this what you are saying?

Yes, changing the icon for the launcher (linux equivalent of windows' shortcuts) will not affect the application at all.

The icons files are stocked in the Firefox/Thunderbird install directories, so if you use the script to change these icons, it will affect everything that calls them (shortcuts, menu items, applications, ...)

---

### Post by CaveRat on 2006-08-27
> **Sam said:**
> Yes, changing the icon for the launcher (linux equivalent of windows' shortcuts) will not affect the application at all.

The icons files are stocked in the Firefox/Thunderbird install directories, so if you use the script to change these icons, it will affect everything that calls them (shortcuts, menu items, applications, ...)

Ok I understand now. I have a problem though. After creating the script, I came up with a syntax error on line 31 when I tried to execute.

/usr/local/bin/restore_mozilla_icons: line 31: syntax error: unexpected end of file

---

### Post by Sam on 2006-08-27
> **CaveRat said:**
> Ok I understand now. I have a problem though. After creating the script, I came up with a syntax error on line 31 when I tried to execute.

/usr/local/bin/restore_mozilla_icons: line 31: syntax error: unexpected end of file

It seems you haven't copied the whole script (the script code block has a vertical scrolling). I've attached the script here. Download it to your home folder then type in a terminal:```
sudo mv ~/restore_mozilla_icons.txt /usr/local/bin/restore_mozilla_icons
```. Then continue the howto from the third point.

---

### Post by jamadagni on 2006-08-28
I just use the Firefox PNG from [this icon set]("http://www.crystalxp.net/galerie/en.id.792.htm") for my K Menu entries.

---

### Post by CaveRat on 2006-08-28
> **Sam said:**
> It seems you haven't copied the whole script (the script code block has a vertical scrolling). I've attached the script here. Download it to your home folder then type in a terminal:```
sudo mv ~/restore_mozilla_icons.txt /usr/local/bin/restore_mozilla_icons
```. Then continue the howto from the third point.

Oh good Lord. Thanks, that worked. :oops:

---

### Post by CaveRat on 2006-08-28
I have to take the compliments to another level. One of the most amazing things I think is so cool is the OS can be tweaked to our liking with text. Plain ol' English language text. All of you people who build, manipulate, tweak, etc, must have brains like an elephant to remember all the commands to make this work. I read the entire script and can not for the life of me know what much of it is telling me. And to know that another person came along, read the script, and understood every line enough to suggest a significant change. Awsome! All I know is when I looked in the /usr/lib/mozilla-thunderbird/icons before the script, only the ugly brown envelopes were there. Not only are the eye candy icons there now, the envelopes are changed to "old". Fascinating to say the least. It's people like you and all the others who "Understand and Know" that make this easy for us noobs to appreciate, and enjoy the switch from MS despite small glitches and hiccups that we experience like last week.  A standing ovation to all of you in the "Know". =D> =D> =D>  Keep up the good work.

---

### Post by Sam on 2006-08-28
> **CaveRat said:**
> I have to take the compliments to another level. One of the most amazing things I think is so cool is the OS can be tweaked to our liking with text. Plain ol' English language text. All of you people who build, manipulate, tweak, etc, must have brains like an elephant to remember all the commands to make this work. I read the entire script and can not for the life of me know what much of it is telling me. And to know that another person came along, read the script, and understood every line enough to suggest a significant change. Awsome! All I know is when I looked in the /usr/lib/mozilla-thunderbird/icons before the script, only the ugly brown envelopes were there. Not only are the original icons there now, the envelopes are changed to "old". Fascinating to say the least. It's people like you and all the others who "Understand and Know" that make this easy for us noobs to appreciate, and enjoy the switch from MS despite small glitches and hiccups that we experience like last week.  A standing ovation to all of you in the "Know". Keep up the good work.

Thanks, I'm very glad that you appreciate this aspect of Linux. You're exaclty right, in Linux (even all Unix clones) everything is a file and if possible things are stored in plain english ASCII. This make easy to tweak and debug everything, the control with the operating system is very big.

The console might be freaky for beginners, but with a little experience it become easy to understand the global approach of the commands. And writting home-made script for your repetitive tasks is very handy. If you are interested with the shell (console), [here](http://www.linuxcommand.org/) is a very good introduction.

---

### Post by CaveRat on 2006-08-28
Hey thanks. It looks like it will be a very informative read. I definately can use some experience with the command line. There are so many things I wish to do with my new OS. Like figure out why I could not watch a DVD rental movie. Last time I checked, DMA is enabled. I figure perhaps it's a software glitch somewhere, or perhaps I do not have the proper software installed. Not sure yet. I figured MPlayer would read DVD movies, but maybe not. I'll search through the How TO Forum before asking for help.

---

### Post by TannerLD on 2006-08-28
Thanks!

I like the real icons a lot better than the ones that came with it.

-Tanner

---

### Post by Sam on 2006-08-29
> **CaveRat said:**
> Hey thanks. It looks like it will be a very informative read. I definately can use some experience with the command line. There are so many things I wish to do with my new OS. Like figure out why I could not watch a DVD rental movie. Last time I checked, DMA is enabled. I figure perhaps it's a software glitch somewhere, or perhaps I do not have the proper software installed. Not sure yet. I figured MPlayer would read DVD movies, but maybe not. I'll search through the How TO Forum before asking for help.

Check [this](http://ubuntuguide.org/wiki/Dapper#How_to_install_DVD_playback_capability).

---

### Post by lepre on 2006-08-29
worked flawlessly! 8) 

Thank you! :KS :KS :KS

---

### Post by deol on 2006-08-30
Easy to follow and worked great!  Thanks so much :KS

---

### Post by ampop on 2006-09-12
Great. Thank you very much.

---

### Post by mrojas73 on 2006-09-12
This is one of my favorite howtos!!!

---

### Post by beetee2 on 2006-09-13
This is a great script! Worked perfect, smooth as a ribbon, and did exactly what it was intended to do with no surprises / malfunctions! \\:D/

---

### Post by jpyanowski on 2006-09-13
4 simple steps and I have my icons back, thanks. \\:D/

---

### Post by Emmett on 2006-09-13
Excellent script. Thank you

---

### Post by DC@DR on 2006-09-23
It works fine for me, but I notice one problem, and I'm not sure if this is the case for others...I currrently updated my firefox to v1.5.0.7, and applied this script to get the icons back, it worked seamlessly, but then I couldn't change my theme anymore. It seems like I only can use the default theme, since whenever I change themes, my FF won't even start up?? :-? I just don't understand why... :(

---

### Post by scotty32 on 2006-09-23
ive just read about [firefox here]("http://www.ubuntuforums.org/showthread.php?t=263367"), and was wondering what kind of 'legal issues' would arise from doing this?

---

### Post by Idiot B4K4 on 2006-09-23
Thank You Very Much I learned Alot.

---

### Post by gogogo111 on 2006-09-24
Awesome! Great work!

---

### Post by Sokraates on 2006-09-24
I took a look at Mozilla's licenses and this script actually **could** violate Mozilla's copyright.

First of all, trademarks are not an issue here, since neither the artwork, nor the names are used for a product different than the official one or used for commercial purposes. 

But the artwork is also protected under copyright-law and since it is not redistributed under a special license, the regular provisions apply. So (generally and with exceptions provided by national law) you may not copy, redistribute or make them available to others. Except, of course, if you distribute them as a part of the official Mozilla/Firefox/Thunderbird packages.

The artwork is not actively redistributed, but made available to others on the website the script downloads them from. So the copyright  would be infringed by the one, who put them on that page.

Copying is done by every user her/himself by calling the script, so we all are infringers in that sense.

The script itself is problematic in so far, as it greatly helps to find and copy the artwork. Because of this, the one who distributes or makes this script available could be held liable for copyright infringement. This also applies to the people maintaining this very website (on a sidenote: it's the same with every How-To or script involving copyrighted material, e.g. Automatix).

So the correct way would be to contact Mozilla Corporation and ask for permission. The less correct (and more risky) way would be to simply ignore this issue and see, what happens.

---

### Post by sciyoshi on 2006-09-28
Hey,

Great howto, nice of you to cook up a script for others to use :-). This is always one of the first things I do on a new system, that blue globe is just so ugly...

Anyways, small problem on Edgy: since they've changed the default shell to dash instead of bash, this script doesn't work. The easiest way to fix this is to change the first line to #!/bin/bash instead of #!/bin/sh. Kthkbye :-)

Samuel

---

### Post by testube_babies on 2006-09-30
I'm getting an error in Edgy, even after changing line 1 to #!/bin/bash

Any ideas?

```
keith@thor3edgy:~$ sudo sh icons.sh
Password:
Replace the Mozilla Firefox program icon (y/n)? [y] y
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
Replace the Mozilla Firefox document icon (y/n)? [y] y
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
[: 66: ==: unexpected operator
Replace the Mozilla Thunderbird program icon (y/n)? [y] y
[: 80: ==: unexpected operator
[: 80: ==: unexpected operator
[: 80: ==: unexpected operator
[: 80: ==: unexpected operator
Replace the Mozilla Thunderbird profile manager icon (y/n)? [y] y
[: 80: ==: unexpected operator
[: 80: ==: unexpected operator
[: 80: ==: unexpected operator
[: 80: ==: unexpected operator
Nothing to do here.
keith@thor3edgy:~$
```

---

### Post by eXSiR on 2006-09-30
Howto says:
This script is for Dapper only !!!

So Edgy may have some problems lke this...

---

### Post by testube_babies on 2006-09-30
> **eXSiR said:**
> Howto says:
This script is for Dapper only !!!

So Edgy may have some problems lke this...

Yeah...maybe I should just learn to read!!!

---

### Post by GStubbs43 on 2006-09-30
> **testube_babies said:**
> Yeah...maybe I should just learn to read!!!

hmm... It worked with no problems for me in Edgy! :D I never even changed it to /bash instead of /sh!

---

### Post by Binary Jay on 2006-10-04
To use this script in Edgy do the following:

```
$ sudo bash /usr/local/bin/restore_mozilla_icons
```

---

### Post by testube_babies on 2006-10-04
> **Binary Jay said:**
> To use this script in Edgy do the following:

```
$ sudo bash /usr/local/bin/restore_mozilla_icons
```

I was able to use it by editing the script and making it automatically change the icons regardless of user input.  But I'll try this out next time...

---

### Post by Danny Boy on 2006-10-09
Worked on Edgy fine for me with just changing the first line.

---

### Post by Aberrix on 2006-10-13
This worked perfect for me. Thanks for the write-up!

---

### Post by ilbozo on 2006-10-16
yeah worked perfectly on edgy:
just do the steps in the first post and run the script with:
$ sudo bash /usr/local/bin/restore_mozilla_icons

---

### Post by peachy on 2006-10-18
My Thunderbird is beautiful again! Thank you so much!

---

### Post by PrinceArithon on 2006-10-18
Thank you so much, my little friend is back on the screen!!!

Aaron

---

### Post by ielliott on 2006-10-18
Is there anyway to use this to change the Logo to anything?

Say if i wanted to use an ice weasel logo :)

---

### Post by andiii on 2006-10-25
Put the Iceweasel Logo in $TMPDIR and then run the commands in the script, but change the "Replace Icons" ones:
#Replace icons
cp $TMP_DIR"Iceweasel.png" usr/share/pixmaps/firefox.png

instead of 
cp $TMP_DIR"mozilla-firefox.png" /usr/share/pixmaps/firefox.png


That should work...



If anyone knows how I can do this to Iceweasel I woulb be happy to get a hint. Right now Iceweasel has no Logo in the Tasklist, just like an xterm.

I think I have to put the logo in /lib/Iceweasel or something, but that doesn't exist.

---

### Post by creatix on 2006-10-28
in edgy there are already the original firefox icons.
but the thunderbird icon is still the ugly one.

maybe someone could split up the script for firefox and thunderbird?
i am waiting for a new script in edgy.

---

### Post by Toddy on 2006-10-28
Actually, it appears that not all the firefox icons are back to the original. The menu icon is correct, but the window icon is still the blue globe as well as the icon task bar when minimized.

---

### Post by drug on 2006-11-10
Worked without a hitch in Edgy amd64 also.:) 
You can probably take off the warning that its only for Dapper

Unni

---

### Post by Sokraates on 2006-11-10
> **Toddy said:**
> Actually, it appears that not all the firefox icons are back to the original. The menu icon is correct, but the window icon is still the blue globe as well as the icon task bar when minimized.

Same here on two Edgy-machines (both are fresh installs). Maybe they changed the names?

---

### Post by static chaser on 2006-11-10
It worked fine for me on my Edgy machine.  Good post!!

---

### Post by Frederik2 on 2006-11-12
I tryed so many times to run the schript but the first command give's me an error. Please help.

sudo: gedit/usr/local/bin/restore_mozilla_icons: command not found

---

### Post by n3Cre0 on 2006-11-12
It's

sudo    gedit    /usr/local/bin/restore_mozilla_icons

Watch the spaces

---

### Post by Sam on 2006-11-12
I put a notice that the script works in Edgy. For now I have no box with Edgy, but I'll put soon a fresh script for Edgy (I need to check if all steps are ok/obsolete/missing). Thank you all for your feedback.

---

### Post by angrykeyboarder on 2006-11-17
> **drug said:**
> Worked without a hitch in Edgy amd64 also.:) 
You can probably take off the warning that its only for Dapper

Unni

This is the reason I went straight to the (then) last post in this thread. :-)

---

### Post by angrykeyboarder on 2006-11-17
I'm not sure where the Firefox icon came from, but it looks a bit jagged around the edges compared to the original (from mozilla.org).  On the other hand, the Thunderbird icon looks just fine.

I'd been meaning to mention this for a while. I first noticed it when I ran this script in Dapper and it's still true in Edgy as well.

---

### Post by JohnSilver on 2006-11-18
Worked great on my Edgy system.. Thanks!

---

### Post by n3Cre0 on 2006-11-18
Worked great here too. Thanks for the "bash" tip.

---

### Post by jpyanowski on 2006-11-22
It's a great script and I think the way you set off your examples with the $ makes it easier to copy and paste, at lease it is for me. Again, thanks. \\:D/

---

### Post by roberto73 on 2006-11-26
Once again: Nice script! ;)
The TB Icons are replaced correctly! But I see a  "default program icon" in the task bar when I start TB profile manager...

---

### Post by Y4CcduyctJL3 on 2006-11-27
you get a steamin' hot cup of ubuntu for this one!  thanks

---

### Post by adds2one on 2006-11-28
This script worked great at replacing my Firefox icons but it has also created a problem. The script causes some of my panel icons to disappear! Every time I reboot I have to put them back on the panel.

Has anyone else experienced this? Is there a fix? Can I undo this script?

---

### Post by digeratess on 2006-12-02
Thanks! Works great.

---

### Post by leeley on 2006-12-11
What a great script it works in edgy 6.10 also. Keep up the good work.

Thanks Lee:mrgreen: :p 
now if I could only edit my xorg.conf file to work better??????

---

### Post by total wormage on 2006-12-15
(obviously) this works with xubuntu / xfce as well!
except for the panel refreshing, if you run xfce-panel that is

nice script, easy to use and effective ;]]]]
:KS :KS

---

### Post by Kaladar on 2006-12-19
The script is not working for me. :( 

The address in the script is no longer valid. Does anyone have a copy of the archive or an updated address :confused:

---

### Post by ciscosurfer on 2006-12-19
> **Kaladar said:**
> The script is not working for me. :( 

The address in the script is no longer valid. Does anyone have a copy of the archive or an updated address :confused:The address looks like it is simply down right now.  Try again later in the day or tomorrow.

---

### Post by angrykeyboarder on 2006-12-20
If this becomes a permanant issue and if somebody has the tarball I'd be happy to host it on my site.

---

### Post by redDEADresolve on 2006-12-22
worked in edgy too

---

### Post by leeley on 2007-01-02
Just got to love it very well written and easy to implimnet
:mrgreen:

---

### Post by PisstMSTRCHIEF on 2007-01-06
Work great nice job man!:mrgreen:

---

### Post by kolinab on 2007-01-17
I hesitated to add a 'me too' to this thread but can't resist. It's amazing how much more I like the real icons. Somehow it makes such a nice difference! Thanks very much for the slick script.

K

---

### Post by gibbylinks on 2007-01-24
Cheers, also works in Feisty

---

### Post by Raznog on 2007-01-27
Thanks alot! i've been looking for a way to do that, was having trouble. =D

---

### Post by Catsworth on 2007-02-04
'ello :)

Thanks for all the hard work on this script, it worked an obsolute treat when it came to replacing the Thunderbird icon, unfortunately it didn't replace the Firefox icon.

Any ideas what might have gone wrong, or if it's possible to do this manually?

Thanks.

---

### Post by Catsworth on 2007-02-04
NVM, solved it :D

Thanks again :)

---

### Post by Ambimom on 2007-02-13
Thanks! worked like a charm!

---

### Post by Danny Boy on 2007-02-22
This script worked as is in Feisty, last night (Feb 21 2007)

This is one of the first scripts I run. :)

---

### Post by kolinab on 2007-04-07
I installed the Feisty beta last night - my T-bird icon in the notification area got borked (I use a minimise to tray extension). Acutally, the icon just showed up a lot smaller than it should have and accodringly, looked awful. I went out on a limb and tried the script to see if it would work on this problem too - success!

Gotta love this script. Thanks again.

---

### Post by SunshineTalia on 2007-05-16
It worked for my with Firefox, but not thunderbird. Any suggestions?

---

### Post by vtel57 on 2007-05-16
In some older versions of Ubuntu and some current other distros, the Thunderbird user directory is called *.thunderbird* instead of *.mozilla-thunderbird*. Look in your /home/Talia directory (must have Show Hidden Files activated in Nautilus) and see if your T-bird directory is *.thunderbird*. If it is, then you'll need to modify the script to substitute .thunderbird wherever it uses .mozilla-thunderbird. I had to do this on a couple of my other distros. Works fine. Just make sure you swap out ALL the ones in the script. If you miss one, it won't work. 

Have FUN! :)

---

### Post by thehawke on 2008-02-25
> **Sam said:**
> Usually all your personnal settings are stored in your home folder in dot files/directories (files starting with a dot are hidden). In a terminal list the hidden files with **ls -a** or with nautilus hit Ctrl-H. gDesklets settings are stored in ~/.gdesklets. You can safely remove this directory (ensure that gDesklets is not running) to wipe out the config. However you'll need to set up your desklets again after that. I hope it'll fix that annoyance.

THANK YOU SO MUCH! I was fighting with this all night, trying to get gdesklets to quit hanging. Deleting the folder did the trick!

---

### Post by altonbr on 2008-03-31
Just letting everyone know that I had to install Dapper on an older computer and this script still works, thank you!

---

