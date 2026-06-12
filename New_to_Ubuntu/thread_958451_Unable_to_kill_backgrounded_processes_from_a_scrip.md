---
title: "Unable to kill backgrounded processes from a script"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by john.hall on 2008-10-25
I'm messing around with my audio settings (using a loopback device), and I wrote this script to play an audio file:

play_file.sh
```

#!/bin/bash

me=`basename $0`

if [ $# -ne 1 ]; then
  echo "$me: must give filename"
  exit 1
fi

mplayer $1 > /dev/null 2>&1 &
#play_audio > /dev/null 2>&1 &        # doesn't work
arecord -D hw:1,1 -f cd 2> /dev/null | aplay -D hw:0 -f cd > /dev/null 2>&1 &      # works

wait %1
kill %2

```

It works as it is written.  However, when I try to move the arecord line to a separate script, the kill %2 fails to kill the arecord and aplay processes.  You can probably guess what it looks like, but here is the second script:

play_audio.sh
```

#!/bin/bash

arecord -D hw:1,1 -f cd | aplay -D hw:0 -f cd

```

Simply uncommenting the play_audio line and commenting the arecord line in play_file.sh creates the problem.  play_audio.sh is, of course, in the PATH (well, there's a symlink called play_audio involved) and has executable permissions.

Actually, when the kill %2 returns, job #2 is still active (adding 'jobs' in there and checking the output tells this).

Why does this happen?

---

### Post by cantormath on 2008-10-25
eer, kill -9?

[http://www.youtube.com/watch?v=Fow7iUaKrq4](http://www.youtube.com/watch?v=Fow7iUaKrq4)

or maybe killall

---

### Post by john.hall on 2008-10-25
OK, this is somewhat related (same task, but a different problem).  When I restarted the machine and issued modprobe snd-aloop, audio no longer goes through the loopback device.  

Here is my .asoundrc:
```

pcm.!default {
    type hw
    card 1
    device 0
}

```

ls -l /proc/asound/Loopback:
```

lrwxrwxrwx 1 root root 5 2008-10-25 12:04 /proc/asound/Loopback -> card1

```

I don't see a difference between this time (when it doesn't even go through the loopback device) and last time (when it did).

Nice vid BTW.

---

### Post by john.hall on 2008-10-25
Nevermind, that last was because I forgot to kill pulseaudio.  Now I'm back to the original problem of it not killing the arecord and aplay processes.

Unfortunately, using kill -9 %2 didn't help.  Using killall play_audio did not kill the arecord and aplay processes.  It did, however, stop the job.  In fact, it gives me a strange message:

```

/home/joha/bin/play_file: line 19:  6630 Terminated              play_audio > /dev/null 2>&1

```

Using killall arecord does what I want, but I'd rather not do it that way.  What if I decide to change to a different program besides arecord?  There should be a way to do this without knowing the inner workings of the play_audio.sh script.

---

