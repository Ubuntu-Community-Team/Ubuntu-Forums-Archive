---
title: "[SOLVED] script help please"
date: 2008-11-06
forum: Programming Talk
---

### Post by DTPhantom on 2008-11-06
I'm not sure if this is the right area to post in so my appologies if it isn't, but I was hoping somebody show me how to make a script.

What I want to do is go through my /Music folder and all of its subdirectories looking for any folder.jpg, I want every folder.jpg to be copied and renamed cover.jpg so each folder contains both of them.  My music collection was orginized on my windows machine so every album has a folder.jpg but I've notice that most media players look for cover.jpg and I'd rather not go through and create that by hand.  Any help is appreciated.

---

### Post by unutbu on 2008-11-06
```
#!/bin/sh
find . -name 'folder.jpg' -execdir cp {} cover.jpg \;
```
Save this in a file called cp_covers (or whatever you like).

Put the script in a directory which is in your PATH. (See [http://ubuntuforums.org/showpost.php?p=5953944&postcount=2](http://ubuntuforums.org/showpost.php?p=5953944&postcount=2)).

Make it executable:
```
chmod +x cp_covers
```
Run it like this:
```

cd /top/level/directory # change this to the appropriate directory
cp_covers

```

---

### Post by DTPhantom on 2008-11-06
thanks

---

### Post by DTPhantom on 2008-11-06
ok I tried that a couple of times now but it didn't work at all.

---

### Post by raf_kig on 2008-11-06
The script works fine, though to make things less complicated just
cd to your music directory and do

```
find . -name 'folder.jpg' -execdir cp {} cover.jpg \;
```

That is, assuming your really mean paths like music/someartist/folder.jpg and not music/someartist/someartist.jpg
if the latter is the case the 'script' won't work

Regards

raf

---

### Post by DTPhantom on 2008-11-06
> **raf_kig said:**
> The script works fine, though to make things less complicated just
cd to your music directory and do

```
find . -name 'folder.jpg' -execdir cp {} cover.jpg \;
```

That is, assuming your really mean paths like music/someartist/folder.jpg and not music/someartist/someartist.jpg
if the latter is the case the 'script' won't work

Regards

raf

no that didn't work either.  the path of my music would look like this /Music/artist/album/file every album folder has all of that albums tracks and of course folder.jpg and yes each picture is named folder.jpg
When I run that script it sits for a bit and seems like its working I can see my possessor use spiking but nothing gets changed.

---

### Post by DTPhantom on 2008-11-06
ok it did work that was my fault.  I forgot in linux folder.jpg and Folder.jpg are different.  All of mine were capitalized and that script had lowercase so I just had to change that.  Thanks again.

---

