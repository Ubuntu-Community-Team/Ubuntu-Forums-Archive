---
title: "Problems with Tar (Bash)"
date: 2009-04-24
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-04-24
Ey guys having a little trouble with appending with tar...

```

$ tar -cvzf TEST.tar.gz megaZORD.sfv 
megaZORD.sfv
$ tar -Af TEST.tar.gz meta.txt 
tar: Cannot update compressed archives
tar: Error is not recoverable: exiting now

```

What am I doing wrong? I have tried multiple variations and already tried google to no avail. If I remember correctly on one site it said you cannot append to compressed files... is this true? Thanks!

---

### Post by Arndt on 2009-04-24
> **StunnerAlpha said:**
> Ey guys having a little trouble with appending with tar...

```

$ tar -cvzf TEST.tar.gz megaZORD.sfv 
megaZORD.sfv
$ tar -Af TEST.tar.gz meta.txt 
tar: Cannot update compressed archives
tar: Error is not recoverable: exiting now

```

What am I doing wrong? I have tried multiple variations and already tried google to no avail. If I remember correctly on one site it said you cannot append to compressed files... is this true? Thanks!

If they said that and the program says it too, it's probably true. And it makes sense too. 'tar' would have to unpack the archive, add the file and pack it again, so they must have decided that the user can do those steps himself.

---

### Post by StunnerAlpha on 2009-04-24
How would I go bout doing it manually then? I don't have the commands, but I have tried a ton without the "-z" flag and it wasn't workin...

---

### Post by albinootje on 2009-04-24
> **StunnerAlpha said:**
> How would I go bout doing it manually then? I don't have the commands, but I have tried a ton without the "-z" flag and it wasn't workin...

I think you have to realize that tar and gzip (and gunzip) are two different programs.
The error message probably refers to the tar file being gzipped.
Can you try to gunzip the .tar.gz file, and then use -A to add your file to the tar file ?
When that works, you can use gzip again (gzip -9) to compress the updated tar file.

---

### Post by StunnerAlpha on 2009-04-24
> **albinootje said:**
> I think you have to realize that tar and gzip (and gunzip) are two different programs.
The error message probably refers to the tar file being gzipped.
Can you try to gunzip the .tar.gz file, and then use -A to add your file to the tar file ?
When that works, you can use gzip again (gzip -9) to compress the updated tar file.
This is what I did:
```

$ tar -czvf TEST.tar.gz megaZORD.sfv 
megaZORD.sfv
$ ls
[1-5]          cleaner.sh  makill.mp3    r            touchy
bombackaz.nfo  emptry      megaZORD.sfv  test.sh      zipfile.tar.gz
chaat          empty1      meta.txt      TEST.tar.gz
$ gunzip TEST.tar.gz 
$ ls
[1-5]          cleaner.sh  makill.mp3    r         touchy
bombackaz.nfo  emptry      megaZORD.sfv  test.sh   zipfile.tar.gz
chaat          empty1      meta.txt      TEST.tar
$ tar -Af TEST.tar bombackaz.nfo 
$ ls
[1-5]          cleaner.sh  makill.mp3    r         touchy
bombackaz.nfo  emptry      megaZORD.sfv  test.sh   zipfile.tar.gz
chaat          empty1      meta.txt      TEST.tar
$ gzip -9 TEST.tar
$ ls
[1-5]          cleaner.sh  makill.mp3    r            touchy
bombackaz.nfo  emptry      megaZORD.sfv  test.sh      zipfile.tar.gz
chaat          empty1      meta.txt      TEST.tar.gz
$ vi TEST.tar.gz 
(As vi opens this comes up)Error detected while processing /usr/share/vim/vim71/autoload/tar.vim: 
line 30:
(autoload/tar.vim) need vim v7.1 with patchlevel 299

```
And in the vim file only megaZORD.sfv shows up as in the tarred file. So I don't think that method worked. Thanks for the response. Any other suggestions?

---

### Post by dwhitney67 on 2009-04-24
Why are you vim-ing a compressed tar-ball?

---

### Post by StunnerAlpha on 2009-04-24
> **dwhitney67 said:**
> Why are you vim-ing a compressed tar-ball?
How else to view what its contents are? I don't know... other students do it... works with .tar.gz files.

---

### Post by dwhitney67 on 2009-04-24
```

tar tzvf tarball.tar.gz

```

---

### Post by StunnerAlpha on 2009-04-24
> **dwhitney67 said:**
> ```

tar tzvf tarball.tar.gz

```
Hmm...
```

$ ls
[1-5]          cleaner.sh  makill.mp3    r        zipfile.tar.gz
bombackaz.nfo  emptry      megaZORD.sfv  test.sh
chaat          empty1      meta.txt      touchy
$ tar -tzvf tarball.tgz megaZORD.sfv
tar: tarball.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: megaZORD.sfv: Not found in archive
tar: Error exit delayed from previous errors
$ tar -tzvf tarball.tgz
tar: tarball.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
$ 

```

What am I doing wrong? Thanks for the responses!

---

