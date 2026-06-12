---
title: "[SOLVED] compiz screensaver plugin Hardy"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-07-06
back when i had gutsy i found some compiz unsupported plugins (i mainly want the screensaver plugin)

i was able to compile the plugins and all worked great

now i have hardy and i cant remember where i got the screensaver plugin

so basically where can i get the screensaver plugin for compiz in hardy?

---

### Post by cariboo on 2008-07-06
I think this is what you are looking for:

[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

Have a good look at it before going ahead with it.

Jim

---

### Post by sayakb on 2008-07-06
[http://ubuntuforums.org/showthread.php?t=820802](http://ubuntuforums.org/showthread.php?t=820802)

Also, install the latest compiz fusion:
[http://ubuntuforums.org/showpost.php?p=5332505&postcount=5](http://ubuntuforums.org/showpost.php?p=5332505&postcount=5)

---

### Post by tjwoosta on 2008-07-06
> 
[http://ubuntuforums.org/showthread.php?t=820802](http://ubuntuforums.org/showthread.php?t=820802)

Also, install the latest compiz fusion:
[http://ubuntuforums.org/showpost.php...05&postcount=5](http://ubuntuforums.org/showpost.php...05&postcount=5)


your first link i like, but how do i run the .sh without root?

on the first page it says **do not run as root**, so i changed the permissions so everyone has full read/write access and i checked allow as executable, yet still when i try to run the .sh it asks for my (sudo) password even when im not using sudo


and for your second link, i installed the new version of compiz, but for some reason i still cant make the cube deformation plugin work (not a big deal because i didnt even know about it untill i saw your link)

---

### Post by bhadotia on 2008-07-06
> and for your second link, i installed the new version of compiz, but for some reason i still cant make the cube deformation plugin work
I have tried the deformation plugin in sus11. There I had to customize the plugin to deform the cube as a cylinder or sphere to deform the cube when it is rotated. I mean that just enabling the plugin won't work you will have to customize it.

---

### Post by tjwoosta on 2008-07-06
yea i already tried but nothing i change makes any difference (i can setup the reflection fine, but the deformation does nothing no matter how i set it)


also i used to be able to disable nautilus from drawing the desktop with gconf-editor (that way i could use 4 different wallpapers by setting them in the "desktop cube" settings), 
but now in the desktop cube settings there is no place to choose wallpapers

and the thickness of my windows for the 3d windows plugin wont change (each windows only like one pixel thick now no matter how i set it)


how can i get my old compiz back?

---

### Post by bhadotia on 2008-07-06
I think you should try logging out and then logging back in (or rebooting).
I am surfing the net from suse at present and the deformation plugin is working like any other plugin.
I will be logging into ubuntu in an hour or two (after I finish installing some software here) and will try that plugin for myself also.

---

### Post by tjwoosta on 2008-07-06
just rebooted again but still nothing

---

### Post by bhadotia on 2008-07-06
Hmm.. I will get back to you in an hour .
I will try the plugin myself and let you know if it worked for me.

---

### Post by tjwoosta on 2008-07-06
so does anybody know exactly what packages i need to remove and what packages i need to install to get the original hardy compiz back?

---

### Post by bhadotia on 2008-07-06
So you are planning to uninstall the plugin already?
Well if you are, I myself won't be trying it coz I don't need it - I was just gonna try it for you .

---

### Post by tjwoosta on 2008-07-06
> 
So you are planning to uninstall the plugin already?
Well if you are, I myself won't be trying it coz I don't need it - I was just gonna try it for you . 


yea well what i originally wanted was just the screensaver plugin
(i found that and it works great)

but then i got the post from LinuxIsInnovation where i saw the deformation plugin (i wanted to try it, cuz it looks cool)

but now that i have upgraded my compiz from the unsupported repository it has broken alot of the things that i like (for instance the 3d windows plugin and having 4 different wallpapers) and the deformation plugin dont even work

so basically if i can get the deformation plugin to work then i will keep this version of compiz, but if not i want to know how to remove this version and get my old version back

but dont install the deformation plugin just for me, i dont want to waste your time

if you know how i can fix it though that would be cool

---

### Post by tjwoosta on 2008-07-06
ok, 

i figured it all out

before upgrading compiz i had gone into gconf-editor and disabled nautilus from drawing the desktop(so the compiz "desktop cube" plugin could draw it instead)

when i upgraded my compiz it installed the "wallpaper" plugin automatically and i am no longer able to set the wallpapers from the "desktop cube" plugin

so i had to set my 4 wallpapers in the "wallpaper" plugin instead of the "desktop cube" plugin

(or alternatively i could have just gone back into gconf-editor and re-enabled nautilus to show desktop)

so after selecting either compiz or nautilus to draw the wallpapers the deformation plugin started working

so basically the new compiz does all the same stuff as the old one, plus i get the deformation plugin

(the only thing that i dont like is how my "3d windows" plugin no longer lets me change the window thickness, but whatever thats nothin)

---

