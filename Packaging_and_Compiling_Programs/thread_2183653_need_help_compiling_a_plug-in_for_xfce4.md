---
title: "need help compiling a plug-in for xfce4"
date: 2013-10-25
forum: Packaging and Compiling Programs
---

### Post by sam_baker2 on 2013-10-25
hi, 
I am trying to compile an app for xubuntu 12.04 with the xfce4 desktop 4.8.
It is the weather plug-in app "xfce4-weather-plugin-0.8.3" ( also, I am  beginner at compiling )
The xfce4-weather-plugin I have now has a date of Nov 19, 2011 and it quit
working out of the blue for some reason. 

I downloaded the app and extracted to a folder and when I go to compile using these commands:
```
./configure; make; make install 
```
it seems to work ok  until the very bottom and then I get these comments:
```
checking for gtk+-2.0 >= 2.14.0... not found
*** The required package gtk+-2.0 was not found on your system.
*** Please install gtk+-2.0 (atleast version 2.14.0) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

```

I can't find a "gtk+-2.0" in synaptic.

any help appreciated.

also~ the original location of the app on my system is:
```
/usr/lib/x86_64-linux-gnu/xfce4/panel-plugins/xfce4-weather-plugin

```
"xfce4-weather-plugin" being a "shared library"

---

### Post by MG&amp;TL on 2013-10-25
I believe you want the *libgtk2.0-dev* package:

```
sudo apt-get install libgtk2.0-dev
```

Autoconf isn't always very useful for finding package names.

---

### Post by sam_baker2 on 2013-10-25
I installed the libgtk2.0-dev and ran the compile again, and it keep asking me to install other packages,
which I found in synaptic and I installed. But I got to this one :
```
checking for libxfce4panel-1.0 >= 4.7.0... not found
*** The required package libxfce4panel-1.0 was not found on your system.
*** Please install libxfce4panel-1.0 (atleast version 4.7.0) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
```

and I couldn't find a "libxfce4panel" in synaptic.

---

### Post by sam_baker2 on 2013-10-25
I found that I do have a /usr/lib/x86_64-linux-gnu/libxfce4panel-1.0.so.3.0.0
 and also a libxfce4panel-1.0.so.3 ( a link to libxfce4panel-1.0.so.3.0.0 ) in the
same folder

but I don't know how to set the PKG_CONFIG_PATH environment variable
so that the compile can find them.

---

### Post by Toz on 2013-10-25
I think that you are going to find that to meet the dependencies of the latest xfce4-weather-plugin for Xfce 4.8, you'll be looking at re-building most of the Xfce components. This in itself, is not a bad learning exercise (though frustrating and tedious). However, there is an easier way. You can install version 4.10 via PPA. This particular PPA comes not only with the 0.8.3 version of the weather plugin, but also with the 4.10 version of Xfce (win-win). More information about installing/using the PPA can be [found here]("http://www.webupd8.org/2012/05/install-xfce-410-in-xubuntu-1204.html").

---

### Post by sam_baker2 on 2013-10-25
thanks for reply Toz.
I installed the PPA and got the new xfce4-weather-plugin to work, now I have 4.10 
I did notice that Google earth will not run. I had this problem some time back, maybe when I went from
11.4 to 12.04, not sure.

---

### Post by Toz on 2013-10-25
> **sam_baker2 said:**
> I did notice that Google earth will not run. I had this problem some time back, maybe when I went from
11.4 to 12.04, not sure.

If you enter:
```
google-earth
```
...into a terminal window, what responses do you get?

---

### Post by sam_baker2 on 2013-10-25
it runs Toz!.
Aparently there is some setting that needed me to run it
in the terminal to get the settings back.
Now it will run from the menu like it is supposed to.

---

