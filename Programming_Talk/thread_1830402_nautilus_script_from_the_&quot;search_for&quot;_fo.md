---
title: "nautilus script from the &quot;search for&quot; folder"
date: 2011-08-21
forum: Programming Talk
---

### Post by PGScooter on 2011-08-21
Hi, I can use nautilus scripts in any folder but I just realized I can't use them (at least to act a single selected file) in the "search for" folder.
I think that the problem is that the following variable is not set for some reason in the "search for" folder:
$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

I want to make a simple script to copy the location of that file. The following script works fine except in that folder:
echo "`dirname "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"`" | perl -pe 's/\n//' | parcellite

Any ideas? Thank you!

---

### Post by hakermania on 2011-08-22
which is the 'search for' folder?

---

### Post by PGScooter on 2011-08-22
The "search for" folder is what I mean when you are in a nautilus folder window and you use the search feature. For example, press control f and search for something. It will display the results of the find. Sorry I'm not sure how to call it.

---

### Post by kaibob on 2011-08-22
I tried a simple Nautilus script that redirected NAUTILUS_SCRIPT_SELECTED_FILE_PATHS to a text file, and I encountered the same issue as you describe when running the script on a file in what you call a "search for" folder. A workaround that did work was to use NAUTILUS_SCRIPT_SELECTED_URIS instead. You have to cut "file://" from the front of the returned path and additional manipulation will be needed if the path contains spaces (spaces in file names are OK). I have no knowledge of parcellite, so this may not work with your script, but it's easy to give it a try.

Anyways, the Nautilus script that I used is:

```
#!/bin/bash

var="${NAUTILUS_SCRIPT_SELECTED_URIS%/*}"
var="${var#file://}"
echo "$var" > "${var}/test.txt"
```

---

### Post by hakermania on 2011-08-23
Also you may wish to go and fill in a bug in nautilus.

---

### Post by PGScooter on 2011-08-25
Thanks for the workaround kaibob! i appreciate your help.

Good idea hakermania. Here is the link to the bug report:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/833520](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/833520)
If anyone feels like confirming the bug and saying that on the report, that could help.

Thanks.

---

