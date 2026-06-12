---
title: "Allegro game library question"
date: 2008-06-01
forum: Programming Talk
---

### Post by arseniy on 2008-06-01
Say I create a game using Allegro. How would I compile it so that when someone who doesn't have the Allegro game lib installed can play it?

Or is that even possible?

---

### Post by nvteighen on 2008-06-01
With gcc/g++, static linking is what you need: the library is merged into your executable, but, you should be aware of any licensing problems that may produce! Of course, the size of your compiled executable will increase a lot compared to a dynamically linked one.

```

gcc -static (...)

```

```

g++ -static (...)

```

That will static link **all** libraries your program uses... (inluding the respective Standard Library!). Not sure if you can chose to static link some and not others.

---

