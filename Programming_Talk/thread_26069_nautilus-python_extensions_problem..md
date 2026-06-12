---
title: "nautilus-python extensions problem."
date: 2005-04-11
forum: Programming Talk
---

### Post by minio on 2005-04-11
I tryied to write nautilus menu entry extension for opening files as root (as described in one post in howto section). I am newbie in python and progrmming at all and this looks like good first excersie  :smile: . But i run into problem the extension works OK, when clicked it opens correct file with correct application as root but freezes nautilus for a minute :-? . Here is the code for extension (redone openterminal extension from examples):
```
import os

import gtk
import nautilus

class OpenTerminalExtension(nautilus.MenuProvider):
    def __init__(self):
        pass
        
    def _open_terminal(self, file):
        os.system("gksudo 'gnome-open %s'" % file.get_uri())
	    
        
    def menu_activate_cb(self, menu, file):
        self._open_terminal(file)
        
       
    def get_file_items(self, window, files):
        if len(files) != 1:
            return
        
        file = files[0]
        if file.is_directory() or file.get_uri_scheme() != 'file':
            return
        
        item = nautilus.MenuItem('NautilusPython::openterminal_file_item',
                                 'Open As Root' ,
                                 'Open File %s As Root' % file.get_name())
        item.connect('activate', self.menu_activate_cb, file)
        return item,
``` 

I have no idea where is the problem. Can anyone help me please?

---

### Post by DoctorMO on 2008-09-29
Still have problems?

---

### Post by Perberos on 2008-10-03
Try to use

os.system("gksudo 'gnome-open %s' [COLOR="Red"]&[/COLOR]" % file.get_uri())

Greatings

---

