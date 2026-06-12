---
title: "arronax url launcher in ubuntu 12.04"
date: 2013-08-05
forum: New to Ubuntu
---

### Post by misswham2 on 2013-08-05
I want to make launchers for websites like youtube and I saw a video on youtube about arronax.  I have installed it on my system but I need a little help.  First off I cant put icons on my desktop for some reason and I dont actually want it on my desktop anyway I want it in the side panel in unity and in awn or cairo dock.  How can i do this?  Im a little confused.  If someone can kind of talk me through the making of a url launcher with this app would be nice or does someone know an easier way to do it?

I have figured out how to make the launcher.  Now I want it on my side panel dock and my cairo dock.  When I drag it to the 2 panels, they wont stick.  It keeps going back to the desktop.  I made a youtube url laucher/starter.  It was easy with arronax, just type in the url address and add an icon pic and its on my desktop now but I still want it on my side dock and in my awn or cairo dock.Can someone help me there?

---

### Post by Frogs Hair on 2013-08-05
I created a launcher via the main menu AKA alacarte which is not installed by default. By adding the Youtube  url to a separate Firefox launcher, I created an _application luncher_ which opens Firefox to  Youtube. Once created I dragged the the icon from dash to the panel. Alacarte brings the gnome classic panel/session as a dependency when installed. 

My launcher command is as follows.    ```
 firefox %uhttp://www.youtube.com/music
``` This saves a step by opening the browser directly to Youtube and it will open a new tab for Youtube if the browser is already open. It really doesn't save much time , but It was fun to see if it cold be done. The Youtube Unity Lens does not appear to be available for 12.04.

---

### Post by misswham2 on 2013-08-05
Thanks but I guess when I drag the icon to the dock it wont stick.  Its on my desktop but I wanted the icon to float on the dock acutally like all other launchers from the dock.  thanks anyway

---

### Post by Frogs Hair on 2013-08-05
I was also unable to add a link to the launcher so I created an application launcher via the main menu that opens FF to Youtube Music. I can add the Youtube lens to Unity, but that is not an option for 12.04.

---

