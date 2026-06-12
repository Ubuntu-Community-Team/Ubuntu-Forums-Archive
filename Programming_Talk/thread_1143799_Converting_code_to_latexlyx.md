---
title: "Converting code to latex/lyx"
date: 2009-04-30
forum: Programming Talk
---

### Post by benjorino on 2009-04-30
Hi,

I've got a load of C++ and C code that I need to put in a lyx document, does anybody know how to do this, while preserving syntax highlighting and indentation?

I have tried:
K-develop --> HTML --> copy/paste to odt --> open odt with lyx
the above, but using writer2latex and then opening the tex file
I've tried [http://cpp2latex.geodar.com/](http://cpp2latex.geodar.com/) but it wouldnt preserve the highlighting. I can't get the command line version to work for some reason.
I've tried various other things like copying/pasting the raw tex into an ERT box in lyx instead of importing etc... without luck so far.
The closest I've come to success is to get the syntax highlighting without indentation. There's too much code to put it in manually.

Does anybody know an easy way to do this? Its getting frustrating. I'm running out of time to do this report and this has already taken a lot of my time. I don't have time to learn to write much actual latex code unless its pretty simple stuff.

Hope this is in the right forum

Thanks,
Ben

---

### Post by simeon87 on 2009-04-30
In LaTeX, you can preserve indentation by using:

```

\begin{verbatim}
// code here
\end{verbatim}

```

For syntax highlighting you'll need a separate tool (which probably exists but I wouldn't know).

---

### Post by benjorino on 2009-04-30
Thanks! That does indeed maintain the indentation... so thats both achieved individually just not together...

By the way; I don't know if this makes any difference, but all my code is indented with spaces, and not tabs.

---

### Post by hessiess on 2009-04-30
You can use the listings package for hi lighting, it works perfectly for me.
Spaces vs tabs shouldn't make any difference so long as you don't mix them

---

