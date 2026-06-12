---
title: "Bash: while loop error, can't figure it out"
date: 2009-03-19
forum: Programming Talk
---

### Post by fela on 2009-03-19
Hi
I'm making a script to convert all .icns files in the current directory to png, using the icns2png program found in the icnsutils package. The thing is, no matter what I try I always get the error: ```
line 75: syntax error near unexpected token `done'
``` When I try to run it. I've almost given up and the forums are my last hope! Here is the code of the whole script (roughly 100 lines):

```
#!/bin/bash

# Clear the screen so it's easier to read.
clear

# Set some variables
DEFAULT_OUTPUT_DIR="."
OUTPUT_DIR="."
ANOTHER_DIR="i"
TRASH=old_icns

# Command line options
case $1 in
	-i)
	INTERACTIVE="true"
	;;
	*)
	INTERACTIVE="false"
	;;
esac

# Print a message telling what the script will do, if the user has specified
# Quit early if the user chooses to
if [ $INTERACTIVE == "true" ]; then
	echo "This script will convert all OSX icons (*.icns) to png format in the current directory. It will move all the outputted png files in a folder called 'png'."
	echo "Continue? (y|n)"
	read USER_OPTION
	case $USER_OPTION in
		n) exit 0
		;;
		y)
		;;
		*) echo "I do not understand your language."
		exit 1
		;;
	esac
fi

# Ask for the directory name if the user has specified interactive mode
if [ $INTERACTIVE == "true" ]; then
	echo "Please specify a directory to place the png files in. The
character '.' means the current directory. If it already exists
you will be asked to specify another one. The default is '$OUTPUTDIR'."
	read OUTPUT_DIR
	case $OUTPUT_DIR in
		"") OUTPUT_DIR=$DEFAULT_OUTPUT_DIR ;;
		*) ;;
	esac
fi

# This is a loop to make sure no files/directories get overwritten.
if [ -d $OUTPUT_DIR ]; then # -d means directory exists
	if [ $OUTPUT_DIR != "." ]; then
		DIR_EXISTS="true"
	fi
fi

while [ $DIR_EXISTS == "true" ]; do
	if [ $INTERACTIVE == "false" ]; then # You do not want to hear the same message twice.
		echo "There is already a directory called '$OUTPUT_DIR' in the current directory.
Please type the name of a directory that you would like to use. If it already exists
you will be asked to specify another one. The character '.' means the current directory."
		read OUTPUT_DIR # change the output dir to the users wishes
	else if [ $INTERACTIVE == "true" ]; then
		echo "The directory you have specified, '$OUTPUT_DIR', already exists.
Please specify another one."
		read OUTPUT_DIR
	fi

	if [ ! -d $OUTPUT_DIR ]; then # the ! makes -* mean the opposite, i.e. directory doesn't exist.
		DIR_EXISTS="false"
	else if [ $OUTPUT_DIR == "." ]; then
		DIR_EXISTS="false"
	fi
done

mkdir $OUTPUT_DIR # make the new output directory

for i in *.icns
do
	mkdir "$OUTPUT_DIR/$ANOTHER_DIR"
	icns2png -x -o "$OUTPUT_DIR/$ANOTHER_DIR" "$i"
done

if [ $INTERACTIVE == "true" ]; then
	echo "Delete old icns files? Permanently? (y|n|p)"
	read DELETE_OR_NOT
	case $DELETE_OR_NOT in
	y|yes) if [ ! -d $TRASH ]; then
			mkdir $TRASH
		   fi
		   mv *icns "$TRASH/"
		   echo "The icns files have been moved to the trash folder, $TRASH." ;;
	n|no) exit 0 ;;
	p|permanently) echo "Sure you want to delete all the icns files PERMANENTLY? (y|n)"
				   read SURE
				   case $SURE in
					y|yes) rm *icns ;;
					n|no) exit 0 ;;
					*) exit 0 ;;
				   esac ;;
	*) exit 0 ;;
	esac
else
mv *icns "$TRASH/"
echo "Your old icns files have been moved to $TRASH"
fi
```

The big while loop to make sure that no data is overwritten is the stumbling block.

Many thanks in advance...

-Fela :)

---

### Post by jimi_hendrix on 2009-03-19
this is probably not the answer but if you use if [ ] dont you need to quote your variables

---

### Post by fela on 2009-03-19
> **jimi_hendrix said:**
> this is probably not the answer but if you use if [ ] dont you need to quote your variables

Thanks for the reply. Well I tried that and it didn't seem to make any difference, I think you can have them quoted or not depending on what you like. The funny thing is, I could have sworn that that exact while loop that's causing me errors has worked in the past! Strange, huh? Maybe something else in the script is confusing it.

---

### Post by geirha on 2009-03-19
You must use *elif* and not *else if*. 

Consider this. I've color coded the *if*s, *else*s and *fi*s that belongs to each other. As you can see, *else if*, starts a new *if*, which is closed by the first occuring *fi*, but the green *if* never gets closed. That's why bash is surprised at finding a *done* when it hasn't closed all the *if*s inside the *while* yet.

```
[COLOR="Green"]if[/COLOR] [ "a" = "b" ]; [COLOR="Green"]then[/COLOR]
  echo something
[COLOR="Green"]else[/COLOR] [COLOR="Blue"]if[/COLOR] [ "a" = "a" ]; [COLOR="Blue"]then[/COLOR]
  echo something else
[COLOR="Blue"]fi[/COLOR]

```

The proper way to do it is thus:
```
[COLOR="Green"]if[/COLOR] [ "a" = "b" ]; [COLOR="Green"]then[/COLOR]
  echo something
[COLOR="Green"]elif[/COLOR] [ "a" = "a" ]; [COLOR="Green"]then[/COLOR]
  echo something else
[COLOR="Green"]else[/COLOR]
  echo when all else fails
[COLOR="Green"]fi[/COLOR]

```

Also, it's good practice to quote variables. Especially for variables containing paths.

---

### Post by fela on 2009-03-19
@geirha: thanks so much! I didn't know it was as simple as that, I was starting to tear my hair out over such a small issue! BTW I always quote variables if they contain paths (otherwise they often don't work as I learned the hard way). Maybe I'll start quoting all my variables then.

---

### Post by viperskunk on 2009-07-27
This script seems the answer to my woes!!

Would you make this available for people like us, who don't know squat about bash scripts, but would love to have a handy script to convert icns to png like this?

Many thanks.

---

