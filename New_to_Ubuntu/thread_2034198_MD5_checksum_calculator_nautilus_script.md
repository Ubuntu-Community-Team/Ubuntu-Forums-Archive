---
title: "MD5 checksum calculator nautilus script"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by asmoore82 on 2012-07-28
Coming from this ancient thread: [http://ubuntuforums.org/showthread.php?t=1394388](http://ubuntuforums.org/showthread.php?t=1394388)

The original version of this script has multiple bugs caused by the lack of properly quoting variable references. Such as, it chokes on filenames with spaces in them.

Here's a new one that uses an old zenity progress bar hack I had lying around. It also handles multiple files at once.

```
[COLOR="Blue"]#!/bin/bash[/COLOR]

[COLOR="Blue"]#make a standard zenity title; intentionally [COLOR="Red"]unquoted[/COLOR] throughout[/COLOR]
title=[COLOR="Purple"]"--title MD5checksums"[/COLOR]

[COLOR="Blue"]#feed answers into zentiy list; but also store answer back from the list[/COLOR]
checksum=$( (

[COLOR="Blue"]#make sure list has time to show up below progress bar[/COLOR]
sleep 0.5

[COLOR="Blue"]#zenity progress bar hack; echo is required to begin pulsating[/COLOR]
while echo; do sleep 10; done |
    zenity --progress --pulsate [COLOR="Red"]$title[/COLOR] \
        --text [COLOR="Purple"]"Calculating. May take some time..."[/COLOR] \
        --width 320 &
progressbar=[COLOR="Purple"]"$!"[/COLOR]

for file in [COLOR="Purple"]"$@"[/COLOR]
do
    [COLOR="Blue"]#only process normal files[/COLOR]
    if [ -f [COLOR="Purple"]"$file"[/COLOR] ]; then
        md5sum [COLOR="Purple"]"$file"[/COLOR] | cut -c-32
        basename [COLOR="Purple"]"$file"[/COLOR]
    fi
done
kill [COLOR="Purple"]"$progressbar"[/COLOR]
) | zenity --list [COLOR="Red"]$title[/COLOR] --text "" \
    --height 360 --width 420 \
    --column [COLOR="Purple"]"MD5"[/COLOR] --column [COLOR="Purple"]"File"[/COLOR]
)

[COLOR="Blue"]#display answer if one was picked; maybe good for copying and pasting[/COLOR]
if [ -n [COLOR="Purple"]"$checksum"[/COLOR] ]; then
    zenity --info [COLOR="Red"]$title[/COLOR] --text [COLOR="Purple"]"$checksum"[/COLOR]
fi

[COLOR="Blue"]#End of File[/COLOR]
```

The only limitation is that closing or canceling the zenity dialogs doesn't stop the md5 calculations in the background.

---

### Post by hakermania on 2012-07-28
Very useful! Thanks!

---

### Post by vincentvega2 on 2013-03-17
can you modify this to check/verify md5? more specifically right click an md5 file which contains multiple hashes and start verifying while displaying if each file is "ok" and a status percent of overall completion.

---

