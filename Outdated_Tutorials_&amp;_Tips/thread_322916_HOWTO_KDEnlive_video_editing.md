---
title: "HOWTO: KDEnlive video editing"
date: 2006-12-21
forum: Outdated Tutorials &amp; Tips
---

### Post by uuwatti on 2006-12-21
EDIT: KDEnlive now has Ubuntu builds so it's now a lot easier to install it. Here's how
**Installing official Ubuntu .deb**

```
sudo aptitude install k3b dvdauthor dvgrab libxine1 libsdl-image1.2 libsdl-image1.2-dev  libsdl1.2-dev libsamplerate0 libogg0 libvorbis0a libdv4 libjack0.100.0 sox libxml2 ladspa-sdk libquicktime0 libtheora0
wget http://download128.mediafire.com/ottzmktnmlyg/ammoqj12nzn/kdenlive_mlt_ubuntu.zip
unzip kdenlive_mlt_ubuntu.zip -d kdenlive
cd kdenlive
sudo dpkg -i mlt_cvs20070101_i386.deb 
sudo dpkg -i mlt++_cvs20070101_i386.deb
sudo dpkg -i kdenlive_svn20070101_i386.deb

```**That's it! Enjoy!**

[U]
Or if you want the latest development version:[/U]
[B]Installing cutting edge SVN version:
[/B]
I don't take any credit for this I copied it from french ubuntudocs. I just edited and updated it a bit. Props to the guy who made this.

