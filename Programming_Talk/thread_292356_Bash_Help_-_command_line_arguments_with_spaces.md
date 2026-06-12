---
title: "Bash Help - command line arguments with spaces"
date: 2006-11-03
forum: Programming Talk
---

### Post by IAmNotPhillip on 2006-11-03
Hi. I've been writing a simple script that will convert movie files into a format that will play on my portable media player. I got the converting down, but I'm trying to get the script to recognize file names with spaces in them.

```
#!/bin/bash

mkdir converted

while [ "$1" != "" ]; do
	
	LENGTH=$((${#1} - 4))
	NAME=${1:0:LENGTH}

	# For testing purposes only
	zenity --info --text=$NAME
	
	mencoder ...
	rm divx2pass.log
	
	shift
	
done
```

Currently, it correctly recognizes the number of file names I pass it (with or without spaces) but when it gets to the zenity output, it thinks the name is only up to the first space, which of course screws up the rest of the script.

Any help would be appreciated. :)

---

### Post by Blacktalon on 2006-11-03
Hi, Im not an expert at this or know much about it, my thing is mostly java, and some ruby, php, and you get the picture, but anyways it looks like it might be getting caught at the :

while [ "$1" != [COLOR="Blue"]"" [/COLOR]]; do

Now let me make sure I am getting this right, while $1 is not empty  do ...., if I got this right in my head then even though you don't have a space in "" -> " " it might be still reading it as if you come to a space, perhaps if you tried while ["$1" != "\n"] do ...., this way it will go to the end of the line before it stops.  

I am not sure if that will work it might be a sloppy and bad way to code, but it is a thought.

good luck, and I hope this helps some
~BT

---

### Post by Engnome on 2006-11-03
Im not sure about bash but in some languages you cant compare strings with == or != because then it will try and see if they are the same object. In perl for instance you use eq  (if($a eq ""){doSomething;})

---

### Post by Peepsalot on 2006-11-03
well, i don't know much about bash scripting, but can't you just use double quotes around your file names when you are invoking your script?

---

### Post by skymt on 2006-11-03
```
#!/bin/bash

mkdir converted

if (( $# < 1 )); then
	print "Error: no arguments."
	exit
fi

for NAME in $@; do
	
	LENGTH=$((${#NAME} - 4))
	NAME=${NAME:0:LENGTH}

	# For testing purposes only
	zenity --info --text="$NAME"
	
	mencoder ...
	rm divx2pass.log
	
done
```

Here's what I changed:

* It now prints an error message if there are no arguments. $# contains the number of arguments the script was given.

* It uses "for x in y" loop syntax, instead of that rather inelegant while loop. It also removed the need to shift at the end.

* I added quotes around $NAME. Adding quotes escapes any spaces in the string.

---

### Post by IAmNotPhillip on 2006-11-03
Thanks guys. The solution basically involved me having to put some simple quotations around a few places (namely within my mencoder command -- stupid me was just editing the zenity command which, of course, didn't change where it actually tries to convert) which still confuses me. If it was any other language (like java) then when I System.out.println( string ); it will print the whole string. Not just up to the first space. But whatever. At least it "works" now.


Now that that ordeal is over, do any of you know a better solution to show the progress (via a GUI) than with zenity? Zenity technically works, but it doesn't really show the progress, and the cancel button neglects to actually cancel the conversion. Not to mention it forces mencoder to split CPU time with it.

And a final question, does anyone know a command to check a movie file for multi audio tracks or subtitles? That way I can present the user (me) with a drop down menu choice from which one to include in the final conversion.

---

