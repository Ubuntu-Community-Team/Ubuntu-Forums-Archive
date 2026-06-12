---
title: "Shell Script - various questions..."
date: 2007-06-23
forum: Programming Talk
---

### Post by ryanVickers on 2007-06-23
For one, I have built this little script that finds any of those annoying text backup files ending in ~ in my home directory, and asks to remove them or not.  My code so far is this:
```
#!/bin/bash
echo
echo "=================================="
echo "= Will now display all '~' files ="
echo "=================================="
echo
find $HOME -name "*~"
echo
echo "=================================="
echo "=    End of list of '~' files    ="
echo "=================================="
echo
echo -n "Delete these files? (y/n): "
read sure
if [ $sure == "y" ]
then
rm $list
echo
echo "================="
echo "= Files deleted ="
echo "================="
echo
elif [ $sure == "n" ]
then
echo
echo "===================================="
echo "= Script aborted - Files were kept ="
echo "===================================="
echo
else
echo
echo "======================="
echo "= Not a proper answer ="
echo "======================="
echo
fi

```As you can see, it's not quite finished - it will ask to remove the files, but not be able to because there is nothing to delete!  You'll notice it's trying to delete everything in "list".  I want that 'list' to be everything that the 'find' command finds.  How might I do this?

---

### Post by netyire on 2007-06-23
Thanks for the script!

---

### Post by ryanVickers on 2007-06-23
:lolflag:

any ideas, though!? :p

Oh, if your loking for more, this ones quite simple, but...
```

#!/bin/bash
echo
echo -n "enter filename part (case sensitive): "
read part
echo
echo "please wait - scanning home directory..."
echo
rm "("$part").findersearch" >/dev/null 2>&1
find $HOME -name "*"$part"*">>"("$part")".findersearch
cat $HOME"/("$part").findersearch"
echo
echo "=========================================="
echo "= Displaying all matches in /home/%user% ="
echo "=========================================="
echo
echo -n "Search for old finder searches?(y/n/x): "
read ans
echo "- - - - - - - - - - - - - - - - - - - - - - - - - - -"
echo
if [ $ans == "y" ]
then
find $HOME -name "*.findersearch"
echo
echo "========================================="
echo "=     Displaying all search records     ="
echo "========================================="
echo
echo -n "Remove? (y/n): "
read rem
    if [ $rem == "y" ]
    then
    find $HOME -name "*.findersearch" -print0|xargs -0 /bin/rm -f >/dev/null 2>&1
    echo
    echo "========================================="
    echo "=      Old search records removed!      ="
    echo "========================================="
    echo
    else
    echo
    echo "========================================="
    echo "=    Search records were not removed    ="
    echo "========================================="
    echo
    exit 0
    fi
elif [ $ans == "x" ]
then
find $HOME -name "*.findersearch" -print0|xargs -0 /bin/rm -f >/dev/null 2>&1
echo
echo "========================================="
echo "=      Old search records removed!      ="
echo "========================================="
echo
elif [ $ans == "n" ]
then
echo
echo "========================================="
echo "=   Search 'yes' = false, Exiting now   ="
echo "========================================="
echo
else
echo
echo "========================================="
echo "=     Incorrect answer, Exiting now     ="
echo "========================================="
echo
fi

```you enter a part of a fileneme, and it will check if it exists and list all matches that exist (or not) int your home folder.  It will also save the output to a text file in home by name of your search with extension "findersearch".  Afterwards, you can enter n, y, or x to "search for residual search records; y means yes, then you can delete them if you want, n means no - skip, and x means just find and delete them, no conformation, no lists provided.  It surrounds the search name in brackets so searches for an extension (.xml for example) don't become hidden!  Just a little thought of mine!

---

### Post by ryanVickers on 2007-06-23
I made a counter that I question the efficiency of, but:
```

#!/bin/bash 
echo
echo "At anytime, hit control + c to quit"
echo
echo "Please specify a filename (or path starting at home): "
read path
echo
echo "Enter number to count to (add 1 to desired number!): "
read num
echo
echo "Enter number to start at: "
read stt
COUNTER=$stt
echo
echo "Enter number to count by: "
read by
echo
echo "Counting from "$stt" to "$num" by "$by"'s NOW!"
while [ $COUNTER -lt $num ]; do
echo $COUNTER $1 1>>$HOME"/"$path
let COUNTER=COUNTER+$by
done
echo
echo "=============================================="
echo "=      Counting Completed Successfully!      ="
echo "=============================================="
echo "The file can be found at: "$HOME"/"$path
echo -n "The filesize and name is: "
du -h $path
echo

```
it asks for a file name, where to start, end, what to count by, and displays some finishing data like ~ file size and path to file!

---

### Post by ryanVickers on 2007-06-23
If your woundering about this post, check the first one for an actuall problem! :p

---

### Post by Bluecircle on 2007-06-23
lol, for the ~ backup files, do you know that you can turn the creation of them off in gedit preferences?

---

