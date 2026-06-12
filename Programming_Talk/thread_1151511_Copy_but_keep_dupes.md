---
title: "Copy but keep dupes"
date: 2009-05-07
forum: Programming Talk
---

### Post by jamesdcarroll on 2009-05-07
I would like to find all the pictures on my system and copy them to a single folder. I found a little script that will see them out and do that:

```
 find . -name '*.jpg' -type f   -exec sh -c 'exec cp -f "$@" /home/jim/AllPictures' find-copy {} 
```

but when it tries to copy files that have the same name as one that's already in the destination folder it won't overwrite which is fine, but I would rather that it make another copy(ie image.jpg, image1.jpg, image2.jpg... etc)

Would it be possible to do that? I know I'm gonna have dupes and will deal with that later. Right now I just want to get everything in one place.

Thanks!

---

### Post by geirha on 2009-05-07
The cp command can make numbered backups, which means that if the destination file allready exists, the destination file is renamed with a .~1~, .~2~, etc... extension. That would be the easiest way to get all copied to the same directory at least. Unless there are alot of dupes, renaming should be easy enough to do manually.

```
find . -iname "*.jpg" -type f -print0 |
xargs -0 -- cp -v --backup=numbered --target-directory="/home/jim/AllPictures" --

```

---

### Post by geirha on 2009-05-07
In case there are alot of dupes, this rename command will rename "something.jpg.~1~" into "something.1.jpg"

```
cd /home/jim/AllPictures/
rename -v 's/\.jpg\.~(\d+)~$/.$1.jpg/i' *

```

---

### Post by jamesdcarroll on 2009-05-09
Thanks!  I saw the '--backup=numbered' thing in the man page but I didn't quite understand how to make it work or what its action was.

---

