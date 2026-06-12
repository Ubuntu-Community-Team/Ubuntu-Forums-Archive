---
title: "Shell Script - while-read loop doesn't work."
date: 2009-05-22
forum: Programming Talk
---

### Post by kaibob on 2009-05-22
The fourth line of the following script (echo "no file") is never executed. Apparently, this is because the script aborts if there are no files to read. 

```
#!/bin/bash
find /target/directory -name "nomatchingfiles" -type f | while read FILE ; do
	if [ "$FILE" = "" ] ; then
		echo "no file"
	else
		echo "$FILE"
	fi
done
```

An altenative that does work is:

```
#!/bin/bash

ALLFILES=$(find /target/directory -name "nomatchingfiles" -type f)

for FILE in "$ALLFILES" ; do
	if [ "$FILE" = "" ] ; then
		echo "no file"
	else
		echo "$FILE"
	fi
done
```

Is there some way to get the first script to work?

BTW, I'm curious about this simply to learn. This issue came up in relation to an actual script, which works fine with the approach contained in the second script. Thanks!

---

### Post by KyleBrandt on 2009-05-22
I see two problems with the command substitution method. The first is that if your file name has spaces the for loop would consider them multiple files instead of one.  With echo, that is probably okay... But if you were doing something more ( like rm $file) I would use the command execution capability of find within the command substitution instead of the for loop.  

Also, if there is error with find and it aborts, the file might be there, but since you didn't test find's exit status your script would think the file is not there.

---

### Post by Dill on 2009-05-22
To follow up on what Kyle said, if the file has spaces, you can resolve this by setting the Internal Field Separator variable to a newline, like so:

```
IFS=$'\n'
```

You can also test to see if a file exists with 

```
[ -f $FILE ]
```

And integrate it into a conditional like so...

```
if [ -f $FILE ]
then
    echo "$FILE"
else
    echo "no file!"
fi
```

I guess I'm not sure exactly what your code is trying to accomplish. Why would you need to print "no file" if a file doesn't exist? If you're trying to find files with a given name and then printing their names, why would you need to print "no file"? Why not just print the names of the files that met the given criterion?

Forgive me... lack of coffee in the morning makes me a bit dense : ).

Cheers,
Dill

---

### Post by KyleBrandt on 2009-05-22
Although, if people are really nasty, they can even put a newline in a file:

```
touch foo$'\n'
```

---

### Post by kaibob on 2009-05-22
@Kyle, Thanks for the response. I didn't but should have mentioned that my actual script contains the following to deal with files that contain spaces:

```
IFS=$'\n'
```

@Dill, I did try your suggestion and received the following message when find did not locate any matching files:  

> find: /target: No such file or directory. 

I didn't think it pertinent, but FWIW the actual script is:

```
#!/bin/bash

# Shell script to find files in predefined search locations. 

# Prompt for search location.
while true ; do
	read -p "Enter (h)ome (r)oot (u)ser (w)estern or (e)xit: " KEYPRESS
	case "$KEYPRESS" in
	  "h" ) SEARCHDIR=/home/bob/ ; break;;
	  "r" ) SEARCHDIR=/ ; break;;
	  "u" ) SEARCHDIR=$(ls -d /home/bob/*/) ; break;;
	  "w" ) SEARCHDIR=/media/WESTERN-EXT3/ ; break;;
	  "e" ) echo ; exit 0;;
	   *  ) echo -e "\nYou did not make a valid selection!\n";;
	esac
done

echo

# Prompt for search string.
while true ; do
	read -p "Enter search string or (e)xit: " SEARCHFILE
	if [ "$SEARCHFILE" = "e" ] ; then 
		echo
		exit 0
	elif [ "$SEARCHFILE" != "" ] ; then 
		break
	else
		echo -e "\nYou forgot a search string!\n"
	fi
done

# Set variable.
OLDFILEPATH=/none

# Find and output search results to screen.
find $SEARCHDIR -xdev -iname "*$SEARCHFILE*" -type f 2>/dev/null | \
sort -d | while read FILES ; do
	for FILE in "$FILES" ; do
		FILEPATH="${FILE%/*}"
		FILENAME="${FILE##*/}"
		if [ "$FILEPATH" != "$OLDFILEPATH" ] ; then
			echo -e "\n\033[1m${FILEPATH}/\033[0m"
		fi
		echo -e "$FILENAME"
		OLDFILEPATH="$FILEPATH"
	done
done

echo
```

---

### Post by Dill on 2009-05-22
Ah, OK. 

