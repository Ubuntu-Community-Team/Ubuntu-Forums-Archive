---
title: "SDL &amp; Linux"
date: 2009-06-06
forum: Programming Talk
---

### Post by Dolf123 on 2009-06-06
Hello,

Today I loaded my visual studio project to check Linux compatibility. I fixed some small things but now I am stuck on this:

error: conflicting declaration &#8216;typedef long unsigned int size_t&#8217;
error: &#8216;size_t&#8217; has a previous declaration as &#8216;typedef unsigned int size_t&#8217;


I know very well what this means but I do not know how to solve it. My windows xp pc is 32 bit, and my Ubuntu pc is 64 bit.

I tried -m32 but it gave me the same error but then on a different typedef. The conflict is between SDL_config_minimal.h and in the -m32 case: stdint.h, and in the x64 case: stddef.h

How can I solve this? (Without actually modifing the header files that is).

Thanks a lot!

---

### Post by wmcbrine on 2009-06-07
SDL has no business redefining size_t. Hmm... On my system (Ubuntu 9.04 64bit), I only have SDL_config.h, no SDL_config_minimal.h, and it does have a line "#undef size_t", but it's commented out. Where did you get your SDL -- from the repos?

---

