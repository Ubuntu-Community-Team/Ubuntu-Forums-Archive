---
title: "SMPlayer failing to pass file to mplayer"
date: 2008-04-05
forum: Packaging and Compiling Programs
---

### Post by Robbyx on 2008-04-05
Videos are playing in mplayer.
The same videos when opened in SMPlayer produce an immediate error message:

> MPlayer has finished unexpectedly: Exit code 1. 

I get the same error message whatever the type of file eg avi


> /usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -zoom -nokeepaspect -framedrop -autosync 100 -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 54525966 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast -1 -brightness -6 -hue -6 -saturation 1 -volume 40 -nocache -osdlevel 0 -idx -vf-add pp -autoq 6 -vf-add screenshot -vf-add eq2,hue -channels 2 -af volnorm=2 -softvol -softvol-max 110 /media/flm/English.rmvb

I am using v .6.0rc3 with qt4.2.3 in Ubuntu Gutsy

I would appreciate some help because I used SMPlayer in Fiesty and would like to continue to use now I am in Gutsy.

Robin

---

### Post by mc4man on 2008-04-05
maybe better to move to muiltimedia forum rvn4000 answers smplayer posts very quickly. While the issue doesn't appear to be the same you may want to try newer version of smplayer and or mplayer - see here #24
[http://ubuntuforums.org/showthread.php?t=684193&page=3](http://ubuntuforums.org/showthread.php?t=684193&page=3)

---

### Post by Robbyx on 2008-04-06
Thank you.  I have repeated my question in the suggested conference.

---

