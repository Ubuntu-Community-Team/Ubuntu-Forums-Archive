---
title: "C/C++ On Live CD"
date: 2008-01-03
forum: Programming Talk
---

### Post by PlatinumPlus on 2008-01-03
Has anybody tried to compile a C program on the liveCD 7.10?

I use the command cc hiheaven.c -o test but it fails. (Sorry, I don't have the message here) but I am hoping if someone has tried it they might have noticed it.

Are there any additional apps I need to add before it can work?

---

### Post by LaRoza on 2008-01-03
For Ubuntu, you need the build-essential package. If you have the RAM for this (on a live cd) you can install it.

```

sudo aptitude install build-essential

```

You will need to install this everytime for a live session.

Use gcc to compile.

---

