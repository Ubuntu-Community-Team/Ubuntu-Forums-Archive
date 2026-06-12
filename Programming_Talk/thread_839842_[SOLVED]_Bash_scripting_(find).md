---
title: "[SOLVED] Bash scripting (find)"
date: 2008-06-24
forum: Programming Talk
---

### Post by Xaero252 on 2008-06-24
allright basically I am trying to cheat writing a lot of code for recursion to do a trivial task...
I have a LARGE collection of Manga, most of it in CBR, or CBZ format (which through Comix, I have thumbs of the cover), but the rest is in Rar, or Zip format, so what I want to do is Symbolicly link the files into a collection folder...
so far this is my find string:
find ./ -iname \*.rar -exec ln -sfv {} /Manga\ Collection/*.cbr \;
(of course its just changing the extensions to match zip, cbr,cbz for the rest.
however that find string doesn't work as expected, it tries to link the correct file to "*.cbr", instead of what I wanted it to, but how can I fix that???

---

### Post by dwhitney67 on 2008-06-24
I'm not a bash expert, so even though the script below is lengthier than your 'find' command, at least it works -- ACTUALLY, IT DOESN'T WORK -- SORRY!.
```
#!/bin/sh

for file in `find . -name '*.rar'`
do
        FILENAME=`basename $file | cut -d '.' -f1`
        ln -sv $PWD/$FILENAME.rar /Manga\ Collection/$FILENAME.cbr
done
```

---

### Post by dwhitney67 on 2008-06-24
Try this script
```
#!/bin/sh

for file in `find . -name '*.rar'`
do
        FILENAME=`basename $file | cut -d '.' -f1`
        ln -sv $PWD/$file Manga\ Collection/$FILENAME.cbr
done
```
Note how I had to specify $file instead of $FILENAME.rar as I had done previously in my original script.

---

### Post by ghostdog74 on 2008-06-24
> **dwhitney67 said:**
> I'm not a bash expert, so even though the script below is lengthier than your 'find' command, at least it works -- ACTUALLY, IT DOESN'T WORK -- SORRY!.
```
#!/bin/sh

for file in `find . -name '*.rar'`
do
        FILENAME=`basename $file | cut -d '.' -f1`
        ln -sv $PWD/$FILENAME.rar /Manga\ Collection/$FILENAME.cbr
done
```

use a while loop
```

find . -name '*.rar' -printf "%f:%p\n" | while IFS=":" read FNAME FPATH
do
  ln -sv "$FPATH" /Manga\ Collection/${FNAME}.cbr
done

```

---

### Post by lloyd_b on 2008-06-24
> **dwhitney67 said:**
> I'm not a bash expert, so even though the script below is lengthier than your 'find' command, at least it works -- ACTUALLY, IT DOESN'T WORK -- SORRY!.
```
#!/bin/sh

for file in `find . -name '*.rar'`
do
        FILENAME=`basename $file | cut -d '.' -f1`
        ln -sv $PWD/$FILENAME.rar /Manga\ Collection/$FILENAME.cbr
done
```

I think you have the right general idea - this task is a bit too much for the "-exec" option of find.  You made one serious mistake, though - $PWD is *not* the directory containing the file, it's the directory that the script is run in. But that doesn't matter - use $file...

Also, "basename" is perfectly capable of stripping off the .rar extension by itself, without having to resort to "cut".

So here's a version 2 of this script:
```
#!/bin/bash

for FILE in `find . -name "*.rar" -print`; do
    BASE=`basename "$FILE" ".rar"`
    ln -sfv "$FILE" "/Manga/Collection/$BASE.cbr"
done
```

Note: I'm assuming that that backslash "\" after "Manga" was a typo.  At least, I *hope* you don't have any directories with embedded backslashes in them.

One note of warning:  If there are any spaces in the directories or filenames, then the above script won't work properly.

---

### Post by dwhitney67 on 2008-06-24
Ghostdog and Lloyd_b -

I noticed that you left off the $PWD as I indicated in my script.  When I tested my script without the $PWD, it did not setup the symbolic links correctly.

Ghostdog, I tested your script, and it did not setup the links correctly.  Lloyd_b, I suspect yours would have an error too.

Here's the script I used to setup the test:
```
#!/bin/sh

# create dummy directories, including the Manga directory
mkdir -p temp/one temp/two temp/Manga

pushd temp

# create some dummy rar files
touch one/one.rar  one/two.rar  one/three.rar
touch two/four.rar two/five.rar two/six.rar

# run test
find . -name '*.rar' -printf "%f:%p\n" | while IFS=":" read FNAME FPATH
do
        echo "FNAME = $FNAME"
        echo "FPATH = $FPATH"
        echo ""
        ln -sv "$FPATH" Manga/${FNAME}.cbr
done

ls -l Manga

popd
```

---

### Post by rikxik on 2008-06-25
This works perfectly for me:

```

#!/bin/sh

# create dummy directories, including the Manga Collection directory
COLLN=temp/Manga\ Collection
mkdir -p temp/one temp/two "$COLLN"

# create some dummy rar files
touch temp/one/one.rar  temp/one/two.rar  temp/one/three.rar
touch temp/two/four.rar temp/two/five.rar temp/two/six.rar

echo "-----Pre-linking-------"
ls -ltr temp/one temp/two "$COLLN"

echo "-----Linking------------"
find . -name '*.rar' -print |while read file ; do
        ln -s "$file" "$COLLN"/.
done

echo "-----Post-Linking-------"
ls -ltr temp/one temp/two "$COLLN"

```

Tried on Solaris 5.8

HTH

---

### Post by ghostdog74 on 2008-06-25
> **dwhitney67 said:**
> 

Ghostdog, I tested your script, and it did not setup the links correctly.  Lloyd_b, I suspect yours would have an error too.

fyi, i did not test the script using ln. Secondly, try to use full path in the find command. this is tested and working
```

find /full_path -name '*.rar' -printf "%f:%p\n" | while IFS=":" read FNAME FPATH
do
        echo "FNAME = $FNAME"
        echo "FPATH = $FPATH"
        echo ""
        ln -sv $FPATH /destination/${FNAME}.cbr 
done

```

---

### Post by Xaero252 on 2008-06-25
Wow, thank you all so much. well, all of the above are much shorter than I would have tried to write.
the backslash is a cheap workaround for using quotes to handle directory spaces, bash wouldn't interpret a directory name with a space in it if you just did
cat /dev/input devices (if that existed)
you would do
cat /dev/input\ devices and then it would escape the space, much like if you didn't want a double quote to break a string contained in double quotes

Also, perfected script is here (works in all cases, regardless of directory and spaces)
```

#!/bin/sh
#Do Rars first
find "$PWD" -name '*.rar' -printf "%f:%p\n" | while IFS=":" read FNAME FPATH
do
        ln -sv "$FPATH" Manga\ Collection/"`basename "${FNAME}" ".rar"`".cbr 
done
#Now do zips
find "$PWD" -name '*.zip' -printf "%f:%p\n" | while IFS=":" read FNAME FPATH
do
        ln -sv "$FPATH" Manga\ Collection/"`basename "${FNAME}" ".zip"`".cbz 
done

```
personal explination of the code:
basically the quotes around variables ensure the spaces don't get lost
the complicated series of quotes around basename is to ensure proper handling no matter the filename
"$PWD" passed into the find function passes the Present Working Directory to the find function, so say you have manga located in /media/drive/Manga and in /media/drive/somefolder/newManga
you can simply cd to each of those directories, and put the script in your path, now you can just run the script out of you path
obviously you would need to edit the portion with where the files get linked to, but thats no biggie ;-)
thanks for everyone contributing, it works perfectly now XD

---

### Post by ghostdog74 on 2008-06-25
there's no need to have 2 rounds of find. you can simply -name "*.rar" -o -name "*.zip" and in your loop, grab for the file extension and use it in the ln command.

---

### Post by Xaero252 on 2008-06-25
true, but I'm not 100% sure on how to do that, but then again I was just looking for a simple script, polishing more is definately worth the learning experience, so I'll polish it the rest of the way, and post the final polished version here.

---

