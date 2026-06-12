---
title: "[C] Creating a fuse filesystem driver"
date: 2012-05-05
forum: Programming Talk
---

### Post by Xandaros on 2012-05-05
Hey there, I'm really stuck on this one.

Every time I try to compile this, I get the following error:
[/quote]undefined reference to `fuse_main_compat2'[/quote]

I even copy&pasted the official example: [http://fuse.sourceforge.net/helloworld.html](http://fuse.sourceforge.net/helloworld.html)
But it resulted in the very same error.

What the hell is going on there?
I hope you can help me sort this out

---

### Post by Bachstelze on 2012-05-05
Please post the exact command you are running, and all the output (everything until the next shell prompt).

---

### Post by Xandaros on 2012-05-05
[http://pastebin.com/Zm0E1Yhq](http://pastebin.com/Zm0E1Yhq)

Sorry, should have been obvious to add this :/

---

### Post by Bachstelze on 2012-05-05
Second command should be

```
gcc hello.o `pkg-config fuse --libs`
```

That said, when you are compiling only one file, you don't need to do it in several steps. If you omit -c from your first command, it will create the executable directly.

---

### Post by Xandaros on 2012-05-05
just omitting -c didn't work, but adding the `pkg-config fuse --libs` to the linker parameters did the trick.

Thank you so much!
Danke sehr!
&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;

seriously, I'd have never figured that out myself

---

