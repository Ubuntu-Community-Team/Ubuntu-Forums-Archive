---
title: "AVI programming"
date: 2010-04-06
forum: Programming Talk
---

### Post by hyperdrinky on 2010-04-06
Hi Guys/Girls,

i'm looking for a little advice. I come from a windows game programming background and am looking to branch out into Linux. I'm getting the hang of gcc and want to use openGL purely for my familiarity with it.

However, I want to play AVI files in my programs and wondered if there was a decent library available around the interweb. I found references to AVIfile but it seems to be quite old. Has anybody used this and if so, is it up to the job? is there something newer which I am missing?

Thanks for your input.
Hyperdrinky

---

### Post by heikaman on 2010-04-06
You can try to write a video player yourself, using **ffmpeg**, basically, you decode the video stream and map each frame on a **texture** but you still need to play the audio stream and sync, I wrote a video player like this before following** dranger's **[[COLOR="Blue"]tutorial[/COLOR]]("http://dranger.com/ffmpeg/") but it wasn't an easy task.

There's also a nehe [[COLOR="Navy"]tutorial[/COLOR]]("http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=35") that talks about playing **avi** with **opengl** maybe there's an easier way.

---

