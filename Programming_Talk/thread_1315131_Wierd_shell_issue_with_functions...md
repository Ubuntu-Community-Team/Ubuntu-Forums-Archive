---
title: "Wierd shell issue with functions.."
date: 2009-11-05
forum: Programming Talk
---

### Post by rekahsoft on 2009-11-05
Hi all, i am writing a script to make it easier for me to encrypt a file from terminal...basically the script takes care of removing the old files when needed and is used by simply: ./crypt [-e|-d] filename.. But the issue i'm having is when i trun (the now only skeleton of my script), i get thye following error: "[: 78: missing ]"..here is the script for reference. Thanks for your help :)

```
#!/bin/sh

#########################################################
# Author: Collin J Doering <rekahsoft>                  #
# Date: Nov 4, 2009                                     #
# Description:                                          #
#########################################################

#############
# Variables #
#############

encrypt=0
decrypt=0
keep=0
file=
gpgPATH=/usr/bin/gpg

#############
# Functions #
#############

completeTasks() {
    if [ "$encrypt" = 1 && "$decrypt" = 1 ]; then
	echo "Error! cannot use both encrypt and decrypt flags!"
	exit 1
    elif [ "$encrypt" = 1 ]; then
	echo "Encrypting..."
    elif [ "$decrypt" = 1 ]; then
	echo "Decrypting..."
    else
	echo "No apropriate options selected!"
	usage
	exit 1
    fi
}

usage() {
    echo "Usage is: crypt [options..] [-e|--encrypt|-d|--decrypt] filename"
    echo "Options:"
    echo "     --keep: Keep uneeded files (UNSECURE!)"
    echo "     --gpg-path path: specify a special path for gpg"
    echo "Enjoy!"
}

while [ "$1" != "" ]; do
    case $1 in
	-e | --encrypt )
	    encrypt=1
	    shift
	    file="$1"
	    break
	    ;;
	-d | --decrypt )
	    decrypt=1
	    shift
	    file="$1"
	    break
      	    ;;
	--gpg-path )
	    shift
	    gpgPATH="$1"
	    break
	    ;;
	--keep )
	    keep=1
	    break
	    ;;
	* )
	    echo "Error! Unknown usage!"
	    usage
	    exit 1
	    ;;
   esac
   shift
done

completeTasks
echo "Done..."
exit 0

```

---

### Post by eightmillion on 2009-11-05
This syntax is wrong:
```
[ "$encrypt" = 1 && "$decrypt" = 1 ]
```
It should be:
```
[ "$encrypt" = 1 ] && [ "$decrypt" = 1 ]
```

---

### Post by rekahsoft on 2009-11-07
Thanks! :) i ended up writing it using the test command and getting it to work..but good to know :)

---

