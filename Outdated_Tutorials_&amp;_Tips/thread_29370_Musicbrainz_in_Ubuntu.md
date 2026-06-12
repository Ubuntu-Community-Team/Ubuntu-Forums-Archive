---
title: "Musicbrainz in Ubuntu"
date: 2005-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Gianni Exile on 2005-04-24
Get the packages 
  libtunepimp2 libtunepimp2-dev libtunepimp-bin

from Debian/testing and magically apps like amarok and juk will be able to use musicbrainz again (Guess MP3 tags from Internet based on file contents).  

It looks like ubuntu disabled mp3 header reading.

---

### Post by JonahRowley on 2005-05-01
> It looks like ubuntu disabled mp3 header reading.

Actually, musicbrainz doesn't have much to do with the header at all, it generates a unique ID based on the waveform of the audio.  This means it has to decode the mp3, which means it's patent-encumbered code..  Maybe there should be an alternative package in multiverse instead of having to get the debian packages?

Edit:  Just a small warning, don't install the -dev package unless you need it, or install the Ubuntu -dev package.  The debian -dev package depended on packages I didn't have, and apt refused to install anything else until I removed it.

Edit:  **OK, now a big warning**, there appears to be an infinite memory consumption bug related to musicbrainz or libtunepimp and amaroK.  It's very annoying, perhaps there should be some resource limits to prevent things like this bringing the whole system down?

---

### Post by JonahRowley on 2005-05-01
OK, I've got this working well.  I went the other method, with apt-build.  You have to install libmad0 and libmad0-dev in order for libtunepimp2 to have mp3 support.  The following commands will get things done:

```
apt-get install libmad0 libmad0-dev apt-build
apt-build --reinstall install libtunepimp2
apt-get install libtunepimp2 libtunepimp-bin
```

The last apt-get install is because apt-build count not install it, but you can force it with apt-get.  Everything is working well, and no infinite memory utilization!

Edit:  *sigh* spoke too soon, I categorized maybe 150 songs before I can into it again, but the memory problem is still there.

---

### Post by Gianni Exile on 2005-05-17
I don't know what client you're using, but I wrote my own and it works fine, no leaks running over ~2000 songs without any errors.  I had no problems with any other client either (Juk, etc).

---

### Post by pirrux on 2005-05-25
[QUOTE=JonahRowley]OK, I've got this working well.  I went the other method, with apt-build.  You have to install libmad0 and libmad0-dev in order for libtunepimp2 to have mp3 support.  The following commands will get things done:

```
apt-get install libmad0 libmad0-dev apt-build
apt-build --reinstall install libtunepimp2
apt-get install libtunepimp2 libtunepimp-bin
```

The last apt-get install is because apt-build count not install it, but you can force it with apt-get.  Everything is working well, and no infinite memory utilization!

Edit:  *sigh* spoke too soon, I categorized maybe 150 songs before I can into it again, but the memory problem is still there.[/QUOTE]
 JonahRowley, I've used you metod and it work!!!! THX

---

### Post by boobytrapped on 2005-06-06
I realized as well that the ubuntu hoary versions of the libtunepimp2 and libtunepimp-bin packages got compiled with mp3 support intentionally left out.  This is really sad, because most of the music files people have are still in mp3 format, and it is a big loss in quality to tanscode them into ogg.

I tried the apt-build method to build libtunepimp2 but it kept on giving me errors about a size mismatch.

```

After unpacking 0B of additional disk space will be used.
Get:1 http://archive.ubuntu.com hoary/main libtunepimp-bin 0.3.0-2ubuntu5 [22.7kB]
Fetched 22.3kB in 0s (45.0kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libt/libtunepimp/libtunepimp-bin_0.3.0-2ubuntu5_i386.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I could not figure out how to work around this problem. So instead I went to packages.debian.org and downloaded libtunepimp2 and libtunepimp-bin packages for the debian-testing distribution.  These packages install very easily using dpkg -i packagename.deb command.

Now, I can query the MusicBrainz database for my mp3 files without any problems.  The mechanism works both via the command line (using the 'trm' command) and from within amarok.

---

### Post by RastaMahata on 2005-06-12
I think this only applies for kubuntu (KDE apps)

---

### Post by boobytrapped on 2005-06-12
[QUOTE=RastaMahata]I think this only applies for kubuntu (KDE apps)[/QUOTE]

I don't think that is the case.  the libtunepimp-bin packages is supposed to provide command line utilities that one can use to find the MusicBrainz fingerprint of any music file.

```

