---
title: "Understanding AptMove"
date: 2005-12-29
forum: Repositories &amp; Backports
---

### Post by ShirishAg75 on 2005-12-29
This is being straight-lifted from the wiki :- ([https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto))

[quote=ubuntu wiki]
Make sure you have enough disk space first. 
 sudo apt-move get 
sudo apt-move move
sudo apt-move packages
It would seem that some ubuntu packages are not inserted into the packages.gz file by apt-move. Is this because of some ubuntu-specific reposiitory structure? You must delete the Packages.gz file and remake it with dpkg-scanpackages. Make the directory writable and then cd into it and run: 
  cd /mirrors/debian/dists/stable/main/binary-i386

sudo dpkg-scanpackages ../../../../pool/ /dev/null > Packages
You can identify the cd by making a .disk directory and making an info file in it. 
 Make the /mirrors/debian direcory writable and do 
 mkdir /mirrors/debian/.disk 
echo "Custom packages" $(hostname) $(date +%y%m%d) > /mirrors/debian/.disk/info
[/quote]

My questions are these :-

Q1. How much space should I devote for making Packages.gz?
Q2. The whole thing is going to be setup in a 700 MB CD so 
    how much space should I spare to make the other directories
    & files needed? Thanx in advance.

---

### Post by az on 2005-12-29
[QUOTE=shirishag75]This is being straight-lifted from the wiki :- ([https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto))



My questions are these :-

Q1. How much space should I devote for making Packages.gz?
Q2. The whole thing is going to be setup in a 700 MB CD so 
    how much space should I spare to make the other directories
    & files needed? Thanx in advance.[/QUOTE]
Q1. Packages.gz is just a text file with all the package data in it.  I think the one for universe which contains the info to 13000 packages is something like 5 megs big.  (I dunno)  So, do not worry about disk space.
Q2.  What do you mean?  Is the cd going to be just packages or are you putting other stuff on it, too?

Basically, whatever is in your /var/cache/apt/archives will be copied into your /mirrors directory.  If you have 500 megs worth of packages there, you will need another 500 megs.  You can tell apt-move to delete the files from the cache once they have been moved.  That configuration is set to no by default.

---

### Post by ShirishAg75 on 2005-12-29
[quote=azz]Q1. Packages.gz is just a text file with all the package data in it.  I think the one for universe which contains the info to 13000 packages is something like 5 megs big.  (I dunno)  So, do not worry about disk space.
Q2.  What do you mean?  Is the cd going to be just packages or are you putting other stuff on it, too?.[/quote] First of all thanx for taking time to answer my query. There will be only packages. What other stuff can I put on it. Have no idea. If u're talking about some html pages or something. That's ruled out as have no expertise or even basics yet. First understand how to make an archive then at some point know how to have a some good list. But that's in the future. Do have something small in mind which u'll find in the later half. 
[quote=azz]
Basically, whatever is in your /var/cache/apt/archives will be copied into your /mirrors directory.  If you have 500 megs worth of packages there, you will need another 500 megs.  You can tell apt-move to delete the files from the cache once they have been moved.  That configuration is set to no by default.[/quote] 
Q1.This 500 megs is for  /mirrors I guess? Is it similar to how the cp command works when we're copying one file from one place to other. Obviously with some meta-data & some links (all top of my head or guesswork). So something like let's say something like 650 MB of packages should be enough+ whatever overheads for making the different directories. I hope that's good enough. 
Q2. What is the command to tell apt-move to delete files from the cache. Would it just be ```
apt-get clean
``` or something differnt? As per whatever I know if I install something then that also is in /var/cache/apt/archives hence doing :-
a) downloading stuff
b) making a CD backup of downloads & 
c)then installing the packages. Q3. There was something also about md5sum which is there on the Install CD. If possible some kind of checksum, so that as in the Debian install CD the data integrity could be checked. How hard/easy is this to achieve?
              Thanx again in advance.

---

### Post by az on 2005-12-29
[QUOTE=shirishag75]
 
Q1.This 500 megs is for  /mirrors I guess? Is it similar to how the cp command works when we're copying one file from one place to other. Obviously with some meta-data & some links (all top of my head or guesswork). So something like let's say something like 650 MB of packages should be enough+ whatever overheads for making the different directories. I hope that's good enough. .[/QUOTE]


