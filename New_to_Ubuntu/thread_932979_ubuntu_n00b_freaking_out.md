---
title: "ubuntu n00b freaking out"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by bluthunder on 2008-09-29
I installed ubuntu because, i don`t think any OS (windows XP) should cost $250 and up. I just want to watch internet movies, using things like java, adobe flash player, and most importantly, I just want to play World of Warcraft on this PC. i such a noob, i cant figure anything out about this ubuntu. how do i get the nessesary applications to run WoW or play youtube videos, is there someone out there that has good insightful knowledge i can understand, that is n00b proof.

---

### Post by perlluver on 2008-09-29
> **bluthunder said:**
> I installed ubuntu because, i don`t think any OS (windows XP) should cost $250 and up. I just want to watch internet movies, using things like java, adobe flash player, and most importantly, I just want to play World of Warcraft on this PC. i such a noob, i cant figure anything out about this ubuntu. how do i get the nessesary applications to run WoW or play youtube videos, is there someone out there that has good insightful knowledge i can understand, that is n00b proof.

To get java and flash, install ubuntu-restricted-extras.  Open up Applications>Accessories>Terminal then ```
sudo apt-get install ubuntu-restricted-extras
``` as for World of Warcraft, it will run in Wine, for that sudo apt-get install wine, however since it is a windows game, it will be a bit slow, if it does run for you at all.

---

### Post by bluthunder on 2008-09-29
i tried that termanal command thingy, and this popped up, E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. whats that mean

---

### Post by perlluver on 2008-09-29
> **bluthunder said:**
> i tried that termanal command thingy, and this popped up, E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. whats that mean

Ok, run this in a terminal first: ```
sudo dpkg --configure -a
``` then run that other code.

---

### Post by jerome1232 on 2008-09-29
edit: I type slow on a laptop :)

to install adobe flash you can open a terminal and install the flashplugin-nonfree package (Applications->Accessories->Terminal) then type
```
sudo apt-get install flashplugin-nonfree
```

or the gui way would be to open synaptic (System->Administration->Synaptic Package Manger) Click in the upper righthand pane and start typing flashplugin-nonfree, right click the package and mark it for installation then apply your changes.


Since WoW is an applicatin written for Windows you will need this nifty application called wine, which you can install with both of the methods that I gave above, that particular game happens to work great with a few changes outlined on this page [http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)


As far as java goes I have never needed it enough to try and install sun's java on my 64 bit system (can be a royal pain I understand) but if you are running a 32 bit system I believe you just have to install the sun-java6-bin package, could be wrong there.

---

### Post by northern lights on 2008-09-29
The meta package *ubuntu-restricted-extras* contains *flashplugin-nonfree*, yet I'd also suggest replacing the default webvideo plugin with *mozilla-mplayer* -```
sudo apt-get autoremove totem-mozilla && sudo apt-get update && sudo apt-get install mozilla-mplayer
```

---

### Post by WWSmith36 on 2008-09-29
First enable all the repositories go to menu System-> Administrator-> Software Sources

On the Ubuntu Software tab make sure you select main universe restricted and multiverse

You will need to open a terminal from the menu Applications-> Accessories-> Terminal and type in some commands

Update source list

```
sudo apt-get update
sudo apt-get upgrade
```

Get codecs to play most multimedia you own

```
sudo apt-get install ubuntu-restricted-extras
```

To install java

```
sudo aptitude install sun-java6-bin sun-java6-jre sun-java6-plugin
```

To install flashplayer

```
sudo apt-get install flashplugin-nonfree
```

To run WoW you will need to install Wine

```
sudo apt-get install wine
```

Here is a link to Wine website
[http://www.winehq.org/](http://www.winehq.org/)

Hope this helps

---

### Post by bluthunder on 2008-09-29
trevor@trevorpiece:~$ sudo dpkg --configure -a
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Setting up ssl-cert (1.0.14-0ubuntu2.1) ...

Setting up libxslt1.1 (1.1.22-1ubuntu1.2) ...

Setting up pidgin-data (1:2.4.1-1ubuntu2.1) ...

Setting up linux-restricted-modules-common (2.6.24.13-19.45) ...

Setting up python-gtkhtml2 (2.19.1-0ubuntu7.1) ...

Setting up hal (0.5.11~rc2-1ubuntu8.2) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting Hardware abstraction layer hald                                     /usr/sbin/hald already running.
                                                                         [ OK ]

Setting up linux-restricted-modules-2.6.24-19-generic (2.6.24.13-19.45) ...

Setting up libgksu2-0 (2.0.5-1ubuntu5.2) ...

Setting up libxml2-utils (2.6.31.dfsg-2ubuntu1.2) ...
Setting up libtiff4 (3.8.2-7ubuntu3.1) ...

Setting up samba-common (3.0.28a-1ubuntu4.5) ...

Setting up deskbar-applet (2.22.3.1-0ubuntu1) ...

Setting up smbclient (3.0.28a-1ubuntu4.5) ...
Setting up yelp (2.22.1-0ubuntu2.8.04.3) ...

Setting up libpoppler2 (0.6.4-1ubuntu3.1) ...

Setting up compiz-fusion-plugins-main (0.7.4-0ubuntu6) ...

Setting up rdesktop (1.5.0-3+cvs20071006ubuntu0.1) ...
Setting up python-gobject (2.14.2-0ubuntu1) ...

Setting up xsltproc (1.1.22-1ubuntu1.2) ...
Setting up poppler-utils (0.6.4-1ubuntu3.1) ...
Setting up xserver-xorg-video-intel (2:2.2.1-1ubuntu13.6) ...

Setting up libgtksourceview2.0-common (2.2.2-0ubuntu1) ...
Setting up linux-headers-2.6.24-19 (2.6.24-19.41) ...
Setting up python-libxml2 (2.6.31.dfsg-2ubuntu1.2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up nautilus-sendto (0.13.2-0ubuntu2) ...

Setting up update-notifier-common (0.70.9) ...
Setting up libpurple0 (1:2.4.1-1ubuntu2.1) ...

Setting up update-notifier (0.70.9) ...

Setting up libpoppler-glib2 (0.6.4-1ubuntu3.1) ...

Setting up libgtksourceview2.0-0 (2.2.2-0ubuntu1) ...

Setting up pidgin (1:2.4.1-1ubuntu2.1) ...

Setting up linux-headers-2.6.24-19-generic (2.6.24-19.41) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place



does this look right? is this a good thing?

---

### Post by perlluver on 2008-09-29
Yes that means it fixed the update errors, now you can run the other code, and install the extras.

---

### Post by WWSmith36 on 2008-09-29
I would fully update and reboot your system

But to fully check and upgrade your system using terminal using command line,
open a Terminal from the menu Applications->Accessories->Terminal and type:

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove
```

