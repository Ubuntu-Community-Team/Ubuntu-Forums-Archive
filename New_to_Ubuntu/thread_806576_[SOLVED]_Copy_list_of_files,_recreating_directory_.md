---
title: "[SOLVED] Copy list of files, recreating directory structure"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by HyperHacker on 2008-05-25
I have a list of files (actually an M3U playlist) like this:
```
#EXTM3U
#EXTINF:7,[SPC] Donkey Kong Country - Opening Fanfare
Games/Donkey Kong Country/dkc 03 opening fanfare.ogg
#EXTINF:92,[MP3] 01 - Loop 1 Opening - .hack//game - OST CD 2 - .hack//GAME MUSIC Perfect Collection CD2
Anime/Dot-Hack/All Hack OSTs/dotHack Game Music - Perfect Collection/Disk 2/Loop1.mp3
#EXTINF:97,[MP3] 19 - Obsession (TV-Mix) - .hack//sign - OST1 -  Unknown Album
Anime/Dot-Hack/19-Obsession (TV-Mix).mp3
```
I want to copy all files in this list to an SD card, maintaining the directory structure (so create a "Games/Donkey Kong Country" directory on the card and copy the first file there, and so on). So far I've been able to use regular expressions to turn the list into a shell script:
```
cp -a /files/music/Games/Donkey\ Kong\ Country/dkc\ 03\ opening\ fanfare.ogg /media/PORN/Audio/Games/Donkey\ Kong\ Country/dkc\ 03\ opening\ fanfare.ogg
cp -a /files/music/Anime/Dot\-Hack/All\ Hack\ OSTs/dotHack\ Game\ Music\ \-\ Perfect\ Collection/Disk\ 2/Loop1.mp3 /media/PORN/Audio/Anime/Dot\-Hack/All\ Hack\ OSTs/dotHack\ Game\ Music\ \-\ Perfect\ Collection/Disk\ 2/Loop1.mp3
cp -a /files/music/Anime/Dot\-Hack/19\-Obsession\ \(TV\-Mix\).mp3 /media/PORN/Audio/Anime/Dot\-Hack/19\-Obsession\ \(TV\-Mix\).mp3
```
However, there doesn't seem to be any option for cp to create the destination directory if it doesn't exist. -r, -a and -f all don't do it; they just show the same message:
```
cp: cannot create regular file `/media/PORN/Audio/Games/Donkey Kong Country/dkc 03 opening fanfare.ogg': No such file or directory
```
Google says -a should do it, but it doesn't want to for me... :-/ Maybe there's a better way to do this? (Need to learn Python and write a script... :P)

---

### Post by sdennie on 2008-05-25
I would just use tar for this:

```

cd base_directory_of_stuff
tar cvf stuff.tar .
cd /location/of/sd/card
tar xvf base_directory_of_stuff/stuff.tar

```

I believe there is a way to use tar like this without the intermediate file by piping stuff but, I can't recall it off the top of my head.

---

### Post by h4mx0r on 2008-05-25
umm I just use mkdir /someplace/directory and cp /some/directory/*

---

### Post by HyperHacker on 2008-05-25
vor: I don't think that will work unless tar has an option to read a list of files. The files I want to copy are scattered over many directories and those directories have many other files that I don't want to copy.
The idea here is I have my music collection organized into directories, and I want to copy all the songs on this playlist to the SD card. But sometimes I want to play a specific song, so I want to keep the directory structure so I can easily find it on the player, instead of scrolling through a big list.
Ideally I'd just copy everything, but the card isn't big enough.

h4mx0r: I might be able to use regex to add a "mkdir -p" before each cp to create the directory. Thanks for the idea. :) (I thought of that before actually, but I didn't know mkdir had the -p option.)

[edit] Yeah, that did it. Bit of a hack, but eh. :P

---

### Post by warp99 on 2008-05-25
You would do it like this:

```

mkdir /media/PORN/Audio/
cd /files/music
cp -rv Games /media/PORN/Audio/
```
or
```

mkdir /media/PORN/Audio/
cd /files/music
cp -rv * /media/PORN/Audio
```
to copy **all** of the directories and not just the Games directory. The 'v' parameter is just verbose so you can see what is going on.

---

### Post by HyperHacker on 2008-05-25
That would still be copying every file, though. Anyway I managed to use another regex to add a "mkdir -p" to the script:
```
mkdir -p /media/PORN/Audio/Games/Donkey\ Kong\ Country; cp -u /files/music/Games/Donkey\ Kong\ Country/dkc\ 03\ opening\ fanfare.ogg /media/PORN/Audio/Games/Donkey\ Kong\ Country/dkc\ 03\ opening\ fanfare.ogg
mkdir -p /media/PORN/Audio/Anime/Dot\-Hack/All\ Hack\ OSTs/dotHack\ Game\ Music\ \-\ Perfect\ Collection/Disk\ 2; cp -u /files/music/Anime/Dot\-Hack/All\ Hack\ OSTs/dotHack\ Game\ Music\ \-\ Perfect\ Collection/Disk\ 2/Loop1.mp3 /media/PORN/Audio/Anime/Dot\-Hack/All\ Hack\ OSTs/dotHack\ Game\ Music\ \-\ Perfect\ Collection/Disk\ 2/Loop1.mp3
mkdir -p /media/PORN/Audio/Anime/Dot\-Hack; cp -u /files/music/Anime/Dot\-Hack/19\-Obsession\ \(TV\-Mix\).mp3 /media/PORN/Audio/Anime/Dot\-Hack/19\-Obsession\ \(TV\-Mix\).mp3
```

---

### Post by warp99 on 2008-05-25
You can use sed to remove the comments and empty lines like this.

```
sed '/ *#/d; /^ *$/d' extm3u.list > cleanlist.list
```
then add a backslash+space for the empty spaces:
```
sed 's/ /\\\ /g' cleanlist.list > final.list
```
then use xargs and cp command with the final.list as input:
```
xargs -IFILES cp -rv FILES /media/PORN/Audio < final.list
```

If you have additional garbage in you extm3u.list file you may need to run sed again to remove this.

---

