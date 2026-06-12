---
title: "[TIP] Sort files AND folders by size"
date: 2007-07-26
forum: Outdated Tutorials &amp; Tips
---

### Post by KIAaze on 2007-07-26
Since I usually have certain well sorted folders (not all of them ^^), I usually find it easier to search for big files and folders in certain directories.

Here's a way I found to do this:
```
ls -lS --block-size=1 | awk ' {print $5,$6,$7,$8}' >size.txt
du -s --block-size=1 */ >>size.txt
sort -n size.txt

```

The one-line way:
```
ls -lS --block-size=1 | awk ' {print $5,$6,$7,$8}' >size.txt; du -s --block-size=1 */ >>size.txt; sort -n size.txt
```

As you can see, this creates a size.txt file. But it shouldn'take too much space, so I think it's ok.
And it's also not listed itself in size.txt since the command listing files by size comes before.

--block-size=1 was necessary since ls and du seem to use different default block sizes.
As far as I know, this way, the sizes indicated are in bytes. (1 block = 1 byte)

necromancing edit:
I just needed this again and took some time to create a smart script from it:
```

#!/bin/bash
FILE=size.txt

generate_size_file()
{
	TMP=$(mktemp)
	ls -lS --block-size=1 | awk ' {print $5,$6,$7,$8}' >$TMP
	du -s --block-size=1 */ >>$TMP
	sort -n $TMP >$FILE
}

if [ -s $FILE ]
then
	echo "$FILE exists. Overwrite?(y/n)"
	read ans
	case $ans in
	  y|Y|yes) generate_size_file ;;
	  *) echo "Using existing file." ;;
	esac
else
	generate_size_file
fi

cat $FILE

```

See also the posts below for other useful tricks. ;)

---

### Post by frodon on 2007-07-27
Thanks for the tip, i'm making an alias right now :)

And what about a "rm size.txt" at the end of the script/command line ?

EDIT: to have better results (i was missing some file names) i added $9 in the awk command, because otherwise i miss filenames in the output and only get directory names.

---

### Post by KIAaze on 2007-07-27
Thanks for accepting my thread. :)

> **frodon said:**
> 
And what about a "rm size.txt" at the end of the script/command line ?


I didn't do that because the du command takes a lot of time to finish, so I prefer storing the result.
That way I can always just run ```
sort -n size.txt
``` if I need to free more space.

---

### Post by vanadium on 2007-07-27
This is the on-the-fly version that needs no size.txt and additionally pipes the output in the less pager. Output is sorted from big to small.

```

{ ls -lS --block-size=1 | awk ' {print $5,$6,$7,$8}'; du -s --block-size=1 */ ; } | sort -nr | less

```

Nice tricks that can be done on that command line ;)

---

