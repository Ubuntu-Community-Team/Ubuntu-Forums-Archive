---
title: "What does libc do?"
date: 2008-03-25
forum: Programming Talk
---

### Post by nvteighen on 2008-03-25
A little newbie question: what's exactly libc's function when running compiled C code? I know what a shared library is and does, but I don't see which is the point of it if you're #including headers which define the routines you need.

Or does C use runtime libraries as, say, Java or Visual Basic executables?? Maybe I'm missing something...

Please, could you clarify me a bit on this point?

---

### Post by CptPicard on 2008-03-25
Well, you don't understand what a shared library does. :)

When you #include, you just essentially tell the compiler what the library looks like "from the outside" so that your binary knows how to communicate with it. You aren't including any of the actual code into the binary, which would be static compilation. The shared library is linked with your binary when you load your program, so in some sense your idea of "runtime libraries" is more correct here.

---

### Post by nvteighen on 2008-03-25
> **CptPicard said:**
> Well, you don't understand what a shared library does. :)

So it seemed! :)

> When you #include, you just essentially tell the compiler what the library looks like "from the outside" so that your binary knows how to communicate with it. You aren't including any of the actual code into the binary, which would be static compilation. The shared library is linked with your binary when you load your program, so in some sense your idea of "runtime libraries" is more correct here.

OK, I see. So, in order to run the program you need to have libc.so.6 or something equivalent installed at /lib. But, why if stdlib.h and stdio.h point both to the Standard Library, so there isn't just one header file?

And just for curiosity, is there a way in gcc to link statically?

---

### Post by CptPicard on 2008-03-25
> **nvteighen said:**
> But, why if stdlib.h and stdio.h point both to the Standard Library, so there isn't just one header file?

Well, I suppose you could have one humongous header, but it would just be... big. I'd suppose the reason is simply one of modularisation and manageability :)

> And just for curiosity, is there a way in gcc to link statically?

Yes. I think the gcc -static flag did that, but read the manpage (I don't really code seriously in C)...

---

### Post by nvteighen on 2008-03-25
> **CptPicard said:**
> Well, I suppose you could have one humongous header, but it would just be... big. I'd suppose the reason is simply one of modularisation and manageability :)



Yes. I think the gcc -static flag did that, but read the manpage (I don't really code seriously in C)...
Then, if I use stdio.h, I'm just giving access to a part of the shared library and not the whole. Well, it's an intelligent approach... (I'm liking C even more!).

I've read the man page on the -static flag and it seems that it's used only to prevent linking if your system supports dynamic linking. If your system doesn't support it, it has no effects.

Thanks for answering my doubts!

---

### Post by Zwack on 2008-03-25
The Standard C library is defined in the C standard... but there is no reason why the different headers have to implement functions in the same library.  So stdio.h and stdlib.h could define functions that are in different libraries...  The standard doesn't (as far as I know) state explicitly how many libraries should be there.  You can statically link or dynamically link, but you use the same headers for both.

I hope that this helps,

Z.

---

