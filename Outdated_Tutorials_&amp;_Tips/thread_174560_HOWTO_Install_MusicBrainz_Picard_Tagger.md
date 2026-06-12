---
title: "HOWTO: Install MusicBrainz Picard Tagger"
date: 2006-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by yoshiznit123 on 2006-05-12
Tired of all those MP3's sitting around and not being nice and neat like the rest of your Ubuntu install :rolleyes:? You can organize your music using the MusicBrainz tagger, see [here]("http://musicbrainz.org/") for more information. THIS IS A BETA VERSION, A LOT OF THINGS WILL NOT WORK... This beta has rudimentary support for acoustic fingerprinting. This is based off the INSTALL file in the package ([INSTALL]("http://bugs.musicbrainz.org/browser/picard/trunk/INSTALL.Ubuntu")).

This has only been tested on Dapper, post below if something doesn't work for you :-)

This guide will install all packages into /usr/local, so you can easily remove them if you don't want them anymore or if they don't work.

OK, so let's get started... fire up your trusty terminal and install some dependencies:
```
sudo apt-get install libmusicbrainz4-dev libexpat1-dev libcurl3-dev fftw3-dev python2.4-ctypes python-wxgtk2.6 libmad0-dev libogg-dev libvorbis-dev libflac-dev libmp4v2-dev
```

Also, let Ubuntu know where your new libraries are:
```
echo "/usr/local/lib" | sudo tee -a /etc/ld.so.conf
```

Now, we get some libraries, compile and install them. We'll make a folder in your home directory to keep things cleaner:

```

mkdir ~/mb
cd ~/mb
wget http://www.musicdns.org/themes/musicdns_org/downloads/libofa-0.9.2.tar.gz
wget http://ftp.musicbrainz.org/pub/musicbrainz/libtunepimp-0.5.0-alpha2.tar.gz
wget http://musicbrainz.org/~matt/python-musicbrainz2-0.3.1.tar.gz
wget https://helixcommunity.org/download.php/2009/picard-0.7.0-beta3.tar.gz

tar -xzf libofa-0.9.2.tar.gz
cd libofa-0.9.2
./configure
make
sudo make install
cd ..

tar -xzf libtunepimp-0.5.0-alpha2.tar.gz
cd libtunepimp-0.5.0
./configure
make
sudo make install
cd python
python setup.py build
sudo python setup.py install
cd ../../

tar -xzf python-musicbrainz2-0.3.1.tar.gz
cd python-musicbrainz2-0.3.1
python setup.py build
sudo python setup.py install
cd 

tar -xzf picard-0.7.0-beta3.tar.gz
cd picard-0.7.0-beta3
sudo python setup.py install
cd

```

Try it out :-)
```
picard
```

This worked for me, there's a few bugs with wxPython and drawing some widgets, other than that, the UTF-8 support is wicked :-) Later, and happy taggin :-({|= 

For more info on how to use Picard, see the [wiki]("http://wiki.musicbrainz.org/PicardTaggerDocumentation")
:D

---

### Post by luks on 2006-05-15
Easier way: :)
```

sudo echo "deb http://users.musicbrainz.org/~luks/ubuntu dapper main" >>/etc/apt/sources.list
sudo apt-get update
sudo apt-get install picard

```

---

### Post by sciyoshi on 2006-05-16
Except I tried that, and I think the musicbrainz library is out of date... meh :-) Oh and by the way this is my real account, I accidentally made two... does anybody know how I can delete the old one? Later

---

### Post by luks on 2006-05-16
[QUOTE=sciyoshi]Except I tried that, and I think the musicbrainz library is out of date... meh :-)[/QUOTE]
Which one?

---

