---
title: "Zenity : How to change some dialog icon"
date: 2014-07-15
forum: Programming Talk
---

### Post by manutd94 on 2014-07-15
Hey guy, I'm newbie in ubuntu.
I'm starting to make a Quiz by Shell Programming Language and Zenity . 
Then I want to change info icon in zenity 
```
zenity --height=400 --width=400 --icon-name="/home/letien/Downloads/icon.png" --info --title "Quiz " --text "ABC";
```
But the result is :
[IMG]http://www.upsieutoc.com/images/2014/07/15/abc.jpg[/IMG]
How can i fix it ?
Thanks alot for helping me :D

---

### Post by VCoolio on 2014-07-17
--icon-name doesn't take a path, you put in an icon-name. Check the filenames for the icons in your theme, or check [here]("https://developer.gnome.org/icon-naming-spec/#names") for some defaults.

---

