---
title: "Install Arch Linux Without a CD From FTP"
date: 2007-09-21
forum: Other OS Talk
---

### Post by tuxcantfly on 2007-09-21
Note to mods: I don't see an Archlinux subforum here, so I'm posting here, move this to wherever it's appropriate. This isn't a duplicate of my other thread at [http://ubuntuforums.org/showthread.php?p=3400831](http://ubuntuforums.org/showthread.php?p=3400831) since this covers Arch Linux specific instructions, though I also posted this in the archlinux forums at [http://bbs.archlinux.org/viewtopic.php?pid=283021](http://bbs.archlinux.org/viewtopic.php?pid=283021)

Main Website At [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

**What This Does**

It's an installer for Windows or Linux users that lets you install Arch Linux without a CD. The way it works is that a small (20 MB) installer places the PXE (netboot) version of the Arch Linux installer on your hard drive, and configures your boot loader, either NTLDR if using Windows, or GRUB if using Linux, to boot from the PXE installer, and downloads and installs Arch Linux from the net.

**Requirements**

You will need to either have a Windows (95-Vista) or Linux (any distro that uses GRUB) install already on your hard drive. You'll also need an internet connection. Apart from that, the requirements are the same as the standard Arch Linux requirements.

**Instructions**

Download the appropriate installer package from [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

If using Windows, download the .exe file, if using Fedora or another rpm-based distro, download the .rpm file, if using Ubuntu or another deb-based distro, download the .deb file, and if using a distro that doesn't support rpm or deb, download the sh file.

Then, install the package, and reboot. A menu entry should appear in the boot menu, titled "UNetbootin". Select that entry, and boot.

When you get to the installer prompt, enter:

```
/arch/setup
```

And that will start the installer. When asked for a source of installation media, select "FTP". After that, the installation will be the same as if it were done using a CD; just follow the usual steps for selecting packages and partitioning, then wait as Arch Linux is downloaded from the FTP servers and installed.

**More**

UNetbootin also supports Ubuntu, Debian, and Fedora. Post a reply if you need any help, new features, or another supported distro. The website is located at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

**Notes**

If installation from FTP is broken, or if you already have the iso file, install using the iso from the hard drive; details at [http://bbs.archlinux.org/viewtopic.php?pid=284090#p284090](http://bbs.archlinux.org/viewtopic.php?pid=284090#p284090)

---

### Post by tuxcantfly on 2007-09-21
ignore this post, I'm subscribing to this thread

---

### Post by afonic on 2007-09-21
I think Arch FTP install is busted right now due to the change in the repositories from "current" to "core".

---

### Post by tuxcantfly on 2007-09-24
> **afonic said:**
> I think Arch FTP install is busted right now due to the change in the repositories from "current" to "core".

I have a workaround; I also posted this at [http://bbs.archlinux.org/viewtopic.php?pid=284090#p284090](http://bbs.archlinux.org/viewtopic.php?pid=284090#p284090)

This is how you can install Arch from a base or standard Arch iso you have already downloaded to your hard drive, without needing a CD; this is to be used as a temporary workaround while Arch's FTP servers are undergoing the transition between repos:

1. Download the Arch Install iso (either base or full will do), then install UNetbootin for Arch, procedure described in [http://bbs.archlinux.org/viewtopic.php?pid=283021](http://bbs.archlinux.org/viewtopic.php?pid=283021)
2. When you reboot, before running /arch/setup, do the following:

```
mkdir /temphdd
mount /dev/sda1 /temphdd
mount -o loop /temphdd/archlinux.iso /src
```
Here, I'm assuming that you downloaded the arch iso directly to partition 1 of hard drive 1 (/dev/sda1); adjust the filenames of the iso and directories accordingly. When you enter in:

```
ls /src
```
You should see "arch" and "isolinux". If not, you must have mounted something to the wrong spot; go back and check the commands you entered.

3. Now, run:

```
/arch/setup
```
And when you get to step 2 (select packages), select "Other/Src" installation media. It should then give you a list of packages to install. If it doesn't, and gives you an error (could not find /src/arch/pkg), go back to step 2; otherwise, if it goes well, select the packages and continue on with the standard install process.

**Notes**

Make sure you don't delete the partiton on which the iso is stored during the partitioning stage; also make sure that if you need to do partitioning for that partition, do it before mounting the partition and iso (you can't resize partitions while they're mounted).

---

### Post by tuxcantfly on 2007-10-08
Archlinux 2007.08 has been released, and it now actually has a working ftp install, which means a new build of UNetbootin for Arch... See the usual spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) for downloads (exe, sh, deb, and rpm formats)

---

### Post by ynnhoj on 2007-10-08
> **tuxcantfly said:**
> Archlinux 2007.08 has been released, and it now actually has a working ftp install, which means a new build of UNetbootin for Arch... See the usual spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) for downloads (exe, sh, deb, and rpm formats)
woo!  i can finally do a fresh install on my laptop :)

---

### Post by tuxcantfly on 2007-10-10
I've uploaded some 64-bit Arch Linux UNetbootin builds. Check the download page at [https://sourceforge.net/project/showfiles.php?group_id=198821](https://sourceforge.net/project/showfiles.php?group_id=198821) Since the packages are all marked as "noarch/all", you don't need to necessarily install 32-bit from a 32-bit OS, or 64-bit from a 64-bit OS; you can install 64-bit if your processor is capable of it (amd64 or intel core2 and above), even if you're running a 32-bit Windows or Linux install.

---

### Post by tuxcantfly on 2007-10-28
I've updated the Arch Linux UNetbootin builds to support installing from Windows Vista, usual download spot at [https://sourceforge.net/project/showfiles.php?group_id=198821](https://sourceforge.net/project/showfiles.php?group_id=198821)

---

### Post by meborc on 2007-10-29
going to try it now!

---

