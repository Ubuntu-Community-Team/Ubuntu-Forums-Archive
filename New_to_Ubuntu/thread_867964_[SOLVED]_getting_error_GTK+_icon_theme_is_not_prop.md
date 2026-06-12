---
title: "[SOLVED] getting error GTK+ icon theme is not properly set when switched to lxde envi"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by imgkg on 2008-07-23
hi guys ,i am getting error every time i log into lxde environment a dialog box appears saying:-





GTK+ icon theme is not properly set

This usually means you don't have an XSETTINGS manager running.  Desktop environment like GNOME or XFCE automatically execute their XSETTING managers like gnome-settings-daemon or xfce-mcs-manager.

If you don't use these desktop environments, you have two choices:
1. run an XSETTINGS manager, or
2. simply specify an icon theme in ~/.gtkrc-2.0.
For example to use the Tango icon theme add a line:
gtk-icon-theme-name="Tango" in your ~/.gtkrc-2.0. (create it if no such file)

NOTICE: The icon theme you choose should be compatible with GNOME, or the file icons cannot be displayed correctly.  Due to the differences in icon naming of GNOME and KDE, KDE themes cannot be used.  Currently there is no standard for this, but it will be solved by freedesktop.org in the future.


:(

what is this error how to fix it i have that .gtkrc-2.0 file in my home directory please help me out

---

### Post by mali2297 on 2008-07-23
Post the content of the the gtkrc file. 

Just to be sure that it is in the right place and everything, use the command
```

cat ~/.gtkrc-2.0

```
from the terminal.

Also, post the output of
```

ls ~/.icons /usr/share/icons/ 

```
to see which icon themes that are available.

---

### Post by imgkg on 2008-07-23
```
~$ cat ~/.gtkrc-2.0
gtk-menu-popup-delay = 0"| tee -a .gtkrc-2.0

~$ ls ~/.icons /usr/share/icons/
/home/user/.icons:

/usr/share/icons/:
application-default-icon.png  gnome                          Mist
Crux                          handhelds                      nuoveXT2
crystalsvg                    hicolor                        redglass
default                       HighContrastInverse            scalable
default.kde                   HighContrastLargePrintInverse  skype.png
DMZ-Black                     Human                          Tangerine
DMZ-White                     locolor                        whiteglass
user@user-desktop:~$ 


```

---

### Post by mali2297 on 2008-07-23
Open the .gtkrc-2.0 file in an editor and remove the line that is there (unless you know what it does).

Instead, insert the lines
```

gtk-font-name = "DejaVu Sans 9"
gtk-theme-name = "Human"
gtk-icon-theme-name = "Human"

```

I have here set the fonts to DejaVu Sans (size 9), the theme to Human and the icon theme to Human as well. You can change them as you wish. You can find the available themes in the directory /usr/share/themes/ (the icon themes in /usr/share/icons/).

---

### Post by mali2297 on 2008-07-23
If you don't like to manually edit configuration files, check out [LXAppearance]("http://ubuntuforums.org/showthread.php?t=738747").

---

### Post by imgkg on 2008-07-23
thank you mali2297 it worked  its not giving error now

---

### Post by eumakant on 2008-08-25
anand@anand-desktop:~$ ls ~/.icons /usr/share/icons/
/home/anand/.icons:
aero                                    ComixCursors-opaque-Orange-Large
ComixCursors-opaque-Black-Huge          ComixCursors-opaque-Orange-Large-Slim
ComixCursors-opaque-Black-Huge-Slim     ComixCursors-opaque-Orange-Regular
ComixCursors-opaque-Black-Large         ComixCursors-opaque-Orange-Regular-Slim
ComixCursors-opaque-Black-Large-Slim    ComixCursors-opaque-Orange-Small
ComixCursors-opaque-Black-Regular       ComixCursors-opaque-Orange-Small-Slim
ComixCursors-opaque-Black-Regular-Slim  ComixCursors-opaque-White-Huge
ComixCursors-opaque-Black-Small         ComixCursors-opaque-White-Huge-Slim
ComixCursors-opaque-Black-Small-Slim    ComixCursors-opaque-White-Large
ComixCursors-opaque-Blue-Huge           ComixCursors-opaque-White-Large-Slim
ComixCursors-opaque-Blue-Huge-Slim      ComixCursors-opaque-White-Regular
ComixCursors-opaque-Blue-Large          ComixCursors-opaque-White-Regular-Slim
ComixCursors-opaque-Blue-Large-Slim     ComixCursors-opaque-White-Small
ComixCursors-opaque-Blue-Regular        ComixCursors-opaque-White-Small-Slim
ComixCursors-opaque-Blue-Regular-Slim   default
ComixCursors-opaque-Blue-Small          Gion
ComixCursors-opaque-Blue-Small-Slim     glass-icons
ComixCursors-opaque-Christmas           gruppled_black
ComixCursors-opaque-Ghost               gruppled_white
ComixCursors-opaque-Green-Huge          Obsidian
ComixCursors-opaque-Green-Huge-Slim     OSX
ComixCursors-opaque-Green-Large         OxygenRefit2-black-version
ComixCursors-opaque-Green-Large-Slim    PolarCursorTheme
ComixCursors-opaque-Green-Regular       PolarCursorTheme-Blue
ComixCursors-opaque-Green-Regular-Slim  PolarCursorTheme-Green
ComixCursors-opaque-Green-Small         ROX
ComixCursors-opaque-Green-Small-Slim    Shere_Khan_X
ComixCursors-opaque-Orange-Huge         tuxcursor
ComixCursors-opaque-Orange-Huge-Slim    Vienna3

/usr/share/icons/:
application-default-icon.png   Human              oxy-sea_blue
cab_extract.png                locolor            oxy-violet
cab_view.png                   Mist               oxy-viorange
Crux                           nuoveXT2           oxy-white
crystalsvg                     oxy-black          oxy-yellow
default                        oxy-blue           redglass
default.kde                    oxy-brown          skype.png
DMZ-Black                      oxy-emerald        sugar
DMZ-White                      oxy-green          Tangerine
gestikk.xpm                    oxy-grey           Tango
gnome                          oxy-hot_orange     whiteglass
handhelds                      oxy-navy           wmii.png
hicolor                        oxy-purple         xmonad.png
HighContrastInverse            oxy-red
HighContrastLargePrintInverse  oxy-red-argentina
anand@anand-desktop:~$ /home/user/.icons

this is what i get when i type -->ls ~/.icons /usr/share/icons/ in the terminal and i cant use cat ~/.gtkrc-2.0 it does not shows me any thing i dont know where the file gtkrc-2.0 is in the human theme folder and i dont know what to do i get the same error of GTK+ icon theme is not properly set

---

### Post by mali2297 on 2008-08-25
> **eumakant said:**
> i cant use cat ~/.gtkrc-2.0 it does not shows me any thing i dont know where the file gtkrc-2.0 is in the human theme folder and i dont know what to do i get the same error of GTK+ icon theme is not properly set

Well, you need to create the file .gtkrc-2.0 then. From the terminal, open the file in the editor *nano* with the command
```

nano ~/.gtkrc-2.0

```
Then add the lines given in post #4. Save (ctrl+o) and quit (ctrl+x). (If you have gedit, you can use that instead of nano.)

---

### Post by eumakant on 2008-08-25
wow i just did this in the terminal 


touch .gtkrc-2.0
nano -w .gtkrc-2.0

and then added this 

gtk-font-name = "DejaVu Sans 9"
gtk-theme-name = "Human"
gtk-icon-theme-name = "Human"

its nice
lxde  working great, very fast, faster then gnome and similar to Windows xp type enviroment and similar in speed as compared to XFCE. 

keep the lxde development going its rocks 
thanks And Regards 
Umakant Chaudhari 
India Mumbai

---

### Post by Versusnja on 2008-12-22
Thanks for the advise!
lxappearance worked like a charm.

---

### Post by gychang on 2009-04-28
> **mali2297 said:**
> Post the content of the the gtkrc file. 

Just to be sure that it is in the right place and everything, use the command
```

cat ~/.gtkrc-2.0

```
from the terminal.

Also, post the output of
```

ls ~/.icons /usr/share/icons/ 

```
to see which icon themes that are available.

I also have the same problem, following is what I get, would appreciate the help.

apa@main-CB:~$ cat ~/.gtkrc-2.0
# DO NOT EDIT!  This file will be overwritten by LXAppearance.
# Any customization should be done in ~/.gtkrc-2.0.mine

gtk-theme-name="Redmond"
gtk-icon-theme-name="hicolor"
gtk-font-name="Sans 8"
gtk-toolbar-style=1
include "/home/apa/.gtkrc-2.0.mine"
apa@main-CB:~$ ls ~/.icons /usr/share/icons/
ls: cannot access /home/apa/.icons: No such file or directory
/usr/share/icons/:
cab_extract.png  default    dwm.png  remastersys.png  xchat.xpm
cab_view.png     DMZ-Black  gnome    skype.png
CrunchBang       DMZ-White  hicolor  Tango
apa@main-CB:~$ 

--

thanks,

gychang

---

### Post by mali2297 on 2009-04-29
> **gychang said:**
> I also have the same problem, following is what I get, would appreciate the help.

apa@main-CB:~$ cat ~/.gtkrc-2.0
# DO NOT EDIT!  This file will be overwritten by LXAppearance.
# Any customization should be done in ~/.gtkrc-2.0.mine

gtk-theme-name="Redmond"
gtk-icon-theme-name="hicolor"
gtk-font-name="Sans 8"
gtk-toolbar-style=1
include "/home/apa/.gtkrc-2.0.mine"
apa@main-CB:~$ ls ~/.icons /usr/share/icons/
ls: cannot access /home/apa/.icons: No such file or directory
/usr/share/icons/:
cab_extract.png  default    dwm.png  remastersys.png  xchat.xpm
cab_view.png     DMZ-Black  gnome    skype.png
CrunchBang       DMZ-White  hicolor  Tango
apa@main-CB:~$ 

--

thanks,

gychang

Post the output of
```

cat ~/.gtkrc-2.0.mine

```
as well.

Have you tried to correct the error with help of LXAppearance?

---

### Post by gychang on 2009-04-29
> **mali2297 said:**
> Post the output of
```

cat ~/.gtkrc-2.0.mine

```
as well.

Have you tried to correct the error with help of LXAppearance?

I entered the code:
---
apa@main-CB:~$ cat ~/.gtkrc-2.0.mine
cat: /home/apa/.gtkrc-2.0.mine: No such file or directory
apa@main-CB:~$ 
----

I have not tried to use LXAppearance, since I am not sure how to do it.

gychang

---

### Post by mali2297 on 2009-04-30
> **gychang said:**
> 
I have not tried to use LXAppearance, since I am not sure how to do it.


Look through the menus or open a terminal window and type
```

lxappearance

```
I have not used it but it should be rather straight-forward.

Alternatively, you could delete the line
```

include "/home/apa/.gtkrc-2.0.mine"

```
from the file gtkrc-2.0.

---

### Post by gychang on 2009-04-30
> **mali2297 said:**
> Look through the menus or open a terminal window and type
```

lxappearance

```
I have not used it but it should be rather straight-forward.

Alternatively, you could delete the line
```

include "/home/apa/.gtkrc-2.0.mine"

```
from the file gtkrc-2.0.

sorry but can't seem to find gtkrc-2.0, what directory will it be under?

gychang

---

### Post by mali2297 on 2009-05-01
> **gychang said:**
> sorry but can't seem to find gtkrc-2.0, what directory will it be under?

gychang

Sorry, it's **.gtkrc-2.0** (note the dot). It is a hidden file in your home folder.

---

### Post by gychang on 2009-05-01
> **mali2297 said:**
> Sorry, it's **.gtkrc-2.0** (note the dot). It is a hidden file in your home folder.

I deleted the line on the file and still getting the same error pop up.  Any other ideas will be greatly appreciated.

Here is the output of the file. With the .ine deleted.

--
# DO NOT EDIT!  This file will be overwritten by LXAppearance.
# Any customization should be done in ~/.gtkrc-2.0.mine

gtk-theme-name="Redmond"
gtk-icon-theme-name="hicolor"
gtk-font-name="Sans 8"
gtk-toolbar-style=1
--

gychang

gychang

---

### Post by mali2297 on 2009-05-01
Check the available themes with
```
ls /usr/share/themes/ ~/.themes
```
Is "Redmond" on the list? Otherwise, change the theme in .gtkrc-2.0.

---

