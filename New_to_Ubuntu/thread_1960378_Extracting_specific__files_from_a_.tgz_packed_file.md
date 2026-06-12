---
title: "Extracting specific  files from a *.tgz packed file"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by newport_j on 2012-04-17
I have several *.tgz files that I do not want to unpack. I do want to extract, if possible, some files and a directory from theses files if this is possible.
 
I have read about this and I believe it can be done. But how do i do it?
 
 
Thanks in advance.
 
Newport_j

---

### Post by JRV on 2012-04-17
Right click on it and select "Open in Archive Manager" then select the file you want to unzip.

---

### Post by cortman on 2012-04-17
^^ Right, or even just double click on it, browse through the files, select the certain file or folder and click "Extract".

---

### Post by newport_j on 2012-04-18
Please understand that I had a lot to backup so I had to break all of it up into smaller pieces. The tar file sizes were 4 GB, enough for one file onto one DVD.
 
Now when I went back to check on one of those pieces, by clicking on it as you said i got the following eroor.
 
 
tar : Unexpected EOF in archive
tar : Error is not recoverbale: exiting now
 
 
I do not believe that this error is unrecoverable, I just do not know what to do next. Should I put all the tar files (pieces really) back to together and then click on the newly rebuilt file?
 
Any help appreciated.
 
 
Newport_j

---

### Post by flurospar on 2012-04-18
> **newport_j said:**
> ... so I had to break all of it up into smaller pieces ...I put all the tar files (pieces really) back to together and then click on the newly rebuilt file?
 

What do you mean by breaking the tar into small pieces?

---

### Post by cortman on 2012-04-18
> **flurospar said:**
> What do you mean by breaking the tar into small pieces?

Indeed. ??
You extracted various bits from a tarball, edited them, and now want to reinsert them in the original tarball?

---

### Post by newport_j on 2012-04-18
The final compressed tar-ed file if not broken up would have been over 26 GB in size. It was a major backup of my whole Ubuntu system. I had to create pieces of it that could fit on a DVD; each was about 4 GBs.
 
So now I have 7 DVDs each containing a section of the backup. This was done correctly, I believe because I have done it before; put it back together. It is a simple straghtforward command to put the file back togehter. 
 
If they made optical storage disks as large a 30 GBs and I had one of the drives, then I would not have had to break the tarred file up. i had no such drive.
 
That is why I had to break a large file into smaller pieces. 
 
Newport_j

---

