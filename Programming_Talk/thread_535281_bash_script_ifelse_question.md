---
title: "bash script: if/else question"
date: 2007-08-26
forum: Programming Talk
---

### Post by kwaanens on 2007-08-26
I'm trying to work my way through a script that should be easy. I start with something like this:

```
# How would you like to molest your file today?
DESIRED_OPTIONS=`zenity --list  --checklist  --width 800 --height 600 --separator " | " --column "Use" --column "Option" --column "Explanation" \
TRUE "Title" "Set the title" \
FALSE "Comment" "Make your comment" \
TRUE "File format" "Select a file format/ extension (like avi)" \
TRUE "Video codec" "Select video codec to use" \
FALSE "Qmin" "Set minimum video quantiser" \
etc... `
```

Notice that two of these are FALSE. The first one (Comment) runs fine with this entry:

```
## Set -comment.
if echo $DESIRED_OPTIONS | grep -q "Comment"
   then COMMENT=`zenity --entry --title="File comment" --text="Do you have any comments to be written to the output file?"`
   else echo "You did not wish to set a comment"
fi

if [ "${PIPESTATUS[0]}" != "0" ]
   then
   exit 1
fi
```

But it just stops after this one:

```
if echo $DESIRED_OPTIONS | grep -q "Qmin"
   then QMIN=`zenity --entry --title="Min. video quantiser" --text="Set MINIMUM video quantiser scale. Default is 1" --entry-text="1"`
   else echo "You did not wish to use Qmin"
fi

if [ "$QMIN" = "" ];
      then
     exit 1
fi
```

If I set Qmin to TRUE (checking the box in zenity), it runs through the command.
It also just stops if I leave out the "else echo "You did not wish to use Qmin""
I know it runs that else command if it is set to FALSE, because that shows up in terminal.

Can someone see what I'm doing wrong here?
I'm trying to finish off all of my blocks as I move along, because I find that it's easier to keep track of myself by doing that.

Thanks!

- Ketil

---

### Post by kwaanens on 2007-08-26
Nevermind...
I of course forgot this:


if [ "$QMIN" = "" ];
    then
    exit 1
fi

"$QMIN" = "" is true, when I did not give a value for it...

- Ketil

---

### Post by Mr. C. on 2007-08-26
Use the simpler:

```
[ -z "$QMIN" ] && exit 1
```

MrC

---

### Post by cwaldbieser on 2007-08-27
> **Mr. C. said:**
> Use the more simpler:

```
[ -z "$QMIN" ] && exit 1
```

MrC

What about
```

[ "$QMIN" ] && exit 1

```
?
I have to admit I am somewhat puzzled when I learned an empty string test.  Is it identical to the -z test?

---

### Post by Chaotic Thought on 2007-08-27
> **cwaldbieser said:**
> What about
```

[ "$QMIN" ] && exit 1

```
?
I have to admit I am somewhat puzzled when I learned an empty string test.  Is it identical to the -z test?

The following are equivalent (the test is true if the string is not the null string):

```
[ "$QMIN" ] && echo exists
```
```
[ -n "$QMIN" ] && echo exists
```

The following are equivalent and are opposite of the above (the test is true if the string is null):

```
[ "$QMIN" = "" ] && echo does not exist
```
```
[ -z "$QMIN" ] && echo does not exist
```
```
[ xx = x${QMIN}x ] && echo does not exist
```

---

