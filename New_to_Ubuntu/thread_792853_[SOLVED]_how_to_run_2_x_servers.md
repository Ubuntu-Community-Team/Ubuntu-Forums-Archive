---
title: "[SOLVED] how to run 2 x servers?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by -random on 2008-05-13
hello.. can i have a gui on both tty7 and tty8 ?

I found this post:

> Another workaround would be to start another x server runing the game:
X :1 -ac & DISPLAY=:1 et

from [http://ubuntuforums.org/showthread.php?t=120704&page=2](http://ubuntuforums.org/showthread.php?t=120704&page=2)

and tried it:
```

asdf@64BiTuBuNtU:~$ startx X:1 -ac & DISPLAY=:1 et
[1] 6655
xauth:  creating new authority file /home/alrich/.serverauth.6655

X: user not authorized to run the X server, aborting.
bash: et: command not found
asdf@64BiTuBuNtU:~$ Couldnt get a file descriptor referring to the console

[1]+  Exit 71                 startx X:1 -ac
alrich@64BiTuBuNtU:~$ 
```

but didn't work..

how do i have a gui on both tty7 and tty8?

Anyh hjelp plz!

i know it's got something to do with Xorg, starx , xinit or something.. ? :mad:

---

### Post by bodhi.zazen on 2008-05-13
See this thread :

[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674") 

While perhaps not the exact same thing you should be able to easily adapt.

My guess is with[FONT=monospace] [/FONT]Xwrapper.config.

See section 2, "2. Enable script for use within X."

---

### Post by -random on 2008-05-13
Thanks a mil!

Somehow I can't do anything in tty8, All I see is:
* some stuff 
*         some more stuff..
* Checking battery state...                          [OK]
* Running local boot scripts (/etc/rc.local)         [OK]

And then I can type stuff, but 'enter' only 'returns' a new line and doesn't do anything. Then I run the script on tty6 ( cant login on any tty's above 6 as a matter of fact..) and it pops up on tty9 and tty10 (a fulscreen app).

Is this behavior normal?

( Thanks for the script it's awesome.. i'm gonna give all the windows managers a go now! ta.):popcorn::popcorn::KS:KS:KS

---

### Post by bodhi.zazen on 2008-05-13
Sounds like normal behavior.

Normally you can only log into tty 1-6

Normally tty 7-12 are for (virtual) X sessions.

---

### Post by carlosalvatore on 2009-05-01
> **-random said:**
> hello.. can i have a gui on both tty7 and tty8 ?

I found this post:



from [http://ubuntuforums.org/showthread.php?t=120704&page=2](http://ubuntuforums.org/showthread.php?t=120704&page=2)

and tried it:
```

asdf@64BiTuBuNtU:~$ startx X:1 -ac & DISPLAY=:1 et
[1] 6655
xauth:  creating new authority file /home/alrich/.serverauth.6655

X: user not authorized to run the X server, aborting.
bash: et: command not found
asdf@64BiTuBuNtU:~$ Couldnt get a file descriptor referring to the console

[1]+  Exit 71                 startx X:1 -ac
alrich@64BiTuBuNtU:~$ 
```

but didn't work..

how do i have a gui on both tty7 and tty8?

Anyh hjelp plz!

i know it's got something to do with Xorg, starx , xinit or something.. ? :mad:

To allow enay user to run X server, do as follows: 

```
sudo dpkg-reconfigure x11-common
```

then it asks...

**Users allowed to start the X server: Root, Console, Anybody.**

you must select anybody.

Then continue without changing anything until the end, and that's it.

For now on the message "X: user not authorized to run the X server, aborting." won't appear anymore.

Good luck!

---

