---
title: "Metacity: How to remove the window borders?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by crowhill on 2008-09-30
Hi there

I'm desperately trying to remove the borders and titlebars from all windows I ever open in Gnome. I went so far to give Fluxbox a try but I'm not a big fan of it even tough, there, I can remove the borders somehow. Is there a way to tell Metacity to get rid of the borders? I tried to modify the metaicty-theme-1.xml file but I couldn't get the values right. The file isn't loading (I made a backup though :)). Also, I tried to find a window border theme online but none of them is as simple as I want it. I can understand that ... imagine the website offering window border themes and one of the themes has no borders :)

Some help would be extremely appreciated.

Best regards,
crowhill.

---

### Post by kk0sse54 on 2008-09-30
How about trying out a tiling window manager? Such as perhaps dwm or wmii

---

### Post by crowhill on 2008-09-30
Thank you a lot for this quick answer! I was thinking about that too. The thing is I'm not quite sure about the consequences of this. Is switching to one of those similar to switching to Fluxbox? Will I have to set my keybord shortcuts again? Will I have to set a menu again (the one in Fluxbox is a complete pain)? Will I have to add Gnome apps to the control panel again? All that and other things are very good under Gnome.

crowhill.

---

### Post by karlmp on 2008-09-30
what about openbox?

---

### Post by aeiah on 2008-09-30
like [this](http://linux.softpedia.com/get/Desktop-Environment/Themes/Cobra-theme-41269.shtml) ([image](http://linux.softpedia.com/screenshots/Cobra-theme_1.png))? or without the top bit as well? im sure you can edit the height in the metacity theme (and the colours) without too much bother

---

### Post by kk0sse54 on 2008-09-30
> **crowhill said:**
> Thank you a lot for this quick answer! I was thinking about that too. The thing is I'm not quite sure about the consequences of this. Is switching to one of those similar to switching to Fluxbox? Will I have to set my keybord shortcuts again? Will I have to set a menu again (the one in Fluxbox is a complete pain)? Will I have to add Gnome apps to the control panel again? All that and other things are very good under Gnome.

crowhill.

a tiling wm to be quite honest will probably seem very overwhelming at first as it's very different than more traditional DE's and WM's like fluxbox and openbox. And yes unfortunetly you will need to redo your menu by installing something like dmenu and your shortcuts too. Just remember that the point of a tiling wm is never to have to lift your hands off the keyboard and use your mouse. Here's a dwm tutorial if you are interested [http://www.xsnake.net/howto/dwm/dwm-eng.php](http://www.xsnake.net/howto/dwm/dwm-eng.php) and this is their homepage [http://www.suckless.org/dwm/](http://www.suckless.org/dwm/) goodluck :)

---

### Post by whitethorn on 2008-09-30
I'm not really sure if this is what you need. But I use a program called devilspie which allows me to tell what programs should start where (desktops), it also lets you control what size the program should have and with or without window borders. You can get it in synaptic.  I don't know how you would get it to work on all windows but I'm guessing it might be a little easier than what I've read above.

---

### Post by crowhill on 2008-09-30
> **aeiah said:**
> like [this](http://linux.softpedia.com/get/Desktop-Environment/Themes/Cobra-theme-41269.shtml) ([image](http://linux.softpedia.com/screenshots/Cobra-theme_1.png))? or without the top bit as well? im sure you can edit the height in the metacity theme (and the colours) without too much bother

this looks fine but it seems to me that it's somehow tricky to change the window borders from the metacity-theme-1.xml file.

> a tiling wm to be quite honest will probably seem very overwhelming at first as it's very different than more traditional DE's and WM's like fluxbox and openbox. And yes unfortunetly you will need to redo your menu by installing something like dmenu and your shortcuts too. Just remember that the point of a tiling wm is never to have to lift your hands off the keyboard and use your mouse. Here's a dwm tutorial if you are interested [http://www.xsnake.net/howto/dwm/dwm-eng.php](http://www.xsnake.net/howto/dwm/dwm-eng.php) and this is their homepage [http://www.suckless.org/dwm/](http://www.suckless.org/dwm/) goodluck 

maybe, i give it a try, since, the keyboard action is what i'm really keen on ... then the window borders are just a complete waste of space !

> I'm not really sure if this is what you need. But I use a program called devilspie which allows me to tell what programs should start where (desktops), it also lets you control what size the program should have and with or without window borders. You can get it in synaptic. I don't know how you would get it to work on all windows but I'm guessing it might be a little easier than what I've read above.

this sounds fine too.

-------------

thanks a lot for the replies!

as usual, this forum is amazing - love it :D

---

### Post by jeansch on 2008-11-07
With this theme:

[http://schurger.org/themes/No-Title.tar.gz](http://schurger.org/themes/No-Title.tar.gz)


--
Jean Schurger <jean@schurger.org>

---

### Post by viktiglemma on 2009-08-28
> **jeansch said:**
> With this theme:

[http://schurger.org/themes/No-Title.tar.gz](http://schurger.org/themes/No-Title.tar.gz)


--
Jean Schurger <jean@schurger.org>

This was awsome. However, is there any easy way to resize the windows now?

---

### Post by nothingspecial on 2009-08-28
Alt F8 then use the arrows.

---

### Post by crowhill on 2009-08-28
i'm sorry, i wrote i created it even though it was you ... it's a loooooong time ago and i remember having modified yours a little bit ... sorry again if that was bothering you :)

---

### Post by km0r3 on 2010-11-07
You can also follow the instructions [here]("http://kennymeyer.blogspot.com/2010/11/hacking-metacity-remove-window.html"), if you want to have the window decorations away "forever".

---

### Post by drmmundy on 2012-02-24
> **km0r3 said:**
> You can also follow the instructions [here]("http://kennymeyer.blogspot.com/2010/11/hacking-metacity-remove-window.html"), if you want to have the window decorations away "forever".
That link is broken. Here's how to hide the borders and get resize controls past the edge of the window the correct way.

Borderless windows:

Go into /usr/share/themes/[your theme's name]/metacity-1/metacity-theme-1.xml

Find the following lines (there may be more than one of each):
```
<distance name="left_width" value="[number]"/>
<distance name="right_width" value="[number]"/>
<distance name="bottom_height" value="[number]"/>
```

Change each of the values to "0".

Invisible resize borders:

Inside the <frame_style> elements where name="normal_focused" and name="normal_unfocused", add the following line: 
```
<padding left="7" right="7" bottom="7"/>
```

Log out and in, and your windows should be borderless and resizeable.

---

