---
title: "Extracting Files from a Non-Zipped Folder"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by linuxguy049 on 2012-09-07
I'm not even sure if that's the right way to put it.

I've got 100+ folders from itunes (the good ole days!) which each contain a certain amount of songs. I want to bump all the songs up from the folders, and into the folder above, but it'll take me forever to do it manually. 

I'm doing it right now, but I'm just wondering for future reference: is there a command-line program for this?

---

### Post by androssofer on 2012-09-07
> **linuxguy049 said:**
> I'm not even sure if that's the right way to put it.

I've got 100+ folders from itunes (the good ole days!) which each contain a certain amount of songs. I want to bump all the songs up from the folders, and into the folder above, but it'll take me forever to do it manually. 

I'm doing it right now, but I'm just wondering for future reference: is there a command-line program for this?

i know a semi quick way.. thts simple.. does involve going into each folder via command line, but moves all the files in that folder for you. 

run this in the terminal:

```
mv *.mp3 /home/username/Music
```

would move all the .mpg files in the current folder to your Music folder.

you could probably write a small script to recursively go into each folder for you.. or someone might have already done this.. 

I don't have time otherwise I would..

**note: change username, to your own username. and changes .mpg to the file type you want to move..

---

### Post by sisco311 on 2012-09-07
```

cd path/to/dir
mv --backup=numbered -- */*.mp3 ./
```
*/*.mp3 matches every mp3 file in the subdirectories

---

### Post by linuxguy049 on 2012-09-07
> **sisco311 said:**
> ```

cd path/to/dir
mv --backup=numbered -- */*.mp3 ./
```*/*.mp3 matches every mp3 file in the subdirectories


What do all these options mean?

I'm just not sure what exactly you mean by it "matches every mp3 file in the subdirectories"


Thanks guys!:guitar:

---

