---
title: "HOWTO: VLC for DVD playback"
date: 2005-01-28
forum: Outdated Tutorials &amp; Tips
---

### Post by jsgotangco on 2005-01-28
VLC is a highly portable multimedia player for various audio and video formats as well as DVDs, VCDs and various streaming protocols.

Use VLC if the other known applications like Totem, Xine, Ogle doesn't work for you. On my configuration, only VLC worked perfectly with DVD playback (with menus).

You will need to add extra repositories to be able to add some of the applications/codecs to be used in this guide. [You can refer to the Unofficial Ubuntu 4.10 Starter Guide to do this.](http://www.ubuntuguide.org/#extrarepositories) 

This HOWTO is tested only on Ubuntu 4.10 (Warty Warthog)

Once you have added the repositories, open up Terminal and encode the following.

```
user@ubuntu:~ $ sudo apt-get install libdvdcss2
user@ubuntu:~ $ sudo apt-get install vlc
```

You may also want to install other multimedia codecs (win32, DivX, XviD) so that VLC will be able to play those as well.

```
user@ubuntu:~ $ sudo apt-get install w32codecs
user@ubuntu:~ $ sudo apt-get install gstreamer0.8-plugins
user@ubuntu:~ $ sudo apt-get install libxvidcore4
user@ubuntu:~ $ sudo apt-get install libdivxdecore0
```

Once VLC and the codecs are installed, you can start vlc on terminal:

```
user@ubuntu:~ $ vlc
```

Before loading a DVD from VLC, you need to make a link from /media/cdrom0 to /dev/dvd (VLC assumes this is the path of your dvd).

```
user@ubuntu:~ $ sudo ln -s /media/cdrom0 /dev/dvd
```

You may also want to make this link permanent (taken from ubuntuguide.org):

```
 $ sudo ln -sf /dev/cdrom /dev/dvd
$ sudo cp /etc/udev/udev.rules /etc/udev/udev.rules_backup
$ sudo gedit /etc/udev/udev.rules
```

Edit this line:

```
 BUS="ide", KERNEL="hd[a-z]", PROGRAM="/etc/udev/cdsymlinks.sh %k", SYMLINK="%c{1} %c{2}"
```

to this:

```
 BUS="ide", KERNEL="hd[a-z]", SYMLINK="cdrom dvd"
```

And save.

Now you can play DVDs in VLC by right clicking on the application then choose **OPEN** -> **OPEN DISC**. On the Disc Type tab, choose DVD (menus). Device name should be /dev/dvd, the press OK to start playing the DVD. If you didn't make the link on the previous code, the DVD will not load.

If you noticed, VLC didn't make an entry in Nautilus. You can manually add a link to the launcher in Gnome by doing:

```
user@ubuntu:~ $ nautilus Applications:///Multimedia
```

This will open up the Multimedia window. **Select File** -> **Create Launcher**. The Create Launcher window will appear and fill up the fields with the following:

Name: VLC (You can also put VideoLAN Client)
Comment: Cross platform media player and streaming server
Comman: vlc
Icon: /usr/share/pixmaps -> scroll down and you'll see vlc.png and click OK.

Now you have created a launcher for VLC. Enjoy watching your DVDs!

---

### Post by ctt1wbw on 2005-01-28
Speaking of vlc, I don't have audio using this program.  I also don't have audio using MPlayer either.  I've got audio using totem and others.  Anything I should do or change?  I've tried everything I can think of.

---

### Post by ctt1wbw on 2005-01-28
Wait a minute, now I don't have audio anywhere...  I'm very very very very very confused with audio settings in Ubuntu.  I can hook up a home theater but I can NOT figure this out...

---

### Post by jsgotangco on 2005-01-28
[QUOTE=ctt1wbw]Wait a minute, now I don't have audio anywhere...  I'm very very very very very confused with audio settings in Ubuntu.  I can hook up a home theater but I can NOT figure this out...[/QUOTE]
 maybe the volume controls just got messed up to mute. sometimes my laptop does that. when choosing menus on some DVDs with VLC, the app just closes but it only happens rarely.

---

### Post by ctt1wbw on 2005-01-28
No, I'm not getting audio anywhere.  I just updated the kernel to the 686 version.  Think that had anything to do with it?  Maybe ALSA?

---

### Post by ctt1wbw on 2005-01-28
Yep, that was it.  Now I have audio, but still not in MPlayer.

---

### Post by Caesar on 2005-02-06
I can't install css libs.... any help?

After "sudo apt-get install libdvdcss2" (yes, apt-get is updated and universe sources are added to apt-get list) it can't find the package. Any idea?

---

### Post by ctt1wbw on 2005-02-06
do a search on [www.google.com/linux](www.google.com/linux)

---

### Post by celloandy on 2005-02-06
[QUOTE=Caesar]I can't install css libs.... any help?

After "sudo apt-get install libdvdcss2" (yes, apt-get is updated and universe sources are added to apt-get list) it can't find the package. Any idea?[/QUOTE]

You need to add the Debian Marillat repositories to get libdvdcss2.  That's where any of the legally questionable packages, like w32codecs, live.  See [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) for details.

Andrew

---

### Post by QzarBaron on 2005-02-06
I installed it and made the symbolic link from my dvd drive (cdrom1) to /dev/dvd... I am getting these errors whenever I try to play a dvd:

[00000230] v4l input error: cannot open device (no such file or directory)
[00000230] v4l input error: cannot open audio device (no such file or directory)
[00000230] main input error: no suitable access module for '/://dvd:///dev/dvd@:1'

what could be wrong?

---

### Post by Caesar on 2005-02-07
[QUOTE=celloandy]You need to add the Debian Marillat repositories to get libdvdcss2.  That's where any of the legally questionable packages, like w32codecs, live.  See [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) for details.

Andrew[/QUOTE]

Thanks for answering Andrew.

I've added Debian Marillat repositories but i can't get them to work... take a look:
```

ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-powerpc/Packages.gz: Unable to fetch file, server said ‘/debian-marillat/dists/stable/main/binary-powerpc/Packages.gz: No such file or directory  ’
ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-powerpc/Packages.gz: Unable to fetch file, server said ‘/debian-marillat/dists/unstable/main/binary-powerpc/Packages.gz: No such file or directory  ’
ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-powerpc/Packages.gz: Unable to fetch file, server said ‘/debian-marillat/dists/testing/main/binary-powerpc/Packages.gz: No such file or directory  ’
```

Maybe is a PPC-packages related issue?

---

### Post by QzarBaron on 2005-02-15
Anyone have a solution to my problem?

---

### Post by WW on 2005-02-17
Caesar: I believe Marillat's repository is i386 only.

---

### Post by Hermes on 2005-02-18
[QUOTE=QzarBaron]Anyone have a solution to my problem?[/QUOTE]
 I get the same error as Qzar...anyone know whats up?

---

### Post by jsgotangco on 2005-02-21
[QUOTE=QzarBaron]I installed it and made the symbolic link from my dvd drive (cdrom1) to /dev/dvd... I am getting these errors whenever I try to play a dvd:

[00000230] v4l input error: cannot open device (no such file or directory)
[00000230] v4l input error: cannot open audio device (no such file or directory)
[00000230] main input error: no suitable access module for '/://dvd:///dev/dvd@:1'

what could be wrong?[/QUOTE]
 that's strange those error messages would only come out if there's no such thing as /dev/dvd but you did say you made a symbolic link, so it should be there...

---

### Post by HerrSieben on 2005-02-23
[QUOTE=QzarBaron]I installed it and made the symbolic link from my dvd drive (cdrom1) to /dev/dvd... I am getting these errors whenever I try to play a dvd:

[00000230] v4l input error: cannot open device (no such file or directory)
[00000230] v4l input error: cannot open audio device (no such file or directory)
[00000230] main input error: no suitable access module for '/://dvd:///dev/dvd@:1'

what could be wrong?[/QUOTE]
 Thanks for your knowledge.

I think i have found a little mistake in your HowTo:

> ```

user@ubuntu:~ $ sudo apt-get w32codecs 
user@ubuntu:~ $sudo apt-get gstreamer0.8-plugins
```


should be

```

user@ubuntu:~ $ sudo apt-get **install** w32codecs 
user@ubuntu:~ $sudo apt-get **install** gstreamer0.8-plugins
```

or?

---

### Post by jsgotangco on 2005-02-23
[QUOTE=HerrSieben]Thanks for your knowledge.

I think i have found a little mistake in your HowTo:



should be

```

user@ubuntu:~ $ sudo apt-get **install** w32codecs 
user@ubuntu:~ $sudo apt-get **install** gstreamer0.8-plugins
```

or?[/QUOTE]
 ahh yess I didn't notice that at all...I made the appropriate changes..many thanks.

---

### Post by jsgotangco on 2005-02-23
Just an addendum to the original post, you might also want to have DivX and XviD support (decoder only), so just install them via apt or synaptic the following:
[B]
libxvidcore4[/B] - High quality ISO MPEG4 codec library
**libdivxdecore0** - DivX MPEG4 decoder library

Cheers!

---

### Post by jsgotangco on 2005-03-02
HOWTO is updated.

---

### Post by gameman12 on 2007-03-15
this how to didn't work for me, just a friendly FYI :)

---

