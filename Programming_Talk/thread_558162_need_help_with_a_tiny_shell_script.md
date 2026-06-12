---
title: "need help with a tiny shell script"
date: 2007-09-23
forum: Programming Talk
---

### Post by pedrotuga on 2007-09-23
I have  a load of text files i want to convert from iso-blabla to utf-8

I tested iconv for one file and it worked like a charm
```
iconv -f ISO-8859-15 -t UTF-8 wine.txt>wine2.txt
```

Now i want to recursively convert all files in a directory, but the destination need to be saved in a file with the same name.

I think this is what i have to do, but i don't really know how :

1.get all files name's
2.if its a directory make a recursive call or something
3.if its a file get its content, convert it with iconv and save that same file

can a anybody tell me how to do number 1 for starting?

---

### Post by duff on 2007-09-23
something like this?

```
#!/bin/bash

function recurse {
	ls -1 |
	while read line; do
		if [ -d "$line" ]; then
			pushd "$line" >/dev/null
			recurse
			popd >/dev/null
		else
			echo "$line"
		fi
	done
}

recurse
```

---

### Post by nanotube on 2007-09-24
here's what i can come up with:

```
#!/bin/bash
cd /your/target/dir
find . -type f -print0 |xargs -0 -I'{}' iconv -f ISO-8859-15 -t UTF-8 {}>../newdir/{}

```

then, when it's done, and after you confirm that your target dir (newdir) contains all the files and in the proper encoding, then you can delete your old dir and put the newdir in its place.

(running a script that directly overwrites files is a pretty risky proposition, and generally to be avoided - unless it's a well-tested production-quality script.)

---

### Post by cwaldbieser on 2007-09-24
I would use "find" to copy the file to a temporary location and then iconv it back over the original.  I haven't tested the following:

```

umask 177
TEMPFILE="/tmp/tmp.$RANDOM.$RANDOM.$RANDOM.$RANDOM"
find "$STARTDIR" -type f -print | while read FILE; do cp "$FILE" "$TEMPFILE"; iconv -f $ENCODING -o "$FILE" "$TEMPFILE"; done
rm -f "$TEMPFILE"

```
This snippet create the name of a temp file.  It uses find to recurse the directories looking for regular files.  Each file is copied to the tempfile and then iconv'd back to the original file.  Finally, the tempfile is removed.

---

### Post by pedrotuga on 2007-09-24
A big thanks to the three of you and sorry I came and ask a question like this without understanding $&%$% of shellscript.

duff: yes, I meant something like that, unfortunately I don't even know how to  concatenate strings in shellscript nor how to loop through lines :(
I guess calling your script and pipe it's output to iconv wouldn't work as I would need a iconv call per file.

nanotube: i would kindly ask you to debug your script as i can't make it :(... it 
creates a folder called a file called *newdir{}* and a folder called *newdir* with a file called '{}'. unfortunately that's all it creates. :(

cwaldbieser: I don't have enough shellscript syntax to fully understand your script. More precisely i don't even know how to pass or define the parameters.. i suck!

OK... instead of bother you guys to do my work, i think will make a small php or python script and call iconv from it. I can post it in here just in case somebody runs across a similar problem.

---

