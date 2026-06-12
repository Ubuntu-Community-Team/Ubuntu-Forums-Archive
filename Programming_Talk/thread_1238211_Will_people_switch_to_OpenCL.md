---
title: "Will people switch to OpenCL"
date: 2009-08-12
forum: Programming Talk
---

### Post by froggyswamp on 2009-08-12
Folks, do you think it makes sense that instead of relying on VDPAU it would be better to rewrite the video codecs using OpenCL ?(when OpenCL becomes (fully) supported on Linux)

The pros I see so far:
-it would be not only cross-platform but also "cross-videocard"
-the video acceleration would become opensource even if the drivers were closed source.

Cons:
-on Linux, ati, nvidia and intel have yet to release final OpenCL support
-the vendors could choose not to support OpenCL on some (older) versions of their hardware.

What are your thoughts?

---

### Post by kjohansen on 2009-08-12
As a current CUDA user I know I am looking into OpenCL.

NVIDIA is very close to releasing final support, I believe the estimate is within the year.  

Feature I like the most over CUDA: JIT compiling for cross device use.

---

