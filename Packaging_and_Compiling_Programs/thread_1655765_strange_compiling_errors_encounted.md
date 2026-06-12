---
title: "strange compiling errors encounted"
date: 2010-12-30
forum: Packaging and Compiling Programs
---

### Post by OliviaYi on 2010-12-30
hey guys, I am struggling with my final year project, but trapped in a prob recently: I got following error message during the compilation:

[B][COLOR=RoyalBlue]checking for gcc... gcc
checking whether the C compiler works... no
configure: error: in `/home/nus1/vlc':
configure: error: C compiler cannot create executables[/COLOR][/B]

Strangely, when I tried to run some other test c-programming, the compiler can create executables well.
I checked some previous similar problem, and followed their solutions such as installing "build-essential" etc.
but still the error exist. 

I wonder what's wrong with the compiler, or maybe the program?

can any experienced fellow kindly give some suggestions? Million thanks!:p

---

### Post by SevenMachines on 2010-12-30
Hi, this can be caused by a few things, you need to look at/post 'config.log' for more details, should be in the same directory you ran './configure' in.

---

