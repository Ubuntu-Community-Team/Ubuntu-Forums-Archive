---
title: "[SOLVED] C++ error &amp;quot;expected primary-expression before ‘=’ token&amp;quot;"
date: 2008-10-07
forum: Programming Talk
---

### Post by srt5 on 2008-10-07
Hello,

Hopefully someone on this forum can help point me in the right direction.

I'm starting out with OpenGL development as part of my graphics programming course. I've chosen to use SDL for it's cross-platform capabilities.

I've been trying to follow the online tutorials at NeHe, they look very good and I'm looking forward to working my way through them.

However I seem to have fallen at the first hurdle and I'm getting an error during compilation when calling one of the SDL methods (note: before even starting on the OpenGL drawing code).

I am using Eclipse as my IDE. I have a project set up to run the tutorial code. This compiles and runs fine.
Then I created a new project for my own code. The code for setting up the window is almost identical to the tutorial code apart from a couple of naming changes, but when I compile my code I get the following error:

```
error: expected primary-expression before ‘=’ token
```

The line of code which causes this error is:

```
SDL_SetVideoMode(window_width, window_height, bitsPerPixel, videoFlags);
```

So this one's got me a bit confused. There's no '=' operator in sight...
If I comment out this line, the rest of the code builds fine.

Does anyone know why I would be seeing this error in my project when the other project that I created for the tutorial code works fine? I suspect it has something to do with the project properties as opposed to the actual code. As a sanity check, I pasted the tutorial code into my new project and get the same error.

Any help greatly appreciated. :)

---

### Post by Zugzwang on 2008-10-07
See how you defined window_width, window_height, bitsPerPixel, videoFlags - You might have defined these as macros containing a "=". 

Try running the GNU C++ preprocessor to expand all macros: "cpp <youroptions> yourCPPFile.cpp" and then send it through g++.

---

### Post by srt5 on 2008-10-07
> **Zugzwang said:**
> See how you defined window_width, window_height, bitsPerPixel, videoFlags - You might have defined these as macros containing a "=". 

Try running the GNU C++ preprocessor to expand all macros: "cpp <youroptions> yourCPPFile.cpp" and then send it through g++.

Indeed I had! :) Thanks for pointing that out. It now compiles successfully.

---

### Post by dribeas on 2008-10-07
> **srt5 said:**
> Indeed I had! :) Thanks for pointing that out. It now compiles successfully.

And remember: [macros are evil]("http://www.parashift.com/c++-faq-lite/misc-technical-issues.html#faq-39.4"), and [defines]("http://www.parashift.com/c++-faq-lite/newbie.html#faq-29.7") too.

---

