---
title: "Reference problems :/"
date: 2006-03-31
forum: Programming Talk
---

### Post by K-Zodron on 2006-03-31
Hello!

I have happily been using Ubuntu for a week or so, and now I would like to develop games using C++ and SDL again, but I have smashed myself into some problems ](*,) 

I installed the necessary libsdl libraries, they are on the computer fine..but when I try to compile anything, I get errors like this:
rpg_main.cpp:(.text+0x31): undefined reference to `operator new(unsigned int)'
rpg_main.cpp:(.text+0x44): undefined reference to `operator new(unsigned int)'
/tmp/ccrwZtBT.o: In function `__tcf_0':
rpg_main.cpp:(.text+0x17b): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccrwZtBT.o: In function `__static_initialization_and_destruction_0(int, int)':
rpg_main.cpp:(.text+0x1a8): undefined reference to `std::ios_base::Init::Init()'


Even the most simple int main() { cout << "Hi"; return 0; } doesn't wanna compile without at least 6 errors :/

I tried reinstalling the SDL libraries..no luck :(

You guys got any ideas? Is there some specific header that would help here? Should I get the libraries from somewhere else then the Synaptic package manager program? 

Yours,
K-Zodron

---

### Post by benvdh on 2006-03-31
Hey,

did you also install the dev packages, because those are the packages that contain the headers ?

If not try installing those and see if it works.

Regards,

Ben

---

### Post by K-Zodron on 2006-03-31
Yes, I installed the dev packages too (smth like libsdldev etc.)

Any other ideas ? =/

---

### Post by LordHunter317 on 2006-03-31
You are calling GCC as G++, right?

---

### Post by K-Zodron on 2006-03-31
Yes..now I managed to f'ck up the whole crap, command prompt doesn't start, can't run commands etc. xd maybe a reboot will help :P

Gtg sleep now, I'll be back tomorrow

---

