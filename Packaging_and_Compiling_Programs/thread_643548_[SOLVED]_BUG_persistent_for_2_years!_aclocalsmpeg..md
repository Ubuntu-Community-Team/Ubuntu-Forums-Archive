---
title: "[SOLVED] BUG persistent for 2 years?!? aclocal/smpeg.m4: underquoted definition AM_PA"
date: 2007-12-17
forum: Packaging and Compiling Programs
---

### Post by perixx on 2007-12-17
I have trouble compiling some program (freedroidRPG) vom SVN-sources; while searching for a sulution, I tried running 
```
sh autogen.sh
```
which returnded the following:
> sh autogen.sh
/usr/share/aclocal/smpeg.m4:13: warning: underquoted definition of AM_PATH_SMPEG
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
configure.ac: installing `./install-sh'
configure.ac: installing `./missing'
croppy/Makefile.am: installing `./depcomp'
configure.ac:6: installing `./config.guess'
configure.ac:6: installing `./config.sub'
You are ready to run ./configure now!


Having a look into that smpeg.m4-file, it revealed quickly, that there wasn't applied any fix, as propsed in this post at Debian's development HQ:

[http://www.linuxarkivet.se/mlists/debian-devel/0701/msg00919.html]("http://www.linuxarkivet.se/mlists/debian-devel/0701/msg00919.html")

**[COLOR="Red"]Bingo[/COLOR]** - after replacing the line
```
AC_DEFUN(AM_PATH_SMPEG,
```
with the suggested line
```

AC_DEFUN([AM_PATH_SMPEG],
```
'autogen.sh' ran without any hassle!

> 
sh autogen.sh
configure.ac: installing `./install-sh'
configure.ac: installing `./missing'
croppy/Makefile.am: installing `./depcomp'
configure.ac:6: installing `./config.guess'
configure.ac:6: installing `./config.sub'
You are ready to run ./configure now!


Obviously, dev's at Debian have been really careless about BUG-reporting in this case! And while no one addressed to that problem, it seems to have been staying [COLOR="Red"]**persistent for about 2 years**[/COLOR] now!! Really annoying...

It might be a small error and I don't know if some of my troubles have vanished with that, but things like that tend to get newbies like me tearing their hair out :P


perixx

---

### Post by dholbach on 2007-12-18
usr/share/aclocal/smpeg.m4:13: warning: underquoted definition of AM_PATH_SMPEG

is just a warning. Also it seems to have been fixed in Gutsy: [https://bugs.launchpad.net/ubuntu/+source/smpeg/+bug/52044](https://bugs.launchpad.net/ubuntu/+source/smpeg/+bug/52044)

---

### Post by Majorix on 2007-12-18
I would use the newer versions of the OS if you don't have a good reason not to.

---

### Post by perixx on 2007-12-18
Well, the reason for me not using Gutsy is that I had simply too much trouble to get it to work in the first place. Feisty - a little rough in initial installation-state, regarding menu-access and functionality, but it works much more stable... apart from Tunar, that is!

With all flavours of Gutsy (32/64bit/Mint) I couldn't even boot from Live-CD reliably, I would most probably always get stuck on black screens at boot-up and then have to manually 'startx' - and still having borked graphics and all. I had to import a working xorg.conf from my other installation. Grub didn't finish the installation and left me with crippled or no menu.lst at all. 

The stability of the OS itself was also really unsatisfactory to me. I suppose it's due to bad graphics-drivers or buggy Xorg version. And reading about many apps having serious trouble (like OO), convinced me to keep hands off Gutsy, in the end. I seriously hope that the HH - release will be better! 

Besides, I have the feeling that Ubuntu is pretty castrated when it comes to compilation -- not even 'build-essential' and 'autotools' are installed by default (!). And also other ppl. said likewise, which have by far more experience with compiling.


perixx

---

### Post by dholbach on 2007-12-19
Did you file bugs about Gutsy not booting for you?

The system is not castrated when it comes to compiling at all. build-essential is in main and on the DVD, just not on the CD. 95% of Ubuntu users will never need it and unfortunately CD size isn't unlimited.

---

### Post by perixx on 2007-12-20
Ah, no. I'm using the downloaded iso-CD-images! Pretty soon after my initial installation, I realized that many apps in the repositories are far too outdated for my taste, that's why I like to compile newest versions of some programs - 'build-essential' didn't seem to be part of the basic installation. 

There's also a certain program that I need to compile from Subversion from time to time - which won't work at all so far. These files don't come with a 'configure'-file, thus neither './configure', nor 'make' will work without running autoconf and automake first - which aren't installed by devault.

Besided, I've read many times that a lot of people miss those programs for similar reasons than me...

I regret having been too concerned about ironing out problems via the forums and paying too little attention in bugreporting; usually, I'm doing my 'bugreports' here in the forum, not via launchpad - but one time I did submit (the annoying Thunar-crashes)....

perixx

---

### Post by kelvin spratt on 2007-12-20
Thuner crashes new one to me the first thing I do is install Thunar as its rocksolid.

---

### Post by perixx on 2007-12-20
**[COLOR="Blue"]I was talking about those boot/install-problems[/COLOR]** with Gutsy 32/64-bit:
[http://ubuntuforums.org/showthread.php?t=626963]("http://ubuntuforums.org/showthread.php?t=626963")
[http://ubuntuforums.org/showthread.php?t=621827]("http://ubuntuforums.org/showthread.php?t=621827")
[http://ubuntuforums.org/showthread.php?t=612757]("http://ubuntuforums.org/showthread.php?t=612757")
[B]

Btw, I addressed the problems with 'aclocal' during compilation to the Debian-development, as Ubuntu derives from it (and also shares its errors).

[COLOR="Blue"]Regarding the Thunar-problem[/COLOR][/B] (Feisty, on 2 completely different machines), I'm referring to my post here:
[http://ubuntuforums.org/showthread.php?t=600711]("http://ubuntuforums.org/showthread.php?t=600711")
Analog to this problem I also requested help on shutting down frozen application automatically by default in this tread (no answer so far):
[http://ubuntuforums.org/showthread.php?t=599687]("http://ubuntuforums.org/showthread.php?t=599687")


[COLOR="SeaGreen"]**Having the attention**[/COLOR] of Ubuntu-involved people here...=)... perhaps you can also help me on some long-time unresolved matters..?

> Thunar's autoplay-feature + (SM-)player is unreliable:
[http://ubuntuforums.org/showthread.php?t=584700]("http://ubuntuforums.org/showthread.php?t=584700")

Disabling kernel's NTFS-abilities:
[http://ubuntuforums.org/showthread.php?t=631233]("http://ubuntuforums.org/showthread.php?t=631233")

Schedule daily 'SBackup' start at boot-up or shutdown:
[http://ubuntuforums.org/showthread.php?t=602409]("http://ubuntuforums.org/showthread.php?t=602409")

Trying to create a 'Start/Stop' internet-connection button/script:
[http://ubuntuforums.org/showthread.php?t=601847&page=3]("http://ubuntuforums.org/showthread.php?t=601847&page=3")

Disable or alter the X-server kill-Hotkey CTRL+ALT+BACKSPACE:
[http://ubuntuforums.org/showthread.php?t=603048]("http://ubuntuforums.org/showthread.php?t=603048")

Disable single/specified drive-symlinks on Xfce-desktop:
[http://ubuntuforums.org/showthread.php?t=601821]("http://ubuntuforums.org/showthread.php?t=601821")

Firefox-config-file, specifying the apps to use for certain file-/mime-types: 
[http://ubuntuforums.org/showthread.php?t=581849]("http://ubuntuforums.org/showthread.php?t=581849")

Live-CD's X-server video-output on ANALOG graphics card con.:
[http://ubuntuforums.org/showthread.php?t=633073]("http://ubuntuforums.org/showthread.php?t=633073")

Application/function to access and mount .sfs + .2fs file-containers (of Puppy):
[http://ubuntuforums.org/showthread.php?t=631627]("http://ubuntuforums.org/showthread.php?t=631627")

Function of 'nremote'-setting in gconf-editor:
[http://ubuntuforums.org/showthread.php?t=600339]("http://ubuntuforums.org/showthread.php?t=600339")

many thanks!


perixx

---

### Post by perixx on 2007-12-21
though they're off-topic, I'm gonna bump again in the hope for some answers to the questions above. Additionally, I marked thread as 'solved'.

perixx

---

