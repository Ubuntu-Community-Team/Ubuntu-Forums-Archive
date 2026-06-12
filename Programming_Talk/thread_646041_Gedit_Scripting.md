---
title: "Gedit Scripting"
date: 2007-12-20
forum: Programming Talk
---

### Post by lwylie on 2007-12-20
Hi everyone,

     I'm trying to write a very basic script that takes a .tex file, compiles it with latex, and then views it in evince using Gedit's External Tools plugin.

I am able to return the current file using $GEDIT_CURRENT_DOCUMENT_PATH and am able to plug that into latex.  However, I can't get at the pdf file that is generated from latex.  Basically what I need to do is strip the last three characters from $GEDIT_CURRENT_DOCUMENT_PATH and add on "pdf" in their place.  What are some basic string manipulation function for /bin/sh?

Thanks!
~Luke

---

### Post by engla on 2007-12-20
We all do these kinds of scripts. I wrote mine a year ago, and it strips the extension in a really dumb way.. :)

This is my script for gedit. It uses the "rev" and "cut" commands (reverses input)

```
pdflatex "$GEDIT_CURRENT_DOCUMENT_PATH"
PDF="`echo $GEDIT_CURRENT_DOCUMENT_PATH | rev | cut --complement -c -4 | rev`.pdf"
echo "$PDF"
test -e "$PDF" && evince "$PDF" &

```

Note that there is a huge latex plugin for gedit too. I don't use it though.

---

### Post by engla on 2007-12-20
However, I also wrote these two scripts, I hope they can help some latex writers (these scripts are not for gedit)

They depend on the package "*inotify-tools*", since with inotify you can watch when a file changes. So this script watches a tex file and rebuilds it when it is changed on the disk.

~/bin/onchange
Helper script to run something when a file changes
```
#!/bin/sh
FILE="$1"
COMMAND="$2"

while inotifywait -e close_write "$FILE"; do
    sh -c "$COMMAND"
done

```
~/bin/textwatch
Script to watch a tex file. Run as it is. It shows a notification icon in the notification area to show that it is running. Clicking the notification simply terminates the watching script.

```
#!/bin/sh
FILE="$1"

if test -z $1
then
	FILE=`zenity --file-selection --filename=$HOME/Documents`
	echo $FILE
fi

DIR=`dirname "$FILE"`
FILE=`basename "$FILE"`
cd "$DIR"

TEX="$FILE"
PDF="`echo $FILE | rev | cut --complement -c -4 | rev`.pdf"

test ! -e "$FILE" && echo "No such file" && exit

~/bin/onchange "$TEX" "pdflatex -interaction nonstopmode $TEX; evince $PDF &" &
PID="$!"

zenity --notification --title "LaTeX running" --text "Watching $TEX"
kill $PID

```


I hope it works. It worked all fine and dandy last time I was writing reports, but I can't make sure since latex isn't even installed right now :)

---

### Post by lwylie on 2007-12-20
Sweet... thanks certainly works.

Thanks!
~Luke

---

