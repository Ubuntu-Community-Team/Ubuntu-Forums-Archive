---
title: "rsync option usage for unidirectional use ..."
date: 2011-12-18
forum: New to Ubuntu
---

### Post by clbeltz on 2011-12-18
Hey all,
I have a cheap USB MP3 player and when I plug it into my Ubuntu (10.04) machine, it sees it as a USB drive.  The player is used to store other files, so what I really want to do is select all mp3 files from my Music folder (/home/me/Music) and sync them to the device, but I am not interested (and do not want) to bring back any player files to the Music folder.

In effect:
a) when I add new tracks to /home/me/Music, they would sync (since they are mp3 files).
b) when I add new albums (tracks and image files), just the tracks would sync (the player does not handle art).
c) when my son adds an XLS file at school to the player, it would be ignored, and not copied to /home/me/Music.  Even an mp3 file should be ignored.  Nothing comes back from the player.

Is it as simple as:[FONT=Verdana]
[/FONT]
rsync -a /home/me/Music/*.mp3 /media/disk/Music

As I write this, and see the mountpoint for the player (it is really /media/disk/Music), I probably also need some pointers on getting linux to create a persistent mountpoint for this specific player.

Any/all help is truly appreciated,
Chris

---

### Post by Dennis N on 2011-12-18
rsync works one way only. source files are copied to destination replacing existing files of the same name based on the options you set. New files will be added. Other files in the destination folder will be left alone, unless you include the --delete option. To transfer anything in the other direction, source and destination have to be switched. There are many options, so study the man page.

(With a FAT formated flash drive as the destination, rsync with options -rt is probably sufficient. I also add --modify-window=1 to prevent unnecessary recopying of previously archived files).

---

