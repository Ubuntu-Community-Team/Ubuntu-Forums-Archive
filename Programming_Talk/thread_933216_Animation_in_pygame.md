---
title: "Animation in pygame?"
date: 2008-09-29
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-09-29
How can I load and use animated GIFs with pygame?

Or if not gif, is there any other way having animated images
in pygame? Or python anyway? 

Maybe another module that can render on pygame surfaces?

---

### Post by strider1551 on 2008-09-29
My God, I've been trying to figure out the same thing for the past hour!  The closest thing I've found is [this]("http://choosetheforce.blogspot.com/2008/04/third-pygame-hulk-want-animation.html"), but I keep getting an error (ValueError: String length does not equal format and resolution size).

Other than this guy, though, the answer I keep finding is no.  Pygame doesn't support it by default, so the best you can do is chop up the gif into a bunch of frames and cycle through (see [this]("http://www.gamedev.net/community/forums/topic.asp?topic_id=459408")).

That being said, I *really* hope someone proves otherwise.

---

