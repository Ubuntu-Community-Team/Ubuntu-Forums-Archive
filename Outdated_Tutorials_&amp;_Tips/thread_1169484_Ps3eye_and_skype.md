---
title: "Ps3eye and skype"
date: 2009-05-25
forum: Outdated Tutorials &amp; Tips
---

### Post by braingram on 2009-05-25
So after a few months of sort of playing around with the ps3eye camera and skype I have everything working (woohoo). Here is what I had to do:

1. install skype (see this: [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) )
2. install modified gspca module from here:
  [http://kaswy.free.fr/?q=node/38#ps3](http://kaswy.free.fr/?q=node/38#ps3)
 if you have problems, search around these forums [http://nuigroup.com/forums/](http://nuigroup.com/forums/)
3. (aka "the special sauce") when launching skype use the following command
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype
```
you can place this is a bash script (I stuck it in ~/bin) or use an alias (probably cleaner)

Caveats. There are plenty of video modes (resolution/refresh rates) and video options for the camera ([http://kaswy.free.fr/?q=en/node/47](http://kaswy.free.fr/?q=en/node/47)). To change modes or options you need to remove and reinsert the module passing the new mode or option to modprobe (see [http://kaswy.free.fr/?q=en/node/47](http://kaswy.free.fr/?q=en/node/47) for more info). Supposedly you can use v4l2-ctl although I haven't tried this. I have not yet experimented with the different modes to see which works best with skype but I imagine some of the >30 fps modes would be a little overkill (so 640x480@30 is probably the sweet spot).

I hope this helps someone and I'd like to say thanks to whoever lives at kaswy.free.fr for modifying the gspca module code.

---

