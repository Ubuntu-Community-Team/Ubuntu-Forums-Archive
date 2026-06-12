---
title: "Can't unzip .zip files in Xubuntu 12.04 64-bit"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by marinecomm on 2013-08-09
I downloaded some .zip files and tried three different programs to open them and these are the results that I got:

Squeeze: command exited with status 2304

Archive Manager: cannot open file as archive

Xarchiver: Archive format is not recognized

So, how am I supposed to open .zip files?

---

### Post by The Cog on 2013-08-09
try:
```
sudo apt-get install zip unzip
```
and then you should at least be able to unzip them by command line:
```
unzip filename
```

---

### Post by marinecomm on 2013-08-09
My results when I issued the command to install zip and unzip:

unzip is already the newest version.
zip is already the newest version.

---

### Post by marinecomm on 2013-08-09
Downloaded Krusader and configured it. When I go to the folder with the .zip files, they don't even show up.

---

### Post by Dennis N on 2013-08-09
Archive Manager (file-roller) will open .zip files. I have used it countless times to do so. My version is 3.4.1 which came with release 12.04 (Xubuntu).

---

### Post by marinecomm on 2013-08-09
As you can see by my original post that I tried Archive Manager. I checked it and I have version 3.4.1 as well. I even tried redownloading it and still no luck.

---

### Post by Dennis N on 2013-08-09
> **marinecomm said:**
> As you can see by my original post that I tried Archive Manager. I checked it and I have version 3.4.1 as well. I even tried redownloading it and still no luck.

Yes, I saw that. I am wrong about the files with spaces - I just tried some and they open too, so I will edit that part out of the previous reply.

Sorry, have no answer at the moment. Possibly something in the .zip file creation process for those files?

As a test, try and use Archive Manager to create a .zip archive of a few files, then try to unzip it. It should work.

---

### Post by oldos2er on 2013-08-09
What does the 'file' command say about these .zip files? ```
file /path/to/zipfile.zip
``` Maybe they're corrupted.

---

### Post by marinecomm on 2013-08-09
I was using flareget to downlaod the files. I tried downloading them through aria2 command-line and I'm able to do that and open the file. Therefore, it must be the way flareget downloads and puts the files onto my computer.

---

### Post by marinecomm on 2013-08-09
I spoke too soon. Tried downloading another .zip file with aria2 and getting the same results. I issued the command 'file path/to/file' and got the following result:

/home/jason/Desktop/surcox.zip: HTML document, ASCII text, with very long lines

So this means when it downloads the file onto my computer it's not really a .zip file?

---

### Post by oldos2er on 2013-08-09
I don't know anything about flareget, but it sounds like it doesn't save the files properly.

---

### Post by marinecomm on 2013-08-09
I THOUGHT aria2 was working for me. Now it's doing the same thing and for the life of me I can't figure out how to turn flareget off and let firefox's download manager handle the files and see if they download correctly then.

---

### Post by marinecomm on 2013-08-09
I'm trying different download manager programs to see if any of them can download these files properly. Now what's happening is that when I download a file and then try to open it a download dialog box opens up and in the URI field is the path to the file. I'm not sure what's going on now. Any ideas or suggestions?

---

### Post by d0006 on 2013-08-10
I would suggest completely uninstalling/removing flareget and using the built in Firefox/Ubuntu download manager.

If you do not want to use the built in download manager you can try:

DownThemAll
JDownloader
(these two seem to get the best reviews. I have used them both.)

There are several CL tools:
wget is the built in
curl

Do a search.

BTW, you can do:
```
head foobar.zip
```
and check the first two bytes.  If they are PK or MZ it is a .zip file. If they are something else you may have a problem.

---

### Post by marinecomm on 2013-08-10
Uninstalled flareget and installed Downthemall. So far it seems to be working but I'm going to test it out some more and see how it goes. Thank you.

---

