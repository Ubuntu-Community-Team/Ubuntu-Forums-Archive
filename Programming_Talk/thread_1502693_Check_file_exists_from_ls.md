---
title: "Check file exists from ls ?"
date: 2010-06-05
forum: Programming Talk
---

### Post by Dave_Connor on 2010-06-05
Well to explain is I am working on a program in BASH to take an input from read and convert through smv_encode for GoGear mp3 player with the same name. I already have this done with count the number of characters and using cut to take off the file extension and replace with ".smv" for the output file. The only issue I am running into when it displays the files I would like for it to check which files have been converted and which have not. I know about using ls as variables but having trouble with this part. 

Here is the code for my program. 
```

#!/bin/bash

function check_file() {

	LIST=$(ls -1 | grep mp4 | sort | wc -l);
	FILE="mp4"
	LIST_2=$(ls -1 | grep flv | sort | wc -l);
	
	if [ $LIST == 0 ]
	then
		LIST=$(ls -1 | grep flv | sort | wc -l);
		FILE="flv";
	fi

	# quit if both list entries return fase
	if [ $LIST == 0 ] && [ $LIST_2 == 0 ]
	then
		echo "0 items found, leaving script";
		exit;
	fi

	# list number of files
	echo "Listing files: $LIST";
	echo "";

	#display files
	ls -1 | grep $FILE;	
#	echo $1;
#	exit;
	
	# ask for user input by read -p
	echo "";
	read -p "Enter File Name: ";

	# define $FULL_NAME and check if file exists
	FULL_NAME=$REPLY;
	if [ -a $FULL_NAME ]
	then
		echo "";
	else
		echo "$FULL_NAME does not exists, quiting script";
		exit;
	fi	

	# count character length in user input
	USER=$(echo "$REPLY" | wc -m);

	# subtract 4 for file extension and check for left over period in file name;
	SUB=$(($USER - 4));
	FILE_NAME=$(echo $FULL_NAME | cut -b-$SUB);
	SEARCH_PER=$(echo $FILE_NAME | grep "." | wc -l);

	# look for period on end of file
	if [ $SEARCH_PER == 1 ]
	then
	        SUB=$(($USER - 5));
        	FILE_NAME=$(echo $FULL_NAME | cut -b-$SUB);
	fi

	if [ $SEARCH_PER == 0 ]
	then
	        SUB=$(($USER - 4));
        	FILE_NAME=$(echo $FULL_NAME | cut -b-$SUB);
	fi

	# define file types
	FILE_TYPE_1=$(echo "$FILE_NAME.mp4");
	FILE_TYPE_2=$(echo "$FILE_NAME.avi");
	FILE_TYPE_3=$(echo "$FILE_NAME.flv");
	OUTPUT=$FILE_NAME.smv;

	if [ -a $OUTPUT ]
	then
	        echo "$OUTPUT has already been converted";
		echo "";
		exit;
	fi
}


# run defined variable
check_file; 

echo "Using: $FILE_NAME";

#if [ -a $OUTPUT ] 
#then
#	echo "$OUTPUT file exists quiting script";
#	exit;
#fi

if [ -a $FILE_TYPE_1 ]
then
	smv_encode -q 84 $FILE_TYPE_1 $OUTPUT
fi

if [ -a $FILE_TYPE_2 ]
then
	smv_encode -q 84 $FILE_TYPE_2 $OUTPUT
fi

if [ -a $FILE_TYPE_3 ]
then
	smv_encode -q 84 $FILE_TYPE_3 $OUTPUT
fi

read -p "Do you wish to remove original file '$FULL_NAME' ? y/n: ";
ANS=$REPLY;

if [ $ANS == 'y' ]
then
	echo "Removing '$FULL_NAME'";
	rm $FULL_NAME;
fi

if [ $ANS == 'n' ]
then
	echo "Quiting Script";
fi

#commented out for already in function file_check;

#done

#FULL_NAME=$REPLY;
#USER=$(echo "$REPLY" | wc -m);

#SUB=$(($USER - 4));
#FILE_NAME=$(echo $FULL_NAME | cut -b-$SUB);
#SEARCH_PER=$(echo $FILE_NAME | grep "." | wc -l);

## look for period on end of file
#if [ $SEARCH_PER == 1 ]
#then
#	SUB=$(($USER - 5));
#	FILE_NAME=$(echo $FULL_NAME | cut -b-$SUB);
#fi

#if [ $SEARCH_PER == 0 ]
#then
#	SUB=$(($USER - 4));
#	FILE_NAME=$(echo $FULL_NAME | cut -b-$SUB);
#fi

#exit;

# 
#FILE_TYPE_1=$(echo "$FILE_NAME.mp4");
#FILE_TYPE_2=$(echo "$FILE_NAME.avi");
#FILE_TYPE_3=$(echo "$FILE_NAME.flv");
#OUTPUT=$FILE_NAME.smv;

```

---

### Post by soltanis on 2010-06-05
You don't have to us ls to check if a file exists. You can use the -e parameter to /usr/bin/[ like this

```

if [ -e "$FILE" ]; then echo ok; fi

```

---

### Post by Dave_Connor on 2010-06-06
Thanks, but also I was wondering how to have ls into array to be able to list out files and see what have already been converted and what haven't been is what I am looking for. Any tips here ?

---

### Post by BoneKracker on 2010-06-06
The 'find' command might be very useful to you here, and greatly simplify your script.

'find' can isolate files based on complicated criteria (extensions are simple to handle), and then perform an action on the files that have been found (any operation that you can code).

Changing the extensions of files is easy using the 'rename' command).

You can use the find command to select files to be renamed, and plug a rename command into the find statement where the action goes).

The 'find' command outputs each file as a discrete word (not just one big string).  In other words, its output is like that of 'xargs'.  So, it should be easy to populate an array from find's output, assuming you actually need to do that.
something vaguely like:
```

i=0
for file in $(find blah blah blah); do
    somearray[i++]=$file
done
```

I say all this without really being able to tell what you're trying to do, and without having thoroughly reviewed your script.

---

