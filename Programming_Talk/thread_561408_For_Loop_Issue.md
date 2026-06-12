---
title: "For Loop Issue"
date: 2007-09-27
forum: Programming Talk
---

### Post by pjpalmq on 2007-09-27
Greetings!

I have a routine I use to convert wav files to mp3 files.

for i in *.wav; do
lame -h -b 192 "$i" "${i%.wav}.mp3"
rm "$i"
done

This works great one directory at a time.  I would like to start at my top level directory and have this routine work recursively.

Any ideas?

Many Thanks!
Peter

---

### Post by gnusci on 2007-09-27
You can use:

**> find . -type d**

to get the directories and then just use each directory.

---

### Post by pjpalmq on 2007-09-27
Please forgive me.....how would that look?  I understand your command returns all directories from this point down, but how would I incorporate this into my little script?

Thanks so much for the help!

Best,
Peter

---

### Post by yabbadabbadont on 2007-09-27
```
while read i
do
    lame -h -b 192 "$i" "${i%.wav}.mp3"
    rm "$i"
done < find /path/to/root/dir/of/music -type f -name "*.wav"

```
:D

(test it on a small test directory tree first)

---

### Post by pjpalmq on 2007-09-27
Okay, I tried this....but as you can see I get a syntax error.  

 $ while read i
> do
>     lame -h -b 192 "$i" "${i%.wav}.mp3"
>     rm "$i"
> done < find /home/pjpalmq/Music -type f -name "*.wav"
bash: syntax error near unexpected token `/home/pjpalmq/Music'

Thanks!
Still Trying!
:confused:

---

### Post by yabbadabbadont on 2007-09-27
Sorry.  That's why I told you to test it first.  :)

Try this instead:
```
find /path/to/root/dir/of/music -type f -name "*.wav" | while read i
do
    lame -h -b 192 "$i" "${i%.wav}.mp3"
    rm "$i"
done 

```

I tested it this time.  ;)

```
/home/daffy/temp $ mkdir -p jj/kk/ll
/home/daffy/temp $ touch jj/jj.wav jj/kk/kk.wav jj/kk/ll/ll.wav
/home/daffy/temp $ find . -type f -name "*.wav" | while read i
> do
> echo $i
> done
./jj/jj.wav
./jj/kk/ll/ll.wav
./jj/kk/kk.wav

```

---

### Post by pjpalmq on 2007-09-27
WOW!!!!  This is fan-friggin-tastic!  Thanks so much!  

:popcorn:

It will run for hours, but it is so much better than me sitting here babysitting!

Thanks again!
Best,
Peter

---

### Post by yabbadabbadont on 2007-09-27
Perhaps you should have changed it to check the error code returned by lame before removing the source file...  especially since it will be running unattended for hours.  ;)

---

### Post by pjpalmq on 2007-09-27
Okay, enlighten me?  While I do have the originals all saved on a DVD, what could happen?

---

### Post by yabbadabbadont on 2007-09-27
Lame could, for some reason (out of disk space, ...), fail to create the mp3 file.  Yet the script will unconditionally remove the wav file anyway.  Since you have the original files backed up, I wouldn't worry about it.

---

### Post by pjpalmq on 2007-09-27
Good to know.  Thankfully, that won't be an issue. 

Out of curiosity, what would the error look like?

Best,
Peter

---

### Post by yabbadabbadont on 2007-09-27
```
/home/daffy $ lame jj
Could not find "jj".
/home/daffy $ echo $?
1

```
The return code would be zero if there were no errors.

Edit: So you would do something like this:
```
find /path/to/root/dir/of/music -type f -name "*.wav" | while read i
do
    lame -h -b 192 "$i" "${i%.wav}.mp3"
    if [ $? -eq 0 ]
    then
        rm "$i"
    fi
done 

```

---

### Post by pjpalmq on 2007-09-27
Thank-you!  That make total sense!  :popcorn:

---

