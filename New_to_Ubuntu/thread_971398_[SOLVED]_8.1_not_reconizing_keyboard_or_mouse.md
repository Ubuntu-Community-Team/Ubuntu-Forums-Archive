---
title: "[SOLVED] 8.1 not reconizing keyboard or mouse"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by fattymatty on 2008-11-04
I wiped my hdd and installed 8.10 and went thru and works good except i cant get to reconize keyboard. I've tried editing xorg.conf file but that came back as error so deleted that. did the console reconfigure of keyboard but to no avail and also today tried sudo apt-get install xserver-xorg-input-all but it said it was all ready upto date. any ideas

Matt

PS Also have tried ms curve keyboard and ms usb mouse as well. currently using compaq ps/2 keyboard and usb ms laser 6000

I launched Live cd and used that to connect to my linux partition and edited it thru the terminal with nano function but when i added

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

but this cameup with an error and wouldnt load so i removed it
also the keyboard works if i go into recovery

the keyboard is ps/2

mouse and keyboard work in live cd
fattymatty is online now Report Post   	Edit/Delete Message

---

### Post by bscbrit on 2008-11-05
The thread is marked as SOLVED but I cannot see any indication of how you solved it, or am I misreading something?.  Care to share your good fortune and knowledge with us as others might have a similar problem? :-)

---

