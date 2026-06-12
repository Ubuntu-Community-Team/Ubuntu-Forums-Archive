---
title: "recompiling Ubuntu kernel from source package"
date: 2024-01-03
forum: Packaging and Compiling Programs
---

### Post by hoover67 on 2024-01-03
Dear Ubuntu community,

I recently purchased a Winwing Orion 2 HOTAS system using the F-16EX grip. Looking at the button numbers in evtest and also jstest-gtk, I see that no button with a number higher than 80 registers with either utility.

Apparently this is caused by a kernel / input limitation which restricts the highest button number to 80. In order to fix this, I'd like to recompile the Ubuntu kernel from the source package with two modified header files according to this patch mentioned on th LKML: 

[https://patchwork.kernel.org/project/linux-input/patch/CACa7zykn0q9XJAUvrqnNATr4DUv3Kc7XujF3vm6sfRB5pE6YNQ@mail.gmail.com/](https://patchwork.kernel.org/project/linux-input/patch/CACa7zykn0q9XJAUvrqnNATr4DUv3Kc7XujF3vm6sfRB5pE6YNQ@mail.gmail.com/)

Applying the patch is easy enough, however I cannot find any recent howto / documention on how to recompile the kernel package. I've tried following this howto in the ubuntu wiki: 

[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

but the build process breaks in several places (the howto is probably outdated as it refers to "disco dingo" or similar), some of which I've managed to fix / circumvent but I gave up  on some tool called "turbostat" that I've never heard of in conjunction with compiling a kernel from source (which I have done many times in the 2000s or thereabouts :)) 

I'd be very grateful for any guidance / help on how to build a recent kernel using the source packages the "Ubuntu" way. It would be great if we could get these advanced flightsim periphals to work in xplane12, flightgear and other sims on Linux! 

Thanks in advance for your time & all the best, 

Uwe

---

### Post by hoover67 on 2024-01-05
Hi folks, 

here's a little bump for my request... I hope there is some up-to-date documentation available on how to recompile the kernel from source packages and I'd be very happy if someone could point me to it. 

Thanks!

Uwe

---

### Post by hoover67 on 2024-01-08
I think I got a bit further down the path to a compiled kernel, modules and tools by installing libcap-dev. Now turbostat compiles ok, however the next stubbed toe was waiting in the form of a missing libjvmti or similiar during installation / deb building. I'll investigate further. 

Cheers, Uwe

---

