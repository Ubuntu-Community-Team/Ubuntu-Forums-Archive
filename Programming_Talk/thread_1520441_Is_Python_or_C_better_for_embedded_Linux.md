---
title: "Is Python or C better for embedded Linux?"
date: 2010-06-29
forum: Programming Talk
---

### Post by stirbad on 2010-06-29
Hi all,

I'm going to be coding for an embedded system and was wondering which of the two languages (C and Python) would be better. Obviously, I'm going to want something that's not very resource-intensive so I'm leaning towards C, but searching on these forums has led me to believe that many of you prefer coding in Python when using Ubuntu.

I also came across a language called Lua that's been compared to Python when coding for embedded systems, and it seems Lua is much less resource-intensive, although it also seems to be a weaker language. Does anyone have experience with Lua? Is it difficult to learn, given that I know C and Python?

---

### Post by Tony Flury on 2010-06-29
It all depends I think if your embedded system has a native support for python - or a cross compiler for C - you can code in any language you want - the key is getting the code to run on your embedded system.

I would imagine that Python (assuming you can run python on your target system), would be more resource intensive (depends what you are doing though).

---

### Post by stirbad on 2010-06-29
> **Tony Flury said:**
> It all depends I think if your embedded system has a native support for python - or a cross compiler for C - you can code in any language you want - the key is getting the code to run on your embedded system.

I would imagine that Python (assuming you can run python on your target system), would be more resource intensive (depends what you are doing though).

The board that the program will be running on will interface with a camera and possibly some sort of wireless data-sending peripheral. It will be working with a lot of data coming in from the camera, so I'm limited in memory. I also agree that Python would be more resource-intensive, but because I'm limited in memory, I'm a bit paranoid about messing up my memory management in C and would rather have Python deal with that stuff for me.

---

### Post by Simian Man on 2010-06-29
"Embedded system" is way to vague a term for people to give you useful replies.  What is this embedded system exactly?  A micro-controller of some kind?  An evil robot?  Until we know, it's impossible to say.

<eidt> Nevermind you just said.

Likely C will be your only real option for interfacing with your devices.  From there, it really depends how much work you need to do.  If it's not too much, writing the rest of the code in C will likely be easiest.  If it's a lot, it may be easiest to do it in a higher level language.  For that purpose I'd recommend Lua because it is extremely easy to interface with C which you'll probably need to do.

---

### Post by soltanis on 2010-06-29
Really depends on how much memory you're talking but if you're operating in a really memory strict environment, I would opt for C over Python, especially since Python is not a very optimized system nor is it targeted at resource-restricted environments.

EDIT: I assume by the way that because you said "embedded Linux" that your system is running a Linux kernel, of course that says nothing about the binary utilities that may be present on the system. You also did mention Lua; it's not "weaker", it just has less standard libraries but it is much easier to embed. If you have binutils present (in the form of BusyBox, probably) bear in mind that you will have access to an sh-compatible shell and awk.

---

### Post by stirbad on 2010-06-29
I believe that the libraries needed to interface with the camera can be directly imported if coding in C, so I'm definitely favoring it. Again, my only quirk with choosing C over Python is that I would have to pay much more attention to memory management, but I suppose it's a tradeoff I'll have to deal with.

As of now, I'm not too sure of how much programming I'll need to do. I have absolutely no experience with Lua and hadn't even heard of it until today...will it be difficult to pick up? I'd code everything in C/Python if it were up to me, but I'm willing to pick up Lua if it's that much more efficient in embedded Linux.

---

### Post by soltanis on 2010-06-29
Memory management isn't a particularly hard concept. You acquire memory when you need it and then release it when you're done using it. The only thing you need to remember is that if you're setting aside a chunk of memory you need to store it in a pointer and remember to free it later.

...and set your pointers to null when not using them, and do your pointer arithmetic correctly, and don't try to double free memory.

That is all.

---

### Post by phrostbyte on 2010-06-29
> **soltanis said:**
> Memory management isn't a particularly hard concept. You acquire memory when you need it and then release it when you're done using it. The only thing you need to remember is that if you're setting aside a chunk of memory you need to store it in a pointer and remember to free it later.

...and set your pointers to null when not using them, and do your pointer arithmetic correctly, and don't try to double free memory.

That is all.

Except when you have structs with pointers in them which point to other structs that are pointed to by more then one struct. Oh all the various types have different sizes. :)

You can write a reference counter in this situation, but this will not solve memory fragmentation.

---

### Post by stirbad on 2010-06-29
> **soltanis said:**
> Memory management isn't a particularly hard concept. You acquire memory when you need it and then release it when you're done using it. The only thing you need to remember is that if you're setting aside a chunk of memory you need to store it in a pointer and remember to free it later.

...and set your pointers to null when not using them, and do your pointer arithmetic correctly, and don't try to double free memory.

That is all.

That's another quirk I have with C and memory management: I'm paranoid about messing up my pointers, and I can't even remember what a double asterisk does at the moment. However, I have done it before and I'm sure that an hour or two of tinkering around will be more than enough time to re-learn it all.

Another thing: I will most likely have to perform mathematical operations on the data gathered by the camera, although I'm not sure how complicated the math needs to be right now. If the math ends up having to be very complicated, which of the languages (C, Python, Lua) would handle the operations best?

---

### Post by stirbad on 2010-06-29
> **phrostbyte said:**
> Except when you have structs with pointers in them which point to other structs that are pointed to by more then one struct. Oh all the various types have different sizes. :)

You can write a reference counter in this situation, but this will not solve memory fragmentation.

This also worries me. However, is there ANY language that deals with fragmentation in a spiffy way? If I'm not mistaken, Java may have a good shot at it, but I'm certainly not going to use Java for this project since it's rather resource-intensive.

---

### Post by soltanis on 2010-06-29
I mean, just how much memory are you going to be allocating here? What kind of math are you doing with the camera input?

---

### Post by stirbad on 2010-06-29
> **soltanis said:**
> I mean, just how much memory are you going to be allocating here? What kind of math are you doing with the camera input?

I'm restricted to 2 GB of RAM, and ideally, the final product will not be hooked up to a HDD so that's all I have to work with. The images captured by the camera would regularly take up way more than 2 GB, so I need to perform operations on the data and dump whatever data I don't need. That said, I suspect I won't have to do math beyond basic trigonometry, but anything up to Fourier transforms is a possibility.

---

### Post by soltanis on 2010-06-29
Oh, okay. Well first, with 2GB of memory, Python is totally a possibility, but not very fast or smart for math-intense operations, unless you want to write those in C, the rest of the code in Python, and then SWIG them together.

---

### Post by splicerr on 2010-06-29
Why not use Vala? You'll get all the benefits of using a higher level language than C -- including reference counting so you don't have to worry about memory management  -- yet it compiles to C code so you don't have the burden of a big runtime or interpreter.

---

### Post by stirbad on 2010-06-29
> **splicerr said:**
> Why not use Vala? You'll get all the benefits of using a higher level language than C -- including reference counting so you don't have to worry about memory management  -- yet it compiles to C code so you don't have the burden of a big runtime or interpreter.

I looked up Vala, and although it seems promising, the fact that the compiler is somewhat incomplete makes me wary of it.

I think that I'm going to stick with C, since there's no real drawback in using it. It'll probably make my life a lot easier when trying to interface with the camera, too. Thanks for all of your help! Please don't hesitate to provide additional comments if you think I'm digging a hole for myself, haha.

---

### Post by soltanis on 2010-06-29
Writing in C is always digging a hole for yourself, lol.

---

