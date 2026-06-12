---
title: "HowTo: Create your own Clearlooks theme."
date: 2005-06-12
forum: Outdated Tutorials &amp; Tips
---

### Post by tristan on 2005-06-12
I really like clearlooks, but none of the theme colourschemes (clearlooks, olive,  deepsky) float my boat. In particular none really match the ubuntu brown/orange theme. 

It's pretty easy to make your own theme though:

1 - sudo su or whatever you need to do to get root.

2 - Clearlooks themes live in /usr/share/themes/ . Create a directory called  Clearlooks-ubuntu (or whatever you want to call it).

3 - Copy the directory /usr/share/themes/Clearlooks/gtk-2.0 into /usr/share/themes/Clearlooks-ubuntu

4 - Edit  /usr/share/themes/Clearlooks-ubuntu/gtk-2.0/gtkrc

The three important lines to change are:

bg[SELECTED]      = "#7c99ad" # blueish  
base[PRELIGHT]    = "#7c99ad" # blueish  
base[SELECTED]    = "#7c99ad" # blueish

For my theme I replaced #7c99ad with #deb17c (orange/brown).

5 - Go to System->Preferences->Theme and select Clearlooks. Then hit the Theme Details button. In the Controls tab you should be able to select Clearlooks-ubuntu.

Voila! New theme.

---

### Post by bored2k on 2005-06-12
Moved to the Tips and tricks forum ;).

---

### Post by tristan on 2005-06-12
Thanks. Could you perhaps put it in the hoary tips not the warty?

---

### Post by bored2k on 2005-06-12
[QUOTE=tristan]Thanks. Could you perhaps put it in the hoary tips not the warty?[/QUOTE]
 It's on both ;).

---

### Post by tristan on 2005-06-12
Hmm, that's what happens when I get on the computer the morning after a big night on the town :)

Thanks bored2k!

---

### Post by bored2k on 2005-06-12
This is just great. I no longer have to drive myself crazy looking for a theme to match my wallpapers :D

---

### Post by tristan on 2005-06-12
[QUOTE=bored2k]This is just great. I no longer have to drive myself crazy looking for a theme to match my wallpapers :D[/QUOTE]

Glad you like it. It's nice being able to contribute to the ubuntu community, even if in a microscopic way :)

---

### Post by bored2k on 2005-06-12
[QUOTE=tristan]Glad you like it. It's nice being able to contribute to the ubuntu community, even if in a microscopic way :)[/QUOTE]
 Oh it's not microscopic. You just saved me a bunch of time on gnome-look :D -sometimes I wouldn't even use a wallpaper because I couldn't find a window border for it-.

---

### Post by Sionide on 2005-06-13
Wow! That is nice. There should be more Ubuntu-ish themes  included as default. That's a great tip - thanks.

---

### Post by frodon on 2005-06-14
Thanks a lot, i was looking for that for a long time ! 

thanks tristan

---

### Post by bvc on 2005-06-14
[QUOTE=bored2k]Oh it's not microscopic. You just saved me a bunch of time on gnome-look :D -sometimes I wouldn't even use a wallpaper because I couldn't find a window border for it-.[/QUOTE]
with everything I've posted on this forum and gnome-look, I didn't know they were such a secret :-? 
**WARNING: these are for clearlooks 0.5**
Not only are some of the colors bad on clearlooks 0.6 but you'll also have to update the sunkenmenubar line to menubarstyle :roll: 
Because of inconsistant ratios, I had to adjust the colors to make them work for 0.5. Now that clearlooks-devel has corrected the ratio, the colors are off. Mostly the SELECTED color.

[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/index.html](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/index.html)
Clearlooks-Coffee

[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/Big_Pack.html](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/Big_Pack.html)
[Clearlooks-4Humans](http://kwh.kernow-gb.com/~bvc/theme/screenshots/clearlooks/Clearlooks-4Humans.jpg) 
Clearlooks-Decaf_Coffee
Clearlooks-Ubuntu
[Clearlooks-Darjeeling](http://kwh.kernow-gb.com/~bvc/theme/screenshots/clearlooks/Clearlooks-Darjeeling.jpg) 
[Hedgehog](http://kwh.kernow-gb.com/~bvc/theme/screenshots/clearlooks/Hedgehog1.jpg) 
Hedgehog2
[Human-In-Blue](http://kwh.kernow-gb.com/~bvc/theme/screenshots/clearlooks/Clearlooks-HumanBlue.jpg)

---

