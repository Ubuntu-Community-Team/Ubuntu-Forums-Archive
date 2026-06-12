---
title: "Bash Shift Question"
date: 2009-04-21
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-04-21
Ey guys I know bash has a shift command that shifts things to the left, but is there any command that shifts things over to the right? I have tried shift -1 and it says the shift count is our of range...

Thanks in advance!

---

### Post by ghostdog74 on 2009-04-22
take a look at the bash manual about shift and you will know that it doesn't accept negative number.
> 
 shift [n]
              The  positional  parameters  from n+1 ... are renamed to $1 ....  Parameters represented by the numbers $# down to $#-n+1
              are unset.  n must be a non-negative number less than or equal to $#.  If n is 0, no parameters are changed.  If n is not
              given,  it is assumed to be 1.  If n is greater than $#, the positional parameters are not changed.  The return status is
              greater than zero if n is greater than $# or less than zero; otherwise 0.



what is it that you trying to do? describe properly, using examples

---

### Post by StunnerAlpha on 2009-04-22
Alright, well here is my code:
```

#!/bin/bash

for a in `find`
do
	if !(test -s $a); then
		read -p "Do you wish to remove $a?(Y/N)" choice
		case $choice in
			[Yy]* ) echo rm "$a";;
			[Nn]* ) echo "$a not removed";;
			* ) echo "Enter \"Y\" or \"N\"";;
		esac

	fi
done

```

Now watch when I run it:
```

$ bash cleaner.sh 
Do you wish to remove ./emptry?(Y/N)Y
rm ./emptry
Do you wish to remove ./chaat/chutney/watermalon?(Y/N)o
Enter "Y" or "N"
Do you wish to remove ./chaat/nole?(Y/N)y
rm ./chaat/nole


```

When an incorrect command is given, it moves on to the next file rather than staying at the file again for a proper command. This is why I need to be able to shift $a right once when an improper command is given so that it asks about that file again.

I did man shift but it didn't work.

Thanks for the help!

---

### Post by JK3mp on 2009-04-22
man bash.

---

### Post by ghostdog74 on 2009-04-22
you can just use find with -exec on rm -i
```

find /path -type s -exec rm -i {}\;

```

---

### Post by StunnerAlpha on 2009-04-22
Yeah I could... but I need to do it in a for loop because I am making a script to handle lots of different things... so is it at all possible to shift to the right by one or not? Thanks.

---

### Post by Arndt on 2009-04-22
> **StunnerAlpha said:**
> Yeah I could... but I need to do it in a for loop because I am making a script to handle lots of different things... so is it at all possible to shift to the right by one or not? Thanks.

It seems not, as shift only shifts to the left. It also only works on the command line arguments, not an arbitrary variable. You don't even have a variable, but that could easily be solved by doing "files=`find`" before the loop, and then "for a in $files".

I suggest you write a small 'do' loop around the case of invalid input. Even if you could shift back 'files' where you want, it's not certain that the "for a in $files" would see the put back entry.

However, one can play a little with arrays. If you try out the code below, maybe you will something useful.
```

#! /bin/bash

list="$@"

for a in $list
do
    echo /$a/
done

echo

list2=("$@")

first=${list2[0]}
unset list2[0]

for a in ${list2[@]}
do
    echo /$a/
done

echo

list2=($first ${list2[@]})

for a in ${list2[@]}
do
    echo /$a/
done

```

Example run:

```
$ /tmp/sh.sh a b c
/a/
/b/
/c/

/b/
/c/

/a/
/b/
/c/

```

---

### Post by StunnerAlpha on 2009-04-22
Thanks for that Arndt, I will definitely look into that example when I get some free time. Well I ended up creating an until loop for the invalid input case:
```

* ) until [ $choice == "Y" ]; do
	read -p "Enter \"Y\" or \"N\"" choice
done;;

```

I get stuck creating an "or" statement:
```

* ) until [ $choice == "Y" || $choice =="N" ]; do

```

I even tried:
```

* ) until [ $choice == "(( Y || N ))" ]; do

```

To no avail I got error messages in both cases... What am I doing wrong? Thanks!

---

### Post by Arndt on 2009-04-22
> **StunnerAlpha said:**
> 
I get stuck creating an "or" statement:
```

* ) until [ $choice == "Y" || $choice =="N" ]; do

```


There seem to be two errors: 1) the or operator is -o, not ||, and 2) $choice has no value the first time around, so bash in effect sees

```
until [ == Y || == N ]; do
```

You need to put $choice in double quotes:

```

* ) until [ "$choice" == "Y" -o "$choice" =="N" ]; do

```

or give 'choice' an arbitrary value before the loop.

---

### Post by StunnerAlpha on 2009-04-22
> **Arndt said:**
> There seem to be two errors: 1) the or operator is -o, not ||, and 2) $choice has no value the first time around, so bash in effect sees

```
until [ == Y || == N ]; do
```

You need to put $choice in double quotes:

```

* ) until [ "$choice" == "Y" -o "$choice" =="N" ]; do

```

or give 'choice' an arbitrary value before the loop.
Hmmm... it is now giving me this:

```

aaron@T60:~/Documents/Programming/BashProjects/test$ bash cleaner.sh 
Do you wish to remove ./emptry?(Y/N)i
cleaner.sh: line 20: [: too many arguments
Enter "Y" or "N"j
cleaner.sh: line 20: [: too many arguments


```

---

### Post by Arndt on 2009-04-22
> **StunnerAlpha said:**
> Hmmm... it is now giving me this:

```

aaron@T60:~/Documents/Programming/BashProjects/test$ bash cleaner.sh 
Do you wish to remove ./emptry?(Y/N)i
cleaner.sh: line 20: [: too many arguments
Enter "Y" or "N"j
cleaner.sh: line 20: [: too many arguments


```

What does the code look like now?

---

### Post by StunnerAlpha on 2009-04-22
> **Arndt said:**
> What does the code look like now?
```

* ) until [ "$choice" == "Y" -o "$choice" =="N" ]; do
    read -p "Enter \"Y\" or \"N\"" choice
done;;

```

---

### Post by Arndt on 2009-04-22
> **StunnerAlpha said:**
> ```

* ) until [ "$choice" == "Y" -o "$choice" =="N" ]; do
    read -p "Enter \"Y\" or \"N\"" choice
done;;

```

You should have a space between == and "N".

But shouldn't you have the loop around the whole case?

(What I said about double quotes was right but for the wrong reason. Of course 'choice' will have a value there, but it may still be the empty string.)

---

### Post by StunnerAlpha on 2009-04-22
Ah that did the trick. No I want the loop inside of the case, I have the for loop outside of the case already... If you are seeing something that can be more efficient than the way I am doing it please let me know haha. Thanks a lot by the way.

---

### Post by StunnerAlpha on 2009-04-22
One more small question... how would I go about finding empty folders only? I know I can use "find . -empty" but that gives me empty files as well. I don't see an option for directories only in the man find page either. Thanks.

---

### Post by ghostdog74 on 2009-04-22
use the -type option of find to specify directory. as usual, read the man page

---

### Post by Arndt on 2009-04-22
> **StunnerAlpha said:**
> One more small question... how would I go about finding empty folders only? I know I can use "find . -empty" but that gives me empty files as well. I don't see an option for directories only in the man find page either. Thanks.

-type d

---

### Post by StunnerAlpha on 2009-04-22
> **ghostdog74 said:**
> use the -type option of find to specify directory. as usual, read the man page
Aweome! That was enough to get me on the right track. I used "find . -type d -empty" to do it for anyone that is curious. Thanks for the help!

---

