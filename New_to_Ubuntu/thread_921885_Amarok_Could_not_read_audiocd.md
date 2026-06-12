---
title: "Amarok: Could not read audiocd"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by ChompTheMan on 2008-09-16
I am using Amarok 1.4.9.1 in KDE 3.5.10 on Hardy Heron.  When I try to play an audio cd I get the message 'Could not read audiocd' in the bottom left corner.  I have all necessary codecs installed, tried installing kdemultimedia-kio-plugins and kdemultimedia-kfile-plugins, changed the default device in Audio CD Configuration to /dev/cdrom, /dev/cdrom0, and media:/scd0/, and changed the output plugin to ALSA, all to no avail.  Anyone know anything else I can try?

---

### Post by ChompTheMan on 2008-09-17
Bump.  Still haven't found a solution.

---

### Post by mc4man on 2008-09-17
While kubuntu has some quirks with multimedia playback this *could* be something basic
 run ```
sudo lshw -C disk
``` and ck. under the *cdrom listing for device node and /dev/links for your drive.

> /dev/cdrom, /dev/cdrom0, and media:/scd0/,
the only valid one is /dev/cdrom
your drive may be /dev/cdrom1 or even higher (if you did an upgrade or have swapped drives

If it's not that, then can look at kubuntu

---

### Post by cowb0y on 2009-01-12
As indicated, your CD drive may be assigned /dev/cdrom1 (open a konsole and enter:

ls /dev/cdrom*

to see the device filenames.

By default, Amarok is looking for /dev/cdrom.  Either create a symlink from /dev/cdrom1 to /dev/cdrom (advanced), or tell Amarok the correct device filename to use: In Amarok, go to menu Settings/Configure Amarok.... Under the Engine section, set Default Device to the correct filename (probably /dev/cdrom1).

Also, if this resolved your issue, please add [SOLVED] to the subject line of your original post.

---

### Post by ilam_user on 2009-03-18
I had the same problem and this post solved my problem.

In my case I had added a new DVD drive in place of my old CD drive.

Many thanks cowb0y and mc4man.

---