So a while loop has a "loop continue condition" that it tests each time the loop is executed (here, *read FILE*). As long as the loop continue condition is true, the body of the loop will execute. Then, the continue condition is tested again, and if it's true, the body of the loop executes, etc. etc... In your case, there's nothing to read, so the loop continue condition fails automatically and never executes.

The for loop operates in a similar way, but iterates through whatever data you've given it (in this case, "$ALLFILES"). And $ALLFILES actually doesn't reference any data -- by putting the quotation marks around $ALLFILES, you're *creating* data (in this case, and empty string) and iterating though that. Remove the quotation marks and you'll find that the for loop also doesn't execute, just like the while loop above.

I thought you might be able to test the exit status of find in this case, as well, but it doesn't prove helpful. Whether or not find finds anything, it still returns an exit code of 0, since find *completes* its search either way.

```
satherdy@lamp:~/trash$ find . -name "test" -type f
./test
satherdy@lamp:~/trash$ echo $?
0
satherdy@lamp:~/trash$ find . -name "gobbledygoop" -type f
satherdy@lamp:~/trash$ echo $?
0
satherdy@lamp:~/trash$
```

Perhaps someone who's more adept at using find can provide more useful exit code info or suggestions.

EDIT: I also had one more suggestion -- you should be able to cut down on your if-elif-else construct at the top of your script (where you read input to get the search directory) by using *case*, instead. 

```
case "$KEYPRESS" in
  "h" ) SEARCHDIR=/home/bob/;;
  "r" ) SEARCHDIR=/;;
  "u" ) SEARCHDIR=$(ls -d /home/bob/*/);;
  "w" ) SEARCHDIR=/media/WESTERN-EXT3/;;
  "e" ) exit 0;;
   # Otherwise, default to...
   *  ) echo -e "\nYou did not make a selection!\n";;
esac
```

You may have to do a little bit of playing around to get it perfect, but you can see how this cuts down quite a chunk of code and makes it easier to read

Cheers,
Dill

---

### Post by kaibob on 2009-05-22
Dill,

Thanks for the response. I think the first paragraph of your post summarizes the issue very accurately when you state:

> In your case, there's nothing to read, so the loop continue condition fails automatically and never executes.

I also tried various other approaches including exit status and setting the read variable before the while-read loop but none of them worked. 

Thanks for the suggested case statement. I plugged it into my script and after a few minor tweaks it worked great

Thanks again.

Kaibob

---

### Post by ghostdog74 on 2009-05-22
> **kaibob said:**
> 
```
#!/bin/bash
find /target/directory -name "nomatchingfiles" -type f | while read FILE ; do
	if [ "$FILE" = "" ] ; then
		echo "no file"
	else
		echo "$FILE"
	fi
done
```

i hope you are just giving a hypothetical example, otherwise, there's really no need to check whether the file exist or not. The find command will do it for you.

---

### Post by kaibob on 2009-05-22
> **ghostdog74 said:**
> i hope you are just giving a hypothetical example, otherwise, there's really no need to check whether the file exist or not. The find command will do it for you.
Yes, this is hypothetical only to demonstrate the issue.

---

### Post by ghostdog74 on 2009-05-22
> **kaibob said:**
> Yes, this is hypothetical only to demonstrate the issue.
well, if you want to test for null string , use -z
```

find ... | while read FILE
do
 if [ -z "$FILE" ] 
 ....
done

```

---

### Post by kaibob on 2009-05-22
> **ghostdog74 said:**
> well, if you want to test for null string , use -z
```

find ... | while read FILE
do
 if [ -z "$FILE" ] 
 ....
done

```
Ghostdog74, That doesn't work. For example, the following will not find a file, and my original expectation was that it would echo "file not found" to the screen. It doesn't. 

```
#!/bin/sh

find . -name "xxxxx" | while read FILE ; do
	if [ -z "$FILE" ] ; then
		echo "file not found"
	else
		echo "file found"
	fi
done
```

---

### Post by ghostdog74 on 2009-05-22
well, you could do it another way 
```

result=$(find ...... )
if [ ! -z "$result" ];then
  #do something with $result
fi

```

---

### Post by slavik on 2009-05-22
...

what is the purpose of this?

---

### Post by kaibob on 2009-05-22
> **ghostdog74 said:**
> well, you could do it another way 
```

result=$(find ...... )
if [ ! -z "$result" ];then
  #do something with $result
fi

```

That's the way I finally got it to work. It just irritated me that I couldn't get it to work the other way. Thanks for the response.

---

