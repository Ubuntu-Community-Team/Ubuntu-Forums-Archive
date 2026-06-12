---
title: "patch prerequisite"
date: 2018-12-30
forum: Packaging and Compiling Programs
---

### Post by luca31 on 2018-12-30
Hi all, I don't get how prereq of a patch are checked/applied

here's a stupid sample:

```


fusillator@catorcio:~/Code/diff$ cat patch.diff
Prereq: v0.2

diff -N -c old_v0.2/f1_v0.2 new/f1_v0.3
*** old_v0.2/f1_v0.2    2018-12-30 02:15:19.952007557 +0100
--- new/f1_v0.3    2018-12-30 01:37:38.253703121 +0100
***************
*** 1,4 ****
  a
  b
! f
  
--- 1,5 ----
  a
  b
! h
! p
  
diff -N -c old_v0.2/new new/new
*** old_v0.2/new    1970-01-01 01:00:00.000000000 +0100
--- new/new    2018-12-30 02:16:57.481122783 +0100
***************
*** 0 ****
--- 1,3 ----
+ z
+ y
+ x

fusillator@catorcio:~/Code/diff$ patch --verbose -p0 <patch.diff 
Hmm...  Looks like a new-style context diff to me...
The text leading up to this was:
--------------------------
|Prereq: v0.2
|
|diff -N -c old_v0.2/f1_v0.2 new/f1_v0.3
|*** old_v0.2/f1_v0.2    2018-12-30 02:15:19.952007557 +0100
|--- new/f1_v0.3    2018-12-30 01:37:38.253703121 +0100
--------------------------
This file doesn't appear to be the v0.2 version -- patch anyway? [n]

fusillator@catorcio:~/Code/diff$ ls -1 old_v0.2/*
old_v0.2/f1_v0.2  
old_v0.2/new

```

Could so enlighten me?
Moreover I would like to check the version only on the directory name.. not on the basename if possible.. 
Regards 

Luca

---

