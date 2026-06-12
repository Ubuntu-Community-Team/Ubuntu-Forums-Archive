---
title: "program calls for specific file: no such file found"
date: 2013-11-26
forum: New to Ubuntu
---

### Post by acodea on 2013-11-26
I am trying to install a game, Lost Labyrinth. The software center opens the file: but then posts "will not install libsdl1.2:i386". I am putting this here because the makers selling this game have placed it there where no support is available, I am a newbie and have had it happen repeatedly. This is what makes Ubuntu not the most popular O/S, no packages available for games because this package or that is not available or else is of "poor quality", or am I being off the wall? The bing search of this "libsdl1.2:i386" in quotes returns two results of how many billion files?
From: Software Center:
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
libsdl-sound1.2:i386: Depends: libc6 (>= 2.4) but 2.15-0ubuntu10.5 is to be installed


                      Depends: libflac8 (>= 1.2.1) but 1.2.1-6 is to be installed
                      Depends: libmikmod2 (>= 3.1.10) but 3.1.12-2 is to be installed
                      Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.14-6.4ubuntu3 is to be installed
                      Depends: libspeex1 (>= 1.2~beta3-1) but 1.2~rc1-3ubuntu2 is to be installed
                      Depends: libvorbisfile3 (>= 1.1.2) but 1.3.2-1ubuntu3 is to be installed

---

### Post by buzzingrobot on 2013-11-26
Is the game available through Software Center, or from an independent source?  If the latter, then it is the game vendor's responsibility to know which required packages are not available from the Ubuntu repositories and then package with the game all those other packages on which it depends.  And, then, it becomes the game vendors' responsibility to ensure that it can run an each new version of Ubuntu *if* the games is advertised as being available for Ubuntu. The vendor should state which Ubuntu releases can run the game.

If the game is offered via the Software Center and will not install, then I would contact Ubuntu with the details and ask for a refund.

---

### Post by acodea on 2013-11-26
Buzzingrobot: I agree with you but if a game is not free of defects it should not be said
 to have a purpose.
Downloaded from here: [http://www.lostlabyrinth.com/index.php?p=download](http://www.lostlabyrinth.com/index.php?p=download)

And I used Ubuntu-Software-Center to try to open it. 
I went to synaptic and found the file: synaptic said there was a dependency which couldn't be met.
...and from command-line:
```
sudo apt-get install: libsdl1.2:i386
```
returns:
Package libsdl1.2:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

---

### Post by sandyd on 2013-11-26
> **acodea said:**
> Buzzingrobot: I agree with you but if a game is not free of defects it should not be said
 to have a purpose.
Downloaded from here: [http://www.lostlabyrinth.com/index.php?p=download](http://www.lostlabyrinth.com/index.php?p=download)

And I used Ubuntu-Software-Center to try to open it. 
I went to synaptic and found the file: synaptic said there was a dependency which couldn't be met.
...and from command-line:
```
sudo apt-get install: libsdl1.2:i386
```
returns:
Package libsdl1.2:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

package has wrong dependency name
[http://packages.ubuntu.com/search?keywords=libsdl1.2debian](http://packages.ubuntu.com/search?keywords=libsdl1.2debian)

Try maybe...
```
ar x lostlabyrinth*deb
tar xzf control.tar.gz
nano control
#Here, replace libsdl1.2 with libsdl1.2debian, press control+x to save
tar c {post,pre}{inst,rm} md5sums control | gzip -c > control.tar.gz
ar rcs lostlabyrinth.deb debian-binary control.tar.gz data.tar.gz
```

Commands above may need some tuning

---

