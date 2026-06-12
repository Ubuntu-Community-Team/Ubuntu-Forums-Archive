---
title: "compiling Avidemux"
date: 2005-10-18
forum: Packaging and Compiling Programs
---

### Post by rama on 2005-10-18
I am trying to compile avidemux. The tar I used is [this]("http://developer.berlios.de/project/showfiles.php?group_id=1402") and I got it from [this site]("http://avidemux.sourceforge.net/")

I tried to follow the instructions but could not get it to compile. I checked the forum and found [this post]("http://www.avidemux.org/phpBB2/viewtopic.php?t=1647"). So I run " sudo aptitude install automake1.9 autoconf" and tried again ... 
No luck. 

The error I get is while executing ./configure. The lsat lines of the output are:
```
checking for GNU gettext in libc... yes
checking for pkg-config... /usr/bin/pkg-config
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
************ Cannot identify gtk2 version ***************
configure: error: *** pkg-config installed incorrectly or gtk2-dev absent ! ***
```

I believe that I m missing something trivial ... but I m still a noob...
Any ideas?

---

### Post by ow50 on 2005-10-18
[QUOTE=rama]```
configure: error: *** pkg-config installed incorrectly or gtk2-dev absent ! ***
```[/QUOTE]
You're missing either pkg-config or libgtk2.0-dev.

---

### Post by rama on 2005-10-19
Ok. I ve installed gtk2-dev and now I get :
```
...
checking /usr/local/ is full of divx... "yes"
checking win32 host... no
checking spidermonkey engine ... using :  : as extra flags
checking jsapi.h usability... no
checking jsapi.h presence... no
checking for jsapi.h... no
configure: error: *** SPIDERMONKEY javascript engine not found !***
```

So I ve installed libsmjs1, libsmjs-dev, spidermonkey1, spidermonkey-bin and spidermonkey-dev. No luck.

---

### Post by ow50 on 2005-10-19
From avidemux website:
```
./configure --with-jsapi-include=xxxx [--with-newfaad for gentoo or breezy]
```
where xxx is the directory where jsapi.h is. Jsapi.h comes from spidermonkey. You NEED it.

Run
```
locate jsapi.h
```
to find out where that file is.

---

### Post by rama on 2005-10-19
I tryied that but I included jsapi.h in the path and ./configure failed with the same message](*,) 
Anyway now I get a new error message :```
************ LIBXML2 IS MANDATORY ***************
************ get it from http://www.xmlsoft.org*********
configure: error: *** No xml2 found***

```

I looked for a package with a name like that and downloaded libxml2-dev ... Success!
Now I m waiting for make to finish the job allthough it doesnt look good ... lots of warnings...

---

### Post by ow50 on 2005-10-19
[QUOTE=rama]Now I m waiting for make to finish the job allthough it doesnt look good ... lots of warnings...[/QUOTE]
Warnings don't matter, you'll always get lots of them.

---

### Post by rama on 2005-10-19
YES! my first app out of source! So now how can I add some more compatibility? Let me explain. It seems that I the configure script looked for a few other libs ass well which it did not find and did not consider crucial. So I guess that I ll be lacking support for xvid, vorbis and various other things that either I dont know how they relate to this app or I havent got a the slightest idea what they are. 

In order to include support for xvid and vorbis should I just look for a lib*-dev  package with a name that refers to xvid, vorbis or any other lib I m interested in? Is there a way to figure out which pakage is the right one?

---

### Post by ow50 on 2005-10-19
[QUOTE=rama]In order to include support for xvid and vorbis should I just look for a lib*-dev  package with a name that refers to xvid, vorbis or any other lib I m interested in? Is there a way to figure out which pakage is the right one?[/QUOTE]

