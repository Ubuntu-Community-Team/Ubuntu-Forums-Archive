---
title: "[SOLVED] Bash/Nautilus script to reencode file(s) with iconv"
date: 2007-02-24
forum: Programming Talk
---

### Post by Simon-v on 2007-02-24
Good day all. I've been thinking about this for some time and i'm starting to think i'm missing something really simple, yet important. A common mistake, maybe?

I'm trying to make a bash/Nautilus script to reencode file(s) into a different encoding with the "iconv" command. It works perfectly from terminal; my wish is to automate it, even if a bit.
I figured to use the $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS variable, however the script still, as before, spits out an empty file.
The code i'm using is
```
#!/bin/bash
#
iconv -f cp1251 -t utf8 "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" -o '"$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS-utf"'
```

The reference and samples i stumbled upon couldn't help me... well, maybe a little. Before it used to spit out empty file *chunks*. :)

Any ideas of where i should look?

---

### Post by po0f on 2007-02-24
Simon-v,

Maybe try using NAUTILUS_SCRIPT_SELECTED_URIS?  I don't have any experience writing Nautilus scripts, but all the scripts I *have* glanced through used this and not NAUTILUS_SCRIPT_SELECTED_FILE_PATHS (I haven't even seen it in an example script).

If you do end up getting this to work, could you link to  the reference/tutorial you used?

---

### Post by Simon-v on 2007-02-24
po0f,

I have tested this version, and it doesn't quite do it. A simple test script found around the forums shows that NAUTILUS_SCRIPT_SELECTED_FILE_PATHS outputs the path in the "/home/dir/file.ext" format, whereas NAUTILUS_SCRIPT_SELECTED_FILE_URIS outputs "file:///hime/dir/file.ext" - something that can't be used as output path, it seems; in essence, NAUTILUS_SCRIPT_SELECTED_FILE_PATHS is a perfectly usable variable to be used as input for a bash script, as it makes the output file at least be in the same directory as the input file, though still empty.

However, i noticed something puzzling. The output file seems to have a non-printable character in the end; and it seems to be a "new line" indicator! This would explain everything, because if Nautilus feeds iconv the name with the control character, then *of course* the output file would be empty, as such a file doesn't exist...

Now, for the real question: what can be used in place of Nautilus' script variable, that will return the full path and filename? I checked some references, but i don't remember seeing any bash variables with the needed description...

---

### Post by gradedcheese on 2007-02-24
> 
Now, for the real question: what can be used in place of Nautilus' script variable, that will return the full path and filename? I checked some references, but i don't remember seeing any bash variables with the needed description...

There's a variable for the base path, and then the file name is passed as $1 through $n, so if you put quotes around $@ (to protect file name with spaces in them) you can do, as an example:

```

for FILENAME in "$@"; do
  echo $FILENAME >> some_log_file
done

```

to see each selected file name

---

### Post by Simon-v on 2007-02-24
Okay, i played with it a little more.
So far i've managed to make the script convert the file(s) *only* if the source file is in the home folder; the output is to the home folder as well. Looks like it's where the script starts executing... Not exactly what i need, but it might do, if nothing better will occur.
Searching again, i couldn't find mentions of the variable responsible for returning the selected file's path; could that be because the console doesn't need such a thing? This, of course, makes the script fail to do what it is intended to - recode any selected files in any directory and place the output files into the same directory.

The only variable that remotely does that is the $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS, which is newline-delimited, seeing from the description, and that means it is not useful for any string operations, such as "for... in... ; do".

There is also $NAUTILUS_SCRIPT_CURRENT_URI, but it returns the path in "file:///home/dir/" format. I don't think it will do any good without converting it to "/home/dir/" format, cutting off the "file://"...

A workaround would be make the script navigate to the current directory and execute there, but a path must be fed to the script anyway.

Puzzling.

---

### Post by po0f on 2007-02-24
Simon-v,

Will [this](http://www.grumz.net/?q=node/47) help you at all?  It shows a bunch of parameters that you can use with Nautilus scripts.

---

### Post by gradedcheese on 2007-02-24
Nautilus does start your script where the user right-clicked... your script can use pwd to grab the path ;)

```

MY_PATH=`pwd`

```

---

### Post by Simon-v on 2007-02-25
Thank you for the replys and hints. It helped a great deal. Currently, i managed to make the script reliably do what it is intended for. I used the workaround i originally had in mind to achieve this: performing a string operation. The code (which looks overly complicated even for my tastes ^^ ) is:

```
for FILENAME in "$@"
do
iconv -f windows-1251 -t utf-8 "${NAUTILUS_SCRIPT_CURRENT_URI##file://}/$FILENAME" -o "${NAUTILUS_SCRIPT_CURRENT_URI##file://}/$FILENAME-utf"
done
```
( **${variable##pattern}** trims the longest match from the beginning.)
The string operations reference was [here]("http://linuxgazette.net/issue18/bash.html").

As for your suggestion, **gradedcheese**, at first glance, **pwd** doesn't seem to work as reliably as the workaround; i think i'm missing something. I'll play with it some more to figure out when and why does it return what. :)

Many thanks, and good day!

EDIT: I have found a nice piece of code on g-scripts.sourceforge.net that cuts the NAUTILUS_SCRIPT_CURRENT_URI and rids of %20 that might be there. I also added two lines to make the script "replace" the original file and create a backup. It almost approaches "professional" quality by now... :)
```
mypath="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"
for filename in "$@"
do
# Convert
iconv -f windows-1251 -t utf-8 "$mypath/$filename" -o "$mypath/$filename-new"
# Create backup
mv "$mypath/$filename" "$mypath/$filename~"
mv "$mypath/$filename-new" "$mypath/$filename"
done
```

EDIT 2: I studied the syntax and found that **pwd** works as a reliable argument in variable setting only if the following format is used: ```
variable="`pwd`"
```
So, as of now, my script has reached the elegance i originally looked for.
```
# Get current path
mypath="`pwd`"

for filename in "$@"
do
# Convert. Modify arguments to handle different encodings
iconv -f windows-1251 -t utf-8 "$mypath/$filename" -o "$mypath/$filename-new"
# Create backup
mv "$mypath/$filename" "$mypath/$filename~"
mv "$mypath/$filename-new" "$mypath/$filename"
done
```

Thank you again for the assistance!

---

