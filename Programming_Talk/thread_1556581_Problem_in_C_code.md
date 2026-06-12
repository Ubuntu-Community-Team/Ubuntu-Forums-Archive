---
title: "Problem in C code"
date: 2010-08-19
forum: Programming Talk
---

### Post by piyush.neo on 2010-08-19
Can anyone explain me this code..?
[http://golf.shinh.org/p.rb?duplicate+certain+lines+_C_](http://golf.shinh.org/p.rb?duplicate+certain+lines+_C_)
```
short*p;
f(){
*p%691||f(++p);
puts(p);
}
main(s)
{
for(;gets(p=&s);)
f();
}

```

Most surprising is what this magic number  691  doing here?
Is assembly language something to do?
Thanks....

---

### Post by schauerlich on 2010-08-19
A short is 2 bytes wide, so he's using p to grab 2 characters at a time. "d " (the letter 'd' plus a space) is represented by 0x2064 on a little endian machine, which translates to 8292. 8292/691 is exactly 12, so 8292%691 will be 0. This evaluates to false, so it will evaluate the other half of the or statement. That makes it move on to the next two bytes and does the same thing. Whenever p doesn't point to "d " it will print out whatever is there, and since it's recursive it will print out the same p as the recursion unwinds. Quite clever, actually, if a bit cryptic.

---

### Post by worksofcraft on 2010-08-19
> **schauerlich said:**
> 
...Quite clever, actually, if a bit cryptic.

lol yes, it violates so many recommended programming practices, like passing short * where a char * should be, relying on byte ordering, having one parameter in main of no type and using it's address to stash input lines. It is evidently intended to be cryptic. It's a great little brain teaser that illustrates how unsafe the C language really is. Using techniques like that in a real project would be bound to cause no end of problems :lolflag:

---

### Post by SledgeHammer_999 on 2010-08-19
unless it is an optimization for something :)

---

### Post by schauerlich on 2010-08-19
> **worksofcraft said:**
> lol yes, it violates so many recommended programming practices, like passing short * where a char * should be, relying on byte ordering, having one parameter in main of no type and using it's address to stash input lines. It is evidently intended to be cryptic. It's a great little brain teaser that illustrates how unsafe the C language really is. Using techniques like that in a real project would be bound to cause no end of problems :lolflag:

I didn't scour the site, but it appears to be one of those fewest-character challenges. Sometimes it's fun to play around at that level and see what you can get away with. I seem to alternate between appreciating this type of stuff and then going and learning Lisp and functional programming and thinking of everything in very abstract terms. :) Each is useful in its own way.

---

### Post by piyush.neo on 2010-08-19
Thank u all....:p

---

