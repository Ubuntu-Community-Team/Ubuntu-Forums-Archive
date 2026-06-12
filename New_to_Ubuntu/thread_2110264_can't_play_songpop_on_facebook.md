---
title: "can't play songpop on facebook"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by Mayasilal on 2013-01-29
hey people :)
I can not play songpop on facebook, and also can't open some web-sites for music... it says that I need to install adobe. I did, but still can't access to those pages. :/

---

### Post by Kamargov on 2014-01-06
> **Mayasilal said:**
> hey people :)
I can not play songpop on facebook, and also can't open some web-sites for music... it says that I need to install adobe. I did, but still can't access to those pages. :/

Install [FONT=Tahoma]the newer "Pepper" (PPAPI) version of the Adobe Flash Player plugin for use with the Chromium [/FONT][[FONT=inherit][COLOR=#95181C][FONT=inherit]Web browser[/FONT][/COLOR][/FONT]]("http://www.ubuntugeek.com/how-to-install-pepper-flash-for-chromium-web-browser-on-ubuntu-gnulinux.html#")
Open terminal, tem type the following lines (press enter after each one and your password after the first one)

[FONT=arial][FONT=Tahoma]sudo apt-add-repository ppa:skunk/pepper-flash[/FONT]
[FONT=Tahoma]sudo apt-get update[/FONT]
[FONT=Tahoma]sudo apt-get install pepflashplugin-installer[/FONT]
[/FONT]
[FONT=arial][FONT=Tahoma]
[/FONT][/FONT]
[FONT=arial]Once installed, there's** one more step** to get Chromium to use the Google Chrome Pepper Flash Player: you need to open */etc/chromium-browser/default* as root with a text editor (e.g.: gedit - which I'll use in the command below on Terminal):
sudo apt-get install gksu #it`s not installed by default in Ubuntu 13.04
gksu gksu gedit /etc/chromium-browser/default("gksu" is used twice to avoid a bug with Gedit opening a blank file next to our file) 

and in that file, **paste the following line at the bottom of the file** (after the CHROMIUM_FLAGS="" line):
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh(yes, there's a dot in the beginning of the line, then a space!)[/FONT]

---

