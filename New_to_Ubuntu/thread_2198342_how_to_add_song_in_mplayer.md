---
title: "how to add song in mplayer"
date: 2014-01-08
forum: New to Ubuntu
---

### Post by Hasan55 on 2014-01-08
hey guys plz help me..........................


Recently i have installed mplayer because of playing vedio in terminal.......but when i  
command in TERMINAL like as.........

mplayer /home/ruhul/Videos/.avi

then only one avi formate videos playing but other videos which are also AVI formate remain in the same folder
not playing EVEN IF I DON'T KEEP ANY VIDEO FILE IN MY (Videos) FOLDER THEN ONLY
SAME VIDEO IS PLAY BY THE ABOVE COMMAND  ............why????????????????????

how to (add ) videos in mplayer playlist or play all videos only one command on the 
same folder ............................plz give me suggestion !!.

I AM WAITING FOR YOUR KIND REPLY..................

---

### Post by mc4man on 2014-01-08
it would be 
mplayer /home/ruhul/Videos/*.avi

or create a playlist file (.pls
In that case enter each video on a separate line, best to full path, spaces in file names don't matter nor do any internal " or ' or whatever, just the real actual name

made a quick playlist to example different type filenames & paths
> /home/doug/Videos/FlashXX04Ei2a
/home/doug/Videos/Youtube/Rihanna - Stay (Live on SNL) ft. Mikky Ekko.mp4
/home/doug/Music/I'll Be Around.opus
/home/doug/Music/10 - Here Comes the Sun - Richie Havens.mp3
/home/doug/Music/mp3-1/Crusaders - Way Back Home.mp3

Then basic mplayer command is-  (where 'whatever' is whatever you named the playlist
mplayer -playlist /path/to/whatever.pls

You can add parameters to the mplayer command, video ones would be ignored if playing an audio only file, ect.

---