Yes.  If you have 650 megs of packages in /var/cache/apt/archives, then that should easliy fit onto a 700 meg cd.


Q2[QUOTE=shirishag75]. What is the command to tell apt-move to delete files from the cache. Would it just be ```
apt-get clean
``` or something differnt? .[/QUOTE]


No.  Edit /etc/apt-move.conf and change the configuration to tell apt-move to delete whatever it moves.  If you run apt-get clean before you run apt-move, you will be missing packages.


[QUOTE=shirishag75]As per whatever I know if I install something then that also is in /var/cache/apt/archives hence doing :-
a) downloading stuff
b) making a CD backup of downloads & 
c)then installing the packages. Q3. There was something also about md5sum which is there on the Install CD. If possible some kind of checksum, so that as in the Debian install CD the data integrity could be checked. How hard/easy is this to achieve?
              Thanx again in advance.[/QUOTE]


Well, once you make the cd, you can always run md5sum to tell you it's checksum.  Since the installer is not on the cd, you will not have such a nifty way of checking the cd's integrity.  You can always make a script and put it on the cd.

---

### Post by ShirishAg75 on 2005-12-29
[quote=azz]Yes.  If you have 650 megs of packages in /var/cache/apt/archives, then that should easliy fit onto a 700 meg cd.[/quote]
cool



[quote=azz]
Q2.No.  Edit /etc/apt-move.conf and change the configuration to tell apt-move to delete whatever it moves.  If you run apt-get clean before you run apt-move, you will be missing packages.[/quote]
I was talking about doing ```
apt-get clean
``` after running the apt-move package. Actually wouldn't be doing that as would be installing the packages whichever I've downloaded using ```
apt-get -d install packagename
``` so just running apt-get install packagename should do the trick.

[quote=azz]
Well, once you make the cd, you can always run md5sum to tell you it's checksum.  Since the installer is not on the cd, you will not have such a nifty way of checking the cd's integrity.  You can always make a script and put it on the cd.[/quote] Is there a wiki/page which also tells how one can copy the installer on the CD or make a list of the info ?

---

### Post by az on 2005-12-29
[QUOTE=shirishag75]
 Is there a wiki/page which also tells how one can copy the installer on the CD or make a list of the info ?[/QUOTE]

No.  There is not a wiki page about that AFAIK.  However, D-I (the debian installer) is quite well documented.  You can also download the source and read the included documentation (? I guess it is complete).  

emma@ubuntu:~$ apt-cache search installer
debian-installer-manual - Debian installation manual
...

libdebian-installer4 - Library of common debian-installer functions
bf-utf-source - Source for fonts needed to build Debian installers
di-packages-build - Helper packages for Debian-Installer packages build
kernel-wedge - udeb package builder for Debian-Installer
libdebian-installer-extra4 - Library of some extra debian-installer functions
libdebian-installer4-dev - Library of common debian-installer functions
libdirectfb-udeb-dev - frame buffer graphics library, development files
...

systeminstaller - Creates Linux distribution images from a set of packages
t...



All that you would need in that case is to generate a key to authenticate your cd (only available from the ubuntu-dev team) and write a wiki page about it and you have yourself a custom-ubuntu-distribution how-to.

---

### Post by ShirishAg75 on 2005-12-30
Thanx azz, one last thing if I wanna move some debs so they're also on this writable CD obviously with all the dependencies which I've downloaded from sites then just move them into /var/cache/apt/archives or something else is also required Thanx for all the help.

---

### Post by az on 2005-12-30
[QUOTE=shirishag75] then just move them into /var/cache/apt/archives or something else is also required Thanx for all the help.[/QUOTE]


Apt-move was made for debian package maintainers who keep their own repositories.  Every time they upload a new version of a package, they just shove it into the cache and run apt-move to update their own repository.  So, yes.  Just copy them there and re-run apt-move.  It will add to your existing repository.

---

### Post by ShirishAg75 on 2006-01-01
The cmd would be ```
sudo apt-move move
```  or something else

---

