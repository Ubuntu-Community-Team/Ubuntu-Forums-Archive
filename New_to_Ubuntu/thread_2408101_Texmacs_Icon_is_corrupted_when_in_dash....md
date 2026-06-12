---
title: "Texmacs Icon is corrupted when in dash..."
date: 2018-12-13
forum: New to Ubuntu
---

### Post by automate-stuff on 2018-12-13
I installed the .deb package for Texmacs using Gdebi (which I downloaded straight from their website, since Ubuntu reps don't contain it)...Everything works out except the Texmac's icon does not show up in the dash....How do I fix this issue ? Here is a photo : 




[ATTACH=CONFIG]281926[/ATTACH]

---

### Post by DuckHook on 2018-12-14
It's been ages since I've installed anything with Gdebi, so my knowledge is incomplete, but let's see if this might help:

The icon is probably undefined in the .desktop file. But we don't even know the name of the particular .desktop file for your app. It used to be easy to find this stuff, but these days we have to delve into the obscurity of the dconf database, so:```
gsettings get org.gnome.shell favorite-apps
```Look for the entry that might be the .desktop file for your app. Example: it could be called texmacs.desktop (you should be so lucky).

Then:```
sudo updatedb && locate texmacs.desktop
```&#8230;or whatever ***.desktop

After file is located, open it with a text editor. If location is owned by root, you will need to use sudo:```
sudo nano /path/to/texmacs.desktop
```
Look for the line:```
Icon=
```You will have to fill in the path/name to your texmacs icon. I have no idea where this icon might be. Yours is a nonstandard app and I can't help you with the details and locations of your various components. Be sure to use the proper icon size if you don't want it to look disproportionate in the dash.

---

### Post by CatKiller on 2018-12-14
Good news. It does include the .desktop file, which *is* called texmacs.desktop, *and* it includes a handy icon. It's simply that it doesn't put that icon in a sensible place.

```
ln -s /usr/local/share/icons/gnome/scalable/TeXmacs.svg /usr/share/icons/hicolor/scalable/apps/
```

should work, I think.

---

### Post by automate-stuff on 2018-12-16
Here is what i did to fix the issue:




(1) Run "xprop WM_CLASS" in terminal and click Texmac's window. 


    output: "WM_CLASS(STRING) = "texmacs.bin", "Texmacs.bin"


(2) Install menulibre and find out where texmacs.desktop is.


(3) Change texmacs.desktop to texmacs.bin.desktop

---

