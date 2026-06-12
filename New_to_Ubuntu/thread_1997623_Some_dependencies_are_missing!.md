---
title: "Some dependencies are missing!"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by Shadius on 2012-06-05
Hey everybody!

I'm trying to install this [icon theme]("http://gnome-look.org/content/show.php/?content=102435"), and after running the command, I get "Some dependencies are missing!". So how do I continue? 

Output:
```
shadius@shadius-5410US:~$ cd ~/.icons/ACYL_Icon_Theme_0.9.4/ && bash AnyColorYouLike
Some dependencies are missing!
The following ones are required:
gtk, gtk.glade, sys, os, subprocess,
shutil, gettext, ConfigParser
Traceback (most recent call last):
  File "/home/shadius/.icons/ACYL_Icon_Theme_0.9.4/scalable/scripts/script_gui.py", line 23, in <module>
    sys.exit(1)
NameError: name 'sys' is not defined
shadius@shadius-5410US:~/.icons/ACYL_Icon_Theme_0.9.4$ 

```

---

### Post by snowpine on 2012-06-05
This script is not provided by Ubuntu so you would have to ask the person who wrote it.

Judging by the fact it was uploaded in 2009 my guess is that this script has not been tested/intended for the current Ubuntu release. There have been some **major** changes to Ubuntu's graphical interface in the past 3 years.

---

### Post by wildmanne39 on 2012-06-05
Hi, using unity, you need to make sure you use the themes built for GTK3, and +1 to snowpine's answer that script is so old it would depend on GTK2.
Thanks

---

### Post by Shadius on 2012-06-05
I forgot the mention that I'm not using Unity. I'm using GNOME Classic (No effects).

---

### Post by wildmanne39 on 2012-06-05
Hi, it still uses GTK3.

---

### Post by Shadius on 2012-06-05
> **wildmanne39 said:**
> Hi, it still uses GTK3.

Okay, I really don't know what that means. GTK3, GTK2? :confused: What's the difference besides the 3 & 2?

---

### Post by snowpine on 2012-06-05
Personally I think it is a really bad idea to download and execute random scripts from the interwebz, unless you a) completely trust the person providing the script; and b) know exactly what the script does; and c) are sure the script is compatible with your specific Ubuntu release. 

If you install themes and icons from the Ubuntu repositories using the Software Center, then you shouldn't have any dependency issues. :)

---

### Post by wildmanne39 on 2012-06-05
Hi, I did not find much to help explain it but here is a link.
[http://www.gtk.org/](http://www.gtk.org/)
GTK2 is obsolete is the main thing you need to know.
Thanks

---

### Post by Shadius on 2012-06-05
Ohhhh okay. I didn't know the Ubuntu Software Center had themes too. I'm such a beginner. ](*,) Okay, so since GTK+ 2 (GIMP Toolkit) is obsolete, I'm assuming GTK+ 3 replaced GTK+ 2? So GNOME used to used GTK+ 2 and is now using GTK+ 3? Clarify my confusion please. :)

---

### Post by snowpine on 2012-06-05
Yes, and someday it will use GTK+4, and then GTK+5, and so forth.
It is important to install trusted software specifically intended for your Ubuntu release, **if** you want to have the most stable experience.

---

### Post by Shadius on 2012-06-05
> **snowpine said:**
> Yes, and someday it will use GTK+4, and then GTK+5, and so forth.
It is important to install trusted software specifically intended for your Ubuntu release, **if** you want to have the most stable experience.

Ohhhh I see, I see. Thank you for helping me understand. At some point GNOME used to use GTK+ 2?

---

### Post by wildmanne39 on 2012-06-05
Hi, yes it did hence the word GTK2 is obsolete.
Thanks

---

### Post by Shadius on 2012-06-05
> **wildmanne39 said:**
> Hi, yes it did hence the word GTK2 is obsolete.
Thanks

Gotcha. So GNOME 3 is related to GTK+3. GTK+3 makes up GNOME 3, correct? If so, it's correct to say that GNOME 2 is related to GTK+2?

---

### Post by vasa1 on 2012-06-05
Even if one is now on GNOME 3, there are several apps that are still gtk-2.0.

So if you're looking for a theme, it should accommodate **both** gtk-3.0 and gtk-2.0 apps. If not, you'll have discordant appearances.

Examples of apps that are still stuck at gtk-2.0 would be Firefox, Chrome and LibreOffice.

---

### Post by Shadius on 2012-06-05
> **vasa1 said:**
> Even if one is now on GNOME 3, there are several apps that are still gtk-2.0.

So if you're looking for a theme, it should accommodate **both** gtk-3.0 and gtk-2.0 apps. If not, you'll have discordant appearances.

