---
title: "How to create folders automatically - scripted solution"
date: 2016-06-29
forum: Programming Talk
---

### Post by seanbw2 on 2016-06-29
I have a folder and sub folders and massive numbers of files as follows:


```
Folder  called Movies
Sub Folder called "009 - A bad Wolf"
Files called  " 009  A bad Wolf.avi"
Files  called  " 009  A bad Wolf.txt"
Files  called  " 009 - A bad Wold.nfo"
Sub folder   A damn Good Film
Files          >  A Very good Film .mp4
Files          >  A very good Film .nfo
Files          > A Very good Film.txt
Files          > American Babe -Estelle Feat Kan Wass.mkv
Files          > American Babe -Estelle Feat Kan Wass.nfo
Files          > American Babe -Estelle Feat Kan Wass-poster.jpg
Files          > American.History.X.1998.Bluray.1080p.DTS-HD-7.1.x264-Grym
Sub Folder     > Baste - taste
.
.
Files          > Baa Baa Sheep.ogg
Files          > Baa Baa Sheep.nfo
Files          > Baa Baa Sheep.txt
.
.
Files          > Saa Baa Sheep.mp3
Files          > Saa Baa Sheep.nfo
.
Files          > Zaa Baa Sheep.flv
Files          > Zaa Baa Sheep-poster.jpg
Files          > Zaa Baa Sheep.nfo
Files          > Zaa Baa Sheep.txt
How can I get each similar set of files into individual directories without going through one by one? There are 1075 files and sub folders in the sub folder and 6 file in the main folder + the sub folder I am totally out of my depth. I know I have to use find and exec but how to create the directory with matching names? i.e. It should be like this:


Folder > Movies
Sub Folder > 009 - A bad Wolf with the following files in this sub folder:        
        Files          >  009 - A bad Wolf.avi
        Files          >  009 - A bad Wolf.txt
        Files          >  009 - A bad Wold.nfo
 Sub folder     >  A damn Good Film with all the files of same name in this sub folder
 Sub Folder     > A Very good Film with all these files in this sub folder :            Files          >  A Very good Film .mp4
         Files          >  A very good Film .nfo
         Files          > A Very good Film.txt
Sub Folder     > American Babe -Estelle Feat Kan Wass with all these files of same name in this sub folder:
         Files          > American Babe -Estelle Feat Kan Wass.mkv
         Files          > American Babe -Estelle Feat Kan Wass.nfo
         Files          > American Babe -Estelle Feat Kan Wass-poster.jpg
Sub Folder     > American.History.X.1998.Bluray.1080p.DTS-HD with files of same name in this  sub folder:
          Files         > American.History.X.1998.Bluray.1080p.DTS-HD-7.1.x264-Grym
Sub Folder     > Baste - taste as above with files of same names in this sub folder
.
.
Sub Folder     > Baa Baa Sheep with files of same name in this sub folder:
       Files          > Baa Baa Sheep.ogg
       Files          > Baa Baa Sheep.nfo
       Files          > Baa Baa Sheep.txt
.
Sub Folder     > Saa Baa Sheep with files of same name in this sub folder:
       Files          > Saa Baa Sheep.mp3
       Files          > Saa Baa Sheep.nfo
.
Sub Folder     > Zaa Baa Sheep with files of same name in this sub folder:
       Files          > Zaa Baa Sheep.flv
       Files          > Zaa Baa Sheep-poster.jpg
       Files          > Zaa Baa Sheep.nfo
       Files          > Zaa Baa Sheep.txt
```

Because of the number of files 1075+, a manual solution is not realistic. A scripted solution will be preferable for instance I know it will be something like this:
find . \( -name "*.mp4" -o -name ".avi" -o -name ".mkv" -o -name ".ogg*  -o -name-poster ".jpg"\)  but my abilities here are non existent and I am not even sure that I need the extensions as it is the common names that need to be grouped into a sub folder each.
There is a maximum of four  files names per set and most are three file names so this potentially gives me 250+ sub folders. Where there are four files, the fourth is usually a  poster that terminates in a jpg. 
My question is :
How can I use a find + exec or xargs script to go through this list of files and group each set of similar names and then create a sub folder for each group in a destination directory?
Can any linux/bash ninja assist?
thanks

---

