---
title: "Pygame problem (there is no soundcard)"
date: 2010-10-19
forum: Programming Talk
---

### Post by Skriveleif on 2010-10-19
Hi,

I've written a small python program searching through a maze. Anyways, to visualize this, I use pygame to draw what I find in the maze etc. When I had ubuntu 10.04 I had no problems with pygame, but after upgrading to 10.10 I keep getting the following message when initializing pygame: "there is no soundcard".

I don't try to play any sound at all and I don't want to either :P Any discussions I find about this message is from people wanting to play sound. I just want to get rid of it.

---

### Post by Bodsda on 2010-10-20
> **Skriveleif said:**
> Hi,
 
I've written a small python program searching through a maze. Anyways, to visualize this, I use pygame to draw what I find in the maze etc. When I had ubuntu 10.04 I had no problems with pygame, but after upgrading to 10.10 I keep getting the following message when initializing pygame: "there is no soundcard".
 
I don't try to play any sound at all and I don't want to either :P Any discussions I find about this message is from people wanting to play sound. I just want to get rid of it.
 
It may be helpful to provide your code and the traceback of the error. Without this, we would be making a semi-educated guess at what the problem is.
 
Thanks,
Bodsda

---

### Post by Skriveleif on 2010-10-22
It got nothing to do with my code, it's got to do with pygame. Making a script as follows gives the same error:

```

import pygame

pygame.init()
print "omg"

```

---

### Post by bestron on 2011-02-16
Anyone got the solution?
I have the exact same problem with Pygame and I googled it for long hours but found nothing, plz help

---

### Post by lavinog on 2011-02-16
What version of python are you using?
Is this 32 or 64 bit?
Does a sound card really not exist or is it just not supported?

Have you tried a try..except clause?

---

### Post by bestron on 2011-02-17
I have Python 2.6 for 32 bit (running Ubuntu 10.10 32 bit)

My sound card works well for all applications without any problems

and this is not an exception, it's just a message and the rest of the code will continue to run

This is some code to illustrate

```
import pygame

pygame.init()

print("Test")
```

And this is the output:
there is no soundcard
Test

---

### Post by ryuurei on 2011-03-19
I apologize for the "thread necromancy" here, but I found that calling pygame.init() twice seems to take care of the problem. The first call tends to fail for some reason on some debian-based systems, but the second call runs through and works fine (for me, anyway).

---

### Post by unknownPoster on 2011-03-19
While pygame.init() is very convenient you can also initialize the modules individually, in order to introduce some more robust exception handling.

---

### Post by m3tajak3 on 2011-05-31
> **ryuurei said:**
> I apologize for the "thread necromancy" here, but I found that calling pygame.init() twice seems to take care of the problem. The first call tends to fail for some reason on some debian-based systems, but the second call runs through and works fine (for me, anyway).

Thread, Necromancer, ryuurei did the trick. 

Calling pygame.init() twice removes the error for me on Ubuntu 11.04, using pygame 1.9.1

Thanks!

---

### Post by rblakem on 2011-06-27
I'm having the same problem, but didn't have any success calling pygame.init() twice in pygame 1.9.1 on linux mint 11

---

### Post by Niriel on 2011-11-03
But does it actually play sounds despite the error ?

---

