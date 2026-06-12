---
title: "How in heck to do I get a large mouse cursor?"
date: 2018-10-19
forum: New to Ubuntu
---

### Post by cybervigilante on 2018-10-19
The default mouse pointer is too tiny for me, but I've tried five different ways to make it larger and nothing works. Why is this so hard? It's not unimportant. Visual usability is very important - I learned that as a webmaster - and half of Americans have vision problems. 

I finally got Comic Cursors installed but they won't enlarge either, although there is a checkoff to do that. Other installs simply didn't work 

Is there Anything that will give me a large cursor for Lubuntu without obscure command line finagling that doesn't work anyway?

---

### Post by Autodave on 2018-10-19
Settings -> Mouse & Touchpad -> Theme.  Then look for cursor size.

---

### Post by Dennis N on 2018-10-19
> Is there Anything that will give me a large cursor for Lubuntu without obscure command line finagling that doesn't work anyway?
Yes, how to do it is not easy to discover (as with many things about Lubuntu), but it can indeed be done without the terminal.
First, choose cursor theme:
```
Preferences > Customized Look and Feel > Mouse Cursor Tab 
```
It must be a resizable cursor. **DMZ-White, DMZ-Black** are resizable. Select which one you want.
Then, open this file in a text editor:
```
~/.config/lxsession/Lubuntu/desktop.conf
```
Find the section [GTK].
In that section, look for the line beginning with:
```
iGtk/CursorThemeSize=
```
and set the size to one available for your cursor theme. I can inform you that DMZ-White and DMZ-Black have three sizes: 24, 32, 48 so you must use one of these.
So your edited line might be:
```
iGtk/CursorThemeSize=48
```
Save the file, and reboot.  Size takes effect after log in.

---

### Post by cybervigilante on 2018-10-19
Thanks. That actually worked. Yuge cursor :D Now I have to get the damn numlock to be on after I boot.

---

### Post by Dennis N on 2018-10-19
> Now I have to get the damn numlock to be on after I boot. 
Install **numlockx**
Add it to startup applications.
Preferences > Default Applications for lxsession > Autostart button > Add numlockx in box on right under "Manual autostarted applications", click 'Add'
Log out and Log in. numlock will now turn on after log in.

---

### Post by cybervigilante on 2018-10-19
Instead of casting around looking for all this stuff, is there a Lubuntu manual somewhere?

---

### Post by PaulW2U on 2018-10-20
> **cybervigilante said:**
> Instead of casting around looking for all this stuff, is there a Lubuntu manual somewhere?
[https://manual.lubuntu.me/](https://manual.lubuntu.me/)

Other useful information about Lubuntu can be found at its home page: [https://lubuntu.me/](https://lubuntu.me/)

---

### Post by Lew on 2018-10-21
> **Dennis N said:**
> Yes, how to do it is not easy to discover (as with many things about Lubuntu), but it can indeed be done without the terminal.
First, choose cursor theme:
```
Preferences > Customized Look and Feel > Mouse Cursor Tab 
```
It must be a resizable cursor. **DMZ-White, DMZ-Black** are resizable. Select which one you want.
Then, open this file in a text editor:
```
~/.config/lxsession/Lubuntu/desktop.conf
```
Find the section [GTK].
In that section, look for the line beginning with:
```
iGtk/CursorThemeSize=
```
and set the size to one available for your cursor theme. I can inform you that DMZ-White and DMZ-Black have three sizes: 24, 32, 48 so you must use one of these.
So your edited line might be:
```
iGtk/CursorThemeSize=48
```
Save the file, and reboot.  Size takes effect after log in.

Wouldn't Settings -> Universal Access -> Cursor Size be a simpler way to do it?

---

