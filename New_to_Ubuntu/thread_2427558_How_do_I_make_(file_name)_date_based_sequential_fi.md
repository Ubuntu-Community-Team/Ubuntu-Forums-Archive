---
title: "How do I make (file name) date based sequential files?"
date: 2019-09-24
forum: New to Ubuntu
---

### Post by jaxom98 on 2019-09-24
I need to make sequential files. Currently I can enter a file name/date(McDonald-18/04/19), BUT when I want to add to the file I get an error message "file name in use" and there is a total block on adding to the existing file. The next update in the sequence should be McDonald-18/08/19, same file with the date being the "divider" between each set of photos and invoices.
Senario: lease maintenance requires sequential documentation,(mainly photos) to verify the maintenance is being carried out. I have to use a different file name to be able to enter the documentation for the same file.

How do I add to existing file?
I am new to office stuff.

---

### Post by Skaperen on 2019-09-24
which office program are you using?  are you making a text document?  is there a specific type of file you need to make?

---

### Post by The Cog on 2019-09-24
Can you clarify the file name? "McDonald-18/04/19" describes a file with name "19" in a folder called "04" in a parent folder called "McDonald-18". 
Maybe your editor doesn't like multiple files all called "19"?  
Or maybe it won't save a new version of "19" to a folder "08" if folder "08" does not already exist.
As you see, I am thinking that maybe the choice of filename is the cause of the problem.

We use folders signifying the date at work, but the files all have their own names in a folder that signifies the date, e.g.
2018/08/18/log1.txt
2018/08/18/log2.txt
2018/08/18/log3.txt
2018/08/19/log1.txt

---

### Post by QIII on 2019-09-24
If you are speaking only of the file name and are not trying to place files in sub-directories, I would use neither the dash nor the slash. 

McDonald_20190924 would be better (the order of the day, month and year would, of course, depend on your cultural sensibilities.)

If you want a directory called McDonald with dated sub-directories, McDonald/20190924 or McDonald/2019_09_24

---

### Post by TheFu on 2019-09-24
Using "funny" names that file systems dislike will make problems.
In all OSes, the /, is the directory separator.  That includes Windows.
Using () will cause hassles too.

The best *sort order* is created by using yyyy-mm-dd names, but really files like that should have different years placed into different directories to make data cleanup following the company data retention policies easier, at least on an annual basis.  Creating the filenames for today in a script is easy:
```
$ date "+%F"
2019-09-24
```

For photo organization, I most definitely use yyyy/mm/dd-Event/   organization.
[https://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](https://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival)  I have over 60K photos now.  Photos have multiple dates stored inside the EXIF information, so having it in the file name isn't really needed. Let the directories handle that.

And for data cleanup: [https://blog.jdpfu.com/2013/01/01/annual-digital-cleanup](https://blog.jdpfu.com/2013/01/01/annual-digital-cleanup)

If you just want a way to make sequential names, 
```
$ seq 0 100
```
or if you use bash, 
```
$ for N in {1..24} ; do echo "# $N  "; done
```

---

### Post by jaxom98 on 2019-09-24
Skaperen, I am using Shot Well photo manager as that is default

---

### Post by jaxom98 on 2019-09-24
The Cog,Qlll,and The Fu, if I am reading you right it is the / IN the date that is causing the trouble , so changing the / to a" ." or " _" should eliminate the no additions to file problem?

---

### Post by TheFu on 2019-09-25
> **jaxom98 said:**
> The Cog,Qlll,and The Fu, if I am reading you right it is the / IN the date that is causing the trouble , so changing the / to a" ." or " _" should eliminate the no additions to file problem?

I would use an '_' or '-'.  The '.' is a special character with special meaning in the regex language.  It is possible, just a huge hassle.  We are trying to save you hassles.  Everyone starts out trying to make filenames like some other system, but when it comes to dates, really, the 2019-09-24 format is the best.

---

### Post by pushbike06 on 2019-09-25
Try using Thunar Bulk Rename, its available from the repository. I would use it to rename pic files downloaded from my camera. It is not Thunar File Manager but a stand alone ap.

---

### Post by jaxom98 on 2019-09-26
Problem solved.  I removed the "/" from the date and that allowed squential additions.
The Cog ,Qlll, The Fu, thank you for your help.

---

