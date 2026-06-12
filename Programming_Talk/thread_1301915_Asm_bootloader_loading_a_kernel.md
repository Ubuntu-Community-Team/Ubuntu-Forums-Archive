---
title: "Asm bootloader loading a kernel"
date: 2009-10-26
forum: Programming Talk
---

### Post by cam888 on 2009-10-26
So i have a basic bootloader setup, written in asm, and I have a basic kernel written that just prints things to the screen, but I can't find anything telling me how to load the kernel from the bootloader. Does anyone have any ideas?

Thanks 
Cameron

---

### Post by SunSpyda on 2009-10-26
First you will need to work out if you are gonna stick with 16bit real mode, or shift up to 32/64bit protected mode.

32/64bit protected mode is a pain due to drivers. In 16bit real mode, the BIOS can do a lot for you, but a modern, sophisticated OS should be 32/64bit protected based.

---

### Post by cam888 on 2009-10-26
If I were to write the kernel (mostly) in C, will it matter what mode I'm in? Because I would prefer to go into 32 bit mode, but I have also not seen any example code for this.

(I'm new to this, as you may be able to tell, thanks for the help)

---

### Post by SunSpyda on 2009-10-27
I did this a long while back, so I may have forgotten or mistake certain aspects, so sorry in advance for any unbelievable mistakes I may make :p

The BIOS uses finds the bootloader (a flat binary) on the first 540k of the boot disk (not sure if thats a restraint anymore), & executes it. The bootloader can then boot the OS which itself can be 32/64bit protected mode. But as soon as you do that, you will need to write drivers for the H/W, since the BIOS can no longer operate the H/W for you. The BIOS is a simple 16bit thing, so it can't operate your H/W in a 32/64bit environment.

The bootloader is a ASM job, that NASM, FASM, SolASM & a few others can do. So can GNU, but I hear some linker magic is needed. The OS can be mostly written in a higher level language like C/C++. You can't run languages like Python, Java, .NET or whatever else until you get a operating kernel that can execute programs in a multiprogramming system, & you have compiled the runtimes into the necessary executable.

You can rip a lot of others work. Like using the ELF format, or GRUB rather than your own bootloader, etc.

If you want to go into higher H/W specs like higher than 16bit real mode, investigate drivers. This path is painful, & requires a LOT of knowledge. Generic drivers are a obvious first solution.

My opinion? Either make a 16bit OS & take full advantage of the BIOS, & live with the evil unprotected mode restraints. Think about DOS - amazing stuff was done with that, & that was 16bit. The other solution is to take a existing 32/64bit protected mode kernel & build off it. Like BSD, Linux, OpenSolaris etc.

Remember, it's a long time since I did this stuff, so there will be embarrassing inaccuracies in the above stuff :/

---

### Post by grayrainbow on 2009-10-27
In general the biggest issues with OS are memory, scheduler, and of course hardware recognition and addressing. That's the stuff that every manufacturer try to provide(when it comes to embeded systems). So 32/64 bit wont matter much, its just better to go 64 couse that's the future :)

Anyway. In most height level view, bootloader doesn't differ from OS loader(that thing which run when you start some program). Load image in memory, and set instruction pointer somewhere in it. Well, becouse of multytasking modern OSs doesn't run programms exactly that way, but since after bootloader there's only one program(the OS itself) it's the simplest way. If you want more fancy stuff consider implementing argument passing protocol from loader to kernel.

P.S. Btw, there's some grate sites on that matter. Most notably kernel.org. tldp.org. Or BSD if you like more academic(which usually mean more readable code, and not so well working, never try to install BSD on laptop) aproach.

---

### Post by cam888 on 2009-10-28
Thanks for all the advice everyone, this is a very steep learning curve :p I have been looking at bootloaders and kernels and pmode solidly for the last two days and I'm still pretty vague on how to do things... 

Anyway, if I did stay in 16bit mode so that the bios could do the hardware stuff for me, would I still be able to use C/C++ to write most of it in, or will i be restricted to ASM because of the interrupts?

Thanks

---

### Post by SunSpyda on 2009-10-28
Yes, you can use C with certain precautions. Inline ASM can be used within C if needed. Pure ASM I imagine will be needed in spots though.

Regarding BSD, most of its variations are damn stable, but yes, they do lack drivers. They are rock solid though, I have put my OpenBSD machine under incredible amounts of stress, & it copes without a sweat.

That all being said, developing on the Linux kernel would be better, since its community is a little less 'l33t' & more plenty, so you can get better help. That is a heavy generalization though, there are many in the BSD community that would help, just less.

---

### Post by grayrainbow on 2009-10-29
Don't forget to post some pics from the OS :) (assuming you use virtual machine). And you going to look a lot about interrupts, probably even start making difference between interrupt and trap. Good look :)

P.S. SunSpyda, not so far ago every single server in microsoft(most of the parts Windows copy from Unix are probably from BSD) was running BSD, yahoo too, I thing that's says enough for the stability of the OS. Just it not support ton of hardware, Mac OS X is kind of a proof that it can be really good desktop system as well. Just to not got in wrong impression for my opinion about BSD :)

---

### Post by SunSpyda on 2009-10-30
> **grayrainbow said:**
> Don't forget to post some pics from the OS :) (assuming you use virtual machine). And you going to look a lot about interrupts, probably even start making difference between interrupt and trap. Good look :)

P.S. SunSpyda, not so far ago every single server in microsoft(most of the parts Windows copy from Unix are probably from BSD) was running BSD, yahoo too, I thing that's says enough for the stability of the OS. Just it not support ton of hardware, Mac OS X is kind of a proof that it can be really good desktop system as well. Just to not got in wrong impression for my opinion about BSD :)

Hahaha, didn't MS remove the BSD due to bad PR? :p Y'know, because people kept saying 'If Windows Server is sooooo good, why don't you use it on your hotmail server?'.

I can certainly see why someone would opt to build on Linux over BSD though.

@cam88 - I would just like to add that there are books by Andy Tanenbaum about OSes which are highly regarded, so you may wish to look at them.

---

