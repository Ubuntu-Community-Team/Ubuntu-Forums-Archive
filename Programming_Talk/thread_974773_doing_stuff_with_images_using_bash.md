---
title: "doing stuff with images using bash"
date: 2008-11-06
forum: Programming Talk
---

### Post by brcre on 2008-11-06
```
#!/bin/bash

program () {
     filetype="$1"
     newname="$2"
     if [ -e ~/bin/extension.sh ]; then
       ~/bin/extension.sh $filetype
     fi
             # Count the number of jpg files in the current dir.
             # This is used to determine if program will likely execute without errors.
             NUM_FILES=`ls *\.$filetype | wc -l`
     if test $NUM_FILES -ge 999; then
          echo "This program is intended for use on less than 1,000 files"
          echo "files will end up scrambled when ran on greater than 999 files"
          exit 1
     fi

     n=1
     for file in *\.$filetype; do
         sBaseName=$(basename $file $filetype)
                       # printf explained:
                       # %0 - add leading zeros.
                       # ${#NUM_FILES} - number of digits in NUM_FILES.
                       # i - argument is type integer.
                       # ${FILENAME} - append the filename to the string.              
         if test $n -le 9; then              
              NEW_FILE=`printf "$newname"_"00$n"."${filetype}"`
         elif test $n -le 99; then     
              NEW_FILE=`printf "$newname"_"0$n"."${filetype}"`
         else     
              NEW_FILE=`printf "$newname"_"$n"."${filetype}"`
         fi   
         if [ $file != $NEW_FILE ]; then  
           mv -i $file $NEW_FILE
         fi
         (( n++ ))
     done    
exit 0
}

                       
case $1 in
    --help)   echo;echo;echo "Usage: rename.sh filetype newname  i.e. rename.sh jpg My_Newname";echo;echo;echo
    ;;
    -h)   echo;echo;echo "Usage: rename.sh filetype newname  i.e. rename.sh jpg My_Newname";echo;echo;echo
    ;;
    *) program $1 $2
    ;;
esac    
```

---

### Post by brcre on 2008-11-06
```
#!/bin/bash

program () {
     filetype="$1"
     newsize="$2"
     if [ -e ~/bin/extension.sh ]; then
       ~/bin/extension.sh $filetype
     fi

   for i in `ls *.$filetype`; do 
      convert -resize $newsize -quality 80 $i ZSM_$i
   done
exit 0
}
# Check usage 
case $1 in
    --help)   echo;echo;echo "Usage: resize.sh filetype newsize  i.e. resize.sh jpg 640X480";echo;echo;echo
    ;;
    -h)   echo;echo;echo "Usage: resize.sh filetype newsize  i.e. resize.sh jpg 640X480";echo;echo;echo
    ;;
    *) program $1 $2
    ;;
esac

```

---

### Post by acreech on 2008-11-07
if 

> rename.sh JPG stupid 

returns

 > bash: rename.sh: command not found

then go in and make these edits

> gedit ~/.profile

Make sure the file includes the following. Then save/exit

> PATH=$PATH:$HOME/bin
export PATH

Then run the following commands

> hash -r ./.profile

echo $PATH


This should tell the computer where to find the personal programs in the ~/bin folder.

---

### Post by brcre on 2008-11-07
```
#!/bin/bash

#extension JPG jpg  -->Goes from upper case to lower case
#extension jpg JPG  -->Goes from lower case to upper case

program () {
     filetype="$1"
     if [ -e "temp_name" ]; then
        echo "";echo "";echo ""
        echo "This program uses the name temp_name please rename or remove this file before running this program"
        echo "";echo "";echo ""
        exit 1
     fi
     ls `ls -1 | grep -i $filetype` > /dev/null
     if [ "$?" -ne "0" ]; then
           echo "";echo "";echo ""
           echo "There aren't any files ending in that file type."
           echo "Please double check the file extensions you're trying to change"
           echo "";echo "";echo ""
           exit 1
     fi

     for file in `ls | grep -i $filetype | sed s/\ /\~/g`; do
         file=`echo $file | sed s/\~/\ /g`
         if [ `echo $file | awk -F. '{print $2}'` != $filetype ]; then
           sBaseName=`basename "$file" | awk -F. '{print $1}' | sed s/\ /_/g`
                NEW_FILE=`printf "$sBaseName"."${filetype}"`
           mv -f "$file" temp_name
           mv -i temp_name $NEW_FILE
         fi
     done    
exit 0
}

                       
case $1 in
    --help)   echo;echo;echo "Usage: extension.sh filetype i.e. extension.sh JPG changes lower case jpg to upper case JPG";echo;echo;echo
    ;;
    -h)   echo;echo;echo "Usage: extension.sh filetype i.e. extension.sh JPG changes lower case jpg to upper case JPG";echo;echo;echo
    ;;
    *) program $1
    ;;
esac    

```

