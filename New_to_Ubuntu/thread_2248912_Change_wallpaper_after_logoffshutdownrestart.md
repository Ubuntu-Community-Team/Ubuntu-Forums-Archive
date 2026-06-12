---
title: "Change wallpaper after logoff/shutdown/restart"
date: 2014-10-18
forum: New to Ubuntu
---

### Post by Hellboy256 on 2014-10-18
I have set four different wallpapers with ccms. The four picture links point to locations like 
/home/.../0.jpg
/home/.../1.jpg
/home/.../2.jpg
/home/.../3.jpg
I wrote a script that copies from a pool of piictures 4 new pictures in this location overwritting the existing once.
I have tried to run this script after login via 'Startup Applications' but then I only receive four black screens. I assume that I would somehow need to reload the desktop backgound!?
Another possiblitly would be to execute it on logoff/shutdown/restart. Does anyone know where I'd have to put the command then?

---

### Post by CantankRus on 2014-10-18
You should post your script so others can test or give a better method.

---

### Post by CantankRus on 2014-10-18
I've been looking at compiz and the wallpaper plugin.
Once I have manually set up 4 wallpapers in ccsm I can use this script to change to 4 new wallpapers.
```
#!/bin/bash 

desk1="/home/glen/Pictures/wallpaper/ross-zietz-1680x1050.jpg"
desk2="/home/glen/Pictures/wallpaper/sVvAH - Imgur.jpg"
desk3="/home/glen/Pictures/wallpaper/Slumber-wallpaper-1680x1050.jpg"
desk4="/home/glen/Desktop/weird-world.jpg"

gsettings set org.compiz.wallpaper:/org/compiz/profiles/unity/plugins/wallpaper/ bg-image "['$desk1', '$desk2', '$desk3', '$desk4']"
```

It will change images instantly if the desk# variables are new paths to those already in use.
Overwriting the images and keeping the path as you described earlier doesn't update till I reload unity.

If you make the desk# variables the actual random image paths it would probably work.

**[COLOR="#FF0000"]EDIT[/COLOR]**
Been playing around and this script works for me.
Just set [COLOR="#FF0000"]your wallpaper directory[/COLOR] and add to startup applications for new walls at login.
 ```
#!/bin/bash
#set -x 
##############################################################################
## Enable the compiz wallpaper plugin and manually set 4 wallpapers in ccsm ##
## before running this script                                               ##
##############################################################################

directory="[COLOR="#FF0000"]/home/glen/Pictures/wallpaper[/COLOR]"   # set your wallpaper directory

find "$directory" | grep -E ".jpg|.jpeg|.png" | shuf -n 4 > ~/.4walls    # searches recursively
 
desk1="$(awk 'NR==1' ~/.4walls)"
desk2="$(awk 'NR==2' ~/.4walls)"
desk3="$(awk 'NR==3' ~/.4walls)"
desk4="$(awk 'NR==4' ~/.4walls)"

gsettings set org.compiz.wallpaper:/org/compiz/profiles/unity/plugins/wallpaper/ bg-image "['$desk1', '$desk2', '$desk3', '$desk4']"
```

---

### Post by Hellboy256 on 2014-10-18
Works perfect!!
Thanks a lot

---

### Post by CantankRus on 2014-10-20
No problem. Solving this helped me as well.

I've actually started using the wallpaper plugin and the script with a little amendment.
```
## background set in dconf by xplanetfx 
## alternates between ~/.xplanetFX/output/xplanetFX1.png and ~/.xplanetFX/output/xplanetFX2.png
**desk1="$(gsettings get org.gnome.desktop.background picture-uri | cut -c 9- | tr -d "'")"**  

#desk1="$(awk 'NR==1' ~/.4walls)"  # random image
desk2="$(awk 'NR==2' ~/.4walls)"
desk3="$(awk 'NR==3' ~/.4walls)"
desk4="$(awk 'NR==4' ~/.4walls)"
```

I use xplanetfx which draws an image of the earth and moon to any wallpaper
and then sets this image as the background you see in "Appearances".

So now desk1 remains a constant image showing the earth rotation rendered by xplanetfx
and the other desktops change to a random image every 30 mins.
The script is run by xplanetfx after each rendering.

---

