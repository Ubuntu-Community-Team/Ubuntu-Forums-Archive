---
title: "Replacing bad characters"
date: 2006-10-11
forum: Programming Talk
---

### Post by rbroen on 2006-10-11
Hi Everybody,

I'm about to migrate an Mac OS X server to an Ubuntu server, but a lot of bad characters are stopping me. In the (distant) past people have named files (and directories ) in the following sloppy way:

This is the "test' file / please don't move.txt
Johnson & Johnson chart part 1/2.eps

Copying files like these is a bit of a problem....

Is there anybody who can help me with a bash (/perl/other) solution? (Mac OS X has a bash and perl environment, so that shouldn't be a problem.)

I've looked into a samba solution, but couldn't find any "SOLVE CHARACTERPROBLEM = YES" option for the smb.conf file.

Any help would be greatly appreciated.

---

### Post by foxylad on 2006-10-11
I'd write a short python program to do this. Read a directory,  make a new version of the filename with only letters, numbers and periods, and then rename the file. 

If you're not programmer, either consider paying someone to do this or learn - this is an ideal example to cut your teeth on.

---

### Post by JonahRowley on 2006-10-11
They're not "bad" characters, they just mean something special in the shell.  They can be escaped or quoted though, so in your script to move everything over, just make everything is quoted (as everything in a shell script should be anyway).

```

$ touch 'test & test'
$ ls -ld 'test & test'
-rw-r--r-- 1 uzi uzi 0 2006-10-11 18:37 test & test

```

See?  All is good.  If you forget to quote the & character, it'll launch ls in the background with an incomplete filename, and then probably try to launch an invalid command with what's left on the line.

---

### Post by steve.horsley on 2006-10-11
I don't think '/' is a legal character in a Linux filename. I'm surprised it's allowed in OSX. 
I don't know of a samba setting that would mangle filenames to fix this (I'm no expert). You could run a script on the OSX machine to rename the files, then copy them. If OSX has python, this script should work:
```

#!/usr/bin/python
import os
for name in os.listdir("."):
    if "/" in name
        os.rename(name, name.replace("/", "-"))

```

I'm no good with shell (bash) scripts.

---

### Post by slavik on 2006-10-12
```

#!/usr/bin/perl
@files = `ls`; #I forget the exact glob parameter
for (@files) {
    $newname = $oldname = $_;
    $newname =~ tr|/|_|;
    `mv $oldname $newname`;
}

```

If you dig around, you can get it done in less lines. :P

---

### Post by JonahRowley on 2006-10-12
Oops, I missed the slashes in the filenames.  Assuming OSX has the find command, this would work:

```

find /some/path -name '*/*' -exec mv "{}" `echo {} | tr / _` \;

```

I have no idea why OSX would allow slashes in filenames.  If you have a test/test file, and a test directory with a test file in it, what does test/test refer to?  It's ambiguous!

---

### Post by rbroen on 2006-10-16
> I have no idea why OSX would allow slashes in filenames.
It turns out that slashes are shown, but not used; in the shell they show up as ":"; the ":" itself is not allowed in filenames.

---

### Post by rbroen on 2006-10-16
> **foxylad said:**
> If you're not programmer, either consider paying someone to do this or learn - this is an ideal example to cut your teeth on.

Hi,

I'm a php/sql programmer with limited bash experience. Yes I would like to improve my Bash skills, and yeas I'm reading up on it with help of my good friend O'Reilly.... but sometime you have to get work done now. 

Because of the power of Bash, I'm certain that it can be done in an compact and elegant way... for now, I'll use a quick GUI tool and keep on learning Bash programming. 

@everybody:
Thank you for your help!

---

### Post by rbroen on 2006-10-20
Ok, this is what I'm using to plow trough 80.000 files (of which 1.000 need fixing). It could probably be prettier or more efficient, but thank God it works! 

```


#!/bin/bash

# this is the script I wrote for preparing filenames for the migration
# from Mac OS X Server 10.2.8 to Ubuntu 6.0.6 

# This script will have to run serveral times;
# files in a directory with a name that needed changing will not be processed correcly.
# i just restart the script until I'm convinced that the job is done.

# the -r make sure the \ will stay included
find /Users/rbroen/Desktop/bash/testmap -name '*' | while read -r file ; do

	# the length of the filenames dit not cause trouble at 137 characters
	#     something I can live with
	
	# problem characters while migrating from macosx to ubuntu:  ? " * / \
	# the / from the finder (GUI) is actualy a : in the terminal
	
	# This seems to work for everything exept the *
	tempstep="${file//[\?\:\\]/_}"

	# I'll use tr tot take care of the *
	newname=`echo "${tempstep}" | tr '?*\"\' "_"`
	
	
	# for some strage reason the following comparison fails if there are 
	# brackets [ ] in $file or $newname, even if they are the same!?
	if [[ $file != $newname ]] 
	then
		
		echo mv "${file}" "${newname}"
		mv "${file}" "${newname}"

	fi
	
done


```

---

### Post by JonahRowley on 2006-10-22
```

$ a="abc123/:?*"
$ echo ${a//[\/:?*]/_}
abc123____

```

Hmm..  I didn't have any problems there.  The script looks pretty good.  I'd make it a **mv -i** though, you could possibly wipe out some files by accident.

---

