---
title: "Batch renaming problem."
date: 2012-02-12
forum: New to Ubuntu
---

### Post by userub on 2012-02-12
Hello.

I want to use a batch rename program to remove the back part of a filename. I've tried GPrename, but the only option seems to be to delete from the front of the filename; Thunar, which does the job but auto-installs xfce which slows down the computer; and I have no idea how to use the rename function in the Terminal.

I've looked at numerous guides for the rename command, but those don't fully explain how the code works, so I am at a loss as to how to customize the code for the situation I want.

---

### Post by nothingspecial on 2012-02-12
Well the best thing would be to post an example of what the filenames look like now and what you want them to look like afterwards.

---

### Post by userub on 2012-02-12
The filenames currently look like this: youtubevideo(720p_H.264-AAC).mp4

I'd like to get them like this: youtubevideo.mp4

Thunar worked, by deleting characters from the right side of the name. The only problem was that it auto-installed xfce. GPrename only deletes from the left. And I don't know how to use the Rename command in the Terminal.

---

### Post by nothingspecial on 2012-02-13
This will remove brackets (parentheses) from file names and everything inbetween

```
rename -n 's/\(.*\)//g' *.mp4
```

the rename command uses delimiters, usually / in this form

```
rename /old_stuff/new_stuff/
```

The stuff in the first two /s gets changed to what's in the second two /s so old_stuff becomes new_stuff in that example.

( and ) are special characters so you have to put a \ infront of them.So inbetween the first two we have

\(    this means a literal ( Then we have
.*    . means any character and * means any number so any number of characters. Then we have 

\)    which is the close brackets. 

Then in between the second two /s is nothing. So that command will find parentheses and everything inbetween them and replace it with nothing.

The -n option in the command means don't actually rename the files just show how they would be renamed so you use it to test that you've got it right. If you do have it right then run it again without the -n

---

### Post by HiImTye on 2012-02-13
Nothingspecial, I always forget to use '.*' in a useful way and end up typing out the section I want to replace and then afterwards thinking 'why didn't I just use .*'

edit: perhaps you could help me with [my problem]("http://ubuntuforums.org/showthread.php?t=1922160")

---

