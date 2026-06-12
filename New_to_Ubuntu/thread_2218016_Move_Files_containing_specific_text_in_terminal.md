---
title: "Move Files containing specific text in terminal"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by adam17 on 2014-04-19
Hi, I am able to move files around from one place to  another in the terminal, however I have a massive collection of audio files that I would like to sort and move by the album title. 

for example: my file names in the music folder consist of - Artist Album Trk# Title

In the terminal I imagine the command would look something like this:

sudo mv /home/user/Music/*Album        /home/user/Music/Album\ Title

I know this doesnt work but could someone please help it would make the whole process a lot easier.

Thanks.

---

### Post by steeldriver on 2014-04-19
Are you trying to move them to a different directory location, or rename them? Are the files all in one directory, or in subdirectories?

It would help if you gave some specific examples.

---

### Post by adam17 on 2014-04-19
Hi Sorry,

Right I have files for example 9 files: file album-afi1.mp3 album-afi2.mp3 album-afi3.mp3 album-bfs1.mp3 album-bfs2.mp3 album-bfs3.mp3 album-cod1.mp3 album-cod2.mp3 album-cod3.mp3

I want to move files album-afi1.mp3 album-afi2.mp3 album-afi3.mp3 to folder afi

Then move files album-bfs1,2&3.mp3 to folder bfs

album-cod1,2,3.mp3 to folder cod

ect.

so if files album-afi1.mp3 album-afi2.mp3 album-afi3.mp3 album-bfs1.mp3  album-bfs2.mp3 album-bfs3.mp3 album-cod1.mp3 album-cod2.mp3  album-cod3.mp3 are in /home/adam/Music/All

and I want to move just the files that contain afi from all to /home/adam/Music/AFI  

the command I tried was sudo mv /home/adam/Music/All/*afi*               /home/adam/Music/AFI
                                                 move all containing afi           to              folder called AFI

hope this make sense.

Thanks

---

### Post by steeldriver on 2014-04-19
The ***-t target*** form of the mv command is handy for situations like this  where you want to move multiple source files to one destination.
```

       -t, --target-directory=DIRECTORY
              move all SOURCE arguments into DIRECTORY

```

If the target directories already exist, you should be able to do something like

```

mv -t /home/adam/Music/AFI/ /home/adam/Music/All/*afi*

```

or (if you want to restrict the match more precisely)
```

mv -t /home/adam/Music/AFI/ /home/adam/Music/All/album-afi*.mp3

```
or even (to match only names that have one or more digits after the afi)
```

mv -t /home/adam/Music/AFI/ /home/adam/Music/All/album-afi+([0-9]).mp3

```

and so on. If the directories don't already exist, there are ways of generating them progamatically (i.e. by chopping up the filenames) but that's a bit more complicated.

EDIT: and no need to use sudo if the files and target directories are under your own home dir

---

### Post by adam17 on 2014-04-19
Thanks, I think I understand.

Why does this method apear to be in reverse?

When moving files previously I have used the mv /existing/file.to /new/location
where as your method seems to be the reverse.

is there a difference?

is it to do with the target directory bit at the start?

thanks

---

### Post by llamabr on 2014-04-19
Also, notice that it's unlikely that you must begin this command with sudo.  Unless you know why you should, we'll probably advise against it.

---

### Post by Vaphell on 2014-04-20
> **adam17 said:**
> Thanks, I think I understand.

Why does this method apear to be in reverse?

When moving files previously I have used the mv /existing/file.to /new/location
where as your method seems to be the reverse.

is there a difference?

is it to do with the target directory bit at the start?

thanks

it should work if you switch places but the common convention is -options first (*-t dir* here), arbitrary number of items to process at the end. That makes it easy to determine at a glance what the command is supposed to do. *"A-ha! -t dir, so it gathers a bunch of files and moves them in bulk at once to dir!".*
Options often introduce huge differences and having to look for switches all over the place, potentially even at the end, would be a massive pain.

---

### Post by adam17 on 2014-04-21
Thanks for the help.

---

