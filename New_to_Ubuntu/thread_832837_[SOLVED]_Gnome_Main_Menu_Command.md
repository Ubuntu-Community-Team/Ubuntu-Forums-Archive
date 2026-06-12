---
title: "[SOLVED] Gnome Main Menu Command"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Daryl7352 on 2008-06-18
[]

---

### Post by _sphinx_ on 2008-06-18
To initiate main menu press Alt+F1.
To launch any application through the command press Alt+F2 and then type the name of the command.
Hope this is what you needed.

---

### Post by Daryl7352 on 2008-06-18
[]

---

### Post by iaculallad on 2008-06-18
I don't think there is a command to launch the GNOME main menu (if what you're implying are the **Applications**, **Places**, **System** menu's) as it is pre-build on **gnome-panel**. Gnome-panel hosts the menu applets.

---

### Post by Daryl7352 on 2008-06-18
[]

---

### Post by Daryl7352 on 2008-06-18
[]

---

### Post by ad_267 on 2008-06-18
What dock is it? Often the dock has an applet that is similar to the main menu. Sometimes you have to download one. If you're using AWN from the repositories I don't think it comes with a main menu and you have to use a different repository to get the menu applet.

---

### Post by Daryl7352 on 2008-06-18
[]

---

### Post by ad_267 on 2008-06-18
If I recall correctly no, you can't get a main menu in the AWN that is available form the Hardy repositories. This is how I installed AWN:

[http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

---

### Post by Daryl7352 on 2008-06-18
[]

---

### Post by ad_267 on 2008-06-18
I don't think there is a command to make the main menu come up. Maybe there is but not that I know of.

---

### Post by cdtech on 2008-06-18
alacarte

---

### Post by ad_267 on 2008-06-18
> **cdtech said:**
> alacarte

He wants a command to open the actual menu, not the menu editor.

---

### Post by cdtech on 2008-06-18
What application are you trying to open? It makes no sense what your trying to explain. Are you trying to launch an application, a desktop icon, command line?

---

### Post by Daryl7352 on 2008-06-18
[]

---

### Post by ad_267 on 2008-06-18
Apparently you can do this in Cairo dock by using the command "<Alt>F1" but I doubt this will work in AWN. You can always use the Alt+F1 keys to open a menu, but I don't know how to tie this to a launcher.

---

### Post by ad_267 on 2008-06-18
I think I might have it. Install the package xvkbd then use this command:

```
xvkbd -text "\[Alt_L]\[F1]"
```

Edit: Damn sorry, doesn't work from a launcher, only from the command line.

---

### Post by Daryl7352 on 2008-06-18
[]

---

### Post by ad_267 on 2008-06-18
Woohoo I got it to work.
Ok first you need the xautomation package:
```
sudo apt-get install xautomation
```

Now create a launcher and set it to "application in terminal"
and for the command enter:
```
xte "keydown Alt_L" "key F1" "keyup Alt_L"
```

Now remove your old menu launcher from the panel if there is one and the new launcher should work.

The only problem is a terminal window opens up for a split second but I couldn't get it to work without the application in terminal part.

---

### Post by Daryl7352 on 2008-06-18
[]

---

### Post by ad_267 on 2008-06-18
Oh sorry didn't see that haha. Yeah I can't figure out why my launchers wouldn't work as it worked from Alt-F2.

---

### Post by hariks0 on 2009-09-15
Please visit my post at

[http://ubuntuforums.org/showthread.php?p=7947781#post7947781](http://ubuntuforums.org/showthread.php?p=7947781#post7947781)

---

### Post by vlke on 2009-11-09
> **ad_267 said:**
> He wants a command to open the actual menu, not the menu editor.

Thanks, this is what I was looking for.:D

---