then please reboot your system, type

```
sudo reboot
```

---

### Post by jerome1232 on 2008-09-29
Yup that's fine, that's what a normal install/upgrade process looks like. You might want to reboot because it looks like you had a kernel update.

---

### Post by perlluver on 2008-09-29
> **jerome1232 said:**
> Yup that's fine, that's what a normal install/upgrade process looks like. You might want to reboot because it looks like you had a kernel update.

+1, I wasn't paying attention.

---

### Post by bluthunder on 2008-09-29
so, im supposed to reboot my system, then run the original code as stated in reply #2?

---

### Post by jerome1232 on 2008-09-29
> **bluthunder said:**
> so, im supposed to reboot my system, then run the original code as stated in reply #2?

Yes, that meta package will install all the packages I mentioned and some extra goodies to boot.

edit: except for wine, you will still need to install wine after  you run the command from post #2
```
sudo apt-get install wine
```

---

### Post by bluthunder on 2008-09-29
ok, im going to try rebooting, now, i'll reply in a few

---

### Post by bluthunder on 2008-09-29
ok, done rebooting, not what?
oh, and what am i trying to do in the first place?

---

### Post by perlluver on 2008-09-29
> **bluthunder said:**
> ok, done rebooting, not what?
oh, and what am i trying to do in the first place?

You are installing the restricted extras for Java and Flash. ;)

---

### Post by bluthunder on 2008-09-29
ok, yes or no?

trevor@trevorpiece:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for trevor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse java-common
  liba52-0.7.4 libavcodec1d libavformat1d libavutil1d libcdaudio1 libdc1394-13
  libdvdread3 libfaac0 libfaad0 libfreebob0 libgmyth0 libgsm1 libid3tag0
  libiptcdata0 libjack0 liblame0 libmad0 libmjpegtools0c2a libmms0 libmpcdec3
  libmpeg2-4 libmysqlclient15off libopenspc0 libpostproc1d libquicktime1
  libsidplay1 libsoundtouch1c2 libwildmidi0 libx264-57 libxvidcore4
  msttcorefonts mysql-common odbcinst1debian1 sun-java6-bin sun-java6-jre
  sun-java6-plugin unixodbc unrar
Suggested packages:
  konqueror-nsplugins libflashsupport ttf-xfree86-nonfree xfs equivs debhelper
  fakeroot libdvdcss2 jackd sidplay-base xsidplay binfmt-support
  sun-java6-fonts ttf-wqy-zenhei libct1 libmyodbc odbc-postgresql
Recommended packages:
  w32codecs freepats gsfonts-x11
