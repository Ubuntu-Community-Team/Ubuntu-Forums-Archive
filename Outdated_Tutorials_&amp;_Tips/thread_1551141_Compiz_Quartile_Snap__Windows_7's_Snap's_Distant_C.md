---
title: "Compiz Quartile Snap:  Windows 7's Snap's Distant Cousin"
date: 2010-08-11
forum: Outdated Tutorials &amp; Tips
---

### Post by boaty on 2010-08-11
So, inspired by the Compiz half-screen snaps, I decided to try to work together quartile snaps.  Using [this]("http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html") method, you can have assign these commands to each corner.

top-left
```
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALFWIDTH=$(($WIDTH/2)) && HEIGHT=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d p` && HALFHEIGHT=$(($HEIGHT/2)) && wmctrl -r :ACTIVE: -e 0,0,0,$HALFWIDTH,$HALFHEIGHT

```

bottom-left
```

WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALFWIDTH=$(($WIDTH/2)) && HEIGHT=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d p` && HALFHEIGHT=$(($HEIGHT/2)) && wmctrl -r :ACTIVE: -e 0,0,$HALFHEIGHT,$HALFWIDTH,$HALFHEIGHT

```

top-right
```

WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALFWIDTH=$(($WIDTH/2)) && HEIGHT=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d p` && HALFHEIGHT=$(($HEIGHT/2)) && wmctrl -r :ACTIVE: -e 0,$HALFWIDTH,0,$HALFWIDTH,$HALFHEIGHT

```

bottom-right
```

WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALFWIDTH=$(($WIDTH/2)) && HEIGHT=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d p` && HALFHEIGHT=$(($HEIGHT/2)) && wmctrl -r :ACTIVE: -e 0,$HALFWIDTH,$HALFHEIGHT,$HALFWIDTH,$HALFHEIGHT

```

If you have any suggestions to make this better, please let me know!

Enjoy!

Edit:
The link above is broken.  Here is a [link]("http://lifehacker.com/5402090/emulate-windows-7s-aero-snap-sizing-in-linux") to the lifehacker page referencing the method.

Down the page a little are the two commands (actually slightly different than the original, but better; they prevent overlapping).

Left Snap
```

WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$((($WIDTH/2)-10)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1

```

Right Snap
```

WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$((($WIDTH/2)-12)) && HALFP=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALFP,0,$HALF,-1

```

Also for damn good measure, here is [Google's cache of the original link]("http://webcache.googleusercontent.com/search?sourceid=chrome&ie=UTF-8&q=cache:http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html").

Now, enjoy :D

---

