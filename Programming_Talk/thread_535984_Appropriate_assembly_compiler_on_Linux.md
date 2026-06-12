---
title: "Appropriate assembly compiler on Linux"
date: 2007-08-27
forum: Programming Talk
---

### Post by xlinuks on 2007-08-27
What assembly compiler would be best for me (a newbie) to use?
gas - since gcc uses it, AT&T style
nasm - Intel systax, looks like doesn't get development at the moment

I would happily choose NASM/FASM, but I'm not sure if I can use it to create gcc inline assembly instructions, and if so, ain't it better start with and to stick "gas"?

---

### Post by LaRoza on 2007-08-27
> **xlinuks said:**
> What assembly compiler would be best for me (a newbie) to use?
gas - since gcc uses it, AT&T style
nasm - Intel systax, looks like doesn't get development at the moment

I would happily choose NASM/FASM, but I'm not sure if I can use it to create gcc inline assembly instructions, and if so, ain't it better start with and to stick "gas"?

My wiki has books and tutorials for Assembly programming in Linux. 

The syntax is different, as you know, but the basics are the same, so learning more than one would not be that difficult. I would (actually, I did) start with NASM.

There is another assembly language, that has a C like syntax, specifically for beginners, but I wouldn't use it, because NASM isn't that difficult.

---

### Post by xlinuks on 2007-08-27
Can I have a look at your wiki? I couldn't find a reference to it.
As to the 'same basics' -  true. I use Java for my projects, so if I write something incorrect Java tells it to me in a user/programmer friendly way, be it compile or runtime. In assembly the compiler (quitely) lets you shoot yourself in the foot, if you make a mistake you can expect it to hang even the OS, thus I'm trying to be very precautious with assembly mistakes. Thus the whole point is to avoid another possible type of mistakes I would make: for example passing a pointer instead of a value and other hard-to-find bugs.The GCC compiler checks the types you pass as parameters, but the gas/nasm don't care at all (which is understandable).

---

### Post by LaRoza on 2007-08-27
> **xlinuks said:**
> C
The GCC compiler checks the types you pass as parameters, but the gas/nasm don't care at all (which is understandable).

Sorry, it is the first link in my sig, look in the "Library".

With assembly, you have the power to directly manipulate resources that other languages handle silently. Java will not allow you to directly access the memory address, while C does.

With Assembly, passing "pointer" and "values" is not something you will do by accident. 

With Assembly, you will get a good understanding of how programming actually works, but you will almost never use Assembly, and when you do, it probably won't be by itself.

---

### Post by LaRoza on 2007-08-28
After reading the posts over again, you might be looking for this:

[http://www.computer-books.us/assembler_6.php](http://www.computer-books.us/assembler_6.php)

I just resumed my studing of Assembly, and rethought my earlier post about NASM. NASM is slightly easier to read, but the above language, will do what you wanted exactly.

(The above link is in my wiki, I just posted it here to make things easier, and I reread it last night)

---

### Post by Wybiral on 2007-08-28
> **xlinuks said:**
> What assembly compiler would be best for me (a newbie) to use?
gas - since gcc uses it, AT&T style
nasm - Intel systax, looks like doesn't get development at the moment

I would happily choose NASM/FASM, but I'm not sure if I can use it to create gcc inline assembly instructions, and if so, ain't it better start with and to stick "gas"?

The reasy NASM doesn't get much development is because it's basically done... It's just an assembler.

As far as inline assembly with NASM... No, not possible (at least not with the GCC compiler). But you can still develop libraries for C in NASM and link to them.

Either one will do... It's just assembly, if you get used to one they are both the same, just different ways of typing it.

I personally prefer NASM, but learn GAS is good too because it helps you understand how GCC works (which makes you look at C much different).

---

### Post by xlinuks on 2007-08-31
LaRoza, I'm currently learning Assembly from the book on your site "Programming From The Ground up". By the time I'm at page 63 and I'm positively impressed by the author's ability to explain difficult things in such an understandable fashion. I'm also impressed that it's free and teaches exactly what I need: the "native Linux" assembly compiler (as). Looks like I finally understood how the stack works! It took me about 4 times to re-read the section explaining it. IMHO a few pictures of how the bytes are pushed/popped in/from the stack would be good for people like me who rather understand from viewing than reading :)

@Wybiral as to the thing that NASM might not get development any more - I guess you're right - it's "just" an assembler and as such there ain't much to do (although it's impossible for me for the time to implement one:)  )

As to "almost never using assembly" you're prolly right, but I like it so far, and for it creating very small binaries which therefore load and execute lightening fast.

Thanks both!

---

### Post by Wybiral on 2007-08-31
> **xlinuks said:**
> (although it's impossible for me for the time to implement one:)  )

You would actually be surprised by just how simple an assembler is... All it does is convert mnemonics like "mov" and "add" to their proper byte in machine code. Some subtle differences with registers and addresses, but it's all very simple really.

Compilers are MUCH more complex then assembler since assembly is just textual machine code.

---

### Post by pmasiar on 2007-08-31
> **xlinuks said:**
> As to "almost never using assembly" you're prolly right, but I like it so far, and for it creating very small binaries which therefore load and execute lightening fast.

Even if you later will program in C, after your immersion in ASM you will forever "feel" how your C code will be translated to CPU instructions. Because after all, any code needs to be translated down into CPU instructions, and rest in just layers of abstraction which we add to hide details, so we can solve more complicated problems. It is not easy way, but certainly it is worth to know C and even ASM ... only don't start with it, learn first basics (variable, loop, function, parameters) in something simpler like Python :-)

After you know ASM, C is just convenient thin abstraction over ASM. 

If you are fascinated in world close to hardware, you might be also interested in Forth: very flexible high-level language which can seamlessly incorporate functions written in assembly. Google has the links. :-)

---