The original instructions are here -->[http://doc.ubuntu-fr.org/applications/kdenlive](http://doc.ubuntu-fr.org/applications/kdenlive) I hope I managed to get all the dependencies right.

_Only GNOME users should do this part:_
```
sudo aptitude install kdelibs4c2a kdelibs-data
```
_This is for all:_
```
sudo aptitude install kdelibs4-dev libqt4-dev unsermake libsdl-image1.2 libsdl-image1.2-dev libsdl1.2-dev libsamplerate0 libsamplerate0-dev libogg0 libogg-dev libvorbis0a libvorbis-dev libdv4 libdv4-dev libjack0.100.0-0 libjack0.100.0-dev sox sox-dev libxml2 libxml2-dev ladspa-sdk-dev libquicktime0 libquicktime-dev libtheora0 libtheora-dev ladspa-sdk swh-plugins libavformat0d libavformat-dev kdesvn build-essential libgtk2-dev libmad0 libmad0-dev autoconf automake1.9 dvgrab cvs subversion k3b dvdauthor
```
```
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg
./configure --enable-gpl --enable-shared --enable-vorbis --enable-libogg --enable-pp
make
sudo make install
cd ..
```
```
cvs -d:pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/mlt login
```
Hit <enter> for password
```
cvs -z3 -d:pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/mlt co mlt
cd mlt
./configure --enable-gpl --enable-shared --enable-theora --enable-vorbis --enable-libogg --enable-pp --enable-shared-pp --enable-motion-est --avformat-svn --prefix=/usr
make
sudo make install
cd ..
```
```
cvs -d:pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/mlt login
```
Hit <enter> for password
```
cvs -z3 -d :pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/mlt co mlt++
cd mlt++
./configure --prefix=/usr
make
sudo make install
cd ..
```
Then start kdesvn from the menu OR type to terminal: 
```
kdesvn
```
Go to --> Subversion --> General --> Checkout a repository
and add
```
https://svn.sourceforge.net/svnroot/kdenlive/trunk/kdenlive
```
as URL and your home folder as target. Hit ok.
```
cd kdenlive
make -f Makefile.cvs
./configure --prefix=/usr
make
sudo make install
```
Enjoy!

P.S. there is something at the end of the original instructions about creating softlinks, but at least I didn't need them. (I don't speak a word of french, so I don't understand why should I do the linking.)

---

### Post by bodhi.zazen on 2006-12-24
Nice How-to

This thread has been added to the UDSF wiki.

[KDEnlive](http://doc.gwos.org/index.php/KDEnlive)

FYI here is a link to the English KDEnlive Handbook;

[KDEnlive Handbook (English Edition)](http://www.uchian.pwp.blueyonder.co.uk/kdenlive/documentation/handbook/en/index.html)

---

### Post by amonsul on 2006-12-26
Hi!

When i insert this "./configure --prefix=/usr"
I got this error message....

> checking for rpath... yes
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
amonsul@amonsul:~/kdenlive$ 



Whats the problem?

---

### Post by uuwatti on 2006-12-27
My bad.. just do (if you are using ubuntu instead of kubuntu):
```
sudo aptitude install kdelibs4c2a kdelibs-data
```
and then configure again.

---

### Post by vgrisham on 2007-01-05
After entering the first line of the second set of code, I get the following error: "bash: svn: command not found"

Any hints? I'm running Kubuntu Dapper.

Thanks,
Vaughn

---

### Post by stalefries on 2007-01-05
vgrisham:
```
sudo aptitude install subversion
```Synaptic is your friend :).

---

### Post by lime4x4 on 2007-01-05
i get this error on ubuntu-edgy

john@john-edgy:~/kdenlive$ kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!

john@john-edgy:~/kdenlive$

---

### Post by uuwatti on 2007-01-06
Now they have Ubuntu builds!
[http://kdenlive.sourceforge.net/wiki/index.php?title=Faq_Install&section=6#Ubuntu]("http://kdenlive.sourceforge.net/wiki/index.php?title=Faq_Install&section=6#Ubuntu")
try that one first

---

### Post by gotgenes on 2007-01-15
On Ubuntu Edgy, I've done both the described SVN build (install in /usr/local) and an install from the .debs and I wind up with the same error when launching KDENLIVE.
```
Will not save configuration.
Configuration file "/home/chris/.kde/share/config/kdenliverc" not writable.
Configuration file "/home/chris/.kde/share/config/kdeglobals" not writable.
Please contact your system administrator.

```
At the console, this appears:
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/tmp-feathers: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
trying to create local folder /home/chris/.kde/share: Permission denied
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8219a88 ): KAccel object already contains an action name "edit_paste"
kdenlive: Mlt inited
kdenlive: +++++++++++  Generating scenelist start...  ++++++++++++++++++
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: ****************  INIT DOCUMENT VIEW ***************
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
kdenlive: Mlt inited
kdenlive: ****************  INIT DOCUMENT VIEW 1***************
kdenlive:  +  ++ + ++ ++ PREPARE VID THUMB
kdenlive:  +  ++ + ++ ++ PREPARE AUDIO THUMB

```

Then when I go to open a file, I get several warning boxes
```
Could not find mime type
application/octet-stream
```
```
No mime types installed
```
```
Malformed URL
file:///home/chris/
```
If I try to navigate to another directory, I get a Malformed URL error. No files appear. Any clues would I be getting these permission errors? Is there a missing dependency not listed in the howto?

---

### Post by uuwatti on 2007-01-15
look like for some reason the .kde folder has the wrong owner (it should be you)
try this:
```
sudo chmod 777 -R ./.kde
```

---

### Post by gotgenes on 2007-01-15
That did it! I dunno why I didn't think of that, except that sometimes I skip over the most obvious answers. ](*,) Actually, instead of using chmod, I used
```
chown -R username:username ~/.kde
```

For whatever reason, root was the owner of my .kde files.

Thanks very much for this HOWTO. This **really** helped! :-D

---

### Post by uuwatti on 2007-01-15
It seems some people have difficulties configuring mlt and mlt++. To fix that you need to edit the configure files so that the line which says ```
#!/bin/sh
``` change it to say:```
#!/bin/bash
```
Do that on both configure files.

---

### Post by amoore on 2007-01-16
Will Kdenlive be added to the repos for Ubuntu 7.04? I would realy like to give it a try!!!!

---

### Post by uuwatti on 2007-01-16
Why not try the official(?) Ubuntu build? It is very simple to install and the download is only 5mb.

---

### Post by 4ebees on 2007-01-17
Hi Vaughn,

Did you manage to get this to install on Dapper. I'm quite curious myself about Kdenlive.

Regards,

Patrick




> **vgrisham said:**
> After entering the first line of the second set of code, I get the following error: "bash: svn: command not found"

Any hints? I'm running Kubuntu Dapper.

Thanks,
Vaughn

---

### Post by amoore on 2007-01-20
> **uuwatti said:**
> Why not try the official(?) Ubuntu build? It is very simple to install and the download is only 5mb.

Actually, thats how I installed it. Kdenlive shows more potential that any other editing app Ive seen for Ubuntu. =D>  I would just like to see a version in the repos for 7.04:KS

---

### Post by P_Badger on 2007-01-28
Kdenlive is probably, (imo), the best looking DV editor for linux, free or otherwise. It doesn't crash nearly as easily as Cinerella, though that's not to say it doesn't crash at really odd times and fairly often, ya know?

Lets hope the programmers keep at it and one day release a bug free version.

---

### Post by sk8dork on 2007-02-03
does anyone else have issues configuring the project properties? like changing the resolution? every time i try to change anything in the configure project window, after hitting apply and ok, i go back in to see that everything is back to where it was before. i also can't add or remove templates or anything...

---

### Post by uuwatti on 2007-02-05
Probably a bug or an unimplemented feature. NTSC and PAL templates work for me at least. People, you have to remember that this is version 0.4, not everything works properly yet.

---

### Post by flammenwurfer on 2007-02-06
Does anyone know if there is a 64 bit version?

---

### Post by uuwatti on 2007-02-07
[Building instructions for AMD64 under debian/Kubuntu Edgy]("http://kdenlive.sourceforge.net/wiki/index.php?title=Amd64")

---

### Post by id000 on 2007-05-10
i compilled under amd64 according to previous post, but:
igor@igor-laptop:~$ kdenlive
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdenlive: Mlt inited
kdenlive: Creating new document
kdenlive: deleting contents...
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive: **************  SCREEN SET SCENELIST
KCrash: Application 'kdenlive' crashing...

  What could it be?
                                 Thanks

---

### Post by cotcot on 2007-05-15
I got the same but without Qapplication errors with a 32 bit install on a 64 bit machine.
What is the device that fails to open ? 
> ~$ kdenlive
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8219710 ): KAccel object already contains an action name "edit_paste"
kdenlive: Mlt inited
kdenlive: +++++++++++  Generating scenelist start...  ++++++++++++++++++
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive: Mlt inited
kdenlive: ****************  INIT DOCUMENT VIEW 1***************
kdenlive:  +  ++ + ++ ++ PREPARE VID THUMB
kdenlive:  +  ++ + ++ ++ PREPARE AUDIO THUMB

---

### Post by mohnkern on 2007-05-17
The Wget isn't working properly:


 613 2007-05-17 16:46 kdenlive_mlt_ubuntu.zip

 wget [http://download128.mediafire.com/ottzmktnmlyg/ammoqj12nzn/kdenlive_mlt_ubuntu.zip](http://download128.mediafire.com/ottzmktnmlyg/ammoqj12nzn/kdenlive_mlt_ubuntu.zip)
--16:46:03--  [http://download128.mediafire.com/ottzmktnmlyg/ammoqj12nzn/kdenlive_mlt_ubuntu.zip](http://download128.mediafire.com/ottzmktnmlyg/ammoqj12nzn/kdenlive_mlt_ubuntu.zip)
           => `kdenlive_mlt_ubuntu.zip'
Resolving download128.mediafire.com... 38.114.196.147
Connecting to download128.mediafire.com|38.114.196.147|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified

    [ <=>                                 ] 613           --.--K/s             



it gives a redirect error

 more kdenlive_mlt_ubuntu.zip
<html><head><title>Loading...</title><script  language="JavaScript">
<!--
function changecolor() {
 document.vlinkColor='BLUE';
document.linkColor='BLUE';
document.fgColor='#000000';
return;
}
//-->
</SCRIPT>
</head><body bgcolor=#FFFFFF text=#FFFFFF link=#FFFFFF vlink=#FFFFFF onload="set
Timeout('changecolor()',5000);"><div name='loading id='loading'><B>The browser y
ou are using does not support redirects...</b><BR><BR>

Please click <a href='http://www.mediafire.com/?www.mediafire.com'>here</a> to c
ontinue.
<meta http-equiv="refresh" content="0;url=http://ammoqj12nzn/?ammoqj12nzn"></div
></body></html>

---

### Post by uuwatti on 2007-05-21
use Treviño's repositories for installing via apt.
```
sudo gedit /etc/apt/sources.list 
```
add this:```
deb http://download.tuxfamily.org/3v1deb feisty 3v1n0
```
then:
```
sudo apt-get update
gpg --keyserver subkeys.pgp.net --recv 2D6CFB44DD800CD9 
gpg --export --armor 2D6CFB44DD800CD9 | sudo apt-key add -
sudo apt-get install kdenlive
```

---

### Post by JeevesBond on 2007-05-22
> **uuwatti said:**
> P.S. there is something at the end of the original instructions about creating softlinks, but at least I didn't need them. (I don't speak a word of french, so I don't understand why should I do the linking.)

Think I know what this is. I recently wrote a howto on [Installing the latest FFMPEG on Ubuntu Feisty](http://www.apaddedcell.com/installing-the-latest-ffmpeg-on-ubuntu-feisty-fawn-7-04), note the last section 'Technical Backflip'. Seems when you compile FFMPEG it installs some libraries into a spot where Ubuntu wont look for them.

You can use the French instructions or my work-around, if you try running FFMPEG without doing one or the other though I *think* it will crash. Try running it and tell me the result, would like to know if I'm right or barking up the wrong tree. :)

---

### Post by Killtown on 2007-06-29
Here is [one current way]("http://ubuntuforums.org/showpost.php?p=2780808&postcount=9") of installing KDEnlive.  Install these 3 files in this order:

mlt:  [http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/mlt_0.2.1-1+3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/mlt_0.2.1-1+3v1ubuntu0_i386.deb)

mlt++:  [http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/mlt++_0.2.1-1_i386.deb](http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/mlt++_0.2.1-1_i386.deb)

KDEnlive:  [http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/kdenlive_0.5~svn20070603+3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/kdenlive_0.5~svn20070603+3v1ubuntu0_i386.deb)

Done.

Files found here:  [http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/index.html](http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/index.html)

---

### Post by krsnendu on 2008-05-28
I am trying to comple Kdenlive with AC3 audio support on Hardy.
I get this error when building... Can anyone help?

gcc -shared -Wl,-soname,libavutil.so.49  -rdynamic -export-dynamic -Wl,--warn-common -Wl,--as-needed -Wl,-rpath-link,"/home/krsnendu/KdenliveBuild/ffmpeg"/libavcodec -Wl,-rpath-link,"/home/krsnendu/KdenliveBuild/ffmpeg"/libavformat -Wl,-rpath-link,"/home/krsnendu/KdenliveBuild/ffmpeg"/libavutil -Wl,-Bsymbolic -o libavutil/libavutil.so.49 libavutil/adler32.o libavutil/aes.o libavutil/base64.o libavutil/crc.o libavutil/des.o libavutil/fifo.o libavutil/intfloat_readwrite.o libavutil/lls.o libavutil/log.o libavutil/lzo.o libavutil/mathematics.o libavutil/md5.o libavutil/mem.o libavutil/random.o libavutil/rational.o libavutil/rc4.o libavutil/sha1.o libavutil/string.o libavutil/tree.o libavutil/  -lz -lbz2 -pthread -lm -lfaad -lmp3lame -lm -ltheora -logg   -ldl -ldl 
/usr/bin/ld: libavutil/: No such file: File format not recognized
collect2: ld returned 1 exit status
make: *** [libavutil/libavutil.so.49] Error 1
make: *** Waiting for unfinished jobs....

---

### Post by RegressLess on 2008-06-08
I can't find a good link for KNEnlive.

---

### Post by 4ebees on 2008-06-08
> **RegressLess said:**
> I can't find a good link for KNEnlive.

Maaaaaaaaaaaaaate!

Lemme see:

[www.google.com.au](www.google.com.au)

kdenlive 

search

[http://www.kdenlive.org/](http://www.kdenlive.org/)

Now, have some popcorn

:popcorn:

---

### Post by niceguy123 on 2009-03-28
I've got no sound in kdnlive, any ideas why not?

---

### Post by ledzepjes on 2009-05-22
I got to this post from an external link, and when I tried to search for "HOWTO: KDEnlive video editing" to find it again I get around 250 threads that aren't this one? Is there a trick for searching the forums for threads using certain titles? I don't wanna have to use google everytime.

****edited****
ok, it's been 4 weeks since I first had problems with searching the forums, I tried again with better results and this time searching for "KDEnlive video editing" comes up with only 3 results. Must have been a glitch with VBulletin...nevermind.

---

