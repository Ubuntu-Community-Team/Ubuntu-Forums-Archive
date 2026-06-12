---
title: "Specifiy .deb files install location"
date: 2014-05-18
forum: New to Ubuntu
---

### Post by Drowz0r on 2014-05-18
Hello all

When I install a .deb file, the Ubuntu Software centre opens and it installs pretty seamlessly. However it does not permit me to specificy a location where to install these files. Sometimes I wish for them to be placed on to a hard disk other than my primary one.

Does anyone know how to go about this?

Thanks

---

### Post by christo3 on 2014-05-18
Why do want to install packages in another location? I think the location to unpack files during installation is set when the source code is packaged.
When you install packages from online repos , the .deb files are stored at /var/cache/archives .

---

### Post by Drowz0r on 2014-05-18
My Primary HDD is just a 64GB SSD for fast booting and apps I use a lot. Things like games, videos, music I install across x2 SATA 500GB disks. If I just let every .deb file I came across go into my main disk, it'd fill up in an afternoon :)

Could I just move them to a new location from  /var/cache/archives?

---

### Post by mcduck on 2014-05-18
Your problem here is that the packages don't get installed to any single location (such as "Program Files" in Windows), but instead the contents are installed into various different directories based on what each file is sued for (for example,a ll executables for user-level applications will go to /usr/share/bin, all documentation goes to /usr/share/doc, system-wide config files to /etc, icons to /usr/share/icons, library files go to /usr/share/lib and so on.

All these locations are based on a standard, which is why you can't usually tell a package to install to any other location than the default.

However, if you need to save space on your main hard drive, there is other way to deal with it. Just move the actual system directory to another drive... For example /usr often ends being a large directory since majority of files for user-level applications get installed somewhere under it. So you could create a new partition on another hard drive, copy everything from /usr to it, and then mount that partition as /usr.

What comes to games, it depends on how you are installing them. Steam allows you to define your own location for the files, and many games that don't come as .deb packages but instead are just extracted somewhere, or come with their own installers, can of course easily be moved to another hard drive.

(/var/cache/archives is just used for storing downloaded package files in case you need to reinstall them. They aren't the actual installed programs)

Anyway, 64GB should be more than enough for the system and pretty much all the packages you'd ever want to install. At least as long as you have your /home on a separate drive. (or have /home on the system drive but use symlins or soemthing to keep the larger personal directories on the separate drive).

---

### Post by christo3 on 2014-05-18
thanks for the insight. Hope I remember this if  I ever get to use up my filesystem with applications and games. I won't be messing with /usr directly anytime soon . Maybe I'll try this in virtualbox and a USB flashdiive as the /usr partition .

---

### Post by Drowz0r on 2014-05-18
> **mcduck said:**
> Your problem here is that the packages don't get installed to any single location (such as "Program Files" in Windows), but instead the contents are installed into various different directories based on what each file is sued for (for example,a ll executables for user-level applications will go to /usr/share/bin, all documentation goes to /usr/share/doc, system-wide config files to /etc, icons to /usr/share/icons, library files go to /usr/share/lib and so on.

All these locations are based on a standard, which is why you can't usually tell a package to install to any other location than the default.

Yeah I'm finding that a lot of installers fail if I try anything other than the default. It's about 50% success.

> **mcduck said:**
>  However, if you need to save space on your main hard drive, there is other way to deal with it. Just move the actual system directory to another drive... For example /usr often ends being a large directory since majority of files for user-level applications get installed somewhere under it. So you could create a new partition on another hard drive, copy everything from /usr to it, and then mount that partition as /usr.

I've got about 40GB free, so if it gets a bit tight, moving this directory would be good.

> **mcduck said:**
> What comes to games, it depends on how you are installing them. Steam allows you to define your own location for the files, and many games that don't come as .deb packages but instead are just extracted somewhere, or come with their own installers, can of course easily be moved to another hard drive.

Yeah Steam is a life saver here... almost everything on my Steam Library has happily installed on one of the other drives.

> **mcduck said:**
> 
Anyway, 64GB should be more than enough for the system and pretty much all the packages you'd ever want to install. At least as long as you have your /home on a separate drive. (or have /home on the system drive but use symlins or soemthing to keep the larger personal directories on the separate drive).

Videos, music, documents etc are all on a separate drive yeah. So hopefully it should hold out...

---

### Post by Impavidus on 2014-05-19
With documents and media files already on a separate drive, the only thing that is likely to fill your 64GB root partition is game data. Most of this is located in /usr/share/games, so if you come to the point that you have to move something it may be good to move just that directory to a separate drive. Moving everything in /usr to a separate drive leaves very little on the SSD, as /usr contains all programs that are not vital for fixing your system in recovery mode. You would loose much of the benefit of an SSD.

I moved /usr/local to a separate partition. I use it for manually installed software and flightgear scenery files. My original intention was to easily move those files from one install to the next, or use them in two Ubuntu installs at the same time – the data files, executables would have to be recompiled. As the scenery files are downloaded automatically, it also protects me if the partition gets full: it won't affect the root partition.

If you have games with separate add-ons – that is, not included in the repos or a separate .deb, but manually installed or via an in-game download function  – it may be possible to tell the game you want them stored in a separate directory, like I did with flightgear scenery.

@christo3: If you move /usr to an usb flash drive your system may get slow, as an usb flash drive is slower than an internal drive. If you don't plug it in, your computer will only be able to boot to recovery mode.

---

