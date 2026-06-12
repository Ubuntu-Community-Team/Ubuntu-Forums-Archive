---
title: "Getting an application icon displayed"
date: 2008-02-05
forum: Packaging and Compiling Programs
---

### Post by W.Boeke on 2008-02-05
Hi,
I created an application for music composition, and I would like to attract interest from real composers. I want to release a debian package from the app's homepage. Composers possibly are not geeks, so the app should be started not from the command line, but by clicking an icon on the panel.

Now here is my problem: I have a .deb file and install it with dpkg -i. Everything okay, but no icon under Applications->Sound&Video. By try-and-error I found out that one has to drag the .desktop file to the Applications window or to the panel. Where in the documentation is this mentioned? And how do I communicate this to my poor musical but non-geek customers?

Wouter

---

### Post by dholbach on 2008-02-05
How does your .desktop file look like? Where do you install it to? Does it show up in the menu at all or just without icon? Where do you install the icon? Do you run dh_icons and dh_desktop in debian/rules somewhere?

---

### Post by W.Boeke on 2008-02-05
> **dholbach said:**
> How does your .desktop file look like? Where do you install it to? Does it show up in the menu at all or just without icon? Where do you install the icon? Do you run dh_icons and dh_desktop in debian/rules somewhere?

That's a lot of questions....
Here is my .desktop file:

  [Desktop Entry]
  Type=Application
  Name=Amuc
  GenericName=An app for music composition
  Comment=the Amsterdam Music Composer
  Icon=amuc-icon.png
  Exec=amuc
  Terminal=false
  MimeType=text/plain;
  Categories=AudioVideo;

- I install the package to the standard places. Lindian does not complain. 
- The app does not show up in any menu. If I drag the .desktop file to the panel, then it shows up, also in the 'Run Application' tool.
- I do NOT run dh_icons and dh_desktop in debian/rules, because I create the .deb file with checkinstall, and install it with dpkg -i. Could this be the problem?

Thanks for your help,
Wouter

---

### Post by dholbach on 2008-02-06
Yes, I guess checkinstall is the culprit. That's one of the problems of checkinstall: you can't use all the script goodness you'd use when you packaged it 'regularly'. Try running 
for i in `find /usr/share/icons -mindepth 1 -maxdepth 1 -type d`; do sudo gtk-update-icon-cache $i; done
and see if that helps. Of course asking your customers and users to do that sucks.

---

### Post by W.Boeke on 2008-02-06
Something must be wrong....
In a 2nd try I used  'dpkg-deb --build debian'. I followed all instructions carefully,
ran lintian and then installed the created .deb package with  dpkg -i. The result was exactly the same as with checkinstall: all files were installed as expected, but no item in the Applications->Sound & Video menu. I suppose that a normal apt-get from a regular repository runs some extra code in order to install a menu item. Please, which knowledgable person is able offer a hint?

Wouter

---

### Post by dholbach on 2008-02-07
You still did not mention where you install the icon to and if the gtk-update-icon-cache run helps.

---

### Post by W.Boeke on 2008-02-07
> **dholbach said:**
> You still did not mention where you install the icon to and if the gtk-update-icon-cache run helps.

Sorry, I installed the icon at /usr/share/pixmaps.
However, I don't suppose that finding the icon is the problem. The app does not show up in the Applications menu, be it with its own icon or with a default one. 

Wouter

---

### Post by Keith Hedger on 2008-02-07
i think you have to do an update-menu, and it also helps to kill your gnome-panel to refresh it (it will reload automatically)

---

### Post by W.Boeke on 2008-02-07
> **Keith Hedger said:**
> i think you have to do an update-menu, and it also helps to kill your gnome-panel to refresh it (it will reload automatically)

Sorry again, but update-menu is not available in gutsy 7.10.
Killing gnome-panel made no difference either.

Wouter

---

### Post by Keith Hedger on 2008-02-07
sorry it should be update-menus with an s (it is in the menu package)

---

### Post by dholbach on 2008-02-08
Where is the .desktop file being installed to?

---

### Post by W.Boeke on 2008-02-08
> **dholbach said:**
> Where is the .desktop file being installed to?

The path to the .desktop file is:  /usr/share/applications/amuc.desktop
Its content is:

[Desktop Entry]
Type=Application
Name=Amuc
GenericName=the Amsterdam Music Composer
Comment=A program for music composition
Icon=amuc-icon
Exec=amuc
Terminal=false
MimeType=text/plain;
Categories=AudioVideo;

If I issue:
  nautilus /usr/share/applications
then I see the icon and can start the program by clicking it. But it is still not listed in the Applications->Sound&Video menu, even if I kill the gnome panel

Keith Hedger suggested that update-menus should be run. I installed this program and used it, but it made no difference. To be honest, I think that update-menus is not needed at all, because when it was not available on my computer, everything still worked correctly. As I understand it, Ubuntu uses the Common Desktop environment, update-menus is for Debian proper.

I also tried my app with Fedora Core 5. I copied the .desktop file to /usr/share/applications and guess what... the menu item showed up where it should be, under Applications->Sound&Video.

So far, thanks for your help, but still hoping for a new tip.

Wouter

---

### Post by Keith Hedger on 2008-02-08
I just tried copying and pasting your desktop file and then copied it to /usr/share/applications and it showed up fine, I then opened the menu editor and unchecked the box for your menu item and it disapeared, so far all as it should do, I then removed the desktop file and then re-copied it but the menu remembered that it had been turned off and I had to manually turn it on in the menu editor maybe you have a similar problem?

---

### Post by W.Boeke on 2008-02-08
> **Keith Hedger said:**
> I just tried copying and pasting your desktop file and then copied it to /usr/share/applications and it showed up fine, I then opened the menu editor and unchecked the box for your menu item and it disapeared, so far all as it should do, I then removed the desktop file and then re-copied it but the menu remembered that it had been turned off and I had to manually turn it on in the menu editor maybe you have a similar problem?

Hi Keith,

This do-it-yourself solution works of course. Maybe in a later Ubuntu release the system will do this automatically again.

Wouter

---