### Post by FuturePast on 2007-06-23
```
list=`find $HOME -name "*~"`
```
though the resulting list will not then be displayed.

---

### Post by McNils on 2007-06-23
> **FuturePast said:**
> ```
list=`find $HOME -name "*~"`
```
though the resulting list will not then be displayed.

Note that files with spaces will not be deleted with aproach.  

Do an other find after with a delete flag instead of rm $list.

find $HOME -name "*~" -delete

---

### Post by ryanVickers on 2007-06-23
Wow, thanks, this is really detailed!  I thought there might be a way to turn them off, but ther stuff, like emerald and stuff, I've foud lots of them!  Run this yourselves and see!
Ok, here's my most recent code:
```

#!/bin/bash
echo
echo "=============================================="
echo "=       Will now display all '~' files       ="
echo "=============================================="
echo
find $HOME -name "*~"
list=`find $HOME -name "*~"`
echo
echo "=============================================="
echo "=          End of list of '~' files          ="
echo "=============================================="
echo
echo -n "Delete these files? (y/n): "
read sure
if [ $sure == "y" ]
then
rm $list
echo
echo "=============================================="
echo "=  Files deleted, unless there was an error  ="
echo "= in which case there was nothing to delete! ="
echo "=============================================="
echo
elif [ $sure == "n" ]
then
echo
echo "=============================================="
echo "=      Script aborted - Files were kept      ="
echo "=============================================="
echo
else
echo
echo "=============================================="
echo "=   Not a proper answer! - Files were kept   ="
echo "=============================================="
echo
fi

```
I didn't use the -delete thing because it seems to just do it with out conformation of if I wanted them removed or not, and what I've got here seems to find them all.

---

### Post by FuturePast on 2007-06-23
```
#!/bin/bash
echo
echo "=================================="
echo "= Will now display all '~' files ="
echo "=================================="
echo
find $HOME -name "*~"
echo
echo "=================================="
echo "=    End of list of '~' files    ="
echo "=================================="
echo
echo -n "Delete these files? (y/n): "
read sure
if [ $sure == "y" ]
then
[COLOR="Red"]find $HOME -name "*~" -print0|xargs -0 /bin/rm -f[/COLOR]
echo
echo "================="
echo "= Files deleted ="
echo "================="
echo
elif [ $sure == "n" ]
then
echo
echo "===================================="
echo "= Script aborted - Files were kept ="
echo "===================================="
echo
else
echo
echo "======================="
echo "= Not a proper answer ="
echo "======================="
echo
fi

```

---

### Post by ryanVickers on 2007-06-23
Of course!  I can't beleive I didn't think of that?! :p  Thakns, I *thought* there must be some better way...

---

### Post by ryanVickers on 2007-06-23
Now, I just made this (you have to install "pi" to use it)
```

#!/bin/bash
echo
echo -n "How many decimal places of pi would you like? "
read dec
echo
echo "Will now 'evaluate' pi to "$dec" decimal places..."
echo
pi $dec >>pi_to_$dec
echo "Finished - File can be found at" $HOME"/pi_to_"$dec
echo

```there seems to be something wrong with it - large numbers seem to fill up my ram and crash it quite quickly.  I tryed 1 million and it was done in about 2 seconds, so I tried 1 billion and it just exploded! :p  Whats wrong?!  Why would this take more than 1Mb of ram at most!!!???

Just had a thought - I think it's storing everything it generates in ram until ther very end!  How do I make it write to disk after avery few numbers?

---

### Post by ryanVickers on 2007-06-23
I made another script along the "cleaner" line, it shows all the stuff in the trash and you cal clear it too.  It's most useful for viewing _*everything*_ in the trash without oping it and going show hidden files and all that.
```

#!/bin/bash
echo
echo "============================================="
echo "=      Will now display Trash contents      ="
echo "============================================="
echo
find $HOME"/.Trash/" -name "*"
echo
echo "============================================="
echo "=       End of list of Trash contents       ="
echo "============================================="
echo
echo -n "Empty the Trash? (y/n): "
read sure
if [ $sure == "y" ]
then
find $HOME"/.Trash/" -name "*" -print0|xargs -0 /bin/rm -f >/dev/null 2>&1
echo
echo "============================================="
echo "=     Answer is yes - Trash was cleared     ="
echo "============================================="
echo
elif [ $sure == "n" ]
then
echo
echo "============================================="
echo "=   Script aborted - Trash was left alone   ="
echo "============================================="
echo
else
echo
echo "============================================="
echo "= Not proper answer! - Trash was left alone ="
echo "============================================="
echo
fi

```Quite similar.  It may look like it will *remove* the trash folder, but it doesn't :)

Edit: I just realized it deletes the files, but it will not remove folders! :p  And if there are files in folders, it sucks them out and leavs the folders behind! I thnk that's kinda cool :) - but it also makes it not a teribly good trash "emptier" ;)

I also updated my "finder search engine" (_*way*_) above :)

Once again, just above this post is an actuall problem insted of just posts of scripts :)

---

