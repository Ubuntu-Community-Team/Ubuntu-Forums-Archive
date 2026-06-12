---
title: "recursively check directory in bash script"
date: 2009-04-13
forum: Programming Talk
---

### Post by wesg on 2009-04-13
I spent an inordinate amount of time this past weekend creating a bash script that converts M4A files to MP3 files so that my new server with MediaTomb can read the metadata. Right now it does everything I want, but only if the conditions are just right. I'm hoping some of the geniuses here can help me make the script better.

Right now the script uses "for files in DIRECTORY" loop to go through each file with the M4A extension. This works, but I want to be able to find files inside other directions. How can I do that?

Also, I need to be able to fail gracefully when no files with the extension are present. What kind of check can I do that also works recursively?

---

### Post by poing on 2009-04-13
Maybe you should post your script and people can help you from there.

To perform an action on some files recursively it is usually easiest to let find take care of that. Example:
> find . -name '*.mp3' -exec ls -lh '{}' \;

Will recursively go through directories and just ls -lh every single file. Just replace the extension with your extension and ls -lh with whatever you do to run the conversion. See the man page of find for more options.

---

### Post by ghostdog74 on 2009-04-13
```

find /path -iname "*.m4a" | while read file
do
 # code to convert m4a to mp3 
done

```

---

### Post by wesg on 2009-04-13
Thank you both, poing and ghostdog. I was able to get the job done. I wasn't able to print the code because I was away from my home computer. Next time!

---

### Post by virgiltibbs on 2009-04-14
wow thanks guys
(I'm trying to do something pretty much identical but in a completely different context..)
@wesg any chance you could post your code when you get the chance? I think it could give me some useful pointers...

---

### Post by haylocki on 2009-04-22
Thanks ghostdog.

Just what I was looking for as well.


Cheers, Ian

---

