---
title: "[SOLVED] BASH Directory Recursion"
date: 2008-06-09
forum: Programming Talk
---

### Post by Barriehie on 2008-06-09
I've looked at this for hours and can't find it!!!  Can anyone please tell me why my LoopCounter isn't incrementing???   At least it appears to not be.  When I run this I only get a directory listing consistent with dirr[0].

Thank You,
Barrie

It's BASH and not PHP / _[COLOR=Black]First time around I'm just ls'ing the files and not rm'ing them[/COLOR]_.
I read the FAQ. :)

[php]
#!/bin/bash

#
#    Recourse through .thumbnail folder and sub-folders removing the .png files.
#        

#
#    Define variables
#
dirr[0]="/home/barrie/.thumbnails/normal/*.png"
dirr[1]="/home/barrie/.thumbnails/large/*.png"
dirr[2]="/home/barrie/.thumbnails/fail/gnome-thumbnail-factory/*.png"
dirr[3]="/home/barrie/.thumbnails/fail/gqview-1.0/*.png"
dirr[4]="/home/barrie/.thumbnails/fail/thunar-vfs/*.png"

LIMIT=5
LoopCounter=0

#
#    Loop through dirr[array] and delete the thumbnails
#
while [ "$LoopCounter" -lt "$LIMIT" ]
    do
#
#        Get the recursion to work then we'll rm the files.
#
        ls -c ${dirr[$(LoopCounter)]}
        let "loopcounter += 1"
    done
#
#    Bye
#
exit 0
[/php]

---

### Post by Phenax on 2008-06-09
Well, you could do this much easier with the find command.

```
find [COLOR=#000000][COLOR=#dd0000]/home/barrie/.thumbnails/ -iname \*.png -exec rm {} \;[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#dd0000]
[/COLOR][/COLOR]

---

### Post by Barriehie on 2008-06-09
> **Phenax said:**
> Well, you could do this much easier with the find command.

```
find [COLOR=#000000][COLOR=#dd0000]/home/barrie/.thumbnails/ -iname \*.png -exec rm {} \;[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#dd0000]
[/COLOR][/COLOR]

Well, that knocked about 32 lines of code out of my backup script and enlightened me to yet another command.  Thank you Phenax!  I'ld still like to know why my script doesn't work though :confused:

Barrie

---

### Post by ghostdog74 on 2008-06-09
look at your spelling please.

---

### Post by HalPomeranz on 2008-06-09
> **Barriehie said:**
> I'd still like to know why my script doesn't work though

Your while loop is a bit busted.  Try this on for size:

```

while [ "$LoopCounter" -lt "$LIMIT" ]
    do
#
#        Get the recursion to work then we'll rm the files.
#
        ls -c ${dirr[$LoopCounter]}
        LoopCounter=$(( $LoopCounter + 1 ))
    done

```

---

### Post by Barriehie on 2008-06-09
Thank you all for your prompt responses.  I'll have to look at that later; or come up with another beginner script.  I almost had it and then broke it!

---

