---
title: "Scripting a PhotoBackup with md5deep"
date: 2006-09-19
forum: Programming Talk
---

### Post by Boelcke on 2006-09-19
Hi. I'm new to scripting in bash, so pardon the general nature of this programming question.

I'm trying to write a script to automate the backup of a large collection of digital photos.  I'd like the script to do several things:

1. Compare the md5 checksums of the current folder and the backup folder, and notify me if one doesn't match the other.  That way, I can check the photos/videos, and determine which one has been corrupted.  If my source file has gone bad, I don't want to simply write over the good backup file with my latest, corrupted copy! This seems to be what many typical backup applications do. (I did have a good experience with an application called SyncBack that did do this in my Windows days, but there doesn't seem to be an equivalent here.  Hence the need to make it myself!)

I've had some pretty good luck using md5deep (now availabile in the Dapper repositories!), and its recursive directory abilities.

2. If a file doesn't exist in the backup, but does in the source, I'll want to copy the file over.

Here's where I'm having trouble.  When I run md5deep on my directories, it can generate the hashes for all the files, and even show when two are different.  What it doesn't to is indicate when one file is simply missing.  What command can I use to determine what files exist in one place, but not the other?

3. If a file doesn't exist in the source, but does in the backup, prompt me for what to do about it.

This should be fairly easy, once I've got a solution for #2!

Thanks in advance for any help or pointers in the right direction.  Once I have this working, I'd also like to use the same structure to maintain a backup of my /home directory on a separate drive.

---

