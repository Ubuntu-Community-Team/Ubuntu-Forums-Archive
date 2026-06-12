---
title: "Rename files based on 'creation' date (dumb Olympus VN8100PC digital voice recorder)"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by rocksockdoc on 2012-04-18
Q: How to rename files, en masse, based on 'creation' date? (YYYYMMDD-HHMMSS.mp3)?

I bought an Olympus VN8100PC digital voice recorder which has no method of naming voice recorded files other than in a numerical sequence. I called Olympus Technical Support (888-553-4448 press 4 and then press 2) who said they didn't support Linux - but even on Windows, they said you had to manually name based on the "creation date".
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216267&stc=1&d=1334789176[/IMG]
But, after moving the files (via USB cable) over to the laptop, I will be editing these files in Audacity, and once I do that, the file date stamp can/will change. 

At that point, the file dates will be a royal mess.

May I ask if you already know of a program which will rename files based on the creation date (e.g., 20120418-154259.mp3 for today at 3:42:59 pm)?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216266&stc=1&d=1334789060[/IMG]

---

### Post by TeoBigusGeekus on 2012-04-18
In linux, the creation date isn't stored (at least in the commonly used file systems). You could go though with the modification date: if you haven't touched the files, the modification date should be the same as the creation (birth) date.
Put this code
```
#!/bin/bash
for i in *.mp3
do
	mod_date=$(stat -c "%y" "$i"|sed 's/\..*$//')
	cp "$i" "$mod_date".mp3
done
```
in a text editor and save it as mass_date_renamer (or whatever).
Open a terminal, navigate to the path of the script and make it executable:
```
chmod +x mass_date_renamer
```
Then put it in the folder where your mp3s are and run it with
```
./mass_date_renamer
```
The script will create copies of all the mp3s in the folder changing their names to their last modification date. If you want the files to be renamed and not copied, change the cp command to mv.

---

### Post by rocksockdoc on 2012-04-18
> **TeoBigusGeekus said:**
> 
    mod_date=$(stat -c "%y" "$i"|sed 's/\..*$//')
    cp "$i" "$mod_date".mp3

Thanks! This worked first time!

I created three test files at three different time points, and ran the script, and it worked great. Now I'll just munge the stat command to get rid of the spaces which are always a problem in a file name.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216276&stc=1&d=1334800175[/IMG]

---

### Post by rocksockdoc on 2012-04-18
OK. Here's the slightly modified code with no spaces in the resulting file name.
```

#!/bin/bash
for i in *.mp3
do
#  mod_date=$(stat -c "%y" "$i"|sed 's/\..*$//')
   mod_date=$(stat -c "%y" "$i"|awk '{print $1"_"$2}'|sed 's/\..*$//')
  cp "$i" "$mod_date".mp3
done

```

Here's the result of a quick test:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216277&stc=1&d=1334801341[/IMG]

---

### Post by rocksockdoc on 2012-04-19
Unfortunately, the colon makes the file names not usable on Windows so I'll need to modify.

To modify, I'll need to understand the sed.

Is this the meaning of the sed below:
mod_date=$(stat -c "%y" "$i"|awk '{print $1"_"$2}'|sed 's/\..*$//')

s/   search for 
\.   a literal period
.    then another character
*   any number of them
$   to the end of the line
/    replace that with
/    nothing

---

### Post by rocksockdoc on 2012-04-19
This solves the colon problem and removes the extraneous dashes also:
```

#!/bin/bash
# Copy MP3 files in a directory to a new name based solely on creation date
# FROM: foo.mp3  Created on: 2012-04-18 18:51:44
# TO:    20120418_185144.mp3
for i in *.mp3
do
#  mod_date=$(stat -c "%y" "$i"|sed 's/\..*$//')
#  mod_date=$(stat -c "%y" "$i"|awk '{print $1"_"$2}'|sed 's/\..*$//')
mod_date=$(stat --format %y "$i"|awk '{print $1"_"$2}'|cut -f1 -d'.'|sed 's/[: -]//g')
 cp "$i" "$mod_date".mp3
done

```

---

