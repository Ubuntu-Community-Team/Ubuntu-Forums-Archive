---
title: "How can I do different text-scaling factors or DPI for different programs?"
date: 2015-06-15
forum: New to Ubuntu
---

### Post by jorge22 on 2015-06-15
I've been messing around with different music players to try and find the perfect one for me. Visually Nighingale was amazingly beautiful, it was my favorite but it doesn't support iPod. Clementine was really cool, but didn't have an easily view able library the way I liked.

Banshee was the best one since it combined a little of both. Only one problem. Banshee uses the system base font to make it's font. And it's really big. If I change the text scaling for my entire system, then Banshee looks nice, but then everything looks wrong. 

How can I isolate Banshee and have it have it's own text-scaling factor??

---

### Post by jorge22 on 2015-06-15
I didn't figure out a solution that worke for eveything. But I found a solution for Banshee...

---------------------------------Copy Pasted from another forum---------------------

[COLOR=#000000][FONT=Verdana]Create a file 'gtkrc' in Banshee's config data directory :  ~/.config/banshee-1/gtkrc [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Add the following lines: [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-------------- [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]style "font" [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]{ [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]font_name = "Sans 8" [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]} [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]widget_class "*" style "font" [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]gtk-font-name = "Sans 8" [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]-------------- [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Replace "Sans 8" with whatever font name and size you'd like to use.

------------------------------------------------------------------------------------------------

Worked perfectly for me. Hopefully it works for others!![/FONT][/COLOR]

---

