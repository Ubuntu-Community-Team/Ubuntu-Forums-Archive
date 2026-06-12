---
title: "Bash script help"
date: 2010-10-25
forum: Programming Talk
---

### Post by RedSingularity on 2010-10-25
How can I write a script that runs a specific command and only moves to the next step in the script if the command completes successfully?  I want to run rsync and display a message saying "Done" _ONLY_ if the rsync command successfully completes copying the files.

---

### Post by AlphaLexman on 2010-10-25
The 'exit' value of a successful command should be 0 (zero).

---

### Post by gmargo on 2010-10-25
You can test the exit code from rsync with the shell variable $?.  Zero should indicate success.
```

rsync $OPTS $SOURCE $DEST
rc=$?
if [ $rc -ne 0 ] ; then
    echo "rsync error: $rc"
    exit 2
fi

```

---

### Post by RedSingularity on 2010-10-25
What should I do with that script?

---

### Post by garyed on 2010-10-25
I just finished writing this script with rsync to back up between two computers where one is running two different versions of Ubuntu.
I'm a novice at this & I hope the real programmers don't laugh at how sloppy it is but it works.
```

#!/bin/bash

read -n1 -r -p  "Press \" Y\" to continue with backup or any other key to exit" name
clear
x='y'
y='Y'
if test $x = "$name" ||test $y = "$name"
then
echo ""
echo "Backup is beginning"  
# Backup script if Karmic is running on the music machine
rsync -avhu me@karmic:/media/music /media/Hardy/home/me/backup
if [ $? = 0 ]; then
rsync -avhu /media/Hardy/home/me/backup me@karmic:/media/gusty/home/me/backup
echo " "
echo " Karmic is running on the other computer"
echo ""
else
# Backup script if Gusty is running on the music machine
rsync -avhu me@gusty:/media/music /media/Hardy/home/me/backup
if [ $? = 0 ]; then
rsync -avhu /media/Hardy/home/me/backup me@gusty:/home/me/backup
echo " "
echo "Gusty is running on the other computer"
echo " "
    else 
clear 
echo ""
echo ""
echo "Something is wrong , Backup not working"
echo " Are you sure Linux is running on the other computer ? "
echo ""
read -p "  .. Press \"Enter\" key to exit.."
exit
fi
fi
echo ""
echo ""

 read -p "Backup complete.. Press \"Enter\" key to exit.." 
exit
else
read -p "Backup has been aborted - press \"Enter\" to exit...."
fi
exit


```

---

### Post by RedSingularity on 2010-10-26
garyed thanks for that!  I saw you were using if/else statements.  I did the same in my script and it works great now!  Thanks all of you for your input. :)

---

