---
title: "Not All Updates Can Be Installed"
date: 2014-11-08
forum: New to Ubuntu
---

### Post by wpwend42 on 2014-11-08
Why would this happen? It looks like it is VLC that won't update. How should I go about fixing this? When I try to toggle them nothing happens. Never seen it before...

[http://i220.photobucket.com/albums/dd260/beedoubleyou138/Screenshotfrom2014-11-06191336_zpse10799ba.png](http://i220.photobucket.com/albums/dd260/beedoubleyou138/Screenshotfrom2014-11-06191336_zpse10799ba.png)

[http://i220.photobucket.com/albums/dd260/beedoubleyou138/Screenshotfrom2014-11-08113116_zps0d9cb459.png](http://i220.photobucket.com/albums/dd260/beedoubleyou138/Screenshotfrom2014-11-08113116_zps0d9cb459.png)

---

### Post by wildmanne39 on 2014-11-08
Hi, the server is probably down, just wait a while then try again. It is a very bad idea to do a partial upgrade it tends to break things.
Thanks

---

### Post by wildmanne39 on 2014-11-08
Please use url's or thumbnails when posting images, not every has a fast connection.
Thanks

---

### Post by nerdtron on 2014-11-08
VLC updates now? I thought VLC versions (on the software center at least) are locked on each version of Ubuntu.

---

### Post by wpwend42 on 2014-11-08
It's been doing this for a few weeks.

---

### Post by ian-weisser on 2014-11-08
'A few weeks' is bad.
You may not be receiving security updates.

Please open a terminal and try the following two commands.
Please copy-and-paste the complete output here. Use ```
 tags to contain the output.
[code]sudo apt-get update
sudo apt-get upgrade
```

---

### Post by wpwend42 on 2014-11-08
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libtcl8.5 tcl8.5
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  conky-manager ffmpeg libvlc5 libvncserver0 linux-headers-generic
  linux-signed-generic linux-signed-image-generic system-config-printer-udev
  vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
```

---

### Post by Bashing-om on 2014-11-08
wpwend42; Hi !

Looks like ian-weisser , as normal, has cut to the heart of the matter.

Now what returns:
```

sudo apt-get dist-upgrade

```
as we have:
> 
The following packages have been kept back:
  conky-manager ffmpeg libvlc5 libvncserver0 linux-headers-generic
  linux-signed-generic linux-signed-image-generic system-config-printer-udev
  vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse

Consider carefully prior to hitting 'y', see what might result as we do not know the why these packages are "kept back" .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2014-11-08
Hi Bashing ..

How bout using a different mirror?

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by Bashing-om on 2014-11-08
@ ibjsb4; Good evening, friend.

In this instance the packages are available in the mirror, but, the package manager has "unmet" conditions.
I would expect these conditions to be resolved with authorizing the package manager to install these "held" packages.
Would behoove us to watch what is being installed; perhaps there is an underlying  problem (VLC and/or kernel ??). If "dist-upgrade" takes care of the situation, fine good and dandy. Chances are more than good that the package manager will deal with the situation.

[INDENT][INDENT]give the package manager a chance to
[INDENT][INDENT][INDENT][INDENT]work it's magic ( those scripts, checks, and balances are in place for reasons)
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

