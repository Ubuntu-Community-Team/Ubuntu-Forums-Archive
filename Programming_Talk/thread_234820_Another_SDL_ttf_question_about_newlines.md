---
title: "Another SDL_ttf question about newlines"
date: 2006-08-12
forum: Programming Talk
---

### Post by MoxJet on 2006-08-12
Hello,

Is there a way to get get newlines in the surfaces generated from the TTF_RenderText_... commands? All I get is a little "unknown character square" when I try \n.

Would be nice instead of using a new command for every line.

Thanks in advance,
Dan

---

### Post by GeoMX on 2006-08-13
No, SDL_ttf does not recognize new lines chars. You should write your own function for doing so.

You can have a look at the example in this article:
[http://www.gamedev.net/reference/articles/article1960.asp](http://www.gamedev.net/reference/articles/article1960.asp)

Best wishes,
JJ Enríquez.

---

