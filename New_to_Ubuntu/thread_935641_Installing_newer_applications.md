---
title: "Installing newer applications"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by cjnkns on 2008-10-01
Is it "ok" to install a newer application on my ubuntu machine than the one that is available in the repos?

For example - a newer version of gimp came out. Can I uninstall the one I currently have on Hardy to install the new one manually? 

This application is just an example of course I am curious if I can do this for any application really.

---

### Post by Forbees on 2008-10-01
you have the add/remove apps . .  but the new gimp might not be on there yet

you could just wait for ubuntu to auto update gimp, whenever the overlords add that to the list

or from the gimp site if you can find a .DEB or a .RPM you can do it manually

.deb is just double click
.rpm needs to be converted to .deb with alien

there are many tutorials on how to use alien . . . but it seems there aren't many good ones on the forums, so google search if you have to

---

### Post by hansdown on 2008-10-01
Hi cjnKns.

You should look at this thread.

[http://ubuntuforums.org/showthread.php?t=935155](http://ubuntuforums.org/showthread.php?t=935155)

---

### Post by Paqman on 2008-10-01
> **cjnkns said:**
> Is it "ok" to install a newer application on my ubuntu machine than the one that is available in the repos?


Only if you can find a .deb or another repo for it. Anything else would likely break the dependency system and prevent you from getting future updates of that application.

---

### Post by drs305 on 2008-10-01
"OK" is a pretty relative term. It is your machine and you can do what you wish to/with it. The versions in the repos don't always contain the latest version of an app. The reason for this is that until a new version is tested for reliability it is not included in the supported repositories. You can sometimes find a later version in the "proposed" repositories, which you can find and enable in the Updates tab in synaptic. These packages have been somewhat but not fully tested. For even less-tested packages, you can enable the "backports" repositories.

Fortunately, even these repositories are not full of packages that will intentionally destroy your machine. They may be fine but have had only limited testing or they may have bugs that are waiting to be fixed before the ubuntu team adds them to the repositories. If you have spent any length of time on these forums you know that even fully-tested packages don't work perfectly for everyone.

An additional consideration for Hardy is that it is a LTS (long term support) version. Updates with this version will be more limited than other releases. The goal for Hardy is to keep a stable system over a long period of time. You should not normally expect to see newer versions of most packages unless they are security related. 

You may also like to wait for the release of Intrepid Ibex, the next ubuntu release. The beta version is scheduled to be released Oct 2 and the official release is scheduled for October 30th. This will upgrade quite a few things so if you want more current versions of packages but can afford to wait another month this may be an option to consider.

For a conservative user who needs his/her system to remain reliable, I would recommend going outside the normal repositories only if you must have a feature that is unavailable in the current version. Stick to deb packages and those from reliable repositories.

For the more adventurous, have at it - you can always reinstall!

---

### Post by k3lt01 on 2008-10-01
> **cjnkns said:**
> Is it "ok" to install a newer application on my ubuntu machine than the one that is available in the repos?

For example - a newer version of gimp came out. Can I uninstall the one I currently have on Hardy to install the new one manually? 

This application is just an example of course I am curious if I can do this for any application really.
There is a reason sites like GetDeb are popular and this is because they often have "newer" versions of programs, pidgin is a good example and so is Banshee.

Some programs update very well, e.g. pidgin, and you gain more usability by upgrading. Other programs go backwards, e.g. Banshee, and you lose capabilities you use had or were expecting to keep.

I update things like Pidgin and keep the GetDeb version until an Ubuntu version is released in which case I revert to the Ubuntu version. Other programs I tend to do a google search on and look for bug reports e.g. google "Banshee wont download podcasts"or something similar. After you have read through things you can make an informed choice and weigh up the benefits vs the risks.

---

### Post by cjnkns on 2008-10-17
Thanks for all the replies I appreciate it!

Just as a side note I (today) was thinking of trying Flash 10 just for kicks.
Has anyone else uninstalled the repo version of flash for the latest and greatest?
How does it work?

---

