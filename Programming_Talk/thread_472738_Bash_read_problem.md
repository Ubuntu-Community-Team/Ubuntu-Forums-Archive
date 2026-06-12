---
title: "Bash read problem"
date: 2007-06-13
forum: Programming Talk
---

### Post by jwhite69 on 2007-06-13
I'm trying to write a bash script, but am having trouble with the read command.  When I run the program, I get this output:

********
:invalid option namee 8: shopt: nounset
Enter the table path:
filename
`: not a valid identifier: read: `IN_TABLE
Enter the directory to check:
`: not a valid identifier: read: `CK_DIR
compareArch.bash: line 34: syntax error: unexpected end of file
********

here is my code:
********
#!/bin/bash

shopt -s -o nounset
#
declare -rx SCRIPT=${0##*/}	# SCRIPT is the name of this script
declare IN_TABLE		# the input table that contains the filenames
declare -x CK_DIR		# directory to check for folders
declare TRASH			# trash value in the table "D"
declare CD_DIR			# directory name in the Archives
declare -x Q_DIR		# directory name in the  database
declare FIND_TMP		# temporary variable for output of find
#
printf "Enter the table path: \n"
read IN_TABLE
printf "Enter the directory to check: \n"
read CK_DIR
#
exec 3< "$IN_TABLE"
#
while read TRASH CD_DIR Q_DIR <&3 ; do
	FIND_TMP="find $CK_DIR -name -prune $Q_DIR"
	FIND_TMP="${FIND_TMP/'./'}"
	if ["$FIND_TMP" != "$Q_DIR"]
		printf "%s\t%s" "$CD_DIR" "$Q_DIR"
	fi
done
#
exit 0
**************

---

### Post by jwhite69 on 2007-06-13
I found the problem:

I am using gVim in Windows, and it was set to DOS formatting instead of UNIX formatting, which caused an error in bash (in Cygwin) because gVim set the newline to the carriage return "\r" instead of "\n".

---

