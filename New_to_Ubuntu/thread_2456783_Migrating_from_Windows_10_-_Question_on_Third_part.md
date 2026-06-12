---
title: "Migrating from Windows 10 - Question on Third party apps extenstion"
date: 2021-01-19
forum: New to Ubuntu
---

### Post by dadofrca on 2021-01-19
Hi Folks,

We'll I'm finally ditching Microsoft and gong to work on installing Ubuntu Desktop this week.  I'm going through some of the apps I need, and they have Linux installs, but I'm a bit confused by the variety of extensions.  For example, so far, the extensions below have come up while I gather all the apps I need.  Are these all compatible with Ubuntu Desktop?

.bz2
.AppImage

One app I use offers 3 different installs?
.deb
.rpm 
.PKGBUILD

---

### Post by CelticWarrior on 2021-01-19
Welcome.

Extensions, as in file name extensions, aren't that import in the end. This isn't Windows.

[**bz2** or **bzip2**]("https://en.wikipedia.org/wiki/Bzip2") is a a compressed file typical of the program with the same name.
[Appimage]("https://en.wikipedia.org/wiki/AppImage") is just one of the many way to distribute software.

> [COLOR=#000000]One app I use offers 3 different installs?[/COLOR]

Any Debian or Debian based distroi like Ubuntu and all its derivatives uses the .deb packing format. That's the one you should choose, always. And actually you should first check for the software you want in the official Ubuntu repositories. Downloading software from random websites is something ingrained in the Windows mentality you should leave behind ASAP.

---

### Post by rsteinmetz70112 on 2021-01-21
If you are moving from Windows to Ubuntu - until you get comfortable with it steer clear of anything not in the Ubuntu repositories. Most software is there although if your needs are specialized you potentially need something else but check for alternatives first, in Linux there are often several alternatives for any use. Do as much as you can from the repositories. 

Ask questions here if you need help people are willing to help if you ask for help and provide as much information as you can. You will typically get requests for clarification of your initial post including specific information. For example above you mention one app you use having 3 different installs but you don't identify the app, that limits how much help you can get. 

For what it's worth .deb is the standard way to install packages on the Debian family of Linux Distributions. Ubuntu is one of those but not all .debs will work on all distributions, that is why the correct repositories are so important. .rpm is mostly for the Red Hat family of Linux Distributions. PLKGBUILD is for the ARCH family of Linux. Other Linux distributions use other systems.

---

### Post by hikariws on 2021-01-21
If u're still learning how to install apps on Ubuntu and looking for alternatives for apps u're used to, I suggest to start installing Ubuntu on a VM. Stay on the confortable environment and put the VM on maximized mode and go using it as u find apps that fit ur needs.

No need to make the switch at once. It'll only demand u a big lot of time getting things working, which will get u very stressed and frustrated on the run. Better go slowly and smooth.

---

### Post by sdantonio on 2021-01-21
> No need to make the switch at once.

I think I took that to the extreme, I'm in the same position as you, just making the migration.  I opened the computer and set it up with 2 different hard drives, one windows and the other ubuntu so if I need to I an switch back and forth.  I'm finding I'm using the windows drive less often.  I could have gone dual boot, but that seemed like to much trouble.

---

### Post by 24superuser on 2021-01-22
The start up of dual boot depends on the settings of your system if it  is BIOS or UEFI, since you didn't leave much info so can't say much but  start from investigate your system. And as its been already said, the  virtual Box is a good place to start with linux and get more comfortable  with. Welcome to Linux community and keep going for couple of months  then I bet you switch totally to Linux for sure.

---

### Post by SeijiSensei on 2021-01-22
Windows users are used to downloading applications from various places. Most Linux distributions, Ubuntu included, store all the available applications in "repositories."  You should always use the repositories and avoid installing software from random locations.

There should be an application to install software. Use that.

---

### Post by grahammechanical on 2021-01-22
Just a little bit more information about file extensions. All software in Linux is packaged. That is why we call them packages. It includes libraries, which are referred to as dependencies and executable files, which on Windows are given the .exe extension and in Linux are given the .bin extension meaning a binary file.

There are a few different package management systems. The Redhat Package Management method produces files with the .rpm extension. Whereas the Debian package Management method produces files with the .deb extension.

Linux distributions based on Redhat install software having the .rpm extension. Linux distributions based on Debian install software having the .deb extension. Ubuntu is based on Debian and installs the .deb extension packages. There are Linux distributions based in their turn upon Ubuntu and so they also must install packages having the .deb extension.

I have never tried installing an application having the .rpm extension in Ubuntu but I would expect some problems. Not drastic ones but problems none the less.

Regards

---

### Post by TheFu on 2021-01-22
Lots of great advice above.
[LIST]
[*]Use a virtual machine for the first few months
[*]Only install software through the Ubuntu Repos, never download files to be installed directly. That includes .deb files, at least until you gain necessary background and skills to understand breakage.
[*]NEVER download drivers directly from any vendor. Stick with those built-into the Canonical Repos, unless an expert tells you something different.
[*]Dual boot can be a hassle and MSFT breaks booting other OSes about once a year.
[*]If your hardware is really new, beware. That's the bleeding edge in Linux and difficult.  Drivers may not exist at all or there might be problems for specific drivers on specific kernel versions. Linux desktops are best on a system about 18 - 36 months old.
[*]If you have a system older than 5 or 10 yrs, it could be that the current "default" desktop will be too heavy. It is very GPU dependent. There are less heavy desktops which run crazy fast on 10 yr old hardware. 
[*]File extensions mean next to nothing to Linux system, but some GUI programs will filter lists of files based on them.  It is perfectly valid to have a PDF file that doesn't end in .pdf, for example.  Executable files don't actually have any mandatory extensions at all. Humans seem to like extensions, so depending on the humans involved, there may or may not be file extensions.  Execute is a permission flag assigned to files and directories at the owner, group and "other" level.
[*].rpm files and deb files are packages, but we shouldn't be downloading those directly. .rpm files are typically built for a Redhat-based distro, so the dependencies it specifies inside will follow RH naming, which is slightly different from what Debian/Ubuntu use for package names. Sometimes, there is a 1-to-1 match in the names, but not always.  In 3 yrs after you become super-Admin, you can install 1-2 rpm files onto your ubuntu system, probably, and it won't end the world. For my time and effort, it is best not to download any packages to be installed. They will eventually break the package management system, APT on Ubuntu, and make it so the system cannot be patched at all.
[/LIST]

Linux package management has had a problem since the beginning. Users can't download a file from a random website, install it safely, and expect it to work perfectly.  The Linux OSes move too fast for that, unlike Windows.  Every distro release will have a different build of the core libraries which every other program is based on.  This means that a .deb package for Ubuntu 16.04 isn't compatible with a .deb file for 18.04 or 20.04 versions of Ubuntu or any Debian version.  A number of teams have been trying to solve that problem by making some alternate package formats and tools. The theory is to include all the dependencies in the package which usually means a 32MB program becomes 900MB in size.  Basically, it is like on Windows when a program says that MS-DotNet 4.5 is required, but doesn't install it for you. At runtime, that program will use 900MB of RAM to load the code segments. The good thing is that almost always with 18.04 and 20.04, these alternate packages work.  In my informal use on 16.04, it is a 50/50 guess whether they will work or not.  I have some that don't work on 20.04.  Anyways, these "self-contained" packages come in 3 popular file types:
[LIST]
[*]Ubuntu Snap Packages - aka "snaps"
[*]Flatpaks
[*]AppImages
[/LIST]
Each has pros/cons.  These forums have long discussions about those aspects.

Snaps on your system can be listed using the "**snap list**" command from any terminal.
Flatpaks have a similar method - **flatpak list**?  I don't know. Never used one.
AppImages usually come as files with a .AppImage extension and can be placed anywhere. Any search tool you like can find them.

In general, all those other package formats are slower and larger than the native .deb packaged version.

If you want to see what a file actually is recognized to contain in the same way as the OS, use the 'file' command.
```
$ file /bin/ls
/bin/ls: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=2f15ad836be3339dec0e2e6a3c637e08e48aacbd, for GNU/Linux 3.2.0, stripped

```
That is a natively compiled 64-bit program.

```
$ file /usr/local/vidcutter-appimage/VidCutter-6.0.0-x64.AppImage 
/usr/local/vidcutter-appimage/VidCutter-6.0.0-x64.AppImage: ELF 64-bit LSB executable, x86-64, version 1, dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.18, stripped

```

Hummm.  Thought I was putting all appimages into /usr/local/appimages/.  Ok, fixed that.  Makes life easier to have them in 1 place for backup reasons.

Anyways, hope this wasn't confusing.  Remember, all files and directories are case-sensitive on all Unix systems.

---

