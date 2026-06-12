---
title: "another one 'bout ipod touch (in gutsy worked, in hardy no lol)"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by RoMo on 2008-05-08
Hello guys, i didn't wanted to post since i was sure all the data i needed to fix my problem would be on those forums, but I've been looking like crazy and i just can't find an answer (and even a question) that has to do with my issue.

So, here's the thing:

I have an iPod Touch 1.1.1 jailbroken, i used to send music and videos with gtkpod in ubuntu 7.10 with no problem (i had ipod-convenience) and no problems at all. When i upgraded to hardy i installed ipod-convience, configured it and all that nice stuffs. My iPod mounts OK after a ipod-touch-mount... BUT when i enter to gtkpod it just doesn't show my songs i just have an empty directory, so i tried to upload it, it does upload it but my ipod didn't recognize it, i tried with amarok and with rhythmbox and its the same.

I also tried the FirewireGuid thing in the ubuntu help, but it didn't help at all.

I thought that in this new version I would barely need to install ipod-convience to make it work, and its really *hardy* to do so (bad joke, sorry lol)

thanx in advance!

---

### Post by RoMo on 2008-05-09
c'mon guys, really no one?

---

### Post by RoMo on 2008-05-10
OK i already kinda fixed this... what did i did?

well, i just used the old ipod-convenience... i dunno if someone else overthere is having the same issue as i do, anyways i'm posting here my little script:

```
#!/bin/bash

wget http://romo.homelinux.org/ipod-convenience-downgrade.tar.gz
tar xvfz ipod-convenience-downgrade.tar.gz
cd ipod-convenience-downgrade

if [ ! -d /usr/share/ipod-convenience ]
then
	echo "Creating directories"
	mkdir usr/share/ipod-convenience/
	mkdir usr/share/doc/ipod-convenience/

fi

cp etc/default/ipod-convenience /etc/default/ipod-convenience 
cp var/lib/dpkg/info/ipod-convenience.preinst /var/lib/dpkg/info/ipod-convenience.preinst  
cp var/lib/dpkg/info/ipod-convenience.templates /var/lib/dpkg/info/ipod-convenience.templates
cp var/lib/dpkg/info/ipod-convenience.md5sums /var/lib/dpkg/info/ipod-convenience.md5sums
cp var/lib/dpkg/info/ipod-convenience.list /var/lib/dpkg/info/ipod-convenience.list
cp var/lib/dpkg/info/ipod-convenience.config /var/lib/dpkg/info/ipod-convenience.config
cp var/lib/dpkg/info/ipod-convenience.postrm /var/lib/dpkg/info/ipod-convenience.postrm
cp var/lib/dpkg/info/ipod-convenience.conffiles /var/lib/dpkg/info/ipod-convenience.conffiles
cp var/lib/dpkg/info/ipod-convenience.postinst /var/lib/dpkg/info/ipod-convenience.postinst
cp usr/share/doc/ipod-convenience/changelog.Debian.gz /usr/share/doc/ipod-convenience/changelog.Debian.gz
cp usr/share/doc/ipod-convenience/changelog.gz /usr/share/doc/ipod-convenience/changelog.gz
cp usr/share/doc/ipod-convenience/copyright /usr/share/doc/ipod-convenience/copyright
cp usr/share/doc/ipod-convenience/README.gz /usr/share/doc/ipod-convenience/README.gz
cp usr/share/ipod-convenience/mount-umount /usr/share/ipod-convenience/


echo "ipod-convenience downgraded"
```

*edit*

well, i did some "improvements" to the script:

after installing it you can run ipod-touch-mount firmware-version or iphone-mount firmware-version 

for example ipod-touch-mount 1.1.1

it should mount everything where it should go

*edit*

you can copy it to gedit or somethin' save it as downgrade.sh then change permissions with ```
chmod +x downgrade.sh
``` and then run it as super user with ```
sudo ./downgrade.sh
```

the real issue here is mount-umount (ipod-touch-mount in the source of the newest version of ipod-convenience), but i think is better to move all the files =).

is kinda ugly, i know but it's 2 am and i'm tired lol... i will keep it on my server a couple days, feel free to modify.

---

### Post by t3hi3x on 2008-05-10
Let us know if this worked. I'm curious about my iPhone

---

### Post by RoMo on 2008-05-10
> **t3hi3x said:**
> Let us know if this worked. I'm curious about my iPhone
it did work for me, if you are having troubles please check it out. obviosly you have to have firmware 1.1.2 or 1.1.1 today im making a the fix for 1.1.3

cheers

---

