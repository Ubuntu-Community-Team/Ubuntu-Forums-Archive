---
title: "HOWTO : Solve AptOnCD error - &quot;E: Cannot find filename or size tag&quot;"
date: 2008-09-13
forum: Outdated Tutorials &amp; Tips
---

### Post by bimaljr on 2008-09-13
Hi,
I had created a Repository DVD with APTonCD 0.1.98

But when I was go to add this DVD as repository CD-ROM, I got this error :
> E: Cannot find filename or size tag

The problem is cached-name of .DEB files. You must remove **1%3a**, **2%3a**, **3%3a**... till **9%3a** from all .DEB file names.

*There is one problem too. You must create another DVD after doing this. Your old DVD with the error will not repair.*

**_Here is the step-by-step:_**

1) First, just go to cache folder with this command :
> cd /var/cache/apt/

2) Now CHMOD "archives" folder to make permission to rename files inside this folder.
> sudo chmod -R 777 archives/

3) Now, do this all commands one by one in terminal/konsole to rename all .DEB files :
> for FILE in $(find . -type f -name '*1%3a*'); do NEWNAME=$(echo $FILE|sed s/'1%3a'//); mv -v $FILE $NEWNAME; done

> for FILE in $(find . -type f -name '*2%3a*'); do NEWNAME=$(echo $FILE|sed s/'2%3a'//); mv -v $FILE $NEWNAME; done

> for FILE in $(find . -type f -name '*3%3a*'); do NEWNAME=$(echo $FILE|sed s/'3%3a'//); mv -v $FILE $NEWNAME; done

> for FILE in $(find . -type f -name '*4%3a*'); do NEWNAME=$(echo $FILE|sed s/'4%3a'//); mv -v $FILE $NEWNAME; done

> for FILE in $(find . -type f -name '*5%3a*'); do NEWNAME=$(echo $FILE|sed s/'5%3a'//); mv -v $FILE $NEWNAME; done

> for FILE in $(find . -type f -name '*6%3a*'); do NEWNAME=$(echo $FILE|sed s/'6%3a'//); mv -v $FILE $NEWNAME; done

> for FILE in $(find . -type f -name '*7%3a*'); do NEWNAME=$(echo $FILE|sed s/'7%3a'//); mv -v $FILE $NEWNAME; done

> for FILE in $(find . -type f -name '*8%3a*'); do NEWNAME=$(echo $FILE|sed s/'8%3a'//); mv -v $FILE $NEWNAME; done

> for FILE in $(find . -type f -name '*9%3a*'); do NEWNAME=$(echo $FILE|sed s/'9%3a'//); mv -v $FILE $NEWNAME; done

(Help : This command will remove the "1%3a" with "2%3a" "3%3a" "4%3a"... till "9%3a" )

4) DONE...

---

