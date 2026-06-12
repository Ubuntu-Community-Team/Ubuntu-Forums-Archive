---
title: "Main menu does not work"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by roccivic on 2008-06-26
The computer gave me an error, after which the main menu doesn't work anymore for user "chc", but it is fine for user "administrator".

If I try to run "alacarte" in terminal I get the following output:
```
chc@celtichallscork-pc:/usr/bin$ alacarte
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

```

Please help.

Rouslan

---

### Post by roccivic on 2008-06-26
The errors occoured after there was no more space on "/", I cleaned up the drive and rebooted but the errors still persist.

---

### Post by drs305 on 2008-06-26
If you aren't too concerned about losing any customized menus you may have made you can uninstall and reinstall 'alacarte' in synaptic to see if this corrects the corrupted files.

You alacarte user files are in ~/.local/share/applications . You could make a backup copy of that folder for possible restoration after you have solved your problem (if this isn't the cause of the problem, of course).

---

### Post by roccivic on 2008-06-26
Removed ~/.local/share/applications, reinstalled alacarte and ubuntu-desktop, but it didn't work. alacarte still returns the same error, the main menu is still not working. Actually it is only the Applications menu that doesn't work, when I click on it nothing comes up, Places and System seem alright.

Thank you

---

### Post by drs305 on 2008-06-26
Okay, if it's just the applications menu, this should work and will create a new menu upon logging out and back in.
```

cp ~/.config/menus/application.menu ~/.config/menus/application.menu.bak
rm ~/.config/menus/application.menu
```

---

### Post by mc4man on 2008-06-26
Try going to home dir. -> .config -> menus and deleting applications.menu.
related thread
[http://ubuntuforums.org/showthread.php?p=5225710#post5225710](http://ubuntuforums.org/showthread.php?p=5225710#post5225710)

Edit: same as above but don't bother backing it up  - the file is worthless once you edit it or even try to use a backup that worked
Actually you can edit it in a limited fashion - restoring any deleted  categories won't bork it. see here
[http://ubuntuforums.org/showthread.php?p=5274332#post5274332](http://ubuntuforums.org/showthread.php?p=5274332#post5274332)

---

### Post by roccivic on 2008-06-26
Thank you guys that worked!!
For some reason I went to check in /etc/xdg/menus/applications.menu instead... What is that file for anyway if it's the one in ~/.config/menus/ that matters???

Rouslan

---

### Post by drs305 on 2008-06-26
> **roccivic said:**
> Thank you guys that worked!!
For some reason I went to check in /etc/xdg/menus/applications.menu instead... What is that file for anyway if it's the one in ~/.config/menus/ that matters???

Rouslan

Remember that ubuntu is designed to be a multiuser system. Each user has his/her own configuration files so that you can customize your setup. You removed YOUR menu, but nobody else's. In addition to user menus, there are the *system* configurations which apply to the root system setup. The file you are referencing is root's menu setup.

---

