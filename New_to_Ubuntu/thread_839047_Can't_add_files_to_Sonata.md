---
title: "Can't add files to Sonata"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by weed-n-linux on 2008-06-24
Hi,
i just installed Sonata , and i don't know how to add any MP3 files to it,i would only like to use it as a Local player (no Lan , no nothing ..). i've seen a screenshot of it in somebody's pc , and i noticed that i don't get all the options when i right-click somewhere in the Library tab. I have nothing such as Add files or anything , just this:
______________
Update Library
Repeat
Shuffle
______________
Connection >
Preferences
About...
Quit
______________

I was wondering if this is a common error , or is it EVEN an error, may be there's just some settings i have to consider .
Thanks in advance :)

---

### Post by iaculallad on 2008-06-24
Try referring to this [thread]("http://ubuntuforums.org/showthread.php?t=732881"). Similar query regarding how to open of mp3 files with Sonata.

---

### Post by whitethorn on 2008-06-24
Hi, Sonata is a client program that uses MPD to play music.  It pretty much tells MPD what to play and in what order. To add new songs to the library, you have to update your MPD database.  There's an option in preferences to tell it to update the database when it starts up.  You just have to set up the location for your music folder in you /etc/mpd.conf file.  

Just type

gksudo gedit /etc/mpd.conf

and you can now edit the mpd.conf file.  If you have more than one folder where you have music in, then you have to add symlinks to the other ones.  I pretty much have my conf file looking in my /home/Music folder and in there I have a symlink pointing at my external harddrive.  

Go here 

[http://mpd.wikia.com/wiki/Using_Multiple_Directories_Under_Parent](http://mpd.wikia.com/wiki/Using_Multiple_Directories_Under_Parent)

for an explanation.  Hope this helps if you need more help setting up MPD + Sonata just msg me.

---

