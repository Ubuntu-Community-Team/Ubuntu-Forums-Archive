---
title: "[SOLVED] ubuntu-restricted-extras broken in Intrepid?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Atreus12 on 2008-11-03
I installed intrepid last night (clean install) and am running a completely stock install except for a few packages I've added (tex, bzr,...etc).

When I tried to install ubuntu-restricted-extras, I get the following error:

```

$ sudo aptitude install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  libavcodec-unstripped-51 
The following NEW packages will be installed:
  cabextract{a} flashplugin-nonfree freepats{a} gsfonts-x11{a} gstreamer0.10-ffmpeg gstreamer0.10-pitfdll 
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly 
  gstreamer0.10-plugins-ugly-multiverse java-common{a} liba52-0.7.4{a} libavformat52{a} libcdaudio1{a} libdc1394-22{a} 
  libdvdnav4{a} libdvdread3{a} libfaac0{a} libfaad0{a} libfftw3-3{a} libfreebob0{a} libgmyth0{a} libiptcdata0{a} 
  libjack0{a} libmjpegtools0c2a{a} libmms0{a} libmp3lame0{a} libmpeg2-4{a} libmysqlclient15off{a} libneon27-gnutls{a} 
  libofa0{a} libopenspc0{a} libquicktime1{a} libsidplay1{a} libsoundtouch1c2{a} libswscale0{a} libwildmidi0{a} 
  libx264-59{a} libxvidcore4{a} msttcorefonts mysql-common{a} odbcinst1debian1{a} sun-java6-bin{a} sun-java6-jre{a} 
  sun-java6-plugin ubuntu-restricted-extras unixodbc{a} unrar xutils-dev{a} 
0 packages upgraded, 50 newly installed, 0 to remove and 0 not upgraded.
Need to get 75.8MB of archives. After unpacking 168MB will be used.
The following packages have unmet dependencies:
  libavcodec-unstripped-51: Conflicts: libavcodec51 but 3:0.svn20080206-12ubuntu3 is installed.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libavcodec-unstripped-51 [Not Installed]

Leave the following dependencies unresolved:
gstreamer0.10-pitfdll recommends w32codecs
ubuntu-restricted-extras recommends libavcodec-unstripped-51
Score is -281

Accept this solution? [Y/n/q/?] 

```

What should I do?

---

### Post by philinux on 2008-11-03
```
sudo apt-get update && sudo apt-get upgrade

sudo apt-get install ubuntu-restricted-extras
```

Working on my rig just fine.

---

### Post by Atreus12 on 2008-11-03
dang. I installed miro, I wonder if that broke it.

---

### Post by Toadinator on 2008-11-03
what you want t do is re-install the broken package and then yes, you should accept the solution. All it's saying is that it'll download some extra packages along with ubuntu-restricted-extras; no biggie. ubuntu-restricted-extras is more or less a meta package that installs all of the so called "ugly" packages at once.

---

### Post by kansasnoob on 2008-11-03
Look at this screenshot:

[ATTACH]90971[/ATTACH]

From what I've read:

> libavcodec-unstripped-51: Conflicts: libavcodec51 but 3:0.svn20080206-12ubuntu3 is installed.


It looks like one of the other packages you installed brought in libavcodec51 as a dependency, so look in synaptic like I did and try to uninstall the libavcodec51 and install libavcodec-unstripped-51 in it's place.

Using synaptic you'll see if removing the libavcodec package also removes something else. If so try reinstalling it after you've installed the proper libavcodec-unstripped package.

Clear as mud:confused:

---

### Post by Atreus12 on 2008-11-03
Yeah, that makes sense. It DOES trace back to miro. If someone has a bit of free time they should see if this can be reproduced on a completely fresh system. Just install miro, and then try to install ubuntu-restricted-extras

I guess in the past I've always installed them in the reverse order.

---

### Post by kansasnoob on 2008-11-03
> **Atreus12 said:**
> Yeah, that makes sense. It DOES trace back to miro. If someone has a bit of free time they should see if this can be reproduced on a completely fresh system. Just install miro, and then try to install ubuntu-restricted-extras

I guess in the past I've always installed them in the reverse order.

So does installing the new "unstripped" package work with miro?

---

### Post by Atreus12 on 2008-11-03
> **kansasnoob said:**
> So does installing the new "unstripped" package work with miro?

