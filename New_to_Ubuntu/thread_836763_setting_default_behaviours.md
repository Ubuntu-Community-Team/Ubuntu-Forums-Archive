---
title: "setting default behaviours"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by leemajors on 2008-06-21
hey..

i've got a two part question...

while trying to figure out how to use vlc to play my audio and video files by default i stumbled across the "media" tab under "file management preferences" in the file browser, which has a bunch of "what do i do if you insert a..." kind of options. The options I wanted to be there weren't, for example I want Songbird to be my Music player and Picasa to run when I insert a disc with photos on it. 

So my two questions:

1. how do i make it so VLC is the default media player (register it with all relevant file types)

2. how do i add items to the dropdown list of programs to use when inserting media?

Thanks :)

---

### Post by mc4man on 2008-06-21
here's an easy way to set vlc
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)
The other 2 could prove problematic in hardy as far as autorun. I'll try them on a test box I don't mind borking in the near future.

Actually above only relates to dvd video, in defaults.list you can change the two below also vcd, svcd
Any other file types set by right click on file -> properties -> open with

---

### Post by leemajors on 2008-06-21
i see so saying "open file with..." and choosing the program will actually set it as the default?

---

### Post by benny bronx on 2008-06-21
Yes, for that type of file.  And the programs in that list will be included in your context menu.

---

### Post by mc4man on 2008-06-21
> i see so saying "open file with..." and choosing the program will actually set it as the default
Not exactly, it will possibly give it a separate listing on r.click menu at top. To set as default (where double clicking usually will open the app) go r.click -> _properties -> then open with_. There is a difference.

Edit In the properties open with box look for your chosen app and if it's there click the little circle. If it's not there (in the list) click add for an expanded list and if you find it choose add. Then make sure the little circle is filled next to it.

---

### Post by leemajors on 2008-06-24
that's really helpful thanks to all!

---

