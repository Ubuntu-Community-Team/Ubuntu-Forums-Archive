---
title: "HOWTO: Font de-uglification"
date: 2005-04-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Gianni Exile on 2005-04-17
This one's simple... set DisplaySize as in 
[http://www.ubuntuforums.org/showthread.php?t=20976](http://www.ubuntuforums.org/showthread.php?t=20976)
(Ignore all the other stuff there).

Now X11 has dpi 96.  Make sure Gnome sees it, run
"gnome-font-properties" hit Details and double check it's 96.

Now type, as your regular user name at a shell prompt, for KDE and other Xft apps: ```
echo "Xft.dpi:96" >> ~/.Xresources
```

Lastly, edit ~/.fonts.conf ... here's mine. I merely changed the range to exclude from antialiasing from sizes 8-15 (pixel size 11-20) to sizes 8-11 (pixel 11-15).
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
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <test compare="more" name="size" qual="any" >
   <double>8</double>
  </test>
  <test compare="less" name="size" qual="any" >
   <double>11</double>
  </test>
  <edit mode="assign" name="antialias" >
   <bool>false</bool>
  </edit>
 </match>
 <match target="font" >
  <test compare="more" name="pixelsize" qual="any" >
   <double>11</double>
  </test>
  <test compare="less" name="pixelsize" qual="any" >
   <double>15</double>
  </test>
  <edit mode="assign" name="antialias" >
   <bool>false</bool>
  </edit>
 </match>
</fontconfig>

```

Restart X (ctrl-alt-bksp) or reboot.

Now both Gnome and KDE fonts will be rendered correctly.

---

### Post by gnubios on 2005-04-17
wow, thanx.. working here :P

---

### Post by jonny on 2005-04-17
What fonts is this going to de-uglify?  My normal gnome fonts are great, but other apps (eg KDE) look horrible.

Do I need this how-to or not?

---

### Post by Graben on 2005-04-17
To fix your kde fonts just apt-get install kcontrol, and change them to what they are in gnome.  And turn on font anti-aliasing.

---

### Post by Gianni Exile on 2005-04-27
[QUOTE=Graben]To fix your kde fonts just apt-get install kcontrol, and change them to what they are in gnome.  And turn on font anti-aliasing.[/QUOTE]

Which will write out the exact ~/.fonts.conf file I posted above...

---

### Post by Sionide on 2005-04-27
I'm gonna try this anyway but it would be nice to see before and after screenshots so people can see the difference

---

### Post by Anguilla on 2005-04-27
the resault is quite orrible, for me maybe I made a mistake...
I hope this is not what we have to get...

---

### Post by veritas366 on 2005-04-27
system>preferences>font seems to have a lot of options.  Maybe there aren't enough?  I like my fonts..but I don't know much about all the various options.  They change instantly, though, so you can check them out and switch to another option easily.

---