### Post by dwhitney67 on 2009-04-24
I edited my earlier response to match your file extension; with the 'tar.gz'.  It seems you quoted the command correctly, but perhaps had in your mind the '.tgz'.

Anyhow, retry but with the correct tar-ball extension that you are using.

Btw, the 't' option tells you what is in the tar-ball; the 'z' option uncompresses the tar-ball; the 'v' is for verbose.  And the 'f' is for file (?).

---

### Post by StunnerAlpha on 2009-04-24
> **dwhitney67 said:**
> I edited my earlier response to match your file extension; with the 'tar.gz'.  It seems you quoted the command correctly, but perhaps had in your mind the '.tgz'.

Anyhow, retry but with the correct tar-ball extension that you are using.

Btw, the 't' option tells you what is in the tar-ball; the 'z' option uncompresses the tar-ball; the 'v' is for verbose.  And the 'f' is for file (?).
Ah ok thanks. Awesome it worked! One last question... After adding everything i want to the tar archive how do I go about compressing it furthur into gzip?

---

### Post by dwhitney67 on 2009-04-24
I thought you had that sorted out?

```

tar cf file.tar file(s)

gzip -9 file.tar

```

Then later:
```

gunzip file.tar.gz

tar rf file.tar newfile(s)

gzip -9 file.tar

```


P.S.  The [-]A option is used to concatenate tar-balls; not to concatenate individual file(s) into an existing tarball.  I believe the correct option you want is the [-]r.  The dashes (-) are optional, btw.

P.S.S.  vim works on my system; perhaps you are using an older version?  I have:
```

VIM - Vi IMproved 7.0 (2006 May 7, compiled Nov 25 2008 11:43:45)
Included patches: 1, 3-4, 7-9, 11, 13-17, 19-26, 29-31, 34-44, 47, 50-56, 58-64, 66-73, 75, 77-92, 94-107, 109, 202, 234-235, 237

```

---

### Post by StunnerAlpha on 2009-04-24
Yeah I kinda did get it sorted out after I posted it... that whole run around kind of confused me... sorry. That summary you provided is perfect, really appreciate it. I will check what version of ViM I have tomorrow... just turned off my working machine. Once again, thanks for all the help!

---

### Post by StunnerAlpha on 2009-04-24
> **dwhitney67 said:**
> I thought you had that sorted out?

```

tar cf file.tar file(s)

gzip -9 file.tar

```

Then later:
```

gunzip file.tar.gz

tar rf file.tar newfile(s)

gzip -9 file.tar

```


P.S.  The [-]A option is used to concatenate tar-balls; not to concatenate individual file(s) into an existing tarball.  I believe the correct option you want is the [-]r.  The dashes (-) are optional, btw.

P.S.S.  vim works on my system; perhaps you are using an older version?  I have:
```

VIM - Vi IMproved 7.0 (2006 May 7, compiled Nov 25 2008 11:43:45)
Included patches: 1, 3-4, 7-9, 11, 13-17, 19-26, 29-31, 34-44, 47, 50-56, 58-64, 66-73, 75, 77-92, 94-107, 109, 202, 234-235, 237

```
Actually I tried incororating this into my bash script and it kept on giving me issues with gzip. Here is the function in my bash script that I call when tarring(insurance is just a flag to indicate if user wishes to tar or not):
```

tarArchive(){
if [ "$insurance" == "1" ]; then
	if [ -e "$backupname" ]; then
		tar -cf "$backupname".tar "$filename"
		gzip -9 "$backupname".tar
	else
		gunzip "$backupname"
		tar -rf "$backupname".tar "$filename"
		gzip -9 "$backupname".tar
	fi
fi
}

```

Here is the output I get:
```

----------------MENU-----------------
2.Delete .nfo .sfv .txt .m3u files
1.Search and remove empty folders
0.Exit script
-------------------------------------
Select option: 2
Do you want this script to make a backup of everything you delete within this function for insurance reasons?(Y/N)y
Enter the name of the backup: TEST  
Do you wish to remove ./megaZORD.sfv?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
rm ./megaZORD.sfv
Do you wish to remove ./chaat/test.nfo?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
gzip: TEST.tar.gz already exists; do you wish to overwrite (y or n)? y
rm ./chaat/test.nfo
Do you wish to remove ./chaat/chutney/brazton.m3u?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
gzip: TEST.tar.gz already exists; do you wish to overwrite (y or n)? y
rm ./chaat/chutney/brazton.m3u
Do you wish to remove ./chaat/mastaz.m3u?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
gzip: TEST.tar.gz already exists; do you wish to overwrite (y or n)? y
rm ./chaat/mastaz.m3u
Do you wish to remove ./chaat/killz.m3u?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
gzip: TEST.tar.gz already exists; do you wish to overwrite (y or n)? y
rm ./chaat/killz.m3u
Do you wish to remove ./meta.txt?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
gzip: TEST.tar.gz already exists; do you wish to overwrite (y or n)? y
rm ./meta.txt
Do you wish to remove ./bombackaz.nfo?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
gzip: TEST.tar.gz already exists; do you wish to overwrite (y or n)? y
rm ./bombackaz.nfo
DONE(hit enter)

```
And the contents of the tar file I created with this is:
```

$ tar tvf TEST.tar.gz 
-rw-r--r-- aaron/aaron       0 2009-04-23 22:27 ./bombackaz.nfo

```
I have experimented with changing the file extensions so many times to get rid of this problem that I have lost track of what I have done... also for some reason it doesn't want to append with the -r it just seems to overwrite the tar contents. Any help would be much appreciated! Thanks!