(ali@gravity:~)% trm
usage: trm [-i|-l] <audio file>
Options:
  -i   Print out track metadata along with trm id
  -l   Lookup file at MusicBrainz

BROWSER environment variable to specify your browser of choice.
Check http://www.catb.org/~esr/BROWSER/index.html for details.

Supported file extensions: .wav .mp3 .ogg .flac
(ali@gravity:~)%

```

The default packages in Ubuntu were compiled with mp3 support disabled because (apparently) the developers did not want to have libmad as a dependency.  However, no alternative package is available on Ubuntu that can provide the trm functionality for mp3 files.  

I mentioned amarak because, amarok is one of the few (the only?) music app on ubuntu that comes with musicbrainz (and audioscrobbler) support built in.  I use amaraok even though I do not use KUbuntu.

(BTW, another tip for amaraok users on GNOME: you need konqueror to be installed in order to musicbrainz lookup to work, in addition to the debian testing packages for libtunepimp.)

---

### Post by TheOtherShoe on 2005-09-13
I am using Breezy, and installing the debian version of libtunepimp did not work so well for me. For some reason these packages all have different names in Breezy, as well as some of the dependencies.

So here are my instructions for getting Musicbrainz working in Breezy, based on the instructions posted by JonahRowley:

```
cd some-temp-dir-you-don't-mind-getting-messy
apt-get install libmad0 libmad0-dev
apt-get build-dep libtunepimp2c2
apt-get source libtunepimp2c2
apt-get source -b libtunepimp2c2
dpkg -i libtunepimp2c2_0.3.0-2ubuntu7_i386.deb
```
It is possible the package name in the last line will not be exactly right. Just look around in your working directory and install the deb you find there.

---

### Post by Prolyprole on 2005-10-25
For Breezy you need the debs from the unstable section of Debian rathe than testing. You will know if they are the right ones if it is libtunepimp2c2 rather than libtunepimp2.

I downloaded, installed, and they worked fine.

---

### Post by crispingatiesa on 2005-11-03
I installd  the deb package and it worked. But, now I have the Synaptic notification red ball in the corner of the task bar saying that I have a broken package. Of course, the broken package is he installed .deb. 


I don't know in the developers book but in mine ain't broken if it works. it was broken before!!!,f,  that I couldn't get anything from Musicbrainz!!! ehhh!

---

### Post by virtualXTC on 2006-06-05
Could someone please post the binarys for this (.deb)?  Or at least put a link to a repoistory that fixes this issue so I can just edit my apt/sources.list ?
It would probably save a lot of people some time if they don't have to recompile this.

thanks

---

### Post by daiwai on 2006-06-09
I followed TheOtherShoe's instructions except using libtunepimp2c2a as this seems to be the version dapper is using. Everything works fine but in the Adept Updater it now lists the package as upgradable. Can I exclude that package from upgrades, so the updater does not always sit in the system tray?

---

### Post by iggykoopa on 2006-06-28
same thing is happening to me, anybody figure it out yet?

---

### Post by TheOtherShoe on 2006-07-11
Here is the deb compiled for Dapper:

[http://sitr.us/blog/files/libtunepimp2c2a_0.3.0-9.1ubuntu4_i386.deb](http://sitr.us/blog/files/libtunepimp2c2a_0.3.0-9.1ubuntu4_i386.deb)

This package will allow MusicBrainz to support MP3 files. And I have incremented the version number so the package will not be marked as upgradeable - until an actual newer version comes out that is.

---

### Post by Glauco on 2006-07-11
Thanks, pal... It was bothering me. Now, it works again. Thanks.

> **TheOtherShoe said:**
> Here is the deb compiled for Dapper:

[http://sitr.us/blog/files/libtunepimp2c2a_0.3.0-9.1ubuntu4_i386.deb](http://sitr.us/blog/files/libtunepimp2c2a_0.3.0-9.1ubuntu4_i386.deb)

This package will allow MusicBrainz to support MP3 files. And I have incremented the version number so the package will not be marked as upgradeable - until an actual newer version comes out that is.

---

