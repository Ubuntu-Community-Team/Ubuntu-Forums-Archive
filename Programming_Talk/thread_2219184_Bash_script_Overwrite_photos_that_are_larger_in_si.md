---
title: "Bash script: Overwrite photos that are larger in size than original files"
date: 2014-04-23
forum: Programming Talk
---

### Post by vikler on 2014-04-23
Hi everyone!
I need a bit of help with writing a bash script.
So, the thing is, I have a directory full of .jpg files that are being copied from another directory with the help of exiftool (only jpg files that have certain Caption-Abstract tag are being copied).
However, sometimes photos in "original" directory are incomplete, because they are still being uploaded on the server. Exiftool has no problem reading meta data in incomplete files and therefore it transfers these half-finished images to my "selected photos" directory.

What I basically need is a script that will do following:
1) Write a list of .jpg files in "selected photos" directory
2) For each file listed do these steps:
- compare its size in "selected" and "original" folders
- if the photo in the "selected" directory is smaller in size than the same filename in the "original" directory, it means the photo was copied incomplete. So I need to replace this corrupted file with larger size file from "original" directory (but leave not mv it from the original directory, but copy, because original directory should have all photos saved)

I thought about something like that:
```

ls * > file
for fn in `cat file`; do 
<compare sizes of ./$fn and /home/original/$fn>
<if sized are different> rm $fn ; cd /home/original ;  cp $fn /home/selected; cd /home/selected ; 
done

```

Don't really know how to do this whole size compare step. Maybe you have a better solution in mind? 
Well any help will be appreciated. Thanks in advance!

---

### Post by ofnuts on 2014-04-23
You can easily obtain the size of a file with stat:
```

filesize=$(stat -c %s $file)

```

You can also check if a file is open by some process using
```

lsof $file

```

and check the return code ($? variable): 0 if open, 1 if not.

---

### Post by SeijiSensei on 2014-04-23
You might use diff if you want to insure the files are identical.  If you use diff with binary files, you get results like this:
```

$ cd /usr/bin
$ diff okular firefox
Binary files okular and firefox differ

```
If the files match, diff returns an empty result.

So you can run a test like this:
```

CHECK=$(diff /path/to/dir1/image /path/to/dir2/image)
if [ "$CHECK" = "" ]
then
     files match; do whatever
else 
     files differ; do whatever
fi

```

---

### Post by steeldriver on 2014-04-23
Wouldn't rsync be just the thing here... ?

```

$ diff -s newpics/ oldpics/
[COLOR=#ff0000]Binary files newpics/2rxjmt0-1.jpg and oldpics/2rxjmt0-1.jpg differ
[/COLOR]Files newpics/3006780451_86a22b8ae9.jpg~original.jpeg and oldpics/3006780451_86a22b8ae9.jpg~original.jpeg are identical
Files newpics/Abbey-House-Museum_2484527c.jpg and oldpics/Abbey-House-Museum_2484527c.jpg are identical
[COLOR=#ff0000]Binary files newpics/camelguy.small.jpg and oldpics/camelguy.small.jpg differ[/COLOR]
Files newpics/d29zJ5T.jpg and oldpics/d29zJ5T.jpg are identical
Files newpics/ssPFYvl.jpg and oldpics/ssPFYvl.jpg are identical

```
Then
```

$ rsync --dry-run --size-only -av newpics/ oldpics/
sending incremental file list
./
[COLOR=#0000ff]2rxjmt0-1.jpg
camelguy.small.jpg[/COLOR]

sent 235 bytes  received 33 bytes  536.00 bytes/sec
total size is 755783  speedup is 2820.09 (DRY RUN)

```

---

