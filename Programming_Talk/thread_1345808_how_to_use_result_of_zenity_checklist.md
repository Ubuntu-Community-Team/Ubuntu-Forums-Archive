---
title: "how to use result of zenity checklist"
date: 2009-12-04
forum: Programming Talk
---

### Post by seanmadi on 2009-12-04
I need to make a zenity checklist asking the user to picks options, and then using ifs to execute they picked.  The code I have is:

```

#!/bin/sh
read=`zenity --height=250 --list --checklist --title='Selection' --column=Boxes --column=Selections TRUE a TRUE b TRUE c --separator=':'`

if [ ???? ]; then
	do something
fi

if [ ???? ]; then
	do other thing
fi

if [ ???? ]; then
	do other thing
fi

```

I just need to know what to put for the question marks.  I imagine it needs to be something along the lines of "if read contains a" since if you picked every option it returns "a:b:c" but I don't know how to find out if a string contains another string.

I've tried "if ["$read" =~ *a*]" as seen in various places, but it doesn't work for me at all.  

Anyone know how to do this?

---

### Post by ib.lundgren on 2009-12-04
You could split the string containing the return values and loop through the items.

```

$ string="your:return:values:here"
$ echo $string
your:return:values:here
$ IFS=":"; for word in $string; do echo $word; done; IFS="";
your
return
values
here
```

You can check for the index of a string too, if 0 it does not appear in the searched string.
```

$ echo expr index "hello" "e"
2
$ echo expr index "hello" "y"
0

```

---

### Post by kaibob on 2009-12-04
Just to learn, I thought I would take ib.lundgren's suggestion one step further, and I came up with the following:

```
#!/bin/bash

response=$(zenity --height=250 --list --checklist \
   --title='Selection' --column=Boxes --column=Selections \
   TRUE A TRUE B TRUE C --separator=':')

if [ -z "$response" ] ; then
   echo "No selection"
   exit 1
fi

IFS=":" ; for word in $response ; do 
   case $word in
      A) echo Item A ;;
      B) echo Item B ;;
      C) echo Item C ;;
   esac
done
```

An alternative, that also works but seems a bit klunky is:

```
#!/bin/bash

response=$(zenity --height=250 --list --checklist \
   --title='Selection' --column=Boxes --column=Selections \
   TRUE A TRUE B TRUE C)

[[ $response = A* ]] && echo "Item A"

[[ $response = *B* ]] && echo "Item B"

[[ $response = *C ]] && echo "Item C"

[[ "$response" ]] || echo "No selection"
```

---

### Post by seanmadi on 2009-12-05
Thank you so much!  I spent days trying to figure this out and you answered me just in time for me to finish my class project (which is theming Gnome to look like XP and giving users the option of what they want to specifically be themed).  Thanks again!

---

### Post by t-molli on 2010-05-20
excellent

> **kaibob said:**
> Just to learn, I thought I would take ib.lundgren's suggestion one step further, and I came up with the following:

```
#!/bin/bash

response=$(zenity --height=250 --list --checklist \
   --title='Selection' --column=Boxes --column=Selections \
   TRUE A TRUE B TRUE C --separator=':')

if [ -z "$response" ] ; then
   echo "No selection"
   exit 1
fi

IFS=":" ; for word in $response ; do 
   case $word in
      A) echo Item A ;;
      B) echo Item B ;;
      C) echo Item C ;;
   esac
done
```

An alternative, that also works but seems a bit klunky is:

```
#!/bin/bash

response=$(zenity --height=250 --list --checklist \
   --title='Selection' --column=Boxes --column=Selections \
   TRUE A TRUE B TRUE C)

[[ $response = A* ]] && echo "Item A"

[[ $response = *B* ]] && echo "Item B"

[[ $response = *C ]] && echo "Item C"

[[ "$response" ]] || echo "No selection"
```

---

### Post by dwhitney67 on 2010-05-20
It's always good to reset IFS after you are done using it; not doing so could possibly affect the behavior of statements further down in your script.  I had such an incident with scripts I use on my Mac.

```

...

IFS=":"

...
[B]
unset IFS[/B]

...

```

---

