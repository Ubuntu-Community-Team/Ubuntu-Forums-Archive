---
title: "Can't edit menus...problems...again..."
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Jackfrost123 on 2008-07-12
I edited out all the applications from the menus in the top panel just to try it out. (I was ticking in btw programming and educational categories but didn't see anything appear initially). And now I am trying of course to edit them back in but the control won't launch. Tried it from a terminal and got the following errors:

"sudo alacarte
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
"

Huh? (BTW only places and system appear, apps don't)

:guitar:

---

### Post by iaculallad on 2008-07-12
What about:

Right click on your top panel and select "Add to Panel", select "Main Menu" from Utilities and click on "Add".

---

### Post by Jackfrost123 on 2008-07-12
hey iac, I 've done that already, took it out (whole of the menu) and reput it by adding but the apps menu did not re-appear, it stayed as it was...sigh...

---

### Post by iaculallad on 2008-07-12
> **Jackfrost123 said:**
> hey iac, I 've done that already, took it out (whole of the menu) and reput it by adding but the apps menu did not re-appear, it stayed as it was...sigh...

On your terminal, type in the 3 commands:

```
gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &
```

---

### Post by Jackfrost123 on 2008-07-13
hey iac,

I tried but it didn't work, It got the menus out then I rebooted and they were back, but my launcher icons had changed to the default. Unfortunately the applications menu hadn't changed to default and so it was not there, just applications label was there that is not the menu.

ANY IDEAS GUYS GALS?

p.s. STILL WHEN I RIGHT CLICK AND CHOOSE EDIT MENU THE HDD SHOWS SOME ACTION BUT NOTHING HAPPENS AFTERWARDS.

---

### Post by Jackfrost123 on 2008-07-13
Bump

---

### Post by nowshining on 2008-07-13
try
```

sudo chown -R username:username /home/username/
```

this resets all ur home items to be owned by u. :)

---

### Post by RomeReactor on 2008-07-13
Hi. You could try the solution [posted here]("http://www.oddmint.com/blog/2008/05/24/how-to-reset-the-applications-menu-in-gnome/"); basically, move or rename the **applications.menu** and **settings.menu** files:
```
mv ~/.config/menus/applications.menu ~/.config/menus/applications.menu.backup
```
and:
```
mv ~/.config/menus/settings.menu ~/.config/menus/settings.menu.backup
```
Then log out, log back in, and see if that fixes it.

If, for any reason, you want to revert these changes, you can restore the backups you just made:
```
mv ~/.config/menus/applications.menu.backup ~/.config/menus/applications.menu
```
and:
```
mv ~/.config/menus/settings.menu.backup ~/.config/menus/settings.menu
```

---

### Post by Jackfrost123 on 2008-07-14
@nowshinning

Hey bro, thanks for the help, but here's what I get: chown: cannot access `/home/username/.gvfs': Permission denied


@romereactor

thanks buddy, just giving your help a go.

---

### Post by Jackfrost123 on 2008-07-14
HEY ROME BUDDY!

GREAT GOT IT FIXED!!! THANKS A BUNDLE!!

just a quick question, when I edit the menus and add programming and education categories nothing shows up, is this because maybe I don't have anything in these categories? (i am not sure If I do or dont)

---

### Post by BGFG on 2008-07-14
Interested, did the last fix work ?

---

### Post by RomeReactor on 2008-07-14
> **Jackfrost123 said:**
> just a quick question, when I edit the menus and add programming and education categories nothing shows up, is this because maybe I don't have anything in these categories? (i am not sure If I do or dont)

As far as I know, you can check any sub-menus in the 'Applications' menu, but if they're empty they won't actually show up until at least one application makes an entry there. Try editing the menus now and see if there's at least one app in either the 'Programming' or 'Education' sub-menus.

If you already had application entries there, try looking in the 'Other' sub-menu; if there are launchers there that you're sure belong in another category, you can drag and drop the launchers to where they belong.

---

### Post by Jackfrost123 on 2008-07-14
hey bg buddy, yeah it did.

@Rome, great help pal, much appreciated.

---

### Post by nowshining on 2008-07-14
"chown: cannot access `/home/username/.gvfs': Permission denied"

i get that too, it's normal. :)

---

### Post by AlexanderDGreat on 2010-07-05
Yes Rome fixed it, I did sudo chown -R mine:mine ~/.config/menus in Lucid Lynx. Thanks.

---

