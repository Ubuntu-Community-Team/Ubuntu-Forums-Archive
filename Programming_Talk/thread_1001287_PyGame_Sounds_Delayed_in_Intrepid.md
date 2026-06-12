---
title: "PyGame Sounds Delayed in Intrepid"
date: 2008-12-03
forum: Programming Talk
---

### Post by moephan on 2008-12-03
Hello,

I have a pygame game that I wrote on Hardy. The sounds worked fine on Hardy. Now when I run the game on Intrepid there is a noticeable delay before the sound plays. It has a very negative effect on gameplay.

1. I call pygame.mixer.init() when the program starts up
2. In my sprite subclasses I create new sound objects by calling pygame.mixer.Sound().
3. I play the sound at the appropriate time by calling play() on the sound object.

I don't do anything fancy with channels or anything. Any thoughts about what I am doing wrong?

TIA

Cheers, Rick

---

