---
title: "Play a sound when a condition is met?"
date: 2013-10-09
forum: Programming Talk
---

### Post by vasa1 on 2013-10-09
I have this script to prevent screen blanking when the CPU usage is > 8% :```
#!/usr/bin/env bash

sleep_period=8m 

while true; do
  if ps -eo %C --sort -%cpu | head -2 | awk 'NR==2 { exit !($1>8); }'; then
      xdotool key Shift
  fi
  sleep ${sleep_period}
done

```

Can I have a sound play whenever **xdotool key Shift** is executed? I'm thinking of something like
```
mplayer --really-quiet /usr/share/sounds/freedesktop/stereo/bell.oga
```

My system is Lubuntu 13.04. It doesn't have Pulseaudio as far as I can tell and so **paplay** is not an option. I have **alsa-utils** but **aplay** gives a horrible sound, like white noise.

**Edit**: I'm reading a bit about Pulseaudio v/s alsa and some people feel that alsa can't handle two programs playing sound at the same time. So, I'm wondering whether my question is valid and if it is, whether alsa can do what I want when I watching a video, the most typical situation when I don't want to screen to blank.

---

### Post by ofnuts on 2013-10-09
[http://linux.die.net/man/1/beep](http://linux.die.net/man/1/beep)

(beep is your friendly distro repository)

---

### Post by drmrgd on 2013-10-09
See also this thread where the program 'espeak' was mentioned.  That might also be helpful (or at least entertaining!):

[http://ubuntuforums.org/showthread.php?t=2096908](http://ubuntuforums.org/showthread.php?t=2096908)

---

