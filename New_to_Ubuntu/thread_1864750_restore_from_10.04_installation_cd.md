---
title: "restore from 10.04 installation cd"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by owiknowi on 2011-10-19
which files can be restored from the original ubuntu 10.04.3_64 installation cd? either manually or automatic (restore option?)

say, some localizations are missing from /user/share/i18n/supported. do i have to reinstall 10.04.3 lts, all over again or can i restore those files from cd?

p.s. the installation of language/localization packs from the online repositories doesn't work!

---

### Post by collisionystm on 2011-10-19
Not sure if it would help, but have you tried rebooting to the system rescue menu?

Reboot your computer, immediately after the bios hold the SHIFT key 

choose system rescue

try fsck

try fix broken packages

---

### Post by owiknowi on 2011-10-19
thanks for your reply collisionystm!
alas, it didn't work: i did get a very basic gui with some options.
so i added your commands -not both at the same time of course- as parameters, but the cd booted to the live desktop just the same.

i did however copy the entire **i18n** folder from the live filesystem, and replaced the installed i18n folder. didn't help. still may only choose between english locales.

---

### Post by owiknowi on 2011-10-19
add.
of course i also tried the options as provided on the cd when pressing 'esc' before booting.
one neat comment i got was something along the lines of:
'this cd doesn't provide a recovery tool/mode, but you can always find an answer online" or sum such.

fsck gave another message, ran from cd or a pre-boot command line: "you  ***WILL*** etc.etc. ***SEVERE*** etc.etc. damage your system."
must have been a programmer on something or the rich air on the isle of mann, seeing all them stars...

so, i'm stuck with a system which is unable to switch its locales or repair its file system for that matter.

---

### Post by madjr on 2011-10-19
not sure if this might help:
[http://ubuntuforums.org/showthread.php?t=196414](http://ubuntuforums.org/showthread.php?t=196414)

other than that check your sources list.

if nothing else helps, reinstalling might be the only way (you can see from a live-cd session if the locales download or not).

---

### Post by owiknowi on 2011-10-20
those commands still work in u10.04.3_64, q.e.d. now i'm able to choose the locales from which the text support is installed.

so that's still a valuable link (don't know about later versions of ubuntu, but they look pretty generic commands to me).

thanks a lot madjr!

regards, owiknowi

p.s. i will not mark this thread as solved, since i think ubuntu installation cd's (better a dvd by now) should do a way better job in restoring corrupted installations.

---

