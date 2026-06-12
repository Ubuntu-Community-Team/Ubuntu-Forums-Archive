---
title: "no video on .avi and .mov files"
date: 2006-01-17
forum: Repositories &amp; Backports
---

### Post by janey on 2006-01-17
i'm probably posting in the wrong place, but i'll try anyway.

i've downloaded two files, one is a .avi and the other a .mov, and both will play only sound, not the video. they automatically open in totem. 

:confused:  is there a plugin i need to download, or another program i could get that would play these? a friend mentioned automatix, but i'm not sure how to get it.

help much appreciated!
thanx.

---

### Post by welsh_spud on 2006-01-17
Automatix is available here: [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

It's easy enough to install, the instructions are down the page a little bit.

I find that Automatix tends to solve pretty much every annoying codec problem around!

---

### Post by janey on 2006-01-17
thanks for the link! the first line i put into the terminal all seemed to go ok. the second line, i put in my password, and i got this error:

janey@janey-d:~$ sudo dpkg -i automatix-ubuntu_4.4-2_i386.deb.
Password:
dpkg: error processing automatix-ubuntu_4.4-2_i386.deb. (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 automatix-ubuntu_4.4-2_i386.deb.
janey@janey-d:~$

any clues?

---

### Post by welsh_spud on 2006-01-17
When you downloaded the .deb file, it probably saved in your Desktop directory. When you ran sudo dpkg -i whatever.deb it was looking for the file in your HOME directory. Try this:

cd Desktop

then run the automatix install line.

---

### Post by dragonfyre13 on 2006-01-17
Or you could grab Easy Ubuntu, which doesn't require installation, and is geared much more towards beginners, and less toward power users.

[http://placelibre.ath.cx/keyes/index.php/2005/10/27/65-easy-ubuntu-24-beta](http://placelibre.ath.cx/keyes/index.php/2005/10/27/65-easy-ubuntu-24-beta)

---

