---
title: "Set file associations with Irfanview on ubuntu 11.10?"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by try1211 on 2012-04-07
Hello! This is my first post in the forums! I am new to the Linux world (I've been playing around with Ubuntu since 10.04) and as of 11.10 I made the leap to a Ubuntu only pc. Yey!

However, theres still one windows app I just can't live without... After hours and hours and hours of research (remember, I'm new to this) I figured out how to install and configure wine to run the latest version of IrfanView (v4.33). But it sucks that I can't set Irfanview as the default picture viewer and I've scoured these and other forums for the answer but nothing I find works. 

So if anyone knows the secret of how I can set IrfanView as the default app for opening picture files on wine1.3 & ubuntu11.10, I would be eternally grateful if you shared it with me!

---

### Post by lykeion on 2012-04-07
Hi and welcome to the forums. When I moved from Windows to Linux (long time ago) I still wanted to use some of the good software that I've gotten used to in Windows. It took some time but gradually I found they all could be replaced with Linux applications.

So my first advice would be to try out some Linux image viewers like gThumb and xnview. See if you could do the same in these viewers as you would in IrfanView. If not keep searching, there are lots of image/photo viewers written for Linux (and personally I think it's kind of fun to try out new software).

My second advice is just a link where someone shows how to make .psd files open with Photoshop installed with wine. The procedure for IrfanView would be the same I guess:
[http://blog.thewebsitepeople.org/2010/12/nautilus-open-with-mime-type-associations/](http://blog.thewebsitepeople.org/2010/12/nautilus-open-with-mime-type-associations/)

Good luck

---

### Post by bodhi.zazen on 2012-04-07
When trying to get applications running on wine, you shoule search the winehq database

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834)

See also 

[http://ubuntuforums.org/showthread.php?t=1702848](http://ubuntuforums.org/showthread.php?t=1702848)

---

### Post by try1211 on 2012-04-07
> **lykeion said:**
> Hi and welcome to the forums. When I moved from Windows to Linux (long time ago) I still wanted to use some of the good software that I've gotten used to in Windows. It took some time but gradually I found they all could be replaced with Linux applications.

So my first advice would be to try out some Linux image viewers like gThumb and xnview. See if you could do the same in these viewers as you would in IrfanView. If not keep searching, there are lots of image/photo viewers written for Linux (and personally I think it's kind of fun to try out new software).

My second advice is just a link where someone shows how to make .psd files open with Photoshop installed with wine. The procedure for IrfanView would be the same I guess:
[http://blog.thewebsitepeople.org/2010/12/nautilus-open-with-mime-type-associations/](http://blog.thewebsitepeople.org/2010/12/nautilus-open-with-mime-type-associations/)

Good luck

Thank you.  I like to try out new software myself, and I've tried using gThumb, Shotwell, Inkscape, and Gimp but I just dont like shotwell, Inkscape & Gimp are just too slow when trying to quickly edit, & resize a directory full of images, and I like gThumb but theres some essential shortcuts and features that it just doesn't have.  For the most part, I already know the ins and outs of irfanview and if I can run it on ubuntu I dont see why I would have to learn a whole new program...

And I tried that shortcut with photoshop (modified it to use irfanview) and the script works, it runs irfanview. But when I double-click or try to run the .desktop file pointing to the script nothing happens...

I'm thinking I must have did something wrong, this is how I edited the script and .desktop files:

```
#!/bin/ksh
param=
while [ "$1" ]
do
  param="$param Z:$1"
  shift
done
wine "C:\Program Files\IrfanView\i_view32.exe" $param
```

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/usr/IrfanView-icon.png
Name[en_US]=IrfanView
Exec=~/.local/share/applications/IrfanView %f
Name=IrfanView
Icon=gnome-panel-launcher
MimeType=image/jpeg;image/png;
```


> **bodhi.zazen said:**
> When trying to get applications running on wine, you shoule search the winehq database

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834)

See also 

[http://ubuntuforums.org/showthread.php?t=1702848](http://ubuntuforums.org/showthread.php?t=1702848)

Thank you for this, but I haven't had any trouble getting IrfanView to run.  IrfanView runs perfectly fine.  I was just wondering if there was a way to double click on an image file and have it open in IrfanView vs having to open irfanview and open an image from within the open file dialog.

---

### Post by bodhi.zazen on 2012-04-07
> **try1211 said:**
> Thank you for this, but I haven't had any trouble getting IrfanView to run.  IrfanView runs perfectly fine.  I was just wondering if there was a way to double click on an image file and have it open in IrfanView vs having to open irfanview and open an image from within the open file dialog.

Usually WineHQ will have tips for things like this, it is a good place to start.

---

### Post by Jerry N on 2012-04-08
> **lykeion said:**
>  So my first advice would be to try out some Linux image viewers like gThumb and xnview. 

The linux version of xnview is very old and frankly stinks.  There is a developmental program called XnviewMP (multi platform) that does run in linux, as well as Windows and Mac, but as far as I know it is still incomplete.  I use the Windows version of xnview in Crossover and it works fine but I have never tried to make it the default viewer.  I haven't found any linux programs yet that are as comprehensive as xnview and irfanview.

Jerry

---

### Post by try1211 on 2012-04-08
> **bodhi.zazen said:**
> Usually WineHQ will have tips for things like this, it is a good place to start.

I checked WineHQ and there was only one relevant post to the problem I have, which was the last one on the page, and it was from 2007 and it basically suggested I do what I did above^.

I've edited mimeapps.list to set my IrfanView.desktop file as the default for jpeg&png image types, I made sure I saved the irfanview script in the locating I put in the .desktop. Is there a different argument I should use after 
```
Exec=~/.local/share/applications/IrfanView %f
```
instead of the %f, of course?

---

### Post by lykeion on 2012-04-08
The link I gave you in the 2nd post was perhaps more confusing than helping.
What you can do is this (from [this ubuntu help page]("https://help.ubuntu.com/community/Wine#Creating_file_associations")):

1) Create a script where you open the passed filename parameter with photoshop.
This simple example script takes one filename as parameter (if you need to pass several files to it you need to change it) and opens it up with wine application Notepad (change it to your Photoshop path)
```
#!/usr/bin/env bash
QUICKPARLOCATION="C:\\Windows\\Notepad.exe"
PARAM=`winepath -w "$*"`
wine "$QUICKPARLOCATION" "$PARAM"
exit 0
```

2) Make it executable
After saving the file, rightclick it > properties... > permissions tab > check Allow executing file as program.

3) Then you can set an image file to be opened with your script and make this as default.
Rightclick image file > open with > other application.. > use custom command > browse > select your script file > check Remember this application for...

Hope this helps

---

### Post by Mud.Knee.Havoc on 2012-04-08
> **try1211 said:**
> resize a directory full of images

Back when I used Windows, I loved Irvanview because it was the only program I could find that did batch resizing.

Linux, though, has imagemagick (a commandline program which does batch resizing with the -resize switch) and a handy file manager plugin which does the same thing in a graphical way (it's called nautilus-image-converter - you just select all of the pictures you want to resize, right click and tell it how big to make them).

As soon as I found these, I never looked back!

---

### Post by try1211 on 2012-04-09
> **lykeion said:**
> 
3) Then you can set an image file to be opened with your script and make this as default.
Rightclick image file > open with > other application.. > use custom command > browse > select your script file > check Remember this application for...

I've seen this method in a few forums before and I tried it but apparently the ability to use another app or command NOT in the "open with" list is not possible in 11.10.  Its not a bug, for some reason the developers actually left the option out, or so I've read. It doesn't let me browse for another app or enter a command...

@Mud.Knee.Havoc: Are both those apps available in the software centre? I figure I'd give them a try, but I still want my Irfanview.  I'm stubborn like that. lol

Hope everybody had a Happy Easter!

---

