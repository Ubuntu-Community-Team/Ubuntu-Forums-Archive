---
title: "uL (Microlinux)"
date: 2007-02-03
forum: Other OS Talk
---

### Post by RAV TUX on 2007-02-03
[uL (Microlinux)]("http://www.u-linux.org/") for some this will be a G-d send, for others you may be left with expletives...Enjoy.

> [COLOR=DarkRed]
[/COLOR] [SIZE=3][COLOR=DarkRed]uL (Microlinux) is a tiny linux distribution providing essential command      line utilities. It fits in a few mega bytes and can be installed on the smallest USB pen drive or on older      hard disks.     [/COLOR][/SIZE][COLOR=DarkRed]
[/COLOR] [SIZE=3][COLOR=DarkRed]Lacking in both any X Window management and any specific, cutting edge application, Microlinux      obviously does not intend to compete with more comprehensive distributions and, as a matter of fact,      is not comparable even with the smaller, better built ones.[/COLOR][/SIZE][COLOR=DarkRed]
[/COLOR] [SIZE=3][COLOR=DarkRed]Indeed, uL can hardly be classified      as distribution, as its main purpose is to serve linux almost-beginners as a tutorial, as a hands-on      guide line allowing them to set up a bootable linux system in a few steps. Following the spare notes      written down in the *uL Guide*, any interested reader will in fact be able to bring his own first,      home made linux distribution to life and, even more important, to understand the inner logic of a typical      linux system.     [/COLOR][/SIZE][COLOR=DarkRed]
[/COLOR] [SIZE=3][COLOR=DarkRed]On the other side, if you have already managed to customize, install and put together linux packages,      you're probably too skilled to need what Microlinux is offering. In that case, however, it's uL that needs you:      any practical suggestion to improve and extend its features will be highly appreciated.      [/COLOR][/SIZE][COLOR=DarkRed]
[/COLOR] [SIZE=3][COLOR=DarkRed]Get in touch with us![/COLOR][/SIZE][COLOR=DarkRed]
[/COLOR] [SIZE=3][COLOR=DarkRed]G.S.[/COLOR][/SIZE][http://www.u-linux.org/](http://www.u-linux.org/)

[http://www.u-linux.org/uL-Guide.pdf](http://www.u-linux.org/uL-Guide.pdf)
> [COLOR=DarkRed]
[/COLOR][SIZE=5][COLOR=DarkRed]Download uL[/COLOR][/SIZE]
         [SIZE=3][COLOR=DarkRed]         [uL-0.2.tar.bz2]("http://www.u-linux.org/uL-0.2.tar.bz2")   (18 MB)
          [uL-0.1.tar.bz2]("http://www.u-linux.org/uL-0.1.tar.bz2")   (14 MB)
         [/COLOR][/SIZE]          
         [SIZE=5][COLOR=DarkRed]How to use uL out of an USB pen drive[/COLOR][/SIZE]
         [SIZE=3][COLOR=DarkRed]1. Unpack the downloaded release (tar xjf uL-x.y.tar.bz2) and copy the files to a previously          FAT-formatted USB pen drive.[/COLOR][/SIZE]
 [SIZE=3][COLOR=DarkRed]2. Make the pen drive bootable using the syslinux utility          ([http://syslinux.zytor.com]("http://syslinux.zytor.com/")) under Linux or Windows.         [/COLOR][/SIZE]
 [SIZE=3][COLOR=DarkRed]3. Set-up your BIOS to look first for bootable USB devices...[/COLOR][/SIZE]
         
          [SIZE=5][COLOR=DarkRed]How to use uL out of a CDROM[/COLOR][/SIZE]
         [SIZE=3][COLOR=DarkRed]         1. Unpack the downloaded release (tar xjf uL-x.y.tar.bz2) and copy the files to an empty directory  (let's call it cdrom).
         2. Rename the file syslinux.cfg isolinux.cfg.
             3. Copy the file isolinux.bin (from the above mentioned syslinux package) to the cdrom directory.
         4. From the parent directory issue the command:
         mkisofs -o uL.iso -b isolinux.bin -c boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table cdrom
         5. Burn the newly created uL.iso file to a CDROM.
          
          Enjoy!
[/COLOR][/SIZE][http://www.u-linux.org/download.htm](http://www.u-linux.org/download.htm)

---

### Post by jack.ma on 2008-07-14
The URL you gave is invalid.Please check it. If you have microlinux distro, please send it to me [mail:snip].Thanks

---

### Post by LaRoza on 2008-07-14
> **jack.ma said:**
> The URL you gave is invalid.Please check it. If you have microlinux distro, please send it to me [mail:snip].Thanks

[http://linux.wareseeker.com/System/ul-microlinux-0.2.zip/335103](http://linux.wareseeker.com/System/ul-microlinux-0.2.zip/335103)

This thread is very old, and the "Burnt Beans" mean this user was banned ;)

---

