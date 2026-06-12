---
title: "Accessing gconf-2 values to change them"
date: 2007-01-23
forum: Programming Talk
---

### Post by wadesmart on 2007-01-23
01232007 1056 GMT-6

I found a artigle about gconftool -2 about accessing value pairs.

What I wanted to do was be able to change the background image in a way different than by right clicking. Im using php-cli on 6.06.

After reading the documentation for gconf (dry!) Im left still baffled. 

/desktop/gnome/background:
picture_filename = /home/wadesmart/wallpaper/NATURE-LimetItaly_1280x1024.jpg
picture_options = zoom
picture_opacity = 100
draw_background = true

Basically, the last line of my little app is:

```
system('gconftool-2 -t string -s /desktop/gnome/background/picture_filename'.$dirName.$DisplayImages[$Display]["name"]);
?>
```

However, where /picture_filename ends, how to you get it to take a value?
Its not : or = or "'or ". 

Wade

---

### Post by wadesmart on 2007-01-23
Got it!

```
system('gconftool-2 -t string -s /desktop/gnome/background/picture_filename '.$dirName.$DisplayImages[$Display]['name'].'');

```

---

