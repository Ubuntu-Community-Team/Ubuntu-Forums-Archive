---
title: "Blackberry Playlists Script from rhythmbox,amarok, or any playlist file"
date: 2010-12-01
forum: Programming Talk
---

### Post by excetara2 on 2010-12-01
I want to create a script that reads a playlist output from amarok or rhythmbox. Extracts the file information and copies the music files from the playlist to the blackberry. Then copies the playlist and runs sed to change it into a format the blackberry can read.

I know how to do the last part, but I'm not sure the best way to extract the file information out of a .m3u file.

Recommendations on writing this in bash or python. I don't know any of the os commands in python but am currently program in it quite extensively with numpy and scipy as matlab replacements so know it well.

Bash I think this should be relatively easy to do but not fluent with all the bash commands but copying the file and running sed on this would be easier. Worried about best way to extract the file information.

Cheers for any advice.

---

### Post by excetara2 on 2010-12-01
Wrote it in Python but post here in case anyone wants to use it to transfer music but would need to slightly modify for your setup. Mainly the blackberry path. This assumes all your music is in a Music folder. You export your playlists with rhythmbox to that music folder because then uses relative path names. That is just the way I have it now. May upgrade the script to provide more error checks and easier to use for others. Just give me a shout if you have a question.

---

### Post by excetara2 on 2010-12-01
```
import os
import shutil

def ensureDir(f):
    d = os.path.dirname(f)
    if not os.path.exists(d):
        os.makedirs(d)

namePlaylist = 'Acoust.m3u' #Works on spaces properly but need \' and \"
readPlay = open(namePlaylist, 'r')
dirCompMusic = '/mnt/data/Music/'
dirBlackMusic = '/media/424D-549E/BlackBerry/music/'
dirBlackPlaylist = '/media/424D-549E/BlackBerry/music/'
dirPlayNameBlack = 'file:///SDCard/BlackBerry/music'
if (os.path.exists(dirBlackMusic)):    
    writePlay = open(dirBlackMusic + namePlaylist, 'w')
    for line in readPlay:
        line = line.strip()
        if (line[0] == '#'):
            print "Skipping: " + line
        else:
            line = line.replace('"','\"')
            line = line.replace("'","\'")
            dirBlackPath = dirBlackMusic + line
            ensureDir(dirBlackPath)
            if (not os.path.isfile(dirBlackPath)):
                #ospath = line.replace(' ','\\ ')
                # os.system("cp %s %s" % (ospath, blackberrypath))
                shutil.copy(line, dirBlackPath)
            playNameBlack = line.replace(' ','%20')
            writePlay.write(playNameBlack + '\n')
    writePlay.close()
    readPlay.close()
else:
    print "Please Mount your Blackberry or Change dirBlackMusic to reflect music Folder"

```

---

