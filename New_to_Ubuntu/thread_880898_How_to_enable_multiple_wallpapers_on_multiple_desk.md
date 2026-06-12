---
title: "How to enable multiple wallpapers on multiple desktops"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by SandyM on 2008-08-05
HI!!!!!! I am new to ubuntu and have been using it for two months. I am amazed with the multiple Desktop feature of ubuntu. AND JUST WANTED TO KNOW IF THERE IS A WAY TO ENABLE MULTIPLE WALLPAPERS ON ALL OF MY FOUR DESKTOPS SCREEN.
PLEASE HELP and tell me the way to do it . I amusing gnome and compiz fusion.

---

### Post by finer recliner on 2008-08-05
[http://ubuntuforums.org/showpost.php?p=4372328&postcount=3](http://ubuntuforums.org/showpost.php?p=4372328&postcount=3)

---

### Post by northern lights on 2008-08-05
Navigate to "System > Administration > Software Sources". Enable all
repositories but 'proposed' and 'backports'.

Then run ```
sudo apt-get update && sudo apt-get install gconf-editor compizconfig-settings-manager
```

Navigate to "System > Preferences > Advanced Desktop Effects Settings"

Under "General Options" set "Horizontal Virtual Size" to 4.
Under "Desktop Cube > Appearance tab" put 4 wallpapers.

Now, press Alt+F2 > type 'gconf-editor' > hit Enter.
Navigate to "apps > nautilus > preferences" and uncheck "Show Desktop".

---

### Post by gfg on 2008-08-05
> **northern lights said:**
> Navigate to "System > Administration > Software Sources". Enable all
repositories but 'proposed' and 'backports'.

Then run ```
sudo apt-get update && sudo apt-get install gconf-editor compizconfig-settings-manager
```

Navigate to "System > Preferences > Advanced Desktop Effects Settings"

Under "General Options" set "Horizontal Virtual Size" to 4.
Under "Desktop Cube > Appearance tab" put 4 wallpapers.

Now, press Alt+F2 > type 'gconf-editor' > hit Enter.
Navigate to "apps > nautilus > preferences" and uncheck "Show Desktop".

Is it possible to do this with the desktop wall plugin?

---

### Post by northern lights on 2008-08-05
No it isn't. Unfortunately, the Desktop Wall plugin has no option to set background images.

However, the Cube supports more than 4 viewports. Just not in vertical displacement. You can set 'vertical virtual size' to more than '1', but it will ignore it. Nonetheless, horizontally it can be stretched virtually infinitely (correct me if I'm wrong - just tried 6).

---

### Post by Helios1276 on 2008-08-07
Just out of interest, has anyone found this buggy?

---

### Post by northern lights on 2008-08-07
nope.

---

### Post by Helios1276 on 2008-08-07
> **northern lights said:**
> nope.

I'm not knocking it , just seem to have experienced some slight graphical glitches since implementing .

---

### Post by cszikszoy on 2008-08-07
This functionality should be coming to gnome very soon (perhaps 2.24?)  This is currently being worked upon by one of the Summer of Code students.  He has made good progress and even has a video demonstration of it on his blog, here: [http://gsocblog.jsharpe.net/archives/15](http://gsocblog.jsharpe.net/archives/15)

Now that we (almost) have multiple wallpapers for the desktop, I'm only missing having different icons on different desktops :(

---

### Post by Helios1276 on 2008-08-07
> **cszikszoy said:**
> This functionality should be coming to gnome very soon (perhaps 2.24?)  This is currently being worked upon by one of the Summer of Code students.  He has made good progress and even has a video demonstration of it on his blog, here: [http://gsocblog.jsharpe.net/archives/15](http://gsocblog.jsharpe.net/archives/15)

Now that we (almost) have multiple wallpapers for the desktop, I'm only missing having different icons on different desktops :(

I got the impression that would not function with Compiz.

---

### Post by cszikszoy on 2008-08-07
Yes, he does mention that compiz uses viewports, not desktops.  But, the great thing about open source, is that someone will find a way.  And - it seems that all of the back-end stuff has already been completed.  All that needs to happen is to make this work with viewports as well.

---

### Post by nelsoniv on 2008-08-16
> **northern lights said:**
> Navigate to "System > Administration > Software Sources". Enable all
repositories but 'proposed' and 'backports'.

Then run ```
sudo apt-get update && sudo apt-get install gconf-editor compizconfig-settings-manager
```

Navigate to "System > Preferences > Advanced Desktop Effects Settings"

Under "General Options" set "Horizontal Virtual Size" to 4.
Under "Desktop Cube > Appearance tab" put 4 wallpapers.

Now, press Alt+F2 > type 'gconf-editor' > hit Enter.
Navigate to "apps > nautilus > preferences" and uncheck "Show Desktop".

Just an update.....I'm currently running CSSM 0.7.4 and the Background Images field is no longer available in the Appearance tab of the Desktop Cube. I could only get the above to work by following the above but enabling the Wallpaper plugin instead and adding the images from there. 

Works great!:guitar:

---

### Post by t0p on 2008-08-16
There is an app available from the repos, **desktop-drapes**, that will periodically change your desktop backgrounds from a list of images configured in its preferences.

I don't know how it works with multiple desktops though.

---

### Post by phil66 on 2008-08-16
There is also a .deb apps found at softpedia that work real well.
Its called Wallpapoz 0.4.1 
I have four workspace with different wallpaper on each.
Google has more info on the subject and also ubuntu Desktop and custimazation forum

[http://linux.softpedia.com/progDownload/Wallpapoz-Download-8113.html](http://linux.softpedia.com/progDownload/Wallpapoz-Download-8113.html)

Hope this helps

---

