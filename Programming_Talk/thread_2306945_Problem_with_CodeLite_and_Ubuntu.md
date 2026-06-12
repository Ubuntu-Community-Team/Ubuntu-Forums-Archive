---
title: "Problem with CodeLite and Ubuntu?"
date: 2015-12-20
forum: Programming Talk
---

### Post by Jamie_Edwards on 2015-12-20
Hi guys,

Right, first off, I don't know if this goes here but it's the best shot I have as the actual CodeLite forum seems to be down (as I'm unable to access it on both my laptop and phone).

I've recently installed CodeLite 9.0.0 from their PPA and although it launches fine, as soon as I've created a new workspace and write a simple C++ hello world program and try to build it, CodeLite crashes instantly.

I don't know why this could be so I'm here asking if anyone uses CodeLite on Ubuntu 15.10, if they have any similar issues as the one above, and more importantly, how do I go about fixing it?

Just some background info...

As stated above, I'm using CodeLite v9.0.0.
I'm on Ubuntu 15.10.
CodeLite seems to default to the Cross GCC (x86_64) compiler. I've tried to use the normal GCC compiler but the same outcome happens as stated above.

I've tried using Code::Blocks, but it's not stable on my system, the GUI seems to go very funky and becomes almost impossible to work with. I've also tried using Eclipse CDT, but its indexing seems to be very stupid. So I'd rather not use Eclipse for anything other than to develop Java related things.

Thanks!

Jamie.

---

### Post by eranif on 2015-12-21
> CodeLite forum seems to be down (as I'm unable to access it on both my laptop and phone
Sorry about that, hopefull it will be resolved today ...

About the crash: do you get a file ~/.codelite/crash.log? can you paste its content here?

If you don't have one, please run CodeLite under gdb, like this:

gdb /usr/bin/codelite
(gdb)run

and when it crashes, just type:

(gdb)bt

Thanks,
Eran

---

