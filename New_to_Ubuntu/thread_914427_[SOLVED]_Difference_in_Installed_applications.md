---
title: "[SOLVED] Difference in Installed applications"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by 44tr on 2008-09-08
I want to generate a sorted list of installed applications for two different Ubuntu installs and then create a difference file to see where they are different.  The idea of course is to find out what applications the installs do not have in common and where they are missing.

So what terminal commands will accomplish this?  Much appreciated.

---

### Post by Denestria on 2008-09-09
Sorted by what?
```

dpkg --get-selections > installedfiles.txt
dpkg --get-selections > installedfiles2.txt

```
Will give you an alphabetized list of installed packages saved to a text file called installedfiles.txt, repeated on the second system with installedfiles2.txt.  Then diff will compare and list any differences.
```

diff installedfiles.txt installedfiles2.txt

```
Is this what you need?

---

### Post by Threbus5 on 2008-09-09
Are you looking for installed applications or packages?
If packages then consider the response from the first post.

If executable/usable applications, you can select to view applications. Then, gasp - write them down and compare.
Simplicity has its benefits.

I once spent 8 hours attempting to program a Mac to draw a straight line on a piece of paper in "just the right spot" - gave up and drew the line with a ruler and pencil. At some point simplicity wins. Smile.

---

### Post by jemate18 on 2008-09-09
This isn't the main concern here but this is for sorting so that you'll have time easier.

suppose this is your file with a filename x.txt
> 
5 sun
2 banana
6 daddy
1 xerox
2 for
4 run
8 john

If you want to sort them by the "name" (second field) type
> sort -k 2 x.txt
it will sort the contents of the file without saving it.
if you want to save it then
> sort -k 2 x.txt > xSortedName.txt


If you want to sort them by the "number" (first field) type
> sort -k 1 x.txt
it will sort the contents of the file without saving it.
if you want to save it then
> sort -k 1 x.txt > xSortedNumber.txt

I hope this helps in comparing. The above post about diff is also good. try it and use it too

---

### Post by jemate18 on 2008-09-09
also you can count the lines of the file.

Suppose you have file1.txt 
type
```
wc -l file1.txt
```
It will display how many lines your file has

for the second file (file2.txt)
type
```
wc -l file2.txt
```
It will also display how many lines your second file has.

---

### Post by 44tr on 2008-09-09
Thanks for the replies.  The first reply covered about what I wanted.  Packages is as close as I will likely get.  I certainly understand the point of simplicity, but it isn't clear to me how to get a complete list of installed applications to view, just the ones listed in the menu (which isn't all by a long shot).

Thanks also for the guidance with the sort command.  That helps.

P.S.  Simplicity is actually the point of this.  I have a Windows XP wubi installation of Ubuntu that I pretty heavily customized, but now want to move to a regular installation.  I'm just recreating since the cloning/backup/restore process looks like a nightmare.  I just wanted to see how close I am to what I had application wise.

---

### Post by Denestria on 2008-09-09
I guess you could try something like this

```

ls -1 /usr/bin/ /usr/local/bin/ > installedapps.txt

```

Which would list one file per line in the usr/bin and usr/local/bin directories.  You can add whatever other directories you may have things installed to like /opt in there too.  ls can do its own sorting as well if you want like

```

ls -1 --sort=size /usr/bin/ /usr/local/bin/ > installedapps.txt

```

--sort can also = extension, time or version

run on both installations as per the first instructions I gave and use diff on both outcomes.

```

diff installedapps.txt installedapps2.txt > differences.txt

```

---

