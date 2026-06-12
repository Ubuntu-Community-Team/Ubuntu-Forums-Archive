---
title: "HOW-TO : Randomize Gnome 2 Wallpaper"
date: 2006-05-31
forum: Outdated Tutorials &amp; Tips
---

### Post by llebegue on 2006-05-31
I couldn't make up my mind about what would be my wallpaper ...

So I wrote a small script to choose randomly from my collection.

Pre-requesites are :
- using Linux or another Unix flavor (well Ubuntu here ...)
- using Gnome 2
- Using the standard desktop configurator (gnome-background-properties) as a reference file.

What the script does :

1- look the Gnome background configuration file
2- pick-up a random image from gnome-configuration-properties (excluding images that are not in my home directory 'grep $HOME'  but this is my personal choice)
3- tell Gnome to change the background
4- wait for 5 minutes and change the background randomly again

----------------------------------------------------------------------------
```

#!/bin/bash

while [ 1 == 1 ]
do
ALIST=( `grep filename ~/.gnome2/backgrounds.xml | sed 's/<filename>//g' | sed 's/<\/filename>//g' | grep $HOME` )
RANGE=${#ALIST[@]}
let "number = $RANDOM % $RANGE"
gconftool-2 -t string -s /desktop/gnome/background/picture_filename ${ALIST[$number]}
sleep 300
done

```
----------------------------------------------------------------------------

Save this file with a relevant name (background.sh for instance) with execution rights (chmod u+x background.sh)

I wrote it on Ubuntu Dapper Beta ... but should work on previous version with Gnome 2

How to run it :

- open a terminal and run '/xxx/xx/xx/background.sh &'   ... & is important to detach this process from the terminal one
- exit the terminal
or
- System -> Preferences -> Sessions 
- Startup Program Tab => Add
- Type the command line like above and validate
- The  next time you open a session the background will be chosen randomly


et voilà !

**Tested on Ubuntu 6.06 ... works perfectly**


PS thanks to poptones for the original script [on this thread]("http://www.ubuntuforums.org/showthread.php?t=49336")

---

### Post by markymarknz on 2006-06-01
Hi I would love to get this going, and thanks for the work but I get the following error when I try to run it:

./background.sh: line 5: syntax error near unexpected token `('
./background.sh: line 5: `ALIST= ( `grep filename ~/.gnome2/backgrounds.xml | sed 's/<filename>//g' | sed 's/<\/filename>//g' | grep $HOME\Backgrounds` )'

Apart from specifying $HOME\Backgrounds I have just copied and pasted.

---

### Post by llebegue on 2006-06-02
Yes quit normal I posted it on a forum where it transformed "=" and "(" to a smiley ....

=(

You only need to remove the space between those two :)

---

### Post by thomashauk on 2006-06-02
It still kicks out with the same error

---

### Post by llebegue on 2006-06-02
Copy-past your file here please. I'll check it (or better put it as an attachment)

I paste mine here again :
```

#!/bin/bash

while [ 1 == 1 ]
do
ALIST=( `grep filename ~/.gnome2/backgrounds.xml | sed 's/<filename>//g' | sed 's/<\/filename>//g' | grep $HOME` )
RANGE=${#ALIST[@]}
let "number = $RANDOM % $RANGE"
gconftool-2 -t string -s /desktop/gnome/background/picture_filename ${ALIST[$number]}
sleep 300
done

```

---

### Post by crazygerad on 2006-06-05
Could you please tell me how to do it but addin a folder, I have one called My Pictures and I would like it to randomly choose a background from there.

---

### Post by henriquemaia on 2006-06-05
[quote=crazygerad]Could you please tell me how to do it but addin a folder, I have one called My Pictures and I would like it to randomly choose a background from there.[/quote]

I found a script once that I use with conjuction with cron. 

You can use it to randomize backgrounds from a pictures folder.

```
#!/usr/bin/python
#
# change-background.py
#
# A script to change to a random background image
#
# (c) 2004, Davyd Madeley <davyd@madeley.id.au>
#
#   This program is free software; you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation; either version 2, or (at your option)
#   any later version.
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with this program; if not, write to the Free Software Foundation,
#   Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
#

backgrounds = "/put/your/pictures/folder/path/here"

import gconf
import os
import random
import mimetypes

class GConfClient:
        def __init__ (self):
                self.__client__ = gconf.client_get_default ()
        def get_background (self):
                return self.__client__.get_string ("/desktop/gnome/background/picture_filename")
        def set_background (self, background):
                self.__client__.set_string ("/desktop/gnome/background/picture_filename", background)

client = GConfClient ()


dir_items = os.listdir (os.path.join (os.environ["HOME"], backgrounds))
items = []

for item in dir_items:
        mimetype = mimetypes.guess_type (item)[0]
        if mimetype and mimetype.split ('/')[0] == "image":
                items.append (item)

item = random.randint (0, len (items) - 1)
current_bg = client.get_background ()

while (items[item] == current_bg):
        item = random.randint (0, len (items) - 1)

client.set_background (os.path.join (os.environ["HOME"], backgrounds, items[item]))

```

---

### Post by crazygerad on 2006-06-05
Thank you, it works perfectly.

---

### Post by KillerKiwi on 2006-06-05
In case "cron" gives you a nose bleed try gnome-scheduler to register jobs

---

