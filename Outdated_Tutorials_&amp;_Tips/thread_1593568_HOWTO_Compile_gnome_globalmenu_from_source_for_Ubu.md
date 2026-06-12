---
title: "HOWTO: Compile gnome globalmenu from source for Ubuntu 10.10"
date: 2010-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by alokmenon on 2010-10-11
This is a guide for compiling **[gnome2-globalmenu]("http://code.google.com/p/gnome2-globalmenu/")**, a Global Menu Bar for GNOME.


[LIST=1]
[*]Download the latest source from:** [here]("http://code.google.com/p/gnome2-globalmenu/downloads/list")** and extract it. Lets say you have it extracted to ```
/home/<user>/Desktop/gnome-globalmenu-0.7.9/
```
[*]Download the older source from the Git rep:** [here]("http://github.com/gnome-globalmenu/gnome-globalmenu/archives/v0.7.8")** and extract.```
/home/<user>/Desktop/gnome-globalmenu-gnome-globalmenu-50c0fd1/
```
[*]Open the older source and copy the ./autogen file and paste it in the *gnome-globalmenu-0.7.9* folder.
[*] Now, navigate to *gnome-globalmenu-0.7.9* folder, and install the following packages one by one in the terminal: (When I tried making the source, these packages were missing)
[/LIST]
[INDENT]```
sudo apt-get install intltool
sudo apt-get install libtool
sudo apt-get install libconf2-dev
sudo apt-get install libgtk2.0-dev
sudo apt-get install libwnck*
sudo apt-get install libgnome-menu*
sudo apt-get install libpanelapplet-*
sudo apt-get install libnotify*
sudo apt-get install xfce4-panel*
```[/INDENT]5. Now run aclocal:```
aclocal
```Now you can follow the manually compiling the source tutorial from the wiki **[here]("http://code.google.com/p/gnome2-globalmenu/wiki/BuildFromSource")** 
[LIST]
[*]```
./autogen.sh --prefix=/usr --sysconfdir=/etc --disable-tests --without-xfce4-panel
```
[*]```
make
```
[*]```
export GTK_MODULES=globalmenu-gnome
```
[*]```
sudo make install
```
[/LIST]
Finally kill the X server or logout and login.
Right click on the panel and add new, select gnome global menu and voila, you have the global menu in Ubuntu 10.10. You could make it a script and just run it once. Make sure you use "**-y**" tag for apt-get in the script to avoid it asking for your input whether to install the package or not.

PS: The global menu does not work with firefox :(. It has not been updated in a while, so I did not expect it to magically fix it all.

---

### Post by Rim3nX on 2011-01-09
I only got this... (attached)
What should I do with empty textboxes???

---

### Post by Rim3nX on 2011-01-09
And how do I hide menu from windows, witch was kinda the point of installing this globalmenu :)

---

