---
title: "downgrade firefox"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by neil_1 on 2012-02-05
how do i downgrade my firefox from 10 to 9 ?
i'm having trouble with 10 as it is not supported by my schools learning platform
and i do not want to use a vm to check my mail and for homework :(

---

### Post by WthIteh on 2012-02-05
Indeed there is no direct solution for downgrading ;)
As a workaround you can remove your firefox and then install firefox 9 again.

---

### Post by Carborundum on 2012-02-05
In what way is Firefox 10 not supported by your school's learning platform? Does something actually break when you try to use it with Firefox 10, or do you just get a message telling you that it's not supported? If it's the latter, can you simply choose to ignore it, or does it refuse to let you pass?

---

### Post by pqwoerituytrueiwoq on 2012-02-05
use the user agent switcher addon 
odds are that web site assumes browser version will never exceed 9

if you must use firefox 9 this script will install it  save it as a [FONT=Courier New].sh[/FONT] file and[FONT=Courier New] chmod +x[/FONT] it
this script works with nearly any version of Firefox just edit the version number atm it will install 2.0.0.20, 3.6.24, 3.6.25, 3.6.26, 8.0.1, 9.0.1, or 10.0
do NOT run as root
```
#!/bin/sh
VER="9.0.1"
LOCAL=$(echo $LANG | awk '{ print substr( $0, 0, index($0,".")-1 ) }')
LOCAL=$(echo $LOCAL | awk '{ sub( /\_/, "-", $0); print }')
cd $HOME
if [ ! `ls firefox-$VER.tar.bz2` ]; then # allows manual download
    wget "http://releases.mozilla.org/pub/mozilla.org/firefox/releases/$VER/linux-`uname -m`/$LOCAL/firefox-$VER.tar.bz2"
fi
if [ ! `ls firefox-$VER.tar.bz2` ]; then # make sure firefox if there to install
    echo "Failed to download firefox"
    echo "This is probally due to mozilla not offering firefox in $LOCAL"
    echo "Please download firefox $VER to your $HOME folder then run this script again"
    echo "http://releases.mozilla.org/pub/mozilla.org/firefox/releases/$VER/linux-`uname -m`/"
    exit 1
fi
tar -jxvf firefox-$VER.tar.bz2
mv firefox .firefox
rm firefox-$VER.tar.bz2
chmod +x .firefox/firefox
echo "[Desktop Entry]" > Desktop/Firefox.desktop
echo "Categories=;" >> Desktop/Firefox.desktop
echo "Comment=Browse the World Wide Web" >> Desktop/Firefox.desktop
echo "Comment[en_US]=Browse the World Wide Web" >> Desktop/Firefox.desktop
echo "Exec=$HOME/.firefox/firefox %u" >> Desktop/Firefox.desktop
echo "Hidden=false" >> Desktop/Firefox.desktop
echo "Icon=firefox" >> Desktop/Firefox.desktop
echo "Name=Mozilla Firefox $VER" >> Desktop/Firefox.desktop
echo "Terminal=false" >> Desktop/Firefox.desktop
echo "Type=Application" >> Desktop/Firefox.desktop
echo "Version=1.0" >> Desktop/Firefox.desktop
chmod +x Desktop/Firefox.desktop
zenity --info --text "Please update Firefox icons to point to:\n$HOME/.firefox/firefox"
if [ $(zenity --question --title="Open Firefox?" --text "Would you like to start using Firefox $VER now\nThis will close Firefox first by killing it's process"; echo $?) = "0" ]; then
    killall firefox-bin
    .firefox/firefox
fi
exit 0
```

---

### Post by Frogs Hair on 2012-02-05
If you have the synaptic package manager the older version may still be listed and you can mark for installation . If if is not you will have to locate the  package install manually. I only see 10 and 13 but I use Nightly which is 13.0a1 and don't have any other versions installed .

[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/9.0.1/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/9.0.1/)

---

### Post by neil_1 on 2012-02-05
> **WthIteh said:**
> Indeed there is no direct solution for downgrading ;)
As a workaround you can remove your firefox and then install firefox 9 again.
:(
> **Carborundum said:**
> In what way is Firefox 10 not supported by your school's learning platform? Does something actually break when you try to use it with Firefox 10, or do you just get a message telling you that it's not supported? If it's the latter, can you simply choose to ignore it, or does it refuse to let you pass?
after login it shows a blank oage or it gets stuck at login
> **pqwoerituytrueiwoq said:**
> use the user agent switcher addon

if you must use firefox 9 this script will install it  save it as a [FONT=Courier New].sh[/FONT] file and[FONT=Courier New] chmod +x[/FONT] it
this script works with nearly any version of Firefox just edit the version number atm it will install 2.0.0.20, 3.6.24, 3.6.25, 3.6.26, 8.0.1, 9.0.1, and 10.0

will it remove 10 ?
i have some stuff saved on it
> **Frogs Hair said:**
> If you have the synaptic package manager the older version may still be listed and you can mark for installation . If if is not you will have to locate the  package install manually. I only see 10 and 13 but I use Nightly which is 13.0a1 and don't have any other versions installed .

[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/9.0.1/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/9.0.1/)
synaptic doesnt show 9, only 10

---

### Post by pqwoerituytrueiwoq on 2012-02-05
ff 10 will remain as it is  it does not replace ff10
if you decide to remove ff9 just run [FONT=Courier New]rm -rf ~/.firefox[/FONT]

yuo may want to run a separate profile ([FONT=Courier New]firefox -P[/FONT]) is you were to use very different versions of firefox but 9.0.1 and 10.0 should not hurt yuor profile switching back and forth but that is not very good practice

---

### Post by neil_1 on 2012-02-05
> **pqwoerituytrueiwoq said:**
> ff 10 will remain as it is  it does not replace ff10
if you decide to remove ff9 just run [FONT=Courier New]rm -rf ~/.firefox[/FONT]

yuo may want to run a separate profile ([FONT=Courier New]firefox -P[/FONT]) is you were to use very different versions of firefox but 9.0.1 and 10.0 should not hurt yuor profile switching back and forth but that is not very good practice
how do i run a different profile ?
sorry, i'm new to linux :(

---

### Post by lovinglinux on 2012-02-05
> **neil_1 said:**
> how do i run a different profile ?
sorry, i'm new to linux :(

Launch a  terminal and run the following code to access the profile manager.

```
firefox -P
```

You must close Firefox first.

If you want to use multiple profiles at the same time, then use the -no-remote option.

```
firefox -P -no-remote
```

---

### Post by neil_1 on 2012-02-05
@[pqwoerituytrueiwoq]("http://ubuntuforums.org/member.php?u=865458")
thanks! it works!

@[[COLOR=#d40000]**lovinglinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=649167")
but that only works for v10 
or do i have to switch it first and then use v9 and then before i use v10 i switch it back again ?

edit:
i got it to work, thanks guys!

---

### Post by lovinglinux on 2012-02-05
> **neil_1 said:**
> @[[COLOR=#d40000]**lovinglinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=649167")
but that only works for v10 
or do i have to switch it first and then use v9 and then before i use v10 i switch it back again ?

If you want to use multiple Firefox versions, then use the full path. For example:

```
/opt/firefox/firefox -P -no-remote
```

However, you cannot launch two versions of Firefox using the same profile.

---

### Post by neil_1 on 2012-05-03
just an addition,
seamonkey is an older version of firefox that we can install alongside ff10 or whatever the latest update is

---

