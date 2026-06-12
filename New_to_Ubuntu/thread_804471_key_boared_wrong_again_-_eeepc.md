---
title: "key boared wrong again - eeepc"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by trigsenior on 2008-05-23
hello , as you can probaly see from my title I'm having key board troubles =( 

this is not the first time this has happed , last time i added a fire fox 
add on and it broke this time i think it was because I updated.

Last time the problem seemed to go away by it self but this time it here to stay . 

 i used this thread for help [http://ubuntuforums.org/showthread.php?t=798555]("http://ubuntuforums.org/showthread.php?t=798555") i edit /etc/X11/xorg.conf because on preferences > key board everything seemed right.


I seem to have a number pad now on my key board now. here are my settings.


# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
        Identifier      "Generic Keyboard" 
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"

^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell


i have a french key board , laptop , assus , eeepc 

do these setting look right ?

---

### Post by trigsenior on 2008-05-23
found the problem this 


Option "XkbRules"

should be

Option "CoreKeyboard"

still does not explain why it changes oh well another mystery of life ;)

---

