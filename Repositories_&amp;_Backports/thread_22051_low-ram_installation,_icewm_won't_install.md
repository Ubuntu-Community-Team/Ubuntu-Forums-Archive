---
title: "low-ram installation, icewm won't install"
date: 2005-03-25
forum: Repositories &amp; Backports
---

### Post by p1800 on 2005-03-25
Hi,
I'm following the guide for a low-ram ubuntu installation, and have gotten to the point of installing packages.  
"apt-get install icewm" gets a response:

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  icewm: Depends: imlib1 but it is not installable
         Depends: libfontconfig1 (>= 2.2.1) but it is not installable
         Depends: libfreetype6 (>= 2.1.5-1) but it is not installable
         Depends: libice6 but it is not installable or
                  libjpeg62 but it is not installable
         Depends: libpng10-0 (>= 1.0.15-4) but it is not installable
         Depends: libsm6 but it is not installable or
                  libtiff4 but it is not installable
         Depends: libungif4g (>= 4.1.0b1) but it is not installable
         Depends: libx11-6 but it is not installable or
                  libxext6 but it is not installable or
                  libxft2 (> 2.1.1) but it is not installable
         Depends: libxrandr2 but it is not installable or
                  xlibs (> 4.3.0) but it is not installable
         Depends: libxrender1 but it is not installable

I can find all the lib packages on the installation CD, and am planning to add that to my sources.list, but where is imlib1?
And should all those lib files come along with the icewm package?

Otherwise, it's very refreshing working from command line.

Thanks,

---

### Post by az on 2005-03-25
Make sure that all your repositories are either all Warty or all Hoary.  Do not mix.  Make sure that universe is also enabled.

---

### Post by p1800 on 2005-03-31
Thanks.  After I activated both universe and main, it worked fine.

---

### Post by dfv3 on 2005-04-07
Hi p1800!

Did you get your iceWM "Programs" drop-down menu working?  

I, too, followed through the "Ubuntu/Debian-Sarge Mini-RAM How To, by Ingo LANTSCHNER (ingo@binonabiso.com)", and I've got my Ubuntu (Version 4.10) working on my old PC (Pentium MMX 400MHz, 64MB-RAM, and 880MB-HDD) --- except that the programs that I've installed does not show-up in the iceWM menu!

Through "apt-get install XXXX" --- I've installed AbiWord, gnumeric, bluefish, etc.  And I can only open these programs from the Terminal console (e.i.: typing "abiword" at the $ prompt, opens up a new abiword document).

Are your iceWM drop-down menus all working?  Perhaps, I've missed something; or there's a conflicting program that I've installed.  I've "apt-get install" all the following:
xserver-xfree86
x-window-system-core
xdm
numlockx
xterm
mozilla-firefox
abiword
gnumeric
zip
unzip
gaim
openssh-server
gpdf
cdrecord
mkisofs
bluefish
weblint
rdesktop
tsclient
emelfm

Do you have similar programs?

Help please,
dfv3 :confused:

---

### Post by btdown on 2005-04-08
I too used the same HOWTO and none of my programs showed up either. I assume we'll have to add them manually (somehow) into icewm. For now until I find a way to do it, I'll run them from xterms.

---

### Post by az on 2005-04-08
Install menu
sudo apt-get install menu

---

