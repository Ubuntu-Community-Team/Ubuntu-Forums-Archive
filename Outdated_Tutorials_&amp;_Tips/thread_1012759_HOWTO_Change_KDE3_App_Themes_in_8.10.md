---
title: "HOWTO: Change KDE3 App Themes in 8.10"
date: 2008-12-16
forum: Outdated Tutorials &amp; Tips
---

### Post by GrammatonCleric on 2008-12-16
With the release of 8.10 one of my biggest gripes is the lack of the ability to theme KDE3 applications.  This has been mostly because of 8.10's lack of the KDE Control Center, also known as kcontrol,  which is no longer available in the intrepid ibex repos.   This HowTo covers how to  bring some of kcontrol's functionality back to 8.10.


**Step 1:** Download kcontrol from the hardy release.

```


For amd64:
http://packages.ubuntu.com/hardy-backports/amd64/kcontrol/download

For i386:
http://packages.ubuntu.com/hardy-backports/i386/kcontrol/download


```**Step 2:**  Extract the kcontrol package into a temp directory.

```


dpkg -x kcontrol_3.5.10-0ubuntu1~hardy2_i386.deb ~/temp


```**Step 3:** Change into the directory.

This is to verify that the deb package extraction worked. 

```


cd  ~/temp/usr/lib/kde3


```**Step 4:** Copy several kcontrol modules to /usr/lib/kde3

For the most part you'll just need the icons, colors, fonts and style modules from kcontrol.

```


sudo cp ~/temp/usr/lib/kde3/kcm_icons.* /usr/lib/kde3
sudo cp ~/temp/usr/lib/kde3/kcm_colors.* /usr/lib/kde3
sudo cp ~/temp/usr/lib/kde3/kcm_fonts.* /usr/lib/kde3
sudo cp ~/temp/usr/lib/kde3/kcm_style.* /usr/lib/kde3
sudo cp ~/temp/usr/share/applications/kde/icons.desktop /usr/share/applications/kde
sudo cp ~/temp/usr/share/applications/kde/colors.desktop /usr/share/applications/kde
sudo cp ~/temp/usr/share/applications/kde/fonts.desktop /usr/share/applications/kde
sudo cp ~/temp/usr/share/applications/kde/style.desktop /usr/share/applications/kde


```**Step 5:** Changing KDE3 Applications to match your themes.


Open a Terminal and issue the following commands.

To change KDE3 icons:
```


kcmshell icons


```To change KDE3 colors:
```


kcmshell colors


```To change KDE3 fonts:
```


kcmshell fonts


```To change KDE3 style:
```


kcmshell style


```There you go... enjoy.

[IMG]http://twitpic.com/img/t2e9-4090d7f12e7127a27024a8d851aad8dc.49482196.png[/IMG]

---

### Post by GrammatonCleric on 2008-12-16
Fixed a type-o.

---

### Post by junalmeida on 2008-12-28
Nice tutorial!
Thanks :)

---

### Post by supercheetah on 2009-03-01
Thank you so much.  I made a bad decision a while back with an awful color scheme, and have been racking my brain on how to fix it.

I hacked up a little script so that the above commands could be executed with just one *sudo* command.

```

#!/bin/sh
##
## kc_install.sh

cp ./usr/lib/kde3/kcm_icons.* /usr/lib/kde3
cp ./usr/lib/kde3/kcm_colors.* /usr/lib/kde3
cp ./usr/lib/kde3/kcm_fonts.* /usr/lib/kde3
cp ./usr/lib/kde3/kcm_style.* /usr/lib/kde3
cp ./usr/share/applications/kde/icons.desktop /usr/share/applications/kde
cp ./usr/share/applications/kde/colors.desktop /usr/share/applications/kde
cp ./usr/share/applications/kde/fonts.desktop /usr/share/applications/kde
cp ./usr/share/applications/kde/style.desktop /usr/share/applications/kde

```

PS Note that you must be working from within the directory you extracted (if you're following the above examples, it would be *~/temp*).

---

### Post by Matyy on 2009-03-13
thanks, I did that when I started using intrepid, forgot it meanwhile, and now it quickly helped me achieving the same in jaunty

---

### Post by aniruddha on 2010-07-23
Hello all, many apologies for reanimating an old thread but I have a quick question. Having followed this procedure and applied some font changes to make amarok14 look a little more integrated, I find that the "kcmshell fonts" command has made system wide changes. For e.g. even my firefox window now uses the same font settings as kcmshell (see the screenshot, where the tab fonts, toolbar fonts are blurry and the main window font is different to what is set in my gtk appearances setting).

So my question is whether it is possible to revert back to default settings or to ensure the changes made by kcmshell are undone. 

Many thanks.

---

