---
title: "Screenshot Problem"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by cotcaro on 2008-07-02
Hello. I try to take a screenshot of ubuntu desktop while a taskbar menu is on open state. But at the time I press print screen key, the menu is closed and isnt drawn onto screenshot. How can I make the menu also seen in screenshot?

Thanks in advance.

---

### Post by overdrank on 2008-07-02
> **cotcaro said:**
> Hello. I try to take a screenshot of ubuntu desktop while a taskbar menu is on open state. But at the time I press print screen key, the menu is closed and isnt drawn onto screenshot. How can I make the menu also seen in screenshot?

Thanks in advance.

HI and welcome, can you take a screen shot from applications, accessories and set the time to like 5 sec's.:)

---

### Post by markjensen on 2008-07-02
Well, there are a few options.  One is to have GIMP do your screenshot and tell it to delay a few seconds, so you can get your menus in the state you want them.

Or open a terminal and use "scrot" and specify a time delay, like
**scrot -d 5 desktop.jpeg**

Since scrot may not be pre-installed, you can **sudo apt-get install scrot** to get it.  Or use the "import" program (part of ImageMagick, I believe - if memory serves) with a sleep command in front of it, like
**sleep 5; import -window root desktop.jpeg**

---

### Post by theravenproject on 2008-07-02
If you are using Hardy Heron 8.04 you can select applications-accessories-take screenshot and try it that way and if that doesn't work; right click on take screenshot and select "Add to Panel" and this will add it to your panel and then you can navigate to where you want to take a screenshot and try it from that way?  Hope this helps...I use it all the time and never have any problems!

---