---

### Post by StunnerAlpha on 2009-04-24
> **StunnerAlpha said:**
> Actually I tried incororating this into my bash script and it kept on giving me issues with gzip. Here is the function in my bash script that I call when tarring(insurance is just a flag to indicate if user wishes to tar or not):
```

tarArchive(){
if [ "$insurance" == "1" ]; then
	if [ -e "$backupname" ]; then
		tar -cf "$backupname".tar "$filename"
		gzip -9 "$backupname".tar
	else
		gunzip "$backupname"
		tar -rf "$backupname".tar "$filename"
		gzip -9 "$backupname".tar
	fi
fi
}

```

Here is the output I get:
```

----------------MENU-----------------
2.Delete .nfo .sfv .txt .m3u files
1.Search and remove empty folders
0.Exit script
-------------------------------------
Select option: 2
Do you want this script to make a backup of everything you delete within this function for insurance reasons?(Y/N)y
Enter the name of the backup: TEST  
Do you wish to remove ./megaZORD.sfv?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
rm ./megaZORD.sfv
Do you wish to remove ./chaat/test.nfo?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
gzip: TEST.tar.gz already exists; do you wish to overwrite (y or n)? y
rm ./chaat/test.nfo
Do you wish to remove ./chaat/chutney/brazton.m3u?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
gzip: TEST.tar.gz already exists; do you wish to overwrite (y or n)? y
rm ./chaat/chutney/brazton.m3u
Do you wish to remove ./chaat/mastaz.m3u?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
gzip: TEST.tar.gz already exists; do you wish to overwrite (y or n)? y
rm ./chaat/mastaz.m3u
Do you wish to remove ./chaat/killz.m3u?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
gzip: TEST.tar.gz already exists; do you wish to overwrite (y or n)? y
rm ./chaat/killz.m3u
Do you wish to remove ./meta.txt?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
gzip: TEST.tar.gz already exists; do you wish to overwrite (y or n)? y
rm ./meta.txt
Do you wish to remove ./bombackaz.nfo?(Y/N/C for cancel)y
gzip: TEST.gz: No such file or directory
gzip: TEST.tar.gz already exists; do you wish to overwrite (y or n)? y
rm ./bombackaz.nfo
DONE(hit enter)

```
And the contents of the tar file I created with this is:
```

$ tar tvf TEST.tar.gz 
-rw-r--r-- aaron/aaron       0 2009-04-23 22:27 ./bombackaz.nfo

```
I have experimented with changing the file extensions so many times to get rid of this problem that I have lost track of what I have done... also for some reason it doesn't want to append with the -r it just seems to overwrite the tar contents. Any help would be much appreciated! Thanks!
Nevermind I think I got it I had to change my code to this:
```

tarArchive(){
if [ "$insurance" == "1" ]; then
	if [ -e "$backupname" ]; then
		tar -cf "$backupname".tar "$filename"
		gzip -9 "$backupname".tar
	else
		gunzip "$backupname".tar.gz
		tar -rf "$backupname".tar "$filename"
		gzip -9 "$backupname".tar
	fi
fi
}

```

Here is the output of my program now:
```

----------------MENU-----------------
2.Delete .nfo .sfv .txt .m3u files
1.Search and remove empty folders
0.Exit script
-------------------------------------
Select option: 2
Do you want this script to make a backup of everything you delete within this function for insurance reasons?(Y/N)y
Enter the name of the backup: testing
Do you wish to remove ./megaZORD.sfv?(Y/N/C for cancel)y
gzip: testing.tar.gz: No such file or directory
rm ./megaZORD.sfv
Do you wish to remove ./chaat/test.nfo?(Y/N/C for cancel)y
rm ./chaat/test.nfo
Do you wish to remove ./chaat/chutney/brazton.m3u?(Y/N/C for cancel)y
rm ./chaat/chutney/brazton.m3u
Do you wish to remove ./chaat/mastaz.m3u?(Y/N/C for cancel)y
rm ./chaat/mastaz.m3u
Do you wish to remove ./chaat/killz.m3u?(Y/N/C for cancel)y
rm ./chaat/killz.m3u
Do you wish to remove ./meta.txt?(Y/N/C for cancel)y
rm ./meta.txt
Do you wish to remove ./bombackaz.nfo?(Y/N/C for cancel)y
rm ./bombackaz.nfo
DONE(hit enter)

```
And what is contained in the "tarball" as you guys call it: :)
```

t$ tar tvf testing.tar.gz 
-rw-r--r-- aaron/aaron       0 2009-04-23 22:27 ./megaZORD.sfv
-rw-r--r-- aaron/aaron       0 2009-04-23 20:37 ./chaat/test.nfo
-rw-r--r-- aaron/aaron       0 2009-04-23 20:35 ./chaat/chutney/brazton.m3u
-rw-r--r-- aaron/aaron       0 2009-04-23 20:23 ./chaat/mastaz.m3u
-rw-r--r-- aaron/aaron       0 2009-04-23 20:34 ./chaat/killz.m3u
-rw-r--r-- aaron/aaron       0 2009-04-23 22:27 ./meta.txt
-rw-r--r-- aaron/aaron       0 2009-04-23 22:27 ./bombackaz.nfo

```

