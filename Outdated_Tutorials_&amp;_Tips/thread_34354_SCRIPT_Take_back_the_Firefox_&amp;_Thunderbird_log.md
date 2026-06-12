---
title: "SCRIPT: Take back the Firefox &amp; Thunderbird logo"
date: 2005-05-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Sam on 2005-05-14
[SIZE="3"][COLOR="Red"]**This script is for Hoary or Breezy only !!!**
To use it with **Dapper** please follow [this thread](http://ubuntuforums.org/showthread.php?t=199193) ![/COLOR][/SIZE]


**This script is based from the [HOWTO: Take back the Firefox Logo](http://ubuntuforums.org/showthread.php?t=30133) from [Sionide](http://ubuntuforums.org/member.php?u=16240).**
Also thanks to Commuto, rune and Speque for their help with Dapper.


I wrote this script because the Firefox icon is replaced with the horrible blue globe everytime Firefox is updated.
I also added the possibility to replace the Thunderbird icon and its profile manager.

[img]http://img263.echo.cx/img263/2825/windowbar6xq.png[/img]

You have the choice to replace the Firefox program icon, the Firefox document icon , the Thunderbird program icon and/or the Thunderbird profile manager icon.

[list][*]Tested with Firefox 1.0.6-0ubuntu0.1 and Thunderbird 1.0.6-0ubuntu05.04.
[*]Works in Breezy too (Firefox 1.5 and Thunderbird 1.5).
[*][COLOR="Red"]**For Dapper (Ubuntu 6.06), please see [this thread](http://ubuntuforums.org/showthread.php?t=199193) !**[/COLOR][/list]

Here we go:
[list][*]Create a new script:
```
$ sudo gedit /usr/local/bin/restore_mozilla_icons
```
[*]Paste the following lines:
```
#! /bin/sh

#
# Restore the original Firefox and/or Thunderbird icons.
#

FIREFOX_LIB="/usr/lib/mozilla-firefox/"
FIREFOX_BIN="/usr/bin/mozilla-firefox"
THUNDERBIRD_BIN="/usr/bin/mozilla-thunderbird"

ICON_PACK_URL="http://ubuntu.globalvision.ch/mozilla_icons.tar.bz2"
ICON_PACK_FILENAME="mozilla_icons.tar.bz2"
TMP_DIR="/tmp/moz-icons"$$"/"


#Ctrl-C trapping
trap ctrlc INT
ctrlc()
{
	echo -e "\nAborted by user."
	rm -rf $TMP_DIR
	exit 2
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
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
		replace_ff="1"
	fi

	#Firefox document
	echo -n "Replace the Mozilla Firefox document icon (y/n)? [y] "
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
		replace_ff_doc="1"
	fi
fi

if [ -x "$THUNDERBIRD_BIN" ] ; then
	#Thunderbird
	echo -n "Replace the Mozilla Thunderbird program icon (y/n)? [y] "
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
		replace_tb="1"
	fi

	#Thunderbird profile manager
	echo -n "Replace the Mozilla Thunderbird profile manager icon (y/n)? [y] "
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
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
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
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
	cp -f /usr/share/pixmaps/mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.old.png
	cp -f /usr/share/pixmaps/mozilla-firefox.xpm /usr/share/pixmaps/mozilla-firefox.old.xpm
	cp -f $FIREFOX_LIB"icons/default.xpm" $FIREFOX_LIB"icons/default.old.xpm"
	cp -f $FIREFOX_LIB"chrome/icons/default/default.xpm" $FIREFOX_LIB"chrome/icons/default/default.old.xpm"

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.png >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm >/dev/null
		dpkg-divert --rename $FIREFOX_LIB"icons/default.xpm" >/dev/null
		dpkg-divert --rename $FIREFOX_LIB"chrome/icons/default/default.xpm" >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-firefox.png" /usr/share/pixmaps/mozilla-firefox.png
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
		dpkg-divert --rename $FIREFOX_LIB"icons/document.png" >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-firefox-doc.png" $FIREFOX_LIB"icons/document.png"
	echo -n "."
fi


#Replace Thunderbird icon
if [ "$replace_tb" -gt "0" ] ; then
	if [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
		echo "Cannot continue (unavailable Thunderbird icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp -f /usr/share/pixmaps/mozilla-thunderbird.xpm /usr/share/pixmaps/mozilla-thunderbird.old.xpm
	cp -f /usr/share/pixmaps/mozilla-thunderbird-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-menu.old.xpm
	cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.old.xpm
	cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.old.xpm
	cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.old.xpm

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.xpm >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-menu.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm
	echo -n "."
fi


#Replace Thunderbird profile manager icon
if [ "$replace_tb_pm" -gt "0" ] ; then
	if [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
		echo "Cannot continue (unavailable Thunderbird icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp -f /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.xpm
	cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/default.old.xpm

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm
	echo -n "."
fi


echo " done !"


#Reload gnome-panel
echo -en "\nShall I reload gnome-panel to apply the changes (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	killall gnome-panel
fi


rm -rf $TMP_DIR
exit 0
```

[*]Allow execution:
```
$ sudo chmod +x /usr/local/bin/restore_mozilla_icons
```
[*]Run the script:
```
$ sudo restore_mozilla_icons
```
[*]Your icons are back ![/list]

---

### Post by spd106 on 2005-05-14
Hi 

Great script!!!

Worked like a charm :)

---

### Post by Heliode on 2005-05-14
I can confirm this also works with the backport of Firefox 1.0.3. Good job.

---

### Post by RastaMahata on 2005-05-14
if it's not much asking... I would add two things:
1. Ability to not change the document icon
2. Change the thunderbird icons :D

---

### Post by Sam on 2005-05-14
[QUOTE=RastaMahata]if it's not much asking... I would add two things:
1. Ability to not change the document icon
2. Change the thunderbird icons :D[/QUOTE]
Ok, I'll do this tomorrow !

---

### Post by Paul Atreides on 2005-05-14
After applying the script, you can also type :

```
killall gnome-panel
```

no need to logging out/logging in... 
This little additional tip permits to regenerate the panel icons...

Paul

---

### Post by Nu-Buntu on 2005-05-14
Thanks for the script. Works like a champ.

---

### Post by harryc on 2005-05-14
Nice! Thanks!

---

### Post by bored2k on 2005-05-14
Cute script ;-)

---

### Post by Ricapar on 2005-05-14
Very helpfull. I did it the manual way from the original topic, but explaining it to friends who aren't too good at following directions isn't easy.

---

### Post by Sam on 2005-05-15
Thank you guys for you positive feedback :razz:

I've updated the script:
[list][*]Possibility to replace the Thunderbird icon
[*]The script asks for which icon to replace
[*]The script asks for reloading gnome-panel[/list]


Enjoy !! :wink:

---

### Post by RastaMahata on 2005-05-15
[QUOTE=Sam]Thank you guys for you positive feedback :razz:

I've updated the script:
[list][*]Possibility to replace the Thunderbird icon
[*]The script asks for which icon to replace
[*]The script asks for reloading gnome-panel[/list]


Enjoy !! :wink:[/QUOTE]
 awesome! I Changed my icons very easily with the help of this scrpt! :D
Thanks!

---

### Post by Heliode on 2005-05-15
Thanks man, gotta love  a good script.

It also works with the backport of Thunderbird 1.0.2, in case you were wondering.

---

### Post by Sam on 2005-05-15
[QUOTE=Heliode]Thanks man, gotta love  a good script.

It also works with the backport of Thunderbird 1.0.2, in case you were wondering.[/QUOTE]
Thanks, I've added a note about this.

---

### Post by Marshalus on 2005-05-16
Exactly what I needed. Works like a charm.

NEWBIE NOTE: If you don't have imagemagick installed you'll need to. To do so, run... ```
sudo apt-get install imagemagick
```Then you will be able to run the script without problems.

---

### Post by Sam on 2005-05-16
[QUOTE=Marshalus]Exactly what I needed. Works like a charm.

NEWBIE NOTE: If you don't have imagemagick installed you'll need to. To do so, run... ```
sudo apt-get install imagemagick
```Then you will be able to run the script without problems.[/QUOTE]
Thank you for your remark. The script now installs itself imagemagick if it's not found.

---

### Post by Eproxus on 2005-05-17
Great script!

One thing, however: The icons differ from the ones specified in the manual howto? There's a black border around yours, which IMO doesn't look as good as the others. But its a minor thing...

Thanks!

---

### Post by Sam on 2005-05-17
[QUOTE=Eproxus]Great script!

One thing, however: The icons differ from the ones specified in the manual howto? There's a black border around yours, which IMO doesn't look as good as the others. But its a minor thing...

Thanks![/QUOTE]
:shock: Sounds weird... The script reproduces the steps from the manual howto and uses the same pictures. Try opening the new pictures with an image viewer and check if the border is there...

Have a look on my Firefox and Thunderbird icons in the screenshot attached.

---

### Post by ddocta on 2005-05-17
Great script.  I don't know why those icons aren't used int eh first place.

---

### Post by Eproxus on 2005-05-17
[QUOTE=Sam]Have a look on my Firefox and Thunderbird icons in the screenshot attached.[/QUOTE]

That's the same I have, but I mean the program icon. Take a look at mine. Perhaps it's due to the resizing. The manual howto lets Firefox scale the icon I believe.

---

### Post by Sam on 2005-05-17
[QUOTE=ddocta]Great script. I don't know why those icons aren't used int eh first place.[/QUOTE]
It's due to license restriction from the Mozilla Foundation which doesn't allow thoses icons to bundled into distributions.

[QUOTE=Eproxus]That's the same I have, but I mean the program icon. Take a look at mine. Perhaps it's due to the resizing. The manual howto lets Firefox scale the icon I believe.[/QUOTE]
I don't see any border exept the window border which is near the icon. It must be your theme, try changing it to see the difference.

---

### Post by Eproxus on 2005-05-17
This is what my previous icon looked like. Note the black border around yours, at the lower right.

---

### Post by Sam on 2005-05-17
Ok now I see what you meant... I thought of a square image border, not a border around the fox.

This is strange that with the manual howto it's different. Have a look on the script, it does exactly the same !

---

### Post by Eproxus on 2005-05-17
[QUOTE=Sam]Ok now I see what you meant... I thought of a square image border, not a border around the fox.

This is strange that with the manual howto it's different. Have a look on the script, it does exactly the same ![/QUOTE]
 What do you do with imagemagick? As far as I know the manual way does not use imagemagick. It justs replaces the files, even the .xpm with a .png file.

---

### Post by Sam on 2005-05-17
[QUOTE=Eproxus]What do you do with imagemagick? As far as I know the manual way does not use imagemagick. It justs replaces the files, even the .xpm with a .png file.[/QUOTE]
You're right. The imagemagick usage was somebody's comment ([here](http://ubuntuforums.org/showpost.php?p=150047&postcount=3)). If you rename a file from png to xpm, the destination file is still a png despite his name. It's a better way to convert it.

However if you still doesn't want this feature, you can replace in the script
```
convert $TMP_DIR"mozilla-firefox.png" $TMP_DIR"mozilla-firefox.xpm"
```with```
cp $TMP_DIR"mozilla-firefox.png" $TMP_DIR"mozilla-firefox.xpm"
```
and
```
convert $TMP_DIR"mozilla-thunderbird.png" $TMP_DIR"mozilla-thunderbird.xpm"
``` with ```
cp $TMP_DIR"mozilla-thunderbird.png" $TMP_DIR"mozilla-thunderbird.xpm"
```

---

### Post by Sam on 2005-05-17
I updated the script.
[list][*]Removed imagemagick usage (xpm icons already converted)
[*]Bundled icons in an archive[/list]

---

### Post by Narzuhl on 2005-05-19
All i have to say is nice!
This work great on the backports Firefox 1.0.4 as well. thanks.

---

### Post by Josh M on 2005-05-19
Worked great for me, thank you.

---

### Post by Kyral on 2005-05-19
I followed the directions, but when I go to run it, it says Command Not Found  :???:

---

### Post by Sam on 2005-05-19
Thank you for your feedback :wink:


[QUOTE=Kyral]I followed the directions, but when I go to run it, it says Command Not Found  :???:[/QUOTE]
Please precise your problem. On which step did you get the error ? What is written on the left of "command not found" ?

---

### Post by Kyral on 2005-05-19
[QUOTE=Sam]Thank you for your feedback :wink:



Please precise your problem. On which step did you get the error ? What is written on the left of "command not found" ?[/QUOTE]

It went fine until I tried to run it

[I]sudo restore_mozilla_icons Password:
sudo: restore_mozilla_icons: command not found[/I]

---

### Post by jiyuu0 on 2005-05-19
somebody suggested these to my email

I would suggest an alternate method of doing this.  Although the method on ubuntuguide.org will work fine, it will be overwritten everytime an update for firefox or thunderbird comes out.  The following method avoids that problem by using dpkg-divert to divert the original packaged files to alternate locations, avoiding the overwrite problems.

To take back Firefox:
```

wget -c http://frankandjacq.com/ubuntuguide/mozilla-firefox.png
wget -c http://frankandjacq.com/ubuntuguide/document.png
chmod 644 mozilla-firefox.png
chmod 644 document.png
sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.png
sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm
sudo dpkg-divert --rename /usr/lib/mozilla-firefox/icons/default.xpm
sudo dpkg-divert --rename /usr/lib/mozilla-firefox/icons/document.png
sudo dpkg-divert --rename /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm
sudo cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.png
sudo cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.xpm
sudo cp mozilla-firefox.png /usr/lib/mozilla-firefox/icons/default.xpm
sudo cp document.png /usr/lib/mozilla-firefox/icons/document.png
sudo cp mozilla-firefox.png /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm

```

To take back Thunderbird:
```

wget -c http://frankandjacq.com/ubuntuguide/mozilla-thunderbird.xpm
chmod 644 mozilla-thunderbird.xpm
sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.xpm
sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.xpm
sudo dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm
sudo dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm
sudo dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm
sudo cp mozilla-thunderbird.xpm /usr/share/pixmaps/mozilla-thunderbird.xpm
sudo cp mozilla-thunderbird.xpm /usr/share/pixmaps/mozilla-thunderbird-menu.xpm
sudo cp mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm
sudo cp mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm
sudo cp mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm

```

---

### Post by Sam on 2005-05-19
[QUOTE=Kyral]It went fine until I tried to run it

[I]sudo restore_mozilla_icons Password:
sudo: restore_mozilla_icons: command not found[/I][/QUOTE]
Try instead
```
$ sudo /usr/local/bin/restore_mozilla_icons
```

---

### Post by Sam on 2005-05-19
[QUOTE=jiyuu0]somebody suggested these to my email

I would suggest an alternate method of doing this.  Although the method on ubuntuguide.org will work fine, it will be overwritten everytime an update for firefox or thunderbird comes out.  The following method avoids that problem by using dpkg-divert to divert the original packaged files to alternate locations, avoiding the overwrite problems.

<snip />[/QUOTE]
Great! It's better than running this script on each update. I will update the script when I'll be less busy...

---

### Post by Kyral on 2005-05-19
[QUOTE=Sam]Try instead
```
$ sudo /usr/local/bin/restore_mozilla_icons
```[/QUOTE]

Same thing

[I]sudo /usr/local/bin/restore_mozilla_icons
Password:
sudo: /usr/local/bin/restore_mozilla_icons: command not found[/I]

---

### Post by Sam on 2005-05-19
[QUOTE=Kyral]Same thing

[I]sudo /usr/local/bin/restore_mozilla_icons
Password:
sudo: /usr/local/bin/restore_mozilla_icons: command not found[/I][/QUOTE]
Hum, you probably did a typo or put the script in the wrong place. You should try the howto again, carefully.

---

### Post by Kyral on 2005-05-19
Oops, looks like I did something wrong at the chmod part. Works now :D

---

### Post by bpilgrim1979 on 2005-05-22
this is superb! thanks!   :D 

one small thing--the Applications > Internet > Thunderbird Profile Manager still has an unusual icon.  Maybe replace that one too?

---

### Post by bpilgrim1979 on 2005-05-22
[QUOTE=Sam]Hum, you probably did a typo or put the script in the wrong place. You should try the howto again, carefully.[/QUOTE]

Yes, Kryal, ALWAYS copy and paste code like this.  Don't type it in!  Especially with root...

---

### Post by Sam on 2005-05-22
[QUOTE=jiyuu0]somebody suggested these to my email

I would suggest an alternate method of doing this.  Although the method on ubuntuguide.org will work fine, it will be overwritten everytime an update for firefox or thunderbird comes out.  The following method avoids that problem by using dpkg-divert to divert the original packaged files to alternate locations, avoiding the overwrite problems.

<snip />[/QUOTE]
The script now asks if the user wants to divert the original files.

---

### Post by Sam on 2005-05-22
[QUOTE=bpilgrim1979]this is superb! thanks!   :D 

one small thing--the Applications > Internet > Thunderbird Profile Manager still has an unusual icon.  Maybe replace that one too?[/QUOTE]
Done !

---

### Post by bpilgrim1979 on 2005-05-22
Now if I run the script again to take care of Thunderbird Profiles, will the first backups (the original Ubuntu graphics) be replaced with new backups (the replaced Mozilla icons)?

---

### Post by Sam on 2005-05-22
[QUOTE=bpilgrim1979]Now if I run the script again to take care of Thunderbird Profiles, will the first backups (the original Ubuntu graphics) be replaced with new backups (the replaced Mozilla icons)?[/QUOTE]
No, the script doesn't overwrite the backup files. You can use it many times !

---

### Post by F Cocquyt on 2005-05-23
Worked perfectly, thanks  \\:D/

---

### Post by xristos on 2005-06-07
It's great !
Thanks !

---

### Post by Pollo on 2005-06-09
Thanks it worked just like advertised !  :smile:

---

### Post by darkjedi8359 on 2005-06-09
thanks for this script, I love the default firefox icon :)

---

### Post by Kapre on 2005-06-09
DarkJedi,

This is a great one! Thanks.  :) 

Kapre

---

### Post by drewxhawaii on 2005-06-12
you are beautiful

---

### Post by trivialpackets on 2005-06-12
[QUOTE=Ricapar]Very helpfull. I did it the manual way from the original topic, but explaining it to friends who aren't too good at following directions isn't easy.[/QUOTE]
 Excellent script!  Nice work.

---

### Post by Efwis on 2005-06-15
[QUOTE=eric.proctor]Excellent script!  Nice work.[/QUOTE]
 outstanding, so much easier then the original manual way. Thanks a lot, I was looking for the original thread when i found this one.

Kudos to you

---

### Post by dkitty on 2005-06-16
I dig that you had it prompt for instructions. Very, very well done. It worked perfectly for me with Ubuntu Warty 5.04, Firefox 1.0.2, and Thunderbird 1.0.2.

---

### Post by SAMsan on 2005-06-21
Great ^^ !

+++
SAMsan.

---

### Post by easy_target on 2005-06-24
SUPER SWEET!!! Even for the king of newbies like myself! THANK YOU!!!!

---

### Post by programgeek on 2005-06-25
Great!  Worked like a charm! ^_^

---

### Post by Fexx on 2005-06-25
I got.

xxxx@xxxx:~$ sudo restore_mozilla_icons
Replace the Mozilla Firefox program icon (y/n)? [y] y
Replace the Mozilla Firefox document icon (y/n)? [y] y

Do you want to divert the original packaged files to alternate locations
(make the changes permanent) (y/n)? [y] y

Downloading and replacing icons. Please wait...cp: cannot stat `/usr/share/pixmaps/mozilla-firefox.xpm': No such file or directory
.. done !

Shall I reload gnome-panel to apply the changes (y/n)? [y] y
---

but the firefox icon changed tho, is that error to worry about?

---

### Post by Sam on 2005-06-27
Thank you everybody for your comments ! :razz:



[QUOTE=Fexx]I got.

xxxx@xxxx:~$ sudo restore_mozilla_icons
Replace the Mozilla Firefox program icon (y/n)? [y] y
Replace the Mozilla Firefox document icon (y/n)? [y] y

Do you want to divert the original packaged files to alternate locations
(make the changes permanent) (y/n)? [y] y

Downloading and replacing icons. Please wait...cp: cannot stat `/usr/share/pixmaps/mozilla-firefox.xpm': No such file or directory
.. done !

Shall I reload gnome-panel to apply the changes (y/n)? [y] y
---

but the firefox icon changed tho, is that error to worry about?[/QUOTE]
It seems that one icon was missing... The error message is provided by the backup operation.

Now it's ok you have the icon from the downloaded archive.

---

### Post by Mustard on 2005-06-27
[QUOTE=Sam]
It seems that one icon was missing... The error message is provided by the backup operation.

Now it's ok you have the icon from the downloaded archive.[/QUOTE]

Ah cool..that explains my error message too.  Thunderbird was missing an icon when installed it, which would have led to that error message when I ran your super little script. :)

