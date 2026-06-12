---
title: "zlib/libpng segmentation fault on Edgy"
date: 2007-02-16
forum: Programming Talk
---

### Post by EReckase on 2007-02-16
I have a C routine that writes out a PNG file - very standard code.  On a very irregular basis, I get a segmentation fault (maybe 1 out of 50 function calls).  I also get the same segmentation fault backtrace infrequently when hitting PrintScreen to take a screenshot - so that pretty much eliminates my code as the source of the problem.  This is a freshly built machine - AMD X2 4600+ processor, 2 GB Corsair DDR2 800 RAM, Asus M2N-SLI Deluxe motherboard, no overclocking - running Edgy with all updates.  I've run memtest on the memory and repeatedly gotten no errors.  I recompiled the latest libpng an zlib with debugging, linked my code to the new libraries, and got the following backtrace:

```
[Thread debugging using libthread_db enabled]
[New Thread -1211844944 (LWP 6724)]
[New Thread -1313920096 (LWP 6727)]
[New Thread -1322312800 (LWP 6728)]
[Thread -1313920096 (zombie) exited]         
[Thread -1322312800 (zombie) exited]
writing bench.png...
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1211844944 (LWP 6724)]
0xb7cd337c in memcpy () from /lib/tls/i686/cmov/libc.so.6
(gdb) where
#0  0xb7cd337c in memcpy () from /lib/tls/i686/cmov/libc.so.6
#1  0x080908c9 in read_buf (strm=0x80a9d08, buf=0x80c0db8 "", size=32768) at deflate.c:976
#2  0x08090f99 in fill_window (s=0x80b76f0) at deflate.c:1342
#3  0x080918e6 in deflate_slow (s=0x80b76f0, flush=0) at deflate.c:1569
#4  0x08090189 in deflate (strm=0x80a9d08, flush=0) at deflate.c:790
#5  0x0808c5b4 in png_write_filtered_row (png_ptr=0x80a9c38, filtered_row=0x80fbdf0 "\003")
    at pngwutil.c:2733
#6  0x0808c502 in png_write_find_filter (png_ptr=0x80a9c38, row_info=0x80a9d94) at pngwutil.c:2700
#7  0x080765d2 in png_write_row (png_ptr=0x80a9c38, row=0xb79ee008 "") at pngwrite.c:927
#8  0x0807623d in png_write_image (png_ptr=0x80a9c38, image=0x80ad5a0) at pngwrite.c:752
#9  0x0806e883 in write_png (file=0x80a9ad0, image=0xb795f008 "", width=1024, height=747)
    at png.c:59

```

I know that this RAM isn't on the QVL for the Asus motherboard, but I've seen it used before, and I'd expect more frequent errors with other things if it were the memory, and since all of the memory tests are passing, I have trouble believing that's the problem.

Does anyone have any ideas why this is taking place?  I can provide any additional information as necessary - I've gone just about as far as I can with this bug, especially since I can't debug gnome-screenshot.

---

