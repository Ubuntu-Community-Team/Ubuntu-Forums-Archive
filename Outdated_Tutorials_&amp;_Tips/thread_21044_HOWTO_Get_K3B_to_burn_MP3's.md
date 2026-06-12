---
title: "HOWTO: Get K3B to burn MP3's"
date: 2005-03-20
forum: Outdated Tutorials &amp; Tips
---

### Post by atf487 on 2005-03-20
This is annoying, and a sort of hack to get it to work. VERY annoying. And I'm a linux newb, so this may be unethical or something. 

But this is what i did. 

step 1:go to [http://rpm.pbone.net/index.php3/stat/4/idpl/1703970/com/k3b-mp3-0.11.19-0.lvn.1.3.i386.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/1703970/com/k3b-mp3-0.11.19-0.lvn.1.3.i386.rpm.html) and download the RPM there. 

step 2: sudo alien -i k3b-mp3-0.11.19-0.lvn.1.3.i386.rpm

step 3: sudo chmod 777 /usr/share/apps/k3b/plugins

step 4: download the mad decoder from [http://cvs-digest.org/index.php?transfer&file=kdeextragear-1/k3b/plugins/decoder/mp3/k3bmaddecoder.plugin,v&version=1.4&mimetype=](http://cvs-digest.org/index.php?transfer&file=kdeextragear-1/k3b/plugins/decoder/mp3/k3bmaddecoder.plugin,v&version=1.4&mimetype=)

step 5: cp *filename* /usr/share/apps/k3b/plugins, or just drag and drop it into that directory

Hope this helps anyone who had the same problem as me.

---

### Post by ACK!! on 2005-03-20
[QUOTE=atf487]This is annoying, and a sort of hack to get it to work. VERY annoying. And I'm a linux newb, so this may be unethical or something. 

But this is what i did. 

step 1:go to [http://rpm.pbone.net/index.php3/stat/4/idpl/1703970/com/k3b-mp3-0.11.19-0.lvn.1.3.i386.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/1703970/com/k3b-mp3-0.11.19-0.lvn.1.3.i386.rpm.html) and download the RPM there. 

step 2: sudo alien -i k3b-mp3-0.11.19-0.lvn.1.3.i386.rpm

step 3: sudo chmod 777 /usr/share/apps/k3b/plugins

step 4: download the mad decoder from [http://cvs-digest.org/index.php?transfer&file=kdeextragear-1/k3b/plugins/decoder/mp3/k3bmaddecoder.plugin,v&version=1.4&mimetype=](http://cvs-digest.org/index.php?transfer&file=kdeextragear-1/k3b/plugins/decoder/mp3/k3bmaddecoder.plugin,v&version=1.4&mimetype=)

step 5: cp *filename* /usr/share/apps/k3b/plugins, or just drag and drop it into that directory

Hope this helps anyone who had the same problem as me.[/QUOTE]


gnome-baker now support multi-session burns and all that.

deb [http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/i386](http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/i386) ./


A complete list of the available binary and source packages can be found at:

[http://www.ubuntulinux.org/wiki/GnomeBaker](http://www.ubuntulinux.org/wiki/GnomeBaker)

It worked on Hoary with only one issue.

Ok, it does not make the mp3 strict dependencies.  It makes them like recommended or something.  

So make sure you have all the libs to support converting the types of files you want to burn to audio.

What is the advantage of K3B over gnome baker?  If there is a real one I will try it out.

---

### Post by gnutux on 2005-03-20
but I think that K3B is the best burner out there. Plus, it's designed for KDE users, while your GNOME-baker is designed for GNOME users.

gnutux

---

### Post by IdoMcFly on 2005-03-20
[QUOTE=gnutux]but I think that K3B is the best burner out there. Plus, it's designed for KDE users, while your GNOME-baker is designed for GNOME users.

gnutux[/QUOTE]
 too bad it can't decode mp3 out of the box in hoary :/

---

### Post by ACK!! on 2005-03-20
[QUOTE=gnutux]but I think that K3B is the best burner out there. Plus, it's designed for KDE users, while your GNOME-baker is designed for GNOME users.

gnutux[/QUOTE]

Sorry did not realize you were Kubuntu or KDE user.  Hell in that case it makes perfect sense.  I hate even using Scribus because I am a sucker for consistent look and feel.  

Got to remember not everyone who uses Hoary uses Gnome.  

:)

---

### Post by bman08 on 2005-03-21
Just baked my first disk.  There are many ways k3b is more polished/complete than gnomebaker, but gnomebaker burns mp3s -> audio cds right out of the box.  Also it's  a gtk/gnome app.  Gnomebaker should be part of the default Ubuntu install for the next release!  It's the closest thing we've got to a functional burning package for gnome that I know of (excepting pricey nerolinux)

---

### Post by IdoMcFly on 2005-03-21
I had installed an Ubuntu Preview on my girlfriend box direct from CD 12th March and since, no update as she doesn't have an internet connection. I've just discovered she has the MAD decoder plugin installed, so it was remove recently :(

---

### Post by eric71 on 2005-03-26
I've been using Graveman for the past few weeks, and haven't tried gnomebaker.  Is ther any advantage of one program over the other?

---

### Post by raum13 on 2005-03-31
Hi 

the deb way to go is 

apt-get source k3b
apt-get build-dep k3b
apt-get install libmad0 libmad0-dev
cd k3b-0.11.23
dpkg-buildpackage -tc 
dpkg -i ../k3b_0.11.23-0ubuntu1_i386.deb ../k3blibs_0.11.23-0ubuntu1_i386.deb


with this you get a k3b which has 

/usr/share/apps/k3b/plugins/k3bmaddecoder.plugin
/usr/lib/kde3/libk3bmaddecoder.la
/usr/lib/kde3/libk3bmaddecoder.so

included. these are only included if during the compile the file mad.h is found. And as  libmad0-dev is not required to compile k3b it is not downloaded during the "apt-get build-dep k3b" without the extra install you get a mp3 free k3b. (politcal reasons or just forgotten ?) 

cu r13

---

### Post by uberlinux on 2005-04-04
If this dosent work right away after you do it, you may need to fully remove it and start over. It seems to work better if k3b dosent exist when you begin following these directions.  So use dpkg -r --force to get rid of the crappy k3b first.
P.S.  It will say that it will remove kubuntu-base, thats ok.

---

### Post by raum13 on 2005-04-04
hi 

on my system it worked without removing the k3b first. 


One other thing i found out. after you installed your own k3b you should set the k3b "on hold" with that it will not get upgraded automaticly, because that would overwrite your version with a newer version without mp3 support. 


cu r13

---

### Post by dejitarob on 2005-04-08
[QUOTE=raum13]the deb way to go is 

apt-get source k3b
apt-get build-dep k3b
apt-get install libmad0 libmad0-dev
cd k3b-0.11.23
dpkg-buildpackage -tc 
dpkg -i ../k3b_0.11.23-0ubuntu1_i386.deb ../k3blibs_0.11.23-0ubuntu1_i386.deb
[/QUOTE]Finally, worked great. Just had to change the last step to 'ubuntu3' instead of 1. Thanks a ton!

---

### Post by IdoMcFly on 2005-04-08
it seems that the mad decoder is back. you'll need to remove the k3b-mp3 if you manually installed it with alien.

---

### Post by muzza on 2005-04-08
Sorry if this sounds like a dumb question.  (Newbie here)  what version of Ubuntu will this (these) processes work on.  Isn't k3b a KDE program?  I have the basic install of Warty - will this work for me?

---

### Post by IdoMcFly on 2005-04-08
[QUOTE=muzza]Sorry if this sounds like a dumb question.  (Newbie here)  what version of Ubuntu will this (these) processes work on.  Isn't k3b a KDE program?  I have the basic install of Warty - will this work for me?[/QUOTE]
 it should, if you installed a kde application without jde installed, some qt and kde packages will be installed as well. but not the full kde.

try gnome backer if you don't want any kde lib

---

### Post by Equinox on 2005-04-08
After:
apt-get install libmad0 libmad0-dev

My normal k3b install seems happy to burn MP3s.  Under plugins it displays:
K3b MAD Decoder - Sebastian Trueg <> Version 2.2

And I'm able to drag and drop MP3s into the CD creation area.  I was only missing the libmad0-dev package.. Apparently that's what is required for it to detect the change.

---

### Post by atf487 on 2005-04-09
yeah, since k3b now burns mp3s again this isnt needed, and will just make things a little worse. 

if the mods could delete this, that would be great..

---

### Post by martinjh99 on 2005-04-13
How can I tell If I can create Audio CD's??

---

### Post by jubei on 2005-04-17
I'm running kubuntu 5.04 And I followed this howto but I still cant burn mp3s in K3b. What should I do?

---

### Post by gege71.hu on 2005-04-25
[QUOTE=Equinox]After:
apt-get install libmad0 libmad0-dev

My normal k3b install seems happy to burn MP3s.  Under plugins it displays:
K3b MAD Decoder - Sebastian Trueg <> Version 2.2

And I'm able to drag and drop MP3s into the CD creation area.  I was only missing the libmad0-dev package.. Apparently that's what is required for it to detect the change.[/QUOTE]

Can You burn Audio cd from one mp3-file (full album-in-1 with a cue-sheet) using "burn image" method? Nero has such feature but in k3b I got error message mp3 is not supported bla bla...(It can handle the cuesheet well and it seems OK, but after hitting "write" it returns me the mentioned error.
Do You think fixing the mp3 plugin would solve this issue?

---

### Post by spookylukey on 2005-05-07
This appears to have been fixed in k3b 0.11.23-0ubuntu3 - it depends on k3blibs, which depends on libmad0, and k3b has the MAD decoder plugin. See [https://bugzilla.ubuntu.com/show_bug.cgi?id=8052](https://bugzilla.ubuntu.com/show_bug.cgi?id=8052)

---

### Post by umberleigh on 2005-12-11
I was able to solve this in Breezy Badger simply by installing the package 'k3b-mp3'.

---

### Post by dr.drake on 2006-01-03
ofcourse it works with the k3b-mp3 package in Kynaptic/Synaptic.

maybe it's a good idea for atf487 to state this in his first post of this thread to prevent newbies (like my self) to try 3 pages of solutions in this thread to get to the easy solution? :rolleyes:

eric.

---

### Post by xinelo on 2006-06-18
Hi, 

Thanks everyone for all the feedback. Could somebody tell me what lines I should add to my sources.list in order to be able to install k3b-mp3 and/or kynaptic? 

I'm using kubuntu dapper. Adept won't install k3b-mp3... 

Thanks! xinelo

---

### Post by cosine7 on 2006-06-22
try libk3b2-mp3 at least thats what it is my synaptic

---

### Post by dr.drake on 2006-06-24
[QUOTE=xinelo]Hi, 

Thanks everyone for all the feedback. Could somebody tell me what lines I should add to my sources.list in order to be able to install k3b-mp3 and/or kynaptic? 

I'm using kubuntu dapper. Adept won't install k3b-mp3... 

Thanks! xinelo[/QUOTE]

try this site for your sources list:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

I sometimes prefer synaptic over adept, try installing that as well..

---

### Post by GarethMB on 2006-06-29
Thanks.

Installed libmad0-dev, k3b-dev and libk3b2-mp3 and it works sweet.=D>

---

### Post by starpause on 2006-07-16
yeah, under kubuntu 6.06 i got k3b to burn mp3 by searching Synaptic Package Manager for k3b and intstalling libk3b2-mp3

it would be nice if atf487 (who started this thread) or a mod would put these simple instructions on the first post :-#

---

### Post by xinelo on 2006-07-31
Thanks a lot! I could install libk3b2-mp3. 

Dr. Drake, thanks for the source list generator, I already knew that, but I prefer not to add unsupported repositories to my list. Maybe I'm too cautious? ;)

Cheers, xinelo

---

### Post by TheEHMan on 2006-12-06
> **raum13 said:**
> Hi 

the deb way to go is 

apt-get source k3b
apt-get build-dep k3b
apt-get install libmad0 libmad0-dev
cd k3b-0.11.23
dpkg-buildpackage -tc 
dpkg -i ../k3b_0.11.23-0ubuntu1_i386.deb ../k3blibs_0.11.23-0ubuntu1_i386.deb


with this you get a k3b which has 

/usr/share/apps/k3b/plugins/k3bmaddecoder.plugin
/usr/lib/kde3/libk3bmaddecoder.la
/usr/lib/kde3/libk3bmaddecoder.so

included. these are only included if during the compile the file mad.h is found. And as  libmad0-dev is not required to compile k3b it is not downloaded during the "apt-get build-dep k3b" without the extra install you get a mp3 free k3b. (politcal reasons or just forgotten ?) 

cu r13
I had the same problem burning MP3s to an audio disc.  Here's what I did:
I went to Synaptic, found K3B, right clicked on it and went to "MARK SUGGESTED FOR INSTALLATION" and selected the additional packages to install (libk3b2-mp3, k3b-i18n) and hit the apply button.  THat did the trick for me.

---

### Post by ifergus on 2007-03-02
MP3 decoding in K3B

K3B does not come with MP3 decoding support out of the box. Depending on your version of Ubuntu, you will need different packages.
Ubuntu 6.06

For full functionality, install the following packages: libk3b2-mp3 sox transcode vcdimager
Ubuntu 5.10

Installing the k3b-mp3 package will enable it.

---

### Post by stchman on 2007-03-22
> **gnutux said:**
> but I think that K3B is the best burner out there. Plus, it's designed for KDE users, while your GNOME-baker is designed for GNOME users.

gnutux

K3B can be used on Gnome as well as KDE.  Ubuntu has lots of KDE apps for Gnome.

---

### Post by axl55aa on 2007-03-29
**sudo apt-get install libk3b2-mp3 **
is the more recent approach.

Cheers!

Axel

---

### Post by StarscreamD on 2007-04-04
Thank you axel!

---

### Post by dr.drake on 2007-04-04
for all you future people who start reading at the end of a thread, read this one first:

[HOWTO: all K3B burning: mp3, data, iso, .bin/.cue, avi to dvd, etc.]("http://ubuntuforums.org/showthread.php?t=218165")

:)

---

### Post by llangwm on 2008-06-18
> **axl55aa said:**
> **sudo apt-get install libk3b2-mp3 **
is the more recent approach.

Cheers!

Axel

try **sudo apt-get install libk3b2-extracodecs** under hardy heron

---

### Post by BFris on 2008-06-28
> sudo apt-get install libk3b2-extracodecs under hardy heron 

Yes. libk3b2-extracodecs works a charm under Hardy Heron.

---

### Post by ganda99 on 2008-11-28
I can't seem to find anyone with a problem similar to mine. I'm trying to install the libk3b2-extracodecs in order to burn MP3 files to CD via Amarok and k3b, but Adept Manager wants to REMOVE k3b:

[SIZE="2"][B]sudo apt-get install libk3b2-extracodecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ghostscript-x dmz-cursor-theme kwin-style-crystal libisc32
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libk3b2
The following packages will be REMOVED:
  k3b libk3b3
The following NEW packages will be installed:
  libk3b2 libk3b2-extracodecs
0 upgraded, 2 newly installed, 2 to remove and 40 not upgraded.
Need to get 32.9kB/1157kB of archives.
After this operation, 2187kB disk space will be freed.
Do you want to continue [Y/n]? 
[/B][/SIZE]

Any help or advice would be splendid!  

Thanks. 
-- Gary

---

### Post by Jose Catre-Vandis on 2008-12-07
Hmmm, on Xubuntu 8.10, the installation of libk3b2-extracodecs and libk3b3-extracodecs, libmad0-dev still does not allow for mp3 burning to audio cd. what next? The mad decoder shows up in the plugins list, but still no decoding of mp3s?

EDIT:

Scratch that, its working now, a particular set of mp3s I was using needed re-encoding, most other mp3s work fine.

---

### Post by shinyblue on 2009-04-04
> **ganda99 said:**
> I'm trying to install the libk3b2-extracodecs in order to burn MP3 files to CD via Amarok and k3b, but Adept Manager wants to REMOVE k3b:


instead, on Hardy Herron, do:
$ sudo apt-get install libk3b3-extracodecs

hth.
rich

---

### Post by Big Show on 2009-12-21
newest command is **sudo apt-get install libk3b6-extracodecs**

---

### Post by vlats on 2009-12-22
how do i get rid of this problem ?!
OK it wont burn the CD even with K3B burner... here is the image of what it shows me ! [[IMG]http://img96.imageshack.us/img96/8494/problemcf.th.png[/IMG]]("http://img96.imageshack.us/i/problemcf.png/")

---

### Post by Zenxlow on 2011-01-19
Sooo. confused.. Im using Ubuntu 10 and cant get my laptop to burn mp3.. my goodness!!

---

