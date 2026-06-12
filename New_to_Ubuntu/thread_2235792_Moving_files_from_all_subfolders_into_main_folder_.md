---
title: "Moving files from all subfolders into main folder (rsync?)"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by mike196 on 2014-07-22
Hello all,

I tried Googling a solution to this and it appears that rsync might be able to do what I want, but I don't know how to do it and I"m afraid to experiment out of fear of messing something up.  

Let's say I have a directory, /media, that has numerous other subdirectories (some of which may or may not have sudirectories of their own).  Is it possible to use rsync (or any other package/command) to essentially move every file from every subdirectory so that it's in /media and not it's original subdirectory?  

Thanks in advance for the help.

---

### Post by Dennis N on 2014-07-23
Done without rsync. The actual command that does this is in red. I used the tree command to show the file structure before and after running the command to prove it works. Substitute the folder containing the other folders and files for ~/work/test in the command, and cd to that folder before running.

```
dmn@Erica:~/work/test$ tree
.
&#9500;&#9472;&#9472; folder1
&#9474;   &#9492;&#9472;&#9472; file1
&#9492;&#9472;&#9472; folder2
    &#9500;&#9472;&#9472; file2
    &#9492;&#9472;&#9472; file3

2 directories, 3 files

dmn@Erica:~/work/test$ [COLOR="#FF0000"]find ./ -mindepth 2 -type f -exec mv {} ~/work/test \;[/COLOR]

dmn@Erica:~/work/test$ tree
.
&#9500;&#9472;&#9472; file1
&#9500;&#9472;&#9472; file2
&#9500;&#9472;&#9472; file3
&#9500;&#9472;&#9472; folder1
&#9492;&#9472;&#9472; folder2

2 directories, 3 files
```

All files are moved out of the subfolders and into the main folder.

I suggest you construct a test first before applying to the real files.

---