### Post by #&amp;thj^% on 2018-12-30
I Totally understand how you feel, it took a bit time to understand all of this. (And i still don't fully :) )
```
$ diff originaldirectory/ updateddirectory/
```

Note: if the directories you're comparing also include subdirectories, you should add the -r option to make diff compare the files in subdirectories, too.
More info found here: [https://linuxacademy.com/blog/linux/introduction-using-diff-and-patch/](https://linuxacademy.com/blog/linux/introduction-using-diff-and-patch/)

---

### Post by jeremy31 on 2018-12-30
I thought diff -u was more popular for making patches

---

### Post by #&amp;thj^% on 2018-12-30
> **jeremy31 said:**
> I thought diff -u was more popular for making patches
+1
I find that a lot of patches out there are created by "diff -urN". Or " diff -Naur "

---

### Post by luca31 on 2018-12-30
Hi all, thanks for the quick reply and the useful tutorial..
You're right, the best practice to apply patch on package requires to use the option you kindly suggest. 
-N to force the creation/deletion of file not present in the old/new release
-u use unified context
-r match also the subdirectories recursively
-a check also file with null bytes at the beginning (not recognized as text)

Anyway I need to clarify what I'm trying to probe... 
I took as a reference the info page, exactly the last two paragraphs of the section 11.3 Avoiding common mistake of the chapter Comparing and Merging files, that I hereby attach:

> 
   To save people from partially applying a patch before other patches
that should have gone before it, you can make the first patch in the
patch file update a file with a name like 'patchlevel.h' or 'version.c',
which contains a patch level or version number.  If the input file
contains the wrong version number, 'patch' will complain immediately.

An even clearer way to prevent this problem is to put a 'Prereq:'
line before the patch.  If the leading text in the patch file contains a
line that starts with 'Prereq:', 'patch' takes the next word from that
line (normally a version number) and checks whether the next input file
contains that word, preceded and followed by either white space or a
newline.  If not, 'patch' prompts you for confirmation before
proceeding.  This makes it difficult to accidentally apply patches in
the wrong order.


 now I don't get how to name the directory and/or files to make the version match
In my example I added a header Prereq: v0.2 in the patch file, and I tried to add the version as suffix to the directory and/or file name 
Unfortunately applying the patch the program doesn't match the version in any case...
Note that if I remove the Prereq line from the patch file or I let the program proceed the patch goes smootly, so the strip (-p) option seems right and the context option should not be a problem.
 
thanks again

---

### Post by #&amp;thj^% on 2018-12-30
Sorry I have no experince with the "Prereq".
But this may help hopefully, >>> this is just an example:
Say we are creating a patch for our kernel:
[list][*]Creating a patch

[*]The first thing to remember is to always keep an untouched, pristine version of the kernel source somewhere. Don't compile in it, don't edit any files in it, don't do anything to it - just copy it to make your working copy of the source tree. The original kernel source should be in a directory named linux.vanilla or linux.orig, and your working directory should be in the same directory as the original source. For example, if your pristine source is in /usr/src/linux.vanilla, your working source should be in /usr/src/ also.

[*]After you make your changes to your working copy, you'll create a patch using diff. Assuming that your working tree is named linux.new, you would run this command:
**_(NOTE this is just an example DO NOT COPY and PASTE)_**
```

  me@arch <~>$ diff -uNr linux.vanilla linux.new > patchfile

```
[*]All the differences between the original kernel source and your new kernel source are now in patchfile. NOTE: Do not ever create a patch with uneven directories, for example (DON'T do this):

```
me@arch <~>$ diff -uNr linux.vanilla working/usb/thing1/linux > patchfile
```

[*]This will not create a patch in the standard patch format and no one will bother trying out your patch since it's hard to apply.[/list]

---

### Post by luca31 on 2018-12-30
Thanks again for the explaination and your time
I glimped over the patch code (specifically the funcion plan_a plan_b in the inp.c set a variable found_revision in case the match was found..), and I got that I misunderstood completely the manual:
 the version/release number should be contained in the code to be matched.. I think it conceived to exploit some building system feature which appends the revision of the versioning system automatically but I need to deep further on this subject.. 
Anyway this is the proof on my stupid sample:

```

fusillator@catorcio:~/Code/diff$ cat patch.diff 
Prereq: v0.2
diff -Nur old/f1 new/f1
--- old/f1    2018-12-30 17:34:44.424772753 +0100
+++ new/f1    2018-12-30 17:35:06.017052439 +0100
@@ -1,4 +1,5 @@
-# Release v0.2
+#Release v0.3
 a
 b
-f
+h
+p
diff -Nur old/new new/new
--- old/new    1970-01-01 01:00:00.000000000 +0100
+++ new/new    2018-12-30 17:35:23.749281121 +0100
@@ -0,0 +1,4 @@
+#Release v0.3
+z
+y
+x

fusillator@catorcio:~/Code/diff$ patch --verbose -p0 < patch.diff 
Hmm...  Looks like a unified diff to me...
The text leading up to this was:
--------------------------
|Prereq: v0.2
|diff -Nur old/f1 new/f1
|--- old/f1    2018-12-30 17:34:44.424772753 +0100
|+++ new/f1    2018-12-30 17:35:06.017052439 +0100
--------------------------
Good.  This file appears to be the v0.2 version.
patching file old/f1
Using Plan A...
Hunk #1 succeeded at 1.
Hmm...  The next patch looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Nur old/new new/new
|--- old/new    1970-01-01 01:00:00.000000000 +0100
|+++ new/new    2018-12-30 17:35:23.749281121 +0100
--------------------------
patching file old/new
Using Plan A...
Hunk #1 succeeded at 1.
done

```

Cool... I need to investigate more on building system and the best practice to append the release version..
thanks again for the support
 Best wishes

Luca

---

### Post by luca31 on 2018-12-31
Hi again, in order to handle the dependencies and priorities of the different patches another utility can be used to do the dirty work: quilt
All subsequent modifications on a base code get separated in more patch files handled in a stack structure and automatically created/applied/removed in series following a given order. Diff and patch are used to accomplish these tasks under the hood 
The documentation is available in the file /usr/share/doc/quilt/quilt.pdf.gz
I need to deep further and get if it's automatically used in the installation process of the source package.

---

