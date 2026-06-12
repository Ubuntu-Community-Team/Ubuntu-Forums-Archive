---
title: "Help With Script for WIPE"
date: 2007-07-08
forum: Programming Talk
---

### Post by Deathmoon on 2007-07-08
I've read that shred doesn't work for ext3 partitions and that wipe is the next best.  Therefore, I wanted to create a script (to place in my right-click nautilus options) - much like the shred option for Nautilus Scripts (btw shred doesn't work).

Anyway...I wrote the following and I cannot seem to get it to work...any ideas?  This is only my 2nd script to write therefore please provide feedback; I want to learn.  

Thanks in advance.

```

#!/bin/bash
clear

#if filename is NULL then exit script
if [ -z "$1" ]
then
exit 1
fi

gdialog --title "$1" --yesno "Are you sure you want to WIPE 
$1"

#cancel = 1
#ok = 0

#need to know path of file
if [ $? = 0 ]
then
echo "wipe now"
wipe -f -P 227 -S r "$1"
echo "file wiped"
fi

#EXIT #1
1

```

---

### Post by Deathmoon on 2007-07-08
I have not changed all that much in the code below.  However, if I right click on the file in the location of the script (e.g. I have destroy.sh in /test/ and I also have binder.doc in /test/) and I right click on binder.doc and send to destroy in my scripts context menu; this script works.  However, if I have binder.doc in any other folder it does not get wiped, nor does my output file get generated.  I've done a search on my filesystem for *.dtest and nothing comes up therefore from a debug standpoint I have no clue where to go now.

```

#!/bin/sh
clear

# set the 'file' variable first
file="$1"

# dirname
dirname=`dirname "$file"`

{ # BEGIN CODE BLOCK
	echo "$file"
	echo "$dirname"

	gdialog --title "$file" --yesno "Are you sure you want to WIPE $file"

	# RETURN VALUES
	# Cancel = 1
	# Ok 	= 0
	
	if [ $? = 0 ]
	then
	wipe -f -P 227 -S r "$file"
	echo "File wiped!"
	fi
   echo
} > "$1.dtest"



```

---

### Post by Deathmoon on 2007-07-08
RESOLVED:

```

#!/bin/sh
clear

# set the 'file' variable first
file="$1"

gdialog --title "$file" --yesno "Are you sure you want to WIPE $file"

# RETURN VALUES
# Cancel = 1
# Ok 	= 0
	
if [ $? = 0 ]
then
wipe -f -P 227 -S r $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
fi



```

---

