---
title: "Why didn't my script worked?"
date: 2010-08-07
forum: Programming Talk
---

### Post by pato wlmc on 2010-08-07
Well i was making an .sh for the gtkrc-2.0 file ( i know there are many of them, but i wanna try to make one by my own )

This was my script

```
 #!/bin/bash  

cd /home/patowlmc/

 if [ -e .gtkrc-2.0 ];

  then mv .gtkrc-2.0 .gtkrc-2.0-notactivated
  killall nautilus

 elif [ -e .gtkrc-2.0-notactivated ]

  mv .gtkrc-2.0-notactivated .gtkrc-2.0
  killall nautilus

 fi
   
```

So that way i could "turn off and on" gtkrc.  But the thing is the script gave me an error the second time i executed it ( so the elif function was the worng one )

At the end i managed to solved it by changing

```
 elif [ -e .gtkrc-2.0-notactivated ]

  mv .gtkrc-2.0-notactivated .gtkrc-2.0
  killall nautilus

```

to:
 ```
else

  mv .gtkrc-2.0-motactivated .gtkrc-2.0
  killall nautilus
 
```

Is merely the same, but as you can see now is a little bit more general ( an else function instead of an elif one )

Do you know why it gave me this error : [: 15 missing:]  The number 15 represents the # of lines in my script i'm pretty sure, but that's all i have.

P.D. SORRY FOR THE BAD ENGLISH =p

---

### Post by slooksterpsv on 2010-08-07
The elif is missing a semicolon ( ; ) at the end - like how you have it in your if statement. Also it's missing then afterwards too

---

