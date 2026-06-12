---
title: "Issue with a game that may be solved through bash scripting"
date: 2007-06-30
forum: Programming Talk
---

### Post by brennydoogles on 2007-06-30
I have a script running at my system startup that changes my desktop background every 3 minutes. I love it, and I don't want to get rid of it. However, whenever I am running the game Tremulous, this script causes the game to go out of fullscreen (also causing me to have to restart X). The script that strats up looks like this:
```
#!/bin/bash
while true
do
   python /home/brendon/bin/change-background.py
   sleep 180
done
```

and the python program it runs looks like this:
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

backgrounds = "images/backgrounds"

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

Ok, so my real question is... could I add something to either of these programs to have it check if Tremulous is running, and hibernate until the next iteration (and then check again)?? Thanks for all of your help!!!

---

### Post by meatpan on 2007-06-30
Here is an idea:

Check to see if tremulous is running by parsing the output of 'ps -x'.  For example the command series, 'ps -x | grep tremulous' will return 0 if tremulous is running, and 1 if it isn't .You can check the return value of a previous command by inspecting the $? variable (i.e. 'echo $?'). 

Now you can add a conditional statement based on the return value.

Here's a shot:

```

while true
do
   ps -x | grep tremulous >& /dev/null # some redirection here to keep the screen clean
   if [ $? -ne 0 ]; then
      python /home/brendon/bin/change-background.py
   fi
   sleep 180
done

```

---

### Post by brennydoogles on 2007-06-30
well, unfortunately it didn't work. It did stop the script from running while Tremulous was going, but it did not stop tremulous from crashing. Any ideas??

---

