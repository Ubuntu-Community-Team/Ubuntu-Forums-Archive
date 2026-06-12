---
title: "Incorrectly installed gloobus"
date: 2016-02-15
forum: New to Ubuntu
---

### Post by seal308 on 2016-02-15
Hello,
I'm using lubuntu.
I believe I installed the wrong repositories for gloobus-preview.
Now when I do sudo apt-get update I get this: 
W: Failed to fetch [http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used

I saw somewhere that I should go into /etc/apt/sources.list and comment out affected lines.
I just want to make sure I'm commenting out the correct thing.
At the bottom of the sources.list file is:
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

Should I comment out the bottom 2 lines?
I'm new so I don't really know what I am doing, specifically I don't get why I'm doing it.

Thanks

---

### Post by Habitual on 2016-02-15
Yes, I would comment out any gloobus stuff in your sources.

---

### Post by seal308 on 2016-02-15
> **Habitual said:**
> Yes, I would comment out any gloobus stuff in your sources.

Instead of commenting out the sources.list file directly, I instead cd to the sources.list.d/ directory.
In there I commented out all the lines in gloobus-dev-gloobus-preview-trusty.list.
When I run sudo-apt get update it doesn't fail anymore.
I still don't get how to install gloobus on my lubuntu running ubuntu 14.04.
I tried using this: [http://ubuntuhandbook.org/index.php/2015/01/enable-nautilus-file-preview-ubuntu-14-10-14-04/](http://ubuntuhandbook.org/index.php/2015/01/enable-nautilus-file-preview-ubuntu-14-10-14-04/)
But when I press the space bar on a pdf I don't get a preview, it just opens the document.

Can gloobus-preview not run on lubuntu or something?

Thanks

---

### Post by mc4man on 2016-02-15
Never  used gloobus but took a look & try out. This would be the best page to read/use for it - 
[http://www.webupd8.org/2015/01/quick-file-previewer-gloobus-preview.html](http://www.webupd8.org/2015/01/quick-file-previewer-gloobus-preview.html)

The gist of it to me was, 
nautilus or nemo as file manager
Install from the ppa the gloobus-preview package
For nautilus then install gloobus-sushi package
For nemo install nemo-gloobus-sushi instead.

Restart either nautilus or nemo & it should work reasonably well, here it was good on audio/video & image files, so-so on documents.
(on web page some add. packages mentioned to maybe help docu.'s, a/v justs needs decent gstreamer plugin installs.

As far as Lubuntu,probably not as it just  works with nautilus or nemo (from what I read..

---

### Post by seal308 on 2016-02-16
Yes, I think the only way for me to use it is if I replace whatever file manager Lubuntu uses with nautilus.
Too much work for me, so I'll just leave everything as it is.
Thank you.

> **mc4man said:**
> Never  used gloobus but took a look & try out. This would be the best page to read/use for it - 
[http://www.webupd8.org/2015/01/quick-file-previewer-gloobus-preview.html](http://www.webupd8.org/2015/01/quick-file-previewer-gloobus-preview.html)

The gist of it to me was, 
nautilus or nemo as file manager
Install from the ppa the gloobus-preview package
For nautilus then install gloobus-sushi package
For nemo install nemo-gloobus-sushi instead.

Restart either nautilus or nemo & it should work reasonably well, here it was good on audio/video & image files, so-so on documents.
(on web page some add. packages mentioned to maybe help docu.'s, a/v justs needs decent gstreamer plugin installs.

As far as Lubuntu,probably not as it just  works with nautilus or nemo (from what I read..

---

