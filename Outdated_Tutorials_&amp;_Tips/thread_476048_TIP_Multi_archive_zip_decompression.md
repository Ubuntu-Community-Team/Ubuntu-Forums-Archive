---
title: "TIP: Multi archive zip decompression"
date: 2007-06-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Jose Catre-Vandis on 2007-06-16
Multi part archive decompression in file-roller/archive manager doesn't seem to be supported, so....


When you have .z01, .z02, ... and a final .zip files to unzip, 

you have to do
```
cat foo.z01 foo.z02 foo.zip > new_foo.zip
```
which makes a new zip file of all the parts (new_foo.zip)


and then 
```
unzip -F new_foo.zip
```
which should then unzip the lot for you


HTH someone somewhere

---

### Post by beefcurry on 2008-04-23
Thanks this helped, but it was quite annoying manually typing in all the different .z0# .

---

### Post by designeru on 2008-05-23
you can always do something like:

# cat *.z* > something.zip

---

### Post by jastonas on 2008-11-11
is there no ubuntu application to handle these files??

---

### Post by Green_Star on 2008-11-11
> **jastonas said:**
> is there no ubuntu application to handle these files??

I am not sure what compression programs I have installed in my Ubuntu 804, **my file-roller support extracting a "multi part archive"**. I think I have installed rar/unrar and 7zip etc.

I haven't figure out how to create a multi-part-archive using file-roller.

---

### Post by Jose Catre-Vandis on 2008-11-12
> **jastonas said:**
> is there no ubuntu application to handle these files??

Well this is what the "cat" "application" does!

@ Green_Star

I am fairly certain You can use a rar command at the command line to create multi part archives, check out the man in a terminal for the syntax
```
man rar
```

---

### Post by Green_Star on 2008-11-12
> **Jose Catre-Vandis said:**
> Well this is what the "cat" "application" does!

@ Green_Star

I am fairly certain You can use a rar command at the command line to create multi part archives, check out the man in a terminal for the syntax
```
man rar
```


Thanks man, I know rar can do it from command line, I haven't figure out to do it with file-roller. GUI is always good.. right?

---

### Post by Jose Catre-Vandis on 2008-11-12
It should be easy with file-roller too...

Open file-roller (I have to do it from a terminal on my system!)
```
file-roller
```
Go Archive > New (or click on the white square icon)
type a name and choose .rar from the Archive type drop down
then click on the Other Options arrow/word
Tick the box for "split in volumes of"
and choose your size of rars
Click create and then add files or folders
and there you have your multi file archive :)

(You might need to put your files inside folders in order to create a multi file archive, when I tried just adding files, file-roller didn't split it into parts??)

and your point about using GUI to do this, its horses for courses, I guess once you have your command line syntax set up, it's quick to edit or you can write a script with variables. I don't multi file archive much so doesn't bother me either way.

---

### Post by bth73 on 2009-02-17
What a stupid way of doing zip files. KISS 
WHY is it done? Lots of things can be done, but should they?
Never seen it untill yesterday.

---

### Post by jastonas on 2009-02-17
what are you referring to with WHY?

---

### Post by cthlhu1987 on 2010-11-30
> **jastonas said:**
> what are you referring to with WHY?
Why to use zip and cut this file in pieces when rar and 7z have native multipart archive support!

---