---

### Post by Ken.Lank on 2005-06-27
Thanks this worked great!  I too hated the globe.  Even works with the 1.0.4 backport.

---

### Post by Caboto on 2005-06-27
I'm not sure what I've exactly done before, because your script doesn't work. :(

I've replaced the FireFox Icon in the Panel (and in the menu) with the original one, but left the icons in the taskbar to the globe...
Now, when I run you're script, everything goes on as planned. All files are replaced, but after the gnome-panel is killed, the globe is still in the taskbar and the program itself. In the menu (and the panel) are now the original one (I've replaced them with my backupped one.).
I've looked after the files which should be replaced, if there went something wrong. But everywhere is the real FireFox logo and the globe as *.distrib.
I've got a firefox.xpm in my /usr/share/pixmaps folder (which is the globe), but even if I move it somewhere else, it won't change anything.

If I launch FireFox, there is indeed the real FireFox Icon next to "Starting FireFox WebBrowser".
Seems really weird. :?


Edit: Oh yeah. The ThunderBird icon was replaced properply... Everythings okay there.

---

### Post by flamarro on 2005-06-27
Excellent, Brilliant.
I must say, hell, there's everything in this all forums that we need.
think, search and you will find it.
I'm a newbie also and it worked like a charm. Thank you.

---

