---
title: "Customized login greeting based on time of day"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by 7WYzhFx on 2013-10-18
Hello - I'd like Ubuntu to play an assortment of greetings based on the time of day that I login. So perhaps 2-3 different types of greetings for morning, afternoon and evening. 

"Good morning Robert" for example - I'm guessing these could be mp3 or .wav files?

Is there a way to create a script for this, or is there a personal assistant type of software that can manage the greetings and various tasks?

I am running the default install of Ubuntu 13.04 Desktop

Thanks for any help!


Robert

---

### Post by 7WYzhFx on 2013-10-22
Is this possible or not so much? audio login greetings based on time of day?

---

### Post by ant2 on 2013-10-22
Getting an audio file to play at start-up isn't going to be so hard, i.e. the old Ubuntu 'drums'. Also, I'd think there would be a way to write a script to play specific audio files based on the time which is run at start-up. However, this is currently beyond my abilities, but it sounds like a project should you feel the urge to turn your hand to programming.

[A place to start]("http://askubuntu.com/questions/198864/how-can-i-play-different-sounds-each-time-i-startup")

[More]("http://ubuntuforums.org/showthread.php?t=2137589")

---

### Post by drmrgd on 2013-10-23
I don't think this would be terribly difficult to do.  Since I'm on Kubuntu, I can't test this out.  But, I think the way to do it is to write a script that queries the current time with the **date** command, and then based on that result plays a predetermined sound file.  That script would then be called in the Startup Applications Preferences (according to that link..different on Kubuntu).

So, something along the lines of:

```

#!/bin/bash

now=$(date +%k)
path_to_sounds="path/to/files"
morning_sound="<sound_file>"
afternoon_sound="<sound_file>"
evening_sound="<evening_sound>"


if (( $now < 12 )); then
    # Play good morning sound
    cvlc --play-and-exit "$sound_files/$morning_sound"
elif (( $now < 18 )); then 
    # Play afternoon sound
    cvlc --play-and-exit "$sound_files/$afternoon_sound"
else
    #play evening sound
    cvlc --play-and-exit "$sound_files/$evening_sound"
fi

```

I chose to make the path and the sounds separate variables to make it easy to change in future, should you have different paths to the sounds.  Give that a shot and we can try to tweak it from there.

---

