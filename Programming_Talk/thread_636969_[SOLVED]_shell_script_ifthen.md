---
title: "[SOLVED] shell script if/then"
date: 2007-12-10
forum: Programming Talk
---

### Post by mdpalow on 2007-12-10
I'm having difficulty grasping how to correctly pull the output of $? and make a correct if/then statement out of it. I always seem to end up with the same result regardless of which selection I make in the window.

In order to keep it simple, I've just changed it  as follows, so you can quickly grasp what I'm trying to accomplish.

```
zenity --question --text "Need help?"; echo $?

if [ $? = 0 ] ; then

echo "Let me help you then"

else

echo "Ok, good. You got it."

fi
```


Also, can anyone provide a good on-line source for different types of IF/THEN  statements. All my resources are very limited and always give you the one or two most typical examples and that's it.

thanks in advance...

---

### Post by NathanB on 2007-12-10
Simply remove the ```
; echo $?
``` frome the end of the first line.  It "eats" the Zenity *exit code* and produces its own... your **if** statement always reads the code from echo which is always going to be the same.

---

### Post by mdpalow on 2007-12-10
I understand now... thanks very much for your help NatanB

---

### Post by Trumpen on 2007-12-11
By the way, you can even put directly the command  in the if expression:

```
 
#!/bin/bash

if zenity --question --text "Need help?"; then

           echo "Let me help you then"

else

           echo "Ok, good. You got it."

fi
```

Well, this change doesn't give any performance benefit but it (often) makes the code to be more readable.

---

### Post by mdpalow on 2007-12-11
Thanks Trumpen...

---

