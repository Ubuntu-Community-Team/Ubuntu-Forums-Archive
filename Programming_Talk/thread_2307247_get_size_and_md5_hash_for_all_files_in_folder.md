---
title: "get size and md5 hash for all files in folder"
date: 2015-12-23
forum: Programming Talk
---

### Post by wbloos on 2015-12-23
Hi,

I've made this little script that gets size and md5 hash for all files in one snapshot of our backup.
The reason is that the backup service uses some kind of hardlinks on a ZFS file system. That's great because it saves a lot of space, but it makes it hard to explain the volume of backup that we're using. Since we have 10 snapshots in rotation, files that change every day take up 10 times more space than files that don't change at all.
The hardlinks are not detected by du, all the files seem to take up full space. That's why a simple du command won't help.

```

#!/bin/bash
while IFS= read -r -d '' file; do
	size=$(stat --printf="%s" "$file")
	hash=$(md5sum "$file" | cut -f1 -d ' ')
  printf "$size"\\t"$hash"\\t"$file"\\n
done < <(find /mnt/backup/.snapshots/`date +\%F`-*/ -type f -print0)

```

So i made the above bash script. I found some handy code snippets on the internet which made my script work pretty much the way i want, but there's a few things that i don't understand. Also, there are 2 problems:
[LIST=1]
[*]Files that have a percent sign in the file name cause problems: the filename is truncated and there will be no newline.
[*]The script takes very long to complete. I might be causing more IO than necessary. AFAIK, "read" will read the whole file. But probably, md5sum nor stat will use that information, will they?
[/LIST]

Any help would be very much appreciated!

---

### Post by wbloos on 2015-12-23
Ok i think this resolves the first problem, with the percent signs.

```

#!/bin/bash
while IFS= read -r -d '' file; do
	size=$(stat --printf="%s" "$file")
	hash=$(md5sum "$file" | cut -f1 -d ' ')
  printf "%s\\t%s\\t%s\\n"  "$size" "$hash" "$file"
done < <(find /mnt/backup/.snapshots/`date +\%F`-*/ -type f -print0)

```

Then, i found the documentation on the read command (online), "man 2 read" is not the correct page. [http://linuxcommand.org/lc3_man_pages/readh.html](http://linuxcommand.org/lc3_man_pages/readh.html)
So it turns out that read is part of bash itself and just reads from stdin, not the whole file. Since -print0 (in find) creates null-delimited output, the line with "IFS= read..." seems to be an effective but not so intuitive way of setting the delimiter to a null character in bash and then reading from stdin, which contains a list of the full filenames in the folder.
It would be nice if someone could confirm that.

---

### Post by steeldriver on 2015-12-23
It's the 
```
-d '' 
```
part that sets the read delimiter to null - see "help read"

```

      -d delim    continue until the first character of DELIM is read, rather
            than newline

```

but yes read reads a single "line" of input (default == up to newline, here == up to \0) from stdin (or from another file descriptor, if you use the -u option)

However your md5sum needs to read the whole of each file in order to calculate its hash

---

### Post by lukeiamyourfather on 2016-01-04
What exactly are you trying to get from this information? ZFS has several commands that might just give you the info you're looking for without having to reinvent the wheel.

---

### Post by lukeiamyourfather on 2016-02-01
I saw this and thought of this thread. See slide number 19 because I think it does what you're wanting to do and is a lot more straightforward.

[https://fosdem.org/2016/schedule/event/zfs/attachments/slides/869/export/events/attachments/zfs/slides/869/FOSDEM_2016_ZFS.pdf](https://fosdem.org/2016/schedule/event/zfs/attachments/slides/869/export/events/attachments/zfs/slides/869/FOSDEM_2016_ZFS.pdf)

---

