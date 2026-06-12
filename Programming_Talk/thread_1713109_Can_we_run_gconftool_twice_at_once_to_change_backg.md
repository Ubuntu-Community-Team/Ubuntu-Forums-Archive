---
title: "Can we run gconftool twice at once to change background??"
date: 2011-03-23
forum: Programming Talk
---

### Post by kei-clone on 2011-03-23
So, I decided to hack together this little python script to periodically change my wallpaper. Originally, I had attempted to simply set my wallpaper target as a specific file in my Wallpapers folder, and I was hoping that when my script runs and updates the image, the background would update as well (that's what they do here: [http://www.simplehelp.net/2010/05/31/how-to-set-a-rotating-picture-of-the-earth-as-your-wallpaper-in-ubuntu/](http://www.simplehelp.net/2010/05/31/how-to-set-a-rotating-picture-of-the-earth-as-your-wallpaper-in-ubuntu/))

It didn't work, so I decided maybe I should force gnome to refresh or something, so I did a little bit of hackery, used gconftool to change the background to another image temporarily, then change it back to the correct image. This didn't work at first, at least not until I added the **sleep 5** code below. Now it works, but this feels like horrible, horrible hackery, and I was wondering if there's just an easier way to change wallpapers?

```
#wget the image and store it wherever
wget = ''.join([r'wget -N -U "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.6) Gecko/20070725 Firefox/2.0.0.6" -P ', \
    destination, ' ', imgurl, ';' \
    'mv ', destination, r'/wallpaper-', str(wall_id), r'.jpg ', \
    destination, '/', imagename, ';' \
[B]    r'gconftool -t string -s /desktop/gnome/background/picture_filename ', \
    destination, '/', tempwall, ';', \
    *'sleep 5;' \*
    r'gconftool -t string -s /desktop/gnome/background/picture_filename ', \[/B]
    destination, '/', imagename]) #TODO: for some reason gconf is retarded and doesn't sense that the image has changed, so this changes it to a temp file, waits 5 seconds, and then changes it back
os.system(wget)
```

---

