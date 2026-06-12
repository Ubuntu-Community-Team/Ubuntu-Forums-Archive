---
title: "Is a static echo possible?"
date: 2014-05-20
forum: Packaging and Compiling Programs
---

### Post by j-prat-q on 2014-05-20
Hello Ubuntu Forums :D

I'm trying to set up a small script and I need a percentage to be shown in a static position. atm I have been trying so and I've done it right by using a clear and printing each entire echo, but I need to do with a clear each time, and I was wondering if there is an easier way to do so, what I mean is;

```
var=0

while [ $var -le 100 ];do
     let var=$var+1
     sleep 1
     echo $var
done
```

The final result I want is something like this;

```

********IN*PROGRESS**
**23%***************

(and one second after but in the same position)

********IN*PROGRESS**
**24%***************

```

And I was wondering how to make that $var to be in a static position, as it is shown but without clearing all the screen each time.

Hope this was understandable, thanks.

---

### Post by Lars Noodén on 2014-05-20
You could use [ANSI Escape codes](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/x361.html) to reposition the cursor.

The following  backs up the cursor 80 columns, but since the cursor is positioned at less that the 80th column, it gets set to 0:

```

echo -e "Foo**\e[80D**Bar"

```

Or if you want the output to be placed on a specific X,Y coordinate of the display, that can be done, too.

---

### Post by steeldriver on 2014-05-20
Would something like

```

printf '\r %#3d%%' $var

```

work? The %#3d right-justifies the digits within a field width of 3, which imho makes the 9-->10 and 99-->100 transitions look more natural.

---

