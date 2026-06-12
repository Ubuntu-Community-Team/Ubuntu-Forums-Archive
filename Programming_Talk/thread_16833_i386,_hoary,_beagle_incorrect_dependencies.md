---
title: "i386, hoary, beagle incorrect dependencies"
date: 2005-02-24
forum: Programming Talk
---

### Post by yatesco on 2005-02-24
Hi all,

I have searched and searched through the forums for a solution to this, but cannot find one.  I am *desperately* trying to get beagle installed.  I have followed the HoaryBeagle wiki, but autogen.sh gives the following error:

<code>
configure: error: Library requirements (gtk-sharp glade-sharp gecko-sharp = 0.6 gnome-sharp dbus-sharp >= 0.23.1 gconf-sharp gmime-sharp >= 2.1.11) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
</code>

Am I doing something wrong?  This is with beagle cvs 24/02/05.

Alternatively, could one of you nice people who have managed to build beagle produce a debs of all required files?

Many thanks,

Col

P.S.  I even downgraded my nice amd64 hoary to i386 so I can try beagle!

---

### Post by GilGalad on 2005-02-24
You need to install libgmime-cil & libgconf-cil. Hoary is not updgraded yet to dbus 0.23.1 but you can fool the configure script if you change in the file /usr/lib/pkgconfig/dbus-sharp.pc the version to 0.23.1.

---

### Post by yatesco on 2005-02-24
Excellent.

That worked a treat :)

Now when I start beagled --fg it complains about not being able to use the extended attributes.  I have modified /etc/fstab as requested (/ = ext3 BTW), and rebooted, but still no joy :(

Any ideas?

Col

---

### Post by GilGalad on 2005-02-24
Try removing $HOME/.beagle, run begle --fg --debug and post the exact error.

---

### Post by yatesco on 2005-02-24
running "beagled --fg --debug" after removing the .beagle gives the following:

<code>
INFO: Starting Beagle Daemon (version 0.0.7)
DEBUG: Command Line: /usr/local/lib/beagle/BeagleDaemon.exe --debug --fg
FATAL: Could not set extended attributes on a file in your home directory.  See [http://www.beaglewiki.org/index.php/Enable%20Extended%20Attributes](http://www.beaglewiki.org/index.php/Enable%20Extended%20Attributes) for more information.
</code>

this is on an ext3 filesystem (single /, no seperate /home), with the following options:

<code>
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro,user_xattr 0
      1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
</code>

on a:

<code>
Linux laptopcmy 2.6.10-4-386 #1 Tue Feb 22 23:15:15 UTC 2005 i686 GNU/Linux
</code>

kernel.

Any ideas?  Thanks BTW :)

---

### Post by GilGalad on 2005-02-25
What kernel are you using? Is inotify enabled? I think last kernel in Hoary has inotify disabled by default.

---

### Post by yatesco on 2005-02-25
Ah, that might explain it.

I am trying on 

<code>
Linux laptopcmy 2.6.10-3-386 #1 Tue Feb 15 21:18:07 UTC 2005 i686 GNU/Linux
</code>

Also tried on 2.6.4-10.  Same problem.

How can I tell if inotify is enabled without doing the whole kernel compilation thing?

Col

---

### Post by invitro on 2005-02-25
I had the exact same problem yesterday night, and got help on the #dashboard channel at GimpNet. I was told to change two lines in the source that hadn't been updated yet (since anoncvs is lagging), however it's possible that it's fixed in cvs so if you check out again it might work.

If not, then change the two lines of code described here:

[http://cvs.gnome.org/viewcvs/beagle/Util/ExtendedAttribute.cs?r1=1.11&r2=1.12](http://cvs.gnome.org/viewcvs/beagle/Util/ExtendedAttribute.cs?r1=1.11&r2=1.12)

and recompile. That did it for me!

/ Viktor

---

### Post by yatesco on 2005-02-25
Excellent.  Will try that now....

After installing libexif-dev....

Yep works like a treat.

Unfortunately I have just realised I am using 99% of the 7GB partition I dedicated to ubuntu!  Time to re-install :)

---

### Post by yatesco on 2005-02-25
So none of my messages within evolution (hoary) are being found :(

Also, if I type something in and select all, I thought it would contact google, but it doesn't seem to.  Any ideas on that?

Cheers,

Col

---

### Post by invitro on 2005-02-25
Nopes. I have the same problem. Also I don't get it to search the text of my .doc files.  Ah well, it's cool anyway and its beta so I don't mind.

---

### Post by tim1 on 2005-02-25
[QUOTE=yatesco]So none of my messages within evolution (hoary) are being found :(

Also, if I type something in and select all, I thought it would contact google, but it doesn't seem to.  Any ideas on that?

Cheers,

Col[/QUOTE]

evolution support seems to be broken currently, doens't work for me either. There will be evolution 2.2 soon (together with Gnome 2.10 i guess), which will be definitely supported by beagle, the current 1.1.x branch however isn't.

greets, tim

---

