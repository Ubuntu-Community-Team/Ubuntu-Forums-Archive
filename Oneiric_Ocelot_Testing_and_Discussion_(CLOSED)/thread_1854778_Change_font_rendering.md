---
title: "Change font rendering"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by wladyx on 2011-10-05
Hello,
Does anyone know if it possible to change the font rendering like it was possible in 11.04?
I always used "Best Shapes".
Thanks for any suggestions.

---

### Post by lucazade on 2011-10-05
you could try to change it via dconf-editor in 
org.gnome.settings-daemon.plugins.xsettings

there is hinting option:
The type of hinting to use when rendering fonts. Possible values are: "none" for no hinting, "slight" for basic, "medium" for moderate, and "full" for maximum hinting (may cause distortion of letter forms).

and antialiasing:
The type of antialiasing to use when rendering fonts. Possible values are: "none" for no antialiasing, "grayscale" for standard grayscale antialiasing, and "rgba" for subpixel antialiasing (LCD screens only).

---

### Post by wladyx on 2011-10-05
So actualy the antialiasing setting is the same as 11.04 Rendering/Smoothing? Like in the attached pictures?
Thanks

---

### Post by lucazade on 2011-10-05
yep.. that was the frontend for those settings, in 11.04 was based on gconf and now on dconf.
unfortunately we have no more an easy gui to change it, dconf-editor seems the only way.

---

### Post by wladyx on 2011-10-05
Actually there is: gnome-tweak-tool.

---

### Post by lucazade on 2011-10-05
oh right.. i don't use it lately so i totally forgot it :)

---

### Post by jahLux on 2011-10-05
> **lucazade said:**
> you could try to change it via dconf-editor in 
org.gnome.settings-daemon.plugins.xsettings

there is hinting option:
The type of hinting to use when rendering fonts. Possible values are: "none" for no hinting, "slight" for basic, "medium" for moderate, and "full" for maximum hinting (may cause distortion of letter forms).

and antialiasing:
The type of antialiasing to use when rendering fonts. Possible values are: "none" for no antialiasing, "grayscale" for standard grayscale antialiasing, and "rgba" for subpixel antialiasing (LCD screens only).

What if you're not using GNOME 3 - but rather, UNITY ? Seems like there's no longer a provision for this valuable tool.

---

### Post by philinux on 2011-10-05
> **lucazade said:**
> oh right.. i don't use it lately so i totally forgot it :)

I got a major surprise when I found it too.

[http://ubuntuforums.org/showthread.php?t=1843502](http://ubuntuforums.org/showthread.php?t=1843502)

---

### Post by stopsatgreen on 2011-10-08
Just upgraded to Oneiric and the first thing I wanted to do was get rid of the *huge* default system font. Quite shocked to find out that I had to jump through hoops in order to do something so basic.

---

### Post by el_koraco on 2011-10-08
You gnome people are so spoiled. For the "best shapes" option, make a .fonts.conf file in $HOME, add this in:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
<match target="font">
   <edit mode="assign" name="lcdfilter">
   <const>lcddefault</const>
   </edit>
 </match>
<match target="pattern">
   <edit name="dpi" mode="assign">
   <double>96</double></edit>
</match>
</fontconfig>

```

Obviously, replace the 96 dpi value with your prefered one. Find it via ```
xdpyinfo | grep dots

```

If anything goes wrong, remove the file and voila.

---

### Post by WorLord on 2011-10-09
> **jahLux said:**
> What if you're not using GNOME 3 - but rather, UNITY ? Seems like there's no longer a provision for this valuable tool.

Unity IS Gnome 3.  This is why Gnome-tweak-tool affects Unity as well.

One can use Gnome 3 WITHOUT using Gnome-shell; I think that's where the confusion lies.

---

### Post by t1497f35 on 2011-10-09
> **WorLord said:**
> Unity IS Gnome 3.  This is why Gnome-tweak-tool affects Unity as well.

One can use Gnome 3 WITHOUT using Gnome-shell; I think that's where the confusion lies.

No, Unity is not Gnome 3.
You're probably confusing gtk3 with Gnome 3.

---

