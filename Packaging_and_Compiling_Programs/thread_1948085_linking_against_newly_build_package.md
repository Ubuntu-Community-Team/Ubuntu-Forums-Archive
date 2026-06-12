---
title: "linking against newly build package"
date: 2012-03-27
forum: Packaging and Compiling Programs
---

### Post by cartland on 2012-03-27
Newbie - I think this is the right forum - apologies if not and please point me to the right one.

In Ubuntu 10.4 I have the prebuilt package openssl 0.9.8k (just updated). I downloaded the equivalent source from launchpad and rebuilt (because I wanted to use "no-asm -DPURIFY") and installed to the default locations.

My application calls openssl directly as well as through libcurl. Linking the preinstalled libcurl package with the new openssl binaries produces numerous errors from libcurl of the form:

[FONT=Arial][SIZE=2]libcurl.so: undefined reference to `ENGINE_get_id@OPENSSL_0.9.8'

The methods referenced are definitely in the new binary.

I've tried the "gcc -Wl,-rpath" approach to point the linker at the new libs (as well as -L of course).

As I haven't built ubuntu packages from source before perhaps I'm missing something fundamental?

thanks
[/SIZE][/FONT]

---

