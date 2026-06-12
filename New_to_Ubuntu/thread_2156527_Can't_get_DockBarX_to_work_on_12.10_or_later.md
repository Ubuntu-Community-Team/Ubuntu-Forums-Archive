---
title: "Can't get DockBarX to work on 12.10 or later"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by Horbo on 2013-06-22
I install dockbarx via its ppa, but when I right click a panel (I'm using MATE) to add dockbarx to it, dockbarx isn't an available option!

This is exactly the same way I used to do it before 12.10, but since 12.10 I haven't been able to get it to work...

Am I doing something wrong?  How can I fix it?

---

### Post by monkeybrain2012 on 2013-06-22
Which ppa? it looks fine [https://launchpad.net/~dockbar-main/+archive/ppa?field.series_filter=raring](https://launchpad.net/~dockbar-main/+archive/ppa?field.series_filter=raring)

---

### Post by Horbo on 2013-06-22
> **monkeybrain2012 said:**
> Which ppa? it looks fine [https://launchpad.net/~dockbar-main/+archive/ppa?field.series_filter=raring](https://launchpad.net/~dockbar-main/+archive/ppa?field.series_filter=raring)

I install with this:

```
[COLOR=#000000][FONT=Verdana]$ sudo add-apt-repository ppa:dockbar-main/ppa[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]$ sudo apt-get update && sudo apt-get install dockbarx[/FONT][/COLOR]
```

Then in the past I've just added DockBarX to a panel by right clicking the panel, Add To Panel, and DockBarX is in the list to be selected.

But since I went to 12.10 DockBarX just doesn't show up in Add To Panel.

---

### Post by monkeybrain2012 on 2013-06-23
Seems like you should do > sudo apt-get install dockbarx-mate
instead

It is always a good idea to see what packages are available in the ppa before you install. :) Also, a downside of the command line is that you have to know exactly the name of the package to install, and sometimes you may not get it right if you just cut and paste those commands from old threads or sites because the name may have changed (like libvdpau becomes libvdpau1), so I find it always helpful to install things with synaptic if I am not sure about what packages are available or what the exact name is. If it is not installed already
> 
sudo apt-get install synaptic 

---

### Post by Horbo on 2013-06-27
Thanks mb, that's definitely got me going in the right direction, unfortunately there are are two dependencies that can't be resolved:
```
dockbarx-mate:
 Depends: mate-conf  but it is not installable
 Depends: mate-conf-common  but it is not installable

```
No matter what I try I can't get them installed. (And someone somewhere should be shot for writing such a useless and uninformative message: "it is not installable"....)

Apt-get is slightly more helpful:
```
E: Package 'mate-conf-common' has no installation candidate
```

But I can't find out what to do about this, no matter how much I google it....what can I do about this?

---

### Post by Horbo on 2013-06-28
Here are links to the packages needed to install dockbarx-mate:

[http://www.ubuntuupdates.org/package/mint_import/nadia/import/base/mate-conf](http://www.ubuntuupdates.org/package/mint_import/nadia/import/base/mate-conf)
[http://www.ubuntuupdates.org/package/mint_import/nadia/import/base/libmateconf](http://www.ubuntuupdates.org/package/mint_import/nadia/import/base/libmateconf)
[http://www.ubuntuupdates.org/package/mint_import/nadia/import/base/mate-conf-common](http://www.ubuntuupdates.org/package/mint_import/nadia/import/base/mate-conf-common)
[http://www.ubuntuupdates.org/package/mint_import/nadia/import/base/libmatecorba](http://www.ubuntuupdates.org/package/mint_import/nadia/import/base/libmatecorba)
[http://www.ubuntuupdates.org/package/mint_import/nadia/import/base/mate-corba](http://www.ubuntuupdates.org/package/mint_import/nadia/import/base/mate-corba)

These really should be automatically included with dockbarx-mate.

Anyway, even after all that, and now finally having dockbarx-mate installed, I STILL cannot add it to a panel!
It simply doesn't show up in the list of things to add.

I really am out of my league here, can anyone shed any light on this?

---

### Post by Frogs Hair on 2013-06-28
I use DockBarX in XFCE and it is a stand alone dock/taskbar independent of the panel in my case . I ran across this post and excuse me if you have seen it already. [http://www.webupd8.org/2012/10/dockbarx-sees-new-release-now-available.html](http://www.webupd8.org/2012/10/dockbarx-sees-new-release-now-available.html)

---

