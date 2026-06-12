---
title: "X86 or AMD64? for Intel(R) Core(TM) i5-2320"
date: 2012-09-24
forum: Recurring Discussions
---

### Post by zhiyazw on 2012-09-24
I am runing on a PC with Intel(R) Core(TM) i5-2320, and the version I need is absolutely 64-bit Ubuntu. Then should me use "
[[COLOR=#772953]PC (Intel x86) desktop CD[/COLOR]]("http://releases.ubuntu.com/lucid/ubuntu-10.04.4-desktop-i386.iso") ", or "[[COLOR=#772953]64-bit PC (AMD64) desktop CD[/COLOR]]("http://releases.ubuntu.com/lucid/ubuntu-10.04.4-desktop-amd64.iso")" ? 
I read some threads from others, I think I should choose AMD64, but the brief of X86 make me doubting, it says "For almost all PCs. This includes most machines with Intel/AMD/etc type processors ", pls someone clarify this? Thx

---

### Post by QIII on 2012-09-25
Use the 64 bit CD.  You have 64 bit hardware.  "AMD64" is a historical convention and does not mean it only works on AMD processors.

And prepare for a move to Recurring Discussions in 5 ... 4 ... 3 ...

---

### Post by oldfred on 2012-09-25
We are really slow in moving this: :)

[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

Another new reason. 
Only the 64bit version supports UEFI boot. Most new computers are UEFI/BIOS boot, but depending on how Windows is installed, Ubuntu must be installed in the same UEFI mode or BIOS mode.

---

### Post by Paqman on 2012-09-26
Why would you want to restrict a nice new machine like that to the old 32-bit speeds? It'd be like buying a Ferrari and only ever using first gear.

---

### Post by kio_http on 2012-09-26
> **Paqman said:**
> Why would you want to restrict a nice new machine like that to the old 32-bit speeds? It'd be like buying a Ferrari and only ever using first gear.

Why would 32 bit be slower than 64 bit assuming both have access to the same amount of RAM?

---

### Post by TheMTtakeover on 2012-09-26
> **kio_http said:**
> Why would 32 bit be slower than 64 bit assuming both have access to the same amount of RAM?

Increased RAM usage is probably the best gain from 64-bit but there are other benefits as well. If you are running on a 64-bit capable machine using a 64-bit OS it will allow you to take a full advantage of all your hardware. Think Internal Register and Front-side Bus. The processor can also handle more bits at one time.

To the OP, AMD was the first to make a processor that was capable of running 32 or 64 bit and not being stuck to one or the other. It was named AMD64. Intel followed very quickly their is EM64T, but it is usually just noted as AMD64 as this was the first. It doesn't matter if you are AMD or Intel. Still works the same.

---

### Post by zhiyazw on 2012-09-27
> **QIII said:**
> Use the 64 bit CD.  You have 64 bit hardware.  "AMD64" is a historical convention and does not mean it only works on AMD processors.

And prepare for a move to Recurring Discussions in 5 ... 4 ... 3 ...

Thanks, I think my confusion is cleared.

---

### Post by thatguruguy on 2012-09-27
> **kio_http said:**
> Why would 32 bit be slower than 64 bit assuming both have access to the same amount of RAM?

In a word, multi-threading.

---

### Post by Paqman on 2012-09-27
> **kio_http said:**
> Why would 32 bit be slower than 64 bit assuming both have access to the same amount of RAM?

For any task involving heavy number-crunching such as encryption and video encoding a 64-bit chip will be faster. Essentially this is because it can handle very long numbers in a single operation, whereas a 32-bit chip would have to split it up into several operations.

---

### Post by mips on 2012-09-28
> **kio_http said:**
> Why would 32 bit be slower than 64 bit assuming both have access to the same amount of RAM?

If you had to transfer a pile of sand from A to B then carrying two buckets of sand at a time would be faster than carrying one bucket.

---

### Post by MadCow108 on 2012-09-29
> **mips said:**
> If you had to transfer a pile of sand from A to B then carrying two buckets of sand at a time would be faster than carrying one bucket.

this is a very incomplete.
with 64 bits you carry two buckets at a time no matter if you only needed one.

64 bit can have a negative impact on performance due to everything being 64 bit where it mostly is not required. It clogs the cpu caches (thats why there will soon be x32)

but what makes amd64 better for ubuntu (and all other binary distributions) is the instruction set it requires.
32 bit packages are compiled for i386 (+cmov) instruction set.
This means they cannot use the vector extensions (64 bit) cpu's have and only use 8 the available general purpose registers and none of the vector registers.
64 bit packages on the other hand are compiled for the amd64 instruction set which allows them to use all 16 general purpose registers and all 16 of the vector registers for SSE2 instructions.

This is allows amd64 packages to normally outperform i386 packages.

It is completely different when you compile for 32 bit and tell the compiler to make use of the amd64 instruction set. Then your 32 bit app might be faster and use less ram.
But as this is very machine specific it is only done in source distributions like gentoo.

---

### Post by Paqman on 2012-09-29
> **MadCow108 said:**
> this is a very incomplete.


Deliberately so, clearly.

---

### Post by 3rdalbum on 2012-09-29
> **mips said:**
> If you had to transfer a pile of sand from A to B then carrying two buckets of sand at a time would be faster than carrying one bucket.

That would be a great analogy... if you were talking about multi-core CPUs.

It's not a case of "double the bits, double the speed, all the time".

I haven't heard any good analogies for 64-bit versus 32-bit. The main advantages with 64-bit are that:

1. It can mathematically process 64-bit numbers in one step rather than three steps; 64-bit numbers are used in things like video encoding.

2. It can address and use more RAM than a straight 32-bit CPU.

Thinking of an analogy for #1, it's like the mailman carrying larger bags. It doesn't make his walking speed quicker and he doesn't get his walking route done faster; but it does allow him to drop off larger items without having to come back later with a truck. Not every house has larger items to be delivered.

My analogy for #2 is a bit better. If there were only four digits in a phone number, you could only have 10,000 telephone subscribers (0000-9999). With eight-digit phone numbers, you can have 100,000,000 telephone subscribers. If there are only 500 telephone subscribers you won't see a benefit to having eight digit phone numbers - in fact, it will make the phone book bigger than it needs to be due to all the superfluous digits - but as soon as you hit 10,001 subscribers it pays off.

---

