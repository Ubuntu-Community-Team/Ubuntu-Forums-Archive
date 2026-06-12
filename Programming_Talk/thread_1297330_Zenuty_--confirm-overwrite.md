---
title: "Zenuty --confirm-overwrite"
date: 2009-10-21
forum: Programming Talk
---

### Post by rhalaquist on 2009-10-21
Hi not sure if this is really the right place for this but here goes...
How can I make this:

```
#!/bin/bash
#Move multiple files
moveThis=`echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`
toHere=`zenity --multiple --file-selection --directory`
mv $moveThis $toHere
```so that it will not over-write a file if it is there ( I am new to this as you can probably tell)
I tried 
```
toHere=`zenity --multiple --file-selection --save --confirm-overwrite --directory'
```using all sorts of scenarios.. meaning moving the --save and --confirm-overwrite in different positions what happens is I do get the dialog and it will not move nothing when I click ok (the dialog still stays) however when I click cancel it will move one of the 2 files, I tried it with 3 files, 2 that were in the spot I was moving to and one not, when I click ok nothing, then when click cancel nothing. Any help or pointing me in a direction that might be able give me help will be appriciated, thanks!

---

### Post by geirha on 2009-10-21
I believe the --confirm-overwrite option only makes sense when selecting files, not directories. Instead you could check whether the directory is empty or not in bash, and use a zenity --question if it's not empty.

How to check if a directory is empty or not is explained here [http://mywiki.wooledge.org/BashFAQ/004](http://mywiki.wooledge.org/BashFAQ/004)

Also, remember to "quote" pattern expansions.
```
mv "$moveThis" "$toHere"
```
Without quotes, you'll get undesired results if either of the variables contains path names with spaces. This has an explanation of why [http://bash-hackers.org/wiki/doku.php/syntax/words](http://bash-hackers.org/wiki/doku.php/syntax/words)

---

