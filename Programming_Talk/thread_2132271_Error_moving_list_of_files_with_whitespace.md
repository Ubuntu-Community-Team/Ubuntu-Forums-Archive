---
title: "Error moving list of files with whitespace"
date: 2013-04-04
forum: Programming Talk
---

### Post by hypnoticmonkey on 2013-04-04
Hi,

I'm trying finally to organise my media into one folder on an external hard drive. I've executed a find command to locate all files with given file extensions. I've then exported this to a text document to give a list of filepaths one per line, and removed the ones that I don't want to move (windows system files etc.)

My next job is finding a command to move them all in one go. I don't want to put them in any sort of directory structure, I just want to lump them all to one folder labelled "videos" on my external hard drive. 

Through a bit of googling, I've found this bash script:

```
# bash shell
for file in `cat /files.txt`; do cp $file /; done
```

And, at this point, I should point out that I'm very new to the whole world of coding. I assumed this would work by putting it into a .txt file called move.txt and then opening terminal and running "bash move.txt".

So I created 2 text files to test it, 1.txt and 2.txt and simply listed them in the files.txt. Then I set the destination in the bash script, ran it and hey presto, the files were copied.

Next job: test for file names with white space. I renamed 1.txt as "this is a file.txt" and duly changed the entry /home/1.txt to /home/this is a file.txt

Unsurprisingly, this didn't work. I got:
```
cp: cannot stat `"/home/this': No such file or directorycp: cannot stat `is': No such file or directory
cp: cannot stat `a': No such file or directory
cp: cannot stat `file.txt"': No such file or directory
```

I then tried changing the code in the bash file to:

```
# bash shell
for file in `cat /files.txt`; do cp "$file" /; done
```

Still no luck, same error message.

So I tried changing the file name in the files.txt file to:

```
/home/this is a file.txt
```

But, once again, the same error message occured.

Is it possible to move/copy files with white space in their filename using this method? If so, I'd be very grateful if someone could point me in the right direction...

Many thanks,

Luke

---

### Post by steeldriver on 2013-04-04
Don't use 'cat', use bash's build in 'read' function instead e.g.

```
while read -r file; do cp "$file" /; done < /files.txt
```

or

```
while read -r file; do cp -t / "$file"; done < /files.txt
```

---

### Post by Drenriza on 2013-04-04
If the file is called file.txt and placed in your home folder, say something like

```

for line in `cat /home/username/Desktop/file.txt`;do cp -v ${line} /media/path/to/folder/to/place/movie;done

```
-v = verbose, gives extra information.

${line} = requires that the absolute path is in the file.txt.

Edit.
Didnt see this line in the first post
> 
Is it possible to move/copy files with white space in their filename  using this method? If so, I'd be very grateful if someone could point me  in the right direction...


Solved it as follows
```

IFS=$'\n';for line in `cat /home/username/Desktop/file.txt`;do scp -rv ${line} /media/path/to/folder/to/place/movie;done

```

Pr default the foor loop uses blank spaces as its delimiter point.
IFS=$'\n' changes the delimiter point to a new line.

See here [http://tldp.org/LDP/abs/html/escapingsection.html](http://tldp.org/LDP/abs/html/escapingsection.html) if intersted.

---

### Post by schragge on 2013-04-04
The last solution by **Drenriza** may be more concisely and efficiently rewritten as
```
xargs -a/home/username/Desktop/files.txt -d\\n cp -vt/media/path/to/folder/to/place/movies --
```

---

