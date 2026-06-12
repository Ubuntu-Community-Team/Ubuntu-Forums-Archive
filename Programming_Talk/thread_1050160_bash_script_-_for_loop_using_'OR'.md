---
title: "bash script - for loop using 'OR'"
date: 2009-01-25
forum: Programming Talk
---

### Post by mcai8sh4 on 2009-01-25
Hi,
I'm writing a little script to rename a directory of mp3's based on their id3 tags. ie. getting the name etc and renaming the file, thust getting rid of all my 01.mp3.. file names.

All's working but some files are name.mp3 and some name.MP3
In my for loop I have :
```
for FILE in *.mp3; do
```

is there a way to make it look at mp3 OR MP3?

I've come across this a few times but usually resorted to using 2 for loops - 1 one for lower case and one for caps. 

Thanks for your time.

-s

---

### Post by eightmillion on 2009-01-25
Try this:

> for FILE in *+(.mp3|.MP3); do

---

### Post by sisco311 on 2009-01-25
```
for FILE in *.mp3 *.MP3; do
```

---

### Post by sisco311 on 2009-01-25
> **eightmillion said:**
> Try this:

nice :)

how about:
```
for i in *.{mp3,MP3}; do echo $i; done
```
or
```
for i in *.{mp,MP}3; do echo $i; done
``` ;)

---

### Post by mcai8sh4 on 2009-01-25
Thanks for the quick help.
*+(.mp3|.MP3) <- throws up a syntax error
and
for FILE in *.mp3 *.MP3; <- throws up a funny message (fopen fail) when starting, but if I ignore them, it works after that. Some directories only contain uppercase, so I think the error is when looking for lower case.

Thanks for the help guys. I think I just need to include better error checking to avoid the errors.

---

### Post by mcai8sh4 on 2009-01-25
hehe, the suggestions are coming in quicker than I can type them :) Thanks.

The for i in *.{mp3,MP3}; does the same as for FILE in *.mp3 *.MP3;

I think it's the way I'm reading the id3 tags using... id3 - that the one throwing the error/funny thing.

Thanks once again.

---

### Post by eightmillion on 2009-01-25
There is another option. You can use "**shopt -s nocaseglob**" to turn off case sensitivity for filename globbing before you run "**for FILE in *.mp3; do**"

---

### Post by mcai8sh4 on 2009-01-25
> **eightmillion said:**
> There is another option. You can use "**shopt -s nocaseglob**" to turn off case sensitivity for filename globbing before you run "**for FILE in *.mp3; do**"

That seems to work. Whilst it sounded like what I wanted, I wasn't really sure what I was doing - so I suppose I shouldn't have just ran it, lucky you're a good guy! Thanks for that.

What ever I've done there (I'll have a read up in a min), is it a permanent change or will it only apply to that particular script?

Thanks for all the help.

---

### Post by sisco311 on 2009-01-25
> **mcai8sh4 said:**
> That seems to work. Whilst it sounded like what I wanted, I wasn't really sure what I was doing - so I suppose I shouldn't have just ran it, lucky you're a good guy! Thanks for that.

What ever I've done there (I'll have a read up in a min), is it a permanent change or will it only apply to that particular script?

Thanks for all the help.

Since the script is running in a sub-shell the changes will only effect that script.

You can check if a file exists with:
```
if [ -e $FILE ]; then
  blabla...
  bla
fi
```

---

### Post by eightmillion on 2009-01-25
> **mcai8sh4 said:**
> That seems to work. Whilst it sounded like what I wanted, I wasn't really sure what I was doing - so I suppose I shouldn't have just ran it, lucky you're a good guy! Thanks for that.

What ever I've done there (I'll have a read up in a min), is it a permanent change or will it only apply to that particular script?

Thanks for all the help.

No problem. If you're running it in a script, it will only apply to that script since it's running in a subshell. However, if you want to disable it, you can use "**shopt -u nocaseglob**". The -s and -u are for set and unset. For more info on shopt, you can use "**help shopt**".

---

### Post by mcai8sh4 on 2009-01-25
Thanks to everyone, you've all been a great help!

Much appreciated!

-s

---

