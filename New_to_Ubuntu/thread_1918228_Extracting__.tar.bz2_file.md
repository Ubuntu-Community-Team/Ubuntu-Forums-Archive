---
title: "Extracting  .tar.bz2 file"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by shico90 on 2012-01-31
Hello, How can I extract >tar.bz2 files in Ubuntu?
Thank you

---

### Post by d2btoo on 2012-01-31
Double click on it, or right-click then choose "Extract here...", File Roller( Archive Manager) will do the rest.

---

### Post by MPacheco on 2012-02-03
Hello,

I downloaded the .tar.bz2 file (Blender 2.61) in tmp (on Ubuntu 11.04), right clicked on Extract Here, which it seemed to do, and then I expected the Archive Manager to take over and install it, but nothing happened.  I went to my video editing software and it's still showing the Blender v2.49.

I really do like the Software Center because it's so seamless, but I'd like to understand how to install software not yet available through the Software Center.

Any guidance is greatly appreciated for this wannabe Unbuntu user.

Thanks!

- Mal

---

### Post by drmrgd on 2012-02-03
If you don't specifically need v2.61, there is v2.58 in the repos.  Since I don't use the software, I'm not sure the difference between the two.

In answer to your question, though, the archive tool will only uncompress the package file.  From there you need to manually install the program.  Look in the uncompressed package folder for a README or INSTALL file, which will lay out the instructions for how to manually compile the program along with (hopefully!) any dependencies that the program requires, which you'll need to install as well.

---

### Post by MPacheco on 2012-02-03
Good call, I don't need 2.61, just something above 2.56.  My question is what is repos?  True Newbie here, so I'm wondering if I need to install software to install software?

---

### Post by MPacheco on 2012-02-03
Clueless, but learning: repos, repository, got it.  Downloaded Blender from the Software Center, but that's v.2.49. How do I access the v2.58 to which you're referring.  Not thru Software Center, I'm presuming.

And thank you for the help!

---

### Post by drmrgd on 2012-02-03
> **MPacheco said:**
> Clueless, but learning: repos, repository, got it.  Downloaded Blender from the Software Center, but that's v.2.49. How do I access the v2.58 to which you're referring.  Not thru Software Center, I'm presuming.

And thank you for the help!

Hmmmm...I'm on Kubuntu and that was the version that showed up in the Muon Software Utility (Kubuntu's version of Software Center).  I double checked using the Ubuntu Package Search Website and [found it there]("http://packages.ubuntu.com/search?keywords=blender&searchon=names&suite=oneiric&section=all").  I'm not sure why it's not showing up for you.

The only thing that immediately comes to mind is that my sources list is different, or you need to update package cache (not quite the right term).  First let's look at your software sources.  Would you mind opening a terminal window and typing:

```
cat /etc/apt/sources.list
```

Then copy and paste the full output (it's a bit long) here using the code tags.

While you're at it (and in the terminal) let's try something else.  Run:

```
sudo apt-get update
```

And when that's complete, run:

```
sudo apt-cache show blender
```

The second command should show the version of blender in the repository ready for installation on your system.  

Hope that helps!

---

### Post by MPacheco on 2012-02-03
Thanks for looking at the code.  I ran the update and it looks like 2.49 is the current version:

Package: blender
Priority: optional
Section: universe/graphics
Installed-Size: 28680
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Cyril Brulebois <kibi@debian.org>
Architecture: amd64
Version: 2.49.2~dfsg-2ubuntu4
Depends: libavcodec52 (>= 4:0.6-1~) | libavcodec-extra-52 (>= 4:0.6-1~), libavdevice52 (>= 4:0.6-1~) | libavdevice-extra-52 (>= 4:0.6-1~), libavformat52 (>= 4:0.6-1~) | libavformat-extra-52 (>= 4:0.6-1~), libavutil50 (>= 4:0.6-1~) | libavutil-extra-50 (>= 4:0.6-1~), libc6 (>= 2.11), libfreetype6 (>= 2.2.1), libftgl2 (>= 2.1.3~rc5), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libglu1-mesa | libglu1, libilmbase6 (>= 1.0.1), libjpeg62 (>= 6b1), libopenal1, libopenexr6 (>= 1.6.1), libopenjpeg2, libpng12-0 (>= 1.2.13-4), libpython2.7 (>= 2.7), libsdl1.2debian (>= 1.2.10-1), libstdc++6 (>= 4.5), libswscale0 (>= 4:0.6-1~) | libswscale-extra-0 (>= 4:0.6-1~), libx11-6, libxi6, zlib1g (>= 1:1.1.4), python (>= 2.5), python-support (>= 0.90.0), ttf-dejavu
Suggests: yafray, libtiff4
Filename: pool/universe/b/blender/blender_2.49.2~dfsg-2ubuntu4_amd64.deb
Size: 11189510
MD5sum: 0bb4f8841cdb97dd77d4333fe3ab448e
SHA1: 1834d5ecdcbf1efcc4b22da3875676c0b796dbc0
SHA256: 37d2b901d91c163e1ee13f24e45765b7dd1ae723f9bbfe3224f94a9e995e1bf6
Description: Very fast and versatile 3D modeller/renderer
 Blender is an integrated 3d suite for modelling, animation, rendering,
 post-production, interactive creation and playback (games). Blender has its
 own particular user interface, which is implemented entirely in OpenGL and
 designed with speed in mind. Python bindings are available for scripting;
 import/export features for popular file formats like 3D Studio and Wavefront
 Obj are implemented as scripts by the community. Stills, animations, models
 for games or other third party engines and interactive content in the form of
 a standalone binary and/or a web plug-in are common products of Blender use.
Homepage: [http://blender.org/](http://blender.org/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

mal@MPachecoLT:~$ cat /etc/apt/sources.list
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/
deb-src [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
deb-src [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

So while I'm thinking I can't get a version I need through repos, I was able to download a usable version from the blender website, but now I'm uncertain how to integrate it to it can be used with a video editor.  Any suggestions?

---

### Post by d4m1r on 2012-02-03
> **MPacheco said:**
> Hello,

I downloaded the .tar.bz2 file (Blender 2.61) in tmp (on Ubuntu 11.04), right clicked on Extract Here, which it seemed to do, and then I expected the Archive Manager to take over and install it, but nothing happened.  I went to my video editing software and it's still showing the Blender v2.49.

I really do like the Software Center because it's so seamless, but I'd like to understand how to install software not yet available through the Software Center.

Any guidance is greatly appreciated for this wannabe Unbuntu user.

Thanks!

- Mal

If you want to follow along with what the software center is actually doing, use:

sudo software-center (in terminal)

Which will a) launch software center (but the terminal will remain open) and b) show you what commands its executing

---

