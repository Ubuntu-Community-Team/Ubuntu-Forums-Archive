---
title: "Let's make a program to sort files"
date: 2008-10-20
forum: Programming Talk
---

### Post by kingbilly on 2008-10-20
I want to make a program to sort files by type and put them into folders.
Here is why.

If your like me, you may prefer to keep files organized in folders like /home/user/Video, /home/user/Music, /home/user/Pictures, etc. 

You also might like to have your favorite programs, like amarok, monitor certain folders for music.  

Files traverse my computer like Times Square, New York during the day.  As soon as I get home I have Firefox downloading powerpoint slides for school.  I plug in my flash drive to copy the schedule from work onto my computer.  Torrent files are downloading and I keep extracting zip files to see if any themes from gnome-look.org will look nice on my laptop upstairs. You can quickly see that from multitasking I will have a number of files out of place in just a short amount of time. 

Now,
The first problem with these out of place files is that they are located in many places.  When you have Firefox, Transmission, GTK-Gnutella, and other applications, each program is saving files to different locations.  (Not to mention anything I might have placed on the desktop to work on.)  

So we could use a script/program to sort all these files.

A user could choose to have all these incoming files moved to a new location, say /home/user/sort and then have the script perform actions on the files in that directory.


But I would prefer to create a more granular setup that checks the locations specified by the user, and then performs a selected action.
Like
1)check /home/user/Desktop and move mp3's to /home/user/documents
2)check /home/user/gtk-gnutella/complete and move mp3's to /home/user/music

Perhaps in this above situation a user typically downloads mp3's from a website to use for a specific purpose, like a podcast from a game developer. Perhaps they also typically use gtk-gnutella to find new music, and have their favorite music player check /home/user/music.  It this situation the music mp3 would go to the music folder while the mp3 downloaded to the desktop (through firefox, or anywhere) would be moved to the ~/documents folder.


I've started just writing some scripts in bash. I have called the project Docusync.

What I would like to do is eventually create some gui to make this easier for my friends.  Even if it was zenity and it asked them to input the where and what until they were satisfied.

docusync.sh
```
#!/bin/bash
#
# Docusync 
# A simple script to sort your files by extention.
#
# Author - Rich Boos
# http://sadface for more information 
# or view the README.txt file
# 
# This will be released under the GPL.
# 
#
echo "Docusync Version 0.1"
echo "To configure Docusync run docusync.conf or edit it manually."
#
#
# First we check for the configuration file
if [ -f ./docusync.conf ]
  then
    echo "Configuration file found: Proceeding..."
./docusync.conf 
echo "Document Synconization Complete."
else # If Configuration file was not found
 echo "Configuration file not found, check README.txt"
fi #End of IF for configuration file existance.
```

```
# Docusync Configuration File
# Needed by docusync.sh - Both must be placed in same directory
# unless you edit docusync.sh yourself :) 
# It is more like a list than a configuration,
# but it allows easy editing
#
#if file in download/*.mp3; then
if [ ! -f "download/*.mp3" ];
#for file in $(find download/ -type f -name "*.mp3"); do
then
 mv -v download/*.mp3 ~/Projects/Docusync/music/
# done;
else
echo "No mp3 files found"
fi

```

[http://sadface](http://sadface) :
Google for VpsVille, my hosting company(or person:confused:) had hardware failure that also affected the backup servers.  So my site is down otherwise I would have this posted there too.

If anyone has ideas or can take my ideas out of bash into something more useful, just reply! :)

---

### Post by ghostdog74 on 2008-10-20
you should also check out the find command

also why did you design you config file as a shell script?s A config file  should be a config file where you can set parameters that gets parsed by the main script.

---

### Post by sethvath on 2008-10-20
I see how useful it might be to some, especially me since I download everything to my home folder and it gets cluttered in a day or two. 

Some ideas:
1. daily sort of image files (jpg, png, cr2, nef etc) and move them to the pictures folder
2. sort audio files and move to music folder
3. rest are sorted and moved to documents folder

That way you get a clean Home folder at the end of each day or whenever you choose via crontab. Think GTD. 

On my mac, my music files are automatically sorted by how many times it was last played rather than album and artist. 4 weeks of not being played they get moved to "My collection" folder rather than "Playlist".

---

### Post by rye_ on 2008-10-21
certainly with gnome/nautilus adding scripts is very easy.
just stick the scripts in ~/gnome2/nautilus-scripts, restart nautilus and see your script available in nautilus write click menu.

I see no reason  why you couldn't have one script doing the work, and another scipt used to set program variables which stores config data in a third file in nautilus-scripts.

Ryan

---

### Post by rye_ on 2008-10-21
EDIT Script finished below

---

### Post by rye_ on 2008-10-22
Edit: Script finished below

---

### Post by rye_ on 2008-10-22
woohoo done!

3 files;
1) .FileSort.conf
   Place in ~/
   Define file types and file name keywords by which you would like to sort the files in whatever you current nautilus or thunar directory is   
   I'm not a kde user so I'me not sure if dolphin et al runs scripts) 

2)FileSort.rb
   Does the actual sorting.  if a nautilus user place in ~/.gnome2/nautilus-
   scripts.  Can be accessed from nautilus in the right-click menu

3)Edit_FileSort_conf.rb
   for nautilus, place in ~/.gnome2/nautilus
   A quick way of getting access to .FileSort.conf to define keywords/ file types.  Assumes gedit is on you machine

---

### Post by kingbilly on 2008-10-22
Yes I forgot to add that it would be useful for some to make this script run automatically daily, weekly, etc.  Or if you just did alot of moving around of files you run it on the spot with a launcher

---

### Post by kingbilly on 2008-10-22
> **rye_ said:**
> woohoo done!

3 files;
1) .FileSort.conf
   Place in ~/
   Define file types and file name keywords by which you would like to sort the files in whatever you current nautilus or thunar directory is   
   I'm not a kde user so I'me not sure if dolphin et al runs scripts) 

2)FileSort.rb
   Does the actual sorting.  if a nautilus user place in ~/.gnome2/nautilus-
   scripts.  Can be accessed from nautilus in the right-click menu

3)Edit_FileSort_conf.rb
   for nautilus, place in ~/.gnome2/nautilus
   A quick way of getting access to .FileSort.conf to define keywords/ file types.  Assumes gedit is on you machine

Haven't checked the FileSort_conf.rb yet, looks good so far :)

---

### Post by kingbilly on 2008-10-22
> **sethvath said:**
> I see how useful it might be to some, especially me since I download everything to my home folder and it gets cluttered in a day or two. 

Some ideas:
1. daily sort of image files (jpg, png, cr2, nef etc) and move them to the pictures folder
2. sort audio files and move to music folder
3. rest are sorted and moved to documents folder

That way you get a clean Home folder at the end of each day or whenever you choose via crontab. Think GTD. 

On my mac, my music files are automatically sorted by how many times it was last played rather than album and artist. 4 weeks of not being played they get moved to "My collection" folder rather than "Playlist".

I like all of these ideas :guitar:

---

### Post by rye_ on 2008-10-23
hi,

nice to hear from you!
I'm pretty happy about about the script, let me know if you have any thoughts/ criticims and I'll see what I can do.

Ryan

---

