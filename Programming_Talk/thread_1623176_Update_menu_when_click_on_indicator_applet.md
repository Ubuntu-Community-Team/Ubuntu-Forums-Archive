---
title: "Update menu when click on indicator applet"
date: 2010-11-16
forum: Programming Talk
---

### Post by xisco.rib on 2010-11-16
Hello folks,

I'm developing an application with python which has an icon in the indicator applet.
I've used this example [https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators) and the icon is shown correctly but I'd like to update its menu when i click on it. I've tried with 
 ```
       self.connect('clicked',self._on_click)
```
but i get the follow error
```
TypeError: <Indicator object at 0x99b2acc (AppIndicator at 0x99dd058)>: unknown signal name: clicked

```
So does anyone know how to implement it ?
Thank you in advance !

---

### Post by johnl on 2010-11-16
Hi,

as far as I can tell you create a gtk.Menu and pass it to the indicator, and then handle the menu events like you normally would.  The Indicator will take care of showing the menu when you click on it.

```

menu = gtk.Menu()
item = gtk.MenuItem("test menu item")
# here you can connect signals for each menu item
# item.connect('activate', handle_menu_item)
menu.append(item)
item.show()

your_indicator.set_menu(menu)

```

---

### Post by xisco.rib on 2010-11-16
Well, the indicator shows the menu when i click on it but doesn't update it. 
If i implement a normal menu, I can update it through
```
        self.menu.connect('popup-menu',self._on_popup)
```
but it doesn't work within the indicator. 
Basically what i want to do is create the menu dinamically when i click on the icon.

---

