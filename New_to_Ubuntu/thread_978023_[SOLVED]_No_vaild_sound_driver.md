---
title: "[SOLVED] No vaild sound driver"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by Skivache on 2008-11-10
I just installed moc on a laptop running xubuntu 8.10, and if I open up a terminal window and launch mocp, everythig works perfectly and it plays music.  However, if I ssh into the laptop and launch mocp, I get the following error: 
```
Running the server...
Trying JACK...
Trying ALSA...
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
Trying OSS...

FATAL_ERROR: No valid sound driver


FATAL_ERROR: Server exited

```

I know the sound works because it plays in every application using the GUI. Any help is appreciated :)

---

### Post by Skivache on 2008-11-10
Since this is already the second google result for this error, I figured I would post the solution that worked for me:

1) kick yourself for being a genuis
2) Since I run the laptop without X most of the time, I aparently forgot to log out before killing X, so just restart the process, log in, then back out, and kill it again
3) enjoy wonderful sound

Running the commands as root worked too, which led me to believe that it was something simple instead of truly missing drivers.

---

