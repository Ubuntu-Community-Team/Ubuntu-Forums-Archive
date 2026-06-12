---
title: "[Python] Start application on StartUP?"
date: 2009-11-03
forum: Programming Talk
---

### Post by baskar007 on 2009-11-03
I have designed an downloader application in python.
i need to start my application automatically when system starts.
how to do?

---

### Post by Barriehie on 2009-11-03
See the man page for ***update-rc.d*** for adding init scripts.

Barrie

---

### Post by 0cton on 2009-11-03
Preferences-> Sessions

---

### Post by baskar007 on 2009-11-04
No no no, I want to set it via my python code. not manually via session.

application setting have a option for auto start. if the user set it to yes, python code will edit some system files something like (Barriehie said) "update-rc.d" and set it to automatically.

my question is which file i want to edit?

---

### Post by Barriehie on 2009-11-04
> **baskar007 said:**
> No no no, I want to set it via my python code. not manually via session.

application setting have a option for auto start. if the user set it to yes, python code will edit some system files something like (Barriehie said) "update-rc.d" and set it to automatically.

my question is which file i want to edit?

#
#
#
               Never mind this post!  See the next one.
#
#
#

So, the user tells the python code that they want program X to start automatically?  If so the python code will have to generate a script and put it in **/etc/init.d/<some script name>** and then run update-rc.d with whatever command line arguments.  That's the only way I know of to do it.  Probably some guru's on here know another way but that's it for me!

Barrie

Edit: This might help. [http://ubuntuforums.org/showthread.php?t=40680](http://ubuntuforums.org/showthread.php?t=40680)

---

### Post by Barriehie on 2009-11-04
I think I found it.  See this post. [http://ubuntuforums.org/showthread.php?t=331406](http://ubuntuforums.org/showthread.php?t=331406)  I looked in my ~/.config/autostart and there are launchers in there just like my startup session.  These launchers are plain jain .desktop files.  File specifications can be found [here](http://standards.freedesktop.org/desktop-entry-spec/latest/index.html).

The files in /etc/xdg/autostart appear to be system wide autostarts.

For Sunbird:
```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=No Name
Type=Application
Name[en_US]=Sunbird
Exec=/usr/bin/sunbird
X-GNOME-Autostart-enabled=false
Comment[en_US]=Calendar
Comment=Calendar
GenericName[en_US]=

```

---

### Post by baskar007 on 2009-11-04
> **Barriehie said:**
> I think I found it.  See this post. [http://ubuntuforums.org/showthread.php?t=331406](http://ubuntuforums.org/showthread.php?t=331406)  I looked in my ~/.config/autostart and there are launchers in there just like my startup session.  These launchers are plain jain .desktop files.  File specifications can be found [here](http://standards.freedesktop.org/desktop-entry-spec/latest/index.html).

The files in /etc/xdg/autostart appear to be system wide autostarts.

For Sunbird:
```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=No Name
Type=Application
Name[en_US]=Sunbird
Exec=/usr/bin/sunbird
X-GNOME-Autostart-enabled=false
Comment[en_US]=Calendar
Comment=Calendar
GenericName[en_US]=

```
this what i want.
thank you Barriehie. thank you very much.

---

### Post by Barriehie on 2009-11-04
:)

---

