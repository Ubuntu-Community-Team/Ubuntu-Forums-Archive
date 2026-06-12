---
title: "Best program for transcoding"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by jw860 on 2008-11-06
Ok I need a good program that is easy to use to transcode music I will be transcoding a lot of flac files to mp3 and some flac files to .ogg what would a good program be for that.

---

### Post by SuperSonic4 on 2008-11-06
pacpl audio converter

[http://sourceforge.net/projects/pacpl/](http://sourceforge.net/projects/pacpl/)

it has dolphin, amarok and konqueror integration.

An ffmpeg script could probably do the job too

```

cd [COLOR="Red"]<place>[/COLOR]
for i in *.flac; do ffmpeg -i "$i" -acodec copy "`echo "$i" | sed -r -e 's/(.*)\.flac$/\1.mp3/'`"; done
```

I should point out it might not work since I adapted it from ripping the audio from flv files

---

### Post by SteelDragon on 2008-11-06
I like sox, which you can find in the repos. It does pretty much everything I've ever wanted to do.

---

### Post by jw860 on 2008-11-06
Ok how about lame I have it installed and I no it is a command line program does anyone have a tutorial or is there a good gui for lame I could use?

---

### Post by click4851 on 2008-11-06
EAC with lame of course.........

---

### Post by click4851 on 2008-11-06
you might try....

[http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

I haven't myself, but it looks promising...?

---

### Post by SuperSonic4 on 2008-11-06
I think a CLI would be less trouble for the OPs system but soundconverter is a good frontend (and it is in the repos)

---

