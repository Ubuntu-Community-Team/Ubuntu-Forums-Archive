---
title: "Initializing SDL?"
date: 2011-03-03
forum: Programming Talk
---

### Post by dodle on 2011-03-03
I compiled some code that did not initialize SDL, it did not include the function:

[php]SDL_Init();[/php]

and it seemed to work fine. So why does this function need to be called?

---

### Post by Zugzwang on 2011-03-03
> **dodle said:**
> I compiled some code that did not initialize SDL, it did not include the function:

[php]SDL_Init();[/php]

and it seemed to work fine. So why does this function need to be called?

Because of cross-platform compatibility. On some platform, some operations might have to be performed before anything using SDL might start.

So, if you remove the call to SDL_Init, your code might cease to work on MacOS or Windows, for example.

---

### Post by dodle on 2011-03-03
Thank you for clarifying.

---

