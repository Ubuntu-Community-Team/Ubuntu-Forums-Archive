---
title: "Bash Script To Copy Files With Respective Paths"
date: 2007-10-27
forum: Programming Talk
---

### Post by nfox on 2007-10-27
Hi, thanks in advance for any help. I've been looking at moving my files around to another partition since my stuff is scattered throughout my hard drives. I've seen a lot of similar scripts but nothing tailored to what I need. 

I need to move files of a given type to a dedicated folder, nested within a folder that matches the original folder it was in:

(ex:) ~/music/foo/bar.mp3 needs to move to /media/hole/music/foo/bar.mp3

So I have a list of the files:
```
cd / && locate *.mp3 > ~/musics.txt
```

The code I was working with is:
```
#!/bin/bash  
filelist='~/musics.txt'  
copylocation='/media/music'
for files in `cat $filelist`;
do echo cp -avf $files $copylocation$files;
done  
```

My problem is first I need to wrap the spaces for the file list and I don't think I can just put
```
do echo cp -avf $files[COLOR="Red"] "[/COLOR] $copylocation$files[COLOR="Red"] "[/COLOR]  ;
```

and also I don't know how I can make a folder at the destination with the folder name that the original file is in. (I don't want 2 track01.mp3's in the same directory, I need them in the folders with the name of the cd.)

---

### Post by slavik on 2007-10-27
look into using tar :)

---

### Post by ghostdog74 on 2007-10-27
```

find / -type f -name "*.mp3" -print | xargs -i cp "{}" $copylocation

```

---

### Post by nfox on 2007-11-04
You suggested:
```
find / -type f -name "*.mp3" -print | xargs -i cp "{}" $copylocation
```

I see the $copylocation variable so I assume I add this to my code so far. This looks like a one-liner to do it all so do I declare $copylocation first?

To rephrase my issue, I have multiple partions (sda1-3, sdb1-2) and there are movies, songs and more. So I need something universal to move them to a dedicated folder on a partition. The catch is that I need the parent folder the file is in copied to the destination. I don't want all of the files in one big folder. I need a "move up a folder and copy whatever name it is with all of the files in it" thing going on.

Something to this effect:
```
$where = /media/sdb2/music/
cd / && locate *.mp3 > whichfiles.txt
for $i in $files do cd ../ && mv -R [COLOR="Red"]"the parent folder"[/COLOR] $where
```

So for example:
~/Nas/track1.mp3 moves to /media/sdb2/music/Nas/track1.mp3

---

