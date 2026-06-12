---
title: "Help needed on unpacking a firmware file"
date: 2011-10-04
forum: Packaging and Compiling Programs
---

### Post by cool_recep on 2011-10-04
Hi guys, I know that this forum is not the right place but I need your help on unpacking a firmware file.

The firmware belongs to SONY Bravia Smart TV which runs Linux.

Firmware is here:

[http://www.mediafire.com/?371sodalbkui26h](http://www.mediafire.com/?371sodalbkui26h)

And here is the binwalk analysis:

```
root@ubuntu:/home/user/&#304;ndirilenler/binwalk-0.3.9/src# binwalk fw.bin
binwalk: /usr/local/lib/libcurl.so.4: no version information available (required by binwalk)

DECIMAL   	HEX       	DESCRIPTION
-------------------------------------------------------------------------------------------------------
3485529   	0x352F59  	bzip2 compressed data, block size = u00k
23646804  	0x168D254 	bzip2 compressed data, block size = S00k
24439192  	0x174E998 	BFLT executable  version 3698180314,  code offset: 0xD0DBFC89,  data segment starts at: 0xFC57E3C8,  bss segment starts at: 0x314AD91C,  bss segment ends at: 0x579AC36E,  stack size: -209315630 bytes,  relocation records start at: 0x10C36FC1,  number of reolcation records: 1388897630,  gotpic gzdata
32409668  	0x1EE8844 	bzip2 compressed data
40790549  	0x26E6A15 	gzip compressed data, ASCII, has CRC, extra field, last modified: Sat Dec  8 07:18:40 2012
41683215  	0x27C090F 	bzip2 compressed data
44487229  	0x2A6D23D 	bzip2 compressed data, block size = X00k
```

And the source code:

[http://www.sony.net/Products/Linux/TV/KDL-40NX700.html](http://www.sony.net/Products/Linux/TV/KDL-40NX700.html)

If you can't help, please direct me to the right place. Thanks.

---

