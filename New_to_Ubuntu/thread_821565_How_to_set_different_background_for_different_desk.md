---
title: "How to set different background for different desktop?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by talktoari on 2008-06-07
Hi,

I am a fairly new user even though I have ramped up quite fast in ubuntu.

However 1 small but may appear stupid question is that how can I have different wallpapers for different desktops.

Currently when I change the background of one desktop the other one also changes.

I am using Ubuntu Hardy Heron.

Any help is appreciated... Thanks

---

### Post by billgoldberg on 2008-06-07
You can use wallpapoz.

You can download a .deb file here:
[http://www.getdeb.net/app/Wallpapoz](http://www.getdeb.net/app/Wallpapoz)

double click the file to install.

I can't really recommend it though, had some bad experiences with it in gutsy, but it does work.

---

### Post by talktoari on 2008-06-08
This utility provides the facility to change wallpaper after certain period of time.

I am looking for something which allows different wallpapers for different desktops.

Is there no internal utility or editing of some file possible to do the same? I would be surprised to know then since this can be a new idea / feature which intrepid can include inherent with it.

---

### Post by xjgnsdof on 2008-06-08
I'm assuming that you have a desktop cube. If so, follow these steps:
1) Alt+F2 and run gconf-editor
2) Navigate to nautilus -> preferences
3) uncheck "show desktop"
4) go into Advanced Desktop Settings and select Desktop Cube
5) under Appearance, add and arrange the desktop backgrounds that you want for each face of the cube

---

### Post by talktoari on 2008-06-08
I have the facility of desktop cube but I have not turned it ON.

Without turning ON this, don't I have anything by which I can change teh desktop background for different desktop?

I would assume this facility to be present in Ubuntu itself rather than using any third party software to do the same.

Am I asking too much??

---

### Post by BLTicklemonster on 2008-06-08
I think it's a great idea. I'd like to have different images on each desktop that I can go to.

---

### Post by Drakkor on 2008-06-08
That does work, elgilicious,but I can't get water effects,except on the panels when I do that. :confused:

---

### Post by talktoari on 2008-06-08
Looking from the responses I believe there is no native way which Ubuntu provides to have different desktop background for different desktop?

Can someone tell me where this new idea can be posted and a vote could be taken so as to have it present in the next Ubuntu (INTREPID)?

---

### Post by Drakkor on 2008-06-08
There is other desktops ! see above :lolflag:

---

### Post by ad_267 on 2008-06-08
The application posted by billgoldberg does allow changing the desktop for different workspaces.

> The most important feature is you could have Gnome desktop wallpaper changes when you change workspace.

But no, there is no built in configuration that can do this except with the compiz cube.

---

### Post by denham2010 on 2008-06-08
Hi,

I'm using XFCE, and while it is not something I have tried as of yet (as I am using compiz-fusion and so have different workspace wallpapers set in there).

In the folder ~/.config/xfce4/mcs_settings you will find the file desktop.xml.

Now, depending on how many workspaces you have set up, you will see a series of options similar to the following:

```
<option name="imagepath_0_0" type="string" value="/usr/share/xfce4/backdrops/xubuntu-jmak.png"/>
<option name="imagepath_0_1" type="string" value="/usr/share/xfce4/backdrops/xubuntu-jmak.png"/>
<option name="imagepath_1_0" type="string" value="/usr/share/xfce4/backdrops/xubuntu-jmak.png"/>
<option name="imagepath_1_1" type="string" value="/usr/share/xfce4/backdrops/xubuntu-jmak.png"/>
```

Setting these to the wallpapers you want may work.

If anyone else using XFCE can confirm if this works, please let us know. It wouldn't be to difficult to write a small GUI app with python etc. to change these settings!

Cheers.

---

### Post by dadsbrkn on 2008-06-16
I am currently using wallpapoz to have different wallpapers on each desktop, it seems to work OK on Hardy.  There is a small lag when you change desktops before the wallpaper changes though.

---

### Post by Find on 2009-05-16
I remeber there was such a thing in another distribution, probably Mandrake (if i am not wrong),but aparently is missing in Ubuntu.

Intel 3100 is blacklisted by compiz config, so if the way that was mentioned using cubes is the only way, practically i can not have different backgrounds, is that true?

---

### Post by Thumper33 on 2009-11-25
> **elgilicious said:**
> I'm assuming that you have a desktop cube. If so, follow these steps:
1) Alt+F2 and run gconf-editor
2) Navigate to nautilus -> preferences
3) uncheck "show desktop"
4) go into Advanced Desktop Settings and select Desktop Cube
5) under Appearance, add and arrange the desktop backgrounds that you want for each face of the cube

I did this, but all I can do is set a wallpaper on the top of the cube.  Whichever file is listed first is on the top of the cube, but none of the others show up on any of the main faces.  Also, once I did this, I can no longer RT click on the desktop and change the wallpaper at all.  I went back and re-enabled show desktop, and I still can't change my current wallpaper.

New to Linux so kinda in uncharted territory here.....

---

