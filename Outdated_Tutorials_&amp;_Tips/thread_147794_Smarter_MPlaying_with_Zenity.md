---
title: "Smarter MPlaying with Zenity"
date: 2006-03-20
forum: Outdated Tutorials &amp; Tips
---

### Post by nixclusive on 2006-03-20
The attached tarball contains a simple script that invokes the 'zenity'
dialog manager to feed mplayer with the input file string. Download the
file and extract using the following command:

$ tar xvf smart.tar

Make the script executable:

$ chmod a+x ./mpl.sh

Execute it:

$ ./mpl.sh


It is smart enough to kill any current instance of mplayer so that you
don't end up having parallel files playing if you invoked the script
multiple times. Make a new custom launcher in the panel for quick
access. Also check out the included - 'Screenshot.png'.

BUGS:
1. Will kill ALL INSTANCES of mplayer before launching a new one.
2. Will kill ANYTHING that's called 'mplayer'!!! - Caution here.

DEPENDENCIES:
1. Zenity+
2. mplayer+

TODO:
1. Check for instances for mplayer directly associated with mpl.sh and
kill accordingly.
2. There's currently no way to stop a currently running instance of
mpl.sh!!! -- without the terminal of course.
3. HISTORY MAN HISTORY!!! I hate to navigate all the way over...
4. Support for multiple files.

```
#!/bin/bash
#---mpl.sh---
FILE=`zenity --title "Open file" --file-selection`

echo $FILE

if test "$FILE" != "" ; then
        STAT=`ps -e | grep -c mplayer`

        if test "$STAT" -gt "0" ; then
                killall mplayer
        fi
fi

mplayer "$FILE"
```

Screenshot:
[http://i5.photobucket.com/albums/y165/nixclusive0/Screenshot.png](http://i5.photobucket.com/albums/y165/nixclusive0/Screenshot.png)

Download link:
[http://rapidshare.de/files/16026862/smart.tar.html](http://rapidshare.de/files/16026862/smart.tar.html)

Click the 'free' button in the bottom of the page and enter the code in the displayed image to download.

---

### Post by nixclusive on 2006-03-22
Alright got the history working...makes a file in /tmp:

```
#!/bin/bash
#---mpl.sh---
#Makes a tmp file in /tmp

LAST=`cat /tmp/last_file`

FILE=`zenity --title "Open file" --filename="$LAST" --file-selection`

echo $FILE

if test "$FILE" != "" ; then
        echo "$FILE" > /tmp/last_file
        STAT=`ps -e | grep -c mplayer`

        if test "$STAT" -gt "0" ; then
                killall mplayer
        fi
fi

mplayer -noconsolecontrols -really-quiet "$FILE"
```

;)

---

### Post by SqRt7744 on 2006-03-23
just a suggestion, but instead of using rapidshare, why don't you just attach the file to your post?

---

### Post by SqRt7744 on 2006-03-23
It's a nice script, but I changed all mplayer to gmplayer, I think most people like the controls!

---

### Post by nixclusive on 2006-03-23
We can use 'sed' for multiple file support:

```
echo `zenity --title "Open file" --filename="$LAST" --file-selection --multiple` > /tmp/multi_name

FEED=`sed -e 's/|/ /g' < /tmp/multi_name`

rm -f /tmp/multi_name

echo -e "\n$FEED\n"
```

But bash seems to conk out when sed is told to replace special chars and spaces in back quotes. How do you fix that?

---

### Post by SqRt7744 on 2006-03-24
My (finished) script looks like this:  it supports multi-files+history, and uses gmplayer instead of mplayer.  I don't know what will happen if the filename is funny, but it's good enough for me right now!  The "LAST=" line selects first filename if /tmp/last_file is a list.

Actually I have two versions: this one, and one that is identical except it uses vlc instead of mplayer.  It is nice to have both because sometimes a certain filetype will play better in the one player than in the other. (to make the vlc version just make a new file called vlc.sh and change each instance of the word "gmplayer" in the code below to "vlc"

```

#!/bin/bash
LAST=`cat /tmp/last_file|cut -d' ' -f1`

FEED=`zenity --title "Open file" --filename="$LAST" --file-selection --multiple|sed -e 's/|/ /g'`

if test "$FEED" != "" ; then
        echo "$FEED" > /tmp/last_file
        STAT=`ps -e | grep -c gmplayer`

        if test "$STAT" -gt "0" ; then
                killall gmplayer
        fi
fi

gmplayer $FEED

```

---

### Post by Mr Frosti on 2006-03-25
The concept behind this script is heading a more user-friendly direction. I would like to see G/Mplayer behave more like Winamp in the following sense:

1) Only one instance (closing after finishing each file is a pain)
2) Options for "playlist" and queuing of files
3) Integration with [Nautilus actions]("http://www.grumz.net/?q=taxonomy/term/2/9"), for relevant contextual menu options
4) Recursive directory search for playable content

There might be some movement to do this somewhere, but I haven't come across it, with the exception of this thread. Good start though...

---

