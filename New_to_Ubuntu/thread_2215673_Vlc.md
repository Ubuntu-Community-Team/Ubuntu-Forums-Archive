---
title: "Vlc"
date: 2014-04-07
forum: New to Ubuntu
---

### Post by alexius2 on 2014-04-07
i have a VlC that I recently unnistalled and yet again installed in the ubuntu center software.

First i got the old one in the terminal off.

sudo apt-get purge vlc

then went into the center and installed the vlc.

i got the 2.0.6 but the new version is 2.1.3

why?


I have Ubuntu 12.04 LTS

---

### Post by deadflowr on 2014-04-07
Do you mean vlc 2.1.3 from vlc?
Ubuntu tries to package stability first and foremost.
As such, it freezes packages to certain versions for each release.
This keeps the chances of breakage to a minimum.

Note that packages like vlc, even though they don't get "Feature" updates, do get support/security updates.

If you want to run a newer version, then try a ppa
[Easy how to here]("http://www.webupd8.org/2013/06/install-latest-vlc-in-ubuntu-via-ppa.html")

---

### Post by monkeybrain20122 on 2014-04-07
Because Ubuntu's repository doesn't have the latest vlc. You can reinstall til the second coming and it will still be 2.06.

videolan has a ppa, but it is 'maintenance' ppa only so you won't get newer versions. There is a videolan unstable ppa, which offers the beta version (vlc 2.2) rather than the stable release so some things may not work properly [https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily). There is another ppa [https://launchpad.net/~n-muench/+archive/vlc](https://launchpad.net/~n-muench/+archive/vlc), but it is for Ubuntu 13.10 (I gather you are on 12.04, hence vlc 2.0.6 instead of 2.0.8)

The only way to get vlc 2.1.3 (actually the latest stable is 2.1.4) on Ubuntu is to compile from source. But I am not sure if it would build on 12.04 (ffmpeg may be too old) You can checkout this guide

[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)

Other than ffmpeg the other stuffs (x264, fdk-acc, opus, etc) are in the repo. Install them instead from the Software Centre or synaptic, they may be a bit old but work, you don't need to build them yourself if you are not a cutting edge guy. You don't need x265, it won't work on vlc stable release apparently. You should compile ffmpeg as in the guide because I doubt that the 12.04 version would work.

For compiling vlc, instead of getting the developmental version from git as in the guide, download the source tar ball from [http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html) (this is actually vlc 2.1.4) and you don't need to do ./bootstrap.

So basically 
1) Follow the guide's first two steps (preparations)
2) skip the rest, install the optional packages from Softeware Centre (opus, x264 etc)
3Create a new folder in your home, name it vlc_build
extract the downlaoded tarball into this folder. Let's call this vlc-2.1.4, so vlc-2.1.4 is inside vlc_build which is inside your home directory.
4)follow the guide to compile ffmpeg
5) Skip to the building vlc from git section but change the instructions to 
```
cd $HOME/vlc_build/vlc-2.1.4 &&
CPPFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include" \
LDFLAGS="-L$HOME/vlc_build/vlcdeps/usr/lib" \
PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig" \
./configure --prefix=/usr/local && \
make -j2 && \
mkdir -vp doc-pak && cp -v AUTHORS COPYING INSTALL NEWS README THANKS doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname vlc \
                  --pkgversion "2.2.0-git~$(git rev-parse --short HEAD)" \
                  --fstrans=no --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig
```

---

### Post by monkeybrain20122 on 2014-04-07
> **deadflowr said:**
> Do you mean vlc 2.1.3 from vlc?
Ubuntu tries to package stability first and foremost.
As such, it freezes packages to certain versions for each release.
This keeps the chances of breakage to a minimum.

Note that packages like vlc, even though they don't get "Feature" updates, do get support/security updates.

If you want to run a newer version, then try a ppa
[Easy how to here]("http://www.webupd8.org/2013/06/install-latest-vlc-in-ubuntu-via-ppa.html")
  

Cra*. Didn't know about this ppa, could have saved all those typing. :)

@OP forget about my long post, this would be the easiest way for you.

---

### Post by alexius2 on 2014-04-07
thank you guys, thanx monkey for that terse and not so descriptive guide :)

---

### Post by andrew.46 on 2014-04-12
According to #videolan a new version will be out soon anyway:

```

11:08 -!- 255 nicks totaly - 0 opers, 0 voices and 0 normal
11:08 -!- Home page for #videolan: http://www.videolan.org/
11:08 -!- Join to #videolan was synced in 9 secs
11:08 -!- Topic for #videolan: VideoLAN, VLC and more... | [B][COLOR="#FF0000"]21+1 bugs to go for 
          2.2.0[/COLOR][/B] | Courmisch keeps the lead! | www.videolan.org
11:08 -!- Topic set by j-b Wed Mar 26 00:33:01 2014


```

---

