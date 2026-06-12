---
title: "remove files on NTFS with \n in the filename"
date: 2014-10-03
forum: New to Ubuntu
---

### Post by elang on 2014-10-03
I was moving files using Windows (had to at that time) from one NTFS partition to another but the computer switched off.
Some files have been transferred, but some remain. I'm not able to delete them because they now have `\n` in the filename.
I have a backup of the files, so I **only want to delete the files**.


[LIST=1]
[*]   The output of **ls -b** shows me there are some **\n** characters in the filenames (1 folder + 2 PDF files)
```
$ ls -b
3316546202581         Rapid\ 3D\ Face\ Modeling\ using\ a\ Frontal\ Face\ and\ a\ Profile\ Face\ for\nAccurate\ 2D\ Pose\ Synthesis\n.pdf
3D\ Face\ Reconstruction\ from\ Single\ 2D\ Image\ based\ on\ Robust\ Facial\nFeature\ Points\ Extraction\ and\ Generic\ Wire\ Frame\ Model\n.pdf

``` 
[*]Attempt to remove everything was in vain
```
$ rm *
rm: cannot remove `33316546202581': Is a directory
rm: cannot remove `3D Face Reconstruction from Single 2D Image based on Robust Facial\nFeature Points Extraction and Generic Wire Frame Model\n.pdf': No such file or directory
rm: cannot remove `Rapid 3D Face Modeling using a Frontal Face and a Profile Face for\nAccurate 2D Pose Synthesis\n.pdf': No such file or directory

``` 
[*]The output of **ls -ali** tells me the 2 PDF files have no INODES !!!
I noted that the first few lines of output actually goto newlines, while further down (last 2 lines) **\n** is shown as **?**, but didn't know what to make of it.
```
$ ls -ali
ls: cannot access 3D Face Reconstruction from Single 2D Image based on Robust Facial
Feature Points Extraction and Generic Wire Frame Model
.pdf: No such file or directory
ls: cannot access Rapid 3D Face Modeling using a Frontal Face and a Profile Face for
Accurate 2D Pose Synthesis
.pdf: No such file or directory
total 12
281474976785007 drwxrwxrwx+ 1 Administrators root 0 Oct  3 20:18 .
281474976730073 drwxrwxrwx+ 1 Administrators root 0 Oct  3 20:18 ..
1688849860279472 drwxrwxrwx+ 1 Administrators root 0 Oct  3 20:15 33316546202581
? -?????????? ? ?              ?    ?            ? 3D Face Reconstruction from Single 2D Image based on Robust Facial?Feature Points Extraction and Generic Wire Frame Model?.pdf
? -?????????? ? ?              ?    ?            ? Rapid 3D Face Modeling using a Frontal Face and a Profile Face for?Accurate 2D Pose Synthesis?.pdf
``` 
[/LIST]
 
I rally want to delete these files. How do I do it?

---

### Post by matt_symes on 2014-10-03
Hi

> .... NTFS partition .....

Can you just reformat that one partition and then restore the files from backup ?

Kind regards

---

### Post by yancek on 2014-10-03
You need to delete the pdf files first as you can see from your post above, you need to use:  rmdir   to remove a directory and the directory needs to be empty.  Use double quotes around the files like this:

```
rm "3D Face Reconstruction from Single 2D Image based on Robust Facial\\nFeature Points Extraction and Generic Wire Frame Model\\n.pdf"
``` 

Obviously you need to be in the 3316546202581 directory.  When you run the rm command above you will get the following, enter y for yes after the ? mark prompt and hit the Enter key.  It's deleted, repeat for other .pdf.

```
rm: remove regular file '3D Face Reconstruction from Single 2D Image based on Robust  Facial\\nFeature Points Extraction and Generic Wire Frame Model\\n.pdf'? y
```  

The go to the directory in which the "3316546202581" directory is and run the command:  rmdir 3316546202581 

rmdir to remove directories, rm to remove files.  If this isn't in your /home/user directory you will likely need to use root/sudo.
Did you try deleting them in a file manager as the spaces should not matter in that case.

---