Although this is working and everything now, is there anyway I can have this message not show up? "gzip: testing.tar.gz: No such file or directory"

Thanks!

---

### Post by StunnerAlpha on 2009-04-25
> **StunnerAlpha said:**
> Nevermind I think I got it I had to change my code to this:
```

tarArchive(){
if [ "$insurance" == "1" ]; then
	if [ -e "$backupname" ]; then
		tar -cf "$backupname".tar "$filename"
		gzip -9 "$backupname".tar
	else
		gunzip "$backupname".tar.gz
		tar -rf "$backupname".tar "$filename"
		gzip -9 "$backupname".tar
	fi
fi
}

```

Here is the output of my program now:
```

----------------MENU-----------------
2.Delete .nfo .sfv .txt .m3u files
1.Search and remove empty folders
0.Exit script
-------------------------------------
Select option: 2
Do you want this script to make a backup of everything you delete within this function for insurance reasons?(Y/N)y
Enter the name of the backup: testing
Do you wish to remove ./megaZORD.sfv?(Y/N/C for cancel)y
gzip: testing.tar.gz: No such file or directory
rm ./megaZORD.sfv
Do you wish to remove ./chaat/test.nfo?(Y/N/C for cancel)y
rm ./chaat/test.nfo
Do you wish to remove ./chaat/chutney/brazton.m3u?(Y/N/C for cancel)y
rm ./chaat/chutney/brazton.m3u
Do you wish to remove ./chaat/mastaz.m3u?(Y/N/C for cancel)y
rm ./chaat/mastaz.m3u
Do you wish to remove ./chaat/killz.m3u?(Y/N/C for cancel)y
rm ./chaat/killz.m3u
Do you wish to remove ./meta.txt?(Y/N/C for cancel)y
rm ./meta.txt
Do you wish to remove ./bombackaz.nfo?(Y/N/C for cancel)y
rm ./bombackaz.nfo
DONE(hit enter)

```
And what is contained in the "tarball" as you guys call it: :)
```

t$ tar tvf testing.tar.gz 
-rw-r--r-- aaron/aaron       0 2009-04-23 22:27 ./megaZORD.sfv
-rw-r--r-- aaron/aaron       0 2009-04-23 20:37 ./chaat/test.nfo
-rw-r--r-- aaron/aaron       0 2009-04-23 20:35 ./chaat/chutney/brazton.m3u
-rw-r--r-- aaron/aaron       0 2009-04-23 20:23 ./chaat/mastaz.m3u
-rw-r--r-- aaron/aaron       0 2009-04-23 20:34 ./chaat/killz.m3u
-rw-r--r-- aaron/aaron       0 2009-04-23 22:27 ./meta.txt
-rw-r--r-- aaron/aaron       0 2009-04-23 22:27 ./bombackaz.nfo

```

Although this is working and everything now, is there anyway I can have this message not show up? "gzip: testing.tar.gz: No such file or directory"

Thanks!
I even did this with no error output from gzip:
```

$ tar -cf test.tar megaZORD.sfv 
$ gzip -9 test.tar 
$ gunzip test.tar.gz 
$ tar -rf test.tar bombackaz.nfo 
$ ls
[1-5]          cleaner.sh  makill.mp3    r           rule3py.sh  test.tar
bombackaz.nfo  emptry      megaZORD.sfv  rule3-2.sh  rule3.sh    touchy
chaat          empty1      meta.txt      rule3py.py  test.sh
$ gzip -9 test.tar 
$ ls
[1-5]          cleaner.sh  makill.mp3    r           rule3py.sh  test.tar.gz
bombackaz.nfo  emptry      megaZORD.sfv  rule3-2.sh  rule3.sh    touchy
chaat          empty1      meta.txt      rule3py.py  test.sh
$ tar tvf test.tar.gz 
-rw-r--r-- aaron/aaron       0 2009-04-23 22:27 megaZORD.sfv
-rw-r--r-- aaron/aaron       0 2009-04-23 22:27 bombackaz.nfo

```
So this is really confusing me... I followed my code exactly as I wrote it while emulating it manually...

---

### Post by Arndt on 2009-04-25
> **StunnerAlpha said:**
> 
[...]

Although this is working and everything now, is there anyway I can have this message not show up? "gzip: testing.tar.gz: No such file or directory"

Thanks!

