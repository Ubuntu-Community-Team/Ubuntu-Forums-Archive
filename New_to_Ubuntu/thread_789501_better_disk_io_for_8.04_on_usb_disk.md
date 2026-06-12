---
title: "better disk i/o for 8.04 on usb disk?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by shreaded_teddy on 2008-05-10
i've got a dell e1505 laptop, 2Gb ram, and 8.04 installed to a 8Gb usb flash drive.  i don't really use any ram intensive programs and don't have swap space assigned.  so my question is there an easy way to to boost performance, write less to the usb and make better use of ram?  setting up ram disks for cache or loading more of the os to ram on startup would be cool.  so far i have preload but it hasn't helped much, and i finally got 8.04 and firefox set up the way i want so i'm not really interested in a different distro or browser.

found [http://webshacker.wordpress.com/2006/01/07/moving-your-firefoxs-cache-files-tweaking-firefox-tipstricks/](http://webshacker.wordpress.com/2006/01/07/moving-your-firefoxs-cache-files-tweaking-firefox-tipstricks/) which has a little about boosting mozilla.  adding browser.cache.disk.parent_directory to the about:config as a string to /dev/shm did the trick.

---

