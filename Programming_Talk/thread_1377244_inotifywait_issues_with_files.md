---
title: "inotifywait issues with files"
date: 2010-01-10
forum: Programming Talk
---

### Post by SonicSam on 2010-01-10
```
inotifywait -m --format '%f' -e moved_to "/home/admin/test/" | while read NAME
do
     echo $NAME
done

```According to the inotifywait [COLOR=Blue][man page]("http://linux.die.net/man/1/inotifywait")[/COLOR]

> **moved_to**

A **file _or_ directory **was moved into a watched directory. This event occurs even if the file is simply moved from and to the same directory.Moving a folder named "Dog" into the folder will result in
```
echo Dog
```However, if I move a **file** for example "Tree.txt", I do NOT get
```
echo Tree.txt
```Curious to what I am doing wrong, seems very straight forward. Files do not seem to be monitored.

Thanks,
-Sam

---

### Post by stylishpants on 2010-01-10
Works for me.

Terminal 1:
```
bob@cob:~$ cd /tmp/
bob@cob:/tmp$ mkdir test
bob@cob:/tmp$ inotifywait -m --format '%f' -e moved_to "/tmp/test/" | while read f; do echo $f; done
Setting up watches.  
Watches established.
Tree.txt
folder

```

Terminal 2:
```

bob@cob:~$ touch Tree.txt
bob@cob:~$ mv Tree.txt /tmp/test/
bob@cob:~$ mkdir folder
bob@cob:~$ mv folder /tmp/test/


```

---

### Post by SonicSam on 2010-01-10
That's odd, replicating your exact code, I receive no notifications about the folder or file when moved to /tmp/test/

---

### Post by stylishpants on 2010-01-10
Strange.  

Try debugging by using some more general inotifywait options and dropping the loop.  See if you can see any events at all on this directory.

eg.  inotifywait -m  "/tmp/test/"

Then do some file creation, moving and deletion events in that directory.  What is returned then?

---

### Post by SonicSam on 2010-01-10
Alright this is going to sound weird, and there is probably a logical explanation, however running my original command now finds files.

Not sure what I changed, but it's fixed!

Thanks!

---

