---
title: "How to extract multiple volume tar archives, with multiple files"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by acl123 on 2008-05-11
Hi, I followed this guide ([http://www.cgi-interactive-uk.com/splitting_large_files.html](http://www.cgi-interactive-uk.com/splitting_large_files.html)) to archive some files of mine into multiple volumes. Now I need to extract them but the guide only shows what to do when only one file is tarred. I tarred multiple files into the one set of archives and it is not clear how I can extract them.
I've tried just specifying the directory where I want the files to be extracted to: **tar -x -M --file=MyTarVol1.tar /outputdir/ **... but it just sits doing nothing.

---

### Post by Monicker on 2008-05-11
That link does show how to extract the files

```

Putting the File Back Together

The process is similar when putting the large file back together from its split-up files. Below is the syntax used to re-create the large file from the disk1.tar and disk2.tar images.

C:\tar>tar -x -M --file=disk1.tar largefile.tgz
Prepare volume #2 for disk1.tar and hit return: n disk2.tar
Prepare volume #2 for disk2.tar and hit return:
```


You should verify that you actually split it in the way that they described.

---

### Post by acl123 on 2008-05-12
If you look at the link closely, when it talks about untarring, the output file "largefile.tgz" is specified in the command. This is not necessary - generally one doesn't care what files are actually packaged in the tar file, you just want to extract everything in it.
As it turns out, I was doing the right thing. The tar program looks like it had hung, but it was actually doing something. After 5 minutes it asked for the next volume like it should. Obviously the tar developers didn't complete their UI 101 classes.

---

