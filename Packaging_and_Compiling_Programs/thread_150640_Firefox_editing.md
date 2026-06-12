---
title: "Firefox editing"
date: 2006-03-26
forum: Packaging and Compiling Programs
---

### Post by Dr Nick^ on 2006-03-26
Heya guys,

I wanted to try to modify some packages so I started with firefox, to change my default bookmarks.

These are the things I've done:
1) Downloaded firefox_1.0.7-0ubuntu20_i386.deb

Then I converted it to a .tgz file with alien
2) sudo alien --to-tgz firefox_1.0.7-0ubuntu20_i386.deb

I extracted the tgz >> 
3) tar -zxf firefox-1.0.7.tgz

Then you get 3 directories: usr, etc and var. (for easy i've removed the .tgz file)
I put them together again: 
4) tar -czf firefox-1.0.7.tgz {etc,usr,var}
Made a debian file: 
5) sudo alien --to-deb firefox-1.0.7.tgz
And I installed the debian file: 
6) sudo dpkg -i firefox_1.0.7-2_all.deb

But for reasons this doens't work...
If I just do steps 1, 2, 5 and 6 it does work.

Anybody has an idea why this doesn't work? There aren't any hidden files either...

Greetz

---

### Post by Dr Nick^ on 2006-03-30
it worked without your help:

sudo apt-get build-dep firefox
sudo apt-get install build-essential devscripts
apt-get source firefox
cd into the firefox folder, make your changes
dch -i (this edits the changelog and increases the version number)
dpkg-buildpackage -rfakeroot
Install the newly created .deb file

Nick

---

