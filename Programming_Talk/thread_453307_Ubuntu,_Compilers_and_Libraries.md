---
title: "Ubuntu, Compilers and Libraries"
date: 2007-05-24
forum: Programming Talk
---

### Post by ART_Adventures on 2007-05-24
I have experience at programming on the Windows platform, but I decided to take a look at programming on Linux, and I'm impressed. I downloaded Code::Blocks and having found a whole list of libraries featured in Synaptic (like SDL, OpenGL) I was surprised to find that I could just click on them, install them, and as if by magic the GCC compiler in Code::Blocks could suddenly build and run  apps that used those libraries. In Windows, you often have to fiddle around with compiler settings, specifying the directories where lib and include files are to be found, but not with Ubuntu so far. I just install the libs from synaptic and that seems to be it.

That's great, but rather mysterious for a Windows programmer. Mainly because I'd like to know where all these libs and headers are being downloaded to. I'd like to know exactly which directories my compiler is referencing. This is because I recently tried downloading the ClanLib graphics library. But I believe the libs featured in Synaptic are not the latest because when I try to a compile a simple ClanLib app, the compiler points to syntax errors that should be correct in the latest version. So, I'd like to download the source and headers from the clanlib website, and overwrite the older files that synaptic downloaded.

Has anybody else experienced this? Any ideas?

---

### Post by ankursethi on 2007-05-24
I think they are stored in /usr/lib.

---

### Post by tkjacobsen on 2007-05-24
The include files are in /usr/include

---

### Post by WW on 2007-05-24
The header files (*.h) are in /usr/include (or in subdirectories of /usr/include).  The object files (*.so, *.a, etc) are in /usr/lib.

---

### Post by WW on 2007-05-24
> **ART_Adventures said:**
> So, I'd like to download the source and headers from the clanlib website, and overwrite the older files that synaptic downloaded.


Don't 'overwrite the older files'; go back into Synaptic and remove all the ClanLib packages.

---

