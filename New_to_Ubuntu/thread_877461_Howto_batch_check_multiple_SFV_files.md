---
title: "Howto batch check multiple SFV files?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Bd0g on 2008-08-01
I got this command to easily extract multiple collections of rar files:
```
find /home/user/packed-files/ -type f -name '*.rar' -execdir unrar x {} \;
```

or test them with unrar:
```
find /home/user/packed-files/ -type f -name '*.rar' -execdir unrar t {} \;
```

I was wondering if I could tune this to also do a sweep test on the SFV files that's located in the same folders.

Any tips?

---

### Post by unutbu on 2008-08-01
I have never used cfv or cksfv, but judging  from the man pages ([url]http://linux.die.net/man/1/cksfv
[/url] 
[http://linux.die.net/man/1/cfv](http://linux.die.net/man/1/cfv)), maybe try:

```
find /home/user/packed-files/ -type f -name '*.rar' -execdir cfv -r {} \;

```
or

```
find /home/user/packed-files/ -type f -name '*.rar' -execdir cksfv -r {} \;
```

---

### Post by Bd0g on 2008-08-01
```
find /home/user/packed-files/ -type f -name '*.rar' -execdir cfv -r {} \;

```

Yeah, actaully tried that before and all it gave me was a listing of the SFV files it found and telling me it cant locate any of the files that they are pointing at.

---

### Post by unutbu on 2008-08-01
Use a text editor to look inside one of the .sfv files. According to [http://en.wikipedia.org/wiki/Simple_file_verification](http://en.wikipedia.org/wiki/Simple_file_verification), it should look something like this:
```

file_one.zip   c45ad668
file_two.zip   7903b8e6
file_three.zip e99a65fb
```

Do the files listed there actually exist (and are in the same directory as the .sfv)?

---

### Post by Bd0g on 2008-08-02
Yupp, the linked files are there in the same directory as the SFV file and work with other apps like quicksfv etc..

---

### Post by unutbu on 2008-08-02
What is the output if you run
```

cfv SOMEFILE.sfv
```
(Does it check the sfv?)

---

### Post by Bd0g on 2008-08-02
You know what, I just solved it :D

```
find /home/user/packed-files/ -type f -name '*.rar' -execdir cfv -f {} \;
```

Not really sure why this **-f** (force the file to test) works instead of the original solution ... but it does.

I do get a few funny errors when he begins to scan the files like:

```
rarfiles.r00 : #################/var/lib/python-support/python2.5/cfv.py:763: DeprecationWarning: struct integer overflow masking is deprecated
  return struct.pack('>I',self.value)

```

Just curious if I can supress them or do anything else to make it go away :D

---

### Post by unutbu on 2008-08-02
Try this:
```
find /home/user/packed-files/ -type f -name '*.rar' -execdir cfv -f {} 2>/dev/null \;
```

---

### Post by Bd0g on 2008-08-02
Nice :)

Thank you so very much for sticking by and helping out, you have my sincere gratitude ;)

---

### Post by Fifoxtasy on 2010-03-23
just wanted to add, that -f doesn't mean *force*. ```
cfv -f <f>
``` means use <f> as list file. see ```
cfv --help
```

---

