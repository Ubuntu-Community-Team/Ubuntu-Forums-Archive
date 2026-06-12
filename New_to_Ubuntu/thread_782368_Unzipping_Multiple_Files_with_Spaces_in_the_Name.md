---
title: "Unzipping Multiple Files with Spaces in the Name"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Vasto on 2008-05-04
I just made the switch from windows vista to Ubuntu 8.04, and I used the Windows Backup utility to backup all my stuff to an external. The naming convention is: Backup files 1.zip .... Backup files 591.zip. I'm trying to get all the files unzipped, and overwrite instead of rename, and for the files be written in a different directory. Any help is appreciated alot.

I tried doing it with the terminal. I found someone else that I thought had a similar problem on the forums, their solution didn't work for me.
```
ls *.zip | xargs -n10 unzip
```
The error I get is
```
unzip:  cannot find or open files, files.zip or files.ZIP.
unzip:  cannot find or open 96.zip, 96.zip.zip or 96.zip.ZIP.
unzip:  cannot find or open Backup, Backup.zip or Backup.ZIP.

```

---

### Post by tamoneya on 2008-05-04
assuming that they are the only zip files in the directory you should just do ```
tar -xf *.zip
```

---

### Post by Vasto on 2008-05-04
```

tar: Backup files 97.zip: Not found in archive
tar: Backup files 98.zip: Not found in archive
tar: Backup files 99.zip: Not found in archive
tar: Backup files 9.zip: Not found in archive
tar: Error exit delayed from previous errors

```
That is the error code I get.

---

### Post by Monicker on 2008-05-04
Try this

```
ls --quoting-style=escape *.zip | xargs -n10 unzip
```

---

### Post by Vasto on 2008-05-04
Thank you, that worked. But how can I add a command to move the files from my external to my internal as it unzips (unfortunately the zip files combined are over a hundred gigs, and both hard drives are only 160 gb so I can't have both the zips and extracted on the same drive)?

---

### Post by Monicker on 2008-05-05
Is it just 2 drives on the same computer? You can specify the destination directory for unzipping with the -d option.  If these are 2 separate machines then you could do an nfs or samba mount from one to the other, in conjuction with -d.

---

### Post by Vasto on 2008-05-05
When I used:
```
ls --quoting-style=escape *.zip | xargs -n10 unzip -d home/michael/Desktop/Windows/

```

I get the error
```
checkdir:  cannot create extraction directory: home/michael/Desktop/Windows

```

---

### Post by Monicker on 2008-05-05
Are you sure about that path?

I think it should be

```
/home/michael/Desktop/Windows/
```


What you posted did not have a leading slash.

---

### Post by Vasto on 2008-05-05
Oh wow, that was simple. I'm pretty noobish with the terminal still.

I am getting a couple errors errors in the very beginning of the unzip process, however because so many files became unzipped that I can't go back to see the errors in the terminal. Not all of the files are becoming unzipped, in fact very few are. Is there a way I can make the terminal display more lines before clearing them?

---

### Post by Monicker on 2008-05-05
You can pipe the output to file
```

ls --quoting-style=escape *.zip | xargs -n10 unzip > info.txt
```


Or to the less command

```
ls --quoting-style=escape *.zip | xargs -n10 unzip|less
```

With less use the PageUp and PageDown keys to move around, q to quit.  There are actually a lot more options for navigating but that should do you for now.

---

### Post by Vasto on 2008-05-05
Ok, I outputted the file to a text file. and I think what the problem is that only archive 9 is getting extracted for some reason. (at least that is the only one that says inflating file xxxx a whole bunch of times after it). Coincidentally archive 9 is the last archive if you sort numerically (in the weird linux way)

EDIT: Using the unzip|less command I get the following
```
michael@michael-ubuntu:/media/Backup/MICHAEL-HP/Backup Set 2008-05-02 165426/Backup Files 2008-05-02 165426$ ls --quoting-style=escape *.zip | xargs -n10 unzip|less -d /home/michael/Desktop/Windows/
/home/michael/Desktop/Windows/ is a directory
xargs: unzip: terminated by signal 13

```

---

### Post by Vasto on 2008-05-05
Bump!

---

### Post by Monicker on 2008-05-05
Bad syntax.  You put less in between your unzip option of -d.

It would be
```
ls --quoting-style=escape *.zip | xargs -n10 unzip -d /some/dir|less
```

If you want to keep it from scrolling off the screen.

---

### Post by Vasto on 2008-05-05
```
michael@michael-ubuntu:/media/Backup/MICHAEL-HP/Backup Set 2008-05-02 165426/Backup Files 2008-05-02 165426$ ls --quoting-style=escape *.zip | xargs -n10 unzip -d /home/michael/Desktop/Windows/|less

```
Only Backup file 9.zip gets extracted
```
caution: filename not matched:  Backup files 94.zip
caution: filename not matched:  Backup files 95.zip
caution: filename not matched:  Backup files 96.zip
caution: filename not matched:  Backup files 97.zip
caution: filename not matched:  Backup files 98.zip
caution: filename not matched:  Backup files 99.zip
warning:  Backup files 9.zip appears to use backslashes as path separators

```

---

### Post by Vasto on 2008-05-05
```
for i in *.zip ; do unzip "$i" -d /home/michael/Desktop/Windows/; done

```
I'm pretty sure that code solved my problems. Everything is extracting as I speak. :-)

SOLVED! (Thank you for being patient and for all your help Monicker! :-)

---

