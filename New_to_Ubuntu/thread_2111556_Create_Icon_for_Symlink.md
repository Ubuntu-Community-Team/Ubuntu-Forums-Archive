---
title: "Create Icon for Symlink"
date: 2013-02-02
forum: New to Ubuntu
---

### Post by cheatos on 2013-02-02
Hi,

I have some symlinks on my desktop and to make it easier to see what is what I would like to add some images to the icons. Right now they all look the same with the code-like icon.

How can I change the icons in lubuntu?

---

### Post by ajgreeny on 2013-02-02
Right click on the icon for the symlink on your desktop and open it with leafpad.

There you will find a line **Icon=iconname**

Edit the line and  replace **iconname** with the full pathway to your chosen icon graphic file.  Save.  Done.

---

### Post by cheatos on 2013-02-02
nope, it shows the content of the target I suppose.
Here is what I get when I right click my symlink to mapl and then open with leafpad:

```

#!/bin/sh

# Copyright (c) 1993-2009 by Maplesoft, a division of Waterloo Maple Inc.
# All rights reserved. Unauthorized duplication prohibited.
# Permission is granted to modify this file to be appropriate
# for use at the installation for which Maple was purchased.

# This script runs Maple with the Java interface.
MAPLE='/usr/local/Maple'
export MAPLE 

"${MAPLE}/bin/maple" -x $*

```

---

### Post by ajgreeny on 2013-02-02
Yes, so it does.  I didn't think about that possibility, but it does make sense.

I've tried every other way I can think of, but nothing seems to work, I'm afraid.

---

### Post by cheatos on 2013-02-03
hmm, too bad.
Anybody else having an idea?
Would it be possible to first create a document on the dektop, then add the icon and then make it a symlink?
Thanks for your effort though!

---

### Post by mcduck on 2013-02-03
> **cheatos said:**
> hmm, too bad.
Anybody else having an idea?
Would it be possible to first create a document on the dektop, then add the icon and then make it a symlink?
Thanks for your effort though!

No, but what you can do it create a launcher instead of a symbolic link.

A symbolic link is a filesystem level feature, so it will always have the same appearance as the original file. A launcher on the other hand is the closest equivalent of "shortcuts" in Windows, a separate file used to launch a command or an application, giving it an icon of your chose, proper name, description, and so on.

I don't know if LXDE comes with any tool for creating launchers, but if nothing else, you can always create on by hand using a texteditor. Just create a new text file, with a ".desktop" extension. Here'aa farily simple docu,etn about .desktop files, made for gnome but theya re a common standard used between all major desktop environments so I'd assume LXDE's fle manager should also support them: [http://developer.gnome.org/integration-guide/stable/desktop-files.html.en]("http://developer.gnome.org/integration-guide/stable/desktop-files.html.en")

---

### Post by ugm6hr on 2013-02-03
Application icons are created by .desktop files
Perhaps a .desktop file can link to any file, not just an application launcher?

A quick google found: [http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/](http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/)
This has a type=Link option - worth trying?

EDIT: Sorry - left without posting for far too long! See above.

---

### Post by cheatos on 2013-02-03
Thanks alot,

I now can make a shortcut using the commands given here:
[http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/](http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/)

Also, theres a nice icon now. I'll definitely be reading the stuff you suggested, right now I've just copy-pasted it but I still want to understand the difference between my symlink and the .desktop file...

---

### Post by monkeybrain2012 on 2013-02-03
.desktop files are stored in /usr/share/applications or ~/.local/share/applications (if you have program install in home) you can just go to /usr/share/applications to open any of it with leafpad and edit it appropriately and save it under a new name (then make it executable) and you make a new one. If you store it in /usr/share/applications (or ~./local/share/applications) it will show up in the menu. You can also drag and drop it to the desktop to make a short cut.

---

### Post by monkeybrain2012 on 2013-02-03
> **ugm6hr said:**
> Application icons are created by .desktop files
Perhaps a .desktop file can link to any file, not just an application launcher?


I have made one linked to a bash script. Just need to enter the path of the script in the line Exec=

---

### Post by cheatos on 2013-02-05
well thank you monkeybrain, sounds interesting. So i just have to save a copy under the ~/.local/share/applications of my .desktop file and it will show up in this "start" menu-llike menu?
How does lubuntu determine where to put it?
I mean, I would expect maple in the office part (or maybe education, but there is none) so how can I set this?

---

### Post by deadflowr on 2013-02-05
Try adding the line Category = nameofcategory(office, internet, whatever).

Otherwise I think it puts it in a generic place, like other, or something.

---

### Post by mcduck on 2013-02-05
The "Category" entry in the .desktop file defines that.

...and here's a list of the common categories you can use: [http://standards.freedesktop.org/menu-spec/latest/apa.html]("http://standards.freedesktop.org/menu-spec/latest/apa.html")

---

### Post by cheatos on 2013-02-05
so, just out of curiosity...
I can't define new categories? That would be very "unlinux" or however you call it...

---

### Post by mcduck on 2013-02-05
> **cheatos said:**
> so, just out of curiosity...
I can't define new categories? That would be very "unlinux" or however you call it...

well, you *can* put anything you want in the category field. But the problem is that the programs (like your menus) aren't usually able to detect any random categories or able to do anything useful with them.

Having some standards most program can then support does make sense in the end.

...and the Additional Categories-list does give quite a lot of options, although I can't remember right now any program that would use them.

---

