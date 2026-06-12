---
title: "Small bash script ? (converts a windows md5 file to one usable in linux)"
date: 2012-03-17
forum: Programming Talk
---

### Post by jerome1232 on 2012-03-17
I was helping this guy in this thread [http://ubuntuforums.org/showthread.php?t=1941596](http://ubuntuforums.org/showthread.php?t=1941596) with an issue about some md5sums, it turned out he just needed to convert newlines in his files and change all instances of \ to /.

Anyways I tried to help him create a small and dirty (since I'm terrible at bash scripting) script to do the job. The one I gave has an issue with paths enclosed in qoutes "", it also has issues if you give it ~/ as a path (probably other things)

If you read the thread the OP would like the script to convert say md5sum to the file linuxmd5sum, how can you accomplish the automatic appending of a fixed string to the file path?

See the thread for the actual script and the actual purpose of the script. I'm asking because I'm curious and I'm not happy with handing him a crappy script as the solution.

---

### Post by CynicRus on 2012-03-17
cat file_win.txt | tr -d "\r" > file_.txt

---

### Post by jerome1232 on 2012-03-17
Perhaps it'll be better for me to actually post the script in here, this was the script I ended up on, it doesn't like filenames enclosed in " " and it doesn't like me using something like ~/Desktop.

I also was wondering if it's easy to just scrap specifying a target, and have it simply append "linux" to the old filename and use that as the new filename.

```
#!/bin/sh
if [ -z "$1" ] || [ -z "$2" ]; then
        echo usage: $0 infile outfile
        exit
fi

SRCF=$1
TGTF=$2
dos2unix "$SRCF" "$TGTf"
sed -i 's:\\:\/:' "$TGTF"

exit 0
```

---