I haven't looked into it, but you can follow the execution of your script by using the -x or -v flags to sh. Then you will see which command it is that gives this message.

The program 'tar' is older than the word "tarball", but if someone wants to say "tarball", I let them.

---

### Post by StunnerAlpha on 2009-04-25
> **Arndt said:**
> I haven't looked into it, but you can follow the execution of your script by using the -x or -v flags to sh. Then you will see which command it is that gives this message.

The program 'tar' is older than the word "tarball", but if someone wants to say "tarball", I let them.
Ah, thanks for the tip man, that definitely helped me figure out to problem. Turns out the conditions in the tarArchive() function should have been reversed, that is, everything in the if statement be swapped with everything in the else statement.

---

### Post by dwhitney67 on 2009-04-25
> **Arndt said:**
> ...
The program 'tar' is older than the word "tarball", but if someone wants to say "tarball", I let them.
The program is called 'tar'; some people, including myself, like to refer to a tarred (sp?) package of files as a "tarball".

I've been using tar for over 20 years; and the "tarball" name has been floating around just as long if not longer.

---

### Post by StunnerAlpha on 2009-04-25
I have this code:
```

tarArchive(){
if [ "$insurance" == "1" ]; then
	if [ -e "$backupname".tar.gz ]; then
		gunzip "$backupname".tar.gz
		tar -rf "$backupname".tar "$filename"
		gzip -9 "$backupname".tar
	else
		tar -cf "$backupname".tar "$filename"
		gzip -9 "$backupname".tar
	fi
fi
}

```
With the names of the variables quoted and everything, yet when I try to refer to a file with a space in it, it doesn't let me... This is the error I am recieving:
```

----------------MENU-----------------
2.Delete .nfo .sfv .txt .m3u files
1.Search and remove empty folders
0.Exit script
-------------------------------------
Select option: 2
Do you want this script to make a backup of everything you delete within this function for insurance reasons?(Y/N)y
Enter the name of the backup: go
Do you wish to remove ./artist/a/afi/play.m3u?(Y/N/C for cancel)y
rm ./artist/a/afi/play.m3u
Do you wish to remove ./artist/a/alkaline?(Y/N/C for cancel)y
tar: ./artist/a/alkaline: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
rm ./artist/a/alkaline
Do you wish to remove trio/playlist.m3u?(Y/N/C for cancel)c
DONE(hit enter)

```

Thanks in advance for any help!

---

### Post by dwhitney67 on 2009-04-25
Can you please post your entire script?  It's Saturday, and I do not have the desire to build up the entire framework around your tarArchive() function.

P.S.  Here's a small script that successfully creates a tarball with filenames containing spaces:
```

#!/bin/bash

# create dummy files, which contain white-space in name
filename="foo bar"
filename2="dark matter"

touch "$filename"
touch "$filename2"

# create tarball with dummy file
tar cf "$filename".tar "$filename"

# zip tarball
gzip -9 "$filename".tar

# unzip tarball
gunzip "$filename".tar.gz

# add second dummy file to tarball
tar rf "$filename".tar "$filename2"

# (re)zip tarball
gzip -9 "$filename".tar

# verify results
tar tf "$filename".tar.gz | grep -q "$filename"
if [ $? -ne 0 ]
then
        echo "$filename" not found
fi

tar tf "$filename".tar.gz | grep -q "$filename2"
if [ $? -ne 0 ]
then
        echo "$filename2" not found
fi

```

---

### Post by Arndt on 2009-04-25
> **dwhitney67 said:**
> The program is called 'tar'; some people, including myself, like to refer to a tarred (sp?) package of files as a "tarball".

I've been using tar for over 20 years; and the "tarball" name has been floating around just as long if not longer.

I think it got really popular with the spread of Linux. I don't doubt you; but perhaps it was used more informally before, not for example in News groups or installation instructions.

---

### Post by Arndt on 2009-04-25
> **StunnerAlpha said:**
> 

With the names of the variables quoted and everything, yet when I try to refer to a file with a space in it, it doesn't let me



I'm not going to write anything very helpful, just remark on the trouble people get into when file names have spaces in them (I'm a victim myself - in my project, people write documents in Word and let their names be whole sentences). There ought to be a good guide somewhere on how to deal with the problem, but the information seems spread out, when I google a bit.

One thing to do is to put quotes around variables: "$x", not $x. Another is to use -print0 and -0 with the find/xargs pair. There must be more.

---

### Post by StunnerAlpha on 2009-04-25
> **dwhitney67 said:**
> Can you please post your entire script?  It's Saturday, and I do not have the desire to build up the entire framework around your tarArchive() function.

