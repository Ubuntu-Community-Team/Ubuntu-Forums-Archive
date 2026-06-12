---
title: "File search by extension"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by osx on 2008-09-23
I'm trying to do something that seems like it would be very easy. I know I have done this in KDE before, but cannot seem to get it work in Ubuntu Gnome.

I want to find files with either the .jpeg or .jpg extensions. In KDE I would just enter *.jpeg;*.jpg in the browser, but this will not work in Gnome. Is there a way to do this in Gnome? I'm using the "Search for Files" feature located in the "Places" menu.

Is this a Gnome issue or an Ubuntu issue? I was doing this in KDE from Knoppix.

Thanks.

---

### Post by osx on 2008-09-23
By the way, I know how to do this from the command line, I need to know how to do this from the GUI for teaching some newbies.

---

### Post by engtg on 2008-09-24
Try *.jpeg* [COLOR="Red"]with no ;[/COLOR]

---

### Post by jemate18 on 2008-09-24
If in case one is curius how to do it in the command line.....


[COLOR="DarkRed"]find[/COLOR] [COLOR="SeaGreen"]/home/xxxxxx[/COLOR] [COLOR="Teal"]-name [/COLOR] "*.jpg"

[COLOR="DarkRed"]find -> the command to search for files[/COLOR]

[COLOR="SeaGreen"]/home/xxxxxx[/COLOR] -> the location you want to search..

[COLOR="Teal"]-name [/COLOR] -> the option passed to command find

"*.jpg" -> the extension of th file you want to search....

---

### Post by osx on 2008-09-24
> **engtg said:**
> Try *.jpeg* [COLOR="Red"]with no ;[/COLOR]

That works, but I want to be able to search by multiple file extensions at once. For example, I want to search for all JPEGs and PNGs at once. Trying something like *.jp*;*.png does not work.

Thanks.

---

### Post by engtg on 2008-09-28
Try this
*[.png.jpeg]*

---

### Post by jemate18 on 2008-09-28
try this in the command line.....```
find /home/user/folder -name "*[.png\|.jpeg]"

```

you can change the location of /home/user/folder

---

