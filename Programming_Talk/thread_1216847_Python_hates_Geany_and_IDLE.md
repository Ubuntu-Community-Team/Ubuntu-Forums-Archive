---
title: "Python hates Geany and IDLE?"
date: 2009-07-18
forum: Programming Talk
---

### Post by Xcmd on 2009-07-18
Okay, I'm having a strange, strange STRANGE problem. Whenever I make a .py from Geany or IDLE that includes the "import pygame" information and then attempt to run it, I get a problem stating that pygame.locals does not exist. However if I copy and paste the exact code to NetBeans and run the .py from Terminal, IDLE *or* Geany, it works fine.

In fact, I opened up the NetBeans .py in Geany and the one I copied from and ran both. The NetBeans version ran from Geany. The Geany one did not. As near as I can tell, using ls -l the file permissions and ownerships are identical, as are the containing folders. Even moving or copying (either with Nautilus or the terminal) the .py to another folder isn't affecting which version will run. The ONLY difference I see is that the Geany version is coming up with 1 byte extra that the NetBeans version is not coming up with.

Has anyone ever heard of this? It's... the strangest thing.

---

### Post by kknd on 2009-07-18
Well, maybe it's an encoding problem? Set the same encoding that you use in Netbeans and test.

Doesn't makes much sense, but the problems doesn't too =)

---

### Post by Xcmd on 2009-07-19
They both use UTF-8. The only significant difference I can find is that Geany and IDLE both force an extra character at the end of the file, while NetBeans does not. Oh, and I rechecked and IDLE for 2.6 refuses to run it at all.

I wonder if there's a way to reinstall Python from scratch without having to completely reinstall the base system?

---

### Post by smartbei on 2009-07-19
Have you tried adding an encoding line in the python file?

It should look something like this:
```

#! /usr/bin/python
# encoding: utf-8

## Your code here.

```
If it is indeed utf-8, and there are non-ansi characters, then this may solve the problem. Basically it tells python what encoding the file is in.

---

### Post by Xcmd on 2009-07-19
Using [http://www.python.org/dev/peps/pep-0263/](http://www.python.org/dev/peps/pep-0263/) I tried several different encodings with no success.

My error is always:

```
Traceback (most recent call last):
  File "test.py", line 1, in <module>
    import pygame
  File "/home/######/Projects/Python/pygame.py", line 2, in <module>
    from pygame.locals import *
ImportError: No module named locals
```

My code is:

```
import pygame
import random
import os

from pygame.locals import *

pygame.init()
random.seed()

window = pygame.display.set_mode((640, 480))
pygame.display.set_caption("Pygame Window")
canvas = pygame.display.get_surface()

def main():
    event = pygame.event.poll()
    if event.type == pygame.QUIT:
        sys.exit(0)

main()
```
(This one works in NetBeans)

Even simply setting a main loop and importing only pygame it doesn't work. Any ideas?

---

### Post by smartbei on 2009-07-19
You named your file 'pygame.py'. It is importing your file instead of the library. Change the filename and it will work.

---

### Post by Xcmd on 2009-07-19
Ah. I feel dumb. I thought global libraries override local ones. :\ Thanks for the help!

---

### Post by TironN on 2010-06-11
Oh wow. I was having this same error with pygtk and now I feel dumb too :{

---

### Post by panthar91 on 2010-12-09
LOL I too had this same problem. named my file 'pygame.py' this should be documented better!

---

### Post by Tony Flury on 2010-12-11
Um - the fact that python searches the local directories first when you do an import is well documented.

[http://docs.python.org/reference/simple_stmts.html#import](http://docs.python.org/reference/simple_stmts.html#import)

If you think about it it is an incredibly useful feature - it means for instance you can do development work on pygame in one directory - by having your own local copy - whike all of your other programmes use the correct core version.

---