---

### Post by slavik on 2008-11-07
is there a reason why there are TWO separate threads in this ONE thread?

---

### Post by brcre on 2008-11-13
```
#!/bin/bash 
# name of the script 'search'

# a little bit of help in case of misuse 
if [ $# -lt 2 ] 
    then 
       echo "usage: l /directory pattern" 
       echo "example: l /etc config" 
       return 1
       exit 
fi

# $DIR is the first argument, the path to the directory 
DIR=$1

# $SEARCH is what you are looking for, and it's the second argument 
SEARCH=$2

# $RED sets the text to inverted red, changing the capabilities of the terminal via terminfo parameters 
# setaf 1 = red, smso = inverted 
RED=`tput setaf 1; tput smso`

#  $NORMAL returns text to normal attributes 
NORMAL=`tput sgr0`

# 
ls -1 $DIR | sed s/"$SEARCH"/"$RED$SEARCH$NORMAL"/ | grep $SEARCH | sort -u

```

---

### Post by acreech on 2009-01-06
Use this to rename and scramble up images. It is programmed in a loop to re-run 500 times. 


```
#!/bin/bash

program () {
     filetype="$1"
     newname="$2"
     if [ -e ~/bin/extension.sh ]; then
       ~/bin/extension.sh $filetype
     fi
             # Count the number of jpg files in the current dir.
             # This is used to determine if program will likely execute without errors.
             NUM_FILES=`ls *\.$filetype | wc -l`
     if test $NUM_FILES -ge 999; then
          echo "This program is intended for use on less than 1,000
files"
          echo "files will end up scrambled when ran on greater than 999
files"
          exit 1
     fi

     m=1
  while [ "$m" -lt 500 ];do
     echo "Run $m of 500"
     n=1
     for file in *\.$filetype; do
         sBaseName=$(basename $file $filetype)
              NEW_FILE=`printf "$newname$m"_"$n"."${filetype}"`
         if [ $file != $NEW_FILE ]; then
           mv -i $file $NEW_FILE
         fi
         (( n++ ))
     done
         (( m++ ))
  done
exit 0
}


case $1 in
    --help)   echo;echo;echo "Usage: rename.sh filetype newname  i.e.
rename.sh jpg My_Newname";echo;echo;echo
    ;;
    -h)   echo;echo;echo "Usage: rename.sh filetype newname  i.e.
rename.sh jpg My_Newname";echo;echo;echo
    ;;
    *) program $1 $2
    ;;
esac


```

---

### Post by skoorbevad on 2009-01-25
So you've written complex wrappers for simple one-liner programs that already exist?

**rename** - "man rename"

**convert image size** - "apt-get install imagemagick && man convert"

**search** - "sudo updatedb && locate whatever", or for the adventurous, "man find"

**extension** - once again, see "man rename".  For bonus points, combine with "find".


...good effort I guess, it just all seems superfluous.

---

### Post by brcre on 2009-01-26
About as superfluous as posting a comment indicating your disapproval.  The forums are all ready over flowing with people and their can't do, won't do, don't like it attitude. Why add to it?
   The point here is they work for us and we shared them for someone else to use as well.  You know of another way to do it great then keep reading in your search for what ever brought you to the forums in the first place.

---

