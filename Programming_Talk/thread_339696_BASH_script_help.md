---
title: "BASH script help"
date: 2007-01-16
forum: Programming Talk
---

### Post by derby007 on 2007-01-16
Basic personal programming Q here: can someone tell me if this works, >> the 'if -- else' bit, ie. i dont ave access to a Linux system at the mo & i'm writing this off the top of my 'tiny brain', ie. i'm in work & i'm bored.....pls suggest improvements aswell, i know this could be done a hundred ways, i'm not looking for the most obscure way!!.......the script should give the user the options to either search for a file on the filesystem, or a word in a particular file......maybe improvements like looping on the MENU & e for EXIT, dare i say it a graphical way to do it !!

echo clear
echo "Enter 1 for Word-Find program:"
echo "Enter 2 for File-Find program:"
read a
if [ "$a" -eq 1 ] 
 then
   	echo "Enter search WORD:"
	read w
	echo "Enter /path/file to search:"
	read p
	grep $w $p

elif [ "$a -ep 2 ]
 then
   	echo "Enter search FILE:"
	read f
	echo "Enter /path/ to search:"
	read pa
	find -xdev $pa -type f ¦ grep $f      #xdev > dont search thru other partitions/drives
 
 else
	echo "Wrong choice !"
fi
exit $?

---

### Post by amo-ej1 on 2007-01-16
Well you don't need quotes around variable name "$a" -eq 1 will compare 1 to the string $a not to the contents of the variable named a 

and you will want some indentation around that too :D

---

### Post by derby007 on 2007-01-16
Note: i'm no programmer & i was doin all this from memory.....
so.....what ure saying is: 
if [ $a -eq 1 ]   >>   is correct ?
'indentation'     >> sorry i dont understand, 

i'm new to all this.....:-k

---

### Post by amo-ej1 on 2007-01-16
i was trying to say that putting everthing between code tags and adding some spaces will make you script a lot more easy to read

---

### Post by souki on 2007-01-16
the 'if' 'elif' 'else' construction is ok
there's some typos in your script, but quite good if you did it from memory, 

here is your code, with some fixes and wrapped with ```
 tag (the '#' icon)

[code]#!/bin/sh

echo clear
echo "Enter 1 for Word-Find program:"
echo "Enter 2 for File-Find program:"
read a
#if [ "$a" -eq 1 ]
if [ "$a" -eq "1" ]
then
        echo "Enter search WORD:"
        read w
        echo "Enter /path/file to search:"
        read p
        #grep $w $p
        # chang this to : insensitive search, recursive, show only file name
        grep -irl $w $p

#elif [ "$a -ep "2" ]
elif [ "$a" -eq "2" ]
then
        echo "Enter search FILE:"
        read f
        echo "Enter /path/ to search:"
        read pa
        #find -xdev $pa -type f ¦ grep $f #xdev > dont search thru other partitions/drives
        # fixed syntax, use of -iname (insensitive search)
        find $pa -xdev -type f -iname $f

else
        echo "Wrong choice !"
fi
exit $?
```cheers

---

### Post by derby007 on 2007-01-16
Thanks souki, sorry amo-ej1, actually i had it indented in notepad (rem. i'm nowhere near a Linux desktop, bummer) but when i pasted in the code i didn't check for indentation, i assumed it went in OK, doh!
If i was to start to try and put a graphical look to it, what should/could i use? note: i have netbeans installed but i have also some basic C/C++ knowledge. Shud i now learn some Perl/Python ? I'm thinking it wud be cool to get a Gnome app going  :-D

---

### Post by souki on 2007-01-16
> **derby007 said:**
> Thanks souki, sorry amo-ej1, actually i had it indented in notepad (rem. i'm nowhere near a Linux desktop, bummer) but when i pasted in the code i didn't check for indentation, i assumed it went in OK, doh!

yes, that's why there is a "Preview Post" button ;)

>  If i was to start to try and put a graphical look to it, what should/could i use? note: i have netbeans installed but i have also some basic C/C++ knowledge. Shud i now learn some Perl/Python ? I'm thinking it wud be cool to get a Gnome app going  :-DI think python+pyGTK is realy good, there's some great tutos and great apps [http://www.pygtk.org/](http://www.pygtk.org/)
perl is powerfull but I would not use it for that

---

### Post by jblebrun on 2007-01-16
> **amo-ej1 said:**
> Well you don't need quotes around variable name "$a" -eq 1 will compare 1 to the string $a not to the contents of the variable named a 

and you will want some indentation around that too :D

That's not true. BASH will expand variables within double-quoted strings. It will NOT expand variables within single-quoted strings. But in this poster's example, the syntax is correct, and will do what he or she expects. 

echo "$DISPLAY" 
:0.0
echo '$DISPLAY'
$DISPLAY

---

