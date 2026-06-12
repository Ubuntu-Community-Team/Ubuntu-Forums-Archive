---
title: "system structure and finding conf files"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by yamJoyous on 2012-11-15
Hello,

I'm a complete newbe to Ubuntu, I have a little experience with MacOS and Fedora, but I'm lost here.

I'm trying to change the refit.conf entry to make Linux the default value at boot, but I can't find the folder where the file is located!

I've tried the online docs from [http://refit.sourceforge.net/](http://refit.sourceforge.net/) no luck with that.

When I follow along with this well written tutorial [http://thehungrycoder.com/tutorial/setting-linux-as-default-in-refit-boot-loader.html](http://thehungrycoder.com/tutorial/setting-linux-as-default-in-refit-boot-loader.html)
they say it is here: sudo vi /etc/efi/refit/refit.conf
but that folder and file doesn't exist

When I do a search in Dash home I get a result in:
/home/media/username/home/efi/refit.conf
using terminal to navigate to this location doesn't exist! I cd to home and ls and all I have is my username, no "media"

So I can't sudo with vi the file is not available!
When I start the file from Dash home I'm only in usermode, not sudo, so the file is locked.

When I sudo gedit the folders aren't available within the navigation window!

Is there a place for me to read on the system file structure, or does anyone have an idea how I get unrestricted access to the refit.conf file?

Thanks.

PS: running unbutu on a macbook 1.1 from an SSD drive.

---

### Post by Paqman on 2012-11-15
That guide suggests you edit that file in OS X, not Ubuntu. The file will be on your OS X partition, if you mount that from within Ubuntu you should be able to navigate to it but I'd be inclined to follow the guide to the letter in something boot-related, just in case.

One thing I would do differently: don't open the file in vi unless you're familiar with vi. It's not at all straightforward to use.

---

### Post by yamJoyous on 2012-11-15
Thanks for your response! Sometimes I read too fast! From Mac OS? I missed that. Yes vi is not easy to use, just noticed that! Argh, got to learn to make backups of my files before I edit! Good thing I figured out how to fix my errors.

Thanks again! :-)

---

