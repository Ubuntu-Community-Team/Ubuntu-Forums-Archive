---
title: "reszing photos"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by blairm on 2008-09-27
Hi,

In Windows, I'm able to resize photos by right clicking on them and hitting resize - that opens a menu of choices ie small, medium etc.

In Ubuntu I've been using Gimp, but it's really too much for what is needed - for quick and dirty resizing, is there any way I could replicate the Windows behaviour?

Cheers,

Blair

---

### Post by fooman on 2008-09-27
here is a neat little addition to nautilus that will do what you ask.  it adds "resize image" and "rotate image" to the right-click context menu:

```
sudo apt-get install nautilus-image-converter
```

---

### Post by mike1234 on 2008-09-27
> **fooman said:**
> here is a neat little addition to nautilus that will do what you ask.  it adds "resize image" and "rotate image" to the right-click context menu:

```
sudo apt-get install nautilus-image-converter
```
   

 This is why I enjoy UF. Little tips and tricks you pick up from hanging around. I wish most of the naysayers on here would just relax and take the time to learn about Ubuntu. I'm so used to .deb packages now most of the other distros seem alien to me now. 

M.

---

### Post by kansasnoob on 2008-09-27
> **fooman said:**
> here is a neat little addition to nautilus that will do what you ask.  it adds "resize image" and "rotate image" to the right-click context menu:

```
sudo apt-get install nautilus-image-converter
```

Awesome!

---

### Post by hubie on 2008-09-27
If you are OK with the command line, you can use Imagemagick to resize with a simple [convert]("http://www.imagemagick.org/Usage/resize/#resize") command.  You can even do all the images in the directory at once, if you want:
```
$convert *.jpg -resize 640x320 resize_%d.jpg
```
I'm pretty sure that command will work, unless the resize needs to go on the right.

You can probably even go that extra step and emulate your Windows functionality by adding the convert command to the right-click menu in Gnome by using [FONT="Fixedsys"]nautilus-actions[/FONT].  Check out [this post]("http://ubuntuforums.org/showthread.php?t=264500") to see how.

Edit:  Boy, I do a little research and come back to see much better answers posted than mine! :)

---

### Post by kansasnoob on 2008-09-27
> **hubie said:**
> If you are OK with the command line, you can use Imagemagick to resize with a simple [convert]("http://www.imagemagick.org/Usage/resize/#resize") command.  You can even do all the images in the directory at once, if you want:
```
$convert *.jpg -resize 640x320 resize_%d.jpg
```
I'm pretty sure that command will work, unless the resize needs to go on the right.

You can probably even go that extra step and emulate your Windows functionality by adding the convert command to the right-click menu in Gnome by using [FONT="Fixedsys"]nautilus-actions[/FONT].  Check out [this post]("http://ubuntuforums.org/showthread.php?t=264500") to see how.

Edit:  Boy, I do a little research and come back to see much better answers posted than mine! :)

Is there a gui front end available for that?

I do a lot of imaging work and appreciate anything and everything new! But I'm a gui guy!

---

### Post by akiratheoni on 2008-09-27
> **kansasnoob said:**
> Is there a gui front end available for that?

I do a lot of imaging work and appreciate anything and everything new! But I'm a gui guy!

Well there was the solution posted above:

> sudo apt-get install nautilus-image-converter

Then you'll get the right-click options.

Unfortunately I use Thunar, not Nautilus :( does any one know of a Thunar equivalent for the command I just posted?

---

### Post by hubie on 2008-09-27
> **kansasnoob said:**
> Is there a gui front end available for that?

I do a lot of imaging work and appreciate anything and everything new! But I'm a gui guy!

From the looks of the nautilus-image-converter [homepage]("http://www.bitron.ch/software/nautilus-image-converter.php"), I think that package does exactly what I described.

I didn't know I was so smart. :)

---

### Post by hubie on 2008-09-27
> **akiratheoni said:**
> Unfortunately I use Thunar, not Nautilus :( does any one know of a Thunar equivalent for the command I just posted?

[This post]("http://wiki.zenwalk.org/index.php?title=HOWTO_create_%27Open_as_Root%27_option_in_Thunar_right-click_menu") shows you how to add an "Open as Root" right-click option to Thunar.  You can follow those instructions but change the command you put in to something like what I posted above using [FONT="Fixedsys"]convert[/FONT].  You can add commands for [FONT="Fixedsys"]-size[/FONT], [FONT="Fixedsys"]-rotate[/FONT], [FONT="Fixedsys"]-scale[/FONT], etc.

---

### Post by blairm on 2008-09-29
Thanks to everyone for your replies - the nautilus thing is just what I was after!

Blair

---

