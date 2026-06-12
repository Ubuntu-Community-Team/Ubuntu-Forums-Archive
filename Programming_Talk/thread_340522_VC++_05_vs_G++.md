---
title: "VC++ 05 vs G++"
date: 2007-01-17
forum: Programming Talk
---

### Post by Lster on 2007-01-17
Im just wondering what everyone else who have used Visual C++ (2005) and G++ (4.1) found in performance difference.

Im just interested as Linux always seems to be fast and Windows always seems a bit sluggish.

Thanks,
Lster

---

### Post by Wybiral on 2007-01-17
I think it's more of an issue of how the code is written. Both of them have optimization features, but neither are specially OPTIMIZING compilers and hence will not make THAT big of a speed difference. I've seen people argue both sides, but what it basically comes down to is this... If the code is standard C++, it will work on both compilers, and there probably won't be a big difference in the assembly state of the code. So, I could be wrong but code matters more than the compiler, so keep it standard and you can test it on both... But at least you don't have to pay to test it on GCC!

---

### Post by jblebrun on 2007-01-17
> **Lster said:**
> Im just wondering what everyone else who have used Visual C++ (2005) and G++ (4.1) found in performance difference. I have tried a few benchmarks, ending with G++ always slaughtering Visual C++, but have you guys noticed any difference?

Im just interested as Linux always claims to be fast and Windows always seems a bit sluggish.

Thanks,
Lster

What are the benchmarks that you are using to test? How are you measuring performance? Are you checking the timing of a fixed, known calculation, or the run-time of an entire program? Can you post your numbers here?

---

### Post by skeeterbug on 2007-01-17
> **Wybiral said:**
> I think it's more of an issue of how the code is written. Both of them have optimization features, but neither are specially OPTIMIZING compilers and hence will not make THAT big of a speed difference. I've seen people argue both sides, but what it basically comes down to is this... If the code is standard C++, it will work on both compilers, and there probably won't be a big difference in the assembly state of the code. So, I could be wrong but code matters more than the compiler, so keep it standard and you can test it on both... But at least you don't have to pay to test it on GCC!

At least you get what you pay for ;)

Anyone who tries to bash VS 2005 has never obviously used it for *real* development work day to day.

---

### Post by jblebrun on 2007-01-17
> **skeeterbug said:**
> At least you get what you pay for ;)

Anyone who tries to bash VS 2005 has never obviously used it for *real* development work day to day.

Anyway, you can get Visual Studio Express for free, now.

---

### Post by Wybiral on 2007-01-17
Yeah... But the issue here was about speed, and a compiler isn't going to do much more than another compiler can when it comes to speed. It depends on the code, it's that simple.

There are special optimizing compilers, but Vc++ and Gcc were not specially designed to be excellent optimizers... There's only so much a compiler can do, it really depends on the code.

---

### Post by std on 2007-01-19
> **Wybiral said:**
> Yeah... But the issue here was about speed, and a compiler isn't going to do much more than another compiler can when it comes to speed. It depends on the code, it's that simple.

There are special optimizing compilers, but Vc++ and Gcc were not specially designed to be excellent optimizers... There's only so much a compiler can do, it really depends on the code.

Actually, the optimization in both g++ and vc++ is quite good. I haven't measured it against intel's compilers (not against any recent version anyhow, the last time I tried was years ago when gcc was somewhere at 2.something) -- but there are some other ways to test. There's a clear performance gain (you can sense it even without benchmarking) if you look at the difference between compiling with -0 and -3 in g++ for example.

Of course, a compiler will never be a good substitute for good code -- no optimizing compiler is a match for human stupidity -- but compile-time optimization has gone quite far in the last 20 years. The closes example in my mind now is LISP, which is so much faster than it used to be, and not only due to the development of superior processing power.

As for the question here, as far as I know (I can't give any relevant quote though) the performance of g++ is close enough to that of the vc++ compiler for the "average code". 

Testing compiler optimization capabilities is not something to be taken too lightly. I'd guess that it would require running all tests on Windows, and I don't know what's the status of a gcc 4.1 port to Windows (is there any?). Lster, I'd really want to see the tests you ran, too, I've never seriously though about comparing the two in terms of performance.

---

### Post by DoktorSeven on 2007-01-19
Given that I've had perfectly legal, standards-compliant C and C++ not compile under VC++ (2005) while compiling just fine in gcc/g++, I'd say VC++ isn't a very good C/C++ compiler.

---

### Post by hod139 on 2007-01-19
> **DoktorSeven said:**
> Given that I've had perfectly legal, standards-compliant C and C++ not compile under VC++ (2005) while compiling just fine in gcc/g++, I'd say VC++ isn't a very good C/C++ compiler.
I don't think this is a good argument, I've had perfectly legal standards-compliant C/C++ code not compile with gcc/g++ but compile fine in Visual Studio.  The newest version of Visual student significantly increased standards compliance.

Neither compiler is perfect, but trying to decide which one is better will probably become a flame war.

---

### Post by blanky on 2007-01-19
Wow, I'm amazed at all of your replies. I'm surprised to not see much bias in any of your posts, all which I really respect. Typically when you ask people they'll just bash it because it's Microsoft.

I recently got Visual Studio 2005 Standard for free from Microsoft (*Haha, no I don't work for them*), and I really like the IDE but that's probably because I'm used to it, but I understand this isn't a thread about IDE's but rather what compiler has better 'performance' ? I actually wouldn't know as I rarely do anything that would really make a difference. However, I would figure that it also matters on other things, not just the code or the optimization, but hey I wouldn't know.

But it's nice to see a mature discussion every once in a while :)

---

### Post by lnostdal on 2007-01-19
> **std said:**
> I'd guess that it would require running all tests on Windows, and I don't know what's the status of a gcc 4.1 port to Windows (is there any?).

Seems latest Windows port of MinGW is 3.4.x. I don't know if there are any reasons 4.x hasn't been ported yet; maybe something is mentioned on the mailing-list -- or maybe no one has bothered with it yet.

Another alternative -- which can be easier when compiling free GNU software is Cygwin. I'm thinking especially of the build-procedure which amongst other things sometimes depends on standard *nix-tools which are not present under Win32.

As for optimizing; there can be a large difference between compiling the same software (code) in non-optimized mode and optimized mode!
[http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html) (applies to both GCC and it's Win32-port MinGW). 

Not really related, but in Lisp one can also optimize by adding declarations directly in parts of the code. This allows one to adjust the generality of parts of the code or just optimize parts of it; quite unique -- I think. This is useful as a last step in a development-cycle, and has large consequences:
[http://groups.google.com/group/comp.lang.lisp/msg/2bbc5591ad786777](http://groups.google.com/group/comp.lang.lisp/msg/2bbc5591ad786777) .. 135 lines of ASM (_not_ including the calls to external code which probably accounts to thousands of ASM-instructions) reduced to 6 inline simple instructions! :)

---

