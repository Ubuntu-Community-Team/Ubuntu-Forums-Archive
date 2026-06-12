---
title: "mkdir question"
date: 2012-04-18
forum: Programming Talk
---

### Post by conradin on 2012-04-18
Hi all, I just realized from making a bash script, then reading the man pages, that mkdir seems to have no force option, and only creates folders if they do not already exist. My script created a bunch of directories, and coppied a Makefile to each folder. Then I realized it would be nice to add some empty program files. hello$i.c. when I ran the script again to now touch in some files, I got an error about the file already existing. 

```
#!/bin/bash
for i in `seq 2 9`
do 
	mkdir hello$i
	cd hello$i
	touch hello$i.c
	cp -f /home/h/Desktop/kernDev/hello1/Makefile  .
	cd ../
done
```

Basicaly all I want to know, is how to force an overwrite of an existing directory, or if there is a different program besides mkdir that i should use for overwriting directories.

---

### Post by dwhitney67 on 2012-04-19
> **conradin said:**
> Hi all, I just realized from making a bash script, then reading the man pages, that mkdir seems to have no force option...

Uh, what?

What is it that you want to force to happen (or not happen)?  The way you are using mkdir in the script, it has the potential to fail if the directory already exists or if it cannot be created.

Check the status value in your script, after calling mkdir, by examining $? and/or consider using the -p option for mkdir.  For example:
```

mkdir some_dir

if [ $? -eq 0 ]; then
    # directory successfully created
else
    # creation of directory failed
fi

```

---

### Post by for.i.am.root on 2012-04-19
I think he means he wants to force the script to overwrite the folder if it exists, however, that would (probably) delete all its contents. Something like this should work:

```

#!/bin/bash
for [ i in `seq 2 9` ]; do
     if [ -d hello$i ]; then
          #directory exists
          cd hello$i
     else
          #if file with name exists
          if [ -f hello$i ]; then
               echo "error $0: there is already a file with that name"
               # exit 1 is error. exit returns 0 regardless of execution status
               exit 1
          fi
     # no file with same name, no directory with same name
     mkdir hello$i
     cd hello$i
     fi
touch hello$i.c 
cp -f /home/h/Desktop/kernDev/hello1/Makefile .
cd../
done

```

If the directory exists it will cd into it. Otherwise it creates it. This also checks for a file with the same name as the directory you are attempting to create and exits with an error code if it finds one.

The if conditional -d is if directory exists, -f is if file exists.

Have fun bash coding. One of my favorite time killers :-D.

Overwriting the old dir will delete its contents. You should always check for existence before creating. Rather than overwrite you should use mv hello$i hello$i.old.

If you are overwriting folders a single typo can cause a ton of data loss.

---

