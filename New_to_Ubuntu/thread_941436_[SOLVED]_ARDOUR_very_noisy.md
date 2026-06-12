---
title: "[SOLVED] ARDOUR very noisy"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by sophie27 on 2008-10-08
Hi All!
I've just begun to use Ardour to record my guitar.
Here's my problem: when I listen what I have recorded, the sound is very noisy and often interrupted! You can't listen to that...

How can improve the quality of the recording?
Notice that:
- I use Toshiba A300 laptop
- I use MIC socket to record (I don't have any other LINE IN socket...)
- I have already tried to change MIC parameters with KMIX, but I suppose the MIC is not the cause because
- THE PROBLEM OCCURS ALSO IF I ADD AN EXISTING AUDIO inside my laptop

Any idea about that?
THANK YOU, have a good day



:guitar:


I precise that jack seems to work fine

---

### Post by sophie27 on 2008-10-08
The same problem occurs if I try to use something else, like qtractor...
So I guess the problem is in jack...

---

### Post by sophie27 on 2008-10-09
OK, found the solution!

The problem was with the qjackctl setup: 
I changed the parameter Periods/Buffer, i put 3 instead of 2 and all works now.

I think the qjackctl setup is a quite tricky question, but on the web i haven't found an exhaustive manual. I mean, I've found the solution to my problem but i actually don't know the meaning of the parameter i have changed...

Any advise on this argument will be accepeted!!

Have a good day.

---

