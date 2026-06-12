---
title: "Need a native C# compiler"
date: 2008-09-05
forum: Programming Talk
---

### Post by snova on 2008-09-05
The title of this thread may be misleading. I am not looking for a C# compiler that runs natively on Linux, but for a compiler that can generate native C# code. Does anybody know of such a thing? I don't think Mono can do it.

I know the point of C# is to *not* be compiled, but I don't think I have a choice in this particular matter. It has nothing to do with performance, or I'd just stick with C++.

Please excuse me if the answer is obvious (like an extra command line parameter), but I've only just started in this field...

---

### Post by jimi_hendrix on 2008-09-05
C# isnt supposed to be compiled? then ive been doing it wrong...did you check the sticky?

---

### Post by snova on 2008-09-05
I meant that C# is not supposed to be compiled *natively*. I think .NET languages are compiled to an intermediate bytecode; and then either interpreted at runtime or compiled to native machine code just prior to executing (JIT - Just In Time).

I looked at the sticky, or the two that looked useful anyway. One of them had an example of how to compile a simple program, but resources on C# were lacking. Unless I missed it...

---

### Post by true_friend on 2008-09-06
Operating systems built in c# may have a native code compiler.
Like [SharpOS]("http://www.sharpos.org/redmine/") or [Cosmos]("http://gocosmos.org/index.en.aspx").
Regards

---

### Post by kirsis on 2008-09-06
Check this link out: [http://www.mono-project.com/AOT](http://www.mono-project.com/AOT)

For reference, what you seek is called Ahead of Time (AOT) compilation (as opposed to JIT - just in time). Hope that helps.

---

### Post by babyhuey on 2008-09-06
Out of curiosity, why do you need this? 
I'm not second guessing you, I'm genuinely curious why someone would need this.

Once you jit c# it is compiled just the same as AOT, right? Except that AOT is more generic so it could actually run slower.

I'm obviously missing something.

---

### Post by jimi_hendrix on 2008-09-06
> **true_friend said:**
> Operating systems built in c# may have a native code compiler.
Like [SharpOS]("http://www.sharpos.org/redmine/") or [Cosmos]("http://gocosmos.org/index.en.aspx").
Regards

never heard of a C# OS

---

### Post by snova on 2008-09-06
I discovered last night that what I wanted was an "AOT" compiler. I also found that mono has an option for this (--aot) but until I look into the specifics I probably shouldn't try it.

Why do I want one? Well, because I write kernels for fun, and I thought a C# kernel was a neat idea, and because I wanted to try it myself... So I already know about SharpOS. Never heard of Cosmos, though...

My concerns with using the SharpOS tool is that their compiler might be too specialized for their project. But then, it's not so much a compiler as it is a converter. I might just have to tweak it...

Hmm... By the looks of it, both SharpOS and Cosmos convert IL to assembly and then compile it from there. Ok. I've learned something. There is no such thing as a C# to native code compiler. They all work from bytecode. This actually simplifies things, since I can just use standard compilers for the first stage.

Alright, I'm downloading Cosmos now. I'll see what I can borrow from it...

Thanks everybody! I think that's it for now.

---

### Post by jimi_hendrix on 2008-09-06
i know quite a bit of C#...wered you find out how to write a kernel in it?

---

### Post by snova on 2008-09-06
> i know quite a bit of C#...wered you find out how to write a kernel in it?

I *don't* know how! But I do know that I'm going to need a compiler eventually, so I asked about it. For now, though, I'm sticking with C++. And after I read all the posts on these forums that look interesting, I'm going to modify it to trigger a panic after it dumps a bunch of debug information, just to see how it looks.

The first example of a C# kernel I found was Singularity. It's a Microsoft Research project.

Unfortunately, I think only two of Microsoft's licenses are OSI approved, and Singularity is under neither of them.

But not only is Singularity written in C# (actually a variant called Sing#), but it pretty much starts over with OS's. In particular, it can only run managed code applications. This might seem like a limitation, but it's actually a neat idea, because it can run everything in ring 0. Without the constant context switches, code overall is supposed to run faster. In addition, the runtime is built in, which should improve it further.

I got a number of neat ideas from it.

---

### Post by jimi_hendrix on 2008-09-06
cool...can you tell me how when you find any resources for writing the kernel?

---

### Post by babyhuey on 2008-09-07
> **snova said:**
> I *don't* know how! But I do know that I'm going to need a compiler eventually, so I asked about it. For now, though, I'm sticking with C++. And after I read all the posts on these forums that look interesting, I'm going to modify it to trigger a panic after it dumps a bunch of debug information, just to see how it looks.

The first example of a C# kernel I found was Singularity. It's a Microsoft Research project.

Unfortunately, I think only two of Microsoft's licenses are OSI approved, and Singularity is under neither of them.

But not only is Singularity written in C# (actually a variant called Sing#), but it pretty much starts over with OS's. In particular, it can only run managed code applications. This might seem like a limitation, but it's actually a neat idea, because it can run everything in ring 0. Without the constant context switches, code overall is supposed to run faster. In addition, the runtime is built in, which should improve it further.

I got a number of neat ideas from it.

I looked at Singularity a while back. It is definitely intriguing.

---

### Post by snova on 2008-09-07
I think the most important idea I took from it was the thought of making an io port into a class. Despite using C++, I'd forgotten about that possibility. So now I have "class IoPort".

I don't think you can successfully make an entire OS from managed code. It's simply too much to give up; too much to rewrite from scratch (the entire userspace!). I would suggest a hybrid for the best of both worlds: run managed code in kernel space and compiled apps in ring 3.

But Singularity is just a research project. I'm more concerned about [Midori]("http://en.wikipedia.org/wiki/Midori_(operating_system)"). They took the concept behind Singularity and started to build a new OS out of it. One wonders what they will do with it...

---

### Post by jimi_hendrix on 2008-09-07
i thought mindori was a joke os where they put people in a room to test it and it was really vista

---

### Post by LaRoza on 2008-09-07
> **jimi_hendrix said:**
> i thought mindori was a joke os where they put people in a room to test it and it was really vista

First, there is a "shift" key. In the Latin alphabet, certain words should be capitalised. It really helps for readability.

Second, [Midori]("http://en.wikipedia.org/wiki/Midori_(operating_system)") is the name, and it isn't the same as **The Mojave Experiment**.

---

### Post by jimi_hendrix on 2008-09-07
> **LaRoza said:**
> First, there is a "shift" key. In the Latin alphabet, certain words should be capitalised. It really helps for readability.

whats latin...while were at it whats capitalised? </joke>
> 
Second, [Midori]("http://en.wikipedia.org/wiki/Midori_(operating_system)") is the name, and it isn't the same as **The Mojave Experiment**.

thank you

---

### Post by LaRoza on 2008-09-07
> **jimi_hendrix said:**
> whats latin...while were at it whats capitalised? </joke>


[http://en.wikipedia.org/wiki/Latin_alphabet](http://en.wikipedia.org/wiki/Latin_alphabet)

[http://en.wikipedia.org/wiki/Capital_letters](http://en.wikipedia.org/wiki/Capital_letters)

---

