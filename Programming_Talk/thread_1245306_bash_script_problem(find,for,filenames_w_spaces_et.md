---
title: "bash script problem(find,for,filenames w spaces etc)"
date: 2009-08-20
forum: Programming Talk
---

### Post by denarced on 2009-08-20
The script should work like this
```
cp `./script.sh` dest_dir
```

So the script includes a find statement which should echo the filenames escaped but it doesn't work for some reason.
I tried putting quotes around filenames instead of escaping but that didn't work either. I successfully made a script for filenames with no special characters or whitespace but that's not enough...
NOTE: copying is not the end purpose, it's just an example.

---

### Post by geirha on 2009-08-20
You cannot reliably do that. 
[http://mywiki.wooledge.org/BashPitfalls#for_i_in_.60ls_.2A.mp3.60](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.60ls_.2A.mp3.60)

Use «find ... -exec cp {} destdir \;» or «find ... -print0 | xargs -0 cp -t dest_dir» instead.
[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by denarced on 2009-08-20
> **geirha said:**
> You cannot reliably do that. 
[http://mywiki.wooledge.org/BashPitfalls#for_i_in_.60ls_.2A.mp3.60](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.60ls_.2A.mp3.60)

Use «find ... -exec cp {} destdir \;» or «find ... -print0 | xargs -0 cp -t dest_dir» instead.
[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

Thank you.
You're the man.
This was what I was looking for exactly!

---

### Post by denarced on 2009-08-20
damn .. I thought I had it but no
The first reply almost helped me but I shouldn't have used cp as an example simple because in that particular command you can go around the problem.
The problem is that in imagemagick's command montage, the LAST argument is montage-file-name and all the filenames that have been found with find, are in the middle. So it would be something like this:
```
montage `find . -type f -ctime -10` montage.jpg
```
That one doesn't work but you get my point.
I can't use xargs for that very reason and I can't use find-command's -exec for that same reason.

Any ideas?

---

### Post by unutbu on 2009-08-20
```
find . -type f -ctime -10 -exec sh -c 'montage "$@" montage.jpg' _ {} +
```

---

### Post by denarced on 2009-08-21
> **unutbu said:**
> ```
find . -type f -ctime -10 -exec sh -c 'montage "$@" montage.jpg' _ {} +
```

This works .. thank you

---

