---
title: "little script to generate gnome wallpaper slideshow xml"
date: 2010-05-19
forum: Programming Talk
---

### Post by muebau on 2010-05-19
Hi, I created just a little script to create the XML file for gnome  wallpaper slideshows.
usage: ./createBackgroundXML.sh <hold duration> <fade duration> file1  file2 ...
example: ./createBackgroundXML.sh 120 10 ~/bgrounds/*.jpg > bg.xml
To use  the background just use the default dialog and choose "add"-->"all  files"
Please give feedback.
Bye muebau

PS:
More info
[http://www.linuxjournal.com/content/create-custom-transitioning-background-your-gnome-228-desktop](http://www.linuxjournal.com/content/create-custom-transitioning-background-your-gnome-228-desktop)

---

### Post by unc0nn3ct3d on 2010-07-12
Genius!  Nice work, was going to write one of these handy little guys but you saved me the trouble.. Just downloaded dozens and dozens of new wallpapers from [http://joejesus.deviantart.com](http://joejesus.deviantart.com) and was dreading coding that xml all by hand.  But then I thought 'Hey, I use linux for a reason, there's scripting for all this manual labour' and so here I am!

---

### Post by Gamgigo on 2010-07-14
Brilliant piece of software. Been looking for this for ages.:P

---

### Post by Köntzä on 2010-12-05
Hi,

Great script but to make it even greater is to use *readlink* to refer to all files so that you get absolute paths to files.

The fix is easy, replace all occurrences of $1, $2, and $first with
```
$(readlink -f $1)
$(readlink -f $2)
$(readlink -f $first)
```
respectively.

---

### Post by johnmay on 2010-12-05
That is a great little script! 

Does anyone know the difference between the slideshow script and the screensaver script? 

The slide show is cool and all, but the screensaver will place different wallpaper on each monitor. I am curious if it would really drag my system to have a different wallpaper.

Thanks!

---

### Post by Cybernot on 2011-01-25
Hi

I just modified this script ([http://code.google.com/p/gnome-wallpaper-slideshow/](http://code.google.com/p/gnome-wallpaper-slideshow/)) so that it scan recursively directory for picture for wall papers. I needed that because my picture are ordered by year and event inside other directories.

I attached my modified script... its my first time with python so its probable that someone could do a better job. You have to "browse" and select the directory each time you open the script. If you only open it and click validate somehow it does not work.

btw, thank for the initial script

---

### Post by welf on 2011-03-02
Your modified script worked well for me thanks!

Now if only there was some way of randomising the order...
(but I guess that's difficult given that it's an xml file?)

---

### Post by welf on 2011-03-13
Actually I did find a way of getting a random wallpaper, using the script given here:
[http://forums.debian.net/viewtopic.php?f=16&t=60791](http://forums.debian.net/viewtopic.php?f=16&t=60791)

I think I made a few tweaks to it, but it is now working fine.

---

