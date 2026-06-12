---
title: "How do I find my desktop background image?"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by Nixarter on 2012-04-11
So I took a panorama a while ago and the hard drive crashed, now the only copy I have is my desktop background.  But I haven't been able to figure out where it actually is.  How do I find my picture?

---

### Post by winh8r on 2012-04-11
Just a suggestion

have a look in /usr/share/backgrounds

It might be there unless you have it linked to from another location.


***edit*** 

when you go to change backgrounds , the location of the image should be shown along with its details as you move your mouse over the image.

---

### Post by gandalf3 on 2012-04-11
it should be under /usr/share/backgrounds in the file system.
hope this helps!

oops.. winh8r got here first.. while i was typing..

---

### Post by stinkeye on 2012-04-11
Look in 
```
~/.gconf/desktop/gnome/background/%gconf.xml
```
for the location.

---

### Post by evilsoup on 2012-04-11
Also, you can right-click your desktop and select 'Change Desktop Background', and then hover the pointer over the image you want, and that will show you the absolute path to the directory it is in.

---

### Post by stinkeye on 2012-04-11
> **evilsoup said:**
> Also, you can right-click your desktop and select 'Change Desktop Background', and then hover the pointer over the image you want, and that will show you the absolute path to the directory it is in.

> So I took a panorama a while ago and the **_hard drive crashed_**
Will most likely be doing this from a live cd.

---

### Post by Nixarter on 2012-04-11
> **stinkeye said:**
> Look in 
```
~/.gconf/desktop/gnome/background/%gconf.xml
```for the location.

how do I get there?  I can't find it..

and the image isn't in the backgrounds folder.  When I hover over the small computer screen (sample) with the image, it does nothing.

---

### Post by stinkeye on 2012-04-11
The file should be there.
"~" is short for **/home/USERNAME** AND .gconf is a hidden file (ctrl+h to show hidden).

eg for me the directory is 
```
/home/glen/.gconf/desktop/gnome/background/%gconf.xml
```

and the file shows the location of my chosen desktop background.
```
<?xml version="1.0"?>
<gconf>
	<entry name="draw_background" mtime="1333142280" type="bool" value="true"/>
	<entry name="picture_filename" mtime="1333845571" type="string">
		<stringvalue>[COLOR="Red"]file:///home/glen/Pictures/wallpaper/mushroomlake_wds.jpg[/COLOR]</stringvalue>
	</entry>
</gconf>
```

---

