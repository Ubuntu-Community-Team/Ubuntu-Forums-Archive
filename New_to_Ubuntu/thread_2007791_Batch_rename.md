---
title: "Batch rename"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by Sohaib Afzal on 2012-06-21
I have some .mp4 files, named e.g. '3.1New [94a40d14] .mp4' and I want to rename them to have the same name as the corresponding subtitle files, named e.g. '3 - 1 - What are block ciphers? (17 min).srt' 
I want to do this in the terminal without installing any special program.

I searched around a bit and found this
[http://ubuntuforums.org/showthread.php?t=1694592&highlight=batch+rename](http://ubuntuforums.org/showthread.php?t=1694592&highlight=batch+rename)
which seems helpful but I cannot get it to work.

When I type ```
for i in $(ls | grep \.mp4); do a=$(ls *.srt | sed s/\.srt/\.mp4/) && mv "$i" "$a"; done
``` I get a string containing all the srt files separated by \n and mv gives the error "File name too long" for each mp4 file.

It appears that the "do" part of my code is wrong. It outputs just one huge string while I want it to output a different string for each i. Help please.

---

### Post by papibe on 2012-06-21
Hi Sohaib Afzal. Welcome to the forums!

A few tips:

It is not necessary to use the 'ls' on your for expression. Instead use something like this:
```
for i in *.mp4; do
    ...
done
```
Then, inside the for, I would avoid running 'ls' again, but matching the only srt file that correspond to the mp4 file.

If I understood correctly, the mp4's first and third character will match the the srt file as follow:
```
3.1xxxxx.mp4'  --> '3 - 1 - xxxxxx.srt
```
If so, I would use Bash string extraction to match the corresponding file. For instance:
```
for i in *.mp4; do
    a="${i:0:1} - ${i:2:1} - "*.srt

    echo mv -i "$i" "$a"
done
```
Note that I'm not actually renaming the files, but echoing the command so you can debug it, and correct it as your needs.

I hope that points you in the right direction, and tell us how it goes.
Regards.

---

### Post by Sohaib Afzal on 2012-06-21
@papibe Thank you for pointing me in the right direction! I did not know you could do string extraction in Bash. It is really cool. 

Here is the code that finally worked:
```

for i in *.mp4; do
    for j in *.srt; do
        if [ "${i:0:1} - ${i:2:1}" == "${j:0:5}" ]
        then
            mv -i "$i" "$j".mp4
        fi
    done
done

```Now the only remaining bug is that I have my files named .srt.mp4
I guess I'll need to read up perl regexp to use rename or maybe try something else.
Thanks again.

---

### Post by Sohaib Afzal on 2012-06-21
Just for completeness, here is the final bit of code:
```
rename 's/\.srt\.mp4$/\.mp4/' *.srt.mp4
```

---

### Post by papibe on 2012-06-21
EDIT: you got it.!

> :) Glad you are getting closer.

About your srt.mp4 files: that is why I always first echo my move commands, and only remove the echo part when I am sure I got it right ;).

Since the 'damage' is done, I would recommend using the command rename to replace all .srt.mp4 files for just mp4:
```
rename 's/srt.mp4/mp4/' *
```
Regards.

---

