---
title: "script wont save to file"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by hyburn on 2008-11-26
Im trying to create a very basic script, but it wont save anything into the designated file. File is created, but no results are saved in the file

#!/bin/sh
echo &#8220;here are your dmesg results&#8221;
dmesg
./hyburn.sh >> /home/hyburn/Desktop/dmesg.txt

---

### Post by jpkotta on 2008-11-26
I'm suspicious of your quotes.  They look fancy (as in, not ascii).  Maybe it's just the forums formatting them nicely.  Try removing the quotes.  What editor are you using?

---

### Post by Tyke91 on 2008-11-26
can you be more specific? Is it your script code that won't save? Or is it not outputting to the dmesg.txt file that you created? Have you given the script rights to execute?

---

### Post by hyburn on 2008-11-26
removing the quotes doesnt fix it. I am using notepad

it is the outputting information that wont save

---

### Post by jpkotta on 2008-11-26
So the script outputs stuff to stdout, but doesn't work with the redirect?

What happens when you just redirect dmesg?```
dmesg >> /home/hyburn/Desktop/dmesg.txt 
```

---

### Post by hyburn on 2008-11-26
got it thanks, now I can continue to write my ****

---

### Post by handydan918 on 2008-11-27
> **hyburn said:**
> got it thanks, now I can continue to write my ****
Great. Thanks a lot for helping all the other little people who will run into a similar problem. Way to finish a thread. 




I bet your GF just LOVES you...

---