The following NEW packages will be installed:
  cabextract flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse java-common
  liba52-0.7.4 libavcodec1d libavformat1d libavutil1d libcdaudio1 libdc1394-13
  libdvdread3 libfaac0 libfaad0 libfreebob0 libgmyth0 libgsm1 libid3tag0
  libiptcdata0 libjack0 liblame0 libmad0 libmjpegtools0c2a libmms0 libmpcdec3
  libmpeg2-4 libmysqlclient15off libopenspc0 libpostproc1d libquicktime1
  libsidplay1 libsoundtouch1c2 libwildmidi0 libx264-57 libxvidcore4
  msttcorefonts mysql-common odbcinst1debian1 sun-java6-bin sun-java6-jre
  sun-java6-plugin ubuntu-restricted-extras unixodbc unrar
0 upgraded, 48 newly installed, 0 to remove and 0 not upgraded.
Need to get 42.0MB of archives.
After this operation, 120MB of additional disk space will be used.
Do you want to continue [Y/n]? sudo apt-get install ubuntu-restricted-extras

---

### Post by perlluver on 2008-09-29
Yes, that will install them.  And choose y.

---

### Post by bluthunder on 2008-09-29
im going to go with yes

---

### Post by bluthunder on 2008-09-29
ok, m typing "y" and nothing is happening.... how should me saying yes look like?

---

### Post by perlluver on 2008-09-29
> **bluthunder said:**
> ok, m typing "y" and nothing is happening.... how should me saying yes look like?

Type y, then hit enter.  That should do it.

---

### Post by bluthunder on 2008-09-29
Need to get 42.0MB of archives.
After this operation, 120MB of additional disk space will be used.
Do you want to continue [Y/n]? sudo apt-get install ubuntu-restricted-extrasy 
Abort.
trevor@trevorpiece:~$ y
bash: y: command not found
trevor@trevorpiece:~$ y
bash: y: command not found
trevor@trevorpiece:~$

---

### Post by perlluver on 2008-09-29
> **bluthunder said:**
> Need to get 42.0MB of archives.
After this operation, 120MB of additional disk space will be used.
Do you want to continue [Y/n]? sudo apt-get install ubuntu-restricted-extrasy 
Abort.
trevor@trevorpiece:~$ y
bash: y: command not found
trevor@trevorpiece:~$ y
bash: y: command not found
trevor@trevorpiece:~$

Ok, ```
sudo apt-get install ubuntu-restricted-extras
``` then press y, then press enter.

---

### Post by northern lights on 2008-09-29
> **bluthunder said:**
> Need to get 42.0MB of archives.
After this operation, 120MB of additional disk space will be used.
Do you want to continue [Y/n]? [COLOR="Red"]sudo apt-get install ubuntu-restricted-extras[/COLOR]y 
Abort.
trevor@trevorpiece:~$ y
bash: y: command not found
trevor@trevorpiece:~$ y
bash: y: command not found
trevor@trevorpiece:~$
The red marked is redundant and does not belong there.
'y' only, then Enter.

---

### Post by bluthunder on 2008-09-29
ok, it worked...Package configuration


 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring msttcorefonts &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; msttcorefonts uses defoma                                                 &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use   &#9474; 
 &#9474; the fonts provided by this package under the X Window System, you must    &#9474; 
 &#9474; configure it to use defoma fonts.                                         &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; The easiest way to do so is to use the x-ttcidfont-conf package. For      &#9474; 
 &#9474; more information, install the x-ttcidfont-conf package and consult its    &#9474; 
 &#9474; documentation under /usr/share/doc/x-ttcidfont-conf.                      &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; For uses of msttcorefonts not related to the X Window System (e.g.        &#9474; 
 &#9474; printing) this is not required.                                           &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                  <Ok>                                     &#9474; 
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                               

hit ok?  ( thank god for copy/paste! :))

---

### Post by perlluver on 2008-09-29
Yes press Ok.  Or enter.

---

### Post by bluthunder on 2008-09-29
Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-bin &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618; 
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618; 
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618; 
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618; 
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618; 
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618; 
 &#9474;     form, any other machine readable materials including, but not         &#9618; 
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                           ok, unfortunaltly, i think it froze or somthing, im hitting enter and i get no response, so i'm going to close the termanil and restart the process...

---

### Post by perlluver on 2008-09-29
No press the tab key and then enter.

---

