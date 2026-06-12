---
title: "Disable Xscreensaver during video playing on Chrome"
date: 2016-01-28
forum: Programming Talk
---

### Post by mroussin51 on 2016-01-28
Greetings,

I am using Xscreensaver to display my 24,000 plus pictures as my screensaver. If there is a better option please chime in. The version of Ubuntu is 15.10 Desktop 64 bit. Thank you developers! It is extremely stable and does whatever I ask it to. I am using the google-chrome-stable browser. We watch Netflix and it just works. However, the screensaver comes on while watching. I spent some time looking into a solution to no avail. I initially looked into using Flash to disable it but the Flash is a part of Chrome with no unique PID. I decided to use the audio as so I wrote a shell script. I'm an absolute novice so be careful if you try this 

if pacmd list-sink-inputs | grep 'application.name = "Chrome"'; then...

The problem is that it Prints its output to the terminal. I am looking for a way to stop that. So when Chrome is outputting audio I write 12:00 hours to the "timeout". Actually, I am writing the whole file since I don't know how to parse the file and just write a single value. I am new and here to learn. I will post the script but not all the configuration files. You can get them from your computer and modify them accordingly. This script works quite well. I am concerned mainly with its output to the Terminal. I want to start it in the background at startup. Is that a problem? If so, what is the suggested fix. Also, as you can see I am writing the whole file instead of just the timeout parameter. How do I tell the script just to write to the line I need and stop output to the Terminal?

Here's the script, my first:

```
#!/bin/sh


# This is my trial script to learn how to read and write data to a file.


FILE="/home/kim/.xscreensaver" # The xscreensaver settings
FILE1="/home/kim/.xscreen5min" # 5 minutes to activate screensaver "timeout: 0:05:00"
FILE2="/home/kim/.xscreen12hour" # 12 hours setpoint watching netflix "timeout: 12:00:00"


while true; do
if pacmd list-sink-inputs | grep 'application.name = "Chrome"'; then 
# listens for audio on Chrome. I use chrome for netflix. Spotify for music.


cat <<EOM >$FILE # Erase .xscreensaver settings file
EOM


value= cat $FILE2 >> $FILE # write 12 hours to .xscreensave file during audio on Chrome. Indicative of video playing.
sleep 2m
else


cat <<EOM >$FILE # Erase .xscreensaver settings file
EOM


value= cat $FILE1 >> $FILE # No audio on Chrome. .xscreensaver set to 5min. No audio = no video we use chrome for video only
sleep 2m


fi
done
```

Like I said, it works! I know there is a better way and I have much knowledge to be gained.

Thanks for looking at this. I hope so can use it and that I may learn a better way. I tried to K.I.S.S and if it ain't broke don't fix it but I am sure with some direction I can get it better.

regards,

Mike

I did this so far. I have a lot to learn!

```
#!/bin/sh


# This is my trial script to learn how to read and write data to a file.


FILE="/home/kim/.xscreensaver" # The xscreensaver settings
FILE1="/home/kim/.xscreen5min" # 5 minutes to activate screensaver
FILE2="/home/kim/.xscreen12hour" # 12 hours setpoint watching netflix


while true; do


if pacmd list-sink-inputs | grep 'application.name = "Chrome"'; then 
# listens for audio on Chrome. I use chrome for netflix. Spotify for music.


cat /dev/null > $FILE # Erases .xscreensaver 
cat $FILE2 > $FILE # Writes .xscreen12hour to .xscreensaver


sleep 2m


else


cat /dev/null > $FILE # Erase .xscreensaver
cat $ $FILE1 > $FILE # Writes .xscreen5min to .xscreensaver


sleep 2m


fi
done
```

---

### Post by mroussin51 on 2016-01-29
The final test failed. When I went to bed Netflix was on. When the movie was over xscreensaver never activated. It was waiting for something to occur before reading .xscreensaver preferences. Also, when Netflix came on it was waiting for input from the keyboard or mouse. The reason it worked in preliminary tests is do to the fact I moved the mouse. Disregard the two scripts above. I found a man page for xscreensaver. I should have read it first. I will do more research up front in the future. Part of learning I guess. Here's a remastered script. Anyone with a better idea please chime in. Don't use this unless you understand it. I must disclaim that I am novice Linux user and a beginner at scripting. Use this at your own risk.

#!/bin/bash


# This script deactivates xscreensaver while there is audio output from Chrome


while true; do


if pacmd list-sink-inputs | grep 'application.name = "Chrome"' > /dev/null;  then # reads list-sink-inputs and looks for appliction.name="Chrome" If true Chrome is using the audio driver


xscreensaver-command -deactivate > /dev/null # If true this line is executed. It is the equivalent of input from mouse or key board. It restarts the counter Preventing xscreensaver from                                                                                         # activating screen saver


sleep 2m # Waits 2 minutes. You can make it more or less. If more make sure that xscreensver preference "Blank After" is greater or screensaver will become active before timer completes


fi


done

---

