---
title: "Missing -&gt; cciobjc, but !"
date: 2023-08-21
forum: Packaging and Compiling Programs
---

### Post by acmehax on 2023-08-21
OK, self-solved.

I just ran a -> sudo apt install gobjc

Apparently, gcc -v lies and the ObjC tools are NOT really part of the basic gcc install even though gcc claims otherwise, lol !

I guess that all of those languages were actually enabled into this gcc build but then "apt install build-essentials" actually only downloads the basics.

Would be nice if that were documented. It's all good.

---

