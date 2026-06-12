---
title: "Multi version"
date: 2011-06-19
forum: Programming Talk
---

### Post by sergio.milici on 2011-06-19
Hello, i am developing a program that it has to run in a lot of ubuntu versions. The question is: Do i have to compile my program in every different version, or a can compile it saticly? How can i resolve diferences between version of libstdc++ if it's not compiled staticly?
Any help would great!!

Thanks

---

### Post by Petrolea on 2011-06-19
I think that porting C++ programs between versions of Ubuntu is not a big problem, not sure for that lib tho. 

For the library, you could request the desired version of it or have it included with the program or make the auto-install / auto-update of it.

---

### Post by cgroza on 2011-06-19
I think if the library does not change it's API between versions you should be fine.

---

### Post by Simian Man on 2011-06-19
If it's open source, then just release the source code and let users figure it out.  Distributing binary code on Linux is way more trouble than it's worth.

---

### Post by JupiterV2 on 2011-06-19
> **sergio.milici said:**
> Hello, i am developing a program that it has to run in a lot of ubuntu versions. The question is: Do i have to compile my program in every different version, or a can compile it saticly? How can i resolve diferences between version of libstdc++ if it's not compiled staticly?
Any help would great!!

Thanks

You can easily statically link libstdc++ into your program. I won't get into the details but there is a holy war raging in the background about dynamic vs. static linking. I see the merits of both. If you choose the static route, then you may want to consider looking at the Go language.

As for dependencies, you will need to determine whether you want to support future, past or both, Ubuntu versions. If all you want is handle the future then you likely need not worry about the API changing, or at least, that it won't be backwards compatible. I'm not saying it WON'T change, just unlikely in the near future. If you want to support previous versions, you will need to determine what is the minimum version of libstdc++ you wish to link against. Then, in your Debian control file stipulate that you want >= than that version. 

The cut and dry: If you want guarantee maximum compatibility you should statically link libstdc++ with the -static (gcc) flag and accept that it will be at the cost of binary size. For stability/longevity, this could be a very minor cost.

In the past, I have always been pro-dynamic linking (and I refer to compile-time linking not run-time dynamic loading) but now I am starting to see/understand/accept the opposing view.

---

