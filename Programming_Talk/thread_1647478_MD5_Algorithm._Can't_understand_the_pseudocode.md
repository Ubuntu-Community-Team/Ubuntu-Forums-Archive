---
title: "MD5 Algorithm. Can't understand the pseudocode"
date: 2010-12-17
forum: Programming Talk
---

### Post by madmax.santana on 2010-12-17
I am not sure what the programmers here think about this.

I was trying to write a program (in C++, using Code::Blocks and g++) to calculate md5 checksum of a file. I have been programming in C++ for 3 years, just for fun. And I must say I haven't gone as far as this, ever. I don't even know whether it's gonna be piece of cake or a brain-squash. But I do know that I can do it.

The only thing that is causing problem is that I don't know how they calculate the md5 hashes. I figured there must be some libraries for crypt and hash functions such as md5. But considering it is only performing DMAS operations on all the bytes of a file, I guess I don't have to use an external library, only if I can understand the pseudocode of md5.

The pseudocode is provided on [Wikipedia]("http://en.wikipedia.org/wiki/MD5#Pseudocode") and I am trying to understand it right now. I am having a hard time understanding it. (I know many would say it is the closest it go to the human comprehensible language, but still.... )

Anyway, I just want to invite you all to look at the pseudocode in the meanwhile and post your views, so that even if I miss something while reading, I can take your help and cover it up later. Also, if any of you have brighter or more-sophisticated ideas about this, I am all eyes and ears.

Thanks for reading the post, and have a nice time.

---

### Post by StephenF on 2010-12-17
Why not post your code or tell us where you are confused. It looks pretty clear to me.

---

### Post by gmargo on 2010-12-17
If your program is GPL, then you can lift the md5 code from the coreutils package.

Or, in any case, you can lift the public domain reference implementation in RFC1321: [http://tools.ietf.org/html/rfc1321](http://tools.ietf.org/html/rfc1321)

---

### Post by madmax.santana on 2010-12-17
> **StephenF said:**
> Why not post your code or tell us where you are confused. It looks pretty clear to me.
I haven't started it yet. Contrary to what I do every time, I tried to be more professional (in my own imagination) and thought it would be better if I had a visualization of the problem before I started coding it.
But clearly, that isn't the case. I am starting to code now, regardless of whether I understand everything or not. As always, it would eventually open up once I am on it...

Thanks a lot for your help gmargo. There is not "my" program yet. However, in case it is, it WILL be GPL. :) Thanks a lot for your help.

---

### Post by madmax.santana on 2010-12-17
> **gmargo said:**
> If your program is GPL, then you can lift the md5 code from the coreutils package.

Or, in any case, you can lift the public domain reference implementation in RFC1321: [http://tools.ietf.org/html/rfc1321](http://tools.ietf.org/html/rfc1321)
I am having a look at that RFC right now. And I see that it is a lot clearer. For instance, I did not understand the modulo concept while skimming Wiki, but reading the RFC, I know now what it is and how it is going to be performed. Cheers.!

---

