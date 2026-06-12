---
title: "Wildcards not working?"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by 2CV67 on 2012-01-26
After upgrading (well - fresh install) to 11.10 - it seems the usual wildcards are not working in terminal...

Example:
```
chris@Acer-desk:~$ ls ./Scripts
hello_world.sh  PhotoRename.sh      show_desktop.sh
PhotoNamer.sh   PhotoRenameTest.sh  Test.sh
chris@Acer-desk:~$ locate PhotoRename
/home/chris/Scripts/PhotoRename.sh
chris@Acer-desk:~$ locate PhotoRename*
chris@Acer-desk:~$ locate Ph*Rename
chris@Acer-desk:~$ locate Photo?ename
chris@Acer-desk:~$ locate Photo*ame*
chris@Acer-desk:~$ locate PhotoRename
/home/chris/Scripts/PhotoRename.sh
chris@Acer-desk:~$ 

```

Any clues gratefully accepted!

Thanks!

---

### Post by ajgreeny on 2012-01-26
I've never tried that with [COLOR=#000000]locate[/COLOR] before, but reading your post I have just done so, and it seems that the [COLOR=#000000]locate[/COLOR] command will not take all wildcards and at the moment I am attempting to sort out the pattern that is acceptable to it.

As an example. here is a copy of an attempt on my system to search for "panasonic" using different uses of the *.  I can't figure it out yet, but there must be a systematic pattern that sets the rules.
```
user@Lucid:~$ [COLOR=#000000]locate[/COLOR] panasonic*
user@Lucid:~$ [COLOR=#000000]locate[/COLOR] *panasonic
/usr/share/doc/libgphoto2-2/camlibs/README.panasonic
/usr/src/linux-headers-2.6.32-38-generic/include/config/panasonic
/usr/src/linux-headers-2.6.35-31-generic/include/config/panasonic
/usr/src/linux-headers-2.6.35-32-generic/include/config/panasonic

user@Lucid:~$ [COLOR=#000000]locate[/COLOR] *panasonic/

user@Lucid:~$ locate panasonic/
/usr/src/linux-headers-2.6.32-38-generic/include/config/panasonic/laptop.h
/usr/src/linux-headers-2.6.35-31-generic/include/config/panasonic/laptop.h
/usr/src/linux-headers-2.6.35-32-generic/include/config/panasonic/laptop.h

user@Lucid:~$ [COLOR=#000000]locate[/COLOR] *panasonic*
/etc/acpi/events/panasonic-lockbtn
/home/user/Videos/panasonic_lumix_dmc_fz38_01.mts
/lib/modules/2.6.32-38-generic/kernel/drivers/platform/x86/panasonic-laptop.ko
/lib/modules/2.6.35-31-generic/kernel/drivers/platform/x86/panasonic-laptop.ko
/lib/modules/2.6.35-32-generic/kernel/drivers/platform/x86/panasonic-laptop.ko
/usr/lib/libgphoto2/2.4.8/panasonic_coolshot.a
/usr/lib/libgphoto2/2.4.8/panasonic_coolshot.la
/usr/lib/libgphoto2/2.4.8/panasonic_coolshot.so
/usr/lib/libgphoto2/2.4.8/panasonic_dc1000.a
/usr/lib/libgphoto2/2.4.8/panasonic_dc1000.la
/usr/lib/libgphoto2/2.4.8/panasonic_dc1000.so
/usr/lib/libgphoto2/2.4.8/panasonic_dc1580.a
/usr/lib/libgphoto2/2.4.8/panasonic_dc1580.la
/usr/lib/libgphoto2/2.4.8/panasonic_dc1580.so
/usr/lib/libgphoto2/2.4.8/panasonic_l859.a
/usr/lib/libgphoto2/2.4.8/panasonic_l859.la
/usr/lib/libgphoto2/2.4.8/panasonic_l859.so
/usr/share/doc/libgphoto2-2/camlibs/README.panasonic
/usr/share/doc/libgphoto2-2/camlibs/README.panasonic-coolshot
/usr/share/doc/libgphoto2-2/camlibs/README.panasonic-l859
/usr/share/media-player-info/panasonic_sv-mp31v.mpi
/usr/share/mime/image/x-panasonic-raw.xml
/usr/src/linux-headers-2.6.32-38-generic/include/config/panasonic
/usr/src/linux-headers-2.6.32-38-generic/include/config/panasonic/laptop.h
/usr/src/linux-headers-2.6.35-31-generic/include/config/panasonic
/usr/src/linux-headers-2.6.35-31-generic/include/config/panasonic/laptop.h
/usr/src/linux-headers-2.6.35-32-generic/include/config/panasonic
/usr/src/linux-headers-2.6.35-32-generic/include/config/panasonic/laptop.h

user@Lucid:~$ [COLOR=#000000]locate[/COLOR] *anasonic*
/etc/acpi/events/panasonic-lockbtn
/home/user/Videos/panasonic_lumix_dmc_fz38_01.mts
/lib/modules/2.6.32-38-generic/kernel/drivers/platform/x86/panasonic-laptop.ko
/lib/modules/2.6.35-31-generic/kernel/drivers/platform/x86/panasonic-laptop.ko
/lib/modules/2.6.35-32-generic/kernel/drivers/platform/x86/panasonic-laptop.ko
/usr/lib/libgphoto2/2.4.8/panasonic_coolshot.a
/usr/lib/libgphoto2/2.4.8/panasonic_coolshot.la
/usr/lib/libgphoto2/2.4.8/panasonic_coolshot.so
/usr/lib/libgphoto2/2.4.8/panasonic_dc1000.a
/usr/lib/libgphoto2/2.4.8/panasonic_dc1000.la
/usr/lib/libgphoto2/2.4.8/panasonic_dc1000.so
/usr/lib/libgphoto2/2.4.8/panasonic_dc1580.a
/usr/lib/libgphoto2/2.4.8/panasonic_dc1580.la
/usr/lib/libgphoto2/2.4.8/panasonic_dc1580.so
/usr/lib/libgphoto2/2.4.8/panasonic_l859.a
/usr/lib/libgphoto2/2.4.8/panasonic_l859.la
/usr/lib/libgphoto2/2.4.8/panasonic_l859.so
/usr/share/doc/libgphoto2-2/camlibs/README.panasonic
/usr/share/doc/libgphoto2-2/camlibs/README.panasonic-coolshot
/usr/share/doc/libgphoto2-2/camlibs/README.panasonic-l859
/usr/share/media-player-info/panasonic_sv-mp31v.mpi
/usr/share/mime/image/x-panasonic-raw.xml
/usr/src/linux-headers-2.6.32-38-generic/include/config/panasonic
/usr/src/linux-headers-2.6.32-38-generic/include/config/panasonic/laptop.h
/usr/src/linux-headers-2.6.35-31-generic/include/config/panasonic
/usr/src/linux-headers-2.6.35-31-generic/include/config/panasonic/laptop.h
/usr/src/linux-headers-2.6.35-32-generic/include/config/panasonic
/usr/src/linux-headers-2.6.35-32-generic/include/config/panasonic/laptop.h

user@Lucid:~$ [COLOR=#000000]locate[/COLOR] *p*nasonic*
/etc/acpi/events/panasonic-lockbtn
/home/user/Videos/panasonic_lumix_dmc_fz38_01.mts
/lib/modules/2.6.32-38-generic/kernel/drivers/platform/x86/panasonic-laptop.ko
/lib/modules/2.6.35-31-generic/kernel/drivers/platform/x86/panasonic-laptop.ko
/lib/modules/2.6.35-32-generic/kernel/drivers/platform/x86/panasonic-laptop.ko
/usr/lib/libgphoto2/2.4.8/panasonic_coolshot.a
/usr/lib/libgphoto2/2.4.8/panasonic_coolshot.la
/usr/lib/libgphoto2/2.4.8/panasonic_coolshot.so
/usr/lib/libgphoto2/2.4.8/panasonic_dc1000.a
/usr/lib/libgphoto2/2.4.8/panasonic_dc1000.la
/usr/lib/libgphoto2/2.4.8/panasonic_dc1000.so
/usr/lib/libgphoto2/2.4.8/panasonic_dc1580.a
/usr/lib/libgphoto2/2.4.8/panasonic_dc1580.la
/usr/lib/libgphoto2/2.4.8/panasonic_dc1580.so
/usr/lib/libgphoto2/2.4.8/panasonic_l859.a
/usr/lib/libgphoto2/2.4.8/panasonic_l859.la
/usr/lib/libgphoto2/2.4.8/panasonic_l859.so
/usr/share/doc/libgphoto2-2/camlibs/README.panasonic
/usr/share/doc/libgphoto2-2/camlibs/README.panasonic-coolshot
/usr/share/doc/libgphoto2-2/camlibs/README.panasonic-l859
/usr/share/media-player-info/panasonic_sv-mp31v.mpi
/usr/share/mime/image/x-panasonic-raw.xml
/usr/src/linux-headers-2.6.32-38-generic/include/config/panasonic
/usr/src/linux-headers-2.6.32-38-generic/include/config/panasonic/laptop.h
/usr/src/linux-headers-2.6.35-31-generic/include/config/panasonic
/usr/src/linux-headers-2.6.35-31-generic/include/config/panasonic/laptop.h
/usr/src/linux-headers-2.6.35-32-generic/include/config/panasonic
/usr/src/linux-headers-2.6.35-32-generic/include/config/panasonic/laptop.h

user@Lucid:~$ [COLOR=#000000]locate[/COLOR] panasonic
/etc/acpi/events/panasonic-lockbtn
/home/user/Videos/panasonic_lumix_dmc_fz38_01.mts
/lib/modules/2.6.32-38-generic/kernel/drivers/platform/x86/panasonic-laptop.ko
/lib/modules/2.6.35-31-generic/kernel/drivers/platform/x86/panasonic-laptop.ko
/lib/modules/2.6.35-32-generic/kernel/drivers/platform/x86/panasonic-laptop.ko
/usr/lib/libgphoto2/2.4.8/panasonic_coolshot.a
/usr/lib/libgphoto2/2.4.8/panasonic_coolshot.la
/usr/lib/libgphoto2/2.4.8/panasonic_coolshot.so
/usr/lib/libgphoto2/2.4.8/panasonic_dc1000.a
/usr/lib/libgphoto2/2.4.8/panasonic_dc1000.la
/usr/lib/libgphoto2/2.4.8/panasonic_dc1000.so
/usr/lib/libgphoto2/2.4.8/panasonic_dc1580.a
/usr/lib/libgphoto2/2.4.8/panasonic_dc1580.la
/usr/lib/libgphoto2/2.4.8/panasonic_dc1580.so
/usr/lib/libgphoto2/2.4.8/panasonic_l859.a
/usr/lib/libgphoto2/2.4.8/panasonic_l859.la
/usr/lib/libgphoto2/2.4.8/panasonic_l859.so
/usr/share/doc/libgphoto2-2/camlibs/README.panasonic
/usr/share/doc/libgphoto2-2/camlibs/README.panasonic-coolshot
/usr/share/doc/libgphoto2-2/camlibs/README.panasonic-l859
/usr/share/media-player-info/panasonic_sv-mp31v.mpi
/usr/share/mime/image/x-panasonic-raw.xml
/usr/src/linux-headers-2.6.32-38-generic/include/config/panasonic
/usr/src/linux-headers-2.6.32-38-generic/include/config/panasonic/laptop.h
/usr/src/linux-headers-2.6.35-31-generic/include/config/panasonic
/usr/src/linux-headers-2.6.35-31-generic/include/config/panasonic/laptop.h
/usr/src/linux-headers-2.6.35-32-generic/include/config/panasonic
/usr/src/linux-headers-2.6.35-32-generic/include/config/panasonic/laptop.h
user@Lucid:~$ 
```

---

### Post by jpeddicord on 2012-01-26
Does it help if you put quotes around the name? As in:

```
locate "PhotoRename*"
```

If there aren't quotes, bash will try to expand the name before it is sent to locate.

Also, note that the wildcard may be needed at the start, as the path is matched as well.
Perhaps this will work as you'd expect:

```
locate "*/PhotoRename*"
```

---

### Post by 2CV67 on 2012-01-26
> **jpeddicord said:**
> Does it help if you put quotes around the name? As in:

```
locate "PhotoRename*"
```

If there aren't quotes, bash will try to expand the name before it is sent to locate.

Also, note that the wildcard may be needed at the start, as the path is matched as well.
Perhaps this will work as you'd expect:

```
locate "*/PhotoRename*"
```

Thanks for the suggestion, but no - it doesn't work.

---

