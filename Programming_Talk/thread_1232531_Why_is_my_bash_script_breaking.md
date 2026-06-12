---
title: "Why is my bash script breaking?"
date: 2009-08-05
forum: Programming Talk
---

### Post by starcannon on 2009-08-05
Edit:
I don't think my script may be the problem; I'm starting to think Nautilus may not be behaving. The script is modifying the values fine, or at least it appears so; for some reason Nautilus will quit toggling though.
----
I wrote this little script to park on my AWN Bar, and I'm not understanding why, but sometimes it requires a reboot in order to toggle it again. I used Geany as my text editor, the script is actually quite short and straight forward; could someone look it over and see if the problem can be diagnosed?
Thanks for looking.
```

#!/bin/bash

#       This program is free software; you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation; either version 2 of the License, or
#       (at your option) any later version.
#       
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#       
#       You should have received a copy of the GNU General Public License
#       along with this program; if not, write to the Free Software
#       Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
#       MA 02110-1301, USA.
 
#  name: Icon I/0
#  author: starcannon
#  description:
#  Tests the condition of Nautilus's show_desktop,
#  and then toggles it off or on depending upon result of test.
#  In the unlikely event that it ever fires,
#  the error message requires libnotify-bin to be installed in order to work.
#  sudo apt-get install libnotify-bin

#  ToDo: Perhaps a set of icons that display status depending on 
#  show_desktop condition. A self extracting installer that also checks
#  for required packages. Rewrite in Python using pynotify instead of 
#  libnotify, and package for use with Avant-Window-Navigator.

tf1=$(gconftool -g /apps/nautilus/preferences/show_desktop)
sdt1='gconftool -s /apps/nautilus/preferences/show_desktop -t bool true'
sdf1='gconftool -s /apps/nautilus/preferences/show_desktop -t bool false'
errmsg1="error, unable to read show_desktop status."

if [ "$tf1" = true ]; then
    $sdf1
elif [ "$tf1" = false ]; then
    $sdt1
elif [ "$tf1" != true ] && [ "$tf1" != false ]; then
    notify-send "$errmsg1"
    echo "$errmsg1"
fi

```

---

### Post by kaibob on 2009-08-05
I think this is a bug of sorts. For example, enter the following in a terminal window and the desktop icons disappear:

```
gconftool-2 -s /apps/nautilus/preferences/show_desktop -t bool false
```

Then enter the following and the desktop doesn't change:

```
gconftool-2 -s /apps/nautilus/preferences/show_desktop -t bool true
```

Then enter the following and nautilus loads and the desktop icons reappear:

```
nautilus
```

You can repeat the above except use the gconf editor and the same behavior occurs.

---

