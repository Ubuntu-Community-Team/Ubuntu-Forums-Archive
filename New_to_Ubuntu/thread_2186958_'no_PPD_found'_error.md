---
title: "'no PPD found' error"
date: 2013-11-10
forum: New to Ubuntu
---

### Post by krisli_hyland on 2013-11-10
I am trying to get an older printer hooked up. (HP PSC 1610) it is supported.  It is recognized, but when I try to finish installing it says "no PPD found."

ater uninstalling HPLIP from the ubuntu software center I tried reinstalling 
It now sees a PPD but I have a different issue:
error: Failed to find the lsusb command

---

### Post by krisli_hyland on 2013-11-10
Uninstalled the HPLIP 3.13.11, and tried RE-re-installing.
New error is that CUPS is not installed.  I apt-get cups and try again.  Same error.
  I try to apt-get cups again, says I have the current version. 
 How can I make HPLIP 3.13.11 understand that I DO have CUPS?

grrrrrr.

***solved,* **the answer to the CUPS not installed error was to run this***

sudo cupsd

apparently this turns CUPS on so HPLIP  will see it.

the printer seems to have installed, and tries to print test page but fails because

now I have [COLOR=#333333][FONT=Ubuntu]error:** Failed to find the lsusb command.**
[/FONT][/COLOR]

---

### Post by oldfred on 2013-11-11
I have a newer HP printer and found the version in the repository was old. So I downloaded the one from HP directly. It also has some prerequisites to resolve but seems to work well.

HP Deskjet 3520
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

---

### Post by krisli_hyland on 2013-11-14
I have the newest HPLIP from HP, not the software centre.  T[COLOR=#000000]he printer seems to have installed, and tries to print test page but fails because[/COLOR]
[COLOR=#000000]
 [/COLOR][COLOR=#333333][FONT=Ubuntu]error:** Failed to find the lsusb command.**[/FONT][/COLOR]

---

### Post by oldfred on 2013-11-15
run 
lsusb
Then plug printer in/turn it on and rerun it to see change
lsusb
does it show printer on USB port?

---

