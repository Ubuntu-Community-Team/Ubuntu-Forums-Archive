---
title: "Compatible &quot;app-bundle&quot; approach"
date: 2013-01-17
forum: Packaging and Compiling Programs
---

### Post by outofsync on 2013-01-17
Hi,

I'd like to ship Linux apps in a similar way as in OSX because I love the "app bundle" concept. I know Linux doesn't support "app-bundles" directly, but I believe there must be an approach which provides what I wish.

BTW: yes, I know there's also the issue of binary compatibility across Linux distributions, of course, but I'm already well documented at that.

Regarding the "app-bundle" approach I'm looking for, it should be a mechanism with these features:

1) Available on all or most Linux distributions. If the user doesn't need to install any additional component, it would be even better (i.e.: if some standard Linux feature can be used to achieve the behavior I wish, thus requiring no additional packages installation, it would be great).

2) The app is shipped as a (read-only) directory hierarchy which contains all files the app needs to run (ie: executable, read-only data, libs, etc...). Note that the executable is already built in a way where its path can be automatically determined, so the location of the rest of the files is done relative to such path, which means the "app-bundle" can be run from whatever place you wish (no installation is needed). On the other hand, writable files are put on the standard Linux places for them (temp files go to the system-standard temp directory, user settings go to its default location for them, documents go to wherever the user wishes to put them, etc...).

3) Ideally, the user should see just one file for the "app-bundle", although it has a directory hierarchy inside, but the user would see it like if it was one object.

4) The executable should be run when the user double-clicks the "app-bundle"


From all these requirements, my first thought is to consider using a **disk image**. In fact, disk images have most of what I need (a read-only directory structure, and the user sees it as just one object on the desktop), but, however... is it possible to create a disk image in a way that some executable is run when you want to open the image (so that the app is run instead of showing the contents in the disk image) ?  Maybe is there any disk image format supporting this feature on Linux?

If you've any other alternatives that could work, please tell!!!!

Thanks a lot!

---

### Post by outofsync on 2013-01-17
(btw, just a quick reply-to-myself, I just imagined another possible way: make it as a self-extracting script or executable that extracts all the app directory hierarchy to a temp dir, runs it from there, and deletes the temp dir when finished... this could be done with just 100% standard UNIX scripting, so would run in all distributions with no additional intallations, but... however... looks quite obscure and dirty...)

---

### Post by aromo on 2013-01-17
How about providing some kind of AUTORUN in the image?

---

### Post by outofsync on 2013-01-17
> **aromo said:**
> How about providing some kind of AUTORUN in the image?

Can it be expected that double-clicking on an image file located in the user hard disk will honor the autorun, or maybe some distributions or desktop environments might ignore the autorun and just open a file navigator on the disk image contents? (I'm asking because I've no idea if there's a standard behavior accepted for this)

---

