---
title: "can you play ubuntu files w/ windows?"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by fignig on 2008-11-16
seeing if there's a way to play the music files that i have saved in Ubuntu, while i game on windows. 

recently i've been having a lot of trouble trying to install WOW on the ubuntu, but i just decided to dual boot, now that i have. and i'm wondering if there's a way to play my music files on windows?
b/c i don't want to have to download them again in windows just to be able to play them, i will if i have to. but i dont' want to, it's not my 1st choice.

---

### Post by sportscrazed2 on 2008-11-16
theres no such thing as windows files and ubuntu files all that matters is the codec

---

### Post by SunnyRabbiera on 2008-11-16
Right, a mp3 is a mp3.
Now if your music is in ogg vorbis you might have to install a codec or application for it.

---

### Post by InfectedWithDrew on 2008-11-16
The short answer: yes.

The long answer: yes, but first, you must set your music up so that your Windows OS can read them.  Windows, by default, does not support reading ext2 and ext3 filesystems.  You must install software in order to do that.  I googled it, and got this: [http://www.fs-driver.org/](http://www.fs-driver.org/)

(I'm assuming you placed your music on your Ubuntu partition.)

---

### Post by binbash on 2008-11-16
'seeing if there's a way to play the music files that i have saved in Ubuntu, while i game on windows. '

You can browse them but i dont know if you can pay them (i did not try)

Sample softwares :
[http://www.fs-driver.org/](http://www.fs-driver.org/)
[http://www.fs-driver.org/](http://www.fs-driver.org/)

MORE : 

[http://www.google.com/search?hl=en&q=access+ext3+on+windows&btnG=Google+Search&aq=f&oq=access+ext3+on+windows](http://www.google.com/search?hl=en&q=access+ext3+on+windows&btnG=Google+Search&aq=f&oq=access+ext3+on+windows)

---

### Post by oilchangeguy on 2008-11-16
> **fignig said:**
> seeing if there's a way to play the music files that i have saved in Ubuntu, while i game on windows. 

recently i've been having a lot of trouble trying to install WOW on the ubuntu, but i just decided to dual boot, now that i have. and i'm wondering if there's a way to play my music files on windows?
b/c i don't want to have to download them again in windows just to be able to play them, i will if i have to. but i dont' want to, it's not my 1st choice.

if you have ubuntu installed as a virtual machine in windows, yes. dual boot, no. unless in a dual boot setup windows is able to read ubuntu's file system.

---

### Post by snova on 2008-11-16
The answer in the end will be yes, but it'll take a few steps to get there.

First, what format do you save your music in?

Secondly, what kind of installation do you have? Dual-boot?

---

### Post by fignig on 2008-11-16
> **snova said:**
> The answer in the end will be yes, but it'll take a few steps to get there.

First, what format do you save your music in?

Secondly, what kind of installation do you have? Dual-boot?

1st: the format i have my music is .mp3

2nd: i have xp sp3 and ubuntu hardy 8.04

---

### Post by poebae on 2008-11-16
> **fignig said:**
> 1st: the format i have my music is .mp3

2nd: i have xp sp3 and ubuntu hardy 8.04
In that case you shouldn't have any problems playing files on both platforms.

As others have said, it all depends on the codec/file format.

---

### Post by inigomontoya on 2008-11-16
To clarify, you have to make Windows be able to "see" the Ubuntu partition.  To do that install the software from the link above and you'll be able to access the Ubuntu partition from within Windows as if it were another drive.

---

### Post by yaknowwat on 2008-11-16
The suggestions about making Windows able to see the Ubuntu parition are very bad.  Those drivers are known to corrupt ext3/2 partitons.

Personally I say make an OS Share Partition. ( FAT32 )

---