I didn't actually check. I removed miro, and then installed ubuntu-restricted-extras, and then installed miro.

I got a crash report from aptitude in the process, but after switching to apt, I was able to remove the miro packages and things seemed to go smoothly from there.

Now I wonder what sort of junk is floating around my system in the form of half broken packages...

Aptitude reports no broken packages though, so it appears to have worked.

The reason I re-installed in the first place was because of broken packages in hardy...looks like my luck continues.

Andrew

---

### Post by bapoumba on 2008-11-03
Did you install miro from the ubuntu universe repos or from another repo?
I'm asking because of the libavcodec-unstripped-5 version conflict that you have. This is the version from multiverse. Looks like a bug :)

---

### Post by Atreus12 on 2008-11-03
> **bapoumba said:**
> Did you install miro from the ubuntu universe repos or from another repo?
I'm asking because of the libavcodec-unstripped-5 version conflict that you have. This is the version from multiverse. Looks like a bug :)

The answer is: kinda.

Here's how I installed Miro:

```
sudo aptitude install miro
```
```
sudo apt-get remove miro miro-data
```
```
sudo dpkg -i miro.deb
sudo dpkg -i miro-data.deb
```

I installed miro from the official repositories in order to get all the dependencies taken care of. However, the version of miro in the repositories has [a bug](https://bugs.launchpad.net/ubuntu/+source/miro/+bug/289433) so I am using debs that a friend built for me.

So before reporting a bug, this should be reproduced on a 'vanilla' system. However, I do not think installing the debs had anything to do with the dependency conflicts.

-Andrew

---

### Post by bapoumba on 2008-11-03
Hmm, yeah, that is strange indeed.
If you removed with apt-get, aptitude does not complain because it does not know the package has been removed (they do not share log files). It does not mean that the dependencies are fixed either..

I've looked at the packages dependencies and they seem fine, as far as I can tell. Not sure how miro makes trouble as libavcodec-unstripped-51 is not a dep.
I've also looked at the medibuntu packages, but they do not ship it.

Have you enabled other third party repos in your sources.list?

---

### Post by Atreus12 on 2008-11-03
No third party repositories. I'm using [a mirror from launchpad](https://launchpad.net/ubuntu/+mirror/lug.mtu.edu-archive) because us.ubuntu.com was going really slow.

Which version "should" I have?
libavcodec51 or libavcodec-unstripped-51?

Edit: here is my sources.list:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://lug.mtu.edu/ubuntu/ intrepid main restricted
#deb-src http://lug.mtu.edu/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://lug.mtu.edu/ubuntu/ intrepid-updates main restricted
#deb-src http://lug.mtu.edu/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://lug.mtu.edu/ubuntu/ intrepid universe
#deb-src http://lug.mtu.edu/ubuntu/ intrepid universe
deb http://lug.mtu.edu/ubuntu/ intrepid-updates universe
#deb-src http://lug.mtu.edu/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://lug.mtu.edu/ubuntu/ intrepid multiverse
#deb-src http://lug.mtu.edu/ubuntu/ intrepid multiverse
deb http://lug.mtu.edu/ubuntu/ intrepid-updates multiverse
#deb-src http://lug.mtu.edu/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://lug.mtu.edu/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://lug.mtu.edu/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
#deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
#deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
#deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

---

### Post by kansasnoob on 2008-11-03
> **Atreus12 said:**
> No third party repositories.

Which version "should" I have?
libavcodec51 or libavcodec-unstripped-51?

I would go with "unstripped". That's what my Intrepid had by default (fresh install, NOT upgrade) and I've modified very little so far. Try the "unstripped" version with the other removed and run:

```
sudo apt-get -f install
```

to see if you have any unmet dependencies.

---

### Post by Atreus12 on 2008-11-03
> **bapoumba said:**
> Hmm, yeah, that is strange indeed.
If you removed with apt-get, aptitude does not complain because it does not know the package has been removed (they do not share log files). It does not mean that the dependencies are fixed either..

I've looked at the packages dependencies and they seem fine, as far as I can tell. Not sure how miro makes trouble as libavcodec-unstripped-51 is not a dep.
I've also looked at the medibuntu packages, but they do not ship it.

Have you enabled other third party repos in your sources.list?

Maybe there was a miscommunication about apt/aptitude. The steps I posted above were what I was doing *before* I messed with ubuntu-restricted-extras. I generally use aptitude because if I remove a package, it will automatically remove the dependencies. However, in this case I installed miro with aptitude, and then removed with apt-get because I didn't want it to remove the dependencies. All I removed with apt-get were the packages "miro" and "miro-data". Then I just added my new debs, and all of their dependencies were taken care of.

Now, as far as what depends on what, here was the problem (I'll show the output of aptitude to make things clear). note, I uninstalled the packages to try to troubleshoot this, that is why it is reporting unmet dependencies.

The miro package:
```

c    --\ miro                                                                                           <none>     1.2.6-0ubu
  Description: GTK+ based RSS video aggregator                                                                               
    Miro (previously known as Democracy Player) is a platform for Internet television and video. It allows you to download   
    and watch videos from RSS feeds (including podcasts, video blogs, and BitTorrent feeds).                                 
  Homepage: http://www.getmiro.com                                                                                           
  Priority: optional                                                                                                         
  Section: universe/net                                                                                                      
  Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>                                                          
  Compressed size: 1810k                                                                                                     
  Uncompressed size: 6889k                                                                                                   
  Source Package: miro                                                                                                       
  --\ Depends (34)                                                                                                           
    --- imagemagick                                                                                                          
    --- libatk1.0-0 (>= 1.20.0)                                                                                              
    --- libboost-date-time1.34.1 (>= 1.34.1-8) (UNSATISFIED)                                                                 
    --- libboost-filesystem1.34.1 (>= 1.34.1-8) (UNSATISFIED)                                                                
    --- libboost-python1.34.1 (>= 1.34.1-8) (UNSATISFIED)                                                                    
    --- libboost-thread1.34.1 (>= 1.34.1-8) (UNSATISFIED)                                                                    
    --- libc6 (>= 2.4)                                                                                                       
    --- libcairo2 (>= 1.2.4)                                                                                                 
    --- libfontconfig1 (>= 2.4.0)                                                                                            
    --- libfreetype6 (>= 2.3.5)                                                                                              
    --- libgcc1 (>= 1:4.1.1)                                                                                                 
    --- libglib2.0-0 (>= 2.16.0)                                                                                             
    --- libgtk2.0-0 (>= 2.13.6)                                                                                              
    --- libnspr4-0d (>= 1.8.0.10)                                                                                            
    --- libpango1.0-0 (>= 1.21.3)                                                                                            
    --- libssl0.9.8 (>= 0.9.8f-5)                                                                                            
    --- libstdc++6 (>= 4.2.1)                                                                                                
    --- libx11-6                                                                                                             
    --- libxine1 (>= 1.1.8) (UNSATISFIED)                                                                                    
    --- libxine1-plugins (>= 1.1.12) (UNSATISFIED)                                                                           
    --- libxine1-x (>= 1.1.12) (UNSATISFIED)                                                                                 
    --- miro-data (>= 1.2.6) (UNSATISFIED)                                                                                   
    --- python (< 2.6)                                                                                                       
    --- python (>= 2.5)                                                                                                      
    --- python-dbus                                                                                                          
    --- python-glade2                                                                                                        
    --- python-gnome2                                                                                                        
    --- python-gnome2-extras (>= 2.19.1) (UNSATISFIED)                                                                       
    --- python-gst0.10                                                                                                       
    --- python-gtk2                                                                                                          
    --- python-pysqlite2                                                                                                     
    --- python-support (>= 0.7.1)                                                                                            
    --- xulrunner-1.9                                                                                                        
    --- zlib1g (>= 1:1.1.4)                                                                                                  
  --\ Suggests (2)                                                                                                           
    --- python-psyco (UNSATISFIED)                                                                                           
    --- ttf-dejavu (UNSATISFIED)                                                                                             
  --- Packages which depend on miro (1)                                                                                      
  --\ Versions of miro (1)                                                                                                   
p    1.2.6-0ubuntu1                                                                                                                                                                                                                     


```

Note that miro depends on a package called "libxine1-plugins".

```

p    --\ libxine1-plugins                                                                               <none>     1.1.15-0ub
  Description: the xine video/media player library, meta package                                                             
    This is the xine media player library (libxine).                                                                         
                                                                                                                             
    Libxine provides the complete infrastructure for a video/media player. It supports MPEG 1/2 and some AVI and Quicktime   
    videos out of the box, so you can use it to play DVDs, (S)VCDs and most video files out there. It supports network       
    streams, subtitles and even MP3 or Ogg files. It's extensible to your heart's content via plugins for audio and video    
    output, input media, demuxers (stream types), audio/video and subtitle codecs.                                           
                                                                                                                             
    This empty package is just for your convenience and depends on commonly-used xine plugin packages.                       
  Homepage: http://xinehq.de/                                                                                                
  Priority: extra                                                                                                            
  Section: universe/libs                                                                                                     
  Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>                                                 
  Compressed size: 54.9k                                                                                                     
  Uncompressed size: 86.0k                                                                                                   
  Source Package: xine-lib                                                                                                   
  --\ Depends (2)                                                                                                            
    --- libxine1-ffmpeg (>= 1.1.15-0ubuntu3) (UNSATISFIED)                                                                   
    --- libxine1-misc-plugins (>= 1.1.15-0ubuntu3) (UNSATISFIED)                                                             
  --\ Suggests (1)                                                                                                           
    --- libxine1-gnome (>= 1.1.15-0ubuntu3) (UNSATISFIED)                                                                    
  --- Packages which depend on libxine1-plugins (3)                                                                          
  --\ Versions of libxine1-plugins (1)                                                                                       
p    1.1.15-0ubuntu3                                                                                                         


```

And libxine1-plugins depends on libxine1-ffmpeg.

```

        p    --\ libxine1-ffmpeg                                                                                <none>     1.1.15-0ub
  Description: MPEG-related plugins for libxine1                                                                             
    This package contains plugins for the xine video/media player engine, which are necessary to decode MPEG-based codecs.   
    Among them, this package includes the ffmpeg input plugin for xine, which enables xine-based players a large variety of  
    modern audio and video codecs.                                                                                           
                                                                                                                             
    You most probably want to install this package. It is required if you want to watch DVDs or digital TV using any         
    xine-based player.                                                                                                       
  Homepage: http://xinehq.de/                                                                                                
  Priority: optional                                                                                                         
  Section: libs                                                                                                              
  Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>                                                 
  Compressed size: 393k                                                                                                      
  Uncompressed size: 881k                                                                                                    
  Source Package: xine-lib                                                                                                   
  --\ Depends (12)                                                                                                           
    --- libavcodec51 (>= 3:0.svn20080206-8) | libavcodec-unstripped-51 (>= 3:0.svn20080206-8)                                
    --- libavutil49 (>= 3:0.svn20080206-8) | libavutil-unstripped-49 (>= 3:0.svn20080206-8)                                  
    --- libc6 (>= 2.8~20080505)                                                                                              
    --- libmad0 (>= 0.15.1b-3)                                                                                               
    --- libogg0 (>= 1.0rc3)                                                                                                  
    --- libpostproc51 (>= 3:0.svn20080206-8) | libpostproc-unstripped-51 (>= 3:0.svn20080206-8)                              
    --- libraw1394-8                                                                                                         
    --- libtheora0 (>= 0.0.0.alpha7.dfsg-1.1)                                                                                
    --- libvorbis0a (>= 1.1.2)                                                                                               
    --- libvorbisenc2 (>= 1.1.2)                                                                                             
    --- libxine1-bin (= 1.1.15-0ubuntu3) (UNSATISFIED)                                                                       
    --- zlib1g (>= 1:1.1.4)                                                                                                  
  --\ Conflicts (1)                                                                                                          
    --- libxine-extracodecs (< 1.1.3-1)                                                                                      
  --\ Replaces (1)                                                                                                           
    --- libxine-extracodecs (< 1.1.3-1)                                                                                      
  --- Packages which depend on libxine1-ffmpeg (11)                                                                          
  --\ Versions of libxine1-ffmpeg (1)                                                                                        
p    1.1.15-0ubuntu3                                                                                                         
  

```

Which is how I ended up with "libavcodec51". Now why that caused problems when I tried to install ubuntu-restricted-extras, I don't know. I'm sure someone who knows apt better than I could explain better.

Andrew

---

### Post by Atreus12 on 2008-11-03
> **kansasnoob said:**
> I would go with "unstripped". That's what my Intrepid had by default (fresh install, NOT upgrade) and I've modified very little so far. Try the "unstripped" version with the other removed and run:

```
sudo apt-get -f install
```

to see if you have any unmet dependencies.

Things seem to be fine now.

---

