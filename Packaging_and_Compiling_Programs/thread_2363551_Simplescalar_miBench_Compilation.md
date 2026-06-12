---
title: "Simplescalar miBench Compilation"
date: 2017-06-11
forum: Packaging and Compiling Programs
---

### Post by dunique on 2017-06-11
Hello all,

I am trying to compile and run adpcm,FFT, gsm, patricia and CRC_32 MiBenchs but i keep getting this error.

Can someone please help on what may be the cause.

THanks

```
ayobami@ayobami-VirtualBox:~/simplescalar$ $IDIR/bin/sslittle-na-sstrix-gcc -o adpcm $IDIR/simplesim-3.0/benchmark/telecomm/adpcm/src/adpcm.c/home/ayobami/simplescalar/sslittle-na-sstrix/lib/libc.a(fmain.o): In function `main':
fmain.c:118: undefined reference to `MAIN__'
ayobami@ayobami-VirtualBox:~/simplescalar$ 
```

---

### Post by howefield on 2017-06-11
Thread moved to the "*Packaging and Compiling Programs*" forum for a better fit.

---

