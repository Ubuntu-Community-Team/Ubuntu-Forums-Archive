---
title: "command line for backup?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by garyed on 2008-08-19
I'm trying to find a simple backup command that only copies anything that has been changed since the last backup. 
In windows I use the xcopy command: 

xcopy \directory\*.* \backupdirectory /m/s

The key is the /m which only backs up files with the archive attribute set on & then turns it off afterwards.
I'm only aware of file permissions in Linux. I assume there is something I'm not aware of that shows other file attributes in terminal.
Would :
```

cp -ur 
``` do the same thing?

---

### Post by anotherdisciple on 2008-08-19
hmmm.... I'm interested in this also.


I have been using a program called "Unison"... but a terminal command would be better.

---

### Post by Dill on 2008-08-19
I believe so. If you compare the help page for xcopy and the man page for cp...

xcopy /m:

```
/M   copies only those files that have been modified since the last
     BACKUP /M or XCOPY /M.  The /M option is identical to the /A
     option except XCOPY /M will reset the flags on those files that
     have been modified since the last backup.

```

cp -u

```
-u, --update
              copy only when the SOURCE file is  newer  than  the  destination
              file or when the destination file is missing

```

and xcopy /s

```
/S   causes XCOPY to copy files in any subdirectories below the
     directory that XCOPY starts in.

```

and cp -r

```
-R, -r, --recursive
              copy directories recursively

```

Then they seem to serve the same purpose, save the fact that xcopy /m "reset[s] the flags" on modified files.

Also, in terms of the "other attributes" you were mentioning, each file has a timestamp which indicates its date and time of modification. You can reset this by editing a file or by entering 

```
touch <filename>
```

into a Terminal.

To give a "long" listing of file attributes, try 


```
ls -l
```

Cheers, 
Dylan

---

### Post by hyper_ch on 2008-08-19
rsync -avz from to

---

### Post by rampageoberon on 2008-08-19
Another alternative for what you want to do is the application "mirrordir". So install it and run as follows

```
sudo aptitude install mirrordir
```
```
mirrordir <main-dir> <backup-dir>
```

hope that helps

---

### Post by garyed on 2008-08-19
For most purposes " cp -ur " should work but it is really the same as
" xcopy /s/d " where " /d " copies only source files that are newer than the 
destination files & also files that don't exist on the destination dir.

Turning off the archive attribute in DOS lets you know that the file has not been edited since the last backup. A cool feature.
 Its hard to believe that DOS can actually do something that Linux can't.

---

### Post by MarkieB on 2008-08-19
no longer participating in ubuntuforums.org

---

### Post by garyed on 2008-08-19
Thanks for the ideas.
I was still hoping that there was some kind of attribute attached to Linux files similar to DOS archive that lets you know if a file has been edited or not. A time stamp only tells you how recent the file is but not if the file was there earlier & then been edited. For most backups that should be sufficient but there is usually a rare exception.

---

### Post by MarkieB on 2008-08-20
no longer participating in ubuntuforums.org

---

