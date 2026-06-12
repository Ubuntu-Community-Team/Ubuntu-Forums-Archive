---
title: "Shell script for OO Impress video player--autodetect screen resolution?"
date: 2010-03-14
forum: Programming Talk
---

### Post by legatek on 2010-03-14
Dear script gurus,

As you may know, playing movies in Openoffice Impress is a pain in the ***. The option that stands the most hope of working is to launch an external player when an image is clicked in the presentation. The problem I foresee is if I present on beamers of different resolution. The one I use most often beams at 800x600, but others can project at 1280x1024 and I want to make sure that the movies project at the right size in the right place no matter what resolution. I can change the resolution of my laptop to match the projector resolution, and I would like to write into my scripts to launch the external player with different options based on my chosen res. here's an example script I use to launch an avi:
```
#! /bin/sh
# WT_actin_dynamics.sh

killall xine
xine --no-splash -B -l=repeat --geometry 422x421+492+369 \
/media/sda2/~lab\ book/cell\ culture\ assays/data/actin\ dynamics/WT4-movie-jpg.avi
```

the geometry options are movie dimensions followed by coordinates of the top left pixel, and are designed to match the image that launches the script. These must change based on screen resolution. How can I modify the script to do this:

if screen resolution = 1280x1024
     launch xine --geometry some_coordinates
if screen resolution = 800x600
     launch xine --geometry some_other_coordinates

Thanks for your suggestions.

---

### Post by legatek on 2010-03-14
Ive been trying to figure this out this afternoon, and am trying to use xrandr to determine the resolution. I want to assign the resolution to a variable, but the problem is when I try to echo the value of the variable the output is empty. What am I missing here?

(Note: everything except the variable assignments is commented out for now.)

```
#! /bin/sh
# WT_actin_dynamics.sh

killall xine
res="$(xrandr -q | awk -F'current' -F',' 'NR==1 {gsub("( |current)","")}')"
res2="$(xrandr -q|grep '^\*')"
#if [[ "$res" = "800x600" ]]; then
#xine --no-splash -B -l=repeat --geometry 305x305+77+153 \
#/media/sda2/~lab\ book/cell\ culture\ assays/data/actin\ dynamics/WT4-movie-jpg.avi
#fi
#if [[ "$res" = 1280x1024 ]]; then
#xine --no-splash -B -l=repeat --geometry 487x487+125+277 \
#/media/sda2/~lab\ book/cell\ culture\ assays/data/actin\ dynamics/WT4-movie-jpg.avi
#fi
echo "$res"
echo "$res2"
```

---

### Post by legatek on 2010-03-14
Ok, I figured it out, using perl instead of awk. Hopefully this will be of some use for someone.

This is how to play videos in Openoffice Impress using the same script for any number of different screen resolutions:

```
#! /bin/sh
# WT_actin_dynamics.sh

killall xine
res="$(xrandr -q|perl -F'\s|,' -lane "/^Sc/&&print join '',@F[8..10]")"
if [ "$res" = 800x600 ]; then
xine --no-splash -B -l=repeat --geometry 305x305+77+153 \
/media/sda2/~lab\ book/cell\ culture\ assays/data/actin\ dynamics/WT4-movie-jpg.avi
fi
if [ "$res" = 1280x1024 ]; then
xine --no-splash -B -l=repeat --geometry 487x487+125+277 \
/media/sda2/~lab\ book/cell\ culture\ assays/data/actin\ dynamics/WT4-movie-jpg.avi
fi
```

Hopefully the OO devteam provides native video support soon. This is a pain in the behind to do for a lot of videos.

---

