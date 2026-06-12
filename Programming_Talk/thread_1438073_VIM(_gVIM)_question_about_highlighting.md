---
title: "VIM( gVIM) question about highlighting"
date: 2010-03-24
forum: Programming Talk
---

### Post by terry_opie on 2010-03-24
I've been searching for a way to do this for quite a while.  Hoping that someone can point me in the right direction.

Using gVIM, with C++ files, I have "[COLOR="Red"]TODO[/COLOR]" highlighed in my code by having the following line in the colorscheme file that I use:

```
call s:X("Todo","ffe400","","bold","","")
```

What I'm wondering, is if there is a way to do other specific words in a similar fashion?

I've tried a few things, but nothing seems to happen.  I have a few types that we use a lot, but aren't standard int/bool, etc, thus aren't highlighted.  I would also like to highlight other tags, that I add to the code for questions, etc.

So if there is a general way to list all of the words that I want to highlight, and how I want them highlighted, it would be great, but I haven't figured it out yet.

Any help/guidance is appreciated!
Thanks.

---

### Post by Barriehie on 2010-03-29
Better late than never...  Are you looking for:
```

:hi
```
while using your colortheme?

---

