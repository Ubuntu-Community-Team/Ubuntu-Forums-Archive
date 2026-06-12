---
title: "Calling clipboard contents into a script"
date: 2008-10-17
forum: Programming Talk
---

### Post by rogerdean on 2008-10-17
Hello all

I'd like to write a script which references and uses the contents of the clipboard when run - how could I do this? It would look like this -

cd /home/roger/Downloads
iplayer-dl [clipboard]

Any ideas? Many thanks
Roger

---

### Post by stylishpants on 2008-10-17
Install the "xclip" package to get xclip.

xclip -o will print the clipboard contents.


You should probably read the clipboard contents into a variable and check that something is in the clipboard.

Something like this (not tested):
```

#!/bin/bash

cd /home/roger/Downloads

# Make sure something is available in the clipboard
# FIXME: Maybe check for the file type you're expecting here?
contents=`xclip -o`
if [ -z "${contents}" ]; then
    echo "Nothing is in the clipboard!"
    exit 1
fi

iplayer-dl "${contents}"

```

---

### Post by rogerdean on 2008-10-18
Brilliant, that works perfectly. Thanks very much indeed

That script, by the way, uses the BBC iPlayer Downloader...

[http://po-ru.com/projects/iplayer-downloader/](http://po-ru.com/projects/iplayer-downloader/)

to download programs from the BBC service. The program ID (eg. b00dtz8l which you need to find from the iPlayer website) should be in the clipboard, then the script can be run. There's a problem with video clips at the moment, but radio downloads work fine.

I should say that this software is not made by the BBC, and they probably don't like it much

---

