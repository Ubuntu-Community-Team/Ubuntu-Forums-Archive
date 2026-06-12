---
title: "Find -exec to make directories and hard links."
date: 2014-11-25
forum: Programming Talk
---

### Post by sotiris2 on 2014-11-25
I want to make a script to hard link the contents of a few folders f1 to f3 to a another folder or actually to folders named f1 to f3 inside that folder. I want to run grive on that folder so I get them all synced to google drive (but I prefer to acess them from their original folder for other purposes). I guess I could move them to the folder and put symlinks to them at their original places but for some reason I don't like it. 

So after a bit of testing with find I think the following would work:

1) cd to folder ( I 'll probably have them read line by line from a file) and run ```
 find . -type d -exec mkdir -p "/home/sotiris/Gdrive/$folder"{} \;
``` Where $folder would be just the directory name not it's full path ( put on $folder via parameter expansion before running find). Running find from each folder produces relative paths for {} which I need to make this work (I think trying to 'mold' absolute paths in find -exec would make it too complicated. I was thinking of having a *for* loop on the results of *find* instead of -*exec* but in the end this seems simpler). 
This  would create (new) subdirectories. 

2) Run ```
find . -type f -exec ln {} "/home/sotiris/Gdrive/$folder"{} \;
``` This would now link the files.

3)Loop back to one with a different folder (thinking of implementing as a while read < file)

4) cd to Gdrive folder and run grive.

Now after experimenting on some fake folders and file I think it should work. I would like someone more experienced one's opinion. I haven't done any test for existing files, I just let mkdir and ln fail on existing ones since there doesn't seem to be a problem. Should I ? Is it possible that something I haven't considered would lead to file loss?
Should I implement it in a different way? I did try simple *for* loops but I wasn't sure how to deal with an ambiguous amount of sub-folders, using find seems easier. 
Is the idea inherently bad (the whole linking idea)?  I 've run find  with an echo {} on the actual folders and it doesn't take much time ( I am not trying to sync huge amount of data ). I am thinking of an hourly / half-hourly cronjob.
I am aware that hardlinking will make files difficult to delete and may cause some problems (deleting one of them wouldn't delete the other) but I think I can deal with that.

---

### Post by ofnuts on 2014-11-25
I don't see much purpose in linking the files and/or subfolders... If you link ***/anywhere/folder*** as ***/home/sotiris/Gdrive/linkedfolder***(*), then any file or folder under ***/anywhere/folder***  (like ***/anywhere/folder/subfolder/somefile***)will show up under ***/home/sotiris/Gdrive/[I][B]linkedfolder*** [/B][/I](as ***/home/sotiris/Gdrive/[I][B]linkedfolder***[/B][/I]***/subfolder/somefile***).

(*) A soft link is likely better...

---

### Post by sotiris2 on 2014-11-25
Well grive's github claims that it does not support symlinks. And when I tested it it deleted the symlink, but it was rather due to the fact that a link to an already existing file doesn't appear to be new and grive simply deletes files that are not on the Gdrive and are older than the time grive last ran. A simple touch on the symbolic link after creating it solved the problem..

---

