---
title: "change desktop icons"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by Xubuntist on 2014-03-16
hello, i read everywhere on here that its easy to change a desktop icon by clicking on its image if you go to its properties
i added a shortcut to the desktop for the images folder bu i wanted to change it to something more colourful
in its properties these is for sure the picture of the icon but i cant click on it
also, i have these emblems but when i use a picture of a photo or camera the icon on the desktop doesn't change
what are emblems if they're not shortcuts, sorry for stupidity of my qustions)
please can you tell me how to just simply change the icon of a desktop shortcut
many many thanks, its driving me to drink and drugs and other things bad for the liver and kidneys ](*,)](*,)](*,)
francois

---

### Post by Toz on 2014-03-16
> **Xubuntist said:**
> hello, i read everywhere on here that its easy to change a desktop icon by clicking on its image if you go to its properties
Yes, but for launchers only.
> i added a shortcut to the desktop for the images folder... 
Sounds like you created a link. Did you use the "Send To-Desktop (Create Link)" option in Thunar?
> ...bu i wanted to change it to something more colourful
in its properties these is for sure the picture of the icon but i cant click on it
No you can't for this type of link (or at least, no easily).
> also, i have these emblems but when i use a picture of a photo or camera the icon on the desktop doesn't change
what are emblems if they're not shortcuts, sorry for stupidity of my qustions)
Emblems are for folders only, and they only work in Thunar, not on the desktop. They are little indicators that take up the right-bottom corner of the icon - they don't change the icon.
> please can you tell me how to just simply change the icon of a desktop shortcut
many many thanks, its driving me to drink and drugs and other things bad for the liver and kidneys ](*,)](*,)](*,)
francois
Here is one way. Right-click on the desktop and select "Create URL Link". Give it a Name and a comment, and for the URL, specify:
```
file:///path/to/folder
```
...where /path/to/folder is the actual full path to the folder you want to display. For example, for me to display a link to the Pictures folder in my home directory, I would use:
```
file:///home/toz/Pictures
```
...and finally, click on the icon to change the icon to whatever you want and click "Create".

The first time you double-click on this icon, you will be notified that it is an untrusted link launcher. You can select "Launch anyway" to launch it this time, "Mark Executable" so that you're not prompted again, or Cancel. Select "Mark Executable". And viola.

For more info on Uniform Resource Locators that you can use in these links, have a read of the [RF 1738 spec]("http://www.w3.org/Addressing/rfc1738.txt").

---

### Post by Xubuntist on 2014-03-17
hello and thank you for your help
i will try what you have said 
i love xubuntu but some things are still beyond me
these forums are a great help
my best regards
francois

---

