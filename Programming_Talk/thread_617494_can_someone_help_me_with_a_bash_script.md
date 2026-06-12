---
title: "can someone help me with a bash script?"
date: 2007-11-19
forum: Programming Talk
---

### Post by ice60 on 2007-11-19
hi, i made a bash script to put in a crontab that will delete files older then 7 days in ~/.thumbnails/normal but it stopped working. the directory now has over 17, 000 items and is 172.8MB

this is the script
```
find ~/.thumbnails/normal -type f -atime +7 -exec rm {} \;
```
can someone help me fix it?

BTW, i tried running this
```
rm .thumbnails/normal/*
```
but, got an error saying this 
```
bash: /bin/rm: Argument list too long
```

i'm trying to open it up in nautilus now lol. i gave up and closed it.

---

### Post by smartbei on 2007-11-19
well, you could if you want to delete the whole thing delete the folder and then bash wouldn't have to enumerate all of the files (and then recreate the folder). The scrpt worked for me, did you check the crontab entry?

---

### Post by ice60 on 2007-11-19
thanks for the help. i think the script is working, i don't understand why there are so many files though, i use thunar and xfce and the thumbnails are from nautilus i think.

i'm just going to change the crontab to this, without the normal directory so it works on the other directories
find ~/.thumbnails/ -type f -atime +7 -exec rm {} \;

the crontab ran today, thinking about it i remember watching the find command, but i thought it was that search program checking files, that's why i thought it wasn't working because nothing changed when i ran the command manaully lol

thanks for the help.

---

### Post by jasong on 2007-11-19
Since the other guys problem seems to be solved and his title is totally appropriate for my problem, I'm going to refrain from making a new thread(less clicking for searchers :) )

Anyway, I am somewhere between a semi-noob and a total noob as far as bash scripts and Linux commands are concerned.  I'm not asking for you guys to write the program, but good search terms and links are definitely appreciated.

I have a directory /home/jason/Desktop/dc/mprime .  This directory has some files, and then 4 sub-directories, numbered 1-4.  If any of these sub-directories suddenly get a file called results.txt , I want the computer to put an icon on the desktop at maximum size(it won't be there long, I just want to notice it as soon as possible) with the name IT'S PRIME!!!

Also, assuming it's between 10am and 9pm local time, I want the speakers to make a very noticeable noise.  SPECIFICALLY, THE SPEAKERS.  If it's motherboard beeps, my parents will probably turn off my computer in order to get it to stop, which means my computers will stop crunching my projects, but if it's the speakers, than they can just turn them down.

And lastly, what I think is the easist thing, though I've never done it.  I'd like to make it an hourly cronjob.  (hopefully right usage of the word)

thanks in advance!!!

---

### Post by volanin on 2007-11-20
Put the script below in ***/etc/cron.hourly***
Don't forget to make it executable with ***chmod 755 SCRIPTNAME***

```
#!/bin/bash

#
# Configuration
#
FILENAME='results.txt'
DIRECTORY='/home/jason/Desktop/dc/mprime'
SOUNDALARM='/home/jason/Desktop/dc/mprime/alarm.mp3'

#
# Script
#
if [[ `find "$DIRECTORY" -name "$FILENAME"` ]]; then
   zenity --info --text "Prime Found" &
   gst-launch-0.10 filesrc location="$SOUNDALARM" ! decodebin ! alsasink
fi
```

You can use any music or sound as alarm.
Also, forget about big icons in the desktop!
This script will pop-up a warning window for you, that will stay in the middle of your screen until you close it!
:)

[i]**Warning:** This script only works if you are using GNOME.
Also, it does NOT check for the time. Turn your speakers off after 9pm!![/I]

---

