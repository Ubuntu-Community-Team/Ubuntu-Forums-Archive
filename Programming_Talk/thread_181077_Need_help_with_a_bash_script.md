---
title: "Need help with a bash script"
date: 2006-05-23
forum: Programming Talk
---

### Post by ketsugi on 2006-05-23
I'm trying to write a script that will recursively apply md5sum to any number of files and directories and save the output. I have no problem doing this with files, but it's a little trickier with directories. md5sum itself refuses to handle directories, so I need to get a complete list of files (with path names) to pass to md5sum.

I originally tried to use ls to get this list, but ls doesn't seem to be able to do what I want.

find seemed a lot more promising, but I'm running into a problem with files/directories with spaces in them.

For example, I have this directory structure:
```
- documents
|- file1
|- file2
|- file with spaces
|- file3
```

I then run this command:
```
for file in `find documents -type f`; do md5sum $file; done
```
This runs fine for files 2-3, but breaks on the file with spaces, trying to run md5sum on "file", "with", and "spaces" instead.

No worries, I thought. I modified the command to
```
for file in "`find documents -type f`"; do md5sum "$file"; done
```
This gave a strange little error:
```
md5sum: documents/file1
documents/file2
documents/file with spaces
documents/file3: No such file or directory
```
In other words, the entire string as is got parsed as a single item in the for loop.

Is there any way to get this to work?

Btw I've tried this:
```
find documents -type f -print0 | xargs -0 md5sum
``` and it works beautifully, but I'd like to be able to (ideally) have a single call to md5sum for each file, so I can pass the info on to zenity's progress bar dialog, so the user can see the progress of the md5sum. I can always fall back to the xargs methods if I have no choice, but I'd really like to be able to give the user some progress feedback.

---

### Post by egon spengler on 2006-05-23
[QUOTE=ketsugi]
```
for file in "`find documents -type f`"; do md5sum "$file"; done
```
This gave a strange little error:
```
md5sum: documents/file1
documents/file2
documents/file with spaces
documents/file3: No such file or directory
```
In other words, the entire string as is got parsed as a single item in the for loop.

Is there any way to get this to work?

Btw I've tried this:
```
find documents -type f -print0 | xargs -0 md5sum
``` and it works beautifully, but I'd like to be able to (ideally) have a single call to md5sum for each file, so I can pass the info on to zenity's progress bar dialog, so the user can see the progress of the md5sum. I can always fall back to the xargs methods if I have no choice, but I'd really like to be able to give the user some progress feedback.[/QUOTE]

I would assume that the top example here would work if you remove the quotes from around the back-ticked find command and leave them solely around the $var.

