---
title: "Shuffling, MP3 playing bash (or python) script"
date: 2008-08-12
forum: Programming Talk
---

### Post by rogier.de.groot on 2008-08-12
Since I'm not much of a bash-programmer, I need some advise for a pet project. I've got a server machine which runs both samba and apache. It's samba share has a folder full of MP3's in it (ordered with several levels of subdirectories). I know I can use mpg123 to play mp3's from the CLI, so I figure it should be possible to write a bash script that picks an mp3 file from my samba share at random, plays it using mpg123 and then repeats. But I don't know how to pick a random file using bash.
Ideally this little script would also set itself and child processes to run at low privilege so it won't interfere with apache on occassional peaks. Don't know how to do that either though.
I guess doing it in python might be a good alternative too, although I do believe the bash version would use less resources.

Anybody got some good suggestions?

---

### Post by aloshbennett on 2008-08-12
You could roughly do it like this
1. mount the samba share
2. get the list of files into an array
3. use $RANDOM (a function under bash) to generate a random number. It returns from 0 to 32767.
4. normalize it against the array indexes
5 happy listening with mpg123 :)

---

### Post by ghostdog74 on 2008-08-12
check the mpg123 help documentation and see if there are any shuffle options.
I believe something like this: mpg123 --shuffle --list
no need to create your own shuffle routine

---

