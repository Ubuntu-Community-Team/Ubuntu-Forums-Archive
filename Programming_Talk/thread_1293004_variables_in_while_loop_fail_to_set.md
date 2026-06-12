---
title: "variables in while loop fail to set"
date: 2009-10-16
forum: Programming Talk
---

### Post by paxmanchris on 2009-10-16
I have been having the same trouble as in this thread
[http://ubuntuforums.org/showthread.php?t=708438](http://ubuntuforums.org/showthread.php?t=708438)

here is a example of what i am trying to do:
```

while read arg
do
        export rt=`echo "$rt '$arg'"`
done < /some/file.txt;
echo $rt

```

contents of file:
> 
someline1
someline2


This program runs fine on ubuntu.
but on sunOS
i get this error:
test.sh: rt=: is not an identifier

I suppose this is a question to put on a sunOS related forum, but if any of you can help, please do.

---

### Post by benj1 on 2009-10-16
google tells me sunOS uses sh by default so obviously youre using a bashism.

the problem is probably that youre referencing the variable in the assignment of the variable, but im not sure.

second thoughts its shell script so it probably wants a space in between 'rt' and '='

---

### Post by johnl on 2009-10-16
Not a bash expert.  But doesn't a 'while' loop like this execute in a sub-shell?

---

### Post by Arndt on 2009-10-16
> **paxmanchris said:**
> I have been having the same trouble as in this thread
[http://ubuntuforums.org/showthread.php?t=708438](http://ubuntuforums.org/showthread.php?t=708438)

here is a example of what i am trying to do:
```

while read arg
do
        export rt=`echo "$rt '$arg'"`
done < /some/file.txt;
echo $rt

```

contents of file:


This program runs fine on ubuntu.
but on sunOS
i get this error:
test.sh: rt=: is not an identifier

I suppose this is a question to put on a sunOS related forum, but if any of you can help, please do.

Set rt on one line, and export it on the next.

But why export it a lot of times, for that matter? Export it once, after the loop.

---

### Post by paxmanchris on 2009-10-16
i figured out its not a sunOS problem..

let me explain what this program is suppose to do. there are two lines in a file, which describe the source and destination to copy a file


the file, filenq.txt contains:
> 
/home/user/Desktop/copy test/src/filetocopy.txt
/home/user/Desktop/copy test/dest/


the space is intentional. this is what make my program fail.

the below code takes the multi line file
puts each into $CPPRAM
then does a
cp $CPPRAM

but it fails.

note: this code file is in the same dir as filenq.txt
```

FILE='filenq.txt'
set -x
while read LINE
do
	#echo "$LINE"
	TEMP='$LINE'
	export CPPRAM="$CPPRAM '$LINE'"
	echo "cp:$CPPRAM"
	if [ -f "$LINE" -o -d "$LINE" ];then
		
		continue;
	else
		echo "you failed to find $LINE";
		exit 1
	fi
done < $FILE;

cp $CPPRAM

```

error:
++ cp ''\''/home/chris/Desktop/copy' 'test/src/filetocopy.txt'\''' ''\''/home/chris/Desktop/copy' 'test/dest/'\'''
cp: target `test/dest/\'' is not a directory



the line: export CPPRAM="$CPPRAM '$LINE'"
is what messes things up. becaus of the quote.

if i had this:
export CPPRAM="$CPPRAM $LINE"

and no space in the 'copy test' directory,
the program runs fine.

so, my question is, how can i make this program work if a directory has a space

---

### Post by ghostdog74 on 2009-10-16
why is there a need to export ?
```

# exec 6<file
# read src <&6
# echo $src
/home/user/Desktop/copy test/src/filetocopy.txt
# read dest <&6
# echo $dest
/home/user/Desktop/copy test/dest/
# exec 6>&- #close file

```

now you have your variable $src and $dest
see my sig for link to learning bash

---

