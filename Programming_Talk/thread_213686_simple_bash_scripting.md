---
title: "simple bash scripting"
date: 2006-07-11
forum: Programming Talk
---

### Post by Paerez on 2006-07-11
Hey all. I can program in C++ and Java, so methods and conditionals and loops come naturally to me, so this is mainly a question of syntax.

I have a whole bunch of files in a directory, they are ".avi" files. I want to run ffmpeg on each one and convert them to an ".mpg" file. I already have the ffmpeg all set up, but only to take one file at a time. My bash script looks like this so far:

```
for file do
  echo $file
#  newname=???
  echo $newname
done

```

all I need to do is take file, which will be something like "movie.avi" and set newname to "movie.mpg" so that I can pass the two variables into my ffmpeg command.

I think I need sed or awk or grep or something but I dont know.

---

### Post by cwaldbieser on 2006-07-11
> **Paerez said:**
> Hey all. I can program in C++ and Java, so methods and conditionals and loops come naturally to me, so this is mainly a question of syntax.

I have a whole bunch of files in a directory, they are ".avi" files. I want to run ffmpeg on each one and convert them to an ".mpg" file. I already have the ffmpeg all set up, but only to take one file at a time. My bash script looks like this so far:

```
for file do
  echo $file
#  newname=???
  echo $newname
done

```

all I need to do is take file, which will be something like "movie.avi" and set newname to "movie.mpg" so that I can pass the two variables into my ffmpeg command.

I think I need sed or awk or grep or something but I dont know.

Try:
```

for file in filelist do
   echo "$file"
   newfile = $(echo "$file" | sed 's/.avi$/.mpg$/')
   echo "$newfile"
done

```

Of course, in bash, it might be simpler to do:
```

for file in filelist do
   echo "$file"
   echo "${file%.avi}.mpg"
done

```

---

### Post by Paerez on 2006-07-11
thanks a lot.

I had tried the sed version, but misused the "s and 's so it was coming out weird. I ended up using the second version but modified it to:
newname="${file%.avi}.mpg"

---

### Post by linuchsan on 2006-07-11
Why don't you use Tovid. You only have to type *.avi.

---

### Post by Paerez on 2006-07-11
I am using the script for a variety of encodings, like ipod format. And I am comfortable with ffmpeg. And I wanted to learn some bash :D

---

### Post by nafai77 on 2006-07-12
Another potential way to do this if you want to not rely on bashisms is this:

```

for file in filelist; do
    echo $file
    echo "$(basename $file .avi)".mpeg
done

```

I was also going to show you how to do it with find and xargs, but xargs doesn't allow you to do the manipulations that I need to do with basename.

---

### Post by Paerez on 2006-07-12
the problem with basename is that it strips the directory, which I would like to keep. I actually changed it to:
newname="${file%.???}.ipod.mp4"

to change any file to an mp4 extension. It works great now. I can pipe output to my script to:
find . -name '*.avi' | script.sh 
to make it work recursively, and put the new with the original. Sweet.

---

