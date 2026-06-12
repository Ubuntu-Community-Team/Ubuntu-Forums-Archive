---
title: "gzip create arachive with the same name  as file name"
date: 2010-10-01
forum: Programming Talk
---

### Post by aliahsan81 on 2010-10-01
Hi All

I have many files in directory like
```

hello.log
hello.20100920.log
hello.20100921.log
------------
and so one

```

I have to make archive like this with single command.I know it possible i have scene some on doing it with gzip or tar but forgot how he did.
```



hello.log.gz
hello.20100920.log.gz
hello.20100921.log.gz

```

---

### Post by vik_2010 on 2010-10-01
I think you're mixing up terms:

"archiving" something means taking a number of files and joining them together into one single file. tar files are archive files.

On the other hand,

"compressing" something means to reduce its size by getting rid of extraneous bits - using some algorithm or another - than be reinserted upon decompression. gzip is a compression utility.

.tar.gz files are files that are archived AND compressed (the former first). T his differs from file  in windows-land like zip files, which are both compression and archive file. 

The tar utility can both archive and compress files.

I'm not sure what you want, but I'm assuming yourmwant to join them all up together.

To create a tar file, just do:
tar -czvf [DESTINATION FILENAME] 
[LIST OF FILES TO ARCHIVE]

If you want to something to each file in a folder:

for file in `ls`;do
gzip $file
done;

But I'm not sure why you'd want to do that.

---

### Post by aliahsan81 on 2010-10-01
> **vik_2010 said:**
> I think you're mixing up terms:

"archiving" something means taking a number of files and joining them together into one single file. tar files are archive files.


The tar utility can both archive and compress files.

I'm not sure what you want, but I'm assuming yourmwant to join them all up together.

To create a tar file, just do:
tar -czvf [DESTINATION FILENAME] 
[LIST OF FILES TO ARCHIVE]

If you want to something to each file in a folder:

for file in `ls`;do
gzip $file
done;

But I'm not sure why you'd want to do that.


Thanks for replay.I mean compress archive sorry for miss understanding.Yes i can do that with loop it possible but i am in middle of script.That will process compress logs later on with zcat that why i want to do this.

---

### Post by slavik on 2010-10-01
use the find command. or simply `gzip *.log`

---

