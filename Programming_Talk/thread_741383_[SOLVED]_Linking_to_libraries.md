---
title: "[SOLVED] Linking to libraries"
date: 2008-03-31
forum: Programming Talk
---

### Post by Zeotronic on 2008-03-31
I have a library... "Box2D.a" in this directory relative to my code: "Box2D/Library/"... I don't know how to link to there... I had done it once before a good while ago, but nothing I'm trying seems to work now. I had asked on the library's forums... but no one answered, so I'm dumping it on you.

How do I link to "Box2D/Library/Box2D.a"?

---

### Post by heikaman on 2008-03-31
this is probably in the programming talk FAQ i think that's why they didn't reply :) , but anyway try
 -l./Box2D/Library/Box2D
copy and paste.
or 
-L./Box2D/Library -lBox2D

---

### Post by Zeotronic on 2008-03-31
> -l./Box2D/Library/Box2D
Ok, I tried that and several variants and it repeatedly says it cant find it... *but...*
> -L./Box2D/Library -lBox2D
I tried this one and it worked perfectly. So whatever, thanks!

---

