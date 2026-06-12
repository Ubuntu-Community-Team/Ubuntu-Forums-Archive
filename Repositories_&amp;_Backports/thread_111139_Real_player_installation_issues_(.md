---
title: "Real player installation issues :("
date: 2006-01-01
forum: Repositories &amp; Backports
---

### Post by TikkiRo on 2006-01-01
[FONT="Comic Sans MS"][SIZE="3"][COLOR="Purple"]Ok - have tried EVERYTHING I've read thus far about installing this darned pkg (from the Linux links on RP site itself as well) and on trying to get it installed in Synaptic get the following error msgs:

realplay:
  Depends: libc6 (>=2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be installed
  Depends: libglib2.0-0 (>=2.8.0) but 2.6.3-1 is to be installed
  Depends: libgtk2.0-0 (>=2.8.0) but 2.6.4-0ubuntu5 is to be installed
  Depends: libpango1.0-0 (>=1.10.1) but 1.8.1-0ubuntu2 is to be installed

Now - I've gone through the entire repository as far as I can see these pkgs are already installed so I don't understand why it's still complaining about them.   I've tried installing both RPM and BIN files but still can't figure out what to do with the darned things once they're downloaded - double clicking on them opens up the contents but I can't find any sort of install/setup type file to get them to run.  Tried using commands I'd found elsewhere to do so in Terminal but can't manage that either as directories aren't correct and I don't yet understand enough of the hierarchy to figure out what I'm doing wrong.  Need help BIG TIME on this one as I'm really really keen to get this program going if at all possible.  Anyone got an hour or two to spare to 'walk' me through what I need to do to progress?  Appreciate it.:) [/COLOR][/SIZE][/FONT]

---

### Post by Solhan on 2006-01-07
I am having trouble installing Real Player myself as well, but i feel my problem is more fundamental than TikkiRo's.  I am just trying to install from the source, and this is the error i get when i run the bin file linked from the site:

./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I would guess this means my c++ source is either out of date or too updated for the package.  How would i go about changing this?

---

