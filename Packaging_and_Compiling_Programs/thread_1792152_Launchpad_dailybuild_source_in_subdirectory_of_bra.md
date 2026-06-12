---
title: "Launchpad dailybuild source in subdirectory of branch"
date: 2011-06-27
forum: Packaging and Compiling Programs
---

### Post by goliathdrakken on 2011-06-27
I have a repo branch that i have mirrored in Launchpad that I am trying to setup a daily build. The problem is that the source directory of the package is a subdirectory in the branch.  When building locally it's no problem because I can just change to that directory. However with launchpad's bzr-builder it does everything from the top directory in the branch. 

My current build recipe is:
```

# bzr-builder format 0.3 deb-version {debupstream}-{revno}-{revno:packaging}
lp:kegbot
nest-part packaging lp:~szechyjs/kegbot/kegbot_debian debian debian

```
Ideally I would use `lp:kegbot/pykeg` but this is not possible in bzr.

Is there a easy way I can build the package in the kegbot/pykeg directory, by setting it up in my recipe or some kind of source directory variable in the rules file?

---

