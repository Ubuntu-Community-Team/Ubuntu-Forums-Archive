---
title: "Bash Script Help"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by GNURULZ on 2008-11-11
Hello all I need some help on a BASH script that is an exercise in my Linux class i am not very sure on how it works and i need someone to explain to me how it will work and maybe some examples. The exercise is listed below thanks in advance.

The Problem

In the Linux file system, it is possible to create a hard link for a file. This is essentially having the file appear in more than one place in the directory tree, by entering the file in more than one directory (or more than once in the same directory).

In this exercise you will be using the ls command to search for files with hard links in every directory in the PATH environment variable. To do this, you will need to search every directory in PATH, and pick out the files with hard links with the -i switch, and then creating a listing of those files.
Help for bash programming exercise

Below, help is provided for the shell programming exercise to create the wi script. Use this in conjuction with the sample scripts.
Pseudo-Code:

1 While the first cmd line parameter is not empty
2     Loop setting a shell variable equal to each word in the current path
3     Execute the "ls" command to show the file
4     If the first cmd line parameter is in the directory of this loop
5       Execute the "ls" command again but his time putting the result into a word list variable
6       If the Third field (word) of this indicates multiple links
7         echo "Links to following files;"
8         Search and display for files with the same inode
9       endif
10     endif
11   endloop
12   Move all parameters down one
13   echo " "
14 endloop

Notes

Lines 1 and 12
    These use all the parameters in the command line in succession. They shift them all down once per iteration so that they all successively take the position $1. When $1 is empty then all command line parameters have been used and the loop should terminate.

    See: while, shift
Line 2
    Use a loop to get each word in word list defined by PATH into a script variable. This loop will iterate with the variable set to each successive directory entry in the path.

    See: for
Line 3
    Show the file with ls.
 
Line 4
    If the current command line parameter $1 is in this directory, process. (hint: Concatenate the current path with the file name to form path/file. Use the if operation to determine existance).
 
Line 5
    Use the ls command, but put its output into a shell variable in the form of a word list.
 
Line 6
    The result of the ls command is tested to see if there are multiple links to the file. (hint. convert to an array to extract the number of links and test for greater than one). 
 
Line 8
    Use the find command to search the current directory, all files with the same inode are found and listed. They should be listed using the exec option of find to list the file, once again using ls. 

General hints

Assigning variables and arrays:

        BORRIS="dog" - sets the variable BORRIS to a string "dog"
        FRED="ls $BORRIS" - sets FRED to a string "ls dog"
        FRED='ls $BORRIS' - sets FRED to a string "ls $BORRIS"
        FRED=(ls $BORRIS) - sets FRED to an array (ls dog)FRED="`ls $BORRIS`" - sets FRED to a string "output of ls"
        FRED=(`ls $BORRIS`) - sets FRED to an array (output of ls)

Most important hint:
    Start slowly. Build it up slowly from the outside inwards.
 
Best hints of the day: Use

        find $dir -inum $info[1] -print

    Then replace the printing option with

        -exec ls -ldi {} \;

    What is the difference between these two?

---

### Post by bodhi.zazen on 2008-11-11
> **GNURULZ said:**
> ... <clip> ...

These forums are not for assistance with home work, please see the "Code of Conduct".

---

