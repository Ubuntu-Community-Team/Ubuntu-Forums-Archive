---
title: "Some thoughts on different Python implementations"
date: 2010-12-26
forum: Programming Talk
---

### Post by zhaotianwu on 2010-12-26
Can anybody provide his/her analogy of the different implementations to Python language? Here is mine, which is not supposed to be a correct one but at least it is mine. An implementation of Python language is like ethnic of human races, we have British, American, Canadian, German, Japanese, Chinese, etc. Although seemingly they all have eyes and mouth, they cannot always speak to each other. What do you think of my analogy here?

Can they really speak to each other? If I'm using Jython, and I want to employ a piece of component that is written in C, and I want everything is in a single GUI rather than switch between different views, what can I do in this case?

---

### Post by zhaotianwu on 2010-12-27
8-[No replies? Is it because my post is silly? If so could anybody help point out so that I can remove it?

---

### Post by nvteighen on 2010-12-28
It's not silly. Probably the case is that people here aren't that used to to this kind of discussion. You know, I'm the only linguistics undergrad student here :P

In the first place, I don't agree to your analogy. I'd rather say that what is like the ethnic diversity of the human race is the diversity of programming languages, not the diversity of implementations of a single programming language.

In theory, the implementation just refer to an interpreter of an already established linguistic code. In theory, all Python implementations should be able to interpret the system of signs we use to call "Python". If my implementation doesn't understand:

```

def my_func():
    pass

```

then it isn't a Python implementation but something else.

I know that in practice this isn't exactly true and that an implementation like Jython will include extensions for JVM-interfacing that CPython doesn't for obvious reasons. 

There are extreme cases like Scheme Lisp, though. The Scheme Standard is so minimal that every implementation is barely compatible with the others. That's the only case I can think of where I'd follow your analogy.

I think we should rather talk about dialects in this case. You know, there are cases in which an American and a British may have trouble understanding eachother even though in theory they speak the same language.

---

### Post by Vox754 on 2010-12-28
> **zhaotianwu said:**
> 8-[No replies? Is it because my post is silly? If so could anybody help point out so that I can remove it?

It is. It is. I do think it's silly. It makes no sense.

Although I understand nvteighen's attempts to make some sense of this discussion, the way the first post in worded makes no sense, at all.

An implementation is like a black box, whatever you feed into it, the result must be the same. It does not matter what's inside the box, only the result must be the same.

What you are talking about communicating between different pieces of code... that makes no sense, that's not implementation.

If you have library A in CPython, and you want to use it in Jython, you would have to port library A from C to Java (implement it in Java). Now, Java may allow wrapping around C code, so you wouldn't have to rewrite the library, just add some syntactic code which interfaces with the library.

---
By the way, remember one of the rules of the Internet: once you upload it, it stays there forever. So don't feel bad if you think you just wrote something stupid. Don't try to hide your shame. Just move on.

I have the impression that many guys get sudden panic attacks and then want their threads removed or closed because of this. Don't bother, it's not big deal.

---

### Post by zhaotianwu on 2010-12-28
Thank you guys! I now make more sense out of it, especially the analogy of dialect rather than different languages. That illuminate things very well! :p

---

