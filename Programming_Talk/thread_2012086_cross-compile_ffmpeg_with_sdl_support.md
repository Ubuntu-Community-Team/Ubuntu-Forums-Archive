---
title: "cross-compile ffmpeg with sdl support"
date: 2012-06-28
forum: Programming Talk
---

### Post by active1 on 2012-06-28
hi, how can i cross-compile ffnpeg with sdl support ??

i compiled sdl and configured ffmpeg with:
./configure --target-os=mingw32 --cross-prefix=i586-mingw32msvc- --arch=x86 --pkg-config=pkg-config

and the sdl support still "no"

then i tried to configure it with:
./configure --target-os=mingw32 --cross-prefix=i586-mingw32msvc- --arch=x86 --pkg-config=pkg-config --enable-outdev=sdl

and the sdl support still "no"

what should i do ? :S

---

