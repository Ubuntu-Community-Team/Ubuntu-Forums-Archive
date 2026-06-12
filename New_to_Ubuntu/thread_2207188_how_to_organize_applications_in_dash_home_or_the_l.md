---
title: "how to organize applications in dash home or the launcher?"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by Katzwinkel on 2014-02-22
Hi,
I'm a little frustrated with the way applications are organized in ubuntu. 

My only way to acess them (apart from the shell or creating desktop links) is to search their direct names in "Dash Home". As I am a little unorganized and forgetful, this is rather inefficient. (Sometimes i install a special tool for an obscure task, and when i want to redo the task I forget that i already hava a tool for this)

I would very much like to be able to organize the applications into categories. And I want to have all the categories I currently assigned to be shown all the time (so that when i put all programming tools into the category "programming" I don't forget that there ever WAS a category "programming"). In the ideal case, this should work similar to the start menu in windows.

Is there a way to add folders or "drawers" to the launcher or custom categories into "dash home"?

thanks in advance

---

### Post by Dennis N on 2014-02-22
You might try Classic Menu Indicator:

[http://www.florian-diesch.de/software/classicmenu-indicator/](http://www.florian-diesch.de/software/classicmenu-indicator/)

---

### Post by grahammechanical on 2014-02-22
Super+A will launch the Dash with the Applications lens open and you can scroll down and look for an applications icon. There is also a filter feature that categorises the applications into sections which we can activate and deactivate according to our tastes.

My install of Trusty Tahr has just lost this feature but I am sure that it will return by the released ate of 14.04. So, I cannot confirm what the categories are but that feature has become much more comprehensive in Unity 7 in Trusty Tahr than it is in 12.04 or even 13.10. It will categorise the scopes and allow us to deactivate the scopes.

Regards.

---

### Post by Dennis N on 2014-02-22
> Is there a way to add folders or "drawers" to the launcher or custom categories into "dash home"?

Some users do this:

Bookmark a folder and it shows on Nautilus' right-click menu in the launcher. In this way you are adding a 'custom category' folder to the launcher. Put the things you need in the folder. Application launchers can be placed in the folder along with documents so you are spared the trouble of finding those applications you want. The folder will also pop up in the Dash when searched by name.

---

### Post by vasa1 on 2014-02-22
> **Katzwinkel said:**
> ...
Is there a way to add ... "drawers" to the launcher ...
[https://apps.ubuntu.com/cat/applications/drawers/](https://apps.ubuntu.com/cat/applications/drawers/) for just $2.99. (There's also a free version.)

---

### Post by Don_Stahl on 2014-02-22
+1 to classic menu indicator. 

```
sudo apt-add-repository ppa:diesch/testing
sudo apt-get update && sudo apt-get install classicmenu-indicator
```

I also use Cairo-Dock, which includes an applications menu on a user-configurable app dock.

But I agree with the OP: application menus are great ways to sort and display applications hierarchically.

---

### Post by david98 on 2014-02-22
I would definitely recommend classic menu indicator it saves me a little time in switching between programs cairo dock's ok but not for me.

---

### Post by Jacobonbuntu on 2014-02-23
Hi Katzwinkel, I am restrained to suggest it, but to organize my work"space" like you mention is exactly why I created the quicklisteditor. You can group applications into quicklists with a few clicks.
[https://launchpad.net/jonb.homelauncher/+download](https://launchpad.net/jonb.homelauncher/+download) (.deb)
or ppa:vlijm/qle

---

### Post by Katzwinkel on 2014-04-30
thanks, i went for classic menu indicator at the end. Works fine for me

---

### Post by divineAngel on 2014-10-04
hey, check out the app I made specifically for that. It's called [B]Unity Launcher Folders
[/B][http://unity-folders.exceptionfound.com/](http://unity-folders.exceptionfound.com/)

---

