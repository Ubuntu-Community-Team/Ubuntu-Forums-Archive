---
title: "32-bit or 64-bit?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by gfern on 2008-06-04
Ahm... I'm sure this is gonna sound ridiculous... but how do I know if I'm a 32-bit or 64-bit user? - truly a newbie, straight from the oven.

---

### Post by Joeb454 on 2008-06-04
Then you'll most likely be a 32 bit user :)

Click Applications > Accessories > Terminal and copy/paste this and hit enter ```
uname -m
``` and post the output back here, and we can tell you for definite :)

---

### Post by gfern on 2008-06-04
Heheh, well, it only says: "i686"

---

### Post by Joeb454 on 2008-06-04
And that means (99.99999% of the time anyway) that you're running a 32 bit system, as I expected, mine returns **x86_64** :) As I'm running a 64 bit system.

---

### Post by gfern on 2008-06-04
Wow, how neat, thanks for the answer Joeb! Is the 64-bit faster? Should I be running that? I'm guessing not... since, judging from your post, 99,99999% of the users who have the same machine as me run the 32-bit system... but who knows... I can be avant-garde... lol

---

### Post by Joeb454 on 2008-06-04
It depends what processor you have. I'm just running 64-bit because I can ;)

But the only real advantage currently is if you do processor heavy tasks - video encoding/large image editing etc.

So basically - if you're not doing that, just stick to 32 bit :)

---

### Post by gfern on 2008-06-04
Ok! Well, 32-bit sounds pretty good for now. ; ) Thanks again!

---

### Post by hexanol on 2008-06-04
Well, first, if you want to run the 64-bit version, you need a 64-bit capable processor. Is it the case ? If you show us the content of the /proc/cpuinfo file, we might be able to tell you so.

As for the question, is 64-bit faster ? Well, for many users, i would say they wouldn't see the difference since I believe there's isn't much of a difference anyway (correct me if I'm wrong). Some people (like me) are only running the 64-bit version because first they can and because they want to use all their memory (if you have 4 GB of memory or more, you'll have to use a 64-bit operating system to use it fully).

Yeah, my first post on the forum! :p
Ooops, but i have been too slow.

---

### Post by Joeb454 on 2008-06-04
> **hexanol said:**
> Ooops, but i have been too slow.

It was still a good first post - and welcome :)

---

### Post by dusanx on 2008-06-04
Try this from terminal to see what kind of processor you have:

> sudo lshw -C cpu | grep width

If result is _width: 64 bits_, there is fair chance that you can run 64 bit system ;)

---

