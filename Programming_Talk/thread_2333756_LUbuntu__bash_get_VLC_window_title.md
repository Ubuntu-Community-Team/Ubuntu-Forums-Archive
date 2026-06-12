---
title: "LUbuntu / bash get VLC window title"
date: 2016-08-12
forum: Programming Talk
---

### Post by nhenry2 on 2016-08-12
Hello,   I upgrade from Lutuntu 14.04 to 16.04 yesterday and one script does not run properly now.  Previously, I make a script to extract the window title of VLC (to show the title of the current track on a webradio), but since the upgrade it doesn't work.  The command line used to extract the data is : ```
line=$(exec xlsclients -l | grep "VLC" | cut -c -9 --complement | cut -d "-" -f 1-2)
``` ```
# first list all windows open, filter for VLC, cut to have only the 2 firsts datas with "-" as separator
``` (and after, an "echo $line > file" to follow the data to one other session). After some checks, the command  xlsclients -l doesn't return the VLC window. What I need to change ? (I don't understand why the line return are ignored by the forum, sorry)

---

