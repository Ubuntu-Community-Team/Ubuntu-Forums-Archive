---
title: "Custom C Libraries"
date: 2010-01-24
forum: Packaging and Compiling Programs
---

### Post by SenojLuap on 2010-01-24
I've written a couple of small utility functions that I will most likely use in my C/C++ programs in the future. I would like to put all such files in some directory so that I can easily #include them.
My best attempt was to compile the source down to object files (.o if that matters), then to move them, along with their headers to a custom include directory (I chose /home/paul/include). Afterwards, I set the environment variables: C_INCLUDE_PATH=/home/paul/include and CPLUS_INCLUDE_PATH=/home/paul/include
I read somewhere that this was the correct approach, but it doesn't work so I have to assume I misunderstood the instructions. Can anyone provide any suggestions? I'd really like to avoid the gcc '-I' or Makefile alterations, as they will have to be done EVERY time I use those functions. A simple "#include <myFunc.h>" would be so much nicer.

---

