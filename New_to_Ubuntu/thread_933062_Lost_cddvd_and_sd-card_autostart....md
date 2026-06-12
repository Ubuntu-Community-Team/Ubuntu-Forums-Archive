---
title: "Lost cd/dvd and sd-card autostart..."
date: 2008-09-29
forum: New to Ubuntu
---

### Post by neocortex on 2008-09-29
Hello!
I am posting this again, since no one seems to saw and react to this problem.
In brief, suddenly my autostart for cd/dvd and sd-card is lost, but for usb-flash behaves properly (by opening Nautilus). I tried various thing, but it appears that problem cannot be found: fstab seems ok, and everything else as well (like checkings in gconftool-2, hal etc.). Now, I need to go to Places and click on cd/dvd. Only then it appears on the desktop and opens in Nautilus.
Can anyone respond and help? I am afraid that this could be some "more serious instability".
There are two links, but no solutions:
[http://ubuntuforums.org/showthread.php?t=897714](http://ubuntuforums.org/showthread.php?t=897714)
[http://ubuntuforums.org/showthread.php?t=897572](http://ubuntuforums.org/showthread.php?t=897572)

Best,
PM

---

### Post by didac on 2008-09-29
Type gconf-editor in a terminal, if you have it installed. Browse to /desktop/gnome/volume_manager and check automoun_media and automount_drives, and any other automount you would like to have.

If you don't have gconf-editor, do it by hand:

gedit ~/.gconf/desktop/gnome/volume_manager/%gconf.xml

and add:

        <entry name="automount_drives" mtime="1222689930" type="bool" value="true">
        </entry>
        <entry name="automount_media" mtime="1222689929" type="bool" value="true">
        </entry>

Hope it helps.

---

### Post by neocortex on 2008-09-29
I tried that, but nothing!

PM

---

