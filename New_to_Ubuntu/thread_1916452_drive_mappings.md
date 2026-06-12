---
title: "drive mappings"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by DGINSD on 2012-01-28
This will probably seem like a really stupid question but its causing me a lot of problems and I cant seem to find a good answer. How are CD/DVD drives named in Ubuntu (SD0 SDA1) and is there a quick command I can give in the terminal to spit out all what I have.

I need to tell wine where my drives are so some burning programs can work and the instructions I found here [help.ubuntu.com/community/Wine]("help.ubuntu.com/community/Wine") didn't work. Not to mention the Linux based programs that I cant set up right cause I just don't know what and where everything is.

Any help is really appreciated.

---

### Post by roger_1960 on 2012-01-28
Hi

does
```
df
```
help?

```
man df
```
gives all the options

---

### Post by mcduck on 2012-01-28
> **DGINSD said:**
> This will probably seem like a really stupid question but its causing me a lot of problems and I cant seem to find a good answer. How are CD/DVD drives named in Ubuntu (SD0 SDA1) and is there a quick command I can give in the terminal to spit out all what I have.

I need to tell wine where my drives are so some burning programs can work and the instructions I found here [help.ubuntu.com/community/Wine]("help.ubuntu.com/community/Wine") didn't work. Not to mention the Linux based programs that I cant set up right cause I just don't know what and where everything is.

Any help is really appreciated.

Like the guide says, the mount points for the drives should be /media/cdrom (or /media/cdrom0) for the first drive, /media/cdrom1 for second drive, and so on.

Note that you should use the mount point, not the device name.

...and also you'll surely get much better results, with much less problems, if you just use a native Linux application instead. Have you tried Brasero, which is already installed by default and should just work without needing any configuration?

---

### Post by DGINSD on 2012-01-28
> **mcduck said:**
> Like the guide says, the mount points for the drives should be /media/cdrom (or /media/cdrom0) for the first drive, /media/cdrom1 for second drive, and so on.

Note that you should use the mount point, not the device name.

...and also you'll surely get much better results, with much less problems, if you just use a native Linux application instead. Have you tried Brasero, which is already installed by default and should just work without needing any configuration?

I tried to do it exactly like the drive, but the program (DVDShrink) still doesn't see either of my drives (built in CD-R/DVD, sr0, or USB connected CD-R/DVDRW DL, SR1)

roger_1960 I tried the DF command heres what output I got 

```

david@david-Latitude-X300:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             15378832   6177840   8419784  43% /
udev                    306932         4    306928   1% /dev
tmpfs                   125580       940    124640   1% /run
none                      5120         0      5120   0% /run/lock
none                    313940       648    313292   1% /run/shm
/dev/sda6             28835836   6828372  20542684  25% /home
/dev/sr0               7894744   7894744         0 100% /media/LTZERO

``` 

Kinda confused about it though the "'/dev/sr0" is my built in CD-R/DVD, but so is "/media/LTZERO"  that's the disc in it. There's no mention of my CD/DVD drive plugged into the USB ports.

---

### Post by mcduck on 2012-01-28
Then how about using a Linux-native application instead of DVDShrink?

Some possible apps made for the same purpose would be Thoggen, Acidrip, xdvdshrink, k9copy and OGMrip. And I'm sure there are plenty of more options available.

---

### Post by DGINSD on 2012-03-26
I actually forgot about this thread I had made for issues I had on my old machine. Reviewing this thread actually helped me solve my other issue I started another thread on, along with some other gathered information online.

[http://ubuntuforums.org/showthread.php?t=1946371]("http://ubuntuforums.org/showthread.php?t=1946371")

---

