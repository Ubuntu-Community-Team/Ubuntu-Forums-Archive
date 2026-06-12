---
title: "How to batch rename a folder of images?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by uarale on 2008-11-18
Just want to know how to rename a folder of images of different types and names to, eg 01.jpg, 02.gif, 03.jpg, 04.png...

I've read the manual of 'rename' command but it seems too complicated in the part 'perlexpr'

---

### Post by rubbsdecvik on 2008-11-18
If you go to Applications -> Add/Remove Applications and search for Rename there are a few bulk renaming packages.  I have used Bulk Renamer before and it did well.

You might like one of the others, but they are small and fairly easy to figure out, so you should be able to find something you like.

Hopefully that helps.  Let me know if you still have questions.

---

### Post by iponeverything on 2008-11-18
You can do it from the command line -- create backup first:

```
mkdir backup
cp *jpg backup

```

Now rename:

```
ls *jpg | awk -F\. '{print "mv "$0" "NR".jpg"}'|sh

```

If you the like result, delete your backup.

Run it without the "|sh" to do a dry run.

---

### Post by jpoRS on 2008-11-18
I could be wrong, but if you are looking for a GUI I believe F-Spot has the ability to do that.

jim

---

### Post by uarale on 2008-11-18
> **iponeverything said:**
> You can do it from the command line -- create backup first:

```
mkdir backup
cp *jpg backup

```

Now rename:

```
ls *jpg | awk -F\. '{print "mv "$0" "NR".jpg"}'|sh

```

If you the like result, delete your backup.

Run it without the "|sh" to do a dry run.

works fine!

after search around, i write a script using 'rename' command
```
#! /bin/bash
$i=1
ls *.jpg | while read l_file
do
        rename -v 's/.+\.jpg$/$i\.jpg/' ${l_file}
        $i=$i+1
done

```

however, i don't know much about perlexpr (insert an integer var into it) so there're still some errors.
how can i correct it?

---

### Post by uarale on 2008-11-18
anyone can help?

---

### Post by uarale on 2008-11-18
ok, i read some tips on shell script as well as regex and this is the code
```
#! /bin/bash
cd /path/to/folder/
i=1
ls | while read l_file
do
        if [ "$i" -lt 10 ]
        then
                rename -v 's/.+\.(\w{3})$/0'$i'\.$1/' ${l_file}
        else
                rename -v 's/.+\.(\w{3})$/'$i'\.$1/' ${l_file}
        fi
        i=$((i + 1))
done

```
works fine for my folder consists of .jpg, .gif and .png images. the number of images is less than 100.

---

### Post by snova on 2008-11-18
I like KRename, although it's a KDE program, which will mean large libraries if you don't have them already.

It supports building new filenames out of various bits of metadata, which is nifty for things like... renaming a bunch of "track01.ogg" files to "Track 01 -- Title of this track.ogg" as I did a while back.

---

