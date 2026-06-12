---
title: "Howto: Simple Incremental backup."
date: 2006-12-12
forum: Outdated Tutorials &amp; Tips
---

### Post by mcglnx on 2006-12-12
Dear All,

[COLOR="Red"]**WARN: the 'delete' parameters may not do you what you want, please read rsync doc to be sure!**[/COLOR]

Here is a simple script that I found usefull to backup my home dir. It just copies the delta from one dir to the other - While the first call is quite slow, the subsequent ones are very fast.

Using hard links you can even improve this to keep an history without wasting drive space.

I use it so synch my music players, photos backups drive and home dir.

Here is the script. Just copy it to *_your favorite USB backup drive directory_*  and run it (test first on dummy location if you don't want to loose everything ! ;) ):

[INDENT]```

#!/bin/sh

EXCLUDES=exclude.list
touch $EXCLUDES

SRC=$HOME
DT=`date`
LOG=/tmp/backup.${DT}.log
# -- Uncomment this line when you know what you do - 
# This will delete the files you've been delete on the source as well.
#DO_DELETE="--delete --delete-excluded"

echo "Starting backup of $SRC at $DT. "
rsync -Cav $DO_DELETE             \
      --exclude-from="$EXCLUDES"  \
      $SRC . > $LOG
DT=`date`
echo "Done at $DT"


```[/INDENT]

On the same directory I have an exclude.list file containing something like:

[INDENT]```

*/import/*
*/tmp/*
*/src/*
*/.bochs/*
*/.gnome/*
*/.mozilla/*/Cache/*
*/.mldonkey/*
*/.aMule/*

```[/INDENT]

---

### Post by gimfred on 2007-03-25
Thanks! I may implement this.

---

### Post by malarie on 2010-04-06
Cna you use rsync to create incremental backups?

---

### Post by mcglnx on 2010-04-07
Sure: you can use hard links for example. See [http://www.mikerubel.org/computers/rsync_snapshots/#Incremental](http://www.mikerubel.org/computers/rsync_snapshots/#Incremental)

---

### Post by fmmarzoa on 2011-01-13
Is it not better just to use rdiff-backup?

[http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)

---

### Post by mcglnx on 2011-01-14
Looks great indeed - I'll give it a try.
I'm aslo trying deja-dup... not 100% what I need, but still not bad.

---

