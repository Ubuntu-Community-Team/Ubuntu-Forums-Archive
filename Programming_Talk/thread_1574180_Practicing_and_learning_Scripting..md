---
title: "Practicing and learning Scripting."
date: 2010-09-13
forum: Programming Talk
---

### Post by Jonny87 on 2010-09-13
*please move this wrong place for this thread*
I'm currently practicing and learning some basic scripting and was hoping that someone can help me with something.

basically I'm trying to get an "if" statement to read from the output of a zenity command, and then go on to  execute another command based on the result of the if. I've tried heaps of different things and tried looking it (though not 100% what to look for) so far what is as shown below.

>         zenity --list --radiolist \
          --title="Choose the Bugs You Wish to View" \
          --column="select" --column="Severity" --column="Description" \
           1 normal "GtkTreeView crashes on multiple selections" \
           2 high "GNOME Dictionary does not handle proxy" \
           3 critical "Menu editing does not work in GNOME 2.0"



if [ "$VAR" == normal ]; then
    zenity --info --title='Test' text='You selected normal'
elif [ "$VAR" == high ]; then
    zenity --info --title='Test' text='You selected high'
elif [ "$VAR" == critical ]; then
    zenity --info --title='Test' text='You selected critical'
fi

I'm still learning this stuff so my apologies if I've missed something obvious. So can any one give me an example of what to put into this script to merge the two sections together so that they work.

---

### Post by ghostdog74 on 2010-09-13
use case/esac
```

case "$var" in
  "normal" ) 
     zenity .........
     ;;
  "high" ) 
     zenity ........
     ;;
  *) echo "\$var has some other values";;
esac

```

---

### Post by Jonny87 on 2010-09-13
> **ghostdog74 said:**
> use case/esac
```

case "$var" in
  "normal" ) echo "normal";;
  "high" ) echo "high" ;;
  *) echo "else";;
esac

```

Sorry to sound like a noob (I kind of am at this scripting stuff). I'm just trying it now but I'm not sure how to apply it to what I've currently got already.

---

### Post by Jonny87 on 2010-09-13
Ok so I've kinda got the that case/esac to work with one little prob. What ever option I choose, it runs only the last option, but if I try to remove the last option, nothing happens and it just appears to crash no matter what i choose. the script is currently as follows.

```
        zenity --list --radiolist \
          --title="Choose the Bugs You Wish to View" \
          --column="select" --column="Severity" --column="Description" \
           1 normal "GtkTreeView crashes on multiple selections" \
           2 high "GNOME Dictionary does not handle proxy" \
           3 critical "Menu editing does not work in GNOME 2.0"

case "$var" in
  "normal" ) zenity --info --title="Test" --text="You selected normal.";;
  "high" ) zenity --info --title="Test" --text="You selected high.";;
  "critical" ) zenity --info --title="Test" --text="You selected critical.";;
 *) zenity --info --title="Test" --text="You Suck";;
esac
```

---

### Post by ghostdog74 on 2010-09-14
then its only logical to check the value of $var. do an echo $var to see. 
Make sure you let zenity output the result of the user chosen option and capture to $var.

---

### Post by spjackson on 2010-09-14
> **Jonny87 said:**
> Ok so I've kinda got the that case/esac to work with one little prob. What ever option I choose, it runs only the last option, but if I try to remove the last option, nothing happens and it just appears to crash no matter what i choose. the script is currently as follows.

It seems that you are simply missing a method of assigning to $var, e.g.
```
var=$(...)
```assuming this is bash. Like this
```
var=$(zenity --list --radiolist \
          --title="Choose the Bugs You Wish to View" \
          --column="select" --column="Severity" --column="Description" \
           1 normal "GtkTreeView crashes on multiple selections" \
           2 high "GNOME Dictionary does not handle proxy" \
           3 critical "Menu editing does not work in GNOME 2.0")

```

---

