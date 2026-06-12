---
title: "Major headache. First time with GCC in Windows"
date: 2011-02-03
forum: Packaging and Compiling Programs
---

### Post by lpcstr on 2011-02-03
I've always used MSVC in Windows and GCC whenever in Linux, but recently I've been doing more work in Linux and wanted to make my projects more cross-platform friendly, so I decided to start using MinGW in Windows.

This has been extremely rough getting started.

I installed the latest version of MinGW (GCC 4.5.2) using their GUI installer for Windows. I had to manually add it to my PATH variable because it did not. Next I tried to compile something and it can't find any of the headers because it doesn't search in the right places.

I installed Code::Blocks and added the include/lib directories under compiler settings. OK, now I can actually compile things. The problem is now I want to build Boost and when I run bjam, MinGW can't find any of the darn headers. How can I fix this so I can build Boost? (I've never worked with MinGW before now, nor have I ever built boost).

Another issue I'm having with MinGW is when trying to use std::thread from the C++0x header. In Linux, GCC 4.5.1 has no issues when trying to use it, but nothing I try will seem to get it to work in MinGW. I've searched for hours on Google and nothing I've found has been remotely helpful.

Any help would be appreciated.

---

