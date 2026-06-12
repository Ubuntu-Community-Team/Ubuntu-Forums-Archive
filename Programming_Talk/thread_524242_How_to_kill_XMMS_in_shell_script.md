---
title: "How to kill XMMS in shell script"
date: 2007-08-12
forum: Programming Talk
---

### Post by JoseArmandoJeronymo on 2007-08-12
I'm trying to have my PC wake me up in the morning with a selected song, then tell me the day and time and then tune in some webstream.

I wrote the following shell script:

#!/bin/bash
amixer set PCM Playback Volume 35%
xmms -p "file:///home/prospero/musica/Manhattan.mp3"
sleep 3
/home/prospero/scripts/date.sh
gxine mms://212.77.1.198/rete1
exit 0

The problem is that once xmms has finished playing the music file it will not go away by itself thus preventing script from executing the next instruction, "sleep 3" and the ones following it.

I have tried to place killall xmms after the xmms play instruction with no results (as one would expect, but I had to try).

Of course if I close xmms manually the script resumes execution but I mean to have a few more minutes in bed, listening to a distant radio:)

I am new in shell scripting and would welcome any guidance here.

Thanks a lot!

---

### Post by slavik on 2007-08-12
try
```

xmms -p "file:///home/prospero/musica/Manhattan.mp3" &

```

or you can fork the script and then in one script run xmms and another to do the other stuff.

---

### Post by JoseArmandoJeronymo on 2007-08-13
Hi slavic

thanks for the hint but unfortunately it did not work. I also tried to fork the process this way:

```
#!/bin/bash
amixer set PCM Playback Volume 35%
(
xmms -p "file:///home/prospero/musica/Manhattan.mp3"
)
sleep 3
#/home/prospero/scripts/date.sh
gxine mms://212.77.1.198/rete1
exit 0
```

but xmms (or xine, FTM) still hangs around after playing the song and do not let the script go on. (I commented out the line that runs date.sh - which makes espeak say the local time - to check if there were some sort of ESD problems, etc but nothing changed)

I'm using this: [http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html) and this:  [http://www.tldp.org/LDP/abs/html/index.html](http://www.tldp.org/LDP/abs/html/index.html) as a bash scripting guide. Any further reference would be welcome.

Thanks again!

---

### Post by slavik on 2007-08-13
> **JoseArmandoJeronymo said:**
> Hi slavic

thanks for the hint but unfortunately it did not work. I also tried to fork the process this way:

```
#!/bin/bash
amixer set PCM Playback Volume 35%
(
xmms -p "file:///home/prospero/musica/Manhattan.mp3"
)
sleep 3
#/home/prospero/scripts/date.sh
gxine mms://212.77.1.198/rete1
exit 0
```

but xmms (or xine, FTM) still hangs around after playing the song and do not let the script go on. (I commented out the line that runs date.sh - which makes espeak say the local time - to check if there were some sort of ESD problems, etc but nothing changed)

I'm using this: [http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html) and this:  [http://www.tldp.org/LDP/abs/html/index.html](http://www.tldp.org/LDP/abs/html/index.html) as a bash scripting guide. Any further reference would be welcome.

Thanks again!
you're not forking anything ... you are simply running another script.

---

### Post by JoseArmandoJeronymo on 2007-08-13
Right.....:confused: 

Maybe I had better going back to the books and finding out exactly how to fork a process.:)

Anyway, I came up with something of a temporary solution by putting the play music part of the script in one separate script and then using a pause  to wait for the lenght of the track played and before killing the script and the player:

```
#!/bin/bash

amixer set PCM Playback Volume 45%

(
/home/prospero/scripts/manhattan.sh &
)
sleep 260
killall manhattan.sh
killall xmms

/home/prospero/scripts/date.sh

gxine mms://212.77.1.198/rete1

exit 0
```

where manhattan.sh is

```
#!/bin/bash

xmms -p "file:///home/prospero/musica/Manhattan.mp3"

exit 0
```

This works but is quite ugly and I look forward to improving it.

Thanks again,

---

### Post by s1ightcrazed on 2007-08-13
Do you have to use xmms? I would think that you might get better results out of a program designed to play audio from the command line. Like *gulp* alsaplayer or mplayer or similar. These are more likely to do what you want, which is 'play song and then exit', whereas calling xmms from the terminal will just open the app, at which point it will play what it was told to play, and then sit and wait for someone to close it.

---

### Post by JoseArmandoJeronymo on 2007-08-13
Thanks for the suggestion!

I've tried alsaplayer but could not make it run without a GUI. Mplayer is working without one but I haven't managed to control its volume, a requirement because the overall goal is to wake me and wife in the morning.

Will post as soon as I have success.

:)

---

### Post by bjarneh on 2007-08-13
if its started as a background process it can be killed with

kill $!

$! holds the pid of the last backgrond process, ie.

#!/bin/bash

xmms&
sleep 32
kill $!

# do something else....

---

### Post by dscherry on 2007-08-14
Try the 'play' command. (It's in the sox package, if you don't have it installed).

You can control the volume, and it's command line only!

Dan

---

### Post by JoseArmandoJeronymo on 2007-08-16
I'd like to thank all of you that gave me interesting suggestions which helped me to better understand what I wanted.

Currently the script is working fine like this:

```

#!/bin/bash

# Make sure we're not startling out of bed in the morning:
amixer set PCM Playback Volume 55%

# In the background play the music selected by musique.sh:
(
/home/prospero/scripts/musique.sh &
)
# Wait the duration of the music plus 5 seconds and...
sleep 280
# Kill player
killall xmms

# Say good morning in Italian:
/home/prospero/scripts/greeting_it.sh

# Then tune in Radio Vaticana:
gxine mms://212.77.1.198/rete1

exit 0
```

Musique.sh is:

```

#!/bin/bash
xmms -p "file:////home/prospero/musica/Italiana/Luna (Alessandro Safina).mp3"
exit 0

```

My next step is to make random selection of music and radio station and start a separate process that will kill the radio station after 15 minutes.

BTW, if anyone would like to use the computer as a alarm clock this way, make sure to turn off log-in sounds as they are not controlled by PCM volume settings. Wife almost had a heart attack last morning at the sound of Ubuntu Log In in full volume.

---