P.S.  Here's a small script that successfully creates a tarball with filenames containing spaces:
```

#!/bin/bash

# create dummy files, which contain white-space in name
filename="foo bar"
filename2="dark matter"

touch "$filename"
touch "$filename2"

# create tarball with dummy file
tar cf "$filename".tar "$filename"

# zip tarball
gzip -9 "$filename".tar

# unzip tarball
gunzip "$filename".tar.gz

# add second dummy file to tarball
tar rf "$filename".tar "$filename2"

# (re)zip tarball
gzip -9 "$filename".tar

# verify results
tar tf "$filename".tar.gz | grep -q "$filename"
if [ $? -ne 0 ]
then
        echo "$filename" not found
fi

tar tf "$filename".tar.gz | grep -q "$filename2"
if [ $? -ne 0 ]
then
        echo "$filename2" not found
fi

```
Aright well here is my entire script:
```

#!/bin/bash

#tar tvf asdfsaf.tar.gz

insurance=0

tarArchive(){
if [ "$insurance" == "1" ]; then
	if [ -e "$backupname".tar.gz ]; then
		gunzip "$backupname".tar.gz
		tar -rf "$backupname".tar "$filename"
		gzip -9 "$backupname".tar
	else
		tar -cf "$backupname".tar "$filename"
		gzip -9 "$backupname".tar
	fi
fi
}

delEmptyDirs(){
read -p "Do you want this script to make a backup of everything you delete within this function for insurance reasons?(Y/N)" yn
if [ "$yn" == "Y" -o "$yn" == "y" ]; then
	insurance=1
	read -p "Enter the name of the backup: " backupname
fi
for a in `find ./ -type d -empty`
	do
#		if [ yn == "C" ]; then
#			break
#		fi
		read -p "Do you wish to remove \"$a\"?(Y/N/C for cancel)" yn
		case $yn in
			[Yy]* ) tarArchive
					echo rm "$a";;
			[Nn]* ) echo "$a not removed";;
			[Cc]* ) break;;
			* ) until [ "$yn" == "Y" -o "$yn" == "N" -o "$yn" == "y" -o "$yn" == "n" -o "$yn" == "C" -o "$yn" == "c" ]; do
					read -p "Enter \"Y\", \"N\", or \"C\"" yn
					if [ "$yn" == "Y" -o "$yn" == "y" ]; then
						 tarArchive
						 echo rm "$a"
					fi
					if [ "$yn" == "N" -o "$yn" == "n" ]; then
						echo "$a not removed"
					fi
					if [ "$yn" == "C" -o "$yn" == "c" ]; then
#						yn=C
						break
					fi
				done;;
		esac
	insurance=0
	done;
}

del_nfo_sfv_txt_m3u_files(){
	read -p "Do you want this script to make a backup of everything you delete within this function for insurance reasons?(Y/N)" yn
	if [ "$yn" == "Y" -o "$yn" == "y" ]; then
		insurance=1
		read -p "Enter the name of the backup: " "backupname"
	fi
	for filename in `find ./ -regex ".*\(m3u\|sfv\|txt\|nfo\)$"`
	do
		read -p "Do you wish to remove $filename?(Y/N/C for cancel)" yn
			case $yn in
				[Yy]* ) tarArchive
						echo rm \"$filename\";;
				[Nn]* ) echo ""$filename" not removed";;
				[Cc]* ) break;;
				* ) until [ "$yn" == "Y" -o "$yn" == "N" -o "$yn" == "y" -o "$yn" == "n" -o "$yn" == "C" -o "$yn" == "c" ]; do
					read -p "Enter \"Y\", \"N\", or \"C\"" yn
					if [ "$yn" == "Y" -o "$yn" == "y" ]; then
						tarArchive
						echo rm "$filename"
					fi
					if [ "$yn" == "N" -o "$yn" == "n" ]; then
						echo "$filename not removed"
					fi
					if [ "$yn" == "C" -o "$yn" == "c" ]; then
						break
					fi
				done;;
			esac

	done;
}

displayMenu(){
	echo "----------------MENU-----------------"
	echo "2.Delete .nfo .sfv .txt .m3u files"
	echo "1.Search and remove empty folders"
	echo "0.Exit script"
	echo "-------------------------------------"
	read -p "Select option: " option
}

until [ "$option" == "0" ]; do
clear
displayMenu
case $option in
	2 ) del_nfo_sfv_txt_m3u_files; read -p "DONE(hit enter)" noUse;;
	1 ) delEmptyDirs; read -p "DONE(hit enter)" noUse;;
	0 ) exit;;
	* ) until [ "$option" == "0" -o "$option" == "1" -o "$option" == "2" ]; do
		read -p "Enter a number (0-1)" option
		if [ "$option" == "2" ]; then
			del_nfo_sfv_txt_m3u_files
			read -p "DONE(hit enter)" noUse
		fi
		if [ "$option" == "1" ]; then
			delEmptyDirs
			read -p "DONE(hit enter)" noUse
		fi
		if [ "$option" == "0" ]; then
			exit
		fi
	done;;
esac
done

exit

```

