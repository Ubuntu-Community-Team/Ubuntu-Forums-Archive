---
title: "Help with splitting videos using ffmpeg+shell script"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by flurospar on 2012-04-19
So, I have a 50 minutes video which I must split in sections (as part of an experiment).

I did this:
```

#!/bin/bash
i=0

while [ $i -le 50 ] ; do
    if [ $i -le 9 ] ; then
        i=0"$i"
    fi
    ffmpeg -ss 00:00:"$i".000 -t 25 -i the_light_bulb_conspiracy.flv -acodec copy -vcodec copy vid."$i".flv -loglevel quiet
    i=$(($i + 1))
done

```But problems arise:
```

$ ./test.sh
./test.sh: line 9: 08: value too great for base (error token is "08")

```Please help me out.

---

### Post by sudodus on 2012-04-19
from ```
man ffmpeg
```
```
       -ss position
           Seek to given time position in seconds.
           "hh:mm:ss[.xxx]" syntax is also supported.

```
I suggest you use seconds, not the hh:mm:ss format for the seek option.

---

### Post by mikechant on 2012-04-19
It looks like you're accidentally using Octal (base 8 ) numbers, probably because of the leading 0 on line 6. Looks like you might need to change line 6 to
```
i=10#0"$i"
```
to force base 10.


NB There are a number of references to this sort of problem, google for "value too great for base (error token is "08")".

---

### Post by flurospar on 2012-04-19
Thanks to everyone. I am going with the first solution.

The shell script thus became (not an equivalent of what I was trying to do in the above, though):
```

#!/bin/bash
i=0

while [ $i -le 5 ] ; do
    ffmpeg -ss $(($i * 100)) -t 25 -i the_light_bulb_conspiracy.flv -acodec copy -vcodec copy vid."$i".flv -loglevel quiet
    i=$(($i + 1))
done


```

---

### Post by sudodus on 2012-04-19
I'm glad it works for you :-)

And when you are satisfied, please click on [COLOR="Red"]**Thread Tools**[/COLOR] at the top of this page and mark this thread as SOLVED! *Edit: Sorry, you already did *

---

