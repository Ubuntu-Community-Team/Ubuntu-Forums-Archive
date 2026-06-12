---
title: "Need help with SDL+Code::blocks - lmingw32 not found :/"
date: 2011-08-06
forum: Programming Talk
---

### Post by NTpspE on 2011-08-06
Hey everyone,

So I've got Code::blocks and it's brilliant in my opinion, really like the interface and layout. I've downloaded all the SDL development packages via terminal, and they all include correctly and everything.

However, as soon as I try to build+run the default SDL program to test it, it says in the build messages:
"ld                      cannot find -lmingw32"

Which i'm stumped at... From what I heard, lmingw is for making windows in windows (lol), but that's not what I want, I'm making a ubuntu program, so why? why is it trying to use that when I don't want it to, and what do I do to solve it? 
There's no mention of -lmingw32 in the source, so it's either something in the header, or SDL can't be used for ubuntu programs (tho i'm sure it can be)

Any and all help will be appreciated immensely :) Thanks guys

-NT

---

### Post by NovaAesa on 2011-08-06
It sounds to me like code::blocks is trying to link using the -lmingw32 flag for some reason (and you correctly said that there is really no need for it to). I don't use code::blocks myself, but there should be options somewhere that say which flags the compiler and linker receive - just remove -lmingw32 and see if that fixes it.

---

### Post by NTpspE on 2011-08-07
Aah yeah, silly me >_< One one of the guides I was following a long time ago it told me to add that flag for SDL to work... guess the guide wasn't for linux after all, removed the flag and it all works fine haha :) Thanks

---