### Post by jc3835 on 2005-07-01
[QUOTE=flamarro]Excellent, Brilliant.
I must say, hell, there's everything in this all forums that we need.
think, search and you will find it.
I'm a newbie also and it worked like a charm. Thank you.[/QUOTE]
 awesome job on the script... now if only thunderbird would install, i could use the script for that too, and not only firefox.
getting the following error when trying to install thunderbird via apt-get/synaptic:
       E: /var/cache/apt/archives/mozilla-thunderbird_1.0.2-1_i386.deb:  corrupted filesystem tarfile - corrupted package archive: Success

Regardless... your script is great, thanks!!

---

### Post by Fexx on 2005-07-05
Say, I wanted the default icons back. How would I do that?

I notice now when changing themes, the firefox/thunderbird wont change and stay the same.

---

### Post by codejunkie on 2005-07-05
thanks worked great.

---

### Post by rpgcyco on 2005-07-05
> Say, I wanted the default icons back. How would I do that?

In Synaptic, you could try right-clicking on the package and marking it for reinstallation.

- Rpg Cyco

---

### Post by vladuz976 on 2005-07-06
> **Sam]**This script is based from the [HOWTO: Take back the Firefox Logo](http://ubuntuforums.org/showthread.php?t=30133) from [Sionide](http://ubuntuforums.org/member.php?u=16240).**


I wrote this script because the Firefox icon is replaced with the horrible blue globe everytime Firefox is updated.
I also added the possibility to replace the Thunderbird icon and its profile manager.

[img]http://img263.echo.cx/img263/2825/windowbar6xq.png[/img]

You have the choice to replace the Firefox program icon, the Firefox document icon , the Thunderbird program icon and/or the Thunderbird profile manager icon.

Tested with Firefox 1.0.2-0ubuntu5.2 and Thunderbird 1.0.2-1, as well as the backport versions Firefox 1.0.4 and Thunderbird 1.0.2.


[list][*]Create a new script:
```
$ sudo gedit /usr/local/bin/restore_mozilla_icons
```
[*]Paste the following lines:
```
#! /bin/sh

#
# Restore the original Firefox and/or Thunderbird icons.
#

FIREFOX_BIN="/usr/bin/mozilla-firefox"
THUNDERBIRD_BIN="/usr/bin/mozilla-thunderbird"

ICON_PACK_URL="http://ubuntuforums.org/attachment.php?attachmentid=1113"

ROOT_UID="0"

TMP_DIR="/tmp/moz-icons"$$"/"


#Ctrl-C trapping
trap ctrlc INT
ctrlc()
{
	echo -e "\nAborted by user."
	rm -rf $TMP_DIR
	exit 2
}


#Check if run as root
if [ "$UID" -ne "$ROOT_UID" ]  said:**
>  ; then
	#Firefox
	echo -n "Replace the Mozilla Firefox program icon (y/n)? [y] "
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
		replace_ff="1"
	fi

	#Firefox document
	echo -n "Replace the Mozilla Firefox document icon (y/n)? [y] "
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
		replace_ff_doc="1"
	fi
fi

if [ -x "$THUNDERBIRD_BIN" ] ; then
	#Thunderbird
	echo -n "Replace the Mozilla Thunderbird program icon (y/n)? [y] "
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
		replace_tb="1"
	fi

	#Thunderbird profile manager
	echo -n "Replace the Mozilla Thunderbird profile manager icon (y/n)? [y] "
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
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
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	divert="1"
fi


#Downloading
echo -en "\nDownloading and replacing icons. Please wait..."

mkdir $TMP_DIR
wget $ICON_PACK_URL -O $TMP_DIR"mozilla_icons.tar.gz" >/dev/null 2>&1 
if [ ! -f $TMP_DIR"mozilla_icons.tar.gz" ] ; then
	echo -e "\nCannot download icons. Please check your internet connection."
	rm -rf $TMP_DIR
	exit 1
fi
tar zxf $TMP_DIR"mozilla_icons.tar.gz" -C $TMP_DIR


#Replace Firefox icon
if [ "$replace_ff" -gt "0" ] ; then
	if [ ! -f $TMP_DIR"mozilla-firefox.png" ] || [ ! -f $TMP_DIR"mozilla-firefox.xpm" ] ; then
		echo "Cannot continue (unavailable Firefox icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp --reply=no /usr/share/pixmaps/mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.old.png
	cp --reply=no /usr/share/pixmaps/mozilla-firefox.xpm /usr/share/pixmaps/mozilla-firefox.old.xpm
	cp --reply=no /usr/lib/mozilla-firefox/icons/default.xpm /usr/lib/mozilla-firefox/icons/default.old.xpm
	cp --reply=no /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm /usr/lib/mozilla-firefox/chrome/icons/default/default.old.xpm

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.png >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-firefox/icons/default.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-firefox.png" /usr/share/pixmaps/mozilla-firefox.png
	cp $TMP_DIR"mozilla-firefox.xpm" /usr/share/pixmaps/mozilla-firefox.xpm
	cp $TMP_DIR"mozilla-firefox.xpm" /usr/lib/mozilla-firefox/icons/default.xpm
	cp $TMP_DIR"mozilla-firefox.xpm" /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm
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
	cp --reply=no /usr/lib/mozilla-firefox/icons/document.png /usr/lib/mozilla-firefox/icons/document.old.png

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/lib/mozilla-firefox/icons/document.png >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-firefox-doc.png" /usr/lib/mozilla-firefox/icons/document.png
	echo -n "."
fi


#Replace Thunderbird icon
if [ "$replace_tb" -gt "0" ] ; then
	if [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
		echo "Cannot continue (unavailable Thunderbird icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp --reply=no /usr/share/pixmaps/mozilla-thunderbird.xpm /usr/share/pixmaps/mozilla-thunderbird.old.xpm
	cp --reply=no /usr/share/pixmaps/mozilla-thunderbird-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-menu.old.xpm
	cp --reply=no /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.old.xpm
	cp --reply=no /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.old.xpm
	cp --reply=no /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.old.xpm

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.xpm >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-menu.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm
	echo -n "."
fi


#Replace Thunderbird profile manager icon
if [ "$replace_tb_pm" -gt "0" ] ; then
	if [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
		echo "Cannot continue (unavailable Thunderbird icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp --reply=no /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.xpm
	cp --reply=no /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/default.old.xpm

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm
	echo -n "."
fi


echo " done !"


#Reload gnome-panel
echo -en "\nShall I reload gnome-panel to apply the changes (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	killall gnome-panel
fi


rm -rf $TMP_DIR
exit 0
```
[*]Allow execution:
```
$ sudo chmod +x /usr/local/bin/restore_mozilla_icons
```
[*]Run the script:
```
$ sudo restore_mozilla_icons
```
[*]Your icons are back ![/list]

Any comment/code improvement is welcome.
 works perfectly fine
even with 1.04

thanks a lot

---

### Post by Caboto on 2005-07-07
[QUOTE=Caboto]I'm not sure what I've exactly done before, because your script doesn't work. :(

I've replaced the FireFox Icon in the Panel (and in the menu) with the original one, but left the icons in the taskbar to the globe...
Now, when I run you're script, everything goes on as planned. All files are replaced, but after the gnome-panel is killed, the globe is still in the taskbar and the program itself. In the menu (and the panel) are now the original one (I've replaced them with my backupped one.).
I've looked after the files which should be replaced, if there went something wrong. But everywhere is the real FireFox logo and the globe as *.distrib.
I've got a firefox.xpm in my /usr/share/pixmaps folder (which is the globe), but even if I move it somewhere else, it won't change anything.

