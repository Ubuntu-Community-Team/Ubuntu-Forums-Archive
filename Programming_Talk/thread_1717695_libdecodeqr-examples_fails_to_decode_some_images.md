---
title: "libdecodeqr-examples fails to decode some images"
date: 2011-03-30
forum: Programming Talk
---

### Post by ras123 on 2011-03-30
Hi,
I tried to decode sample images with the libdecodeqr-examples, they works, but other images returns nothing.
debian.or.jp.qr.jpg gives
> 
libdecodeqr version 0.9.3 ($Rev: 42 $)
STATUS=2080
[http://www.debian.or.jp](http://www.debian.or.jp) 

MEBKM:TITLE:DebianJP;URL:http\://www.debian.or.jp;;

Hit any key to end.

But QrDecoderQt.png image returns no text!
> 
libdecodeqr version 0.9.3 ($Rev: 42 $)
STATUS=2019


Hit any key to end.

Also I make an image with help of qrencoder, this cannot decoded with the above program, and returns similar statement.
> 
libdecodeqr version 0.9.3 ($Rev: 42 $)
STATUS=4400

Hit any key to end.


What mean by status? the above images (attached with this) are decode with a on line qr decoder correctly.

---

