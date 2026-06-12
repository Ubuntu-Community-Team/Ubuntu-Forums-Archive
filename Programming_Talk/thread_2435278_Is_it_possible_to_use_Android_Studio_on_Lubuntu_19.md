---
title: "Is it possible to use Android Studio on Lubuntu 19.10?"
date: 2020-01-18
forum: Programming Talk
---

### Post by mkoniecz on 2020-01-18
Is it possible to use Android Studio on Lubuntu 19.10?

[https://developer.android.com/studio/install](https://developer.android.com/studio/install) has

> If you are running a 64-bit version of Ubuntu, you need to install some 32-bit libraries with the following command:
> sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1 libbz2-1.0:i386

the problem is that this packages are available on 18.10 and unavailable on 19.10.

I have not switched yet my main laptop to 19.10 and I have no good way to test it (and Android Studio is critical to me).

On my secondary laptop Android Studio crashes, but it is likely to be caused by an insufficient RAM. And similarly I am unable to test it in the VM.

---

