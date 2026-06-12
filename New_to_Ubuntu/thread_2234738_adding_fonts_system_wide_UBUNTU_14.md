---
title: "adding fonts system wide UBUNTU 14"
date: 2014-07-16
forum: New to Ubuntu
---

### Post by corey_fairbanks on 2014-07-16
Here is how to add fonts so they will be available system wide.

EXAMPLE: If you want fonts to available in Word, Inkscape, GIMP,etc. etc. then here is how...........

first know where you downloaded your fonts to,  after extacting them, !!! NOTE: ANY FONT DOWNLOADED as a .TTF need not be extracted,it is ready to go as is !!!

 1. click on [COLOR=#ff0000]_**HOME**_  [/COLOR](if  you have not do already ---at the top click on [COLOR=#ff0000]**_VIEW_**[/COLOR]  make sure   [COLOR=#ff0000]**_show hidden file_**[/COLOR] is checked.

 2. click on [COLOR=#ff0000]**_.LOCAL_**[/COLOR]

 3. click on [COLOR=#ff0000]**_SHARE_**[/COLOR]

 4.click on [COLOR=#ff0000]**_FONT --_**[/COLOR]now just paste your new fonts here.now you can use any font no matter what program you are using,if this was helpful leave a note........Thank You................

---

### Post by ajgreeny on 2014-07-16
Unless things have changed, you can just put any fonts into a hidden folder in your /home called ~/.fonts and they will be available across all applications, but only to that user.  My VM install of ubuntu 14.04 does not have a  ~/.local/share/fonts folder but having made one, I have tested it, and all fonts in that also are usable by that user alone

To make fonts available to all users on a machine you must add or copy them to a folder (best in your own chosen named folder) in /usr/share/fonts/truetype.

Eg, make a folder called myttf with ```
sudo mkdir /usr/share/fonts/truetype/myttf
``` then copy the fonts into that folder, and finally update the font cache database with ```
sudo fc-cache -f -v
```

---

