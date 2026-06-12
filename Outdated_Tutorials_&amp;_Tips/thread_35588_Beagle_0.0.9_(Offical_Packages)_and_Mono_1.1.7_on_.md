---
title: "Beagle 0.0.9 (Offical Packages) and Mono 1.1.7 on Hoary &amp; Breezy"
date: 2005-05-19
forum: Outdated Tutorials &amp; Tips
---

### Post by sebgate20 on 2005-05-19
Hey All

With the new BeagleWiki up, I've streamed lined the install and thanks to the guys at Ubuntu Backports, we can now use the offical Breezy Beagle and Mono packages on Hoary!

I've tested the Hoary instructions on serveral machines but Breezy isn't tested so feedback is welcome!

You can find the HOWTO at [http://www.beaglewiki.org/Ubuntu_Installation](http://www.beaglewiki.org/Ubuntu_Installation)

Feedback wanted! PLEASE PLEASE PLEASE replace ANY other Mono/Beagle installation with this one!

Cheers

Seb
Founder and Systems Administrator
Evolution Colt - [www.evolutioncolt.com](www.evolutioncolt.com)

---

### Post by ericsp on 2005-05-24
I tried. Installation works flawless. Beagled runs ok, and best works.... as long as I don't search for words that are present in files. Please check this report and see if you can help us out!

[http://bugzilla.gnome.org/show_bug.cgi?id=304803](http://bugzilla.gnome.org/show_bug.cgi?id=304803)

Eric

---

### Post by sebgate20 on 2005-05-24
I found that installing libgnomeui-dev package solves the problem. I will update the HOWTO now!

Thanks

Seb

---

### Post by supernaut on 2005-05-24
[QUOTE=sebgate20]Hey All

With the new BeagleWiki up, I've streamed lined the install and thanks to the guys at Ubuntu Backports, we can now use the offical Breezy Beagle and Mono packages on Hoary!

I've tested the Hoary instructions on serveral machines but Breezy isn't tested so feedback is welcome!

You can find the HOWTO at [http://www.beaglewiki.org/Ubuntu_Installation](http://www.beaglewiki.org/Ubuntu_Installation)

Feedback wanted! PLEASE PLEASE PLEASE replace ANY other Mono/Beagle installation with this one!

Cheers

Seb
Founder and Systems Administrator
Evolution Colt - [www.evolutioncolt.com](www.evolutioncolt.com)[/QUOTE]
 You should point out that it's i386 only. Ubuntu is on THREE architectures, not one.

---

### Post by Grue on 2005-05-24
[QUOTE=supernaut]You should point out that it's i386 only. Ubuntu is on THREE architectures, not one.[/QUOTE]
 Thanks for pointing that out. I was ready to pull my hair out, when I couldn't find any of the mono packages in backports (I'm running the AMD64 distro).

---

### Post by robertobech on 2005-05-26
Is it true that Beagle won't work on Reiser partitions? If that's the case, then I'm in trouble...

"Note that for Reiser3, extended attributes are not enabled in the reiserfs kernel module by default. Be sure to enable the kernel config option (REISERFS_FS_XATTR) before building the kernel/module.

Also note that neither Reiser4 nor NFS support extended attributes, so Beagle presently will not work on these filesystems. "
[http://www.beaglewiki.org/Enabling_Extended_Attributes](http://www.beaglewiki.org/Enabling_Extended_Attributes)

Hmmm... how do I know if this thing is supported on my PC?

---

### Post by traherom on 2005-07-05
Worked for me after I enabled extended attributes! Without them, the first time I started Beagle I got no reported error, but searches failed. The second time I started it, it reported an error and told me where the log file was.

Thanks!

---

### Post by ACK!! on 2005-07-05
Worked for me except for searching on files.  Yes, I activated extended attributes:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults,user_xattr        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

And I did the remount.  But still nothing.  

Will try again after a reboot since I am on a laptop.

Thanks.  Very cool.

---

### Post by hellraiser_rob on 2005-07-06
yeah i'm having the same issue as ack, can't get all the files indexed, only chat logs and evolution emails!

---

### Post by scadieux on 2005-07-06
[QUOTE=hellraiser_rob]yeah i'm having the same issue as ack, can't get all the files indexed, only chat logs and evolution emails![/QUOTE]

Same here.

In fact, I managed to get everything up and running, but can't get any results from any query, even though I know there must be some results...

---

### Post by varunus on 2005-07-06
Run beagled with debug enabled.  Do you guys see an sqlite error?  If so, you need to install libsqlite0-dev.  I had to do this before I got file searching to work.

---

### Post by hellraiser_rob on 2005-07-06
i just did as you suggested now the daemon won't start, and throws an error

will post you the exact error as soon as i'm able, (VNC'ing in from work  :razz: )

---

### Post by jadugarr on 2005-07-06
This may be a dumb question but I'm confused about enabling the extended attributes?  It says that the default kernel in hoary doesn't enable the attributes for ext2 and reiser3.  Since I'm using reiser3, doesn't that mean that i need to recompile my kernel with that option to enable the attribute or is their a simpler solution?

---

### Post by hellraiser_rob on 2005-07-06
error from starting beagled in console

rob@rimmer:~$ beagled
rob@rimmer:~$
Unhandled Exception: System.ArgumentException: An invalid argument was specified.
in [0x0009b] (at /home/jdong/dev/mono-1.1.7/mcs/class/corlib/System.IO/Path.cs:154) System.IO.Path:GetDirectoryName (string)
in <0x000b2> Beagle.Daemon.FileSystemQueryable.FileSystemModel:AddRoot (string)
in <0x000b3> Beagle.Daemon.FileSystemQueryable.FileSystemModel:LoadConf (Beagle.Util.Conf/Section)
in <0x0003d> (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_Conf/Section (Beagle.Util.Conf/Section)
in <0x000bb> Beagle.Util.Conf:NotifySubscribers (Beagle.Util.Conf/Section)
in <0x0005c> Beagle.Util.Conf:Load (bool)
in <0x00009> Beagle.Util.Conf:Load ()
in <0x0017d> Beagle.Daemon.BeagleDaemon:StartupProcess ()
in <0x00048> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x0002b> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0xb7f77a02
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x0052e> Beagle.Daemon.BeagleDaemon:Main (string[])



Error from best

The query for something failed with error:
System.Net.Sockets.SocketException: Connection refused in [0x00063] System.Net.Sockets.Socket:Connect (System.Net.EndPoint remote_end) in <0x00021> Beagle.Util.UnixClient:Connect (Mono.Posix.UnixEndPoint remoteEndPoint) in <0x00036> Beagle.Util.UnixClient:Connect (System.String path) in <0x00020> Beagle.Util.UnixClient:.ctor (System.String path) in <0x00028> Beagle.Client:SendRequest (Beagle.RequestMessage request) in <0x00010> Beagle.Client:SendAsync (Beagle.RequestMessage request) in <0x000c7> Beagle.RequestMessage:SendAsync () in <0x00142> Best.BestWindow:Search (System.String searchString)

this is my error guys :(

---

### Post by ACK!! on 2005-07-06
[QUOTE=hellraiser_rob]yeah i'm having the same issue as ack, can't get all the files indexed, only chat logs and evolution emails![/QUOTE]

Man, it works now on reboot but - wow! - is the indexing slow.  

Yes, I left the 

export BEAGLE_EXERCISE_THE_DOG=1

option up in a terminal and the beagled running in the same term after.  

I did that and left it running for a loooong time (2 hours straight) and still there are some un-indexed mp3 files that do not show up on searches.  

I ran it in the foreground and noticed the thing went into loops occasionally where it checked the same files over and over and over and ... ad nausem ... you get the picture.  

But wait, I know its alpha.

But wait, do not flame because I still think its the bomb.  

Will Ubuntu developers consider activating the inotify option for the kernel on the next release?  Or consider including this great tool?

I mean despite some pains and a few headaches it is truly amazing finally a tool that matches some of the power of grep and find with both speed and a slick interface.

Wow.  Very frickin' cool.

---

### Post by abmcr on 2005-07-07
In the source list file i have this repository for backports:

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
When i try to apt-get install i get this message: it is necessary i change the repository.? Thank you for any assistance. Ciao

xxxxx@ubuntu:~$ sudo apt-get install libdbus-cil libevolution-cil libgconf-cil libgecko-cil libglade-cil libgmime-cil libgnome-cil libgnome2.0-cil libgnomevfs2-dev libgsf-cil libgtk-cil libgnomeui-dev beagle libsqlite0-dev
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
I seguenti pacchetti verranno inoltre installati:
  dbus-1-dev dbus-glib-1-dev indent libart-2.0-dev libatk1.0-dev
  libaudiofile-dev libbonobo2-dev libbonoboui2-dev libesd0-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgconf2-dev libgconf2.0-cil
  libgcrypt11-dev libglade2-dev libglade2.0-cil libglib2.0-cil
  libgnome-keyring-dev libgnome2-dev libgnomecanvas2-dev libgnutls11-dev
  libgpg-error-dev libgtk2.0-cil libgtk2.0-dev libice-dev libidl-dev
  libjpeg62-dev libopencdk8-dev liborbit2-dev libpango1.0-dev libsm-dev
  libtasn1-2-dev libx11-dev libxft-dev libxi-dev libxml2-dev libxrender-dev
Pacchetti suggeriti:
  glade-2 glade-gnome-2 libgnome2-doc libgnomecanvas2-doc libgnomeui-doc
  libgnutls-doc gnutls-bin libgtk2.0-doc libpango1.0-doc sqlite-doc
Pacchetti raccomandati:
  orbit2
I seguenti pacchetti NUOVI (NEW) saranno installati:
  beagle dbus-1-dev dbus-glib-1-dev indent libart-2.0-dev libatk1.0-dev
  libaudiofile-dev libbonobo2-dev libbonoboui2-dev libdbus-cil libesd0-dev
  libevolution-cil libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libgconf2-dev libgconf2.0-cil libgcrypt11-dev libgecko-cil libglade2-dev
  libglade2.0-cil libglib2.0-cil libgmime-cil libgnome-keyring-dev
  libgnome2-dev libgnome2.0-cil libgnomecanvas2-dev libgnomeui-dev
  libgnomevfs2-dev libgnutls11-dev libgpg-error-dev libgsf-cil libgtk2.0-cil
  libgtk2.0-dev libice-dev libidl-dev libjpeg62-dev libopencdk8-dev
  liborbit2-dev libpango1.0-dev libsm-dev libsqlite0-dev libtasn1-2-dev
  libx11-dev libxft-dev libxi-dev libxml2-dev libxrender-dev
0 aggiornati, 48 installati, 0 da rimuovere e 0 non aggiornati.
È necessario prendere 833kB/17,7MB di archivi.
Dopo l'estrazione, verranno occupati 73,0MB di spazio su disco.
Continuare [S/n]? s
ATTENZIONE: i seguenti pacchetti non possono essere autenticati!
  beagle libglib2.0-cil libgconf2.0-cil libgtk2.0-cil libglade2.0-cil
  libgnome2.0-cil
Install these packages without verification [y/N]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main indent 2.2.9-6 [102kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libgnomecanvas2-dev 2.10.0-0ubuntu1 [119kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libgcrypt11-dev 1.2.0-11 [231kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libjpeg62-dev 6b-9 [181kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libsqlite0-dev 2.8.15-3 [200kB]
Scaricato 833kB in 14s (56,0kB/s)
Impossibile ottenere [http://us.archive.ubuntu.com/ubuntu/pool/main/i/indent/indent_2.2.9-6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/indent/indent_2.2.9-6_i386.deb)  Somma MD5 non corrispondente
Impossibile ottenere [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecanvas/libgnomecanvas2-dev_2.10.0-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecanvas/libgnomecanvas2-dev_2.10.0-0ubuntu1_i386.deb)  Somma MD5 non corrispondente
Impossibile ottenere [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11-dev_1.2.0-11_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11-dev_1.2.0-11_i386.deb)  Somma MD5 non corrispondente
Impossibile ottenere [http://us.archive.ubuntu.com/ubuntu/pool/main/libj/libjpeg6b/libjpeg62-dev_6b-9_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libj/libjpeg6b/libjpeg62-dev_6b-9_i386.deb)  Somma MD5 non corrispondente
Impossibile ottenere [http://us.archive.ubuntu.com/ubuntu/pool/main/s/sqlite/libsqlite0-dev_2.8.15-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/sqlite/libsqlite0-dev_2.8.15-3_i386.deb)  Somma MD5 non corrispondente
E: Impossibile prendere alcuni archivi, forse è meglio eseguire apt-get update o provare l'opzione --fix-missing

---

