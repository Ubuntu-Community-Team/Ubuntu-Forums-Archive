---
title: "My unix class script project."
date: 2007-10-23
forum: Programming Talk
---

### Post by ant2ne on 2007-10-23
I'm working ahead (sort of) This is the project for my final exam. And I'm getting the jump on it early.

The assignment> Create a script file named "filepro" which has a menu that does the following:

Delete a file

Rename a file

Find a File

Display contents of a file using cat

Edit a file using vi

List the contents of a directory

Exit the menu program

Each item should prompt you for the filename or other details needed to carry out the command. Do not pass the filename as a command line argument. Prompt for, then read, the filename as a variable.

Add two items to the menu of your own choosing

Once it performs the task it should return to the menu until you choose to exit.

Set the permissions on filepro to 700

Of course it should give you the opportunity to see the output before returning to the menu. 

The script
```
#!/bin/sh
XNAME=$(whoami)
clear
echo "Greetings " $XNAME
echo "---------- Choice Menu ----------"
echo
echo "1. destroy a file"
echo "2. rename a file"
echo "3. find a file"
echo "4. cat af file"
echo "5. vi a file"
echo "6. list contents of a directory"
echo "7. own a file"
echo "8. backup a file"
echo "Choose the action to be executed" ; read choice
echo
echo "---------- File Name ----------"
echo
echo "enter the file name (and path):  " ; read filename

case $choice in
    1)   rm $filename;;
    2)   echo "enter the new file name (and path):  " ; read newfilename ; mv $filename $newfilename;;
    3)   find $filename;;
    4)   cat $filename;;
    5)   vi $filename;;
    6)   ls $filename;;
    7)   chown $XNAME $filename;;
    8)   sudo tar  --create --file=$XNAME.backup.`date +%m'.'%d'.'%Y`.tar $filename;;
esac
```How do I get it to go back to the top of the menu?

---

### Post by ghostdog74 on 2007-10-23
use a while loop

```


whiile [ 1=1 ];
do
  clear
  echo "Greetings " $XNAME
  echo "---------- Choice Menu ----------"
  echo
  echo "1. destroy a file"
  echo "2. rename a file"
  echo "3. find a file"
  echo "4. cat af file"
  echo "5. vi a file"
  echo "6. list contents of a directory"
  echo "7. own a file"
  echo "8. backup a file"
  echo "9. Exit"
  echo "Choose the action to be executed" ; read choice
  echo
  echo "---------- File Name ----------"
  echo
  echo "enter the file name (and path):  " ; read filename
  
  case $choice in
      1)   rm $filename;;
      2)   echo "enter the new file name (and path):  " ; read newfilename ; mv $filename $newfilename;;
      3)   find $filename;;
      4)   cat $filename;;
      5)   vi $filename;;
      6)   ls $filename;;
      7)   chown $XNAME $filename;;
      8)   sudo tar  --create --file=$XNAME.backup.`date +%m'.'%d'.'%Y`.tar 
 $filename;;
      9)  exit;;
  esac


done

```

---

### Post by slavik on 2007-10-23
why 1=1? you can just do while [[ 1 ]] :)

everything seems correct.

---

### Post by ghostdog74 on 2007-10-23
> **slavik said:**
> why 1=1? you can just do while [[ 1 ]] :)

a long long time ago,  i was  using bourne...:)...habit i guess

---

