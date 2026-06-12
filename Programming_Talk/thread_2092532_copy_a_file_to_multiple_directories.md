---
title: "copy a file to multiple directories"
date: 2012-12-08
forum: Programming Talk
---

### Post by IAMTubby on 2012-12-08
Hey,
My question is, "Is it possible to copy a file to multiple directories/ create multiple copies of the same file using cp and not using a shell script"

For example,
```

cp -option file dir1 dir2 dir3

```
I wanted something which would copy the same file called 'file' to all 3 directories.


PS : Sorry to ask an elementary question, I tried to find it on google, but all I kept getting was shell scripts. I want to do it from the terminal using cp.

Thanks.

---

### Post by MadCow108 on 2012-12-08
something like this is probably closest to "not being a script"
```
echo -e "dir1\ndir2\ndir2" | xargs -P 1 -I{} cp -t {} file file2
```

a simple for loop is probably more readable.

---

### Post by r-senior on 2012-12-08
From the manual page for cp:

> SYNOPSIS
       cp [OPTION]... [-T] SOURCE DEST
       cp [OPTION]... SOURCE... [COLOR="Red"]DIRECTORY[/COLOR]
       cp [OPTION]... -t [COLOR="Red"]DIRECTORY[/COLOR] SOURCE...

DESCRIPTION
       Copy SOURCE to DEST, or multiple SOURCE(s) to [COLOR="Red"]DIRECTORY[/COLOR].


So the answer to your question is no. You would need to wrap cp in some sort of script to copy to multiple targets.

---

### Post by drmrgd on 2012-12-08
Yeah, there's no cp option to do it.  But a simple bash loop would handle it in just a few keystrokes.  Perhaps something like:

```
for d in <dir>; do cp <file> "$d"; done
```

Of course edit <dir> and <file> to meet your needs.

---

### Post by Vaphell on 2012-12-08
just to clarify drmrgd's code
```
for d in "<dir1>" "<dir2>" "<dir3>"; do cp "<file>" "$d"; done
```
if you have to do this multiple times because let's you want to propagate frequent file changes scripting is more convenient because you don't risk typos - the dir list is hardcoded in the script and you never have to type it by hand. 

> PS : Sorry to ask an elementary question, I tried to find it on google, but all I kept getting was shell scripts. I want to do it from the terminal using cp.
shell scripts are just sequences of commands and more often than not you can run the individual commands manually in terminal, you just need to find the part that is responsible for the core functionality.

---

### Post by ofnuts on 2012-12-08
> **IAMTubby said:**
> Hey,
My question is, "Is it possible to copy a file to multiple directories/ create multiple copies of the same file using cp and not using a shell script"

For example,
```

cp -option file dir1 dir2 dir3

```I wanted something which would copy the same file called 'file' to all 3 directories.


PS : Sorry to ask an elementary question, I tried to find it on google, but all I kept getting was shell scripts. I want to do it from the terminal using cp.

Thanks.

Just wondering if in this case it would not be more efficient to create links instead of making copies...

---

### Post by IAMTubby on 2012-12-10
> **MadCow108 said:**
> something like this is probably closest to "not being a script"
```
echo -e "dir1\ndir2\ndir2" | xargs -P 1 -I{} cp -t {} file file2
```

a simple for loop is probably more readable.
Wow that worked ! :)

---

### Post by IAMTubby on 2012-12-10
> **r-senior said:**
> From the manual page for cp:



So the answer to your question is no. You would need to wrap cp in some sort of script to copy to multiple targets.
Thanks a lot rsenior. Yes, I shall write a script for the same. Have got some help from others who replied as well.

---

### Post by IAMTubby on 2012-12-10
> **drmrgd said:**
> 
```
for d in <dir>; do cp <file> "$d"; done
```

Of course edit <dir> and <file> to meet your needs.


and
> **Vaphell said:**
> just to clarify drmrgd's code
```
for d in "<dir1>" "<dir2>" "<dir3>"; do cp "<file>" "$d"; done
```

Thanks a lot drmrgd and Vaphell for that. The response was useful.

---

### Post by IAMTubby on 2012-12-10
> **ofnuts said:**
> Just wondering if in this case it would not be more efficient to create links instead of making copies...
Thanks a lot ofnuts for that thought. I shall do it if I want it sometime. 
Was just curious to know how to do it using the shell actually :)

---

### Post by CinemaFoto on 2013-02-02
Hello, everybody!
After searching a lot in the Net, I decided to specify my question, maybe it will be useful for other users too. That's why I'm publishing it here.
I'm cameraman and I film on Flash Memory Cards (FMC) of different types. But when card is getting full I have to drain it to separate folder of some HDD before I can format the FMC for the next use. Because the filmed data is important and expensive :), I prefer to have dual backup - to copy twice at least the FMC data to two different destinations, let's say, to two different external HDD. Doing it one by one takes twice time - if 32GB can be copied for about 40 min. to single HDD, it means, dual backup may take about 1.5 hours!!!
The mentioned above CLI loop is good - by using it I won't need to start the second copy manually, but it still doesn't solve the problem of long lasting copying time. Is there any utility that's able to read once from the source (FMC) and write twice to two or more different destinations simultaneously? As I see it - the most slow part of this chain is the USB Card reader. An internal SATA HDD of the laptop or even USB2 or USB3 external HDD are much faster than USB2 Card Readers and have some buffers, this way reading once and writing twice will seriously speed up whole backup system.
Thank to all of You in advance for any useful information.

---

### Post by SeijiSensei on 2013-02-02
Copy once from the card to the hard drive, then copy that to the other targets.

---

