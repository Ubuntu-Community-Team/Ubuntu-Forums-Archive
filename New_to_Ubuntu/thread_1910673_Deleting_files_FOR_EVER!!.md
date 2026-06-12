---
title: "Deleting files FOR EVER!!"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by benj23673 on 2012-01-17
Ok, so I am new to lubuntu my question I have is, when I delete a file what happens to it? 
I know on windows if you delete it to the trash and can still be recovered so you have to use a program like cccleaner to delete it for ever or overwrite it. 
Is it the same way using ubuntu and lubuntu?

---

### Post by Double.J on 2012-01-17
Hi there if you delete to trash then it can just be recovered.. even if you clear trash it can still be recovered with a program like photorec until it is overwritten by the system

The unix tool to securely remove is shred - usage example
```

sudo shred exwifescontactlist.txt

```
:)

---

### Post by trikster_x on 2012-01-17
Have a look at the man page for shred too. Some of the options might be just what you want. Specifically the -z option which overwrites the file with zeros after you are done deleting it.

---

### Post by amjjawad on 2012-01-17
> **benj23673 said:**
> Ok, so I am new to lubuntu my question I have is, when I delete a file what happens to it? 
I know on windows if you delete it to the trash and can still be recovered so you have to use a program like cccleaner to delete it for ever or overwrite it. 
Is it the same way using ubuntu and lubuntu?

Hello and Welcome to Ubuntu Forum and thanks for choosing and using Lubuntu :)

Are you trying to get rid of some files permanently or asking whether you can recover the deleted files? what exactly are you looking for? :)

---

### Post by ubuntu27 on 2012-01-17
I never used *shred*, I like to use *Secure Delete*

```
sudo apt-get install secure-delete
```

Open the terminal, go to the desired directory and

```
srm name-of-file
```
to delete files.


Use
```
man srm
```
to read the manual

---

### Post by NerdWermz on 2012-01-17
> **ubuntu27 said:**
> I never used *shred*, I like to use *Secure Delete*



My vote is for Secure Delete as well.  It works very well and even has options to shred free disk space, and some others.  I believe the option is "sfill," for the free space.


In addition to the op's question, even if you use "rm" or "rmdir" from the command line, the information is still on the disk, You have simply removed the pointer.

hope that helps.

---

### Post by Paqman on 2012-01-17
Most secure deletion packages have pretty stupid defaults, and will pointlessly do multiple writes over your data. That's a waste of time, a single pass with random data is completely effective. So that would be something like:
```
srm -s file

OR

shred -n1 -u file

```

If you've got an SSD with TRIM enabled you don't even need to do anything, the drive will automatically write over the data after you do a normal delete.

---

### Post by ivelnal on 2012-01-17
> **ubuntu27 said:**
> I never used *shred*, I like to use *Secure Delete*

```
sudo apt-get install secure-delete
```

Open the terminal, go to the desired directory and

```
srm name-of-file
```
to delete files.


Use
```
man srm
```
to read the manual

I never use this one. it is worth a try.

---

### Post by NerdWermz on 2012-01-17
> **Paqman said:**
> Most secure deletion packages have pretty stupid defaults, and will pointlessly do multiple writes over your data. That's a waste of time, a single pass with random data is completely effective. So that would be something like:
```
srm -s file

OR

shred -n1 -u file

```If you've got an SSD with TRIM enabled you don't even need to do anything, the drive will automatically write over the data after you do a normal delete.

I have experimented with shredding files and trying to recover them.  With one pass I was still able to recover part if not all of some files using hard drive scanners.  There can still be residual data left over.   For personal use I would say that is fine as it will eventually be over written. But if I were to be decommissioning the drive and giving it away I would at least run a DoD 5220.22-M(ECE) 7 pass on the drive.  Or a Gutmann 35-pass algorithm, which I know some say is over kill with todays high density drives.

anyway, just my .02

---

### Post by garyed on 2012-01-17
one thing to remember about shred is that without the "-u" switch it deletes the content but it doesn't delete the filename so it will still show up in the directory.
I always use:
```
shred -uz filename
```

---

### Post by Paqman on 2012-01-18
> **NerdWermz said:**
> I have experimented with shredding files and trying to recover them.  With one pass I was still able to recover part if not all of some files using hard drive scanners.  There can still be residual data left over.   For personal use I would say that is fine as it will eventually be over written. But if I were to be decommissioning the drive and giving it away I would at least run a DoD 5220.22-M(ECE) 7 pass on the drive.  Or a Gutmann 35-pass algorithm, which I know some say is over kill with todays high density drives.

anyway, just my .02

There's never any need to do a 35-pass overwrite, even Gutmann himself said so:

> 
In fact performing the full 35-pass overwrite is pointless for any drive since it targets a blend of scenarios involving all types of (normally-used) encoding technology, which covers everything back to 30+-year-old MFM methods (if you don't understand that statement, re-read the paper). If you're using a drive which uses encoding technology X, you only need to perform the passes specific to X, and you never need to perform all 35 passes. For any modern PRML/EPRML drive, a few passes of random scrubbing is the best you can do. As the paper says, **"A good scrubbing with random data will do about as well as can be expected"**. This was true in 1996, and is still true now.

---

### Post by ubuntu27 on 2012-02-19
> **Paqman said:**
> Most secure deletion packages have pretty stupid defaults, and will pointlessly do multiple writes over your data. That's a waste of time, a single pass with random data is completely effective. So that would be something like:
```
srm -s file

OR

shred -n1 -u file

```

If you've got an SSD with TRIM enabled you don't even need to do anything, the drive will automatically write over the data after you do a normal delete.

To do **two passes** with random data with Secure Remove is

```
srm -l name-of-file
```

And random data with **one pass** is:

```
srm -l -l name-of-file
```

:)

---

### Post by dreamquartz on 2012-03-03
What about Bleachbit?
It is in the repos.

Dream

---

### Post by 3rdalbum on 2012-03-03
From what I've heard, using Shred to remove one file is ineffective because Shred just tells the filesystem to write new data to the file that replaces the old data; however, filesystems today may in fact write this new data to a different place, leaving the old data still in the clear.

Using Shred to overwrite all free space on your hard disk would be more effective. But you don't need Shred for that - dd will work too.

A better idea would be to encrypt your home directory and that way nothing, deleted or non-deleted, is accessible without your password.

---

### Post by surfer on 2012-03-03
+1 for encryption.

ubuntu offers ecrypfs during the install process (it is the default, if i remember correctly).

should you want all the contents of your disk encypted (except for the master boot record and a small /boot partition), the ubuntu alternate install cd offers everything you need for that.

---

