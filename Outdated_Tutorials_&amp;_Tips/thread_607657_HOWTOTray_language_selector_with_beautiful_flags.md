---
title: "HOWTO:Tray language selector with beautiful flags"
date: 2007-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by blacksm1th on 2007-11-09
[IMG]http://img232.imageshack.us/img232/7640/screenshotxy6.png[/IMG]
[IMG]http://img88.imageshack.us/img88/9694/screenshot1ne1.png[/IMG]

To achieve this we need two components: first is fbxkb from [[COLOR="Red"]HERE[/COLOR]]("http://fbxkb.sourceforge.net/") and second are icon packs from [[COLOR="Red"]HERE[/COLOR]]("http://search.deviantart.com/?q=flags+in:customization/icons/os/win&section=browse&qh=boost:popular%20age_sigma:24h%20age_scale:5") - (i use squared but rounded flags are beautiful too)

Now the hard part:

1.Unpack fbxkb-0.6.tgz

2.Open console in folder fbxkb-0.6 and run 
```
./configure
```
3.Then run
```
make
```
4.Here i found one little thing - open file fbxkb.c in gedit and locate this line (this is line 244)
> gtk_container_set_border_width(GTK_CONTAINER(box), 0);
replace 0 with 2 and save file. (By default panel size in UBUNTU is 24 pixels and icons of fbxkb will use all height but with 2 pixels from top and bottom will be like in screenshots above)
 
5.Then look in folder 
> /fbxkb-0.6/images
 and locate flags who you will use (i use bg.png and gb.png) and replace original flags (by replace i mean rename deviantart flags with names of flags in images folder and then replace)

6.Now run 
```
su make install
```
7.Press Alt+f2 and type 
> fbxkb
then press "OK"

If you want to fbxkb to start with UBUNTU  go here - Main menu -> System -> Preferences -> Sessions and press "Add" and fill "Name" and "Command" fields with 
> fbxkb
 then press "OK"

To change keyboard shortcuts go here - Main menu -> System -> Preferences -> Keyboard -> Layout Options -> Group Shift/Lock behaviour - and use checkboxes to change keys to match with your needs (i use "Alt+Shift changes group"). Single left button mouse click on tray icon will change languages.

---

### Post by kagashe on 2008-05-22
fbxkb is available in gutsy and Hardy universe repositories so you need to install with apt-get.

This wonderful applet is also useful for light desktops like Fluxbox, Icewm, LXDE etc.

kagashe

---

### Post by hjacker on 2009-05-24
Shame on me, but I can't locate /images/ folder. I tried hard, but still no chance.

---

### Post by kagashe on 2009-05-25
> **hjacker said:**
> Shame on me, but I can't locate /images/ folder. I tried hard, but still no chance.
It is in /usr/share/fbxkb/images

Unfortunately, the new version of fbxkb has a bug and 'us' map does not get loaded, you get '??" instead.  

kagashe

---

### Post by kagashe on 2009-05-25
By the way I have developed a utility to Add/Change Keyboard layout on Ubuntu jaunty and posted about it [here]("http://ubuntuforums.org/showthread.php?p=7341625") but this forum no longer responds to such things.

kagashe

---