If I launch FireFox, there is indeed the real FireFox Icon next to "Starting FireFox WebBrowser".
Seems really weird. :?


Edit: Oh yeah. The ThunderBird icon was replaced properply... Everythings okay there.[/QUOTE]
Nobody? Not even an idea or hint what i could try?

---

### Post by manicka on 2005-07-07
I'll add my thanks as well.

Great script...thanks :D

---

### Post by Sam on 2005-07-07
Thank you all for your positive feedback ! ;-)


[QUOTE=Caboto]Nobody? Not even an idea or hint what i could try?[/QUOTE]
What about doing the script steps manually? Maybe there is something wrong which is not displayed when your run the script. Try this [howto](http://ubuntuforums.org/showthread.php?t=30133) as well...

---

### Post by Caboto on 2005-07-07
Nothing helped me. So I've searched the given directories and found some more globe icons, which weren't replaced.

In /usr/lib/mozilla-firefox/chrome/icons/default where some different files called main-window.xpm, mozapp.xpm and mozfile.xpm (all again with a 16 in it).
This were the files, which were shown in the taskbar and in the program itself. I don't know, what I've done wrong or what I did installed before... I think, I just installed FireFox through Synaptic and updated several times until 1.0.4.

But finally all FireFox icons are there. :)
Anyhow, Thanks for the How-To and script.

---

### Post by metalox on 2005-07-16
:)  Just to say thank you very much! Worked like a treat.
Ben, Somerset.

---

### Post by gyaresu on 2005-07-18
thank you.

---

### Post by pszilard on 2005-08-06
SAM, your'e a Legend!

I have 15  minutes experiance with Ubuntu and your script is the 1st I ever tried. It worked great. Thanks for the step-by-step instructions for newbies like me :)

-paul

---

### Post by Sam on 2005-08-06
[QUOTE=pszilard]SAM, your'e a Legend!

I have 15  minutes experiance with Ubuntu and your script is the 1st I ever tried. It worked great. Thanks for the step-by-step instructions for newbies like me :)

-paul[/QUOTE]
Thank you !

Glad to see that it functioned. The bash scripting is a great feature available in unix systems, it allows to do big things in a wink !


Enjoy Ubuntu ! :wink:

---

### Post by aroldo on 2005-08-09
It works great. Let's call it a piece of Xtreme support. Play it again, Sam.

---

### Post by +Flip on 2005-08-14
It doesn't work's at my ubuntu install, still have the same blue icon.
What went wrong? :?

---

### Post by SWE_Toblerone on 2005-08-14
Sweet, i've used Ubuntu for about three days now... Have to say i'm loving it. Hardly never use XP even though i use dualboot.

---

### Post by Sam on 2005-08-14
[QUOTE=+Flip]It doesn't work's at my ubuntu install, still have the same blue icon.
What went wrong? :?[/QUOTE]
After running the script did you reload gnome-panel ? Or did you log out then log in ?

---

### Post by Jazzyjazz on 2005-08-16
Thanks a bunch :)

---

### Post by shanghaipi on 2005-09-01
Thanks a bunch for creating this script.  It still works with 1.0.6

---

### Post by truoc444 on 2005-09-01
worked like a charm.  much better.  buh bye blue ball.

---

### Post by doobs on 2005-09-01
Hello All,

thanks for your script, it works fine.

---

### Post by groovywombat on 2005-09-04
awesome thanks

---

### Post by Sam on 2005-09-05
Thank you everybody for your feedback :wink:

---

### Post by manicka on 2005-09-06
Works just as well in breezy :)

---

### Post by duminas on 2005-09-08
Where are all the backups being dropped?
I'm a space-monger, so I'd like to nuke them.

Worked beautifully, though. :)

---

### Post by xodeus on 2005-09-09
[QUOTE=duminas]Where are all the backups being dropped?
I'm a space-monger, so I'd like to nuke them.

Worked beautifully, though. :)[/QUOTE]
 This works like a charm.

---

### Post by zoob on 2005-09-09
Awesome!  Even a newbie like me could follow it!  1 problem tho...  When I create them on the desktop in 1024x768 they are huge!  Any suggestions?

zoob

---

### Post by alinux on 2005-09-10
Cool, Thank Yuo! :razz:

---

### Post by userguy on 2005-09-14
Changing the theme to use Human icons (which are nicer, I think) caused it to invariably go back to the wrong icon. I fixed this by copying the mozilla-firefox.png file to /usr/share/icons/Human/scalable/apps replacing each of the following:

firefox.svg
mozilla.svg
mozilla-firefox.svg
mozilla-icon.svg

I don't know if all four are necessary or not, but I'm getting tired of trying to make the icon that shows up in the properties for the panel launcher match the icon on the panel (which makes sense like the Chewbacca defense).

This should be easily extended to the other icon packs for themes in the /usr/share/icons/ folders.

---

### Post by anatole on 2005-09-25
thank you very much for the script, i've done the replacement earlier, but the Thunderbird icons remained the same... i've found out the my TB, for some strange reason, uses the Thunderbird icon located in /usr/share/mozilla-thunderbird/chrome/icons/default . This is also the place for those horrible looking compose / address book / contact icons. So i asked one of my friends for the original icons, renamed and resized them and voila, the ugly icons are gone :) if someone would like to do this, here are the icons i used.
(note: default.xpm is the Sunbird icon, for the Calendar extension.)

---

### Post by aysiu on 2005-09-25
This script is awesome. I recently installed Mepis (some I'm triple-booting XP, Mepis, and Ubuntu), and the script worked in Mepis, too (well, I answered "no" to refreshing the Gnome panel)! That's amazing.

---

### Post by Dooglus on 2005-09-26
Is what you're doing legal?

I didn't think you were allowed to redistribute the mozilla icons like you're doing.

I think they want their icons only to be used on official mozilla binaries, so they can control the quality of the products which use their icons.

I'm not a lawyer, but this seems wrong to me.

---

### Post by dgold on 2005-09-27
[QUOTE=Dooglus]Is what you're doing legal?

I didn't think you were allowed to redistribute the mozilla icons like you're doing.

I think they want their icons only to be used on official mozilla binaries, so they can control the quality of the products which use their icons.[/QUOTE]

The restriction by the mozilla foundation is on the packaging of the icons with the program files. Distros routinely patch progs pre-release, especially debian-based ones like ubuntu. mozilla foundation want to protect their 'purity' so refuse to allow the icons usage in those circumstances.

[QUOTE=Dooglus]I'm not a lawyer, but this seems wrong to me.[/QUOTE]

IAAL ;) , but i'm not making this comment as anything other than a user. ISTM that the use of the logo in the script is like ricers who put back on the car-makers logo after the customization. The car is no longer truly a renault or fiat, but renault and fiat can't stop you using the logo. <2c>

