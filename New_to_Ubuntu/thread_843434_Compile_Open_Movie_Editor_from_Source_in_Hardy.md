---
title: "Compile Open Movie Editor from Source in Hardy"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by punong_bisyonaryo on 2008-06-28
Hey all!

I'm trying to install Open Movie Editor from source because the one in the repositories are too outdated. But I am running into some dependency problems. I've managed to get past libsamplerate and libsndfile by installing libsamplerate-dev, libflac-dev and libsndfile-dev, but I can't seem to figure out gavl (gmerlin audio).

Any help would be much appreciated.

Thanks!

---

### Post by oldos2er on 2008-06-28
libgavl-dev

---

### Post by aimpau on 2008-06-28
Pwede ba i-save mo rin ako nyang openmovieeditor. hehehe. tagal mag update ng repos.

---

### Post by punong_bisyonaryo on 2008-06-29
I already tried to install libgavl-dev. No such sweet luck since the one in the repos is outdated (0.2.5) and OME requires 1.0.0. I managed to make . deb for gavl 1.0.0, but libquicktime was also a problem. (Repo: 1.0.0 OME, dep: 1.0.2)

I wanted to make a .deb for libquicktime 1.0.2 also but there are quite a few soft-dependencies (vorbis, ffmpeg, etc.)

```
Configuration: 
libdv:      Missing (Go to http://libdv.sourceforge.net)
vorbis:     Missing (Go to http://www.vorbis.com/)
lame:       Missing (Go to http://www.mp3dev.org/)
libjpeg:    Missing (Go to http://www.ijg.org/)
libpng:     Missing (Go to http://www.libpng.org/pub/png/libpng.html)
libavcodec: Missing (Go to http://www.ffmpeg.org/)
libswscale: Missing (Go to http://www.ffmpeg.org/)
gtk >= 2.4.0: Missing (Go to http://www.gtk.org/)
Alsa        Missing (Go to http://www.alsa-project.org/)
GPL plugins Disabled

```

If you can guide me through this, I'll post my .deb.

Thanks!

PS. If you need the GAVL .deb I made, just give me the address to send it to.
PPS. It's not packaged that nicely (couldn't fix the description well), but it works. And it'll get you by.

---

### Post by toasterboy1 on 2008-10-10
Not sure how much help this is but you might just be able to run
```
sudo apt-get build-dep libquicktime
```
I am in the process of compiling from source, on Intrepid, and manually went through and added the following packages from synaptic libdv4-dev, libvorbis-dev, libmp3lame-dev, libavcodeec-dev, libswscale-dev, libfaac-dev, libfaad2-0, and libx264-dev. You will need to run
```
./configure --enable-gpl --with-libdv
```
The --with-libdv got rid of the disabled libdv for me. I do not know how to make debs and even if I did I am not sure if/how to make it work for a different version but if you fill me in I would be willing to try. Just finished installing Open Movie Editor 0.0.20080523.

---

