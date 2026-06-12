---
title: "Help with 'find' and 'cpio'"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Offramp on 2008-09-15
Hi all,

I am trying to organise my thesis references using the find and cpio commands. On my external hard drive I have a shambolic grouping of pdf files amongst many directories.  I thought that I could use the find and cpio files to gather all the pdf files and place them in one directory for later sorting.

The following command worked great, however it maintained the same directory structure at the destination.

```
find -name *.pdf | cpio --null --sparse -pvd ~/MSc
```

A scan of the man page for find indicates that I can use the -print (with options) to strip directory names.  I tried the following command, the file name is displayed without directories and on a new line however cpio complains that the file name is too long. I know that I need to let cpio know the filename is finished with a null, however I cannot seem to get this last part to work?

```
find -name *.pdf -depth -printf "%f\n\r\" | cpio --null --sparse -pvd ~/MSc
```


Am I going about this the correct way?  Any assistance would be appreciated,

Cheers

---

### Post by andrewc6l on 2008-09-15
If this is something you're just going to do once or just a few times, I'd recommend

find / -name \*.pdf -print | gawk '{ print "cp", $1, "~/my-dest-pdf-dir" }' > ~/copy-pdf-script
sh ~/copy-pdf-script

If it's something you'll do more often, you could think about automating...

---

### Post by Offramp on 2008-09-15
> **andrewc6l said:**
> If this is something you're just going to do once or just a few times, I'd recommend

find / -name \*.pdf -print | gawk '{ print "cp", $1, "~/my-dest-pdf-dir" }' > ~/copy-pdf-script
sh ~/copy-pdf-script

If it's something you'll do more often, you could think about automating...
Hi,

Thanks for the reply.  I have not used gawk before so this should broaded my horizons further!  This is a once off and will free up a few 10s of GB on my poorly organised drive.

Cheers

---

### Post by nowshining on 2008-09-15
by the way if you add/remove files/folders find will always show the same items until you run sudo updatedb. ;)

---

