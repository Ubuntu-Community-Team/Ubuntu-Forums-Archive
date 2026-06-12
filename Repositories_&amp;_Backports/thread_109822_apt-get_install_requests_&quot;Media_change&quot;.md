---
title: "apt-get install requests &quot;Media change&quot;"
date: 2005-12-29
forum: Repositories &amp; Backports
---

### Post by zenslug on 2005-12-29
I installed Breezy Badger Preview back in September (no X, just using it as a headless server), and soon after the finaly version came out. I don't know too much about Ubuntu yet, so I don't know if it is possible to easily 'upgrade' to the 5.10 final.

My problem is when I try to install some packages using apt-get. Some packages have installed without any issues, while a few others require a media change. The message I get is below:

```
Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)'
in the drive '/cdrom/' and press enter
```

The problems I am having are #1: I am trying to install this stuff remotely without physical access to my machine, and #2: at night I have physical access but I've already thrown away the installation CD and don't have the iso anymore to burn another copy. And I figure there must be a better way than to need to actually put the CD in the drive.

In my attempts to work around this, I've downloaded 5.10 final and mounted it over /cdrom using a loop. 

```
$ sudo mount ubuntu-5.10-install-i386.iso /media/cdrom0 -t iso9660 -o loop
```

I can see the contents in /cdrom, read files, etc. Unfortunately, when I try to proceed with the installation apt-get doesn't see the cdrom and umounts it.

The following is the full activity:

```
$ sudo apt-get install netpbm
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  bc libnetpbm10
Recommended packages:
  gs gs-aladdin
The following NEW packages will be installed:
  bc libnetpbm10 netpbm
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1288kB of archives.
After unpacking 4542kB of additional disk space will be used.
Do you want to continue [Y/n]?
Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)'
in the drive '/cdrom/' and press enter
```

I've already done an apt-get update and even an apt-get upgrade, but it doesn't seem to help.

Maybe I'm asking the wrong questions, but isn't there something I'm missing (besides the installation CD)? I have a feeling that there must be a fairly easy fix to this problem, and any clues or guidance would help.

If I need the preview version, does anyone have an idea where to get it? All I've been able to find is the final version.

Thanks.


Alec

---

### Post by az on 2005-12-29
You mount it by hand and then apt unmounts the cdrom when it looks for the cd.  You can run apt-get and from a nother login (or terminal) re-mount the iso image.   That should work.

However, if you have net access, forget about the cd.  Comment it out in your /etc/apt/sources.list and make sure that you have the other online repositories active.  Update and it will not ask you for the cd ever again.

---

### Post by zenslug on 2005-12-29
Ok, here was the issue. The first line in my /etc/apt/sources.list was pointing to the install cd. Now that I have that commented out, it works.

Thanks Travis. :)

Below is my new /etc/apt/sources.list

```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

---

### Post by zenslug on 2005-12-29
Thanks, azz. Good timing.  ;)

---