Also find has an option called -exec which can execute a command on each file found in turn (there's also -ok which asks you before each execution).

The syntax is ```
find / -iname foo -exec rm {} \;
```

where {} is a reference to the current file. The semi colon has to be escaped

---

### Post by 5-HT on 2006-05-23
Sorry, can't help you with the scripting issue, but have you heard of md5deep?

It's similar to md5sum, but can recursively examine directory trees and also provides a time estimation (among other things).

It's in Dapper's Universe.

[http://md5deep.sourceforge.net/]("http://md5deep.sourceforge.net/")

Would it be of any help?

 
HTH

---

### Post by ketsugi on 2006-05-23
[quote="egon_spengler"]I would assume that the top example here would work if you remove the quotes from around the back-ticked find command and leave them solely around the $var.[/quote]
Unfortunately, no. Quoting either of the two (or neither) leaves the spaced filename broken, and quoting both gives the peculiar long string as I've shown.

Yes, I know about the exec command, but that won't quite work either for what I'm looking for. I want to be able to do something like this with zenity:
```
# Generate hashes
(
for file in $infiles
do
	echo "# $file..."
	md5sum "$file" >> "$outfile"
	((perc = perc + perc_inc))
	echo "$perc"
done
) | zenity --progress --text="Generating hashes..." --percentage=0 --auto-close
```
So that the progress bar will fill to 100% normally, and also show the name of the current file being processed. If I use the exec or xargs method, I'll be forced to show a pulsating progress bar that gives no indication whatsoever of progress, which is undesirable.

---

### Post by ketsugi on 2006-05-23
5-HT, md5deep looks promising, but I don't see how I can redirect the time estimation info to zenity.

Also, I'd prefer to be able to rely on coreutils' md5sum for this... my issue isn't so much with being able to make md5sum traverse a directory as I can already do this using exec or xargs, but to retrieve a list of all files within a directory in a format that can be parsed properly in a bash for-loop.

---

### Post by egon spengler on 2006-05-23
Ok, instead of backticks try wrapping the find command like this ```
"$( find gift\ of\ gab/ -type l )"
```

edit:
actually that doesn't work either. This time I tested before replying but all I did was echo which in the terminal looks like it was working, but now it's just one long string of all the files. Maybe you could take that long string chop it with sed?

edit2:

Would this produce the right output to pass to zenity?

```
$ find -type f | while read i ; do md5sum "$i" ~/ ; done
```

---

### Post by simonn on 2006-05-23
I find using the -printf param of find very handy.

If you leave the | sh off the end, you can see and check what the command would actually do before doing it.

```

find documents -type f -printf "mdbsum \"%P\"\n" | sh

```

---

### Post by ketsugi on 2006-05-24
[QUOTE=egon spengler]Would this produce the right output to pass to zenity?

```
$ find -type f | while read i ; do md5sum "$i" ~/ ; done
```[/QUOTE]

That did the trick! Thanks a bunch.

---

### Post by Arndt on 2006-05-24
[QUOTE=ketsugi]
Btw I've tried this:
```
find documents -type f -print0 | xargs -0 md5sum
``` and it works beautifully, but I'd like to be able to (ideally) have a single call to md5sum for each file, so I can pass the info on to zenity's progress bar dialog, so the user can see the progress of the md5sum. I can always fall back to the xargs methods if I have no choice, but I'd really like to be able to give the user some progress feedback.[/QUOTE]

It seems the -n option to 'xargs' should do what you want:

```
find documents -type f -print0 | xargs -n 1 -0 md5sum
```

---

### Post by ketsugi on 2006-05-24
Here's my completed script, to be used as a Nautilus script (I don't know if there's a Konqueror equivalent). Save it in ~/.gnome2/nautilus-scripts/md5sum and chmod +x it.

I'd welcome feedback/criticism/suggestions on the script. I'll be working on a companion script soon to graphically open and check md5 digests files.

```
#!/bin/bash

# md5sum - GUI script
# Copyright © 2006 Joel Pan <spamtastic@ketsugi.com>
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# The full text of the GNU General Public License can be found at
# <http://www.gnu.org/copyleft/gpl.html>
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

title="md5sum"
icon="/usr/share/Tango/16x16/apps/system-file-manager.png"
path=`pwd`

# Get the name of the file to output to
outfile=`zenity --title="$title" --window-icon=$icon --file-selection --filename="$path/md5sums" --save`

if [[ $? -ne 0 ]]
then exit 1
fi

if `ls "$outfile" > /dev/null` # Check if the file exists...
then
	# File exists, ask if we want to overwrite the file.
	if `zenity --window-icon=$icon --question --text="$outfile already exists. Do you want to overwrite this file?"`
	then
		# Yes, let's overwrite it! Or rather, let's remove it.
		`rm -f "$outfile"`
	else
		exit 0
	fi
fi

# Calculate how many files there are to process
numfiles=`for file in "$@"; do find "$file" -type f; done | wc -l`
	
# Calculate the percentage increase for each file (or the file increase for 1%, if there are too many files)
if [[ $numfiles -ge 100 ]]
then ((file_inc = numfiles / 100))
else ((perc_inc = 100 / numfiles))
fi
perc=0
filecount=0

# Generate hashes
(
for file in "$@"
do
	find "$file" -type f
done |
while read i
do
	echo "# $i..."
	md5sum "$i" >> "$outfile"
	# Calculate the current percentage
	if [[ $numfiles -ge 100 ]]
	then
		if [[ filecount -eq file_inc ]]
		then
			((perc += 1))
			filecount=0
		else
			((filecount += 1))
		fi
	else
		((perc += perc_inc))
	fi
	echo "$perc"
done
) | `zenity --title="$title" --window-icon=$icon --progress --text="Generating hashes..." --percentage=0 --auto-close`; exit=$?

if [[ $exit -eq 0 ]]
then # Everything went well, let's finish this up
	zenity --info --title="$title" --window-icon=$icon --text="Hashing complete."
	exit 0 
else # We got canceled! Okay well, let's kill off md5sum and remove the digests file
	killall md5sum
	rm -f "$outfile"
	zenity --error --title="$title" --window-icon=$icon --text="Hashing canceled."
	exit 1
fi

exit 0

```

---

### Post by dgray_from_dc on 2007-09-27
Great script!!  However, why do you remove the output file in the event of an error?  I've fought with md5deep and md5sum and gotten them working in Krusader for KDE I have not however created anything that would indicate progress, errors, or anything.  The only thing I have to let me know what happened is the output file (sometimes).  In the case of this script, leaving the file may serve as a backup indication.  Just my opinion.  In any event this is a crafty bit of scripting!

Question.  If I understand correctly, zenity is being used for output into a nice neat Gnome dialog box.  Is that correct?  If so, any idea of what the KDE equivalent is?  Edit: Found it, KDialog.

---

