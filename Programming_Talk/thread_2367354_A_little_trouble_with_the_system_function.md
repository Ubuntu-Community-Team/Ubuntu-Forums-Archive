---
title: "A little trouble with the system function"
date: 2017-07-29
forum: Programming Talk
---

### Post by topkek on 2017-07-29
I'm trying to make a .cpp that will detect if damage has been done and play the hitmarker sound. In CS:GO.

```

bool Settings::hitDetector::enabled = false;
void playSound()
{
       if(Settings::hitDetector::enabled = true)
       {
                      system"canberra-gtk-play -f /home/myname/Downloads/hitsound.wav");
                      return;
       }
}

```

This setup doesn't seem to work in the slightest, even though it compiles fine.
The boolean gets switched ingame.

Any ideas as to why?

I'm probably doing something horrifically wrong, please tell me where.

---

### Post by spjackson on 2017-07-29
> **topkek said:**
> 
```

      if(Settings::hitDetector::enabled = true)

```

```

      if (Settings::hitDetector::enabled [COLOR=#ff0000]==[/COLOR] true)

```
Or more idiomatically...
```

      if (Settings::hitDetector::enabled)

```
g++ -Wall will give you a warning about this.

---

### Post by dwhitney67 on 2017-07-30
> **spjackson said:**
> 
Or more idiomatically...


Interesting (and correct) expression.  I however like to use the term 'preferably', especially when dealing with newbies to C++/C/Python/Java/etc.

---

