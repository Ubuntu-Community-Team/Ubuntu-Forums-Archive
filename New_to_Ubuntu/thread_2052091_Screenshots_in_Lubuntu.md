---
title: "Screenshots in Lubuntu"
date: 2012-09-02
forum: New to Ubuntu
---

### Post by oscillator on 2012-09-02
I've just started using Lubuntu to avoid using Unity and extend my battery life ( which it has done so pretty well :] ) but have run into a bit of a problem with screenshots.

 Looking at this **[http://wiki.lxde.org/en/How_to_make_screenshots](http://wiki.lxde.org/en/How_to_make_screenshots)** installing scrot seems useless, as typing scrot in the terminal just snaps the terminal and then exits.
 So I went to option 2, ImageMagick, but **which *import ***outputs zilch, no error messages, nothing. 

**Locate *import  ***sheds no light on the binary either, so I went to **[http://www.imagemagick.org/script/binary-releases.php#unix](http://www.imagemagick.org/script/binary-releases.php#unix)** to get it, but it's an rpm. 
So then (following these instructions: [http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/) ) converted that to a .deb, but then I remembered last time I tried to install a .deb package manually I broke dpkg, so I've not gone any further. 

If anyone could get me any further (breaking something is likely inevitable!) it'd be much appreciated, or if there are other methods of acquiring screenshots that'd be great :)

---

### Post by oscillator on 2012-09-02
Aha this partly solves my problem (for most web-page related screen-shots at least) but I have just found on online screenshot tool - [http://www.makeuseof.com/dir/talon-online-screen-capture-tool/](http://www.makeuseof.com/dir/talon-online-screen-capture-tool/) 

I now have what I needed but it would still be really useful to have a way to take shots without needing an internet connection :)

---

### Post by oscillator on 2012-09-02
OK, I've now followed these instructions - [http://ubuntu-lxde.wikidot.com/screenshot](http://ubuntu-lxde.wikidot.com/screenshot) - and so far it has worked, albiet it would be great if there was a way to stop the file screenshot.png being overwritten by concurrent screenshots, though I can live with this by changing the file name each time. 
A tip for anyone else who follows the instructions at the above link, DON'T left click and drag the cross-hair, as (only on webpages it seems) the image is blacked out apart from the top application panel and the bottom desktop panel.
Simply hold it in the corner of the area to be recorded (as the instructions state) and left click. 
I'll mark this as solved but would much  appreciate a way to create new files for new screenshots instead of overwriting the file :) (looking forward to the day I'll know how to work that kind of thing out for myself!).

---

### Post by MG&amp;TL on 2012-09-02
You might want to have a look at this: [http://lubuntublog.blogspot.co.uk/2012/02/lxscreenshot.html](http://lubuntublog.blogspot.co.uk/2012/02/lxscreenshot.html) in future. :)

---

### Post by oscillator on 2012-09-02
Ah bugger wish that'd come up in the first page of google results! Thanks a bunch :D

---