### Post by CinemaFoto on 2013-02-02
> **SeijiSensei said:**
> Copy once from the card to the hard drive, then copy that to the other targets.
Thanks for Your answer.
But this is still twice a time - 40 min FMC => HDD, and about 20 min HDD => HDD. And if there was en error in the first copying process, this error will by multiplying by copying...
Any other solutions?

---

### Post by r-senior on 2013-02-02
You could try tee:

```
$ tee < original copy1 > copy2
```

For multiple files you'd have to wrap that in a script. You'd need to test to see if it is any quicker. I would guess it is if the speed of the FMC is the limiting factor.

---

### Post by CinemaFoto on 2013-02-02
> **r-senior said:**
> You could try tee:

```
$ tee < original copy1 > copy2
```

For multiple files you'd have to wrap that in a script. You'd need to test to see if it is any quicker. I would guess it is if the speed of the FMC is the limiting factor.
Thanks! I'll check it. Can You write me an example of the command with exact syntax?

---

### Post by r-senior on 2013-02-02
That is pretty much the exact syntax. For example:

```
$ cp /etc/hosts ./
$ ls
hosts
$ tee < hosts hosts1 > hosts2
$ ls
hosts  hosts1  hosts2
$ diff hosts hosts1
$ diff hosts hosts2
```

So I copied a test file to an empty directory, listed it, made two copies and checked that each copy was the same as the original. Your files would just have directory paths in front of them.

---

### Post by CinemaFoto on 2013-02-02
> **r-senior said:**
> That is pretty much the exact syntax. For example:

```
$ cp /etc/hosts ./
$ ls
hosts
$ tee < hosts hosts1 > hosts2
$ ls
hosts  hosts1  hosts2
$ diff hosts hosts1
$ diff hosts hosts2
```

So I copied a test file to an empty directory, listed it, made two copies and checked that each copy was the same as the original. Your files would just have directory paths in front of them.
Thanks!!!

---

### Post by lavinog on 2013-02-02
What is the largest file size that you would copy?
Assuming you have a decent amount of ram, you should utilize the caching of the files to copy.
something like this (assuming on the source folder):
```

for file in *; do cp -v "$file" disk1; cp -v "$file" disk2; done

```
The kernel will attempt to read the whole file into memory when doing the first copy, then copy from memory to the second disk.

Caching only keeps the last files that you read, so unless you have over 32G of memory, trying to copy the whole card to one drive first will be much slower.

If you provide more details of what you normally do, there might be a way to background copy the second file so reading the next file isn't held up by the second copy.

---

### Post by ofnuts on 2013-02-04
> **CinemaFoto said:**
> Hello, everybody!
After searching a lot in the Net, I decided to specify my question, maybe it will be useful for other users too. That's why I'm publishing it here.
I'm cameraman and I film on Flash Memory Cards (FMC) of different types. But when card is getting full I have to drain it to separate folder of some HDD before I can format the FMC for the next use. Because the filmed data is important and expensive :), I prefer to have dual backup - to copy twice at least the FMC data to two different destinations, let's say, to two different external HDD. Doing it one by one takes twice time - if 32GB can be copied for about 40 min. to single HDD, it means, dual backup may take about 1.5 hours!!!
The mentioned above CLI loop is good - by using it I won't need to start the second copy manually, but it still doesn't solve the problem of long lasting copying time. Is there any utility that's able to read once from the source (FMC) and write twice to two or more different destinations simultaneously? As I see it - the most slow part of this chain is the USB Card reader. An internal SATA HDD of the laptop or even USB2 or USB3 external HDD are much faster than USB2 Card Readers and have some buffers, this way reading once and writing twice will seriously speed up whole backup system.
Thank to all of You in advance for any useful information.
Side tracking the problem:  if you are using CompactFlash cards, then you can find card readers (they can be passive adapters)  that will be much faster than USB. The CF interface is an adaptation of the IDE interface used in hard disks.

---

### Post by CinemaFoto on 2013-02-06
> **lavinog said:**
> What is the largest file size that you would copy?
Assuming you have a decent amount of ram, you should utilize the caching of the files to copy.
something like this (assuming on the source folder):
```

for file in *; do cp -v "$file" disk1; cp -v "$file" disk2; done

```
The kernel will attempt to read the whole file into memory when doing the first copy, then copy from memory to the second disk.

Caching only keeps the last files that you read, so unless you have over 32G of memory, trying to copy the whole card to one drive first will be much slower.

If you provide more details of what you normally do, there might be a way to background copy the second file so reading the next file isn't held up by the second copy.
Thank You for Your answer. As I wrote, I'm trying to make backup copies of Flash Memory Cards (usually SecureDigital (SD) or special cards for professional video like P2 ('Professional Plugin') or SxS). It means that the content of the card may vary. It may contain small files and folders of configuration but also big files with video and sound into them. And it is very important to make recursive copy to save whole folders' structure as is for making it possible to be read by editing software. As I know, most video formats limit the file size upto 2GB or 4GB. But! I'm using for the backup copying my netbook with 1GB RAM, so this size of file cannot be cached, can it? Otherwise, it can still make it faster if it will cash only smaller than available memory size files.
For now, I'm copying once the whole directory tree structure of the Flash Memory Card to external HDD 'A' and then copy again the same whole directory tree structure of the Flash Memory Card to external HDD 'B'.
Thank You in advance for more ideas.

---

### Post by CinemaFoto on 2013-02-06
> **ofnuts said:**
> Side tracking the problem:  if you are using CompactFlash cards, then you can find card readers (they can be passive adapters)  that will be much faster than USB. The CF interface is an adaptation of the IDE interface used in hard disks.
Unfortunately, as I mentioned above, I mostly deal with SD and special professional card formats like P2 and SxS. Most of external readers for those formats are USB2.

---

