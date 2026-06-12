---
title: "Difficulties capturing multi-line output i shell variable"
date: 2010-09-15
forum: Programming Talk
---

### Post by RocketRanger on 2010-09-15
Hi

I'm trying to capture multi-line output from a shell command in a variable in a shell script. I'm using find to look for jpg files which I pipe to awk to enclose the results in quotes. However when I subsequently try to print out the array it has split the contents at the spaces in the input. Is there a way around this?

The offending snippet looks like this:

```

IMAGES=($(find "$WALLPAPER_DIR" -name "*.jpg" | awk -F':' '{print "\"" $1 "\""}'))

for i in ${IMAGES[@]}; do
	echo "$i"
done

```

And example output:

"/media/Elan/pixx/Wallpaper/Susan
Ward
-
1680x1050.jpg"

---

### Post by lloyd_b on 2010-09-15
> **RocketRanger said:**
> Hi

I'm trying to capture multi-line output from a shell command in a variable in a shell script. I'm using find to look for jpg files which I pipe to awk to enclose the results in quotes. However when I subsequently try to print out the array it has split the contents at the spaces in the input. Is there a way around this?

The offending snippet looks like this:

```

IMAGES=($(find "$WALLPAPER_DIR" -name "*.jpg" | awk -F':' '{print "\"" $1 "\""}'))

for i in ${IMAGES[@]}; do
	echo "$i"
done

```

And example output:

"/media/Elan/pixx/Wallpaper/Susan
Ward
-
1680x1050.jpg"

That's a very common problem - by default, bash uses spaces, tabs, or newlines for "field separators", so having spaces in filenames will make for loops behave oddly.

Fast fix - before the "for ..." loop, add the line ```
IFS=$'\n'
```This tells bash to ignore the spaces (and any tabs), and use just newlines for the field separator.

Lloyd B.

---

### Post by RocketRanger on 2010-09-16
That fixed it. Thank you!

However after I posted the question and waited for the reply I decided to see if the same was possible with python. Within a very short time I had a working solution which looks like this: 

```

#!/usr/bin/python

import os
import fnmatch
import random

base_dir = #Wallpaper dir

# list of valid file types
extensions = ["jpg", "jpeg", "png"]

wallpapers = []
for path, subdirs, files in os.walk(base_dir):
	# find valid files
	buf = []
	for e in extensions:
		buf.extend(fnmatch.filter(files, "*." + e))
		
	for entry in buf:
		wallpapers.append(os.path.join(path, entry))
	
	
random.seed()
wallpaper = wallpapers[random.randint(0, len(wallpapers)-1)]

os.system("gconftool-2 -t string -s /desktop/gnome/background/picture_filename \"" + wallpaper + "\"")

```

against pretty much the same thing in the shell script:

```

#!/bin/bash -

BASE_DIR= #Wallpaper dir

RANDOM=$RANDOM
IFS=$'\n'

IMAGES=($(find "$BASE_DIR" -name "*.jpg" | awk -F':' '{print $1}'))

NO_FILES=`find "$BASE_DIR" -name "*.jpg" | wc -l`
let PIC_NO=$RANDOM%$NO_FILES

gconftool-2 -t string -s /desktop/gnome/background/picture_filename ${IMAGES[$PIC_NO]}

```

Now granted the python is a little longer but it matches a set a file extensions as well. I know this is possible with the shell version as well using regex.

Looking at the two implementations I can't help but feel that while the shell script is a lot more compact it does looks a lot like black magic.

There's not a question or point to this. It just made me wonder and I felt like sharing...

---

### Post by lloyd_b on 2010-09-16
> **RocketRanger said:**
> That fixed it. Thank you!

However after I posted the question and waited for the reply I decided to see if the same was possible with python. Within a very short time I had a working solution which looks like this: 

```

#!/usr/bin/python

import os
import fnmatch
import random

base_dir = #Wallpaper dir

# list of valid file types
extensions = ["jpg", "jpeg", "png"]

wallpapers = []
for path, subdirs, files in os.walk(base_dir):
	# find valid files
	buf = []
	for e in extensions:
		buf.extend(fnmatch.filter(files, "*." + e))
		
	for entry in buf:
		wallpapers.append(os.path.join(path, entry))
	
	
random.seed()
wallpaper = wallpapers[random.randint(0, len(wallpapers)-1)]

os.system("gconftool-2 -t string -s /desktop/gnome/background/picture_filename \"" + wallpaper + "\"")

```

against pretty much the same thing in the shell script:

```

#!/bin/bash -

BASE_DIR= #Wallpaper dir

RANDOM=$RANDOM
IFS=$'\n'

IMAGES=($(find "$BASE_DIR" -name "*.jpg" | awk -F':' '{print $1}'))

NO_FILES=`find "$BASE_DIR" -name "*.jpg" | wc -l`
let PIC_NO=$RANDOM%$NO_FILES

gconftool-2 -t string -s /desktop/gnome/background/picture_filename ${IMAGES[$PIC_NO]}

```

Now granted the python is a little longer but it matches a set a file extensions as well. I know this is possible with the shell version as well using regex.

Looking at the two implementations I can't help but feel that while the shell script is a lot more compact it does looks a lot like black magic.

There's not a question or point to this. It just made me wonder and I felt like sharing...

The 'find' utility can match multiple extensions without having to mess with complicated regexes:```
find . \( -name "*.jpg" -o -name "*.jpeg" -o -name "*.png" \) -print
```(the -o is basically a logical OR, so it matches *.jpg or *.jpeg or *.png).

But the *best* solution for you is the one that you can create and maintain with the least effort.  If you're more comfortable with Python than the shell, then Python is best :)

(and yes, shell syntax *can* look a bit like black magic if you aren't familiar with it.  The big advantage of using a shell script is that it's very portable.  Which I'm guessing is a non-issue for you...)

Lloyd B.

---