Examples of apps that are still stuck at gtk-2.0 would be Firefox, Chrome and LibreOffice.

How can I figure out if a theme accommodates both GTK+2 and GTK+3? I've been installing a bunch of themes in trying to find the look that suits me, but I haven't found that look yet. I think it's just the lack of knowledge on my part.

---

### Post by vasa1 on 2012-06-05
> **Shadius said:**
> How can I figure out if a theme accommodates both GTK+2 and GTK+3? I've been installing a bunch of themes in trying to find the look that suits me, but I haven't found that look yet. I think it's just the lack of knowledge on my part.
I don't know. I don't install "outside" themes. I stick with Ambiance and tweak it a bit.
But a theme that supports both gtk-2.0 and gtk-3.0 would have something like this:
```
:/usr/share/themes/Ambiance$ ls -l
total 20
drwxr-xr-x 3 root root 4096 Jun  5 16:06 gtk-2.0
drwxr-xr-x 4 root root 4096 May 25 20:10 gtk-3.0
-rw-r--r-- 1 root root  247 Feb  8 20:48 index.theme
drwxr-xr-x 2 root root 4096 Apr 21 12:44 metacity-1
drwxr-xr-x 2 root root 4096 Apr 21 12:44 unity

```Note the subdirectories, gtk-2.0 and gtk-3.0. This is from Ambiance in 12.04.

---

### Post by Shadius on 2012-06-05
> **vasa1 said:**
> I don't know. I don't install "outside" themes. I stick with Ambiance and tweak it a bit.
But a theme that supports both gtk-2.0 and gtk-3.0 would have something like this:
```
:/usr/share/themes/Ambiance$ ls -l
total 20
drwxr-xr-x 3 root root 4096 Jun  5 16:06 gtk-2.0
drwxr-xr-x 4 root root 4096 May 25 20:10 gtk-3.0
-rw-r--r-- 1 root root  247 Feb  8 20:48 index.theme
drwxr-xr-x 2 root root 4096 Apr 21 12:44 metacity-1
drwxr-xr-x 2 root root 4096 Apr 21 12:44 unity

```Note the subdirectories, gtk-2.0 and gtk-3.0. This is from Ambiance in 12.04.

Since you mentioned tweaking. I do like the default Adwaita and Ambiance themes, however, I would like to tweak some elements of those themes. Like I want the Adwaita style panel, but the dark window theme of Ambiance, a dark toolbar, and instead of the blue highlight color of Adwaita, I prefer the orange of Ambiance. I would love to do that, but I have no idea how to.

---

### Post by vasa1 on 2012-06-05
> **Shadius said:**
> Since you mentioned tweaking. I do like the default Adwaita and Ambiance themes, however, I would like to tweak some elements of those themes. Like I want the Adwaita style panel, but the dark window theme of Ambiance, a dark toolbar, and instead of the blue highlight color of Adwaita, I prefer the orange of Ambiance. I would love to do that, but I have no idea how to.
I put what I did in a thread somewhere here soon after 12.04 was released but it's close to my bedtime and so I'm away ...

---

### Post by Copper Bezel on 2012-06-05
Oh, I think I remember this. I downloaded the theme again, and it still works for me, but I think I simply installed the related packages. They're all Python packages.

It's not that the *icon theme* does or doesn't use GTK3 - icon themes didn't change in the transition to Gnome 3, except for a new category for panel icons. However, the script you're launching actually runs a full windowed application for editing the icon set, and it still works, but....

That icon *editor* uses GTK2, and it's written in Python, which has an interpreter / runtime environment. That interpreter's capabilities are extended by adding packages that give it additional libraries to work with, and a lot of Python packages related to running GTK2 applications are no longer installed by default. For instance, I think you need the packages python-glade2 and python-gtk2. But I really can't guess which other packages are required - I have an absurd number of Python packages installed on my machine.

Sorry. = /

---

### Post by Shadius on 2012-06-06
> **Copper Bezel said:**
> Oh, I think I remember this. I downloaded the theme again, and it still works for me, but I think I simply installed the related packages. They're all Python packages.

It's not that the *icon theme* does or doesn't use GTK3 - icon themes didn't change in the transition to Gnome 3, except for a new category for panel icons. However, the script you're launching actually runs a full windowed application for editing the icon set, and it still works, but....

That icon *editor* uses GTK2, and it's written in Python, which has an interpreter / runtime environment. That interpreter's capabilities are extended by adding packages that give it additional libraries to work with, and a lot of Python packages related to running GTK2 applications are no longer installed by default. For instance, I think you need the packages python-glade2 and python-gtk2. But I really can't guess which other packages are required - I have an absurd number of Python packages installed on my machine.

Sorry. = /

Greatly appreciate your help!

---

