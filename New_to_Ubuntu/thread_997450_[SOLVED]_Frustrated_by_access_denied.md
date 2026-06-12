---
title: "[SOLVED] Frustrated by access denied"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by martynmoore on 2008-11-29
I like the look of ubuntu after a few weeks playing with Puppy, but I'm struggling with access to some files.

I'm denied permission to edit menu.lst in GRUB and it also says "no" to installing OpenOffice3 from CD (I can only get 2.4 on the package managers).

Is there a way around these restrictions?

Also, having asked for my password string to be encrypted, I'm getting tired of having to put my password in all the time. Can I go back and turn this off?

Sorry for two Qs in one post.

---

### Post by Xiong Chiamiov on 2008-11-29
[Read about sudo]("https://help.ubuntu.com/community/RootSudo").

And, while it is possible to turn off the password for sudo, you should **never** do that!  There are many good reasons to have access to essential parts of your operating system restricted.

---

### Post by martynmoore on 2008-11-30
Thanks very much indeed. That was great for letting me edit menu.lst in GRUB.

But how do I get around the problem of installing OpenOffice3 from a CD?

I've tried several of the suggestions for getting OOo3 via the program managers - non worked. Will 3 simply become available through the normal install methods?

Seems odd that an open source OS is more restrictive re: installs than my old XP...

Great distro, though, and brilliant support community. Thanks.

---

### Post by cmay on 2008-11-30
how is the open office cd packed. is it a deb file then just click it and let it install from gdebi package installer.

---

### Post by martynmoore on 2008-11-30
Hi, thanks for the message.

The filename on the CD is "OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz".

I've only tried letting it autostart or double clicking the file icon.

Can I start gdebi package installer? I must admit to being unfamiliar with terminal commands, but learning fast!

---

### Post by Nepherte on 2008-11-30
The file on the cd is a compressed archive file (like zip archives). Unpack that file to your home directory. Because of the archive's file name, I suspect you will find a .deb file inside. Double click on that deb file and it will guide you through the install.

---

### Post by martynmoore on 2008-11-30
OK, progress.

That all worked fine. After clicking on the Desktop Integration file I get the message: "Error: Conflicts with the installed package 'openoffice.orgcore'. Does this mean I must uninstall all elements of 2.4?

---

### Post by cmay on 2008-11-30
no harm in doing that. remove under add/remove menu and install the version from your cd.  if that does not work at all you can always get the 2.4.0 back from same add/remove menu.

---

### Post by ugm6hr on 2008-11-30
Not sure where you got the OO3 CD from, but if it includes the standard .debs for your architecture (i.e. 32 vs 64-bit), this might help:
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

Obviously, you can skip the part about downloading the file, since you have it on CD.

---

### Post by martynmoore on 2008-11-30
Hi all

Thanks very much. Followed Nepherte's suggestions and all looked to be going well but no OpenOffice programs have appeared in the Applications menu.

Also, the install described at ugm6hr's helpful link is very different to Nepherte's plan - it suggests using Terminal to install a package opened/saved to the desktop.

I'm running out of time today, so will need to return to this gnarly little challenge later.

---

### Post by ugm6hr on 2008-11-30
If you copy the file from the CD to the desktop, then double-click it, it will extract to the correct directory to continue following the tombuntu guide.

This is assuming you have the 32-bit Ubuntu, and also that the file on the CD is a compressed folder that contains numerous .deb files (as per the downloaded OO.org)

---

### Post by martynmoore on 2008-11-30
Thanks ugm6hr, that looks like it worked.

My only slight worry now is that the tutorial you pointed me to warns that the "ubuntu-desktop metapackage" might have been uninstalled along with OOo2.4, making future updates of ubuntu impossible.

What do you suggest to overcome this? I'd like to be able to get ubuntu updates.

---

### Post by ugm6hr on 2008-11-30
> **martynmoore said:**
> What do you suggest to overcome this? I'd like to be able to get ubuntu updates.

I think you have misunderstood.

Updates refer to updates for your current Ubuntu version.  There is no problem with that at all.

What is affected, however, is your ability to do an upgrade to the next Ubuntu version (e.g. Hardy to Intrepid, or Intrepid to Jaunty etc).  I would always recommend a fresh install in this scenario in any case, but if you really want to do an upgrade directly, you will have to reinstall the ubuntu-desktop package first (immediately prior to the upgrade - not now).

---

### Post by martynmoore on 2008-11-30
That's great, my friend. Thanks to you and previous respondents I've made good progress this weekend.

---

