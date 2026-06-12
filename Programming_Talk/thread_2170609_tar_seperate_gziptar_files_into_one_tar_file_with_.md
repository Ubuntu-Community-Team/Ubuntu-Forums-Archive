---
title: "tar seperate gzip/tar files into one tar file with one command"
date: 2013-08-26
forum: Programming Talk
---

### Post by pharubu on 2013-08-26
I'm running out of room on the drives and can no longer do separate
tar/gzip files before combining all gzip/tar files into one tar file.  

Is it possible to pipe a separate gzip/tar straight into a combined tar file ?

**Currently**:
#!/bin/sh
fsFilePath="/var/backups/"
fsFileName="WWWBackup.tar.gz"
fsFileLoc="${fsFilePath}${fsFileName}"
pg_dump --blobs DB1 | gzip -c > ${fsFilePath}DB1Dump.out.gz
pg_dump --blobs DB2 | gzip -c > ${fsFilePath}DB2Dump.out.gz
pg_dump --blobs DB3 | gzip -c > ${fsFilePath}DB3Dump.out.gz

tar -czpf ${fsFilePath}[www.tar.gz](www.tar.gz) -C / var/www
tar -czpf ${fsFilePath}apache2.tar.gz -C / etc/apache2

fsFilePathRemoveFirstFwdSlash=`echo ${fsFilePath} | sed 's/^.//'`
cd /
tar -czpf ${fsFileLoc} ${fsFilePathRemoveFirstFwdSlash}*
cd ${fsFilePath}

ls ${fsFilePath}* | grep -v ${fsFileLoc} | xargs rm -f

**To something like**:
pg_dump --blobs DB1 | gzip -c DB1Dump.out.gz | tar -[COLOR=#ff0000]**c**[/COLOR]zpf combined.tar
pg_dump --blobs DB2 | gzip -c DB2Dump.out.gz | tar -[COLOR=#ff0000]**u**[/COLOR]zpf combined.tar
pg_dump --blobs DB3 | gzip -c DB3Dump.out.gz | tar -[COLOR=#ff0000]**u**[/COLOR]zpf combined.tar

tar -czpf ${fsFilePath}[www.tar.gz](www.tar.gz) -C / var/www | tar -[COLOR=#ff0000]**u**[/COLOR]zpf combined.tar
tar -czpf ${fsFilePath}apache2.tar.gz -C / etc/apache2 | tar -[COLOR=#ff0000]**u**[/COLOR]zpf combined.tar

Thanks

---

### Post by evilsoup on 2013-08-27
What's the advantage to doing this rather than just putting all the files in a tarball and compressing that (which could be done with a single tar command)?

---

### Post by Bucky Ball on 2013-08-27
*Thread moved to **Programming Talk**.*

You have more chance of getting help here. Unsure why this was originally posted in **ABS.**

---

### Post by ofnuts on 2013-08-27
Use tar --append?

[http://www.gnu.org/software/tar/manual/html_node/append.html#SEC58](http://www.gnu.org/software/tar/manual/html_node/append.html#SEC58)

---

### Post by pharubu on 2013-08-27
The best way to describe what I was trying to do is to think of it like a bag full of bite sized mini bars.
I didnt want to warp up the bite sized treats first and then individually put them in the bag.
I wanted to wrap the bite sized snacks inside the bag itself thereby saving space on the harddrive.

What I have done is to:
- Dump/gzip all the small DB's and website directories into their own bite sized tar files. 
- tar the bite sized tar files into the one combined tar file. 
- Remove the mini tar files 
- Do a gzip/dump of the big database 
- Add it to the combined tar file
- Remove the big DB tar file

It will work for now however i'd like to know if its possible to wrap files into a tar and put them straight into a combined tar.

---

### Post by ofnuts on 2013-08-29
Use "tar -- concatenate"?

---

