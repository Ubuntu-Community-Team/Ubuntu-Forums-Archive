---
title: "Strange - CDROM will not boot fluxbuntu"
date: 2008-10-08
forum: Other OS Talk
---

### Post by Peter09 on 2008-10-08
I am trying to install fluxbuntu onto an old Pentium 111. I can install Mandriva Live CD, and Ubuntu Live CD, but not fluxbuntu. The Cdrom just says boot failure.

The same CD will boot on other machines (not as old).

I am using fluxbuntu-7.10-installer-i386.iso as the source. Anyone any ideas why this is failing?

---

### Post by Patb on 2008-10-08
Peter, I had what sounds to be the same problem some time back. See: [http://ubuntuforums.org/showthread.php?t=619593](http://ubuntuforums.org/showthread.php?t=619593)

Have a look particularly at post #6 in that thread. I never did get the CD to boot on its own but SBM is a useful tool for this little quirk.  

Let us know how you go.  Cheers, Pat.

---

### Post by snowpine on 2008-10-08
I have never used it, but apparently there is a user-authored "Fluxbuntu Remix" that addresses this problem: [https://bugs.launchpad.net/fluxbuntu-project/+bug/157724](https://bugs.launchpad.net/fluxbuntu-project/+bug/157724)

Keep in mind that Fluxbuntu 7.10 has been in "release candidate" status since Oct. 2007, so it is very much a "do it yourself" project at this point. I personally like a lot of things about it, so I'm glad I put in the effort. Good luck!

---

### Post by Patb on 2008-10-08
Thanks Snowpine. And if you don't want to download another iso image, I have just tried out the method also mentioned in that thread. Copy the (existing flawed) fluxbuntu iso image into a directory and then in that directory, as root:
```
mkdir fluxbuntu-7.10RC
mount -t iso9660 -o loop fluxbuntu-7.10-installer-i386.iso fluxbuntu-7.10RC
tar -cvf fluxbuntu-7.10RC.tar fluxbuntu-7.10RC
umount fluxbuntu-7.10RC
rmdir fluxbuntu-7.10RC
tar -xvf fluxbuntu-7.10RC.tar
chmod -R +w fluxbuntu-7.10RC
genisoimage -J -r -o fluxbuntu-7.10RC-remaster.iso -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table fluxbuntu-7.10RC
```
Now burn the remastered iso image "fluxbuntu-7.10RC-remaster.iso" to CD. This worked okay for me. 

Hope this helps. Cheers, Pat.

---

### Post by Peter09 on 2008-10-08
Thanks gents much appreciated

---

### Post by snowpine on 2008-10-08
Good luck with Fluxbuntu. I learned a lot about Linux during the time I used it. I really wish the developers would revisit the project just long enough to fix a couple of bugs and release Fluxbuntu 8.04 LTS, with a Live CD and a proper "fluxbuntu-desktop" metapackage. Then, they could officially close the doors on the project, saying "Fluxbuntu 8.04 LTS is a finished, stable project, enjoy!"

Sorry, just venting. :) There are some really good threads here on the forum if you have any questions/issues about Fluxbuntu.

---

### Post by RJARRRPCGP on 2008-10-08
It's NOTHING to do with old PCs, it failed to boot with a reasonably new PC, it just went to Windows. 
The boot data appears to be invalid.

---

### Post by snowpine on 2008-10-08
> **RJARRRPCGP said:**
> It's NOTHING to do with old PCs, it failed to boot with a reasonably new PC, it just went to Windows. 
The boot data appears to be invalid.

You are correct, this is a known bug with Fluxbuntu. It seems to affect certain models of computer/CD-rom drive, both old and new. Are you using the Fluxbuntu installer from the official site, or the Fluxbuntu Remaster from the link I provided above (or Patb's instructions)?

---

### Post by RJARRRPCGP on 2008-10-08
> **snowpine said:**
> You are correct, this is a known bug with Fluxbuntu. It seems to affect certain models of computer/CD-rom drive, both old and new. Are you using the Fluxbuntu installer from the official site, or the Fluxbuntu Remaster from the link I provided above (or Patb's instructions)?

I used the original one. Because all other 'buntu CDs are fine.

---

### Post by snowpine on 2008-10-08
> **RJARRRPCGP said:**
> I used the original one. Because all other 'buntu CDs are fine.

Fluxbuntu is an "unofficial" release candidate and does not use the same installer as Ubuntu, Kubuntu, Xubuntu, etc. I believe it actually uses a custom version of the Debian Etch installer. (but I could be wrong)

The Fluxbuntu developer confirmed the installer bug in Dec. 2007, but since Fluxbuntu is no longer an active project, it's up to the community to find a work around. (Hence the Fluxbuntu Remaster I mentioned in my previous thread.)

---

### Post by Patb on 2008-10-08
> **snowpine said:**
> I really wish the developers would revisit the project just long enough to fix a couple of bugs and release Fluxbuntu 8.04 LTS, with a Live CD and a proper "fluxbuntu-desktop" metapackage.
Snowpine +1. It would be great to have, especially for older machines. 

Cheers. Pat.

---

### Post by K.Mandla on 2008-10-09
Moved to Other OS Talk.

---

### Post by snowpine on 2008-10-09
I'll speculate that perhaps one reason we haven't seen a Hardy version of Fluxbuntu is because the minimum system specs crept upwards a bit between Gutsy and Hardy. 64mb of ram is a real issue for any Hardy install.

I had Fluxbuntu upgraded to Hardy on both of my (non-64mb) computers for a while, and it worked really well. The upgrade even solved the problem of separate "Apps" and "Applications" sub-menus. Since support for Gutsy ends in 6 months, we're in danger of losing Fluxbuntu altogether unless there is a Hardy LTS version. 

I've since switched to a couple of different Openbox distros. For some reason, I like Openbox just a little better than Fluxbox. I do miss the gorgeous green/purple Fluxbuntu theme though. I thought it had some of the nicest artwork of any distro I've seen. Does anyone know who did the artwork for Fluxbuntu?

---

### Post by wolfen69 on 2008-10-09
> **snowpine said:**
> 
I've since switched to a couple of different Openbox distros. 

have you tried Boxbuntu? great little distro.

---

### Post by snowpine on 2008-10-09
> **wolfen69 said:**
> have you tried Boxbuntu? great little distro.

Yes I have. I think if Boxbuntu and Crunchbang had come out at the same time, it might have been a coin toss for me. Currently, however, I'm using SliTaz most of the time. It's by far the fastest and lightest-weight Openbox distro that I've encountered.

---

