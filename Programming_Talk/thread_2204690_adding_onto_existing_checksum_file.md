---
title: "adding onto existing checksum file"
date: 2014-02-09
forum: Programming Talk
---

### Post by gamer82987 on 2014-02-09
I'm trying to create a checksum file for file verification purposes. I trying to figure out how to add onto an exisiting checksum file without recalculating the hashes everytime.

ls of directory
```

file1.txt
file2.log
file3.conf
file4.bak
file5.tmp
file6.tar

```

crc32.sfv
```

file1.txt 1234ABCD
file2.log ABCDEF12
file3.conf 12345ABC

```

code I use to calculate crc32 hash and output to file
```
rhash -C -r --sfv * > crc32.sfv
```

i dont know how to create a pattern that filters out existing files that is already in the sfv. The reason I need this is that there are alot of files and it takes a while to calculate the checksums over and over again.

thanks in advanced for the help.

---

### Post by sudodus on 2014-02-10
Welcome to the Ubuntu Forums :-)

I usually make a file containing one line with the checksum and name of each file. Then it is easy to add a new line with checksum and the file name for a new file, that you want to include. (And I use md5sum, but there are many checksum tools, use the one you prefer.)

Example: Watch the checksum files (one of them is signed using gpg)

```

md5sums-phillw.txt
md5sums.txt.asc

```
at the following web-site

[http://phillw.net/isos/one-button-installer/](http://phillw.net/isos/one-button-installer/)

The whole file can be created with the script **2md5sums-phillw.bash**
```

find */ -type f -exec md5sum {} \;|sort -k2 > md5sums-phillw.txt
```

but you can run **md5sum** for a single file for example

```
md5sum scripts/mkusb
```

and put it into md5sums-phillw.txt with an editor, or append it to the end of the file with  **>>**

```
md5sum scripts/mkusb >> md5sums-phillw.txt
```

---

### Post by sudodus on 2014-02-10
*Edit*: I suggested a simple script, but removed it, since *ofnuts* has a better approach

---

### Post by ofnuts on 2014-02-10
MD5 is the standard way to check file integrity (at least against "accidents", it's no longer completely hacker-proof these days).

I'm not convinced that your logic is right, because a changed file would be in the checksum file and its checksum would have to be recomputed anyway. The safest method is hefore to recompute everything. But unless something tweaks the time stamps on purpose you can also consider only the files that have a change date more recent than your checksum file (find -cnewer $checkfile) to spot files that have been added or changed since the last time you ran the checksum. 

You cannot add the checksum blindly to the existing checksum file because you would end up with two entries for the same file if a file is modified/replaced. But instead of editing the checksum file line by line, you can create a new checksum file for only the changed files, and then merge it intelligently with the old one:

```

cat new.md5 old.md5 | sort -c -k 2 

```

---

### Post by sudodus on 2014-02-10
> **ofnuts said:**
> I'm not convinced that your logic is right, because a changed file would be in the checksum file and its checksum would have to be recomputed anyway. The safest method is hefore to recompute everything. 

I must agree with ofnuts. My quick fix (in post #3) for adding new checksums automatically is not complete, and it is probably difficult to make it work for 'all possible cases'.

---

### Post by ofnuts on 2014-02-10
To be a bit more specific, assuming your md5sum file is in files.md5:

```

# compute the sums for the changed/new  stuff
find . -maxdepth 1 -type f ! -name "*.md5" -cnewer files.md5 -exec md5sum {} \+ >added.md5

# merge the two MD5 files
sort -k 2 -u added.md5 files.md5 > combined.md5
rm files.md5 added.md5
mv combined.md5 files.md5

```

To initialize the MD5 file, make sure the files names have a leading "./": "md5sum ./*"

Edit: "find" command above corrected.

---

### Post by gamer82987 on 2014-02-11
First off, thank you for the prompt response! I will try this as soon as I get home from work.

The reason i went for crc32 is that i need a simple and fast way to make sure the file hasn't corrupted. Since these are going to be huge files, i don't need anything too robust i thought a crc32 check would work just fine. However, i am open to using md5

The files are going into an archive and I need a quick and simple way to guard against bit rot, and quickly replace corrupted files.

I am not too familiar with the find command. I understand the merge portion of the code, But I'm going to need help deciphering the find line. 

Thank you!

---

### Post by Vaphell on 2014-02-11
```

-maxdepth 1         # how deep in the directory tree (1 level tops = current dir)
-type f             # file
!                   # not, inverts following condition, -name in this case
-name "*.md5"       # names ending with .md5
-cnewer files.md5   # newer than files.md5 (last change timestamp)
-exec md5sum {} \+  # md5sum on matching elements
>added.md5          # redirect output to added.mp5
```

---

### Post by ofnuts on 2014-02-11
Ninja'ed you... :)

---

### Post by gamer82987 on 2014-02-12
Thank you all for the help. It's greatly appreciated :)

---