In this case, easiest probably would be to check the dependencies of Marillat's avidemux package
[ftp://ftp.nerim.net/debian-marillat/pool/main/a/avidemux/avidemux_2.0.40-0.0.dsc](ftp://ftp.nerim.net/debian-marillat/pool/main/a/avidemux/avidemux_2.0.40-0.0.dsc)

---

### Post by rama on 2005-10-20
I recompiled the source after installing various libs mentioned at the address you pointed out and now I have support for xvid, flac, vorbis .... and some other stuff I dont even know what they are!

I have 3 questions (a bit more generic):
1. Apart from the space in my hard disk do the extra libxyz-dev packages do any harm? Slow down the system? Anything (I dont think so but just checking)
2. Is it "safe" to use this url :[ftp://ftp.nerim.net/debian-marillat/pool/main/](ftp://ftp.nerim.net/debian-marillat/pool/main/)
every time I want to find out the dependent packages of a pakcage I want to compile? Or is it possible that there would be a specific url for package a and another one for package b. 
3. As far as I can tell the url mentioned above is for debian. Is that ok?

---

### Post by ow50 on 2005-10-20
[QUOTE=rama]1. Apart from the space in my hard disk do the extra libxyz-dev packages do any harm? Slow down the system? Anything (I dont think so but just checking)[/QUOTE]
No harm.

[QUOTE=rama]2. Is it "safe" to use this url :[ftp://ftp.nerim.net/debian-marillat/pool/main/](ftp://ftp.nerim.net/debian-marillat/pool/main/)
every time I want to find out the dependent packages of a pakcage I want to compile? Or is it possible that there would be a specific url for package a and another one for package b.[/QUOTE]
Marillat is just a repository of some debian packages, mainly multimedia and codecs, so it's not a general place to check. Usually, if you need to compile from source, there's is no debian source available and hence no such list. However, if you do find a debian source, the build dependencies are listed in the corresponding .dsc file as well as the "Sources" file in the repository, which in the avidemux/Marillat case is
[ftp://ftp.nerim.net/debian-marillat/dists/sid/main/source/Sources](ftp://ftp.nerim.net/debian-marillat/dists/sid/main/source/Sources)

A couple good places where you might find debian sources are
[http://www1.apt-get.org/](http://www1.apt-get.org/)
[http://mentors.debian.net/](http://mentors.debian.net/)

[QUOTE=rama]3. As far as I can tell the url mentioned above is for debian. Is that ok?[/QUOTE]
For this case of checking package names, it's OK, because debian and ubuntu use the same names for packages. Debian repositories are not OK for installing binary packages, but are usually OK for building your own binary package from the source package.

---

### Post by rama on 2005-10-21
Thank you for answering all of my questions. It really helps to have someone pointing the way (while explaining a few things) when you get lost ... 
You wouldnt know of an e-book I could use as a general reference for Ubuntu would you? 
I found this : [http://linux-newbie.sunsite.dk/](http://linux-newbie.sunsite.dk/) but its a bit old and slightly focused on rpm distributions.

---

### Post by ow50 on 2005-10-21
The best Ubuntu link I know is the wiki
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

The kind of stuff you're probably looking for is still in the works
[https://wiki.ubuntu.com/DocteamProjects](https://wiki.ubuntu.com/DocteamProjects)

Debian has quite good documentation and most of it applies to Ubuntu as well
[http://www.debian.org/doc/](http://www.debian.org/doc/)

---

### Post by bored2k on 2005-10-22
I have made an avidemux 2.1_branch1 package using SVN. The avidemux creator is urging everyone to use the SVN instead of the old unstable package. I compiled this one for support with pretty much everything. It's a LOT better than the stable avidemux 2.0.42.

[http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html](http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html)

---

### Post by bored2k on 2005-11-01
[http://rapidshare.de/files/7068397/avidemux_2.1_svn-2_i386.deb.html](http://rapidshare.de/files/7068397/avidemux_2.1_svn-2_i386.deb.html)

New Avidemux 2.1.00 build from SVN .

---

### Post by CyberAngel on 2005-12-19
The following information taken from this link:
[http://openfacts.berlios.de/index-en.phtml?title=AvidemuxInstallCompileFromSVN](http://openfacts.berlios.de/index-en.phtml?title=AvidemuxInstallCompileFromSVN)

Works fine at first try without any issues on me in my breezy amd64 installation.

> 
 Ubuntu/Kubuntu (Breezy 5.10 & Hoary 5.04)

Compiling From SVN

If you have the Ubuntu universe enabled in your /etc/apt/sources.list file, you should be able to download all of the following files without any problems. Running this command line from the root console with either su or sudo will install many of the necessary dependencies for you to compile Avidemux with several extra features.

 apt-get install g++ gcc liba52-0.7.4 liba52-0.7.4-dev libfaac-dev libfaad2-dev libstdc++6 libgtk2.0-dev libglib2.0-dev pkg-config spidermonkey-dev liblame-dev libmad0-dev libvorbis-dev libxml2-dev libxvidcore4-dev 

Go to the place on your system when you want to download the source files for Avidemux. Then using a root console or the sudo command, do:

 svn co svn://svn.berlios.de/avidemux/branches/avidemux_2.1_branch/

Now the source files for the latest version of Avidemux from the SVN repositories on are your system, in a directory usually called avidemux_2.1_branch at your currect working directory. Move into that directory and create the configure script:

 cd avidemux_2.1_branch
 make -f Makefile.dist'

Next comes the ./configure command. In Ubuntu Breezy 5.10 (and probably Hoary 5.04), the version of automake is very old and needs to be updated. The version of automake that comes with Breezy is automake1.4. You will need to remove it. From a root console or via sudo:

 apt-get remove automake1.4 --purge

Next you need to install a newer version of automake, version 1.7 or high should work just fine. Newer versions are usually better. From a root console or via sudo:

 apt-get install automake1.x

In ubuntu, the spidermonkey scripting engine normally installs its development files at /usr/include/smjs/. If the ./configure command complains about missing spidermonkey and you are sure its installed, do a 'locate jsapi.h' from console and use that directory path here for the option --with-jsapi-include

Also, to include the extra audio support given by FAAD2, you need to add the extra argument of --with-newfaad to the ./configure command. If you are ready, do this from a root console or via sudo:

 ./configure --with-jsapi-include=/usr/include/smjs --with-newfaad

If this finishes without any errors, next comes the 'make' command. Ubuntu does not normally come with the 'make' program installed. To install it, from a root console or via sudo:

 apt-get install make

After it is installed, from a root console or via sudo:

 make

You now have a compiled executable file in avidemux_2.1_branch/avidemux called avidemux2. This is your new version of Avidemux. You may run it however you like or install it wherever you please. 


---

### Post by kevin_hill54 on 2005-12-28
Excuse my ignorance. I went to the Avidemux download site and downloaded avidemux_2.1_svn-2_i386.deb.

Is this file the file described in the instructions. I thought the .deb meant it was already compiled and ready to install directly. Do I still have to follow the instructions or should this be simpler to install?

Hope someone can help...

Regards

Kevin

---

### Post by CyberAngel on 2005-12-28
If you downloaded the avidemux_2.1_svn-2_i386.deb you can install it by using the command:
```
dpkg -i avidemux_2.1_svn-2_i386.deb
```

It is already compiled. The above info is if you want to compile it from source on your own.

---

### Post by kevin_hill54 on 2005-12-29
Thanks for the info.

Regards

Kevin

---

### Post by HellSpawn on 2006-01-11
Hi!!

     This thread it's been very usefull to me :D
     I'm haveing this message runiing make

> 
igor@ubuntu:~/Downloads/avidemux-2.1.0$ sudo make
cd . && /bin/sh /home/igor/Downloads/avidemux-2.1.0/admin/missing --run aclocal-1.8 -I m4
/home/igor/Downloads/avidemux-2.1.0/admin/missing: line 65: aclocal-1.8: command not found
WARNING: `aclocal-1.8' is needed, and you do not seem to have it handy on your
         system.  You might have modified some files without having the
         proper tools for further handling them.  Check the `README' file,
         it often tells you about the needed prerequirements for installing
         this package.  You may also peek at any GNU archive site, in case
         some other package would contain this missing `aclocal-1.8' program.
make: *** [aclocal.m4] Error 1


Thanks for any help!

---

### Post by HellSpawn on 2006-01-11
For get it... that's the message that you'll get if you don't have automake1.x ...
Thanks anyway ;)

---

### Post by DaveQB on 2006-02-02
[http://www.avidemux.org/pun/viewtopic.php?id=1647](http://www.avidemux.org/pun/viewtopic.php?id=1647)

The script in this thread worked for me.  I had trouble compiling due to SPIDERMONKEY not being installed (even though i did)
I think it was the configure options he used [--with-jsapi-include=/usr/include/smjs ]

---

### Post by LordMelkor on 2006-02-08
im very new to linux, and i know this may seem like an amateurish question so bear with me... i got the compiled svn package and i ran the dpkg command, and now im wondering.. where did avidemux install to? thanks for the help.

---

### Post by bored2k on 2006-02-08
[QUOTE=LordMelkor]im very new to linux, and i know this may seem like an amateurish question so bear with me... i got the compiled svn package and i ran the dpkg command, and now im wondering.. where did avidemux install to? thanks for the help.[/QUOTE]
From a terminal, run
```
avidemux2
```

Simply put, a menu was not installed.

---

### Post by Robban59 on 2006-02-11
Hi there, 

I must first specify that I'm running Hoary, so I hope this is not the problem : when I try to run avidemux2 I get this : 

avidemux2: error while loading shared libraries: libslang.so.2: cannot open shared object file: No such file or directory


Must be missing some library, but which one ? I have checked the libs stated in the compiling istructions, I seem to have all of them, but still..

Any help ?

---

### Post by DaveQB on 2006-02-14
This night help
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libslang&searchon=all&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libslang&searchon=all&subword=1&version=breezy&release=all)

---

### Post by freematanga on 2006-02-17
Great....its work...tkz

---

### Post by alewian on 2006-03-21
Thank you for your help. I have built a Debian package of Avidemux 2.1.2 for Breezy (it is attached to this post). To install, use:

**sudo dpkg -i avidemux-2.1.2-1_i386.deb**

I think it is useful to install some other packages so use also:

**sudo apt-get install debhelper libgtk2.0-dev liblame-dev libmad0-dev liba52-dev libvorbis-dev libmjpegtools-dev libxvidcore4-dev libdivxdecore0 libdivxencore0 libfreetype6-dev libxml2-dev libasound2-dev libsdl-dev libfaac-dev libfaad2-dev**

---

### Post by fsman on 2006-03-28
how do I get the deb from the rar.gz parts?

---

### Post by _MiniMe_ on 2006-03-29
[QUOTE=alewian] have built a Debian package of Avidemux 2.1.2 for Breezy (it is attached to this post). 

[/QUOTE]

Thanks a lot!

[QUOTE=alewian]
I think it is useful to install some other packages so use also:

**sudo apt-get install debhelper libgtk2.0-dev liblame-dev libmad0-dev liba52-dev libvorbis-dev libmjpegtools-dev libxvidcore4-dev libdivxdecore0 libdivxencore0 libfreetype6-dev libxml2-dev libasound2-dev libsdl-dev libfaac-dev libfaad2-dev**[/QUOTE]


 Does this mean that you didn't compile it with support for that libs or that you included all of them? I'd really like to know that before updating my 2.1.0...

---

