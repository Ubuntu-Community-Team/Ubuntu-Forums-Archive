---
title: "Audible and Nero Nrg file to Iso????"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Shawn Dineley on 2008-04-30
Hello

    I'm trying to find a way to convert an .nrg file to an iso file. So I can burn it to a cd from my ubuntu box. I don't have a cd burner in my XP Box. When I'm at home I just listen to my aubible books on my xp system. But I'm going out of town for a few days, and would like to listen to a book or two on the trip. 

    I've googed it and searched the fourms. And tried a few things on both systems. Some trail software for windows ( But they want to much money. For me to use it only once.) And I've tried a program called nrg2iso on the ubuntu system. It converts the file, but after I burn it to the cd. And try to listen to it. I get an error message saying.

 Cannot mount volume.
 Invalid mount option when attempting to mount the volume.

  So does any one know of a way to make this work. Or am I going to have to search for radio stations on my 12 hour trip??

                              Thanks

---

### Post by megamania on 2008-05-04
I had your same problem (i.e. converting an nrg file to iso). nrg2iso worked perfectly and had no problem mounting the iso file (a dvd).

You may have used the wrong parameters when trying to mount the image. If you post what you used to mount it, I'll try to help.

---

### Post by Shawn Dineley on 2008-05-04
Thanks, but I give up on this. Found the audio book on other site, DRM free.

---

### Post by MeanderingCode on 2008-05-09
I'm having an issue with this.  I have an .nrg image of an audio cd.
```
myself@kioskfreedom:~$ nrg2iso part1.nrg part1.iso
|======================================================================>[100%]
part1.iso written : 835920818 bytes
myself@kioskfreedom:~$ sudo mount -o loop -t iso9660 part1.iso /mnt/iso/
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

myself@kioskfreedom:~$ dmesg|tail -n 1
[32265.404000] Unable to identify CD-ROM format.
```

I can only assume that the nero image was corrupt, nrg2iso didn't work, or the filesystem isn't iso9660 or udf (tried that, too).

Anyone else run into this?

---

### Post by scorp123 on 2008-05-09
See here:
[http://www.linuxquestions.org/questions/linux-software-2/how-can-i-burn-an-.nrg-image-file-with-k3b-224353/](http://www.linuxquestions.org/questions/linux-software-2/how-can-i-burn-an-.nrg-image-file-with-k3b-224353/)

You don't need "nrg2iso" ... the "dd" utility which is already on-board in every UNIX-like  OS is enough. According to that thread above:
```
dd bs=1k if=/path/to/Nero_image.nrg of=/path/to/target/ISO_image.iso skip=300
```

---

