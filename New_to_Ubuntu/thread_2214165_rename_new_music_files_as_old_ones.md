---
title: "rename new music files as old ones"
date: 2014-03-30
forum: New to Ubuntu
---

### Post by elang on 2014-03-30
I have a large music collection, and a good number of playlists that I have formed over the years.
All the music is neatly organised in a folder hierarchy. I use Banshee on Ubuntu, and Winamp on the odd day that I log into Windows.

I have managed to get my hands on higher quality versions of multiple albums, and would like to replace the low quality ones with these. But, that would mean that I have to build my playlists again from the scratch, as the new filenames will not be recognise in the old playlists. What is the best option for me to proceed?

One of the ways I thought would work was to see which filename of in new album is closest to the old one, and then rename it with the old filename (i.e. file named 01-Highway-to-Hell.mp3 in new album would be closest to highway_to_hell.mp3 in the old album). How do go about doing this renaming?

---

### Post by coldcritter64 on 2014-03-30
> **elang said:**
> I have a large music collection, and a good number of playlists that I have formed over the years.
All the music is neatly organised in a folder hierarchy. I use Banshee on Ubuntu, and Winamp on the odd day that I log into Windows.

I have managed to get my hands on higher quality versions of multiple albums, and would like to replace the low quality ones with these. But, that would mean that I have to build my playlists again from the scratch, as the new filenames will not be recognise in the old playlists. What is the best option for me to proceed?

One of the ways I thought would work was to see which filename of in new album is closest to the old one, and then rename it with the old filename (i.e. file named 01-Highway-to-Hell.mp3 in new album would be closest to highway_to_hell.mp3 in the old album). How do go about doing this renaming?

Look up **pyrenamer** for batch renaming with the next bit of code in terminal.
 
To check if your distro has it. If I recall correctly, it is in the Ubuntu repositories, I'm on Debian.
```
apt-cache policy pyrenamer
```

The result of that code in my Debian install is quoted next,
> ```
yeti:~ $ apt-cache policy pyrenamer
pyrenamer:
  Installed: 0.6.0-1.1
  Candidate: 0.6.0-1.1
  Version table:
 *** 0.6.0-1.1 0
        500 http://ftp.au.debian.org/debian/ wheezy/main amd64 Packages
        100 /var/lib/dpkg/status
                                                                      [  OK  ]
yeti:~ $
```


If available install it with,
```
sudo apt-get install pyrenamer
```

With it installed, use it to go into a folder with files you intend to replace, rename all existing music files to be replaced by adding a "Orig_" prefix to the start of the filename (or some additional tag like that) for all files you want to replace. Use the insert/delete tab in pyrenamer to add the "tag" to the name. Use the preview pane to ensure no surprises when batch renaming, check the final result BEFORE you apply batch changes to filenames.

Then place the new files to the same directory using the same name as the old version of the file had in its place, ensure the new filename is identical to the old one (still in the folder at this stage but with the "tag" added) including for case sensitivity, this should save you having to redo any playlists (the identical name as originally used with the playlist in the same location should make that work ok). 

All the old files having the same "tag" as a prefix will be together in the final folder with the new music, select and remove them to another location or send to trash as you wish.

Good luck with the renaming and the playlists,
coldcritter64

---

### Post by elang on 2014-04-05
> **coldcritter64 said:**
> 
Then place the new files to the same directory using the same name as the old version of the file had in its place, ensure the new filename is identical to the old one (still in the folder at this stage but with the "tag" added) including for case sensitivity, this should save you having to redo any playlists (the identical name as originally used with the playlist in the same location should make that work ok). 


If I have understood your solution correctly, I believe this process would have me rename the new files manually. Is there a way around that (there are about 1000 files in around 160 subfolders) ?

---

### Post by steeldriver on 2014-04-05
Automating it would only be feasible if you can define exactly how you intend to match the new and old file name - it may be obvious to you "which filename is closest to the old one" but can you write that down in a way that can be turned into an unambiguous algorithm?

---

### Post by elang on 2014-05-05
I believe lexical similarity should do the trick.
file named **01-Highway-to-Hell.mp3** in new album would be closest to **highway_to_hell.mp3** in the old album

---

