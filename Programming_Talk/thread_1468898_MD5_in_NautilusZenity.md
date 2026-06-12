---
title: "MD5 in Nautilus/Zenity"
date: 2010-05-01
forum: Programming Talk
---

### Post by jamesdcarroll on 2010-05-01
I've always wanted to right click on a file and gets its MD5. So wrote a script for Nautilus:
```
#!/bin/bash
# WriteMD5

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`

md5sum $BASENAME > $BASENAME.md5

exit 0

```

And it would seem to work. What I would like to do though is just display it via Zenity. The following does not work:

```
#!/bin/bash
# ShowMD5

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`

HASH=md5sum $BASENAME
zenity --title $BASENAME --info --text $HASH

exit 0
```

No clue what to do next.... 

Thanks,

---

### Post by kaibob on 2010-05-01
You were pretty close. You have to use command substitution to derive the md5 hash. Also, the md5sum utility returns both the hash and the file name, so I used parameter expansion to remove the file name. I also changed the backticks to the alternate $(...) format, which is preferrred, and I quoted variables just in case any file names contain spaces.

```
#!/bin/bash
# ShowMD5

BASENAME=$(basename "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS")

HASH=$(md5sum "$BASENAME")
HASH="${HASH%% *}"

zenity --info --title "$BASENAME" --text "$HASH"

exit 0
```

---

### Post by jamesdcarroll on 2010-05-01
Thank you very much!

---

### Post by spcwingo on 2011-02-25
I realize that this is an old thread, but I just wanted to thank ya'll for the script.  It has saved me much time and hair (I get kind of tired of opening a terminal and typing "md5sum some_file.iso" and gtkhash just didn't like me at all).  Again, a sincere thanks.

---

