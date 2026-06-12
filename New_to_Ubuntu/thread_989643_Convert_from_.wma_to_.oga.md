---
title: "Convert from .wma to .oga"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Soriano on 2008-11-21
Hi All,

I am currently thinking about changing all my media collection from .wma format to .oga.  I tried using Sound Converter but had severe issues.  The sound was coming out choppy when i tired going from .wma to .ogg.  So my friend suggested I try ffmpeg2theora.  I did and it worked flawlessly at converting one song.

Now I am new to bash and i know there is a better way to do this than one song at a time ( I have 9000 so thats not an option).

My folder Hierarchy is like below:

```

-My Music
|
--Band Name 1
||
|--Album 1
|||
||--Song 1
||--Song 2
||--Song 3
|--Album 2
| |
| --Song 1
| --Song 2
--Band Name 2
 |
 --Album 1
  |
  --Song 1
  --Song 2
ETC

``` 

Hope that makes sense.  So its Band names, then albums, then song files.

Now I don't really know how to make ffmpeg2theora do all this:

1.Keep song names and metadata
2.Perform this one all my music in one LONG process chain(all 9000 songs at once)
3.Keep Folder Hierarchy

If anyone has what they think is a better program to do this this that would be great or if anyone can direct me to a good tutorial that would also be fantastic.

Thanks!

---

### Post by linuxford on 2008-12-13
That sounds like a script to me .. it may be the opportunity to learn Perl or Bash programming.

---

### Post by vanadium on 2008-12-13
This can be done globally with the find command. If you supply the command that works for you to convert a single file from wma to oga, then we can show you how this could be automated for the entire collection using the find command with the -exec option. Keeping metadata might be a problem, though.

---

### Post by linuxford on 2008-12-13
Here's a couple of links that may be helpful:

[http://ubuntuforums.org/showthread.php?t=37793]("http://ubuntuforums.org/showthread.php?t=37793")

[http://ubuntu.wordpress.com/2005/09/29/wma-to-ogg-file-conversion/]("http://ubuntu.wordpress.com/2005/09/29/wma-to-ogg-file-conversion/")

---

### Post by linuxford on 2008-12-13
vanadium is right... that find command is powerful. I installed "sox" as suggested by:

[http://ubuntuforums.org/archive/index.php/t-305724.html](http://ubuntuforums.org/archive/index.php/t-305724.html)

 ```
 apt-get install sox
```

and then use the "find" command listed in the thread

```
  find . -name \*.wma -print -exec sox {} {}.ogg \;
```

but it doesn't look like sox supports .wma

---

### Post by linuxford on 2008-12-13
Instead of using "sox," there is a perl script called "pacpl" that you can get from here

[http://linuxappfinder.com/package/pacpl]("http://linuxappfinder.com/package/pacpl")

It uses ffmpeg so you can install that first

```
apt-get install ffmpeg
```

I am not sure but you may need to also download some decoders?

---

### Post by geirha on 2008-12-14
I did a little search in the repositories and found [dir2ogg](apt://dir2ogg). If you run it with ```
dir2ogg --convert-wma -r "/path/to/My Music"
``` It should recursively find and convert all wma files under "/path/to/My Music", putting the resulting ogg-file in the same directory as the wma-file. I don't know about wma's metadata, but I tested it on some mp3-files I have, and it did convert the id3 tags to ogg metadata.

---

