---
title: "Copy floppy script; Expert advise requested"
date: 2007-09-22
forum: Programming Talk
---

### Post by altonbr on 2007-09-22
I posted this thread regarding a computer I was working on not being able to read a floppy: [http://ubuntuforums.org/showthread.php?t=550371](http://ubuntuforums.org/showthread.php?t=550371). It was able to open Smart Boot Manager on a reboot and mount floppies in root, so if you have any advice on what preferences are blocking the floppy from being used, that'd be much appreciated.

Since the floppy was able to be read by root, I made a quick script called 'floppy.sh' and ran it as:```
$ ./floppy.sh blue1
```

This enabled me to name the floppy disks as they were labelled and copy their contents to the user's document directory under the same name.

Here's the script:

```
#/bin/bash

# Mount Floppy
mount /media/floppy0/
echo " -- Mounted the \"$1\" floppy..."

# Make directory
mkdir /home/lillian/documents/$1
echo " -- Created Directory \"/home/lillian/documents/$1\"..."

# Copy contents of the floppy
cp -p  /media/floppy0/* /home/lillian/documents/$1
echo " -- Copied contents of the \"$1\" floppy..."

# Change permissions to user lillian
chown lillian:lillian /home/lillian/documents/$1/*
echo " -- Changed owner of \"/home/lillian/documents/$1\" to lillian..."

# Unmount floppy
umount /media/floppy0
echo " -- Unmounted the \"$1\" floppy..."
```

Pretty simple eh? With no error detection though.

I know this isn't needed for such a simple script, but how could I detect the output of each line and halt the script if there was an error? What about making variables for those directories... would that make sense so it's not hard coded? What about writing " -- Coping floppy \"$1\"..." with periods being added every second so the user knows what is currently being worked on?

Would I begin the file with:```
HOMEDIR=/home/lillian/documents/
```

And then be able to repeat 'HOMEDIR' throughout the whole script?

Thanks for any tips!

PS: Yes, I've been told "[DON'T COPY THAT FLOPPY!]("http://www.youtube.com/watch?v=-Xfqkdh5Js4")"

---

### Post by altonbr on 2007-09-23
How about this:

```
#/bin/bash

# USAGE: ./copyfloppy2.sh <floppy_name> <folder> <user>
# EXAMPLE: ./copyfloppy2.sh blue1 /home/lillian/documents/ lillian

if [ $# -ne 3 ]
	then
		echo "USAGE: ./copyfloppy2.sh <floppy_name> <folder> <user>"
		echo " ** Exiting ..."
		exit
	else
		# Mount Floppy
		mount /media/floppy0/ &&
		echo " -- Mounted the \"$1\" floppy..."

		# Make directory
		if [ $? == 0 ]
			then
				# mkdir /home/lillian/documents/blue1
				mkdir $2$1 &&
				echo " -- Created Directory \"$2$1\"..."
			else
				echo " ** Mounting the \"$1\" floppy failed!"
				echo " ** Exiting ..."
				exit $?
		fi

		# Copy contents of the floppy
		if [ $? == 0 ]
			then
				# cp -p  /media/floppy0/* /home/lillian/documents/blue1 &&
				cp -p  /media/floppy0/* $2$1 &&
				echo " -- Copied contents of the \"$1\" floppy..."
			else
				echo " ** Creating Directory \"$2$1\" failed!"
				echo " ** Exiting ..."
				exit $?
		fi



		# Change permissions to user lillian
		if [ $? == 0 ]
			then
				# chown lillian:lillian /home/lillian/documents/blue1/* &&
				chown $3:$3 $2$1/* &&
				echo " -- Changed owner of \"$2$1\" to lillian..."
			else
				echo " ** Copying contents of the \"$1\" floppy failed!"
				echo " ** Exiting ..."
				exit $?
		fi


		# Unmount floppy
		if [ $? == 0 ]
			then
				umount /media/floppy0
				echo " -- Unmounted the \"$1\" floppy..."
			else
				echo " ** Changing owner of \"$2$1\" to lillian failed!"
				echo " ** Exiting ..."
				exit $?
		fi
fi
```

---