---

### Post by groovywombat on 2005-09-28
awesome

---

### Post by kananga on 2005-10-03
Thanks for the script. Works great. Does anyone know why they used those other icons for Firefox and Thunderbird?

---

### Post by edurm on 2005-10-08
It DID NOT work here, Firefox 1.07 here, I got it from apt-get upgrade,

I think F.F. 1.07 is in another folder. any help ?

---

### Post by aysiu on 2005-10-08
[QUOTE=edurm]It DID NOT work here, Firefox 1.07 here, I got it from apt-get upgrade,

I think F.F. 1.07 is in another folder. any help ?[/QUOTE] I'm also using Firefox 1.0.7, and it worked just fine for me. Did it *appear* to work, or were there error messages?

---

### Post by edurm on 2005-10-08
[QUOTE=aysiu]I'm also using Firefox 1.0.7, and it worked just fine for me. Did it *appear* to work, or were there error messages?[/QUOTE]


just nothing happens


I don't have the /usr/bin/mozilla-firefox directory, I don't know Why ?


I installed the 5.04 from the DVD and I came with Fire fox 1.02

than I made two commands; apt-get update and apt-get upgrade and F.F. 1.07 was installed



By the F.F. shortcut can I track the FF executable like in windows ?

---

### Post by aysiu on 2005-10-08
> **edurm]j
I don't have the /usr/bin/mozilla-firefox directory, I don't know Why ?[/quote] Is that referenced in the script?

[quote]
I installed the 5.04 from the DVD and I came with Fire fox 1.02

than I made two commands said:**
>  Did you run the script before or after the upgrade?

[quote]
By the F.F. shortcut can I track the FF executable like in windows ? No. The command to execute Firefox is just *firefox* or *mozilla-firefox*. It doesn't need the path to the executable. Likely, it lives in /usr/bin, though.

---

### Post by edurm on 2005-10-08
>  Did you run the script before or after the upgrade?

After


>  Is that referenced in the script?

yes, also I have an application/x-shellscript of mozilla-firefox in my /usr/bin



I'm the only one that happens this kind of shit :D

---

### Post by aysiu on 2005-10-08
Hm. I just double-checked, and I have mozilla-firefox in my /usr/bin.
Does Firefox run for you? Is it actually installed and working properly?

---

### Post by BinaryDigit on 2005-10-09
Excellent script!!!

(Note for others: Also works for 64bit Breezy)

---

### Post by basketcase on 2005-10-09
Works great!!  Thanks

---

### Post by MemoryDump on 2005-11-18
getting:
Downloading and replacing icons. Please wait...cp: cannot stat `/usr/share/pixmaps/mozilla-firefox.xpm': No such file or directory
.. done !

no firefox icon for me :(

---

### Post by jbrader on 2005-11-22
Worked like a charm. Thanks a bunch.

---

### Post by Daminator on 2005-11-30
Works great, thanks!

---

### Post by maxp on 2005-12-27
[QUOTE=MemoryDump]getting:
Downloading and replacing icons. Please wait...cp: cannot stat `/usr/share/pixmaps/mozilla-firefox.xpm': No such file or directory
.. done !

