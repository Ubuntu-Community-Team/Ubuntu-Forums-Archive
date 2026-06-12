---
title: "bzr updates in edgy"
date: 2007-01-26
forum: Programming Talk
---

### Post by WebDrake on 2007-01-26
Is there a reason why bzr in Edgy is not being updated as new versions come out?  The version in Edgy is 0.11 yet the released version is now up to 0.14.

---

### Post by lnostdal on 2007-01-26
> **WebDrake said:**
> Is there a reason why bzr in Edgy is not being updated as new versions come out?  The version in Edgy is 0.11 yet the released version is now up to 0.14.

[https://wiki.ubuntu.com/TimeBasedReleases](https://wiki.ubuntu.com/TimeBasedReleases) Only bug-fixes cause an upgrade in version or just a fix/patch from the newer version to the current one.

I think there is some talk about having a rolling-release version of Ubuntu also.

Seems bzr has its own APT-repositories available. Just remove the bzr you have installed now and add the bzr-repositories to sources.list and you're good to go with the latest version.

---

### Post by gummibaerchen on 2007-01-27
add to **/etc/apt/sources.list**
```
[FONT="Courier New"]# Bazaar DVCS
deb http://bazaar-vcs.org/releases/debs/ .[/FONT]
```

Regards

---

### Post by WebDrake on 2007-01-27
Aaah, thank you for the clarification.  Personally I think it would be well worth maintaining a completely up-to-date bzr in the Ubuntu repositories as after all it is a key technology for the distro.

Oddly the bzr-gtk+ in that repository is not up to date with the bzr and bzrtools packages.  I guess it's only a matter of time, though.  I'll check on the bzr mailing list.

Thanks for the answers.

---

### Post by gummibaerchen on 2007-01-27
> **WebDrake said:**
> Aaah, thank you for the clarification.  Personally I think it would be well worth maintaining a completely up-to-date bzr in the Ubuntu repositories as after all it is a key technology for the distro.

Oddly the bzr-gtk+ in that repository is not up to date with the bzr and bzrtools packages.  I guess it's only a matter of time, though.  I'll check on the bzr mailing list.

bzr is surely not the "key-technology" in Ubuntu. That's pure non-sense! What about the latest Kernel and many other more important programs..

And if you would do so for bzr a lot of other programs would want that as well.

So, if you want a up to date version of bzr, use their repo. Now it's in heavy development, but after 1.0 is released I don't think there will be that much new versions.. And if -> Use their repo :D

:KS

---

### Post by WebDrake on 2007-01-28
> **gummibaerchen said:**
> bzr is surely not the "key-technology" in Ubuntu. That's pure non-sense! What about the latest Kernel and many other more important programs..

And if you would do so for bzr a lot of other programs would want that as well.

So, if you want a up to date version of bzr, use their repo. Now it's in heavy development, but after 1.0 is released I don't think there will be that much new versions.. And if -> Use their repo :D

:KS
I didn't say bzr was *the* key technology, I said it was *a* key technology---which it is: not in the sense of running the OS, but in terms of the wider development project that Ubuntu is building.  Much of the Ubuntu long-term strategy is centred around developing effective communication and development mechanisms to link distros, upstreams and so on.  Bzr is a central part of that.  It therefore makes sense to keep it absolutely up to date for all Ubuntu users.

---

### Post by gummibaerchen on 2007-01-28
> **WebDrake said:**
> I didn't say bzr was *the* key technology, I said it was *a* key technology---which it is: not in the sense of running the OS, but in terms of the wider development project that Ubuntu is building.  Much of the Ubuntu long-term strategy is centred around developing effective communication and development mechanisms to link distros, upstreams and so on.  Bzr is a central part of that.  It therefore makes sense to keep it absolutely up to date for all Ubuntu users.

No. At the moment I would not say that it is *a* key technology.

And as already that, if you want an up2date bazar, then I want an up2date kernel, gnome, etc pp..

---

