---
title: "Q about distribiting software made with GCC"
date: 2008-08-02
forum: Programming Talk
---

### Post by NovaAesa on 2008-08-02
I'm taking a course at Uni where we are leaning C++, and we are using the GCC for our labs and for assignments. The lecturer said something strange about the GCC though. I'm just wanting to know if what he said is right or not before I question him about it.

He said that because the GCC is released under the GPLv2, we would only be able to distribute code created with it under the GPL as well (i.e. it can't be used commercially, at least in the traditional sense). Is this right? I would have though you could do anything with the code you created. The only thing I can think of is if maybe using include pre compiler directives could include GPLed code.

Any thoughts on this?

---

### Post by scourge on 2008-08-02
Your lecturer is totally wrong. First of all, GCC is also licensed under the Lesser General Public License ([http://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License](http://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License)). And even if it wasn't, the license wouldn't apply to binaries created with the software, as long as no parts of GCC were distributed with said binaries.

---

### Post by techmarks on 2008-08-02
That would only be true if you statically link to a library that is licensed under the GPL in that case your program must also be released as GPL.

However if you just use GCC to compile a program that doesn't statically link to any GPL code you are free to license your software as you wish.

If what your lecturer is saying were true, Apple and Redhat and other companies would be in trouble right away.

If you want to get away from compiling with a FSF compiler at all, you can use pcc, but it only compiles C code.

---

### Post by NovaAesa on 2008-08-02
Yeah, it's that static linking that I'm worried about. For example, I use lots of:

#include <istream>

and that kind of thing pretty often. So are these considered "modules" or part of the compiler?

---

### Post by techmarks on 2008-08-02
> **NovaAesa said:**
> Yeah, it's that static linking that I'm worried about. For example, I use lots of:

#include <istream>

and that kind of thing pretty often. So are these considered "modules" or part of the compiler?


That's part of the Standard C++ Library, in other words part of the compiler.

If you were using source code or a library that is not part of the compiler and that library or source code is licensed under GPL and you link statically to that code, you must then license your own program as GPL.

You can still use GPL code without releasing your program as GPL, but then you cannot link to that code statically, and must link to it dynamically only.

---

### Post by nvteighen on 2008-08-02
> **techmarks said:**
> That's part of the Standard C++ Library, in other words part of the compiler.

If you were using source code or a library that is not part of the compiler and that library or source code is licensed under GPL and you link statically to that code, you must then license your own program as GPL.

You can still use GPL code without releasing your program as GPL, but then you cannot link to that code statically, and must link to it dynamically only.
There are some problems regarding dynamic linking and the GPL. Traditionally, if you dynamic link to GPL code, your code is considered a derivative work and is forced to be GPL too.

Why? Because when you #include, the preprocessor puts code that's not under your copyright.

But, the C++ Standard Library is LGPL, which allows to be linked by programs either free or proprietary. The requirement is that you have to allow people access to the **library's** source (see the license for this; either v2.1 and v3 are stored in /usr/share/common-licenses/).

None of both apply if you only distribute your own source code and you tell the user to compile. Why? Because the preprocessor hasn't been run... What happens if you link without including a header is not clear to me, but is very improbable to occur.

---

### Post by techmarks on 2008-08-02
> **nvteighen said:**
> There are some problems regarding dynamic linking and the GPL. Traditionally, if you dynamic link to GPL code, your code is considered a derivative work and is forced to be GPL too.



I think you are probably right, and dynamic linking of GPL code is also a derivative work.

Of course this doesn't apply to the Standard Library.

If the OP wants freedom as to how he licenses his software, it's best he stay away from linking statically or dynamically to GPL source code or libraries altogether.

---

### Post by nvteighen on 2008-08-02
I forgot:

It doesn't matter which license gcc/g++ has. Yes, the compiler is GPL, but what your doing with it is just using it... for what is meant for :). The output object code is not linked in anyway to the compiler.

The same applies for the Linux kernel: the kernel is GPL, but you can develop any non-free application in a Linux system, because your program will just run over the kernel, it doesn't include any part of it (unless you explicitly do that, of course).

In summary: copyright applies only to the work. Whenever you take a part of that work, you have to ask for permission... but not when you use it.

---

### Post by techmarks on 2008-08-02
The GPL is a poor license because it is so complex.

The Linux kernel is GPL so that any code statically linked to the kernel must be covered by GPL.

Companies that develop binary drivers for the kernel get around this by dynamically linking loadable kernel mdules.

I don't see why dynamically linking to a GPL code should make that program GPL.

I undestand why static linking to GPL code makes your code GPL.

But dynamic linking?  you are not including that code in your executable and you are not modifying it either, so it seems it should not become GPL.

But I'm not completely certain, you'll probably have to discuss with a lawyer that is well versed in GPL/open source/patent law.

---

### Post by nvteighen on 2008-08-02
Oh... I supposed we were talking about libraries...

If you executable linked somehow to another GPL executable, then nothing should occur because you're not using the GPL code anywhere in yours.

The problem arrives with GPL libraries, which make you include the header file and thus, you're including code that's not yours.

OK, I was mistaken: the C++ Standard Library is GPL + linking exception:
```

// As a special exception, you may use this file as part of a free software
// library without restriction.  Specifically, if other files instantiate
// templates or use macros or inline functions from this file, or you compile
// this file and link it with other files to produce an executable, this
// file does not by itself cause the resulting executable to be covered by
// the GNU General Public License.  This exception does not however
// invalidate any other reasons why the executable file might be covered by
// the GNU General Public License.

```

So, if you just use the library as a dynamic or static library, you are free to place your terms. The last line seems just to be a preemptive protection.

The obvious question to the GNU guys: Why haven't you used LGPL instead, as in the C Standard Library??

---

### Post by NovaAesa on 2008-08-02
Okay, so my lecturer was wrong on a technicallity? Is this what you are saying?

---

### Post by LaRoza on 2008-08-02
Just distribute the source, and let the user compile.

---

### Post by pmasiar on 2008-08-03
> **techmarks said:**
> The GPL is a poor license because it is so complex.

Compared to what? Ever tried to read MSFT EULA?

GPL is as it is because it gives user important rights (missing in longer EULA).

> The Linux kernel is GPL so that any code statically linked to the kernel must be covered by GPL.

How is Linux kernel relevant to OP's code?

Whole point of using GCC (including standard libraries) is to create code which you can use as you wish. Only if you use some non-standard libraries you have to check the license of those libraries how you can use them, but many are under LGPL to allow also proprietary use.

BTW OP repeats common error (deliberately placed by apologists of proprietary software), mistaking commercial and proprietary code. GPL does not prevent you from selling your code, it just forces you to give sources to recipients of your binaries (including 4 freedoms). Emacs was sold as Free software (on tapes), only with internet became omnipresent, distribution of Free software for no charge ("free as beer") become possible, but it is irrelevant to 4 freedoms of Free software.

GPL just prevents you to make changes to someone else's GPLed code and distribute binaries without changed sources (even for free), that's all. You can use GPL programs for whatever reason, and do whatever you want with your own code: distribute it with whatever license you want, or sell only binaries.

---

### Post by NovaAesa on 2008-08-03
This isn't really a situation where I need to distribute anything as such, it was just something that my lecturer said that struck me as odd. He said words to the effect of "the GCC is useless for commercial software because you have to distribute the source code when you distribute binaries made with it." I found this somewhat odd, that the GPL was taking away your freedoms... so I've been questioning it in my own mind.

---

### Post by NovaAesa on 2008-08-03
> **pmasiar said:**
> 
BTW OP repeats common error (deliberately placed by apologists of proprietary software), mistaking commercial and proprietary code. GPL does not prevent you from selling your code, it just forces you to give sources to recipients of your binaries (including 4 freedoms). Emacs was sold as Free software (on tapes), only with internet became omnipresent, distribution of Free software for no charge ("free as beer") become possible, but it is irrelevant to 4 freedoms of Free software.

I see what you are getting at. I meant commercial in the traditional sense (e.g. released under a commercial license, a bit like Windows). I'll have to be a bit more careful with wording in the future though :)

---

### Post by pmasiar on 2008-08-03
> **NovaAesa said:**
> my lecturer said that struck me as odd. He said words to the effect of "the GCC is useless for commercial software because you have to distribute the source code when you distribute binaries made with it." 

Your lecturer is clearly not a legal expert, but as I said this misunderstanding is deliberately placed by marketoids and repeated by clueless journos, so it is common mistake, not in bad faith from him.

[http://en.wikipedia.org/wiki/GNU_Compiler_Collection](http://en.wikipedia.org/wiki/GNU_Compiler_Collection)
"GCC ... is widely deployed as a tool in commercial, proprietary and closed source software development environments". You may even consider to mention true legal status of GCC to your lecturer, most people repeat that lie ("GPL is cancer") from lack of knowledge, not maliciously.

---

### Post by dwhitney67 on 2008-08-03
> **NovaAesa said:**
> I'm taking a course at Uni where we are leaning C++, and we are using the GCC for our labs and for assignments. The lecturer said something strange about the GCC though. I'm just wanting to know if what he said is right or not before I question him about it.

He said that because the GCC is released under the GPLv2, we would only be able to distribute code created with it under the GPL as well (i.e. it can't be used commercially, at least in the traditional sense). Is this right? I would have though you could do anything with the code you created. The only thing I can think of is if maybe using include pre compiler directives could include GPLed code.

Any thoughts on this?
You either listened incorrectly or your professor is wrong.

---

### Post by NovaAesa on 2008-08-03
> **pmasiar said:**
> You may even consider to mention true legal status of GCC to your lecturer, most people repeat that lie ("GPL is cancer") from lack of knowledge, not maliciously.
Yeah, I'm pretty sure it wouldn't have been maliciously, because he's a Linux user himself (I think he is anyway, he's always talking about how great emacs is). I'll post a question about it on that subject's discussion board on the uni website.

---

### Post by LaRoza on 2008-08-03
> **NovaAesa said:**
> Yeah, I'm pretty sure it wouldn't have been maliciously, because he's a Linux user himself (I think he is anyway, he's always talking about how great emacs is).

Does he use Linux or Emacs? Or does he dual boot them?

---

### Post by NovaAesa on 2008-08-03
> **LaRoza said:**
> Does he use Linux or Emacs? Or does he dual boot them?

LOL

Yes, I realise that my line of (pseudo) argument there is somewhat flawed. It's not a far stretch to say that someone who recommends Emacas is probably either a Unix or Linux user though. And yes, I realise that Emacs can run on Windows, but Emacs seems like something you would more probably run into in the "*nix" world.

---