no firefox icon for me :([/QUOTE]
Hey Memorydump!

I had to tweak the given script as the filename for mozilla-firefox.xpm has apparently changed to just firefox.xpm.

I just went through the script changing every instance of mozilla-firefox.xpm to simply firefox.xpm.

Worked just fine after that. Might have something to do with the fact that I'm running breezy and this is a hoary thread...dunno. I'm new to ubuntu specifically, and linux in general!

Good luck.

BTW thanks Sam for the fantastic script!

---

### Post by bejinxed on 2006-01-15
[QUOTE=MemoryDump]getting:
Downloading and replacing icons. Please wait...cp: cannot stat `/usr/share/pixmaps/mozilla-firefox.xpm': No such file or directory
.. done !

no firefox icon for me :([/QUOTE]

I just did the script without reading all the posts.. and it worked fine (kubuntu 5.10) -but- i got that same error.

Lucky me because I'd have no idea how to fix it lol.

---

### Post by Zerocool10482 on 2006-01-26
I was trying to do this for a week. Just loving Scripts. Thanks.

---

### Post by Commuto on 2006-03-14
Just wanted to testify that it also works under Dapper Testing, **minus some little tweaking**
The firefox directory changed from  /usr/lib/mozilla-firefox/ to  /usr/lib/firefox/ , so basically you have to adapt the script to this new path.
Therefore for **Dapper** the script becomes (hard Search&Replace here, nothing intellectual):
```
#! /bin/sh

#
# Restore the original Firefox and/or Thunderbird icons.
#

FIREFOX_BIN="/usr/bin/firefox"
THUNDERBIRD_BIN="/usr/bin/mozilla-thunderbird"

ICON_PACK_URL="http://ubuntuforums.org/attachment.php?attachmentid=1113"

ROOT_UID="0"

TMP_DIR="/tmp/moz-icons"$$"/"


#Ctrl-C trapping
trap ctrlc INT
ctrlc()
{
	echo -e "\nAborted by user."
	rm -rf $TMP_DIR
	exit 2
}


#Check if run as root
if [ "$UID" -ne "$ROOT_UID" ] ; then
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
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
		replace_ff="1"
	fi

	#Firefox document
	echo -n "Replace the Mozilla Firefox document icon (y/n)? [y] "
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
		replace_ff_doc="1"
	fi
fi

if [ -x "$THUNDERBIRD_BIN" ] ; then
	#Thunderbird
	echo -n "Replace the Mozilla Thunderbird program icon (y/n)? [y] "
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
		replace_tb="1"
	fi

	#Thunderbird profile manager
	echo -n "Replace the Mozilla Thunderbird profile manager icon (y/n)? [y] "
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
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
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	divert="1"
fi


#Downloading
echo -en "\nDownloading and replacing icons. Please wait..."

mkdir $TMP_DIR
wget $ICON_PACK_URL -O $TMP_DIR"mozilla_icons.tar.gz" >/dev/null 2>&1 
if [ ! -f $TMP_DIR"mozilla_icons.tar.gz" ] ; then
	echo -e "\nCannot download icons. Please check your internet connection."
	rm -rf $TMP_DIR
	exit 1
fi
tar zxf $TMP_DIR"mozilla_icons.tar.gz" -C $TMP_DIR


#Replace Firefox icon
if [ "$replace_ff" -gt "0" ] ; then
	if [ ! -f $TMP_DIR"mozilla-firefox.png" ] || [ ! -f $TMP_DIR"mozilla-firefox.xpm" ] ; then
		echo "Cannot continue (unavailable Firefox icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp --reply=no /usr/share/pixmaps/mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.old.png
	cp --reply=no /usr/share/pixmaps/mozilla-firefox.xpm /usr/share/pixmaps/mozilla-firefox.old.xpm
	cp --reply=no /usr/lib/firefox/icons/default.xpm /usr/lib/firefox/icons/default.old.xpm
	cp --reply=no /usr/lib/firefox/chrome/icons/default/default.xpm /usr/lib/firefox/chrome/icons/default/default.old.xpm

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.png >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm >/dev/null
		dpkg-divert --rename /usr/lib/firefox/icons/default.xpm >/dev/null
		dpkg-divert --rename /usr/lib/firefox/chrome/icons/default/default.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-firefox.png" /usr/share/pixmaps/mozilla-firefox.png
	cp $TMP_DIR"mozilla-firefox.xpm" /usr/share/pixmaps/mozilla-firefox.xpm
	cp $TMP_DIR"mozilla-firefox.xpm" /usr/lib/firefox/icons/default.xpm
	cp $TMP_DIR"mozilla-firefox.xpm" /usr/lib/firefox/chrome/icons/default/default.xpm
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
	cp --reply=no /usr/lib/firefox/icons/document.png /usr/lib/firefox/icons/document.old.png

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/lib/firefox/icons/document.png >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-firefox-doc.png" /usr/lib/firefox/icons/document.png
	echo -n "."
fi


#Replace Thunderbird icon
if [ "$replace_tb" -gt "0" ] ; then
	if [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
		echo "Cannot continue (unavailable Thunderbird icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp --reply=no /usr/share/pixmaps/mozilla-thunderbird.xpm /usr/share/pixmaps/mozilla-thunderbird.old.xpm
	cp --reply=no /usr/share/pixmaps/mozilla-thunderbird-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-menu.old.xpm
	cp --reply=no /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.old.xpm
	cp --reply=no /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.old.xpm
	cp --reply=no /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.old.xpm

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.xpm >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-menu.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm
	echo -n "."
fi


#Replace Thunderbird profile manager icon
if [ "$replace_tb_pm" -gt "0" ] ; then
	if [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
		echo "Cannot continue (unavailable Thunderbird icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp --reply=no /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.xpm
	cp --reply=no /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/default.old.xpm

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm
	echo -n "."
fi


echo " done !"


#Reload gnome-panel
echo -en "\nShall I reload gnome-panel to apply the changes (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	killall gnome-panel
fi


rm -rf $TMP_DIR
exit 0
```

Thanks a lot. This feature is very neat :)

---

### Post by Christopher on 2006-03-16
Very nice thank you Sam, worked great with Firefox v1.5.0.1 & Ubuntu v5.10  :-D

---

### Post by klahjn on 2006-03-16
works in Dapper.  Nice....i like the logos that mozilla offer alot better than the ones used in Ubuntu.  Thx

---

### Post by rune on 2006-03-17
Dapper complains about the use of cp --reply, 
"cp: the --reply option is deprecated; use -i or -f instead"

I guess that '--reply=no' has to be changed to '-f'

---

### Post by Danny Boy on 2006-03-22
I just figured out how to install TB 1.5. Just wanted to report the script works like a charm with Firefox and Thunderbird 1.5 in Breezy. Thanks alot! :)

---

### Post by Speque on 2006-03-25
[QUOTE=rune]Dapper complains about the use of cp --reply, 
"cp: the --reply option is deprecated; use -i or -f instead"

I guess that '--reply=no' has to be changed to '-f'[/QUOTE]

I believe, that after that it would look like this (again some search & replace, worked in Dapper without complaining about anything):

```

#! /bin/sh

#
# Restore the original Firefox and/or Thunderbird icons.
#

FIREFOX_BIN="/usr/bin/firefox"
THUNDERBIRD_BIN="/usr/bin/mozilla-thunderbird"

ICON_PACK_URL="http://ubuntuforums.org/attachment.php?attachmentid=1113"

ROOT_UID="0"

TMP_DIR="/tmp/moz-icons"$$"/"


#Ctrl-C trapping
trap ctrlc INT
ctrlc()
{
	echo -e "\nAborted by user."
	rm -rf $TMP_DIR
	exit 2
}


#Check if run as root
if [ "$UID" -ne "$ROOT_UID" ] ; then
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
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
		replace_ff="1"
	fi

	#Firefox document
	echo -n "Replace the Mozilla Firefox document icon (y/n)? [y] "
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
		replace_ff_doc="1"
	fi
fi

if [ -x "$THUNDERBIRD_BIN" ] ; then
	#Thunderbird
	echo -n "Replace the Mozilla Thunderbird program icon (y/n)? [y] "
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
		replace_tb="1"
	fi

	#Thunderbird profile manager
	echo -n "Replace the Mozilla Thunderbird profile manager icon (y/n)? [y] "
	read input
	if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
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
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	divert="1"
fi


#Downloading
echo -en "\nDownloading and replacing icons. Please wait..."

mkdir $TMP_DIR
wget $ICON_PACK_URL -O $TMP_DIR"mozilla_icons.tar.gz" >/dev/null 2>&1 
if [ ! -f $TMP_DIR"mozilla_icons.tar.gz" ] ; then
	echo -e "\nCannot download icons. Please check your internet connection."
	rm -rf $TMP_DIR
	exit 1
fi
tar zxf $TMP_DIR"mozilla_icons.tar.gz" -C $TMP_DIR


#Replace Firefox icon
if [ "$replace_ff" -gt "0" ] ; then
	if [ ! -f $TMP_DIR"mozilla-firefox.png" ] || [ ! -f $TMP_DIR"mozilla-firefox.xpm" ] ; then
		echo "Cannot continue (unavailable Firefox icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp -f /usr/share/pixmaps/mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.old.png
	cp -f /usr/share/pixmaps/mozilla-firefox.xpm /usr/share/pixmaps/mozilla-firefox.old.xpm
	cp -f /usr/lib/firefox/icons/default.xpm /usr/lib/firefox/icons/default.old.xpm
	cp -f /usr/lib/firefox/chrome/icons/default/default.xpm /usr/lib/firefox/chrome/icons/default/default.old.xpm

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.png >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm >/dev/null
		dpkg-divert --rename /usr/lib/firefox/icons/default.xpm >/dev/null
		dpkg-divert --rename /usr/lib/firefox/chrome/icons/default/default.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-firefox.png" /usr/share/pixmaps/mozilla-firefox.png
	cp $TMP_DIR"mozilla-firefox.xpm" /usr/share/pixmaps/mozilla-firefox.xpm
	cp $TMP_DIR"mozilla-firefox.xpm" /usr/lib/firefox/icons/default.xpm
	cp $TMP_DIR"mozilla-firefox.xpm" /usr/lib/firefox/chrome/icons/default/default.xpm
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
	cp -f /usr/lib/firefox/icons/document.png /usr/lib/firefox/icons/document.old.png

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/lib/firefox/icons/document.png >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-firefox-doc.png" /usr/lib/firefox/icons/document.png
	echo -n "."
fi


#Replace Thunderbird icon
if [ "$replace_tb" -gt "0" ] ; then
	if [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
		echo "Cannot continue (unavailable Thunderbird icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp -f /usr/share/pixmaps/mozilla-thunderbird.xpm /usr/share/pixmaps/mozilla-thunderbird.old.xpm
	cp -f /usr/share/pixmaps/mozilla-thunderbird-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-menu.old.xpm
	cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.old.xpm
	cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.old.xpm
	cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.old.xpm

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.xpm >/dev/null
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-menu.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm
	echo -n "."
fi


#Replace Thunderbird profile manager icon
if [ "$replace_tb_pm" -gt "0" ] ; then
	if [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
		echo "Cannot continue (unavailable Thunderbird icon file)"
		rm -rf $TMP_DIR
		exit 1
	fi

	#Backup
	cp -f /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.xpm
	cp -f /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/default.old.xpm

	#Divert
	if [ "$divert" -gt "0" ] ; then
		dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm >/dev/null
		dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm >/dev/null
	fi

	#Replace icons
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm
	cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm
	echo -n "."
fi


echo " done !"


#Reload gnome-panel
echo -en "\nShall I reload gnome-panel to apply the changes (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	killall gnome-panel
fi


rm -rf $TMP_DIR
exit 0

```

---

### Post by Sam on 2006-03-26
Thanks to everyone for your comments !

Special thanks for Commuto, rune and Speque for your contribution. I've updated the first post.

---

### Post by aysiu on 2006-04-10
[QUOTE=Speque]I believe, that after that it would look like this (again some search & replace, worked in Dapper without complaining about anything):[/QUOTE] I just dist-upgraded to Dapper today and tried this script. No joy. Is there anything you see I'm doing wrong? ```
user@ubuntu:~$ sudo kwrite /usr/local/bin/restore_mozilla_icons
Password:
ScimInputContextPlugin()
~ScimInputContextPlugin()
user@ubuntu:~$ sudo chmod +x /usr/local/bin/restore_mozilla_icons
user@ubuntu:~$ sudo restore_mozilla_icons
Replace the Mozilla Firefox program icon (y/n)? [y] y
Replace the Mozilla Firefox document icon (y/n)? [y] y
Replace the Mozilla Thunderbird program icon (y/n)? [y] y
Replace the Mozilla Thunderbird profile manager icon (y/n)? [y] y

Do you want to divert the original packaged files to alternate locations
(make the changes permanent) (y/n)? [y] y

Downloading and replacing icons. Please wait...
gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
Cannot continue (unavailable Firefox icon file)
```

---

### Post by Sam on 2006-04-10
[quote=aysiu]```
Downloading and replacing icons. Please wait...
gzip: stdin: not in gzip format
tar: Child returned status 1
```[/quote]
Yep, I just tried myself. It appears that the file is corrupted. Maybe some maintenance on the ubuntuforums server causes that. You should wait a little bit, if it doesn't work in a while I'll put a new archive and update the script.

---

### Post by aysiu on 2006-04-10
[QUOTE=Sam]Yep, I just tried myself. It appears that the file is corrupted. Maybe some maintenance on the ubuntuforums server causes that. You should wait a little bit, if it doesn't work in a while I'll put a new archive and update the script.[/QUOTE] Well, I just replaced all the icons manually, but I'm sure the updated script should work fine, at least before June 1.

---

### Post by testube_babies on 2006-04-14
[QUOTE=Sam]Yep, I just tried myself. It appears that the file is corrupted. Maybe some maintenance on the ubuntuforums server causes that. You should wait a little bit, if it doesn't work in a while I'll put a new archive and update the script.[/QUOTE]

i've been trying for a few days now and have been getting the same error.

---

### Post by akamatos on 2006-04-14
I' ve been geting the same error message as well. Could someone describe how to restore the icons manually? I can't live with that "blue-globe-thing" icon... ](*,)

---

### Post by garak on 2006-04-15
[quote=akamatos]I' ve been geting the same error message as well. Could someone describe how to restore the icons manually? I can't live with that "blue-globe-thing" icon... ](*,)[/quote] 
This is my temporary solution:

1. download the icons (in the first post)
2. copy it in a dir called "tmp" in your home dir
3. execute this script: 

```

#! /bin/sh

#
# Restore the original Firefox and/or Thunderbird icons.
#

FIREFOX_BIN="/usr/bin/firefox"
THUNDERBIRD_BIN="/usr/bin/mozilla-thunderbird"

ICON_PACK_URL="http://ubuntuforums.org/attachment.php?attachmentid=1113"

ROOT_UID="0"

TMP_DIR="./tmp/"


#Ctrl-C trapping
trap ctrlc INT
ctrlc()
{
    echo -e "\nAborted by user."
    exit 2
}


#Check if run as root
if [ "$UID" -ne "$ROOT_UID" ] ; then
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
    read input
    if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
        replace_ff="1"
    fi

    #Firefox document
    echo -n "Replace the Mozilla Firefox document icon (y/n)? [y] "
    read input
    if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
        replace_ff_doc="1"
    fi
fi

if [ -x "$THUNDERBIRD_BIN" ] ; then
    #Thunderbird
    echo -n "Replace the Mozilla Thunderbird program icon (y/n)? [y] "
    read input
    if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
        replace_tb="1"
    fi

    #Thunderbird profile manager
    echo -n "Replace the Mozilla Thunderbird profile manager icon (y/n)? [y] "
    read input
    if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
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
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
    divert="1"
fi


tar zxf $TMP_DIR"mozilla_icons.tar.gz" -C $TMP_DIR


#Replace Firefox icon
if [ "$replace_ff" -gt "0" ] ; then
    if [ ! -f $TMP_DIR"mozilla-firefox.png" ] || [ ! -f $TMP_DIR"mozilla-firefox.xpm" ] ; then
        echo "Cannot continue (unavailable Firefox icon file)"
        exit 1
    fi

    #Backup
    cp --reply=no /usr/share/pixmaps/mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.old.png
    cp --reply=no /usr/share/pixmaps/mozilla-firefox.xpm /usr/share/pixmaps/mozilla-firefox.old.xpm
    cp --reply=no /usr/lib/firefox/icons/default.xpm /usr/lib/firefox/icons/default.old.xpm
    cp --reply=no /usr/lib/firefox/chrome/icons/default/default.xpm /usr/lib/firefox/chrome/icons/default/default.old.xpm

    #Divert
    if [ "$divert" -gt "0" ] ; then
        dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.png >/dev/null
        dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm >/dev/null
        dpkg-divert --rename /usr/lib/firefox/icons/default.xpm >/dev/null
        dpkg-divert --rename /usr/lib/firefox/chrome/icons/default/default.xpm >/dev/null
    fi

    #Replace icons
    cp $TMP_DIR"mozilla-firefox.png" /usr/share/pixmaps/mozilla-firefox.png
    cp $TMP_DIR"mozilla-firefox.xpm" /usr/share/pixmaps/mozilla-firefox.xpm
    cp $TMP_DIR"mozilla-firefox.xpm" /usr/lib/firefox/icons/default.xpm
    cp $TMP_DIR"mozilla-firefox.xpm" /usr/lib/firefox/chrome/icons/default/default.xpm
    echo -n "."
fi


#Replace Firefox document icon
if [ "$replace_ff_doc" -gt "0" ] ; then
    if [ ! -f $TMP_DIR"mozilla-firefox-doc.png" ] ; then
        echo "Cannot continue (unavailable Firefox document icon file)"
        exit 1
    fi

    #Backup
    cp --reply=no /usr/lib/firefox/icons/document.png /usr/lib/firefox/icons/document.old.png

    #Divert
    if [ "$divert" -gt "0" ] ; then
        dpkg-divert --rename /usr/lib/firefox/icons/document.png >/dev/null
    fi

    #Replace icons
    cp $TMP_DIR"mozilla-firefox-doc.png" /usr/lib/firefox/icons/document.png
    echo -n "."
fi


#Replace Thunderbird icon
if [ "$replace_tb" -gt "0" ] ; then
    if [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
        echo "Cannot continue (unavailable Thunderbird icon file)"
        exit 1
    fi

    #Backup
    cp --reply=no /usr/share/pixmaps/mozilla-thunderbird.xpm /usr/share/pixmaps/mozilla-thunderbird.old.xpm
    cp --reply=no /usr/share/pixmaps/mozilla-thunderbird-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-menu.old.xpm
    cp --reply=no /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.old.xpm
    cp --reply=no /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.old.xpm
    cp --reply=no /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.old.xpm

    #Divert
    if [ "$divert" -gt "0" ] ; then
        dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.xpm >/dev/null
        dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.xpm >/dev/null
        dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm >/dev/null
        dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm >/dev/null
        dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm >/dev/null
    fi

    #Replace icons
    cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird.xpm
    cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-menu.xpm
    cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/mozilla-thunderbird.xpm
    cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow16.xpm
    cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/messengerWindow.xpm
    echo -n "."
fi


#Replace Thunderbird profile manager icon
if [ "$replace_tb_pm" -gt "0" ] ; then
    if [ ! -f $TMP_DIR"mozilla-thunderbird.xpm" ] ; then
        echo "Cannot continue (unavailable Thunderbird icon file)"
        exit 1
    fi

    #Backup
    cp --reply=no /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm /usr/share/pixmaps/mozilla-thunderbird-pm-menu.old.xpm
    cp --reply=no /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/default.old.xpm

    #Divert
    if [ "$divert" -gt "0" ] ; then
        dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm >/dev/null
        dpkg-divert --rename /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm >/dev/null
    fi

    #Replace icons
    cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/share/pixmaps/mozilla-thunderbird-pm-menu.xpm
    cp $TMP_DIR"mozilla-thunderbird.xpm" /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm
    echo -n "."
fi


echo " done !"


#Reload gnome-panel
echo -en "\nShall I reload gnome-panel to apply the changes (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
    killall gnome-panel
fi


exit 0

``` 
it's just the same script of some post above, with little modifications

---

### Post by tul on 2006-04-15
I don't know if I do it propertly, but it still doesn't work :/

---

### Post by garak on 2006-04-16
Sorry, there was a problem of cut&paste, the script was incomplete.
I edited and adjusted: try again now.

---

### Post by testube_babies on 2006-04-16
[QUOTE=garak]Sorry, there was a problem of cut&paste, the script was incomplete.
I edited and adjusted: try again now.[/QUOTE]

thanks, mate!  works like a charm.

---

### Post by akamatos on 2006-04-16
[QUOTE=garak]This is my temporary solution:

1. download the icons (in the first post)
2. copy it in a dir called "tmp" in your home dir
3. execute this script: 

...

it's just the same script of some post above, with little modifications[/QUOTE]

Yup! The fox is back. Thanks mate! :D

---

### Post by Sam on 2006-04-17
I updated the script. I've changed the URL of the downloaded icons archive and the scripts supports Dapper.

---

### Post by dreamsINdigital on 2006-04-19
Worked great, thanks Sam! :)

---

### Post by angrykeyboarder on 2006-04-28
In your mozilla_icons.tar.bz2 file there is a file named "mozilla-firefox.png".

It's now firefox.png (at least in Dapper anyway).  I had to manually change it in order to complete the change,  after running your otherwise great script.

Thunderbird is fine as is (for the time being anyway).

---

### Post by man-d on 2006-05-07
Works with breezy -> firefox 1.08 and thunderbird 1.08. 

Great post !
Great job !

Thanks

---

### Post by tribaal on 2006-05-09
You are the best!
I really hated this ugly blue gloge, but now it's all over, I have nice icons instead :)

Cheers!

- trib'

---

### Post by sciyoshi on 2006-05-10
Hi,
Good work man, but this scripts is kinda a hack... you can also use dpkg-divert so that upgrades don't overwrite the icons. Check out the Wiki page I updated:
[https://wiki.ubuntu.com/FirefoxTipsAndTricks]("https://wiki.ubuntu.com/FirefoxTipsAndTricks")

Cheers

---

### Post by Jason-X on 2006-05-21
Thank you very much. Saved me a lot of messing around.

You are a :KS

---

### Post by tribaal on 2006-05-22
The latest update (updating thunderbird to version 1.5.0.2) seems to be incompatible with this script or something: thunderbird icons in the applications menu and in my custom launcher aren't updated by the script anymore...

Anybody else experiencing such problems?

Cheers

- trib'

---

### Post by mathesis on 2006-05-22
Ubuntu (Gnome - Dapper up to date)
I experience exactely the same trouble.
It seems to occur since the last update of mozilla-thunderbird icons (ubuntu-artwork package)

EDIT : It doesn't work only for menu items (*.png files are now expected, no more *.xpm), but it works fine with window icons (window list and up-left corner icon)

---

### Post by Genican1 on 2006-05-22
Thanks a bunch.  It was annoying having to change them, and I couldn't get the one from the drop down menu to change.   K+

---

### Post by timbo1138 on 2006-05-22
Yep, confirmed that after the latest Dapper update (which included a new Thunderbird version) this script doesn't work for panel or desktop icons, but still works for the taskbar entry and the corner of the main window. Weird.

---

### Post by tribaal on 2006-05-23
Anybody came up with a workaround to this problem?

- trib'

---

### Post by groggyboy on 2006-05-23
Nice script.  But what if I wanna undo the effects of the script?  How do I get the blue globe and the envelope back?  Its just that they look so slick...

groggyboy

---

### Post by blutrane on 2006-05-28
[QUOTE=tribaal]Anybody came up with a workaround to this problem?

- trib'[/QUOTE]

I'm running Dapper here. The recent update wiped out my Thunderbird icons too. First, I tried running the script again, but that didn't fix the problem.

Next, I opened Alacarte Menu Editor, right-clicked the Thunderbird entry, selected Properties, and changed the icon there. I just used the .xpm icons that were already in "/usr/share/pixmaps". After that, Thunderbird displayed the "real" icon in the Applications menu, so I right-clicked that Thunderbird entry and selected "Add this launcher to panel". No more gnarly brown envelope in my panel.

---

### Post by Rackerz on 2006-05-29
This worked perfect for Firefox in Dapper, I don't have Thunderbird so I can't comment. 

Thankyou!

---

### Post by JimmyBEng on 2006-06-03
[QUOTE=tribaal]Anybody came up with a workaround to this problem?

- trib'[/QUOTE]

Here's what I did to correct the problem with thunderbird 1.5 on dapper.
I saved the xpm as a png, then copied it to the correct locations. The icons look correct for now. The copying code i used is below and the png is attached.  hope this helps for anyone else looking for the solution.

```
cp mozilla-thunderbird.png  /usr/share/pixmaps/mozilla-thunderbird.png
cp mozilla-thunderbird.png  /usr/share/pixmaps/mozilla-thunderbird-pm.png
cp mozilla-thunderbird.png  /usr/share/pixmaps/mozilla-thunderbird-menu.png
cp mozilla-thunderbird.png  /usr/share/pixmaps/mozilla-thunderbird-pm-menu.png
```

---

### Post by edurm on 2006-06-06
I have just run this scrip in dapper, I will restart the Pannel later than if something goes wrong I came back here, otherwise it works perfectly

---

### Post by sha_man on 2006-06-09
nice, clean, fast script. It does the job perfectly and also asks what to install! I like it very much, **THANK YOU**!

---

### Post by delfick on 2006-06-15
cool script!

one question though, is it possible to change the icon used?

because i want to use an icon i believe is better than the default ones

more specifically, one of these two...
[http://iconpacks.mozdev.org/packs/firefox2005.html](http://iconpacks.mozdev.org/packs/firefox2005.html)
[http://iconpacks.mozdev.org/packs/firefox-crystalball.html](http://iconpacks.mozdev.org/packs/firefox-crystalball.html)

thnx

---

### Post by Sam on 2006-06-15
Thanks everybody for your positive feedbacks ! ;)


[QUOTE=delfick]cool script!

one question though, is it possible to change the icon used?

because i want to use an icon i believe is better than the default ones

more specifically, one of these two...
[http://iconpacks.mozdev.org/packs/firefox2005.html](http://iconpacks.mozdev.org/packs/firefox2005.html)
[http://iconpacks.mozdev.org/packs/firefox-crystalball.html](http://iconpacks.mozdev.org/packs/firefox-crystalball.html)

thnx[/QUOTE]

Yes, with a little hack in the script (not wget'ing the file but getting it from the filesystem). But aren't these iconpacks self-installable ?

---

### Post by delfick on 2006-06-15
[QUOTE=Sam]But aren't these iconpacks self-installable ?[/QUOTE]

yes, but they don't work

When it is loading, the icon on the taskbar is the cool one from the site but after that (and i have used ur script) it returns to the original icon. :'(

---

### Post by jms830 on 2006-06-17
JimmyBEng's solution [http://ubuntuforums.org/showpost.php?p=1085704&postcount=143](http://ubuntuforums.org/showpost.php?p=1085704&postcount=143) for dapper works for all my icons except the tray/notification area icon. Anyone know where this is located so I can fix it?

---

### Post by Sam on 2006-06-19
:!: I rewrote the script for Dapper [here](http://ubuntuforums.org/showthread.php?t=199193).

---

### Post by blueidealist on 2006-07-20
Hello.  I'm a complete Newb and cannot seem to be able to run this script:
Everything goes well up to the copy/paste.
Then when it comes to entering the command to execute script, nothing happens. It seems my "terminal" isn't responding to any comands.  Opening another "terminal" and entering "sudo chmod +x /usr/local/bin/restore_mozilla_icons" I get a response "cannot access '/usr/local/bin/restore_mozilla_icons' no such file or directory".

What am I doing wrong?

Thank you,

David

---

### Post by Sam on 2006-07-21
> **blueidealist said:**
> Hello.  I'm a complete Newb and cannot seem to be able to run this script:
Everything goes well up to the copy/paste.
Then when it comes to entering the command to execute script, nothing happens. It seems my "terminal" isn't responding to any comands.  Opening another "terminal" and entering "sudo chmod +x /usr/local/bin/restore_mozilla_icons" I get a response "cannot access '/usr/local/bin/restore_mozilla_icons' no such file or directory".

What am I doing wrong?

Thank you,

David
Hi,

I think you didn't save the file after the copy/paste step. When you create a new file it isn't written to the disc until you save it.

The terminal is locked because you ran a command which is already running (in your case 'gedit'). So if you save the file, then close the text editor, your terminal will be unlocked. And you'll be able to do the next command (chmod) on the newly created file.


But beware, you're in the topic for Ubuntu Warty/Hoary. If you use Dapper (the current latest version), please use [this script](http://ubuntuforums.org/showthread.php?t=199193) !!

---

### Post by TuxCrafter on 2006-08-09
Thx for the script.
But i use xubuntu and the icons are png based here.
I run you script and it nicely changed the firefox png and other logo's but the icon package did not contain png file for thunderbird and did not replace all the logo for thunderbird in /usr/share/pixmaps. If you could change the sript to alter all the logo file also png. for firefox and thunderbird the script should also work for xununtu. Could you do this please.

Thx you

---

### Post by Sam on 2006-08-09
> **TuxCrafter said:**
> Thx for the script.
But i use xubuntu and the icons are png based here.
I run you script and it nicely changed the firefox png and other logo's but the icon package did not contain png file for thunderbird and did not replace all the logo for thunderbird in /usr/share/pixmaps. If you could change the sript to alter all the logo file also png. for firefox and thunderbird the script should also work for xununtu. Could you do this please.

Thx you
Hi,

Since I'm not using Hoary anymore, please test this for me and I'll update the script if it works. This must work if Hoary's Thunderbird uses the same files as in Dapper:
[list][*]Download the [latest icons archive](http://ubuntu.globalvision.ch/mozilla_icons_dapper.tar.bz2).
[*]Extract mozilla-thunderbird.png in your home folder.
[*]Run the following lines in a terminal (skip the second block if you don't want to divert the original icons):
```
sudo cp -f /usr/share/pixmaps/mozilla-thunderbird.png /usr/share/pixmaps/mozilla-thunderbird.old.png
sudo cp -f /usr/share/pixmaps/mozilla-thunderbird-menu.png /usr/share/pixmaps/mozilla-thunderbird-menu.old.png

sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird.png
sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-thunderbird-menu.png

sudo cp ~/mozilla-thunderbird.png /usr/share/pixmaps/mozilla-thunderbird.png
sudo cp ~/mozilla-thunderbird.png /usr/share/pixmaps/mozilla-thunderbird-menu.png
```[/list]
Please tell me if it succeed. Thanks.

---

### Post by TuxCrafter on 2006-08-10
Yes it works, I use dapper to (xubuntu 6.06).

The resolution of the thunderbird icons. Is far lower than that of firefox. Can you fix that? If you made a new finall script. I can test it on a vmware image of xubuntu.

---

### Post by Sam on 2006-08-10
> **TuxCrafter said:**
> Yes it works, I use dapper to (xubuntu 6.06).

The resolution of the thunderbird icons. Is far lower than that of firefox. Can you fix that? If you made a new finall script. I can test it on a vmware image of xubuntu.

If you use Dapper this script is outdated. The new version is [here](http://ubuntuforums.org/showthread.php?t=199193).

---

### Post by TuxCrafter on 2006-08-10
Whops i am sorry i think i opend both threads and copied from the wrong one. 

Thx you again :-$

---

### Post by Sam on 2006-08-10
> **TuxCrafter said:**
> Whops i am sorry i think i opend both threads and copied from the wrong one. 

Thx you again :-$

You're welcome ! ;)

---

### Post by kittyhawk63 on 2007-04-23
Easy instructions. Effective script. :guitar:
Thanks.
kh

---

