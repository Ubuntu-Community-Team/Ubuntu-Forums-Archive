---
title: "Lost Frostwire Icon"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by tashmooclam on 2008-07-02
I fooled around with Frostwire after an 8.04 upgrade. Foolishly I had the icon on the desktop, then put it in the trash. I fixed Java and now Frostwire works, but I have no icon, just a square next to Frostwire in a menu. Downloading Frostwire again doesn't work, since I had deleted it and re-installed it before I figured out the Java problem was the cause. 
Any ideas on how to restore that icon?

---

### Post by steveneddy on 2008-07-02
here's one

[IMG]http://www.kde-look.org/CONTENT/content-files/69335-frostwire2.png[/IMG]

and a link to some different icons

[http://ubuntuforums.org/showthread.php?t=335197](http://ubuntuforums.org/showthread.php?t=335197)

or even look here

[http://www.iconspedia.com/](http://www.iconspedia.com/)

BTW - I just searched Google for Frostwire icon. These were in the top 10.

---

### Post by tashmooclam on 2008-07-02
Thanks. Any idea how to make this icon appear on the menu? I probably must place it into some folder somewhere.

---

### Post by steveneddy on 2008-07-02
> **tashmooclam said:**
> Thanks. Any idea how to make this icon appear on the menu? I probably must place it into some folder somewhere.

Just stick it in your home folder, right click the launcher, select Properties, the upper left there is a box with an icon, click it and browse to where you stuck the icon, click it and now that icon will show up on that launcher.

---

### Post by tashmooclam on 2008-07-02
Thank you, that worked for the desktop icon I trashed. I also figured out how to fix the icon on the Menu. I went to System>Preferences>Main Menu>Internet and saw frostwire with the square thing. I right clicked it and selected Properties, then found the icon and got the icon back.

---

### Post by isaacj87 on 2008-07-02
Hey,

I have a really nice Frostwire icon if you want it.

---

### Post by tashmooclam on 2008-07-02
Thanks, looks cool.

---

### Post by go_beep_yourself on 2008-09-11
Here's what I do to get icons for my programs. First check to see if the program came with an icon by getting a list of the files from the package.

```
dpkg -L frostwire
```

You can also:

```
dpkg -L frostwire | grep piximap
dpkg -L frostwire | grep "png\|xpm"
```

You can search online for packages from other distros, extract them, and get the icons from those. You can search wikipedia commons. You can find a picture with a logo for the program and crop that out with Gimp.

Once you have the icon using any of those ways, you can add it to your menu with alacarte. To do that, type alacarte and hit enter from a terminal or right click "Applications" from gnome and "edit menus".

---

