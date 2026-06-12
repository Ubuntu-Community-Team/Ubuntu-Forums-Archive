---
title: "tried to install amarok on new install of 12.04 now i get all sorts of errors"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by totiescone on 2012-07-05
I recently made the switch from vista to ubuntu,and everything was fine. today i tried to install amarok from the software centre and about halfway through it crashed and is now asking me to repair damaged files . i have selected to do this,put in my password and its done nothing for over an hour now, although in the software center it says applying changes ,is stuck in the middle of the progress bar and the little circle just goes round.i also now have a window on the desktop says sorry ubuntu 12.04 has experienced an internal error , theres lots of code there as well which i can post if needed. any help would be much appreciated. thanks

---

### Post by cariboo on 2012-07-05
I'd suggest you kill the software centre if it doesn't seem to be doing anything. Open a terminal (Ctrl-Alt-t) and type the following command:

```
sudo apt-get -f install
```

this should install any missing packages.

If you are running into broken packages, I'd suggest trying another mirror, go to Edit->Software Sources, and select a different server from the Download from: dropdown.

---

### Post by totiescone on 2012-07-06
ok done that now im getting this
Correcting dependencies... Done
The following extra packages will be installed:
  kdelibs5-data
The following NEW packages will be installed
  kdelibs5-data
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
6 not fully installed or removed.
Need to get 0 B/2,827 kB of archives.
After this operation, 7,598 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 182074 files and directories currently installed.)
Unpacking kdelibs5-data (from .../kdelibs5-data_4%3a4.8.4a-0ubuntu0.1_all.deb) ...
xz: (stdin): Compressed data is corrupt
dpkg-deb (subprocess): subprocess data returned error exit status 1
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/kdelibs5-data_4%3a4.8.4a-0ubuntu0.1_all.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/share/kde4/apps/kcharselect/kcharselect-data'
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs5-data_4%3a4.8.4a-0ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
where do i find the edit-change sources?

---

### Post by totiescone on 2012-07-06
tried changing sources i can remove it now (but not the logo from my desktop) every other place i tey toinstall from the same thing happens. is amarok just broken or is it my pc?

---

### Post by Ron O on 2012-07-19
Don't uninstall- try this.

I went through this on every installation till someone on the Amarok forums told me to open terminal and install all the dependencies:
  
sudo apt-get build-dep amarok

This will include MySQL which you will have to provide with a password one time before Amarok uses it. This has worked like a charm on 3 or more installations, but I have not got around to trying it yet on 12.04.

Get a cup of coffee first, because it takes a while.

You might want to install Ubuntu Tweak after and do a cleanup.

---