I have all filenames quoted and such and it refuses to work. This is how to see the problem I am getting:
```

$ bash cleaner.sh 
----------------MENU-----------------
2.Delete .nfo .sfv .txt .m3u files
1.Search and remove empty folders
0.Exit script
-------------------------------------
Select option: 2
Do you want this script to make a backup of everything you delete within this function for insurance reasons?(Y/N)y
Enter the name of the backup: test
Do you wish to remove ./artist/a/afi/play.m3u?(Y/N/C for cancel)y
rm "./artist/a/afi/play.m3u"
Do you wish to remove ./artist/a/alkaline?(Y/N/C for cancel)y
tar: ./artist/a/alkaline: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
rm "./artist/a/alkaline"
Do you wish to remove trio/playlist.m3u?(Y/N/C for cancel)y
tar: trio/playlist.m3u: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
rm "trio/playlist.m3u"
DONE(hit enter)

```

And this is my directory listing:
```

$ ls -Rl
.:
total 24
drwxr-xr-x 4 aaron aaron  4096 2009-04-22 19:41 artist
-rw-r--r-- 1 aaron aaron  3092 2009-04-25 16:26 cleaner.sh
-rw-r--r-- 1 aaron aaron     0 2009-04-25 16:30 dark matter
-rw-r--r-- 1 aaron aaron   219 2009-04-25 16:29 dummytest.sh
-rw-r--r-- 1 aaron aaron 10240 2009-04-25 16:30 foo bar

./artist:
total 8
drwxr-xr-x 4 aaron aaron 4096 2009-04-25 04:45 a
drwxr-xr-x 4 aaron aaron 4096 2009-04-25 04:45 b

./artist/a:
total 8
drwxr-xr-x 2 aaron aaron 4096 2009-04-25 04:45 afi
drwxr-xr-x 2 aaron aaron 4096 2009-04-25 04:45 alkaline trio

./artist/a/afi:
total 0
-rw-r--r-- 1 aaron aaron 0 2009-04-22 19:42 play.m3u
-rw-r--r-- 1 aaron aaron 0 2009-04-22 19:41 test.mp3
-rw-r--r-- 1 aaron aaron 0 2009-04-22 19:41 twe.mp3

./artist/a/alkaline trio:
total 0
-rw-r--r-- 1 aaron aaron 0 2009-04-22 19:41 playlist.m3u

./artist/b:
total 8
drwxr-xr-x 2 aaron aaron 4096 2009-04-25 04:45 bandits of the acoustic revolution
drwxr-xr-x 2 aaron aaron 4096 2009-04-22 19:46 empty folder

./artist/b/bandits of the acoustic revolution:
total 0
-rw-r--r-- 1 aaron aaron 0 2009-04-22 19:42 folder.jpg

./artist/b/empty folder:
total 0

```

Thanks!

---

### Post by dwhitney67 on 2009-04-25
Look at the contents of your tarball; sure enough, "trio/playlist.m3u" is not there.

Sure there is something *similar*, but it is prefaced with a larger path, that of course being "./artist/a/alkaline trio".

I'm not a bash scripting expert, but the problem with your script lies here:
```

...
for a in `find ./ -type d -empty`
...

```
where the value of 'a' is not what you expect.  Using an echo statement will reveal that to you.

---

### Post by StunnerAlpha on 2009-04-26
> **dwhitney67 said:**
> Look at the contents of your tarball; sure enough, "trio/playlist.m3u" is not there.

Sure there is something *similar*, but it is prefaced with a larger path, that of course being "./artist/a/alkaline trio".

I'm not a bash scripting expert, but the problem with your script lies here:
```

...
for a in `find ./ -type d -empty`
...

```
where the value of 'a' is not what you expect.  Using an echo statement will reveal that to you.
Ah, I see what you are saying and you are right. How would I go about getting "a" or "filename" in the for loops to take spaces? I have tried quoting the variable in the for loop like so:
```

for "filename" in `find ./ -regex ".*\(m3u\|sfv\|txt\|nfo\)$"`

```
but this happens:
```

----------------MENU-----------------
2.Delete .nfo .sfv .txt .m3u files
1.Search and remove empty folders
0.Exit script
-------------------------------------
Select option: 2
Do you want this script to make a backup of everything you delete within this function for insurance reasons?(Y/N)y
Enter the name of the backup: yetrt
cleaner.sh: line 56: `"filename"': not a valid identifier
DONE(hit enter)

```
Anyone know how to go about doing this? Thanks.

---

### Post by dwhitney67 on 2009-04-26
See if this will work for you:
```

find . -type d -empty | while read emptydir
do
        echo $emptydir

        ...
done

```
I used 'emptydir' in lieu of 'a'; single variable args are in many cases useless since they do not convey any worthwhile information to the one reading the code.

---

### Post by StunnerAlpha on 2009-04-26
> **dwhitney67 said:**
> See if this will work for you:
```

find . -type d -empty | while read emptydir
do
        echo $emptydir

        ...
done

```
I used 'emptydir' in lieu of 'a'; single variable args are in many cases useless since they do not convey any worthwhile information to the one reading the code.
Thanks, yeah I agree the name should be changed for sure. I put that code into my delete empty folder function but it hangs when I run it... I think it goes into an infinite loop, but I can't figure out why or where:
```

----------------MENU-----------------
2.Delete .nfo .sfv .txt .m3u files
1.Search and remove empty folders
0.Exit script
-------------------------------------
Select option: 1
Do you want this script to make a backup of everything you delete within this function for insurance reasons?(Y/N)n
./artist/b/empty folder


