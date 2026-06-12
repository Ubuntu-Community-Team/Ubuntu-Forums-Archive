---
title: "Reading a file created in UCS-2"
date: 2007-04-20
forum: Programming Talk
---

### Post by alphilli on 2007-04-20
I have a file that was created on a Windows machine using UCS-2 (what Win32 considers to be UNICODE).   The file contains the Byte Order Mark (BOM) at the beginning of the file indicating Little Endian.  

When I read it in Win32 fgetws() works just fine, giving me one line at a time.  However, when I attempt to read it using fgetws() in Linux I get an end of file immediately.

Because Linux assumes that UNICODE is 32 bits I'm not surprised that fgetws() does not work.

But I'm wondering if there is any way to read that file properly in Linux or if the file has to be reformatted into 32-bit data.

One other question:  does Linux understand/respect a BOM at all?

Thanks.

---

