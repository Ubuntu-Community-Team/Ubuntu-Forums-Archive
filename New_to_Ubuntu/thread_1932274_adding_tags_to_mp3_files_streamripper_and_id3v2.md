---
title: "adding tags to mp3 files: streamripper and id3v2"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by Old Jimma on 2012-02-27
Hi Ubuntu Bretheren and Sisteren:

[COLOR="Red"]**I want to add id3v2 tags to mp3 files that I've ripped from a radio station.**[/COLOR]

:guitar:

I'm using streamripper to record a few songs now and then **(for my own educational purposes and not commerical, only)** from a wonderful jazz radio station.

O:)

I need to listen to those songs on my mp3 player (a very cool and cheap Sansa Clip Zip), because it is the only device I have for listening to music (No kidding. I don't have a stereo - I got no money!)

The Clip Zip seems to want id3v2 tags on all files in order to recognize them and list them on its system to be playable.

streamripper enables me to rip the id2v2 tags of each song I rip from the radio station. I use the following code:

[PHP]
NOW=$(date +"%y-%m-%d")
streamripper "radio stream URL" -d "/home/dufus/Music/jazz/todays lesson - $NOW" --with-id3v1  -s  -l 1200
[/PHP]

streamripper records each of ripped the songs to the directory 
[PHP]
/home/dufus/Music/jazz/todays lesson - $NOW
[/PHP]

[COLOR="Red"]**Each of the ripped songs have a title and artist tag, but no album tag.**[/COLOR]

I want to assign "todays lesson - $NOW" as the album tag to each of those ripped files... automatically without dealing with easytag.

There seems to be a thread on modifying tags of [COLOR="DarkGreen"]**flac**[/COLOR] files: see

[http:**[COLOR="DarkGreen"]//ubuntuforums.org/archive/index.php/t-781441.htm[/COLOR]**l]("http://ubuntuforums.org/archive/index.php/t-781441.html")

[COLOR="Red"][B]How to I assign "todays lesson - $NOW" as the album tag to each of those mp3 files in an automatic way with code that follows the streamripper command?
[/B][/COLOR]

Thank you! ):P

---

