---
title: "Personalization (wallpaper, display settings etc.) reset back to default"
date: 2019-12-04
forum: New to Ubuntu
---

### Post by kibainuzuka on 2019-12-04
I'm new to ubuntu, I have been using it for a month now and sometimes when I normally turn off my computer and turn it back on after like a day or so, my display settings reset. I find it a bit annoying because I have to tune my settings to where it was so it's a bit easier to access things. My version of Ubuntu is 16.04 LTS, does anyone get this problem or can it be fixed? Thank you for your help!

***Note***[B][I]: This is not happening because of unrecognized hardware specs and choosing to launch normal graphics anyway. That happened to me only once and my display settings reset.
[/I][/B]

---

### Post by DuckHook on 2019-12-05
Welcome to the forums, kibainuzuka

Are you talking about display resolution? If so, please post results of:```
xrandr
``````
sudo lspci -vk | grep -iA20 vga
```
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by kibainuzuka on 2019-12-07
Not resolution, my wallpaper, brightness, icon size is reset.

---

### Post by Frogs Hair on 2019-12-07
Would that be the icon size in the Unity panel on the left or desktop icons ?

---