y
y
n
n
DONE(hit enter)

```

Thanks!

---

### Post by dwhitney67 on 2009-04-26
Please post the modified delEmptyDirs() function.  If you have an infinite loop, it is probably there.

---

### Post by StunnerAlpha on 2009-04-26
> **dwhitney67 said:**
> Please post the modified delEmptyDirs() function.  If you have an infinite loop, it is probably there.
Yeah sorry I normally post the code that I have, I just thought that when your wrote your code when you tested it and were getting the same result. Anywhere here is the code:
```

delEmptyDirs(){
read -p "Do you want this script to make a backup of everything you delete within this function for insurance reasons?(Y/N)" yn
if [ "$yn" == "Y" -o "$yn" == "y" ]; then
	insurance=1
	read -p "Enter the name of the backup: " backupname
fi
find . -type d -empty | while read emptydir
do
        echo $emptydir

#		if [ yn == "C" ]; then
#			break
#		fi
		read -p "Do you wish to remove \"$emptydir\"?(Y/N/C for cancel)" yn
		case $yn in
			[Yy]* ) tarArchive
					echo rm "$emptydir";;
			[Nn]* ) echo "$emptydir not removed";;
			[Cc]* ) break;;
			* ) until [ "$yn" == "Y" -o "$yn" == "N" -o "$yn" == "y" -o "$yn" == "n" -o "$yn" == "C" -o "$yn" == "c" ]; do
					read -p "Enter \"Y\", \"N\", or \"C\"" yn
					if [ "$yn" == "Y" -o "$yn" == "y" ]; then
						 tarArchive
						 echo rm "$a"
					fi
					if [ "$yn" == "N" -o "$yn" == "n" ]; then
						echo "$a not removed"
					fi
					if [ "$yn" == "C" -o "$yn" == "c" ]; then
#						yn=C
						break
					fi
				done;;
		esac
	insurance=0
	done;
}

```
I am not very good with the syntax, so I do not know if the while loop needs to specify an end to it or not. Thank you very much, I know I say this a lot but I REALLY do appreciate all the help.

---

### Post by dwhitney67 on 2009-04-26
Let's start by simplifying your loop.  How this:
```

...

while [ true ]
do
        read -p "Remove \"$emptydir\"? [Y/N/C for cancel]  " yn

        case $yn in
                [Yy]*) TarArchive; echo "deleting $emptydir."; break;;

                [Nn]*) echo "$emptydir not removed."; break;;

                [Cc]*) echo "operation cancelled."; break;;

                *)     echo "invalid choice pinhead; try again...";;
        esac
done

...

```

---

### Post by StunnerAlpha on 2009-04-27
> **dwhitney67 said:**
> Let's start by simplifying your loop.  How this:
```

...

while [ true ]
do
        read -p "Remove \"$emptydir\"? [Y/N/C for cancel]  " yn

        case $yn in
                [Yy]*) TarArchive; echo "deleting $emptydir."; break;;

                [Nn]*) echo "$emptydir not removed."; break;;

                [Cc]*) echo "operation cancelled."; break;;

                *)     echo "invalid choice pinhead; try again...";;
        esac
done

...

```
Where is emptydir initialized though? Looking more at my code and messing around with it, it appears to me that I need to store everything in an array first, then read out from the array one by one... Any simpler ways?

---

### Post by dwhitney67 on 2009-04-27
Sorry about the bug; I was not using your complete code as a template for development; I was merely attempting to test/present a while-loop.

After integrating the while loop, with its embedded read statement within the find-while-loop, then I came across the bug.

EDIT:  The code I posted still does not work with directories containing spaces within the name.

---

### Post by StunnerAlpha on 2009-04-27
> **dwhitney67 said:**
> Sorry about the bug; I was not using your complete code as a template for development; I was merely attempting to test/present a while-loop.

After integrating the while loop, with its embedded read statement within the find-while-loop, then I came across the bug.

EDIT:  The code I posted still does not work with directories containing spaces within the name.
No worries man, thanks for the attempt. There has to be a way to do this, correct? Would my idea of reading into an array be a potentially viable solution? Any other bash pros out there willing to lend a hand? As always, thanks in advance!

---

### Post by dwhitney67 on 2009-04-27
> **StunnerAlpha said:**
> No worries man, thanks for the attempt. There has to be a way to do this, correct? Would my idea of reading into an array be a potentially viable solution? Any other bash pros out there willing to lend a hand? As always, thanks in advance!

I just tried that, and I was unsuccessful because I was unable to discern how many items had been inserted into the array.

Using something like:
```

declare index=0

find . -type d -empty | while read dir
do
        emptydirs[index]="$dir"
        index=$index+1
done

# everything works fine... but wait... emptydirs and index are not applicable at this point... they were only set within the subshell, thus not usable here!

```

---

### Post by ghostdog74 on 2009-04-27
instead of coding the "find empty directory and asking for removal" loop, you can use -exec rm -irf {} \;

---