### Post by bluthunder on 2008-09-29
****, too late.... sorry :( i plead the noob admenment...hang on, i'll get back to there...

---

### Post by xxernestoxx on 2008-09-29
> **bluthunder said:**
> I installed ubuntu because, i don`t think any OS (windows XP) should cost $250 and up. I just want to watch internet movies, using things like java, adobe flash player, and most importantly, I just want to play World of Warcraft on this PC. i such a noob, i cant figure anything out about this ubuntu. how do i get the nessesary applications to run WoW or play youtube videos, is there someone out there that has good insightful knowledge i can understand, that is n00b proof.

as for the wow thing...check out the link below its a great alternative to commercial software for playing windows games. This guide shows you how to install wow using wine and the necessary tweaks for it to run a lot better.
I can not take credit for it though, thank fsckin.com for it.
[http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/](http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/)

enjoy
-Ernest

---

### Post by bluthunder on 2008-09-29
now i get this:  is this bad?trevor@trevorpiece:~$ sudo apt-get install ubuntu-restricted-extras
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
trevor@trevorpiece:~$ sudo apt-get install ubuntu-restricted-extras

---

### Post by bluthunder on 2008-09-29
btw, ty for taking the time to help me out....i really appreciate it

---

### Post by perlluver on 2008-09-29
> **bluthunder said:**
> now i get this:  is this bad?trevor@trevorpiece:~$ sudo apt-get install ubuntu-restricted-extras
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
trevor@trevorpiece:~$ sudo apt-get install ubuntu-restricted-extras

Yeah do you have synaptic open?  Or any other program manager?

---

### Post by bluthunder on 2008-09-29
how do i tell?

---

### Post by perlluver on 2008-09-29
> **bluthunder said:**
> how do i tell?

Look at the bottom, are there any other things open down there, namely synaptic or Add/Remove Programs?

---

### Post by perlluver on 2008-09-29
If they aren't open, lets try another reboot, and we will do something else.

---

### Post by bluthunder on 2008-09-29
[IMG]http://i67.photobucket.com/albums/h303/kantou_rei/Screenshot.png[/IMG]

you tell me?

---

### Post by bluthunder on 2008-09-29
maby if i restart my pc?

---

### Post by perlluver on 2008-09-29
No you don't, have any open, reboot, and then we will try something else.

---

### Post by bluthunder on 2008-09-29
ok, i will, thanks agian, tonight you just might save me from going back to windows! ugh!

---

### Post by perlluver on 2008-09-29
> **bluthunder said:**
> ok, i will, thanks agian, tonight you just might save me from going back to windows! ugh!

You are welcome, although I will be going to sleep soon, it being 2:30 in the morning in all.

---

### Post by bluthunder on 2008-09-29
trevor@trevorpiece:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for trevor: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
trevor@trevorpiece:~$ sudo dpkg --configure -a
Setting up java-common (0.28ubuntu3) ...
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4310: parser error : Extra content at the end of the document
rePCI/ISA/PCMCIA">
^

Setting up odbcinst1debian1 (2.2.11-16build1) ...

Setting up unixodbc (2.2.11-16build1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
trevor@trevorpiece:~$ 
now what?

---

### Post by bluthunder on 2008-09-29
if you have to go to bed, i understand, i'm not going to worry about flash for the rest of tonight. i'm justgoing to try and install wine, and get WoW installed...could you give me the link for wine?

---

### Post by bluthunder on 2008-09-29
trevor@trevorpiece:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-06-0ubuntu1) but it is not going to be installed
  wine: Depends: binfmt-support (>= 1.1.2) but it is not going to be installed
        Depends: libaudio2 but it is not going to be installed
        Depends: winbind but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
trevor@trevorpiece:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-06-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
trevor@trevorpiece:~$ 'apt-get -f install
> 
> 
> 

is there somehting i need to install first?

---

### Post by perlluver on 2008-09-29
Ok, first run sudo apt-get install -f :: It appears to be set up correctly from the above, try a flash web site.  Now for that link for Wine: sudo apt-get install wine, or via synpatic look for wine

---

### Post by ibuclaw on 2008-09-29
[EDIT]
Fixed URLs :)

[ubuntu-restricted-extras]("apt://ubuntu-restricted-extras")

[WINE]("apt://wine")

[Adobe Flash Plugin]("apt://flashplugin-nonfree")

If you want a more comprehensive streaming experience.
UbuntuForums has a very good thread here -> [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

This has various things such as Firefox Video/Audio streaming, DVD Play/Rip, Codec Conversion, etc.

Also, don't forget to enable the Medibuntu Repository!
A highly recommended source of software.

Regards
Iain

---

### Post by bluthunder on 2008-09-29
yeah, this is appearing:
This game cannot be played using your current settings. Please, try the following:

    * Check to make sure that java is enabled in your browser. (learn more)
    * If you do not have java installed you may download it here.
    * To learn more about java support for browsers, visit our help pages.

---

### Post by bluthunder on 2008-09-29
ok, well it's nearly 1 am where i am, and i need to get some sleep for school. i'll log back on tomarrow to try and make it so i can watch flash movies, and so i can install Wine, so i can finaly play World of Warcraft...
ty for the help tonight, i almost got somewhere, but i screwed it up! :(
tlak to you all later...

---

### Post by aysiu on 2008-09-29
You know, people are trying to help you by giving you a whole bunch of instructions.

I think you're best off learning how to do it yourself.

This tutorial will give you (with screenshots) the basics on software installation:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