### Post by blackjack6.21.91 on 2006-06-10
Thanks for the how to.. but I ran into errors compiling libtunepimp.  It gave me
> *  Version 0.4.0 or higher of the the Open Fingerprint
*  Architecture library library needs to be installed.
*  Please download the library from
*  [http://www.musicdns.org/downloads](http://www.musicdns.org/downloads)
*
configure: error: Cannot build. Stop.


So I grabbed the library over there and compiled it with no errors but libtunepimp kept echoing that.. wierd.  Any help would be appreciated.  I really don't like the taggers in the repos right now..

---

### Post by luks on 2006-06-10
[QUOTE=blackjack6.21.91]So I grabbed the library over there and compiled it with no errors but libtunepimp kept echoing that.. wierd.  Any help would be appreciated.  I really don't like the taggers in the repos right now..[/QUOTE]

Make sure you have /usr/local/lib in /etc/ld.so.conf, and you run ldconfig after installing libofa.

An alternative, as I already said in this thread, is to use [MusicBrainz repository]("http://wiki.musicbrainz.org/PicardLinuxInstall#head-5f60c040c32c67c304b335181b88678ad34149c2").

---

### Post by hugmenot on 2006-06-19
What is wrong here?```
$ picard
Traceback (most recent call last):
  File "/usr/bin/picard", line 2, in ?
    from picard.tagger import main; main('/usr/share/locale')
  File "/usr/lib/python2.4/site-packages/picard/tagger.py", line 73, in ?
    from picard import events, coverartcache, albummanager, util, album, debug, tpmanager, cluster, wpath, cuesheet, playlist, puidmanager
  File "/usr/lib/python2.4/site-packages/picard/albummanager.py", line 57, in ?
    import album, artist, track, coverartcache, events, util, cluster, debug
  File "/usr/lib/python2.4/site-packages/picard/album.py", line 57, in ?
    import dataobjs, artist, track, util
  File "/usr/lib/python2.4/site-packages/picard/dataobjs.py", line 55, in ?
    import util
  File "/usr/lib/python2.4/site-packages/picard/util.py", line 78, in ?
    class ConfigSettings(object):
  File "/usr/lib/python2.4/site-packages/picard/util.py", line 102, in ConfigSettings
    settingID3Encoding = tunepimp.eUTF8
AttributeError: 'module' object has no attribute 'eUTF8'
```


and here&#8217;s what I&#8217;ve got:```
$ apt-cache policy picard
picard:
  Installiert:0.7.0-beta3-0ubuntu2
  Mögliche Pakete:0.7.0-beta3-0ubuntu2
  Versions-Tabelle:
 *** 0.7.0-beta3-0ubuntu2 0
        500 http://users.musicbrainz.org dapper/main Packages
        100 /var/lib/dpkg/status
```

---

### Post by luks on 2006-06-19
Old version of python bindings for libtunepimp. It's a problem of the package, python-tunepimp depends on python2.4-tunepimp, but not on specific version of python2.4-tunepimp, so it is using the old 0.3.0 one. Upgrade python2.4-tunepimp to 0.5.0-... version and it should work.

---

### Post by hugmenot on 2006-06-19
[QUOTE=luks]Old version of python bindings for libtunepimp. It's a problem of the package, python-tunepimp depends on python2.4-tunepimp, but not on specific version of python2.4-tunepimp, so it is using the old 0.3.0 one. Upgrade python2.4-tunepimp to 0.5.0-... version and it should work.[/QUOTE]

I see: aptitude install python2.4-tunepimp=0.5.0-alpha2-0ubuntu1

EDIT: And you are quite quick :) Shouldn&#8217;t you depend on this specific version of tunepimp? python-tunepimp will be python2.4-tunepimp anyway in Dapper &#8211; won&#8217;t it?

---

### Post by hugmenot on 2006-06-19
Thanks luks, got it working now (it&#8217;s grinding away on my files)

Looking around (I downloaded it to see whether my initial impression from the usual player plugins was right) it seems MB is corroborating the oversimplistic view of musical meta-data.

```
Satie: The Complete Solo Piano Music (disc 1) (feat. piano: Jean-Yves Thibaudet)
```
It looks like really old-school snake concatenation style. Is this how it&#8217;s supposed to look like? Are there really only three textual fields that describe the album and its titles?
What about performer, conductor, composer, discnumber, albumartist etc pp.? What about multi-value fields?

Just checking wether I am having misconceptions here.

---

### Post by luks on 2006-06-19
[QUOTE=hugmenot]EDIT: And you are quite quick :) Shouldn&#8217;t you depend on this specific version of tunepimp? python-tunepimp will be python2.4-tunepimp anyway in Dapper &#8211; won&#8217;t it?[/QUOTE]

Yes, I should :) But I found out this problem just a few days ago and still didn't have time to fix it.

And about the album title. Yes, that's how it is currently supposed to be. You can link albums/tracks to conductors, performers, composers, ... on the web site, but these data are not used by the tagger, atm.

---

### Post by hugmenot on 2006-06-19
Yes, I see clearer now. [It&#8217;s a policy indeed](http://wiki.musicbrainz.org/ClassicalStyleGuide) :rolleyes:. Atrocious.

(feat. MC Beethoven in da hood)

---

### Post by nir78 on 2006-07-07
I follow all instruction and python upgrade instruction... but still:
[PHP]Traceback (most recent call last):
  File "/usr/bin/picard", line 2, in ?
    from picard.tagger import main; main('/usr/share/locale')
  File "/usr/lib/python2.4/site-packages/picard/tagger.py", line 61, in ?
    import sys, os, locale, copy, wx
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
    from wx._core import *
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
    import _core_
ImportError: /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core_.so: symbol _ZN12wxAppConsole15CreateLogTargetEv, version WXU_2.6 not defined in file libwx_baseu-2.6.so.0 with link time reference
[/PHP]

Anybody ??? Help ?? ](*,)

---

### Post by gurgle on 2006-07-18
im getting a file not found on the musicbrainz repo. anyone else getting this?

im using amd64

---

### Post by luks on 2006-07-18
> **gurgle said:**
> im getting a file not found on the musicbrainz repo. anyone else getting this?

im using amd64

yes, there are only source packages and binaries for i386. i don't have any amd64 machine available to build the packages on.

---

### Post by gurgle on 2006-08-03
anyone got a amd64 .deb?

---

### Post by themightychris on 2006-08-28
> **luks said:**
> yes, there are only source packages and binaries for i386. i don't have any amd64 machine available to build the packages on.



I too am looking for an AMD64 deb, especially now that there is a stable release.  If you are willing to build the package for AMD64 I am certainly willing to give you shell access to an AMD64 machine.

---

### Post by luks on 2006-08-28
> **themightychris said:**
> I too am looking for an AMD64 deb, especially now that there is a stable release.  If you are willing to build the package for AMD64 I am certainly willing to give you shell access to an AMD64 machine.
I've actually added amd64 packages to the repository just yesterday. But they were not built by me and I haven't tested them at all, there is a chance that something might not work...

---

### Post by Corbelius on 2006-08-29
> **luks said:**
> I've actually added amd64 packages to the repository just yesterday. But they were not built by me and I haven't tested them at all, there is a chance that something might not work...

I just install Picard from your repository on my amd64 system, work fine, thanks for the good application (musicbrainz has a enormous database, better than cddb).

Suggest: why u dont add a "genre" music tag?  

Tnx Again :)

---

### Post by luks on 2006-08-29
> **Corbelius said:**
> 
Suggest: why u dont add a "genre" music tag?

Because genre is subjective and MusicBrainz tries to store only facts. :)

---

### Post by beetee2 on 2006-09-07
:ks

---

### Post by candlepin on 2006-09-16
please forgive the noob that I am.  

I'm trying to install this program.  I get up to the command:
sudo apt-get install picard 

but I get an error:
  picard:  Depends: python-tunepimp (>= 0.5.1) but it is not going to be installed
E: Broken packages

Please help!!

---

### Post by Washington Irving on 2006-11-19
I get this:
```
The following packages have unmet dependencies.
  picard: Depends: python-support (>= 0.2) but 0.1.1ubuntu1 is to be installed
          Depends: python-musicbrainz2 but it is not going to be installed
          Depends: python-tunepimp (>= 0.5.2) but it is not going to be installed
E: Broken packages

```

---

### Post by pedrorolo on 2007-03-06
I installed picard on my edgy using musicbrainz' repository and when I run it it spits this:

```
> picard
Traceback (most recent call last):
  File "/usr/bin/picard", line 2, in ?
    from picard.tagger import main; main('/usr/share/locale')
  File "/var/lib/python-support/python2.4/picard/tagger.py", line 75, in ?
    from tunepimp import tunepimp
  File "/usr/lib/python2.4/site-packages/PIL/__init__.py", line 27, in ?

ImportError: No module named _tunepimp
```

Though, there were no dependency problems during the install

python2.4-tunepimp package is not installed, and when I try to install it, it tries to remove picard.

Does anyone know how to install Picard on Edgy?

Thanks,
Pedro

---

### Post by voidmain on 2007-03-07
If you are having problems on Feisty (or possibly Edgy) with MP3s, the Picard debs do not automatically pull in support to tunepimp and MP3s. You need to install an extra package to get this working:

```

sudo apt-get install libtunepimp5-mp3

```

This should install the tunepimp plugin for MP3 handling.

---

### Post by sciurus on 2007-12-10
> **voidmain said:**
> If you are having problems on Feisty (or possibly Edgy) with MP3s, the Picard debs do not automatically pull in support to tunepimp and MP3s. You need to install an extra package to get this working:

```

sudo apt-get install libtunepimp5-mp3

```

This should install the tunepimp plugin for MP3 handling.

Thanks for that tip; it helped on Gutsy.

---

