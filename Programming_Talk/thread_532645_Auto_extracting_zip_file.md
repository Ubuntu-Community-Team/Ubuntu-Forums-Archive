---
title: "Auto extracting zip file?"
date: 2007-08-23
forum: Programming Talk
---

### Post by hammer v2 on 2007-08-23
Hey guys
I'm looking for an archive format that extracts itself and runs a bash script from within it.... is there such an animal in linux?

thanks guys.
H.

---

### Post by jordanmthomas on 2007-08-23
I don't know how exactly to go about it, but I believe a .bin file typically does just that.

(I've had to extract the scripts out of them before, so I know they can have bash scripts in them.)

---

### Post by HermanAB on 2007-08-23
Yes, those things are called .deb or .rpm.
:)

---

### Post by jordanmthomas on 2007-08-23
\me slaps self in face
lol

Of course, you can't use .debs and .rpms everywhere, just certain systems.

---

### Post by -Rick- on 2007-08-23
You can use makeself for that: [http://peter.cx/stephane/makeself/](http://peter.cx/stephane/makeself/)

---

### Post by Tuna-Fish on 2007-08-23
If you want do it yourself, the trick is writing the script and appending the archive to the end of the script, using cat.  The script must then be able to split off the file in the end, and uncompress it. like this:

the file:
```

echo 'short story' > file
gzip -c file > zipped

ls -l zipped
-rw-r--r-- 1 tuna tuna 37 2007-08-23 12:37 zipped
#note the size!

```
the script:
```

#! /bin/bash
#########

tail --bytes=37 $0 | gzip -c -d
#^cut off last 37 bytes, the size of our file, and feed it to gzip, print output to stdout.

exit 0
#^important! otherwise execution will continue into the binary file.


```

the gory finale:
```

cat script zipped > script.bin
chmod a+x script.bin
./script.bin
short story

```

You can of course  instead extract everything you need into a temp file, or temp dir, and then just continue doing whatever it is you want to do after that. Just don't forget the exit 0 from the end...

---

### Post by Tuna-Fish on 2007-08-23
addendum1: it's also possible to do a safer version of that script by placing a marker at the end of the script, and building a loop in the scrip that reads from the script a line at a time until it hits the marker, then turns into byte at a time mode and spits the rest to the uncompresser.

addendum2: note that there has to be at least a newline character after exit 0, ptherwise the binary file continues on the same line and corrups everything.

addendum3: it's also possible to do this all without gzip, and still place multiple files in there trough a clever use of lots of head and tail commands. That is, if you are masochistic enough. I have actually seen one with five embedded files... (pun about heads and tails suppressed)

---

### Post by hammer v2 on 2007-08-24
WOW!! Thanks everyone for your help. I will try using makeself and see how I go. sounds like just the thing!.

Hey Tuna Fish, you clearly are a scripting GURU!!! Um, can you help with this one quickly?
I need apt-cdrom to run without asking me to insert a CD then press enter. I just want it to assume the CD is already there. It's for the people in Laos who can't read english and will run away screaming if they see command line. :) Any ideaS on how I can get the CD mounted in the sources.list - no questions asked?

(Take a look at this if you've got time and you'll understand my strange request....[http://ubuntuforums.org/showthread.php?p=3244514&posted=1#post3244514](http://ubuntuforums.org/showthread.php?p=3244514&posted=1#post3244514) )

Ta!

H

---

