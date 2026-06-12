---
title: "Moving files and directories with similar names to parent directory with similar name"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by mike196 on 2014-08-12
Hello all,

I'm trying to move multiple files and folders at once that have common elements.  Normally I would use the following:

```
mv *IDENTIFIER* /dest/dir
```

However, I have a problem now in that the destination directory has the same identifier.  Obviously I get a "cannot move to a subdirectory of itself" error.  So my question is: if I have files/directories like this

```

Title #this is the destination directory
Title.ep1.avi
title.ep2 #this is a directory
title.ep3.mp4

```

How can I get the last three files/directories into the destination directory?

---

### Post by mooreted on 2014-08-12
I know everything in Linux is a file, but naming your directories the same as files sounds kind of confusing. Maybe something like this:

find . -type f -iname "*title.ep*" -exec mv {} /title.ep2 \;

So, what that does: Find in the current directory files only with upper or lower case names that contain "title.ep" and move them to "title.ep2"

You might want to test that before you try it as it could mess up your file structure. Maybe put some in a test directory and run it.

---

### Post by Vaphell on 2014-08-12
```
for f in [Tt]itle*; do mv "$f" Title; done
```

---

### Post by mike196 on 2014-08-13
> **mooreted said:**
> I know everything in Linux is a file, but naming your directories the same as files sounds kind of confusing. Maybe something like this:

find . -type f -iname "*title.ep*" -exec mv {} /title.ep2 \;

So, what that does: Find in the current directory files only with upper or lower case names that contain "title.ep" and move them to "title.ep2"

You might want to test that before you try it as it could mess up your file structure. Maybe put some in a test directory and run it.

I have a lot of TV media on my server and the individual episodes have the title in the file name, and I want all the episodes for a particular show in a directory with the title of the show.

Neither one of the commands worked, but they gave me a place to start.  In the end, the following worked:

```
find -type f -iname "*[Tt]itle*" -exec mv {} "/Title" \;
```

Of course, I learned the hard way to make sure the destination directory actually existed or I lose my files.  Ah well, c'est la vie.

Thanks for the help!

---

### Post by mooreted on 2014-08-13
> **mike196 said:**
> I have a lot of TV media on my server and the individual episodes have the title in the file name, and I want all the episodes for a particular show in a directory with the title of the show.

Neither one of the commands worked, but they gave me a place to start.  In the end, the following worked:

```
find -type f -iname "*[Tt]itle*" -exec mv {} "/Title" \;
```

Of course, I learned the hard way to make sure the destination directory actually existed or I lose my files.  Ah well, c'est la vie.

Thanks for the help!

Awesome, glad you got it working.

---

