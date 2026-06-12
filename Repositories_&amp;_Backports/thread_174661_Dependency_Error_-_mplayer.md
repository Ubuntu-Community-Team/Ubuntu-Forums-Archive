---
title: "Dependency Error - mplayer"
date: 2006-05-12
forum: Repositories &amp; Backports
---

### Post by redrabbit on 2006-05-12
Hello everyone,

I'm trying to install mplayer-586 amongst other things to get videos working in firefox.  

So I do this:

# apt-get install mplayer-586
[color=red]Error[/color]
The following packages have unmet dependencies:
  mplayer-586: Depends: libdirectfb-0.9-20 but it is not installable

# apt-get install libdirectfb-0.9-20
[color=red]Error[/color]
Package libdirectfb-0.9-20 is not available, but is referred to by another package.
However the following packages replace it:
  libdirectfb-0.9-22

So I install this new file it mentions, which is libdirectfb-0.9-**22** and it installs without a problem.  I then try to install mplayer again but errors again!

# apt-get install mplayer-586
[color=red]Error[/color]
The following packages have unmet dependencies:
  mplayer-586: Depends: libdirectfb-0.9-20 but it is not installable

The same error as before, still depends on the earlier version.  Has anyone got any suggestions as I am at a loose end and can not work it out.  I believe I am using breezy btw.

gary@ubuntu:~$ uname -a
Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

Thank you!

---

### Post by Sutekh on 2006-05-12
I believe this error occurs when you use repositories that have mis-matching lists on the latest available packages.  

Are you using the stock Breezy repositories or have you added any custom ones?  

I also assume that you have enabled the **universe** and **multiverse** repositories.  If you don't know what this means, that could be the problem.

If you like post your repositories lists here, this code prints it out
```
cat /etc/apt/sources.list
```

---

### Post by redrabbit on 2006-05-12
Using:
Backports
Marrillat
Universe

[quote="Apt-get sources"]
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy **universe**
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy **universe**

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) **breezy-backports** main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) **breezy-backports** main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

[color=grey]
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
[/color]

deb [http://www](http://www).**debian-multimedia**.org stable main
[/quote]

---

### Post by Sutekh on 2006-05-12
Okay mplayer is in the security section of the multiverse repository

[Ubuntu Packages - mplayer]("http://packages.ubuntu.com/breezy/graphics/mplayer")

So I would add the multiverse repository, both the archive and security sections, and comment out the debian-multimedia one.  

You can always change things back.

```
deb [http://gb.archive.ubuntu.com/ubuntu]("http://gb.archive.ubuntu.com/ubuntu") breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu]("http://gb.archive.ubuntu.com/ubuntu") breezy main restricted

deb [http://gb.archive.ubuntu.com/ubuntu]("http://gb.archive.ubuntu.com/ubuntu") breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu]("http://gb.archive.ubuntu.com/ubuntu") breezy-updates main restricted

deb [http://gb.archive.ubuntu.com/ubuntu]("http://gb.archive.ubuntu.com/ubuntu") breezy universe **multiverse**
deb-src [http://gb.archive.ubuntu.com/ubuntu]("http://gb.archive.ubuntu.com/ubuntu") breezy universe **multiverse**

deb [http://gb.archive.ubuntu.com/ubuntu]("http://gb.archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu]("http://gb.archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted


deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe **multiverse**
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe **multiverse**

**#**deb [http://www]("http://www/").debian-multimedia.org stable main
``` Then
```
sudo apt-get update
sudo apt-get install mplayer-586
``` 
Also you mentioned you want the mplayer plugin for Firefox?

Try [Ubuntu Packages - mozilla-mplayer]("http://packages.ubuntu.com/breezy/misc/mozilla-mplayer") also from the multiverse.
```
sudo apt-get install mozilla-mplayer
``` 
See how that goes.

---

### Post by redrabbit on 2006-05-12
Thanks.  I put those sources in an commented the multimedia one out as you suggested, more errors though:

[quote="apt-get install mozilla-mplayer"]
gary@ubuntu:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-mplayer: Depends: mplayer (>= 1.0-pre5) or
                            mplayer-custom (>= 1.0-pre5) but it is not installab le or
                            mplayer-386 (>= 1.0-pre5) but it is not going to be installed or
                            mplayer-586 (>= 1.0-pre5) but it is not going to be installed or
                            mplayer-686 (>= 1.0-pre5) but it is not installable or
                            mplayer-k6 (>= 1.0-pre5) but it is not going to be i nstalled or
                            mplayer-k7 (>= 1.0-pre5) but it is not installable o r
                            mplayer-powerpc (>= 1.0-pre5) but it is not installa ble or
                            mplayer-g4 (>= 1.0-pre5) but it is not installable o r
                            mplayer-amd64 (>= 1.0-pre5) but it is not installabl e or
                            mplayer-nogui (>= 1.0-pre5) but it is not going to b e installed
E: Broken packages
[/quote]

[quote="apt-get install mplayer-586"]
gary@ubuntu:~$ sudo apt-get install mplayer-586
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-586: Depends: libfaad2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not installable
               Depends: liblame0 (>= 3.96.1-1) but it is not installable
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
E: Broken packages
[/quote]

I did havea  look for those 3 packages it depends on, but they are not available.  After a google search the ubuntu website said they are part of the multiverse depository, however I can't find them.  I did do apt-get update too.

I guess mozilla-mplayer didn't work as it doesn't have mplayer-x86 installed.

Does it matter that I am using a 686, as uname tells me?  I did try apt-get install mplayer-686 but it is not available.

Anyway, any further suggestions?

---

### Post by Zorb on 2006-05-23
Looks like this one has been repeatedly put in the "too hard" basket.
I'm having the exact same problem and I can't find a solution other than
getting the source code for everything mplayer (or in my case acidrip, which is getting mplayer as dependancy) depends on, install it in /home/zorb/acidrip and do it the really hard way.
Kind of defeats the purpose of both Debian and Ubuntu, though, doesn't it?

---

