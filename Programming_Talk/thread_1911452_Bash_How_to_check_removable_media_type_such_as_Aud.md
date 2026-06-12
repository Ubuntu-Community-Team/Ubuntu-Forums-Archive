---
title: "Bash: How to check removable media type such as Audio CD and Video DVD?"
date: 2012-01-18
forum: Programming Talk
---

### Post by sideburn on 2012-01-18
Hello Nix Coders!

Is there a way to create a script something like this:
(If removable_media_type = Audio CD then command
If removable_media_type = Video DVD then command)
else
command

Thanks!

---

### Post by Vaphell on 2012-01-19
is there a way? sure
if it's trivial? depends

i can think of few ways to tackle it

1. detect cdda-something in ~/.gvfs (audiocds mount there with some automatically created name)
check if in /media there is a folder with AUDIO_TS and VIDEO_TS dirs (video dvd)

2. mow through the output of lshal
```
lshal | grep volume.disc
```
audio cd:
```
volume.disc.capacity = 472221696  (0x1c258800)  (uint64)
volume.disc.has_audio = true  (bool)
volume.disc.has_data = false  (bool)
volume.disc.is_appendable = false  (bool)
volume.disc.is_blank = false  (bool)
volume.disc.is_rewritable = false  (bool)
volume.disc.type = 'cd_rom'  (string)
```

video dvd:
```
volume.disc.has_audio = false  (bool)
volume.disc.has_data = true  (bool)
volume.disc.is_appendable = false  (bool)
volume.disc.is_blank = false  (bool)
volume.disc.is_blurayvideo = false  (bool)
volume.disc.is_rewritable = false  (bool)
volume.disc.is_svcd = false  (bool)
volume.disc.is_vcd = false  (bool)
volume.disc.is_videodvd = true  (bool)
volume.disc.type = 'dvd_rom'  (string)
```

may be annoying if you have more than 1 optical drive and need to detect proper one

---

### Post by sideburn on 2012-01-20
@Vaphell:

Wahoo!  Thanks for your help!  I use Lubuntu which doesn't use hal so I couldn't use lshal command but because of your hints I whipped up a code (my first bash code :P)...this code will run VLC automatically with less number of mouse clicks between inserting disc to final media output.  And IT WORKS!  Lemme know if there's better way:
```
#!/bin/bash
checkforaudio=`gvfs-info -f cdda://sr0/ | grep "filesystem::type: cdda"`
if [ "$checkforaudio" == "  filesystem::type: cdda" ]; then
    vlc cdda:///dev/sr0
    else
        checkfordvd=`find /media/*/ -name "VIDEO_TS" | grep "VIDEO_TS"`
        if [ ${checkfordvd:(-8)} == "VIDEO_TS" ]; then
            vlc dvd:///dev/sr0
            else
            pcmanfm
        fi
fi
exit 0
```

---

### Post by Vaphell on 2012-01-20
probably there is but i don't know one. Your question made me curious so I did a small investigation about disc detection - i must say that google was surprisingly unhelpful, this certainly is not a common knowledge.

minor stuff
- use $() instead of ``

- try to put use cases on the same level, eg
```
if [ cd ]; then
  ...
elif [ dvd ]; then
  ...
else
  ...
fi
```
makes logic of the script easier to follow

- it's enough to test if these variables are not empty, grep makes sure that not-null string -> test passed

---

### Post by sideburn on 2012-01-20
Thanks for your guidance!  \\:D/

---

