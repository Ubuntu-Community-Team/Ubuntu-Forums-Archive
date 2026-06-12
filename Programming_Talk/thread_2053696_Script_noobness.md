---
title: "Script noobness"
date: 2012-09-05
forum: Programming Talk
---

### Post by MarshyTheKid on 2012-09-05
I'm trying to write a script so when I right click on a rar file it will automatically extract it to a folder. 

```
#! /bin/bash/
unrar x -y $f /home/MarshyTheKid/Videos/Share/
#Notify
notify-send -t 3600 $PWD "Finished!"
```

$ sh ExtractToVideos /home/MarshyTheKid/Desktop/random.rar 


Cannot open /home/MarshyTheKid/Videos/Share.rar
No such file or directory
No files to extract



What am I missing here?

---

### Post by spjackson on 2012-09-06
The first line of your script should be
```

#!/bin/bash

``` - no space and no trailing slash. Are you wanting to use bash as per line 1 or sh as per your command line?

$f is not set so is replaced by nothing. The first command line parameter is $1, so
```

unrar x -y "$1" /home/MarshyTheKid/Videos/Share/

```

---

### Post by MarshyTheKid on 2012-09-06
Okay, I tried that.
I'm using caja with the Mate desktop. 
I saw in another script it was using NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
so I tried changing it how they had it. I've been trying to search for scripting guides but I haven't had any luck finding something to help.

So now this is what the script is
```
#!/bin/bash/
filename=$(echo "$CAJA_SCRIPT_SELECTED_FILE_PATHS")

unrar x -y $filename /home/MarshyTheKid/Videos
#Notify
notify-send -t 3600 $PWD "Finished!"
```
But still, when I right click on a .rar and run the script, nothing.

---

### Post by spjackson on 2012-09-06
Sorry, I was responding specifically to this part of your post
```

$ sh ExtractToVideos /home/MarshyTheKid/Desktop/random.rar 


Cannot open /home/MarshyTheKid/Videos/Share.rar
No such file or directory
No files to extract

``` I don't know anything at all about Caja and not much about Mate.

---

### Post by MarshyTheKid on 2012-09-06
Oh okay.

Scripting wise it should just be a matter of changing it from NAUTILUS_SCRIPT_SELECTED_FILE_PATHS to CAJA_SCRIPT_SELECTED_FILE_PATHS, based upon migration scripts for Caja and Mate.

---

### Post by MarshyTheKid on 2012-09-06
Alrighty. Figured it out from following along this adventure. [http://ubuntuforums.org/showthread.php?t=1845652&page=2](http://ubuntuforums.org/showthread.php?t=1845652&page=2)

Still kinda unsure why some of my attempts didn't work but that did, but I now have some bash scripting tutorials saved to play around with. It'll help me get my coding fingers back. :)

```

#!/bin/bash
unrar x -y "$1" "/home/MarshyTheKid/Videos/Share/"
notify-send -t 3600 $PWD "Finished!"

```
All that for 3 lines of code. :p I think it also would have helped if Mate wasn't so buggy.

---

