---
title: "Ubuntu 16.04 Renaming Packages"
date: 2016-10-13
forum: Packaging and Compiling Programs
---

### Post by optrix on 2016-10-13
I distribute my web application using debian/ubuntu packages. Unfortunately, updating to Ubuntu 16.04 won't allow the package to install, since the old *php5* package is no longer available and the plain *php* (containing PHP 7) has replaced it. (and no, I don't want my users picking up php5 from a ppa).

Previously, I could use my installer on Debian, Ubuntu and Raspbian without any difficulty. Now I need to have a specific version of the package for the latest Ubuntu (that depend on 'php'), while maintaining the old ones for other and older platforms (using 'php5' as the dependency).

There's no easier way around this? Or will I need to maintain the two distinct packages that differ **only in dependencies**, possibly for years to come?

---

### Post by ian-weisser on 2016-10-13
As dependencies evolve, you must roll with the changes. That means new versions of your package.
This seems like the original version treadmill that led to the development of snapshot distros like Debian and Ubuntu in the first place.
Debian/Ubuntu is designed to require a distinct (versioned) package for each release.
Over years, yes, that adds up.

Generally, maintaining multiple packages for multiple releases is not too annoying...if your trees and patches and changelogs are good.

---

### Post by optrix on 2016-10-13
It's more our slow internet connection and uploading several different 30MB packages when there's no change to the contents :P.

I was hoping that there may have been a tool to change the control information of the package file only - for instance, you make a single build, then run a script over it that simply changes the dependencies and throws extensions onto the end of the debian revision number.

I'm aware that some of this can be accomplished via gencontrol (which I've done) - it's just something that would be much more efficient to do post-build than pre-build. 

We also generate our packages locally and then push them to the cloud - if the control file changes could be done on the cloud-side, it would mean that we only have to update a single 30MB package locally and split it across distributions there, rather than prepare several different files for upload.

Thanks for getting back to me, anyway.

---

### Post by optrix on 2016-10-13
Below is a fragment of the script I'm using to build.

First, I use dpkg-gencontrol to create a new control file based on my template plus the changelog.

Then, I scan that file for the current version number.

I then create two different version numbers with suffixes - one for my php5.5 (14.04 LTS) version and one for my php7 (16.04 LTS) version. I also check to see if there is already a suffix present - if there isn't, I add the '-1' version number.

And finally, I use sed to replace the existing version number in the control file with the version that I'm going to build next (in the example below, I'm building **style1**, which is the php5.5/14.04 LTS version). It would make it much easier if 'version suffix' is something I could specify in either the gencontrol command-line, or the parameters file. I'm a little surprised that the option doesn't appear to be there. 

NOTE: I'm very, very poor at linux/bash scripting, so I'm probably making all kinds of errors here - but it's my solution to the issue at the moment. 

<code>

[B]dpkg-gencontrol -T./deb_info/rpi -c./deb_info/control -l./deb_info/changelog -Pdebian -O > debian/DEBIAN/control

v=`cat debian/DEBIAN/control | awk '/Version/ { print $2; exit; }'`
if [[ $v == *"-" ]]; then
  stylea="$v.ubuntu+php5+5"
  styleb="$v.ubuntu+php7"
else
  stylea="$v-1.ubuntu+php5.5"
  styleb="$v-1.ubuntu+php7"
fi

sed -i -- 's/'"$v"'/'"$style1"'/g' debian/DEBIAN/control

dpkg-deb --build ./debian /my/output/directory
[/B]
</code>

---

