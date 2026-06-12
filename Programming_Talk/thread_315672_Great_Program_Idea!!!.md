---
title: "Great Program Idea!!!"
date: 2006-12-09
forum: Programming Talk
---

### Post by Fittersman on 2006-12-09
if someone could make a bitrate changer that would convert all files in a folder that have a bitrate higher than a user specified amount (say 128 for example) to that user specified amount.

because i have alot of music files in one folder and i dont want to be making some of them larger in size and waste time if their bitrate is already = to or lower than my target bitrate.

or if you could make a mp3 to wma converter that would also be awsome!

---

### Post by dutchmega on 2006-12-09
I'm not sure you can request programs here. Or else I would request a whatpulse-alternative (keystrokes counter, mouse distance etc). Hell, I would even code the website if someone else did the client.

Anyway:
sudo apt-get install soundconverter
But why the hell would you convert MP3's to WMA? You can't convert WMA without paying license-fee.

---

### Post by Fittersman on 2006-12-09
wma are smaller though right? (i didnt know that they had to be bought though)

my soundconverter doesnt work for some reason, stops at like 16% every time

---

### Post by kperkins on 2006-12-09
Commandline option--
Install ffmpeg (if it's not already installed) open a terminal, and do this:
```

ffmpeg -i SongToBeConverted.mp3 ConvertedSong.wma

```
Works good, but don't know why anyone would want to use the wma format, especially for music, since it gets it's lower file size by reducing the bitrate, and is a really bad proprietary format.

---

### Post by meng on 2006-12-09
You could do this with lame and nautilus-script.

---

### Post by Choad on 2006-12-09
im thinking ffmpeg and some kind of high level scripting language

if i had any experience in this i'd try and knock one out for you but i dont :(

one day ill be able to just write something like this off the top of my head in half an hour :D one day...

---

### Post by ghostdog74 on 2006-12-09
> **Fittersman said:**
> if someone could make a bitrate changer that would convert all files in a folder that have a bitrate higher than a user specified amount (say 128 for example) to that user specified amount.

because i have alot of music files in one folder and i dont want to be making some of them larger in size and waste time if their bitrate is already = to or lower than my target bitrate.

or if you could make a mp3 to wma converter that would also be awsome!

There are modules like that for Python, eg Pymedia or others
[http://pymedia.org/]("http://pymedia.org/") that caters to  audio/video operations.
you can have a look

---

### Post by Hairy_Palms on 2006-12-09
why not just convert them to ogg or aac? for sound quality wma is rubbish and not much smaller at all, the new aac+ codec sounds good even at 24kbps and ogg has the obvious benefit of being entirely free

---

### Post by slavik on 2006-12-09
> **Fittersman said:**
> wma are smaller though right? (i didnt know that they had to be bought though)

my soundconverter doesnt work for some reason, stops at like 16% every time
WMA uses the same algorithm MP3 uses.

OGG uses the same algorithm WMA and MP3 use but it has been argued that OGG can produce the same quality at a lower bitrate.

Notice that all 3 are lossy, meaning they cut out information from a file that you cannot get back to make the files smaller.

---

### Post by Fittersman on 2006-12-10
thanks for all the help but my songs are going to have to be either mp3 or wma (mp3 player) and one of my friends told me that wma is smaller, but after talking with you guys im not sure if its worth it anymore. 

for that ffmpeg thing is there a loop you can make to have it convert a whole folder?

---

### Post by Ramses de Norre on 2006-12-10
Put this in a file, chmod +x it, cd to the dir with the files and run sh this_file
```
#!/bin/sh
for i in *.mp3
do
    s=`echo "$i"|sed 's/\.mp3//g'`
    ffmpeg -i $i $s.wma
done
```

---

