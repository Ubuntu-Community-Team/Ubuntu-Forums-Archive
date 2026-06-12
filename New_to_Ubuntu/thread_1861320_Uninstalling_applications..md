---
title: "Uninstalling applications."
date: 2011-10-15
forum: New to Ubuntu
---

### Post by xsabrewulf on 2011-10-15
I have installed a bunch of apps, games etc.

when I uninstall a app/game is it 100% removed? I know windows uses a registry so it requires cleaning the registry.

do i ever need to do a clean out?  I uninstall apps/games VIA software centre

---

### Post by madjr on 2011-10-15
dont worry linux/ubuntu has no registry thing and doesnt slow down with time unlike W.

---

### Post by xsabrewulf on 2011-10-15
I just noticed some folders like wine, which i did uninstall months ago. as well as a temp folder? do I need to do any maintence?

---

### Post by Ikkikke on 2011-10-15
You could try the Computer Janitor buildin.

---

### Post by mcduck on 2011-10-15
> **xsabrewulf said:**
> I have installed a bunch of apps, games etc.

when I uninstall a app/game is it 100% removed? I know windows uses a registry so it requires cleaning the registry.

do i ever need to do a clean out?  I uninstall apps/games VIA software centre

Removing an applicaton using the Ubuntu Software Center will remove all the application files, but leaves both system-wide and user-specific setting files around. That's not usually a problem, as they are just simple text files and will not affect your computer's performance in any way, and don't take any relevant amount of disc space.

Using the "Completely remove" option in Synaptic Package Manager, or "apt-get --purge remove" in a terminal will also remove any system-wide configuration files.

User-specific configuration files located in the user's home directory belong to the user, and are never removed automatically. Once again, they have no effect on performance and use no noticeable amount of drive space, and automatically removing them could result in seriously annoying situations especially on multi-user systems. You can clean them manually if you want to, but the only benefit from that is less files appearing in your home directory if you make hidden files visible. :)

...actually the only reason you'd need to remove such config files is if you messed some program's settings really badly and wanted to reset it to defaults.

Like madjr said, there is no registry that would grow and make your system slower over time.

---

### Post by Tyndarus on 2011-10-16
I've got a question which is about the same:

If you install a program from source code (configure, make, make install) let's say somewhere in ~/programs. If you want to uninstall this, do you just delete the folder? (since it hasn't been installed through package manager, it can't be deleted this way)

gtz
Dieter

---

### Post by madjr on 2011-10-16
> **Tyndarus said:**
> I've got a question which is about the same:

If you install a program from source code (configure, make, make install) let's say somewhere in ~/programs. If you want to uninstall this, do you just delete the folder? (since it hasn't been installed through package manager, it can't be deleted this way)

gtz
Dieter

i would suppose so, but am no expert.

am not sure how they handle this for example in a distro like gentoo where you need to compile everything from source.

---

### Post by mcduck on 2011-10-17
> **Tyndarus said:**
> I've got a question which is about the same:

If you install a program from source code (configure, make, make install) let's say somewhere in ~/programs. If you want to uninstall this, do you just delete the folder? (since it hasn't been installed through package manager, it can't be deleted this way)

gtz
Dieter

That really depends on the program in question, installing that way can scatter program's files all around the file system and make changes in configuration files, just like any other installed package can.

You should usually get an uninstall script, or at least instructions, with the source code. If you don't, then just trying to remove all the program's files by hand is pretty much your only option.

Anyway, there's a nice trick that allows you to install your source code through the package management. You need to install the [checkinstall]("apt:checkinstall") package, and then when compiling program instead of running "*sudo make install*" you run "*sudo checkinstall*". It will package the compled code into a .deb package and install it through the package management, making uninstalls as easy as with any other package.

(checkinstall doesn't create proper .deb packages with all the required information about dependencies, signing keys etc, so they aren't usually suitable for distribution to other computers.)

---

### Post by Tyndarus on 2011-10-17
> **mcduck said:**
> ...
You should usually get an uninstall script, or at least instructions, with the source code. If you don't, then just trying to remove all the program's files by hand is pretty much your only option.

Anyway, there's a nice trick that allows you to install your source code through the package management. You need to install the [checkinstall]("apt:checkinstall") package, and then when compiling program instead of running "*sudo make install*" you run "*sudo checkinstall*". It will package the compled code into a .deb package and install it through the package management, making uninstalls as easy as with any other package...

Ok thanks, will check it out
It's for octave, i've installed the latest version (3.4) by compiling the source code cause .deb package isn't available yet in package manager. But there seems to be a problem for using the octave-database package with 3.4 which didn't occur with 3.0 or 3.2 (according to several sources on the internet). That's why i'm downgrading...

Thanks for the quick reply

gtz
Dieter

---

### Post by Mark Phelps on 2011-10-17
Do NOT use Computer Janitor.  It has a nasty habit of removing too much stuff, rendering your PC unusable.  I had that happen to me and have seen lots of forum posts along the same lines.

---

